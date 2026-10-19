---
name: close-task
description: Use when the user asks to wrap up a task by reconciling its specs or docs and capturing useful lessons, or when a delegated workflow reaches task closure. In driver mode, ask which documents to update before editing.
license: MIT
metadata:
  author: GigiLoria5
---

# Close a task

Leave the task's documentation consistent with the verified result and identify
small improvements that would make the next task easier. Closing documentation
does not mean declaring the change merged, deployed, or fully verified.

## Establish what to update

Use the current task, linked spec, actual diff, review decisions, and verification
results. For a different session, read the supplied session or handoff rather
than inventing its history. Inspect known documentation links and repository
navigation enough to propose plausible targets without asking the user to find
facts already available to you.

In **driver mode**, ask which specs and relevant documents the user wants updated
and what they want recorded. Offer a short, grounded shortlist when available:
"The product card, technical spec, and export guide look relevant. Which should
I update, and is there anything you want included or left alone?" Wait for that
choice before editing documents. If the request already names the targets and
desired updates, proceed without asking again. Do not broaden that selection
to every document mentioned in the task.

In an **explicitly delegated automatic workflow**, reconcile the task's known
documentation within the delegated scope. Update repository docs and external
cards when those updates are authorized. Ask about an unknown destination or a
material ambiguity; do not select unrelated external pages or create a tracker
just because the task is ending.

## Reconcile with the actual result

Read each selected source before editing. Compare its relevant requirements,
decisions, and plan against what was implemented and verified. Preserve unrelated
content and human edits. Resolve conflicting intent with the user instead of
rewriting an agreed requirement to disguise an implementation gap.

Adapt content to its reader. Product documents describe the problem, resulting
behavior, relevant scope, and remaining product decisions. Technical task cards
can record concise design choices, implementation hooks, relevant rules, and
useful PR links without becoming execution logs or exhaustive design documents.
Use `develop-spec`'s audience guidance when available; this skill
does not require that companion to keep the two audiences distinct. Keep test
transcripts, commit inventories, and implementation handoffs out of product cards.

Prefer updating an existing authoritative document to adding another summary.
Keep requirements, affected plan items, and current behavior consistent. Mark
remaining work and verification limits accurately; distinguish planned,
implemented, tested, merged, and deployed. Preserve status properties unless
updating them is part of the requested closure or established authorized flow.

Use the repository's documentation placement rules. Stable behavior belongs in
its maintained docs, a consequential architectural decision may warrant an ADR,
and provisional observations should remain provisional. Do not document what
the code, tests, or existing docs already make sufficiently clear.

## Propose useful lessons

Read [lessons](references/lessons.md) when reviewing the session's friction,
corrections, or missed checks. Present only supported, reusable improvements.
Tie each proposal to the observed problem, a specific destination or check,
and the smallest useful change. A session may need no new instruction.

Documentation delegation does not also authorize changing shared skills,
`AGENTS.md`, or other steering instructions. Let the user select those concrete
proposals, in either mode, unless their request already explicitly includes the
specific improvement. Apply selected changes through the available authoring
workflow and validate them; do not manufacture a new skill for each correction.

## Verify and report

Check the saved documents and links, using appropriate documentation tooling
where relevant. Report what was updated, what remains unresolved, and proposed
lessons separately from improvements actually applied. If an external write is
unavailable, leave a usable draft and identify it as unsaved.

Complete any already requested commit or PR updates needed for these docs.
Closing the task alone does not add publication, deployment, or messaging actions.
