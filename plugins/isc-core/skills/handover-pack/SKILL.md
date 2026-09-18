---
name: handover-pack
description: Produce a handover pack for someone leaving the ISC team, or check the team's handover readiness. Use when the user says "build a handover pack", "someone is leaving", "prepare the handover", "end of season handover", "what happens when X leaves", or "are we ready for the board turnover".
---

# Handover pack

Assemble what a departing member knows into something their successor can actually use.

Read `${CLAUDE_PLUGIN_ROOT}/references/notion-workspace.md` and the **Handover** page
first.

## Mode 1: one person's handover pack

Given a name, assemble from Notion:

**What they own.** Their `Owns` field from the Team Directory, plus everything actually
assigned to them: milestones, tasks, sponsor prospects, content items. The assigned
items are often a longer list than the `Owns` field, and the gap between the two is
itself worth reporting, because it is the part nobody thought to write down.

**Decisions they made.** Query the Decision Log filtered to them. This is the reasoning
their successor most needs and cannot reconstruct.

**Relationships they hold.** Sponsor prospects where they are `Owner`, with the contact
name and the state of the conversation. Named external contacts anywhere in their pages.
A sponsor relationship handed over as a company name and nothing else is not handed over.

**What is in flight.** Their open tasks and at-risk milestones, with the next action for
each. Not a list of everything, but what a successor would be blindsided by.

**Access they control.** This is the one Notion cannot answer, and the one that hurts
most. Ask directly: accounts, repositories, domains, subscriptions, shared logins,
workshop keys, anything where they are the only holder. Nobody notices until the person
is unreachable. Always ask, even if it feels tedious.

## Producing the document

Write it for the successor, not for the archive. Structure:

1. What you now own, in priority order
2. What is in flight and what the next step is for each
3. The relationships you inherit, and the state of each
4. Decisions already taken that you should not re-litigate, with the reasoning
5. What was tried and rejected, so you do not repeat it
6. Access you need transferred, and from whom
7. What is undocumented and only in the outgoing person's head

Section 7 is the honest one. There is always something. Ask the outgoing person directly
what they know that is not written anywhere, and write down whatever they say, however
rough. A messy note is worth more than a gap.

Write it as a page under Handover, then set their `Handover status` to `In progress`,
and `Complete` only once the successor has read it with the outgoing person still
reachable. A handover document nobody read is the same as no handover.

## Mode 2: team handover readiness

Query the Team Directory and report:

**Leaving with handover not started.** Anyone `Leaving this season` whose
`Handover status` is `Not started`. Lead with this. If a departure is inside a month,
say so plainly: it is the emergency case.

**Single points of failure.** People whose `Owns` names something no one else touches.
Ask what happens if they are unavailable for a month. Being told this in November is
useful; discovering it in June is not.

**Empty `Owns`.** Directory entries where nobody has written what the person owns. These
are unhandoverable by definition, because nobody knows what would be lost.

**Undocumented reasoning.** Areas with active milestones or subsystems but few or no
Decision Log entries this season. Those decisions are being made and not recorded, which
means they leave with whoever made them.

## Tone

Be direct about what will be lost. The failure mode of handover season is polite
optimism: everyone assumes the knowledge will transfer somehow, and in September it has
not. Naming exactly which subsystem has one owner and no logged decisions is more useful
than a reassuring summary, and it is still actionable while the person is on the team.
