---
name: brand-system
description: Define, extend, or apply the ISC Formula Student team's brand identity. Use when the user says "what's our brand", "define our brand", "work on the brand system", "update the brand guidelines", "decide the logo/colours/typography", "does this fit our brand", "review this against our brand", or asks about the lion motif rebrand.
---

# ISC brand system

Build and maintain the team's identity, and check work against it.

Read `${CLAUDE_PLUGIN_ROOT}/references/isc-context.md` and
`${CLAUDE_PLUGIN_ROOT}/references/notion-workspace.md` first, then fetch the **Brand
System** page in Notion. That page is canonical and mostly unfilled.

## The governing rule: interview, do not invent

A brand is a set of decisions the team owns. It is not something to generate. If a
section of the Brand System page is unfilled, the job is to help the board decide it
and then record the decision, never to fill the gap with something plausible.

Concretely: do not propose a colour palette, invent a tagline, or write positioning and
present it as theirs. Ask what they already have, what they have rejected, and what
they want to be true, then write down what they say.

The one thing worth offering unprompted is a well-argued option set when the board is
stuck, clearly labelled as options to choose between, with the trade-offs named.

## Mode 1: filling in the brand

Work through unfilled sections one at a time. Do not attempt the whole page in one
pass, because brand decisions made quickly get reversed.

For each section, ask what exists today before asking what it should be. Most teams
have more decided than they realise: there is usually already a logo, already colours
on last year's car, already a way people talk about the team. Surface that first, then
ask what should change.

Useful questions per section:

- **Positioning.** What makes ISC different from the other Spanish FS teams? What
  should a sponsor think after thirty seconds on our LinkedIn? What are we not?
- **Visual identity.** What is the current logo and where does it fall apart? What
  colours are on the car, and are they a brand choice or an accident? What must never
  be done to the mark?
- **The lion motif.** A rebrand using the Comillas coat of arms lion has been proposed.
  Ask where it stands, what the objections were, and record the outcome either way. An
  undecided rebrand is worse than either decision, because it splits output.
- **Photography.** The most-used and least-specified part of any team brand. What does
  a good ISC photo look like: car in what state, what light, what background, what gets
  cropped out? A written answer here changes output more than a colour palette does.
- **Verbal identity.** How do we sound? What do we never say?

Write each answer into the Brand System page as it is settled, in the section it
belongs to, and log the decision with the date in the decisions log. Do not batch the
writes to the end of the conversation.

## Mode 2: checking work against the brand

When given a draft, asset, or link, check it against the Brand System page and report
deviations by severity:

- **Blocking**: factually wrong, unsigned sponsor named or shown, a claimed result we
  did not achieve, a render presented as a built part.
- **Off-brand**: violates a recorded rule on tone, logo use, colour, or naming.
- **Weak**: on brand but vague, adjective-heavy, or missing the technical detail that
  would earn credibility with our audience.

Quote the specific line or element and give a concrete replacement, not a note. If the
relevant rule is not recorded on the Brand System page, say the rule does not exist yet
rather than inventing one, and offer to record it.

## Composing with the other plugins

- `brand-voice` enforces the verbal side across content once the Brand System page
  defines it. It reads guidelines; this page is where they come from.
- `canva` brand-checks designs against a Canva brand kit. Keep the kit and this page in
  agreement; if they diverge, this page wins and the kit is out of date.

## Output

Keep responses short. Brand conversations die from long documents. One section at a
time, decisions recorded as they are made, and a clear statement of what is still
undecided.
