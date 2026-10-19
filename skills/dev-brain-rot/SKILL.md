---
name: dev-brain-rot
description: Explicitly delegate a development task from a rough idea through spec, plan, implementation, review, cleanup, documentation, and PR preparation. Designed for users who want the agent to coordinate the workflow and choose routine implementation details.
license: MIT
metadata:
  author: GigiLoria5
---

# Dev Brain Rot

Take the wheel when the user deliberately delegates the development workflow.
Keep explanations accessible and decisions traceable. The user remains
responsible for what ships, including work they choose to delegate.

## Establish the delegated task

An explicit invocation selects automatic coordination of the phases below and
routine technical decisions within the requested outcome. A short brief or a
nontechnical user alone is not an invocation. Establish the desired result and
where to work from the request, linked cards, and repository context. If the goal
or target is genuinely missing, ask one plain-language question; automatic mode
does not supply an unknown product goal.

Briefly state the outcome, material assumptions, and intended delivery. Explain
whether the request includes saving a card, committing, pushing, or opening a
PR. Complete those actions when requested; otherwise prepare the local result
and PR text. Repository publication, merging, and deployment are separate actions
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
no personal stack skill is required.

Before writing code or tests, read
[implementation quality](references/implementation-quality.md). Apply that
baseline while building, alongside the repository's more-specific guidance.
Automatic coordination retains the same simplicity, typing, and verification
standards as driver mode.

1. **Spec — `develop-spec`:** Read the draft and relevant sources. Develop a
   concise spec for the intended audience. Use explicit audience preferences or
   clear destination context; ask only when uncertain. Keep product requirements
   separate from technical decisions. Routine choices are delegated in this mode,
   so move through the spec and plan without the driver mode's phase questions.
   Save to the supplied destination when the request includes updating it;
   otherwise keep a usable draft.
2. **Plan:** Inspect repository guidance and existing code. Define independently
   verifiable slices, their branch/PR boundaries, dependencies, and a suitable
   validation approach. A coherent change can stay on one branch. Default to
   Conventional Commits unless the repository requires another format. Record
   why a material approach was selected and update the plan when new evidence
   changes a dependency.
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
6. **Close the task — `close-task`:** Reconcile affected specs and documentation
   before final delivery. Documentation within the task is delegated here: use
   known destinations and authorized updates without the driver mode's target
   selection question. Resolve ambiguous or unknown external destinations with
   the user. Propose useful improvements from observed friction; changing shared
   skills or steering instructions requires its own explicit selection, even in
   this mode. If the companion is unavailable, update the known task docs and
   report specific lesson proposals using the same boundaries.
7. **Delivery — `write-pr`:** Prepare concise PR wording around the outcome and
   essential reviewer context. Finish requested commits, pushes, and PR creation.
   Check the actual base of each branch in a stack, and put only that PR's
   contribution in its description. Link a technical execution record when useful;
   keep implementation logs out of product cards.

Stop when the agreed outcome and relevant verification are complete, or when a
specific blocker requires the user. Do not keep cycling for cosmetic findings.
If the user asks for explanations or takes over a decision, follow that steering
without treating it as cancellation of the whole task. They can return to driver
mode at any time; stop making newly unassigned decisions automatically.

## Hand back an understandable result

Lead with what the user can now do, a demo or useful artifact when available,
and where the result lives. Briefly explain material decisions, actual validation,
and anything still requiring action. Distinguish prepared, committed, opened,
and verified work. Provide enough context for the user to take responsibility
for the result without making them reconstruct the implementation transcript.
