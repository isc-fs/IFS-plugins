# ISC Project Management

Roadmap, task triage and board reporting for the ISC Formula Student Racing Team.
Install in the Claude account of whoever runs project management, alongside `isc-core`.

## What it does

| Skill | Use it for |
| --- | --- |
| `reschedule` | Recomputing planned dates from the dependency graph. Replaces the Excel cascade. |
| `season-roadmap` | Building the milestone set, and reporting what has slipped or is about to |
| `task-triage` | Who owes what: overdue, unowned, blocked, stale. The weekly cleanup. |
| `board-sync` | The cross-department board meeting report |

## Setup

Connect Notion, with access to the `IFS 09` teamspace. Nothing else.

## Not the same as the `productivity` plugin

The general `productivity` plugin keeps a personal task file. It is fine for your own
work but it is single-user: nobody else can see it and it does not survive you leaving.
Anything the board needs to see goes in the Tasks database in Notion.

## Replacing the Excel workbook

`IFS09 Tasks` in Notion replaces `CAMBIOS_IFS-09.xlsx`. Fields map one to one, the
`Depends on` relation replaces `DEPENDE DE` and still crosses verticals, and the Gantt
view replaces the GANTT sheet.

One thing does not carry over natively. In the workbook, stretching a Duration moved
everything downstream automatically through iterative calculation. Notion formulas
cannot walk a dependency chain, so `Planned start` and `Planned end` are written by the
`reschedule` skill instead. Run it after changing durations or dependencies.

The trade is a manual step in exchange for something the workbook could not do:
`reschedule` detects circular dependencies and refuses to write rather than producing
dates that quietly stop meaning anything.

## The two ideas worth keeping

**Dates change in one place.** The Milestones database is the source of truth. A date
changed in a meeting, a chat, or someone's head has not changed. Every other department
plans from these dates, so a stale roadmap silently corrupts the content plan and the
sponsorship pitch at the same time.

**`At risk` marked early is the highest-value habit in the department.** Seasons are not
lost because a date slipped. They are lost because it slipped silently for six weeks
while three subteams kept planning around it. The status costs nothing to set.

## The data lives in Notion

Under **Tasks & Gantt** in the `IFS 09` teamspace:

- **Milestones**: the season roadmap, one owner each, with a capture flag for Marketing
- **Tasks**: who owes what, across every department

## Maintaining this plugin

Ask Claude to "customize the isc-pm plugin".
