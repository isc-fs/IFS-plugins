---
name: task-triage
description: Triage the ISC task list to find what is overdue, unowned, blocked or stale. Use when the user says "who owes what", "what's overdue", "triage the tasks", "clean up the task list", "what's blocked", "what am I on the hook for", or "what needs chasing".
---

# Task triage

Turn the task list into a short list of things that need a human to act, and clean out
everything that is quietly rotting.

Read `${CLAUDE_PLUGIN_ROOT}/references/notion-workspace.md` first, then query the Tasks
database. Compute against today's date.

## The report

**Overdue.** `Due` in the past, status not `Done` or `Dropped`. Sorted by how late.
Owner named on every line. This is the section people act on, so it goes first and stays
short: if it runs past fifteen items the list has stopped being used and that is itself
the finding.

**Blocked without a name.** Status `Blocked` with an empty or vague `Blocker detail`.
A blocker that does not name a person and a specific ask is not a blocker, it is an
excuse, and it will sit there until someone asks. Flag each one and ask what is
actually needed and from whom.

**Unowned.** Active tasks with no `Owner`. These will not get done. There is no
exception to this.

**Stale.** Tasks in `In progress` with no due date, or untouched for more than a month.
Either they matter and need a date, or they do not and should be `Dropped`.

**Orphaned.** Active tasks with no linked `Milestone`. Ask whether they serve something
real. Some genuinely are necessary overhead; many are work that made sense once and no
longer does.

**Critical inflation.** If more than about a fifth of open tasks are `Critical`, say so.
When everything is critical, nothing is, and the field has stopped carrying information.

## Per-person view

When the user asks what they or a named person owes, filter by `Owner` and give a short
ordered list: overdue first, then due this week, then blocked. Do not pad it with
everything they own. Three to seven items that need action beats a complete inventory.

## Cleaning up

Offer to make the obvious changes directly: mark clearly finished tasks `Done`, drop
tasks that are plainly dead, add missing milestone links where the connection is
unambiguous.

Do not reassign owners, change due dates, or drop anything ambiguous on your own. Those
are decisions for the board. Propose them and let a human confirm.

## Tone

Be blunt and specific. "Six tasks are unowned" is useless; naming them and saying who
should probably own each is not. Where a pattern is visible, say it: one person holding
fifteen overdue tasks is a resourcing problem, not a diligence problem, and reporting it
as the latter is unfair to them.
