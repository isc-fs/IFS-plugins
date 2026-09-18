---
name: prospect-research
description: Research a company as a potential ISC Formula Student sponsor and add it to the Notion pipeline. Use when the user says "research this company as a sponsor", "is X a good sponsor target", "add X to the sponsor pipeline", "find sponsor prospects in a given industry", "who should we approach for a specific part or service", or names a company they are considering approaching.
---

# Prospect research

Assess whether a company is worth ISC's time as a sponsor, find the right person to
contact, and record the result in the Notion pipeline.

Read `${CLAUDE_PLUGIN_ROOT}/references/isc-context.md` and
`${CLAUDE_PLUGIN_ROOT}/references/notion-workspace.md` before starting.

## Step 1: Check the pipeline first

Search the Sponsor Pipeline for the company name before any research. If a row already
exists, stop and report its current stage, owner, and last contact instead of creating
a duplicate. Duplicated outreach from two board members is the single most damaging
mistake this department can make.

## Step 2: Research the company

Use web search. Establish:

- What they actually make or sell, in one sentence.
- Headquarters country. This determines outreach language.
- Rough size (employees, revenue band if public). Small local firms and multinationals
  need completely different approaches.
- Whether they already sponsor Formula Student teams, motorsport, or university
  programmes. Existing FS sponsors are far warmer leads; say which teams.
- Whether they recruit engineers, and for what roles.
- Any recent news that gives a reason to reach out now.

## Step 3: Score the fit

Rate each of the four levers from `isc-context.md` as strong, moderate, or weak:

- Recruitment pipeline value
- Technical product fit (would we genuinely use their product on the car?)
- Brand visibility value to them
- CSR / education narrative fit

Then give an overall verdict: **Priority**, **Worth trying**, or **Low value**.
Be honest. Telling the board a prospect is weak saves more time than a polite maybe.
State the single strongest angle in one sentence, because that becomes the hook of the
outreach email.

## Step 4: Find the contact

Look for a named person over a generic inbox: sponsorship, university relations,
marketing, HR/talent, or an engineering manager depending on the strongest angle.
Report the contact's name, role, and email if findable. Do not fabricate an email
address. If only a pattern is inferable, say it is inferred and unverified.

Flag any warm route: ICAI alumni at the company, existing university relationships,
or a previous ISC contact.

## Step 5: Write it to Notion

Create a row in the Sponsor Pipeline with:

- Stage `Identified`
- Tier `Undecided` unless the research suggests a specific level
- Industry, Website, Value EUR (estimate the realistic ask)
- Contact fields if found
- Next action and Next action date, proposed
- Owner left blank unless the user says who owns it, then ask who should

Put the research summary and the fit reasoning in the page body so the next person to
touch this prospect does not repeat the work.

## Output

Report to the user: the verdict, the strongest angle, the contact, any warm route,
and confirmation of what was written to Notion. Keep it under 200 words. If the fit is
weak, lead with that.
