---
name: content-formats
description: Draft a specific piece of ISC content in one of the team's established formats. Use when the user says "draft a build update", "write a post about X", "make a member spotlight", "we need content for this milestone", "write the competition recap", "sponsor feature post", or asks for a caption or copy for Instagram, LinkedIn or TikTok.
---

# ISC content formats

Draft one piece of content, in an established format, on brand, for a named channel.

Read `${CLAUDE_PLUGIN_ROOT}/references/isc-context.md` and
`${CLAUDE_PLUGIN_ROOT}/references/notion-workspace.md` first, then fetch the **Brand
System** and **Content Formats** pages in Notion. Content Formats defines the formats
and their traps; Brand System defines tone and rules.

## Before drafting: establish the substance

The failure mode is producing fluent copy about nothing. Every format has a factual
core, and without it the piece should not be written.

Ask for whatever is missing:

- **Build update**: which subsystem, what milestone was actually reached, what was hard
  about it, and is there a photo of the real part
- **Technical deep-dive**: which decision, what the alternatives were, what data or
  reasoning settled it, who made it
- **Member spotlight**: who, what they own, why they joined, in their words
- **Process short**: what work is being filmed and when it happens
- **Competition coverage**: which event, which day, what actually happened
- **Sponsor feature**: which sponsor, what they contributed, where it is used on the
  car, and confirmation from Sponsorship that the agreement is signed
- **Season recap**: real results, including what went badly

If the substance is not available, say what is missing and stop. Do not write around
the gap. A build update with no specific milestone is filler, and filler is worse than
silence because it trains the audience to scroll past.

## Channel adaptation

The same substance is written differently per channel. Never post identical copy
across all three.

- **LinkedIn**: the technical audience. Lead with the engineering problem, not the
  announcement. Length is fine if every paragraph earns it. This is where sponsors and
  their engineers actually read us.
- **Instagram**: image-led. The caption supports the photo rather than replacing it.
  Short, concrete, one idea.
- **TikTok**: the hook is the first two seconds of the video, not the caption. Provide
  the on-screen text and the shot sequence, not just a caption.

## Hard rules

- Never invent a statistic, a lap time, a placement, a follower count, or a quote. If a
  number would strengthen the piece and nobody has given it, mark it `[NEEDS DATA: ...]`
  and say so in the response.
- Never name or show a sponsor whose agreement is not signed. Check the Sponsor Pipeline
  stage if unsure.
- Never present a render as a built part. If the image is CAD, the copy says so.
- Never spin a bad result.
- Attribute quotes to the person who actually said them, and get their words rather
  than writing words for them.

## After drafting

Offer to create or update the item in the **Content Plan** database with its format,
channels, milestone, and owner. If the piece needs material that does not exist yet,
set `Status` to `Capture needed` and fill in `Capture needed`, `Capture owner` and
`Capture deadline`, because that is the part that gets lost.

If the piece satisfies something owed to a signed sponsor, link the `Sponsor obligation`
relation. Once it is published, set `Published link` and copy the same URL into the
sponsor deliverable's `Proof` field.
