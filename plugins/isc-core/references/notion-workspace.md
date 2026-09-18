# ISC Notion workspace: team-wide pages

Requires the Notion connector enabled in the chat. If Notion tools are unavailable, say
so and stop rather than tracking anything locally.

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
| Sponsorship Tiers | `3ccd2857-f77c-817b-b99f-f7b1b2daeb84` |
| Marketing & Brand | `3ccd2857-f77c-81c3-8882-d9136722ce3f` |
| Brand System | `3ccd2857-f77c-811d-a04f-f710b7d4ed6a` |
| Content Formats | `3ccd2857-f77c-8193-81db-de209bb0cf48` |
| Team | `3ccd2857-f77c-810e-8bfe-d500bf7ed1ab` |
| Handover | `3ccd2857-f77c-81cc-b54b-f65c5b616cf7` |

The five vertical pages each contain their department pages, named by the team's Slack
codes. The IFS09 Tasks database lives under Tasks & Gantt:
`collection://eee6826a-9cbc-46e2-a933-150bae16624a`.

## Team Directory

Data source: `collection://2c41aeb0-e418-45e6-850b-dca226b3b5be`

| Property | Type | Notes |
| --- | --- | --- |
| Name | title | |
| Person | person | Their Notion account, for mentions and assignment |
| Role | text | |
| Vertical | select | Management, Mechanical, Tractive System, Electronics, Driverless, Business, Board |
| Department | multi-select | The 20 department codes, plus Sponsorship and Marketing |
| Status | select | Active, Joining, Leaving this season, Alumni |
| Owns | text | What breaks if this person disappears tomorrow |
| Handover status | select | Not needed, Not started, In progress, Complete |
| Email | email | |
| Joined | date | |

## Decision Log

Data source: `collection://11050f2e-0f14-460c-b19b-8b34a2464b1a`

| Property | Type | Notes |
| --- | --- | --- |
| Decision | title | |
| Date | date | |
| Area | select | Management, Mechanical, Tractive System, Electronics, Driverless, Sponsorship, Marketing, Team & governance |
| Decided by | person | |
| Why | text | The reasoning. The part with value in twelve months. |
| Alternatives rejected | text | What we did not do, and why not |
| Status | select | Active, Superseded, Reversed |
| Season | select | IFS08, IFS09, IFS10 |
| Revisit when | text | The condition for reconsidering, if any |

## Other databases

| Database | Data source |
| --- | --- |
| IFS09 Tasks | `collection://eee6826a-9cbc-46e2-a933-150bae16624a` |
| Milestones | `collection://a8a8e437-8cab-4a9f-8217-939a8edf6704` |
| Sponsor Pipeline | `collection://8b8ce753-76d5-46fb-863e-002be7bbd8d8` |
| Sponsor Deliverables | `collection://6b264dc4-aea5-4894-bbe6-b44f9f132953` |
| Content Plan | `collection://a190cd6d-01ad-4cb0-b6f1-a23cc7a6ca8e` |

## The plugins

| Plugin | Who installs it |
| --- | --- |
| `isc-core` | Everyone |
| `isc-pm` | Whoever runs planning |
| `isc-sponsorship` | Sponsorship |
| `isc-marketing` | Marketing |

Technical development runs on Claude Code against the `isc-fs` GitHub organisation, one
session per repository, with the general `engineering` plugin. There is no ISC-specific
technical plugin.

## Conventions

- Never delete a decision. Mark it `Superseded` or `Reversed`.
- Keep `Owns` current for everyone, not only people who are leaving.
- Mark someone `Leaving this season` as soon as it is known, not on their last day.

## Query limitation: one data source at a time

The team is on Notion's free Education plan, which does **not** allow SQL across
multiple data sources in a single query. Passing more than one entry in
`data_source_urls` fails with a plan-upgrade error.

Always query **one** data source per call and combine the results yourself. Reading
five databases means five separate calls, which is fine. Never attempt a join or a
subquery spanning two data sources.
