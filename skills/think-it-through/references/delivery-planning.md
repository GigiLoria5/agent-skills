# Plan implementation and delivery together

Fit the plan to the repository and the agreed change. Reuse an existing plan
when updating a spec rather than appending a second competing plan.

In the default driver mode, propose material choices with their consequences and
let the user decide. An explicit request to handle the work automatically can
delegate those choices within its stated scope. Record the chosen approach and
its reason so the user can understand the plan afterward. Preserve decision
ownership in an implementation handoff: record what the user has delegated and
which unresolved choices still belong to them.

Describe verifiable slices, their dependencies, and the check or demonstration
that establishes each slice is done in its intended parent or integrated
context. A slice need not work without its prerequisites. Keep the plan concrete
enough to guide implementation without recreating the patch in prose. Include a
useful point to explain or demonstrate a slice when the user wants to understand
and iterate on the result.

## Branch boundaries

Choose coherent review units with explicit dependencies. Compare one PR with
clear commits, a small ordered stack, and independent PRs where applicable.
Prefer the shape that makes the decisions easier to review without adding
unnecessary coordination. A dependent part can deserve separate review even when
it is not useful on its own. Dependency alone neither requires one PR nor
justifies a stack; file count, backend/frontend folders, and arbitrary size
targets are not sufficient reasons either.

Separate three boundaries: review scope, merge order, and deployment. Inspect
the repository's actual release process before deciding which intermediate
states can reach users. Do not assume every PR deploys independently or that a
stack merges or deploys atomically. For each proposed PR, record its scope,
parent, and verification on top of its prerequisites; check compatibility at
each merge or deployment state the process can produce.

Before rejecting a stack as unsafe, identify a concrete intermediate state and
the behavior or contract it breaks. Evaluate cumulative code including preceding
PRs, not a dependent branch transplanted onto main without its prerequisites.
For example, an additive compatible schema change, an API using it, and a UI
using that API can form an ordered stack. The dependency chain alone does not
make those intermediate states broken. Verify that the actual changes are
additive and compatible rather than assuming they are.

If the changes genuinely require one merge or deployment and the repository
cannot enforce that boundary for a stack, keep one PR with coherent commits. Do
not invent compatibility layers, flags, or release mechanisms merely to force a
split. When release behavior is unknown, state that uncertainty rather than
asserting that a split would ship broken code.

Name actual branches when the user or repository has supplied the convention;
otherwise describe the boundaries without pretending branches already exist.
Preserve an agreed split unless new evidence warrants changing it. Explain the
specific evidence and resulting change, rather than redesigning delivery because
the invocation was shorter. Keep the rationale brief in the working plan or
handoff; it is not a mandatory extra section in the PR description.

When the agreed boundaries form an ordered PR stack, consider `gh-stack` if it
is available and fits the repository's delivery flow. Read its installed
guidance before use. Record the parent/base relationship for each branch;
ordinary Git remains sufficient when the helper is unavailable or unnecessary.
Planning a stack does not submit it or authorize history changes.

## Commits and completion

Plan coherent commits rather than one commit per file or one undifferentiated
commit for unrelated work. Default to Conventional Commits, respecting an
explicit repository requirement if it differs: `<type>: <imperative summary>` or
`<type>(<meaningful scope>): <imperative summary>`. Typical types include
`feat`, `fix`, `refactor`, `docs`, `test`, and `chore`; use a breaking-change
marker only for an actual breaking change.

Treat these as delivery preferences, not permission to create branches, rewrite
history, or commit. Before delivery, account for relevant documentation, verify
the completed behavior, and check whether the resulting diff still matches the
planned review boundaries. Cleanup can recommend a revised split when useful.
