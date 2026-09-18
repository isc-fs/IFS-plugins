---
name: draft-outreach
description: Draft first-contact or follow-up emails to potential ISC Formula Student sponsors. Use when the user says "write an outreach email to X", "draft the first email to this sponsor", "follow up with X", "chase the companies that went quiet", "we haven't heard back from X", or asks for sponsor outreach copy.
---

# Sponsor outreach

Draft outreach emails that a busy engineer or marketing manager will actually read,
and keep the pipeline honest about what was sent.

Read `${CLAUDE_PLUGIN_ROOT}/references/isc-context.md` and
`${CLAUDE_PLUGIN_ROOT}/references/notion-workspace.md` first.

## Before drafting

Pull the company's row from the Sponsor Pipeline. The draft depends on:

- **Stage.** First contact reads completely differently from a fourth follow-up.
- **Last contact date.** Reference the elapsed time honestly if chasing.
- **The strongest angle** recorded during prospect research. Lead with it.
- **Headquarters country**, which sets the language.

If the company is not in the pipeline, run prospect research first. Never send outreach
to a company nobody has assessed.

## First contact

Hard limit: 200 words in the body. Structure:

1. **One line on who we are.** ISC, Formula Student, Comillas ICAI, electric prototype.
   No history, no mission statement.
2. **The specific reason for contacting them.** Their product, their recruitment needs,
   their existing motorsport involvement. This sentence proves the email is not a mass
   mailing, and it is the only reason they keep reading.
3. **What we are asking for**, concretely. Cash tier, specific parts, software licences,
   manufacturing time. Vague asks get vague answers.
4. **What they get**, in one or two lines, drawn from the agreed tiers.
5. **A low-friction call to action.** A 20-minute call, or a yes/no on whether it is
   worth sending the full dossier. Never "let us know your thoughts".

Subject line: specific and factual. "Formula Student team at ICAI: <specific ask>"
beats anything clever.

## Follow-ups

- Never resend the same email with "just checking in" on top. Add something new: a
  milestone reached, a test completed, a competition result, a new render.
- Reference the previous email once, briefly, then move on.
- Second follow-up should make it easy to say no: "If this is not a fit this season,
  just say so and I will stop chasing." This recovers more replies than pressure and
  keeps the relationship intact for next year.
- After three unanswered contacts, recommend moving the prospect to `Dormant` rather
  than continuing.

## Language

Spanish for Spanish-headquartered companies, English for international. Check the
company's headquarters before choosing. Never mix languages in one email.

## Rules

- Never invent statistics, follower counts, past results, or existing sponsor names.
  If a claim needs a number nobody has given you, leave a clearly marked gap and tell
  the user what to fill in.
- Never promise benefits outside the agreed tiers in
  `${CLAUDE_PLUGIN_ROOT}/references/sponsorship-tiers.md`. If that file is still
  unfilled, say so and ask before promising anything specific.

## After drafting

Offer to create the email as a Gmail draft rather than sending it. A human sends it.

Once the user confirms it has gone out, update the pipeline row: set `Last contact` to
today, move `Stage` to `Contacted` if it was `Identified`, and set a concrete
`Next action` and `Next action date` for the follow-up.
