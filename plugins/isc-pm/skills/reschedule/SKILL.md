---
name: reschedule
description: Recompute planned start and end dates for the ISC task tracker by walking the dependency graph. Use when the user says "reschedule", "recompute the dates", "I changed a duration", "update the Gantt", "what does this slip affect", "run the scheduler", or after adding or changing task dependencies.
---

# Reschedule

Compute every task's planned start and end from the dependency graph and write them
back. This replaces the Excel workbook's iterative calculation, which Notion formulas
cannot do because they cannot walk a chain of relations.

Read `${CLAUDE_PLUGIN_ROOT}/references/notion-workspace.md` first.

## Step 0: fill in whichever of Duration / Expected end is missing

Three fields describe how long a task takes, and you only ever enter two:

- **Expected start** — when you want to begin
- **Duration** — how many days it takes
- **Expected end** — when you want it finished

Before scheduling anything, for every task:

- Expected start and Duration set, Expected end empty → write
  `Expected end = Expected start + Duration - 1`
- Expected start and Expected end set, Duration empty → write
  `Duration = Expected end - Expected start + 1`
- All three set and consistent → leave alone
- All three set and **inconsistent** → do not silently pick one. Report the task, both
  implied values, and ask which is right. Someone entered a duration and then changed a
  date, and guessing which they meant is how a plan quietly becomes fiction.
- Only one of the three set → the task cannot be scheduled. Report it and move on.

The inclusive arithmetic matches the workbook: a one-day task starting Monday ends
Monday, which is why the formula subtracts one.

## The rule being implemented

For each task:

```
Planned start = max(Expected start, latest Planned end of every predecessor + 1 day)
Planned end   = Planned start + Duration - 1
```

The arithmetic is inclusive throughout, matching Step 0 and the workbook: a one-day
task starting Monday ends Monday, and a task waiting on one that ends Monday starts
Tuesday.

`Depends on` accepts several predecessors. Take the **latest** of their planned ends, not
the first: a task waiting on three things is ready when the slowest one finishes.

A task with no dependencies simply starts on its Expected start. A task whose
`Planned start` ends up later than its `Expected start` has been pushed by a
dependency, which is exactly the signal the workbook's guide describes.

## Procedure

**1. Pull the graph.** Query the IFS09 Tasks data source for every task: page URL,
Task, Task ID, Duration, Expected start, Planned start, Actual end, Status, and the
`Depends on` relation. Query only this one data source; the plan does not allow
multi-source queries.

**2. Check the data before computing.** Run Step 0 first, then report and skip, rather
than guessing:

- Tasks still missing a Duration after Step 0. These cannot be placed. Do not invent one.
- Tasks with no Expected start and no dependencies: nothing anchors them in time.
- Tasks with a Duration of zero or negative.
- Tasks where Duration and Expected end disagree (from Step 0).

**3. Detect cycles.** Run a topological sort. If any cycle exists, **stop and report
it** with the exact task chain, and write nothing.

This matters: the workbook could not detect this. Its own guide says that if A waits
on B and B waits on A, the dates stop meaning anything and Excel does not warn you.
Silently writing wrong dates is worse than refusing, so refuse.

**4. Compute in topological order.** Process each task only after everything it
depends on. Apply the rule above.

Treat a completed task's `Actual end` as its effective end when scheduling its
dependents, since reality beats the plan. If a predecessor finished early, its
dependents can start early.

**5. Show the diff before writing.** List every task whose dates change, with old and
new values and how many days it moved. Lead with the largest movements. If more than
about twenty tasks move, summarise by vertical and show the ten largest.

Ask for confirmation before writing unless the user has already said to just do it.

**6. Write back.** Update `Planned start` and `Planned end` on each changed task, plus
any `Duration` or `Expected end` derived in Step 0.

Never touch `Expected start`, `Actual end` or `Status`: those are human inputs. Never
overwrite a Duration or Expected end the user already filled in.

**6b. Write the charted lateness fields.** `Deviation` and `Pushed` are formula
properties. Notion cannot chart or filter on a formula, so the Dashboard reads two real
properties that you write instead:

- **`Days late`** (number). For an open task: `today - Planned end`, floored at zero, so
  it is never negative. For a completed task with an `Actual end`:
  `Actual end - Planned end`, which may be negative when it finished early. Leave empty
  when there is no `Planned end` or no `Actual end` to compare against.
- **`Timing`** (select). Exactly one of:

| Value | Condition |
| --- | --- |
| `Not scheduled` | No `Planned end`, usually because `Duration` is empty |
| `Late` | Open and `Planned end` is in the past |
| `Due soon` | Open and `Planned end` is within the next seven days |
| `On track` | Open and `Planned end` is more than seven days away |
| `Done late` | `Status` is Completed, `Actual end` after `Planned end` |
| `Done on time` | `Status` is Completed, `Actual end` on or before `Planned end` |
| `Done - no end date` | `Status` is Completed but `Actual end` is empty |

Write these for **every** task on every run, including the ones that cannot be
scheduled: a task left with an empty `Timing` disappears from the Dashboard instead of
showing up as a gap, which is the opposite of what the page is for.

`Done - no end date` is a data fault, not a state. List those tasks in the report and
ask for their real completion dates.

**7. Report the consequences.** After writing, state:

- Which tasks now finish later than before, and by how much
- Any task whose `Planned end` now falls after a competition date or a milestone
  target date, which is the finding that actually matters
- The critical path: the longest dependency chain, since that is what determines when
  the project finishes and where compression is worth trying
- How the lateness picture changed: how many tasks moved into or out of `Late`, and the
  largest single `Days late` value

## Answering "what does this slip affect"

When asked about a specific task rather than a full run, walk the `Blocks` relation
forwards from it and report the downstream chain with the days each would move. Do not
write anything; this is a question, not a reschedule.

## Honesty rules

- Never invent a Duration or an Expected start to make a task schedulable. Report the
  gap.
- Never write dates when a cycle exists anywhere in the graph.
- If the computed plan pushes work past a competition date, say so plainly in the
  report. A schedule that quietly runs past the event is the single most expensive
  thing this tool can hide.
