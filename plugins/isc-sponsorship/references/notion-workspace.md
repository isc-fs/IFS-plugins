# ISC Notion workspace: sponsorship data

All sponsorship state lives in Notion. Treat Notion as the single source of truth.
If it is not in Notion, it did not happen.

Requires the Notion connector to be enabled in the chat. If Notion tools are not
available, say so and stop rather than tracking anything locally.

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

## Sponsor Pipeline database

Data source: `collection://8b8ce753-76d5-46fb-863e-002be7bbd8d8`

One row per company. Key properties:

| Property | Type | Notes |
| --- | --- | --- |
| Company | title | Legal or trading name |
| Stage | select | Identified, Contacted, In conversation, Proposal sent, Negotiating, Signed, Declined, Dormant |
| Tier | select | Title, Main, Official, Associate, Undecided. See the Sponsorship Tiers page. |
| Contribution type | select | Cash, Equipment, Supplies, Software/tools, Mixed |
| Owner | person | The one board member responsible. Never blank on an active prospect. |
| Next action | text | One concrete next step |
| Next action date | date | Drives overdue detection |
| Last contact | date | Most recent real contact |
| Contact name / role / email | text, text, email | |
| Website | url | |
| Value EUR | number (euro) | Target value, or agreed value once Signed |
| Industry | multi-select | |
| Source | select | Cold outreach, Warm intro, Alumni contact, University contact, Inbound, Previous season sponsor, Competition contact |
| Sponsor ID | unique id | Prefix `SPO` |

**Active stages** are: Contacted, In conversation, Proposal sent, Negotiating.
**Closed stages** are: Signed, Declined, Dormant.

## Sponsor Deliverables database

Data source: `collection://6b264dc4-aea5-4894-bbe6-b44f9f132953`

One row per thing ISC owes a signed sponsor. Related to Sponsor Pipeline via the
`Sponsor` relation (synced property on the pipeline side is `Deliverables`).

| Property | Type | Notes |
| --- | --- | --- |
| Deliverable | title | What we owe |
| Sponsor | relation | Links to Sponsor Pipeline |
| Type | select | Logo on car, Logo on suit/kit, Logo on website, Social media post, Event invitation, Season report, Campus/workshop visit, Product feedback, Other |
| Status | select | Not started, In progress, Delivered, Blocked, Not applicable |
| Due date | date | |
| Owner | person | |
| Proof | url | Link to the live post/photo/page. Needed at renewal time. |
| Notes | text | |

## Conventions when writing to Notion

- Never create a duplicate company row. Search the pipeline by company name first.
- Log call and meeting outcomes in the prospect's own page body, not only in properties.
- When a prospect reaches Signed, create its deliverable rows immediately.
- Set `Last contact` whenever outreach actually goes out, not when it is drafted.

## Query limitation: one data source at a time

The team is on Notion's free Education plan, which does **not** allow SQL across
multiple data sources in a single query. Passing more than one entry in
`data_source_urls` fails with a plan-upgrade error.

Always query **one** data source per call and combine the results yourself. Reading
five databases means five separate calls, which is fine. Never attempt a join or a
subquery spanning two data sources.
