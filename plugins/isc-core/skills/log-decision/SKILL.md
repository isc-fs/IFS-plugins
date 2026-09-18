---
name: log-decision
description: Record a decision the ISC team has taken, with the reasoning and rejected alternatives. Use when the user says "log this decision", "we decided X", "record that we're going with", "add to the decision log", "why did we decide X", or "what did we decide about Y".
---

# Log a decision

Capture decisions while the reasoning is still in someone's head, and answer questions
about past ones.

Read `${CLAUDE_PLUGIN_ROOT}/references/notion-workspace.md` first.

## Why this matters more than it looks

The car is documented in GitHub. The reasoning is documented nowhere unless somebody
writes it down. When the board turns over in September, the reasoning is what leaves
with them, which is why Formula Student teams re-make the same mistakes every three or
four years.

A decision recorded on the day costs two minutes and is accurate. The same decision
reconstructed in June from memory is thin and often wrong. This skill exists so
handover is a byproduct of working normally.

## Recording a decision

Capture, in this order of importance:

1. **What was decided.** One clear sentence.
2. **Why.** The reasoning. This is the part with value in twelve months. A decision
   with no `Why` is trivia, and if the user does not supply one, ask before writing the
   row rather than saving a decision nobody can evaluate later.
3. **What was rejected, and why not.** The single most useful field for a successor,
   because it stops them rediscovering a dead end. Ask explicitly: what else was on the
   table? Most people do not volunteer this.
4. **Who decided**, the date, the area, and the season.
5. **Revisit when**, if the decision was made under a constraint that could change:
   a budget, a supplier lead time, a rule. Not every decision has one.

Write it to the Decision Log. Set `Status` to `Active`.

## What is worth logging

Anything a successor would be puzzled by, or that took real argument to settle. A
component choice with trade-offs, a supplier, a process change, a sponsorship tier
exception, a rebrand, a scope cut.

Not: routine task completion, or anything already captured as a task or milestone.
If the user tries to log something trivial, say so rather than filling the log with
noise. A decision log nobody reads because it is 90% chaff has failed.

## Superseding

When a new decision replaces an old one, never delete the old row. Set its `Status` to
`Superseded` and reference the new decision in the new row's `Why`. The history of how
thinking changed is often more instructive than the current position.

Same for `Reversed`, when something was tried and abandoned. That is the most valuable
entry in the whole log, and the one people are most tempted to delete out of
embarrassment.

## Answering questions about past decisions

When asked why something is the way it is, query the Decision Log by area and keyword
before answering from general reasoning. If there is a logged decision, quote its `Why`
and `Alternatives rejected` and say when it was taken and by whom.

If there is no logged decision, say so plainly rather than constructing a plausible
rationale. "There is no decision logged for this" is useful information: it means the
reasoning exists only in someone's head, and that is worth fixing now while the person
is still on the team.
