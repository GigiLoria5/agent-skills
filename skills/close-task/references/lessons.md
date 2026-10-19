# Improve the next run from evidence

Use actual corrections, failed approaches, unnecessary work, or missing context
from the task. Read the relevant instructions and existing checks before deciding
what was missing. Distinguish a new rule from an existing rule that was unclear,
unavailable, contradictory, or simply not followed.

Look for the smallest intervention that addresses the observed cause:

- **Navigation:** When finding the right source took avoidable work, add or
  sharpen a pointer near the place an agent would look. Avoid copying the source.
- **Mechanical mistakes:** Prefer an existing lint rule, test, type check, or CI
  check over another prose instruction. Verify whether a check already exists
  but is unwired before proposing a new one. Propose the check as follow-up work
  unless implementing it is already authorized.
- **Judgment and conventions:** Clarify the relevant repository rule or existing
  skill reference when automation cannot express the decision. Preserve local
  exceptions and remove contradictions rather than layering on another command.
- **Repeated workflow friction:** Improve the skill that owns that decision. A
  separate skill earns its place when the workflow is independently reusable,
  not merely because one task exposed an edge case.
- **Tooling or information access:** Identify the particular missing log, source,
  or tool capability and the decision it would have improved. Treat access
  changes as proposals, not instructions to acquire broader permissions.
- **Instruction noise:** Remove stale, redundant, or ineffective guidance when
  an addition would otherwise make the context harder to use. Keep always-loaded
  steering files small; put detailed conditional guidance in its proper reference.

For each worthwhile proposal, explain the observed friction, the target, and the
intended change briefly. Do not claim a recurring pattern from one ambiguous
incident or turn every terminal error into a new policy. A concrete serious
failure can justify a focused correction without requiring repeated incidents.

Keep temporary execution history out of permanent agent instructions. Preserve
durable rationale and links where the repository expects them, and keep the
actual patch or check configuration as the source of truth for mechanical detail.
