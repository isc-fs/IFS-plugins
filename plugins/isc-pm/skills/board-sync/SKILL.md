---
name: board-sync
description: Produce the ISC board meeting report covering every department. Use when the user says "prep for the board meeting", "weekly board sync", "state of the season", "board report", "what do we need to decide", or "catch me up on where we are".
---

# Board sync

Produce the report the board actually meets on: where the season stands, what needs a
decision, and what leaves the room as an action.

Read `${CLAUDE_PLUGIN_ROOT}/references/notion-workspace.md` first. This skill reads
across every department, not just PM.

## What to pull

| Source | What for |
| --- | --- |
| Milestones | Slipped, at risk, and due in the next three weeks |
| Tasks | Overdue and blocked, grouped by department |
| Sponsor Pipeline | Committed value, active prospects, anything overdue or unowned |
| Sponsor Deliverables | Anything overdue, since these are commitments |
| Content Plan | Capture deadlines inside two weeks, and any missed |
| Decision Log | Decisions taken since the last sync |

Query each database in a **separate** call. The team's Notion plan does not allow SQL
across multiple data sources, so combining them in one query fails. Six small queries
are correct; one joined query is not.

If a department's connector or database is unavailable, say which one and report on the
rest rather than failing entirely.

## Report structure

**1. Headline.** Three or four sentences. Where the season stands against the
milestones, whether that changed this week, and the single biggest risk right now. Write
this last, from the sections below, but put it first.

**2. Since the last sync.** What moved: milestones completed or slipped, prospects
advanced or closed, content published, decisions taken. If there is no previous sync to
compare against, say so rather than implying nothing happened.

**3. Needs a decision this meeting.** The most important section. Items where work is
blocked pending a board call, each with the options and what each one costs. Do not
bring a decision without framing the alternatives; a board asked an open question with
no options will defer it, and it will appear again next week unchanged.

**4. By department.** Three or four lines each for PM, Sponsorship, Marketing and
Technical. State, biggest risk, what they need from the others.

**5. Cross-department blockers.** Where one department is waiting on another. These are
the ones that only get resolved in a room with everyone present, which is exactly what
the meeting is for, so surface them explicitly.

**6. Actions out of this meeting.** Every action with a named owner and a date. No
exceptions, no "the team will look into it".

## Rules

- Every figure comes from Notion. Never estimate to fill a section.
- Name owners. A report with no names produces no accountability.
- Lead with bad news. A board report that buries a slipped milestone under good news is
  doing the opposite of its job.
- Keep it to something readable in five minutes. If a section is long, the length is
  itself the finding: say so and summarise.

## After the meeting

Offer to write the actions into the Tasks database with owners and dates, and the
decisions into the Decision Log with their reasoning and rejected alternatives. Decisions
that stay in someone's meeting notes are lost by September, which is the whole reason
the Decision Log exists.
