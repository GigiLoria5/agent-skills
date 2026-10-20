# Plan implementation and delivery together

Fit the plan to the repository and the agreed change. Reuse an existing plan
when updating a spec rather than appending a second competing plan.

In the default driver mode, propose material choices with their consequences and
let the user decide. An explicit request to handle the work automatically can
delegate those choices within its stated scope. Record the chosen approach and
its reason so the user can understand the plan afterward.
Preserve decision ownership in an implementation handoff: record what the user
has delegated and which unresolved choices still belong to them.

Describe independently verifiable slices, their dependencies, and the check or
demonstration that establishes each slice is done. Keep the plan concrete enough
to guide implementation without recreating the patch in prose. Include a useful
point to explain or demonstrate a slice when the user wants to understand and
iterate on the result.

## Branch boundaries

Decide the intended review boundaries during planning. A single coherent change
can remain one branch and PR. Consider a split when a prerequisite refactor,
independently useful capability, or separate rollout deserves its own review.
Avoid splitting solely by file count, backend/frontend folders, or an arbitrary
PR-size target.

For a proposed split, record what belongs in each branch or PR, its dependency or
parent, and the behavior that must work at that boundary. State whether the
branches can land independently or require an ordered stack. Coordinate schema,
API, and consumer changes so an intermediate deployed state is supported; a
technically ordered stack does not by itself guarantee safe deployment.

Name actual branches when the user or repository has supplied the convention;
otherwise describe the boundaries without pretending branches already exist.
Revisit the plan if implementation reveals a materially different dependency.

When the agreed boundaries form an ordered PR stack, consider `gh-stack` if it is
available and fits the repository's delivery flow. Read its installed guidance
before use. Record the parent/base relationship for each branch; ordinary Git
remains sufficient when the helper is unavailable or unnecessary. Planning a
stack does not submit it or authorize history changes.

## Commits and completion

Plan coherent commits rather than one commit per file or one undifferentiated
commit for unrelated work. Default to Conventional Commits, respecting an explicit
repository requirement if it differs: `<type>: <imperative summary>` or
`<type>(<meaningful scope>): <imperative summary>`. Typical types include `feat`,
`fix`, `refactor`, `docs`, `test`, and `chore`; use a breaking-change marker only
for an actual breaking change.

Treat these as delivery preferences, not permission to create branches, rewrite
history, or commit. Before delivery, account for relevant documentation, verify
the completed behavior, and check whether the resulting diff still matches the
planned review boundaries. Cleanup can recommend a revised split when useful.
