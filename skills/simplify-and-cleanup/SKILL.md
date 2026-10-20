---
name: simplify-and-cleanup
description:
  Use when recent task changes, a branch or PR, or specified files need a
  behavior-preserving simplification or cleanup pass. Check branch and commit
  boundaries when relevant, while following repository conventions.
license: MIT
metadata:
  author: GigiLoria5
---

# Simplify and cleanup

Make the implementation easier to understand and maintain through two passes:
first simplify its structure, then remove unnecessary verbosity. The central
question is: can we satisfy the same requirement with less code and less effort
to understand it? Prefer straightforward, explicit code over clever compression.

## Establish scope and intent

Use the scope the user supplied. Otherwise focus on the changes from the current
task; use the working diff if task history is unavailable. For a branch or PR,
identify its actual base rather than assuming `main`. Include relevant new
files. If the intended changes cannot be identified, clarify scope rather than
scanning or rewriting the entire repository.

Read applicable repository instructions and nearby code, tests, and callers to
understand the requirement, contracts, and established patterns. This skill is
repository agnostic: discover local conventions, abstractions, and verification
commands rather than imposing a framework, language style, or project layout.
Inspect surrounding code as needed, but keep edits within the requested scope.

Understand why a check, workaround, or abstraction exists before removing it.
Use callers, tests, and local constraints to establish its purpose; consult Git
history when that purpose remains unexplained. Do not require historical
research for every obvious cleanup. If the reason is still uncertain, flag the
removal.

Preserve outputs, error behavior, side effects, and their ordering. Check
database queries and external calls so a rewrite does not inadvertently repeat
work or change when effects occur. Apply changes whose equivalence is supported
by the code and its contracts. Flag changes to behavior for discussion, even
when that behavior looks speculative, unnecessary, or buggy. For example, before
removing an unrequested fallback, explain what triggers it, what removal would
change, and why removal seems worthwhile. Continue with independent cleanup
while leaving that decision open.

## 1. Simplify

- Look for an existing capability before keeping a newly invented helper,
  component, wrapper, or layer. Reuse it when its contract fits the requirement.
- Inline tiny helpers used once when they merely restate an obvious expression.
  A simple one-liner rarely earns an extra function and a jump to its
  definition. Keep a helper when it isolates a difficult step or communicates
  meaningful domain intent. Do not collapse genuinely separate responsibilities.
- Remove temporary aliases that only pass a value to the next line. Keep names
  that explain a domain concept, clarify a difficult expression, or avoid
  repeated work.
- Scrutinize names that hide the actual responsibility or effects, such as a
  `get` function that also mutates data. Rename to communicate the real
  behavior, following local conventions. Treat public names as contracts; flag
  renames that would change an interface rather than silently breaking callers.
- Remove pass-through layers and speculative extension machinery when doing so
  preserves the required contracts. A single implementation invites scrutiny; it
  does not by itself invalidate a useful architectural boundary.
- Reduce nesting and unnecessary state with direct expressions and clear control
  flow. Avoid dense one-liners, nested ternaries, and clever rewrites that save
  lines but demand more thought.
- Share logic when it expresses the same rule and should change together.
  Similar snippets serving different concepts may remain separate. Do not
  extract an abstraction merely to eliminate a little repetition.
- Simplify related test setup and duplicated scenarios where they prove the same
  behavior. Preserve distinct coverage of side effects, transitions, and failure
  paths; fewer tests is not an objective by itself.

### Avoid brittle copy assertions

In frontend and backend tests, avoid duplicating full user-facing messages from
production code when the test is about behavior rather than exact wording.
Prefer matching distinctive keywords or a short stable phrase that identifies
the expected reason, or compare against a named message constant shared with the
implementation. Reuse existing constants; introduce one when sharing the message
removes meaningful duplication, keeping it close to the owning code.

Keep assertions specific enough to distinguish failure reasons and catch the
wrong branch; a generic word or merely checking for a non-empty string is
usually insufficient. Preserve coverage of branch precedence, dynamic values,
and the empty/no-error result. Keep exact literal assertions when the wording
itself is an explicit requirement or external contract; a shared constant checks
message selection, not the correctness of its text.

## 2. Cleanup

Comments are the primary signal to examine. Review newly introduced comments and
docstrings deliberately, including those that sound helpful but only narrate the
implementation.

- Delete captions that restate, announce, or anticipate the code: what the next
  line does, how a branch works, or a routine description on every function and
  class. Test names should explain behavior without narrating the setup.
- Identify test scenarios through descriptive test names or framework-supported
  case IDs rather than comments labeling each row: for example, pytest `ids` or
  `pytest.param(id=...)`, or named Vitest/Jest table cases. Follow the local
  framework's conventions. Keep comments explaining non-obvious intent; do not
  introduce parameterization merely to remove a comment.
- Prefer expressive names and clear structure over explanatory prose. Keep a
  comment when it communicates an essential reason or constraint that the code
  cannot express: a surprising business rule, dependency limitation, deliberate
  workaround, or meaningful TODO/FIXME. Preserve required API documentation,
  legal notices, and tool directives. Do not delete comments mechanically.
- Examine defensive checks, exception handling, retries, locks, and fallback
  defaults. Trace callers and validation boundaries before deciding they are
  redundant. Type annotations alone do not validate external data. Apply only
  proven behavior-preserving removals; flag uncertain or meaningful changes.
- Remove type assertions and broad casts used to avoid understanding a type
  problem. Prefer correct types, inference, and narrowing; do not substitute a
  different escape hatch or invent runtime validation solely to satisfy typing.
- Remove incidental debug output and repetitive logs added without a concrete
  purpose. Preserve diagnostics used to understand real failures or operations;
  flag removal when their operational role is uncertain.
- Replace a comment explaining an unclear literal with a meaningful name when
  useful. Keep obvious values local, and do not create constants for every
  literal or move single-use values into shared modules.
- Remove leftovers introduced by the scoped changes: unused imports, dead
  helpers, redundant aliases, and scaffolding. Mention unrelated dead code
  without expanding the cleanup to remove it.

## Review delivery boundaries

For a feature, branch, or PR cleanup, compare the resulting diff with any agreed
delivery plan. Recommend splitting branches or PRs when the diff contains
independently useful changes, a prerequisite refactor, or distinct rollout risks
that would be easier to review separately. Keep one coherent change together;
file count or separate backend/frontend folders alone do not justify a split.

Also inspect the task's commit boundaries when history is available. Check for
commits mixing independent outcomes or burying a meaningful prerequisite inside
a larger change. Recommend coherent, reviewable commits with the necessary code
and tests together. A large cohesive change can remain one commit; line counts
are a reason to investigate, not a compulsory split threshold. If commits do not
exist yet, propose their boundaries from the working diff. Keep this check
within the current task, not an audit of unrelated history.

When recommending a split, identify what belongs in each part, its parent or
dependency, and whether the parts can land independently or as an ordered stack.
Keep schema, API, and consumer compatibility intact at each landing point.
Suggest coherent commit boundaries and Conventional Commit messages unless the
repository requires another format: `<type>[optional scope]: <description>`.
Enclose a supplied scope in parentheses, for example
`refactor(parser): simplify token lookup`. Mention a split only when it improves
this delivery.

A recommendation leaves Git history unchanged. Carry out branch creation,
history changes, or commits only when the user has requested that delivery;
preserve existing user work and recheck affected boundaries if a split is made.
For an authorized split into an ordered PR stack, use the installed `gh-stack`
guidance when the helper is available and appropriate. Preserve the agreed
parent/base relationships; the helper is optional and adds no delivery
authority.

## Verify and report

Review the resulting diff for readability and preserved contracts. Use the
repository's prescribed checks at the smallest meaningful scope: file-level
lint/type checks and focused existing tests as appropriate. Add or adjust tests
only when a meaningful invariant needs proof; avoid tests that mirror the
refactor. Follow local review requirements without turning cleanup into an
unsolicited broad audit.

Treat changed test expectations as a warning that behavior may have changed. If
cleanup requires a different expected result, stop that change and investigate;
do not weaken assertions to make it pass. Refactoring setup or updating a mock
after removing an internal helper can be legitimate, provided the same
behavioral assertions and coverage remain intact. Replacing duplicated copy with
a shared constant or focused keyword match is legitimate when it preserves the
behavioral distinction being tested, as described above.

Finish with a concise account of substantive simplifications and verification.
Include any behavior changes left for discussion, with their trigger and impact.
Report honestly when no worthwhile cleanup was found or checks could not run. Do
not invent changes to make the pass look productive. Commit, push, or open a PR
only when the user requested that delivery.
