---
name: onboard-member
description: Onboard a new member or board member onto the ISC team and its tools. Use when the user says "onboard someone", "we have a new member", "add someone to the team", "set up the new sponsorship lead", "who is on the team", or "update the team directory".
---

# Onboard a member

Get a new person into the team's systems and pointed at the right briefing.

Read `${CLAUDE_PLUGIN_ROOT}/references/notion-workspace.md` first.

## Gather

Ask for what is needed and not obvious: name, university email, department, subteam,
role, and whether they are joining the board or a subteam. Do not guess a department
from a name.

## Create the directory entry

Add them to the Team Directory with `Status` set to `Joining`, and fill `Department`,
`Subteam`, `Role`, `Email` and `Joined`.

Leave `Owns` empty for now, but say clearly that it should be filled within their first
month. It is the answer to what breaks if they disappear, and a directory where only
the departing people have it filled in is a directory that gets written during a crisis.

Set `Person` once they have accepted the Notion invitation, so they can be mentioned and
assigned. If they have not joined yet, note that this is outstanding.

## Produce their setup list

Give them a short, ordered list, not a document:

1. Accept the Notion invitation to the `IFS 09` teamspace.
2. Connect Notion in their Claude account, and Gmail if their role sends email.
3. Install `isc-core`, plus their department plugin: `isc-pm`, `isc-sponsorship`, or
   `isc-marketing`. Technical members install the general `engineering` plugin and work
   through Claude Code against the `isc-fs` GitHub organisation instead.
4. Read their department page. That is the briefing; there is no separate onboarding
   document.

## Point them at the right reading

Name the specific pages for their department rather than telling them to explore:

- **Sponsorship**: the Sponsorship page and Sponsorship Tiers
- **Marketing**: Marketing & Brand, Brand System, Content Formats
- **Project Management**: Tasks & Gantt, and the Milestones database
- **Technical**: their vertical page (EL · Electronics or DV · Driverless) and the relevant repository

Everyone reads the Team page for the team-wide rules, and the Handover page so they
understand why the Decision Log exists before they are asked to use it.

## First month

Suggest one concrete thing for their first month beyond their actual work: fill in their
`Owns` field, and log one decision they were part of in the Decision Log. Both are
habits that are much easier to start early than to impose in June.

## Listing the team

When asked who is on the team, query the Team Directory and group by department. Flag
anyone `Leaving this season` whose `Handover status` is `Not started`, because that is
the situation that costs the team most and it is invisible unless someone looks.
