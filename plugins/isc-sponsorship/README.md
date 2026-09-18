# ISC Sponsorship

Sponsorship workflows for the ISC Formula Student Racing Team (Universidad Pontificia
Comillas, ICAI). Install this in every board member's Claude account so the whole
sponsorship department works the same way against the same data.

## What it does

| Skill | Use it for |
| --- | --- |
| `prospect-research` | Assess a company as a sponsor target, find the contact, add it to the pipeline |
| `draft-outreach` | First-contact and follow-up emails, in the right language |
| `build-proposal` | A proposal tailored to one company, not a generic dossier |
| `pipeline-review` | The weekly board-ready status report: overdue, stale, unowned |
| `deliverables-check` | What we owe signed sponsors, and whether we actually delivered it |

## Setup

**1. Connect Notion.** Every board member needs the Notion connector enabled and access
to the `IFS 09` teamspace. Without it, none of these skills can read or write the
pipeline. Invite the whole board to the workspace before rolling this out.

**2. Connect Gmail** if you want outreach emails created as drafts directly.

**3. Nothing else.** The real sponsorship tiers are already loaded, and the canonical
copy lives on the Sponsorship Tiers page in Notion. Edit that page when they change;
the skills read it.

## The data lives in Notion

Everything sits directly in the `IFS 09` teamspace.

- **Sponsorship**: this department's AI workflow, working agreements, stage definitions
- **Sponsorship Tiers**: the four categories and what each one gets. Canonical.
- **Sponsor Pipeline**: one row per company, one owner each
- **Sponsor Deliverables**: what we owe signed sponsors, and the proof we delivered it

Editing those pages changes how the skills behave. That is the intended way to evolve
the process: no reinstall, no redistribution.

If it is not in Notion, it did not happen. The skills all read and write there so that
four people can work the same pipeline without colliding.

## Working agreements

- One `Owner` per prospect. Two board members contacting the same company independently
  is the worst failure mode this department has.
- Update `Stage` the same day it moves.
- Every active prospect has a `Next action` and a `Next action date`.
- Log call outcomes in the prospect's Notion page, not in WhatsApp.
- Create deliverable rows the moment a sponsor signs.

## Maintaining this plugin

Ask Claude to customize it: "customize the isc-sponsorship plugin". Update
`references/isc-context.md` at the start of each season with the new car designation,
competitions entered, and season goals.
