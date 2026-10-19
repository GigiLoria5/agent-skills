---
name: develop-spec
description: Develop a feature or change through conversation, then draft or update its spec for a technical or product audience. Use when requirements need discussion or an existing spec needs refining; ordinary implementation and simple page edits do not need this workflow.
license: MIT
metadata:
  author: GigiLoria5
---

# Develop a spec

Help the user think through the work as a colleague. Build on what they already
know and contribute useful reasoning, examples, and alternatives along the way.
The conversation should make the problem clearer and the tradeoffs easier to judge.

## Converse

Read a supplied card or spec and use the current conversation before asking for
context. Look up facts in available sources or code; ask the user for decisions,
preferences, and information you cannot retrieve. State material uncertainty when
the relevant source is inaccessible.

Respond to the user's point before moving to the next uncertainty. Usually ask
one focused question, tied to what was just discussed. Explain a recommendation
when it helps them decide. Follow their corrections and changes of direction.
Answer side questions before resuming the spec discussion.

Use ordinary prose. Avoid questionnaire rounds, mandatory question counts,
confidence percentages, or a fixed Q/GUESS format. A concrete example can clarify
a tradeoff faster than another abstract question. Challenge assumptions that
affect the outcome, without making the user defend every detail.

Establish who benefits, the problem, desired behavior, meaningful constraints,
and what success looks like to the extent this change needs them. Make boundaries
clear when scope could drift. Reuse settled decisions instead of asking for them
again. A small change can be ready quickly; a significant unresolved decision is
a reason to keep talking, not a reason to invent an answer.

## Move from conversation to a draft

When the behavior and consequential decisions are clear enough to document,
briefly reflect the agreed outcome and any remaining uncertainty. End by offering
to draft or update the card in Notion or the user's chosen destination.

Ask which audience and level of detail they want, unless already specified:
personal/technical reference, product/business, or both. For example:
"Ready to update the card? Should this be a technical reference, a product brief,
or two linked versions?" Do not require another approval if the user already
asked you to save an agreed draft to a known destination for a known audience.

Audience is a per-destination choice, separate from language. Confirm an unclear
destination before writing. If there are two versions, establish which page gets
each; keep their requirements consistent while adapting what each reader needs.
Ask only for missing choices, and retain the answers through later updates.

Read [audience guidance](references/audience.md) before drafting or updating.
Show the proposed text before an external write when the user has not already
authorized that write. Keep the question about saving concrete: identify the
target and include or point to the draft they would be approving.

## Plan when the discussion reaches implementation

When an implementation plan is requested or part of the agreed spec, inspect
relevant code and repository guidance first. Read
[delivery planning](references/delivery-planning.md). Append the agreed plan to
the technical reference, preserving decisions and scope above it. For a product
card, keep delivery information at the level of visible outcomes and link to the
technical plan if that linked version exists and the link is wanted.

Spec development does not itself start implementation, create branches or tasks,
commit code, or open a PR. Continue into those actions when the user's request
also authorizes them; otherwise leave the draft or saved spec ready to use.

## Save and maintain

Use the available connector or file tools for the chosen destination. Read the
current page before editing, preserve unrelated content and properties, and
change only the requested sections. An existing technical section does not make
a product card technical; follow the audience choice for the current update.

When requirements change, revise the relevant requirement and its affected plan
items together. Preserve the distinction between decisions, proposals, and
verified implementation. Keep engineering progress and test logs in the technical
reference or PR, rather than accumulating them in the product card.

Verify the saved result and return its link. If access is missing, leave a usable
draft and state that it remains unsaved.
