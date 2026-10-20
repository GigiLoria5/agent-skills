---
name: make-it-happen
description: Use only when explicitly invoked to delegate selected development phases or the whole workflow, from specs and plans through implementation, review, PR delivery, and documentation alignment. A short brief or nontechnical user alone does not select this skill.
disable-model-invocation: true
license: MIT
metadata:
  author: GigiLoria5
---

# Make it happen

Take the wheel when the user deliberately delegates the development workflow.
Keep explanations accessible and decisions traceable. The user remains
responsible for what ships, including work they choose to delegate.

## Establish the delegated task

An explicit invocation delegates coordination and routine technical decisions
for the requested phases, not automatically the entire workflow. Enter at the
requested phase, reuse the agreed spec and plan, and stop at the requested
boundary. For example, implement an agreed plan without reopening the spec or
proceeding to PR delivery when only implementation was delegated. The user
can switch between driver and delegated modes for any piece; retain settled
decisions and return ownership of newly undelegated choices. A short brief or
a nontechnical user alone is not an invocation. Establish the desired result and
where to work from the request, linked cards, and repository context. If the goal
or target is genuinely missing, ask one plain-language question; automatic mode
does not supply an unknown product goal.

Briefly state the outcome, material assumptions, and intended delivery. Explain
whether the request includes saving a card, committing, pushing, or opening a
PR. Complete those actions when requested; otherwise prepare only the local
artifacts needed for the selected phases. Repository publication, merging, and
deployment are separate actions
unless the user includes them. Reuse existing authorization instead of adding
approval gates between phases.

Choose ordinary implementation details and tradeoffs with a clear default.
Bring a decision back when it changes the requested product outcome, makes a
material commitment outside the delegated scope, or requires unavailable access.
Describe its consequence and recommend an option in language the user can judge.
Continue independent work while that decision is pending.

## Coordinate the workflow

Use the companion skills when available, reading their actual instructions at
the relevant phase. Install the collection for the full workflow. If a companion
is unavailable, state that limit and follow the phase's essential behavior below
with the host's available tools. Do not claim a named review or validation ran
when it did not. Repository-specific implementation guidance takes precedence;
read only the companions needed for the selected phases. The phases below
describe the available route, not a required sequence for every invocation.

Before writing code or tests, read
[implementation quality](references/implementation-quality.md). Apply that
baseline while building, alongside the repository's more-specific guidance.
Automatic coordination retains the same simplicity, typing, and verification
standards as driver mode.

1. **Spec — `think-it-through`:** Read the draft and relevant sources. Develop a
   spec whose structure and depth fit the task and intended audience. Use explicit
   audience preferences or
   clear destination context; ask only when uncertain. Keep product requirements
   separate from technical decisions. Routine choices are delegated in this mode,
   so complete the requested spec or planning work without the driver mode's
   phase questions. Stop at the requested boundary.
   Save to the supplied destination when the request includes updating it;
   otherwise keep a usable draft.
2. **Plan:** Inspect repository guidance and existing code. Define independently
   verifiable slices, their branch/PR boundaries, dependencies, and a suitable
   validation approach. A coherent change can stay on one branch. Default to
   Conventional Commits unless the repository requires another format. Record
   why a material approach was selected and update the plan when new evidence
   changes a dependency. Follow `think-it-through`'s plan-destination guidance:
   use ignored local Markdown unless another destination was selected, and
   keep an external technical card and product card distinct.
3. **Implement:** Follow repository conventions and applicable implementation
   skills. Build and verify one useful slice at a time. Fix failures within scope,
   and keep requirements, plan, and relevant documentation consistent with the
   result. A missing tool or failing check is a limit to report, not evidence of
   success.
4. **Review — `cto-code-review`:** Review the completed change at an appropriate
   depth. This invocation explicitly delegates selection and execution for
   supported correctness fixes and behavior-preserving improvements within the
   agreed scope. Keep a compact ledger of fixed, skipped, or deferred findings
   and reasons. For a material product change or contested tradeoff outside
   that delegation, present the finding for the user's decision. Use available
   subagents when useful and permitted; otherwise review sequentially.
5. **Cleanup — `simplify-and-cleanup`:** Simplify without changing agreed
   behavior. Revisit delivery boundaries if the actual diff has diverged from
   the plan. Make an authorized split only when it improves this delivery, and
   verify relevant behavior after edits or branch changes.
6. **Delivery — `write-pr`:** Prepare concise PR wording around the outcome and
   essential reviewer context. Finish requested commits, pushes, and PR creation.
   Check the actual base of each branch in a stack, and put only that PR's
   contribution in its description. Use `gh-stack` when available and appropriate
   for an agreed stack, reading its installed guidance first. Finish generated
   PR wording with `write-pr` after submission, within the requested delivery.
   Verify actual GitHub stack membership as well as branch bases; follow
   `write-pr`'s stack-delivery checks. Keep verification in the completion
   report unless the document's reader needs it for a particular decision.
7. **Align and improve — `align-and-improve`:** After PR preparation or requested PR
   delivery, reconcile affected specs and documentation. Documentation within the task
   is delegated here: use known destinations and authorized updates without the
   driver mode's target selection question. Resolve ambiguous or unknown external
   destinations with the user. Propose useful improvements from observed friction;
   changing shared skills or steering instructions requires its own explicit selection,
   even in this mode. If the companion is unavailable, update the known task docs and
   report specific lesson proposals using the same boundaries. Include resulting
   documentation changes in the already authorized delivery, updating the PR
   when that is part of the request.

Stop when the agreed outcome and relevant verification are complete, or when a
specific blocker requires the user. Do not keep cycling for cosmetic findings.
If the user asks for explanations or takes over a decision, follow that steering
without treating it as cancellation of the whole task. They can return to driver
mode at any time; stop making newly unassigned decisions automatically.

## Keep context economical

Use targeted searches and bounded output; reopen source only when needed.
For sustained work, keep a short checkpoint in the ignored local plan with
decisions, current phase, relevant links or revisions, unresolved choices,
delegated scope, and next action. This is working state, not content to copy
into the final card or PR.

At a meaningful phase boundary, compact bloated context when the host exposes
that capability; otherwise offer the host's compaction command or a short
handoff. Never claim to compact without doing so. Rewind is for abandoning
an approach, not routine compression. Compaction does not refund spent usage.

Use focused fresh-context subagents for independent research or review when
useful and available. Pass the bounded task, relevant source pointers, and
needed decisions rather than the whole conversation; request compact findings
and evidence, and inspect their results. Subagents also consume usage: avoid
duplicating the same investigation or delegating trivial sequential steps.

## Hand back an understandable result

Lead with what the user can now do, a demo or useful artifact when available,
and where the result lives. Briefly explain material decisions, actual validation,
and anything still requiring action. Distinguish prepared, committed, opened,
and verified work. Provide enough context for the user to take responsibility
for the result without making them reconstruct the implementation transcript.
