# ISC Notion workspace: marketing pages

All marketing state lives in Notion. Requires the Notion connector to be enabled in the
chat. If Notion tools are unavailable, say so and stop rather than tracking anything
locally.

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

## Content Plan database

Data source: `collection://a190cd6d-01ad-4cb0-b6f1-a23cc7a6ca8e`

| Property | Type | Notes |
| --- | --- | --- |
| Item | title | |
| Format | select | Build update, Technical deep-dive, Member spotlight, Process short, Competition coverage, Sponsor feature, Season recap, Other |
| Status | select | Idea, Capture needed, Captured, Drafted, Scheduled, Published, Dropped |
| Channels | multi-select | Instagram, LinkedIn, TikTok |
| Milestone | text | The build or season milestone this hangs off |
| Capture needed | text | Exactly what must be shot, during which work |
| Capture owner | person | Who holds the camera |
| Capture deadline | date | Last day this can physically be captured |
| Publish window | date | |
| Owner | person | Who turns material into the finished piece |
| Sponsor obligation | relation | Links to Sponsor Deliverables |
| Published link | url | Proof, and the source for sponsor deliverable proof |

**The important distinction**: `Capture deadline` is a hard physical constraint,
`Publish window` is soft. An item in `Capture needed` past its capture deadline is
permanently lost and should be marked `Dropped` rather than left rotting.

## Sponsor Deliverables database

Data source: `collection://6b264dc4-aea5-4894-bbe6-b44f9f132953`

Owned by Sponsorship. Marketing reads it to find posts owed to signed sponsors, and
writes the `Proof` URL when one is published. Never mark a deliverable `Delivered`
without a proof link.

## Conventions

- Read the Brand System page before producing any public asset. It is canonical.
- When a content item is published, set `Published link` the same day. If it satisfies
  a sponsor obligation, copy that URL into the linked deliverable's `Proof` field too.
- Never create a content item without a `Milestone`. If there is no milestone, question
  whether the piece should exist.

## Query limitation: one data source at a time

The team is on Notion's free Education plan, which does **not** allow SQL across
multiple data sources in a single query. Passing more than one entry in
`data_source_urls` fails with a plan-upgrade error.

Always query **one** data source per call and combine the results yourself. Reading
five databases means five separate calls, which is fine. Never attempt a join or a
subquery spanning two data sources.
