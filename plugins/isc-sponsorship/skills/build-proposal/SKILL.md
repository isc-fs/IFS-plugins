---
name: build-proposal
description: Build a tailored sponsorship proposal or dossier for a specific company for the ISC Formula Student team. Use when the user says "build a proposal for X", "make the sponsorship dossier for X", "they asked for more information", "prepare the deck for this sponsor", or a prospect has moved to the proposal stage.
---

# Sponsorship proposal

Produce a proposal tailored to one company, not a generic dossier with the name
swapped. A tailored proposal is the difference between a reply and silence.

Read `${CLAUDE_PLUGIN_ROOT}/references/isc-context.md`,
`${CLAUDE_PLUGIN_ROOT}/references/sponsorship-tiers.md`, and
`${CLAUDE_PLUGIN_ROOT}/references/notion-workspace.md` first.

## Read the tiers before writing

The four categories are Title (above 30,000 EUR), Main (above 15,000 EUR), Official
(above 7,500 EUR) and Associate (below 7,500 EUR). Software and tooling sponsorship is
always Official regardless of value.

Read the **Sponsorship Tiers** page in Notion first: it is canonical and may have moved
ahead of this plugin's copy. Offer exactly what that page lists and nothing more. Never
invent a benefit, a logo position, or an amount.

## Gather before writing

From the Sponsor Pipeline row:

- The strongest angle from prospect research
- Tier being targeted and Value EUR
- Everything already discussed with them, from the page body

Ask the user for anything the proposal needs that is not recorded and cannot be
researched: current season goals, confirmed competition entries, team size, recent
results, and available imagery. Do not guess at any of these.

## Structure

1. **Cover.** Team name, car designation, season, university. One image if available.
2. **Who we are.** Half a page maximum. Comillas ICAI, Formula Student, what the
   competition actually is, the current car. Assume the reader has never heard of
   Formula Student.
3. **Why this company specifically.** The tailored section, and the one that earns the
   deal. Their product in our car, their recruitment needs against our members, their
   existing motorsport presence. If this section could be sent to any other company,
   it is not finished.
4. **What we are asking for.** The specific tier or the specific parts or services.
5. **What they get.** Benefits for that tier, drawn from the tiers file. Concrete and
   verifiable: placements, sizes, channels, timing.
6. **The season ahead.** Competitions entered, key milestones, timeline.
7. **Contact.** The named board member who owns this relationship, with real contact
   details.

## Rules

- Every number must come from the user, Notion, or verifiable research. Mark any gap
  clearly as `[NEEDS DATA: ...]` rather than filling it with a plausible figure.
- Language follows the company's headquarters: Spanish for Spanish companies, English
  for international.
- Keep it short. Ten focused pages beat thirty padded ones.

## Output

Ask the user which format they need before building: a document, a slide deck, or a
Canva design if the team has brand templates there. Then produce it.

Afterwards, update the pipeline row to `Proposal sent` once it actually goes out, set
`Last contact`, and set a `Next action` and `Next action date` for the follow-up.
Attach or link the proposal in the prospect's Notion page so the rest of the board can
see exactly what was promised.
