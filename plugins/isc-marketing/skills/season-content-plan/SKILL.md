---
name: season-content-plan
description: Plan ISC's content for the season around what has to be captured and when. Use when the user says "plan the season's content", "prepare content for the season", "what do we need to shoot", "build the content calendar", "what content are we missing", "review the content plan", or "we have a milestone coming up".
---

# Season content plan

Build and maintain the season's content plan. The organising principle is capture, not
publishing.

Read `${CLAUDE_PLUGIN_ROOT}/references/isc-context.md` and
`${CLAUDE_PLUGIN_ROOT}/references/notion-workspace.md` first, then fetch the **Content
Formats** page and query the **Content Plan** database.

## Why capture-first

Content for a race team is bottlenecked by capture, not by writing. The car exists in
each state exactly once. If nobody filmed the layup, photographed the loom before it
went into the chassis, or shot the first drive, that content does not exist and cannot
be produced later at any cost.

Writing can be done late. Capture cannot. So the plan is a schedule of capture
obligations with named owners and hard deadlines, and the publishing calendar is
derived from it rather than the other way round.

## Mode 1: building the plan

**Step 1: get the real milestones.** Ask for, or read from the Milestones database under
Tasks & Gantt, the season's build milestones and competition dates. Milestones flagged
`Capture worthy` are the ones PM has already marked as producing something filmable. Without them there is no plan, only
a wishlist. If milestones are not yet defined, say so and stop; this is a dependency on
PM, not something to invent.

**Step 2: for each milestone, ask what is only capturable then.** This is the whole
exercise. For a chassis bonding, a loom build, a first power-up, a first drive, a
shakedown: what will be visible that day and never again? Work milestone by milestone.

**Step 3: turn each into a content item.** Create rows in the Content Plan with:

- The `Milestone` it hangs off
- A `Format` from the Content Formats page
- `Capture needed`: specifically what must be shot, during which piece of work
- `Capture owner`: a named person, who should not be someone doing the engineering
  that day, because they will be busy and will forget
- `Capture deadline`: the last day it is physically possible
- `Status`: `Capture needed`
- `Channels` and a `Publish window`

**Step 4: check coverage.** Report gaps: milestones with no content planned, formats
that never appear across the season, long stretches with nothing publishable, and
competition weekends without an assigned capture owner. A competition with no capture
owner is the single most expensive gap on the calendar.

**Step 5: pull in sponsor obligations.** Query Sponsor Deliverables for anything of
type `Social media post` that is not yet `Delivered`, and make sure each has a
corresponding content item with a real publish window. These are commitments, not
ideas, and they are the ones that cost the team money when missed.

## Mode 2: reviewing the plan

Query the Content Plan and report, in this order:

**Capture at risk.** Items in `Capture needed` whose `Capture deadline` is within
fourteen days or already past. Anything past its deadline is permanently lost;
recommend marking it `Dropped` rather than leaving it to rot and distort the plan.

**Unassigned capture.** Items in `Capture needed` with no `Capture owner`. These will
not happen.

**Stalled.** Items in `Captured` or `Drafted` whose publish window has passed. The
material exists and is going stale.

**Sponsor obligations at risk.** Items linked to a sponsor deliverable whose publish
window is near or past. Escalate these to Sponsorship, because a missed obligation
affects a renewal.

**Coverage gaps.** Upcoming milestones in the next month with no content item.

**Published without proof.** Items marked `Published` with no `Published link`, and
any whose linked sponsor deliverable still has an empty `Proof` field.

## Tone

Be blunt about what will not happen. A plan listing forty content items with no capture
owners is a fiction, and saying so is more useful than summarising it approvingly. Name
the specific items and the specific missing person.

## After a review

Offer to write the review as a dated page under Marketing & Brand so the next review can
compare against it.
