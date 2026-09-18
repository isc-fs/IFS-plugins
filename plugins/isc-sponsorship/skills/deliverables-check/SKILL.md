---
name: deliverables-check
description: Check what ISC owes its signed sponsors and what has actually been delivered. Use when the user says "what do we owe our sponsors", "check sponsor deliverables", "have we posted about X", "are we behind on anything for sponsors", "prepare for sponsor renewal", or a sponsor has just signed.
---

# Sponsor deliverables

Track and close out what ISC promised signed sponsors. Teams lose renewals far more
often by quietly failing to deliver than by anything that happens during acquisition.

Read `${CLAUDE_PLUGIN_ROOT}/references/notion-workspace.md` first.

## When a sponsor has just signed

Create the deliverable rows immediately, while the terms are fresh in someone's memory.
Ask what was agreed if it is not written down, then create one row per obligation with:

- A concrete deliverable name
- The `Sponsor` relation set
- Type, Owner, and a real Due date

Anchor due dates to real events: before the car is wrapped, before the first
competition, within two weeks of the launch event. A deliverable with no date does not
get done.

## Routine check

Query Sponsor Deliverables and report:

**Overdue.** Status is not `Delivered` and Due date has passed. Group by sponsor.
Lead with these.

**Due soon.** Next 30 days, not yet delivered.

**Blocked.** Anything marked `Blocked`, with what is blocking it. Blocked items with no
explanation in Notes are themselves a problem; flag them.

**Missing proof.** Status is `Delivered` but `Proof` is empty. Without a link, the
delivery cannot be shown to the sponsor at renewal. Chase these.

**Unowned.** No Owner set.

## Renewal preparation

When preparing to renew a sponsor, assemble everything delivered to them across the
season with the proof links, so the conversation opens with evidence of value rather
than a fresh ask. Flag honestly anything that was promised and not delivered. Walking
into a renewal unaware of a broken promise is worse than the broken promise.

## Rules

- Never mark something `Delivered` without a proof link, unless the deliverable is
  physical, such as a logo on the car. For physical deliverables, a photo counts as
  proof and should be linked.
- If a deliverable cannot realistically be met, recommend telling the sponsor early
  rather than letting the date pass silently.
