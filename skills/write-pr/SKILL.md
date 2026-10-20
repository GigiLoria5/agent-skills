---
name: write-pr
description:
  Write or revise concise pull request titles and descriptions. Explain the
  outcome and essential reviewer context, omitting implementation inventories
  and routine test reports. Use when preparing or opening a PR or revising its
  wording.
license: MIT
metadata:
  author: GigiLoria5
---

# Write PR

## Defaults

- Write in English unless the user requests another language.
- When asked to open a PR, create it ready for review. Use draft only when
  explicitly requested. Writing wording alone does not authorize pushing,
  opening, or updating a PR.
- Use local domain names and required repository fields. Keep the user's
  language and ready/draft preferences rather than inheriting a conflicting
  template default; omit empty boilerplate.

## Understand, then select

Read the actual diff and enough context to understand the change. Describe the
current PR's contribution, using an earlier PR link for shared stack context.
Rewrite around the final implementation when scope changes.

For stacked delivery, follow the stack checks below before creating a PR.

Open with one short sentence stating what the PR enables or fixes. Add a second
only when it supplies essential context. Attach an available demo, screenshot,
or source card when useful. A clear opening and demo may be the whole
description. Prefer openings such as “Adds…”, “Fixes…”, or “Makes…”. State the
capability or corrected behavior at feature level; do not pack implementation
steps into the opening. Put a consequential mechanism in a note only when it
needs explanation.

Include another detail only when it helps the reviewer:

- Understand a meaningful behavior or scope boundary the opening or demo leaves
  unclear.
- Assess a non-obvious decision, constraint, risk, or tradeoff.
- Take a required review, deployment, or migration action.
- Assess a specific unresolved risk using evidence or a verification limitation.

The diff already shows moved helpers, shared constants, changed methods,
imports, and API calls. Omit those implementation steps unless their consequence
earns a place above. A technical name can identify the relevant contract; it
does not need a bullet merely because it changed. A refactor can be summarized
by the responsibility or complexity it removes.

Give each bullet one point. Keep the rule, consequence, decision, or accepted
risk; remove the surrounding implementation story. Endpoint paths, HTTP codes,
exact error text, roles, and internal lifecycle details earn space only when
essential to evaluating this PR. Use plain wording without weakening a precise
contract. A longer risk explanation can earn its space; length alone is not the
selection rule.

## Use the smallest useful shape

These are alternatives, not sections to fill:

- **Focused change:** opening, optional demo/link, and `## Additional Notes`
  only for details that pass the selection above.
- **Several distinct changes:** opening, optional demo, then `## Changes Made`
  if a short index helps review. Group by behavior or responsibility, using
  past-tense verbs such as “Added” or “Fixed.” Add notes only for context that
  does not belong in the list.
- **Problem explanation:** explain the trigger and consequence, then the
  corrected behavior. Use `## Problem` and `## Fix` when the explanation
  benefits from headings. A small fix can remain one paragraph.

For one feature with a good demo, omit `Changes Made` unless its bullets add
review value beyond what the reviewer can see. Several edited files or layers do
not by themselves make this a several-changes PR. Give each point one home: do
not preview the changes list in the opening or repeat it in notes.

## Evidence and voice

Write as a colleague: direct, concrete, and brief. First person fits an actual
judgment, such as “I kept this synchronous because the data is already
available.” Keep a supplied personality; do not invent jokes, promotional
benefits, or a closing summary.

Report verification in the completion message by default. Tests, manual checks,
representative-data replays, and detailed reproductions do not automatically
belong in the PR. Include evidence only when the reviewer needs it to assess a
specific unresolved concern, or when requested or required. State that concern
and the relevant result or limit concisely; link supporting evidence when
useful. Use only observed results, supplied links, and real decisions.

This fictional example calibrates detail selection, not a required PR shape.
After an opening such as “Allows removing a connected integration,” these notes
are too detailed:

> - `IntegrationDeleteView` checks the workspace-admin role and calls
>   `SyncService.has_active_runs()`, returning 409 with “Sync in progress” if a
>   job is running. It then deletes the credential row but preserves imported
>   data.
> - The discovery job now skips disconnected integrations; the connection
>   handler creates them again only after an explicit connection request.
> - Accepted risk: the dashboard caches connection status for five minutes, so a
>   removed integration may still appear connected during that window. Sync
>   requests read current state and are refused.
> - Replayed a sample sync against a database snapshot and manually checked the
>   confirmation dialog and error banner; all checks passed.

Keep only the reader-relevant points:

> - Removal is blocked while a sync is running.
> - Imported data is kept; saved credentials are deleted.
> - Removed integrations return only after an explicit connection request.
> - **Accepted risk:** connection status can remain stale for five minutes;
>   removed integrations cannot sync during that window.

Before returning the text, delete any sentence that merely narrates a code edit,
repeats an earlier point, or reports routine success. Preserve details that help
the reviewer assess the change, even when they are technical. Do not shorten by
replacing a specific useful explanation with a vague claim.

## Deliver within the existing stack

When the branch belongs to a stack or the user requests stacked delivery, read
the installed `gh-stack` guidance and inspect the existing local and remote
stack before creating a PR. Identify the intended stack, branch order,
parent/base, and any existing PRs. Reuse that structure rather than opening an
independent PR.

For an already tracked stack, use stack-aware submission within the authorized
delivery. With current `gh-stack`, noninteractive ready-for-review submission is
`gh stack submit --auto --open`; use its draft behavior when requested. If the
branches or PRs were created outside the helper, adopt or link them to the
intended stack using its documented commands. For example,
`gh stack link <existing-stack-number> <branch-or-pr>` appends to an existing
stack. Check command scope first: do not submit unrelated branches or create a
competing stack.

Verify both correct bases and actual server-side membership and order, using the
remote stack result and available GitHub/CLI inspection. A local branch chain or
correctly based PR alone does not prove a GitHub stack exists. If stacked PRs
are unavailable or linking fails, report the specific limit and what was created
instead of claiming stacked delivery succeeded.

Treat generated titles and bodies as initial text. After submission or linking,
apply this skill to each requested PR's actual contribution, preserve required
stack links or helper metadata, and verify the saved wording. Recheck after
resubmission in case it was regenerated. A wording-only request does not
authorize pushing, opening, linking, or submitting PRs.

## Title

Use `<type>: <imperative summary>`, with an optional meaningful scope:
`<type>(<scope>): <summary>`. Choose the appropriate Conventional Commit type,
such as `feat`, `fix`, `refactor`, `perf`, `chore`, `build`, `ci`, `docs`,
`test`, `style`, or `revert`. Name the main change; leave rollout locations and
secondary changes to the description. No trailing period.
