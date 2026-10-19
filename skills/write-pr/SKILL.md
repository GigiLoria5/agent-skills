---
name: write-pr
description: Write or revise concise pull request titles and descriptions. Explain the outcome and essential reviewer context, omitting implementation inventories and routine test reports. Use when preparing or opening a PR or revising its wording.
license: MIT
metadata:
  author: GigiLoria5
---

# Write PR

## Defaults

- Write in English unless the user requests another language.
- When asked to open a PR, create it ready for review. Use draft only when explicitly
  requested. Writing wording alone does not authorize pushing, opening, or updating a
  PR.
- Use local domain names and required repository fields. Keep the user's language and
  ready/draft preferences rather than inheriting a conflicting template default; omit
  empty boilerplate.

## Understand, then select

Read the actual diff and enough context to understand the change. Describe the
current PR's contribution, using an earlier PR link for shared stack context.
Rewrite around the final implementation when scope changes.

Open with one short sentence stating what the PR enables or fixes. Add a second
only when it supplies essential context. Attach an available demo, screenshot,
or source card when useful. A clear opening and demo may be the whole description.
Prefer openings such as “Adds…”, “Fixes…”, or “Makes…”. State the capability or
corrected behavior at feature level; do not pack implementation steps into the
opening. Put a consequential mechanism in a note only when it needs explanation.

Include another detail only when it helps the reviewer:

- Understand a meaningful behavior or scope boundary the opening or demo leaves unclear.
- Assess a non-obvious decision, constraint, risk, or tradeoff.
- Take a required review, deployment, or migration action.
- Judge a material verification result or limitation.

The diff already shows moved helpers, shared constants, changed methods, imports,
and API calls. Omit those implementation steps unless their consequence earns a
place above. A technical name can identify the relevant contract; it does not
need a bullet merely because it changed. A refactor can be summarized by the
responsibility or complexity it removes.

## Use the smallest useful shape

These are alternatives, not sections to fill:

- **Focused change:** opening, optional demo/link, and `## Additional Notes` only for
  details that pass the selection above.
- **Several distinct changes:** opening, optional demo, then `## Changes Made` if a
  short index helps review. Group by behavior or responsibility, using past-tense verbs
  such as “Added” or “Fixed.” Add notes only for context that does not belong in the
  list.
- **Problem explanation:** explain the trigger and consequence, then the corrected
  behavior. Use `## Problem` and `## Fix` when the explanation benefits from headings. A
  small fix can remain one paragraph.

For one feature with a good demo, omit `Changes Made` unless its bullets add
review value beyond what the reviewer can see. Several edited files or layers
do not by themselves make this a several-changes PR. Give each point one home:
do not preview the changes list in the opening or repeat it in notes.

## Evidence and voice

Write as a colleague: direct, concrete, and brief. First person fits an actual
judgment, such as “I kept this synchronous because the data is already available.”
Keep a supplied personality; do not invent jokes, promotional benefits, or a
closing summary.

Keep routine successful test runs, file/test counts, lint results, and build
transcripts out of the PR body unless requested or required. Report requested
execution results separately to the user. Include verification when it changes
the risk assessment: a migration exercised against representative data, a
reproduced failure now fixed, or a limitation such as checking only one provider.
Describe the relevant scenario and result instead of using raw test counts as
evidence of quality. Use only observed results, supplied links, and real decisions.

For example, omit “Moved the field lists into shared constants and switched to
bulk inserts” unless that choice has a consequential performance or correctness
reason to explain. Keep a note such as “The migration retains records already
linked to payments, so existing payments keep their contributions.” It explains
a decision and its consequence.

Before returning the text, delete any sentence that merely narrates a code edit,
repeats an earlier point, or reports routine success. Preserve details that help
the reviewer assess the change, even when they are technical. Do not shorten by
replacing a specific useful explanation with a vague claim.

## Title

Use `<type>: <imperative summary>`, with an optional meaningful scope:
`<type>(<scope>): <summary>`. Choose the appropriate Conventional Commit type,
such as `feat`, `fix`, `refactor`, `perf`, `chore`, `build`, `ci`, `docs`, `test`,
`style`, or `revert`. Name the main change; leave rollout locations and secondary
changes to the description. No trailing period.
