---
name: season-roadmap
description: Build and maintain the ISC season roadmap of milestones. Use when the user says "build the season roadmap", "set the milestones", "what are our deadlines", "update the roadmap", "what has slipped", "are we on track", or "when is X due".
---

# Season roadmap

Maintain the milestone set that the whole team runs on, and report honestly on what has moved.

Read `${CLAUDE_PLUGIN_ROOT}/references/notion-workspace.md` first, then query the
Milestones database.

## Mode 1: building the roadmap

Work backwards from the competitions. Competition dates are fixed and everything else
is negotiable, so they anchor the plan.

Ask for what only the team knows:

- Which competitions are entered, and their dates
- The target date for a rolling car, and for the first driverless run if applicable
- Any hard external dates: scrutineering document deadlines, university deadlines,
  supplier lead times that cannot be compressed

Then work through the phases (Design, Manufacturing, Assembly, Testing, Competition),
proposing milestones for each subteam and asking the user to confirm or correct. Do not
invent dates. Propose a structure and let them fill the dates, or ask what date they
have in mind and record it.

For each milestone, insist on:

- **One named owner.** If the answer is a subteam, ask who specifically. A milestone
  owned by "Driverless" is owned by nobody.
- **A real target date.**
- **The capture question.** Ask whether this milestone produces something that can only
  be filmed or photographed while it happens. If so, tick `Capture worthy`. Marketing
  reads this and cannot recover the moment later. It costs one question and saves the
  season's best content.

## Mode 2: reviewing the roadmap

Query the Milestones database and report:

**Slipped.** Status `Slipped`, or `Target date` in the past and status not `Done`.
Lead with these, most overdue first, with the owner named.

**At risk.** Status `At risk`, with what is in `Blocked by`. Any `At risk` milestone
with an empty `Blocked by` is a problem in itself: flag it, because a risk nobody can
articulate cannot be resolved.

**Silently late.** Target date within fourteen days, status still `Not started`. These
are the ones about to become slips and nobody has said so yet. This is the most
valuable section of the report.

**Unowned.** Any milestone with no owner.

**Downstream impact.** For each slipped or at-risk milestone, name what it affects:
tasks linked to it, other departments that depend on the date (Marketing's content plan,
Sponsorship's proposal claims about the season).

## The honesty rule

The purpose of this skill is to surface bad news early, not to produce a reassuring
summary. A roadmap review that reports everything as fine while four milestones are
two weeks from slipping is worse than no review, because it launders the problem.

State plainly what has moved, who owns it, and what it breaks downstream. If the team
is behind, say the team is behind.

## After a review

Offer to write the review as a dated page under Project Management so the next one can
compare. If a date genuinely needs to change, change it in the Milestones database and
say so explicitly, because that database is the source of truth and other departments
plan from it.
