# ISC Marketing

Brand identity and season content preparation for the ISC Formula Student Racing Team.
Install alongside `isc-sponsorship` in every board member's Claude account.

## What it does

| Skill | Use it for |
| --- | --- |
| `brand-system` | Deciding and recording what ISC looks and sounds like, and checking work against it |
| `content-formats` | Drafting a specific piece in an established format, per channel |
| `season-content-plan` | Planning the season around capture deadlines, and reviewing what is at risk |

These sit alongside the general `marketing`, `brand-voice` and `canva` plugins rather
than replacing them. Those handle voice enforcement and design production; this one
holds the ISC-specific decisions they draw on.

## Setup

**1. Connect Notion.** Every board member needs it enabled, with access to the
`IFS 09` teamspace.

**2. Fill in the Brand System page.** It ships as structure, not answers. Run
`brand-system` and work through it with the board. Every other skill is weaker until
this exists, and the `brand-voice` and `canva` plugins have nothing to enforce.

## The idea worth keeping

Content is bottlenecked by **capture**, not by writing. The car exists in each state
exactly once. Nobody filmed the layup means that content will never exist.

So the Content Plan is built around capture deadlines and named capture owners, and the
publishing calendar is derived from it. The capture owner is deliberately not the person
doing the engineering that day, because they will be busy and it will not happen.

## The data lives in Notion

Under **Marketing & Brand** in the `IFS 09` teamspace:

- **Brand System**: visual and verbal identity. Canonical.
- **Content Formats**: the repeatable formats and the trap in each one.
- **Content Plan**: the season's content, organised by capture deadline.

Editing those pages changes how the skills behave. No reinstall.

## Maintaining this plugin

Ask Claude to "customize the isc-marketing plugin". Update
`references/isc-context.md` each season with the new car designation, competitions
entered, and any channel changes.
