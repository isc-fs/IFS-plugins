# ISC Notion workspace

All state lives in Notion. Requires the Notion connector enabled in the chat. If Notion
tools are unavailable, say so and stop rather than tracking anything locally.

## Page structure

Everything sits directly in the `IFS 09` teamspace. There is no wrapper page.

| Page | ID |
| --- | --- |
| Tasks & Gantt | `3ccd2857-f77c-8176-b3e7-c44e3aba3785` |
| MG · Management | `3ccd2857-f77c-8189-8106-d2b3a2f7fd54` |
| ME · Mechanical | `3ccd2857-f77c-817a-b60c-e0c4183a43e7` |
| TS · Tractive System | `3ccd2857-f77c-8184-8440-e437a5fcd697` |
| EL · Electronics | `3ccd2857-f77c-81ed-9650-dcb48424258d` |
| DV · Driverless | `3ccd2857-f77c-81fc-bef4-e5d1ca84d591` |
| Sponsorship | `3ccd2857-f77c-81ce-aaff-cb09a7228260` |
| Marketing & Brand | `3ccd2857-f77c-81c3-8882-d9136722ce3f` |
| Team | `3ccd2857-f77c-810e-8bfe-d500bf7ed1ab` |

Each vertical page contains its department pages, named by the team's Slack codes.

## IFS09 Tasks database

Database: `b170c209-9f57-43ff-95c8-7b2a27c4e41e`
Data source: `collection://eee6826a-9cbc-46e2-a933-150bae16624a`

Replaces the `CAMBIOS_IFS-09.xlsx` workbook. Field names map directly.

| Property | Type | Workbook | Notes |
| --- | --- | --- | --- |
| Task | title | TAREA | |
| Task ID | unique id | ID | Prefix `IFS` |
| Vertical | select | the sheet | Management, Mechanical, Tractive System, Electronics, Driverless |
| Department | multi-select | DEPTS | 20 codes, see below. A task can belong to several departments. |
| Status | select | ESTADO | Not started, In progress, Blocked, Completed |
| Urgency | select | URGENCIA | High, Medium, Low |
| Assignee | person | ASIGNADO | Several people allowed; prefer one owner |
| Progress | number (%) | PROGRESO | |
| Duration | number | DURACIÓN | Days |
| Expected start | date | INICIO PREV. | Set by hand |
| Expected end | date | — | Set by hand, or derived from Duration by `reschedule` |
| Pushed | formula | — | Days a dependency moved this past Expected start. Zero means nothing is holding it up. |
| Planned start | date | INICIO PLAN. | **Written by `reschedule`** |
| Planned end | date | FIN PLAN. | **Written by `reschedule`** |
| Actual end | date | FECHA FIN | Set at completion |
| Deviation | formula | DESVIACIÓN | Days late (+) or early (−). Live, but not chartable |
| Timing | select | — | **Written by `reschedule`**. On track / Due soon / Late / Done on time / Done late / Not scheduled / Done - no end date |
| Days late | number | — | **Written by `reschedule`**. The chartable version of Deviation |
| Depends on | relation | DEPENDE DE | Self-relation, crosses verticals, accepts several predecessors |
| Blocks | relation | — | Reverse side, filled automatically |
| Notes | text | NOTAS | |

**Department codes**: BU · Business Plan, CO · Cost Report, DE · Design (Management);
AE · Aerodynamics, BS · Braking and Steering, CH · Chassis and Structural,
CM · Composites and Manufacturing, CS · Cooling System, SP · Suspension and Dynamics
(Mechanical); BT · Batteries, MI · Motor Inverter, PT · Powertrain, TR · Transmission
(Tractive System); CE · Control Electronics, ES · Electronic Subsystems, TE · Telemetry
(Electronics); DV · Driverless, IN · Integration, PL · Pipeline (Driverless);
TS · Testing (cross-vertical).

Cooling sits in Mechanical, not Tractive System: the team tags radiators and cooling
jackets as mechanical work.

**Views**: `Gantt` (timeline, grouped by Vertical), `Needs attention` (open tasks by
planned end), `By department` (board).

## Milestones database

Data source: `collection://a8a8e437-8cab-4a9f-8217-939a8edf6704`

The season roadmap, a layer above tasks: Milestone, Phase, Status, Target date, Owner,
Subteam, **Capture worthy** (Marketing reads this), Blocked by, Notes.

## Other databases

| Database | Data source |
| --- | --- |
| Team Directory | `collection://2c41aeb0-e418-45e6-850b-dca226b3b5be` |
| Decision Log | `collection://11050f2e-0f14-460c-b19b-8b34a2464b1a` |
| Sponsor Pipeline | `collection://8b8ce753-76d5-46fb-863e-002be7bbd8d8` |
| Sponsor Deliverables | `collection://6b264dc4-aea5-4894-bbe6-b44f9f132953` |
| Content Plan | `collection://a190cd6d-01ad-4cb0-b6f1-a23cc7a6ca8e` |

## Query limitations

Two constraints on the team's free Education plan and on Notion generally:

1. **One data source per query.** Passing more than one entry in `data_source_urls`
   fails with a plan-upgrade error. Query each database separately and combine the
   results yourself. Six small queries are correct; one joined query is not.
2. **Formula properties cannot be read by SQL, or charted.** `Deviation` and `Pushed`
   are formulas: they will not come back in a query, and Notion cannot build a chart or
   a filter on them. This is why `reschedule` also writes the real properties `Timing`
   and `Days late`, which the Dashboard page charts. Compute lateness yourself from
   `Planned end` and `Actual end` when
   a report needs it.

## Conventions

- Dates change in this database first. A date changed in a meeting has not changed.
- Never leave an active task without an assignee.
- Department and Assignee both accept several values, and a task can depend on several
  predecessors. When a task really is shared, tag it that way rather than picking one:
  the scheduler takes the latest predecessor end, so recording only the most obvious
  dependency hides the real constraint.
- `Planned start`, `Planned end`, `Timing` and `Days late` are outputs. Never edit them
  by hand; run
  `reschedule` instead.

## Expected versus Planned

Not a duplication. **Expected** is what the team wants; **Planned** is what the
dependency graph permits.

For a task with no predecessors they are identical. For a task waiting on something,
`Planned start` is later, and the gap is the `Pushed` figure. That gap is the whole
point: it is how a slip three tasks upstream becomes visible here.

`Expected start`, `Duration` and `Expected end` are three views of the same interval.
Enter any two and `reschedule` derives the third. Enter all three inconsistently and it
reports the conflict rather than choosing.
