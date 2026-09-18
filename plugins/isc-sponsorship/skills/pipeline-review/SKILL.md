---
name: pipeline-review
description: Review the ISC sponsor pipeline and produce a board-ready status report with stalled prospects, overdue actions, and priorities. Use when the user says "review the sponsor pipeline", "what's the state of sponsorship", "prep for the board meeting", "who hasn't been contacted", "what's overdue", or "weekly sponsorship update".
---

# Pipeline review

Turn the Sponsor Pipeline into a short, honest status report the board can act on in a
meeting. This is the department's recurring heartbeat: run it weekly.

Read `${CLAUDE_PLUGIN_ROOT}/references/notion-workspace.md` first.

## Pull the data

Query the Sponsor Pipeline. Compute against today's date.

## Report structure

**1. Headline numbers**

- Total prospects by stage
- Committed value: sum of `Value EUR` where Stage is `Signed`
- Weighted pipeline: sum of `Value EUR` across active stages, discounted by stage
  (In conversation ~25%, Proposal sent ~50%, Negotiating ~75%). State the weighting
  used so nobody mistakes it for a forecast.

**2. Needs action now**

Anything where `Next action date` is today or in the past. List company, owner, and the
overdue action, sorted by how late it is. This is the most useful section of the
report; put it high.

**3. Going stale**

Active prospects where `Last contact` is more than 21 days ago, or where `Next action`
is empty. An active prospect with no next action is a leak, not a lead.

**4. Unowned**

Any prospect in an active stage with no `Owner`. These belong to nobody and will be
dropped. Flag every one.

**5. Movement since last review**

Stage changes, new prospects, and closes. If no previous review is available, say so
rather than implying nothing moved.

**6. Recommended focus**

Three to five specific actions for the coming week, each with a named owner drawn from
the pipeline. Not "follow up with sponsors" but "Ana: send the second follow-up to
Company X, quiet since 12 Aug".

## Tone

Be blunt about problems. A review that reports a healthy pipeline when four prospects
are unowned and six are stale is worse than no review. Name what is broken, then say
what to do about it.

## After the review

Offer to write the review as a dated page in the Sponsorship section of Notion so the
board has a history and the next review can compare against it.
