# Build the simplest complete solution

Use the repository's instructions, established patterns, and relevant
implementation skills as the local source of truth. These defaults apply where
the project leaves a decision open; they do not prescribe a framework or stack.

## Earn the code

- Before adding behavior, look for an existing capability, configuration, helper,
  component, validator, or test fixture that meets the need. Reuse its contract
  when it fits. Keep the requested behavior intact.
- Build only what the task needs. Add layers, flags, retries, locks, and generic
  extension points for a demonstrated requirement, not a possible future one.
  Correctness and authorization are part of the complete solution, not optional
  complexity to discard.
- Keep ownership close to the feature or domain. Extract genuinely shared
  concepts with real consumers; avoid broad constants modules and tiny wrappers
  that add navigation without meaning. Similar code for different concepts need
  not be forced into one abstraction.
- Use clear names and direct control flow. Keep derived state derived. Give
  each rule one authoritative home rather than duplicating business logic
  between interfaces or layers.
- Let code communicate ordinary mechanics. Keep comments for essential intent,
  constraints, or surprising decisions, instead of captions and routine
  descriptions of every function. Remove unused scaffolding and debug leftovers.

## Make contracts precise

Use the project's typing system precisely at boundaries and in application code.
Prefer existing domain types and typed structured results when they clarify a
relationship. Use inference where it stays clear and preserve established
framework exceptions. Broad untyped values, unchecked assertions, and blanket
type/lint suppressions are not substitutes for understanding a contract.

Validate untrusted data where it enters the system; a static type does not prove
that external input is valid. Preserve permission checks, error behavior, data
integrity, and relevant side effects while simplifying.

## Prove behavior economically

For a behavior change or bug fix, write a focused test that fails for the intended
reason before implementing the behavior, following the repository's test-first
policy and established test style. Use proportionate verification for docs,
generated files, and mechanical behavior-preserving changes.

Choose the narrowest public boundary that proves the behavior and add enough
integration coverage to verify important wiring, permission checks, and external
contracts. Avoid repeating all lower-layer cases through a UI or endpoint.
Expected results should come from the requirement or an independent worked
example, rather than recomputing production logic in the assertion.

Reuse nearby fixtures and helpers. Parametrize genuinely repeated scenarios when
it improves clarity; keep distinct side effects or failure paths separate.
Name scenarios through descriptive tests and framework-supported case IDs (pytest
`ids` / `pytest.param(id=...)`, or named Vitest/Jest table cases),
rather than comments labeling rows. Preserve comments for non-obvious intent
and follow local conventions; parameterization should earn its own clarity.
Mock only the dependencies needed to isolate the behavior. Add concurrency,
idempotency, or query-count coverage when those are actual properties at risk.

Run focused tests and the repository's relevant lint, type, and build checks.
Broaden to required suites when local guidance or changed interactions call for
them. Fix failures within scope, preserve meaningful assertions, and report
unrun checks or blockers honestly. Test counts and coverage percentages alone
are not evidence that the intended behavior works.
