---
name: write-pr
description: "Write or revise pull request titles and descriptions, including when preparing or opening a PR, using the user's concise voice and three adaptive formats."
license: MIT
metadata:
  author: GigiLoria5
---

# Write PR

## Defaults

- Write titles and descriptions in English unless the user explicitly requests Italian.
- When asked to open a PR, create it ready for review. Use draft only when explicitly requested. Writing a title and description alone does not authorize pushing, opening, or updating a PR.
- Apply across repositories. Use local domain names and relevant required fields without inheriting boilerplate, empty sections, or a different language or draft default from a repository template.

## Ground the description

Use the actual diff, the user's context, and enough surrounding code to understand the behavior. Describe the current PR's contribution; for stacked PRs, refer to the relevant earlier PR for shared context instead of repeating the whole feature story. Rewrite an existing description around the final implementation when its scope changes.

Choose the smallest format below that makes the change understandable. The user may select one. Do not fill missing slots with guesses: demos, source tickets/issues, measurements, tests run, and release actions must come from available evidence.

## Title

Default to `<type>: <summary>`. Use `<type>(<scope>): <summary>` only when the scope adds useful context that the summary does not already convey.

- Choose the conventional-commit type that matches the change: `feat`, `fix`, `refactor`, `perf`, `chore`, `build`, `ci`, `docs`, `test`, `style`, or `revert`.
- Keep scope optional. When useful, name the affected domain or shared area using established repository naming.
- Keep the title compact: an imperative verb and the main change. Leave secondary changes, implementation details, and rollout locations to the description. Do not end the title with a period.

For example, prefer `feat: add opt-in multi-column sorting` over `feat(data-table): add opt-in multi-column sorting and enable it in the report table`.

## Formats

These are ordered building blocks, not forms with compulsory fields. Use `Changes Made` wherever a changes-list heading is needed.

### 1. Focused change

For one coherent feature, API, UI action, or improvement:

1. A brief opening stating the resulting capability or behavior: one sentence by default, at most two for a larger change.
2. A demo, screenshots, or source ticket/issue if useful and available.
3. Optional `## Additional Notes` for decisions, non-obvious rules, constraints, or intentionally deferred work.

A straightforward maintenance change can be one sentence or a few bullets with no headings. Do not manufacture notes to make it look substantial.

### 2. Several related changes

For multiple improvements that benefit from an index:

1. One sentence stating the combined outcome, or at most two for a larger change when essential context helps. Leave interaction details, persistence rules, rollout scope, and mechanisms to the sections below.
2. Optional demo or screenshots.
3. `## Changes Made` with bullets or numbered items grouped by meaningful behavior or responsibility, not by code edit. Combine related implementation steps into one change. Start each item with a verb in the past simple, such as “Added…”, “Improved…”, or “Fixed…”.
4. Optional `## Additional Notes` for reasoning and caveats.

Use topic subheadings or individual commit links only when they make a larger change easier to review. Avoid a list of modified files, classes, or methods.

### 3. Problem explanation

For a fix whose cause or consequences need explanation:

1. Source ticket/issue or a concise statement of the observed failure.
2. `## Context` and/or `## Problem`, with the trigger, consequence, and cause. Combine them when separate sections would repeat information. This can serve as the opening.
3. `## Fix` explaining the corrected behavior and any essential mechanism.
4. Optional reproduction, before/after screenshots, or verification evidence.
5. Optional `## Additional Notes` for decisions and constraints.

Use consistent before/after labels when comparing visuals. A small fix can use the focused format instead.

## Voice and information value

Sound like a colleague explaining a change to its reviewer: direct, specific, and candid. Openings such as “Adds…”, “Improves…”, or “Fixes…” work when they describe a real outcome. The opening answers what the PR enables or fixes at a glance. Use one sentence by default and at most two for larger changes; use the second only for essential context. When a changes list follows, do not preview its details in the opening.

Use first person for an actual judgment: “I kept this synchronous because the data is already available.” Explain why an alternative was rejected, a boundary matters, or complexity was deferred. Invite feedback only on a concrete unresolved question. Occasional humor can remain when supplied by the user; do not invent jokes, emojis, or a personality.

Every additional sentence should help the reviewer understand intent, assess correctness, or act on the change. Keep business meaning, surprising edge cases, tradeoffs, and operational consequences. Omit information already obvious from the diff unless it is needed to explain the outcome. A note such as “Added tests and updated the serializer” offers little; a note explaining why completed records retain their original owner does.

Give each level of detail one home. The opening states the overall outcome; `Changes Made` summarizes the main behavior changes and rollout scope; `Additional Notes` explains decisions, integration requirements, and compatibility caveats. Keep technical mechanisms in notes when they explain a real constraint. Avoid repeating the same detail across sections. Remove generic benefits, promotional adjectives, filler transitions, routine implementation inventories, and closing summaries.

For example, open with “Adds multi-column sorting to `DataTable`, allowing users to sort rows by multiple fields.” In `Changes Made`, combine sort-field aggregation, ascending → descending → removed cycling, and visible priorities into one bullet about the opt-in multi-sort behavior. Give URL persistence and the table rollout their own bullets. Keep element-plus limitations and the required column `property` in `Additional Notes`, where they explain an integration constraint. Do not give every helper or method its own bullet.

Dependencies, release actions, roadmaps, and concrete test cases are conditional additions. Mention verification when it supports an important claim or reveals a limit, distinguishing checks actually run from tests merely added. Do not automatically append a testing checklist or recreate a roadmap for each PR.
