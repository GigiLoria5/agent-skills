# Write the task for its reader

Choose the card's purpose before its wording. A personal/technical reference
helps its author resume work or return months later and understand what was done,
why, and which choices shaped it. Its structure and depth follow the task.
A product card explains the operational problem and intended outcome to a reader
who does not need the implementation.

Preserve the destination's language unless requested otherwise. Language alone
does not establish the audience. The example below is fictional; it is not a
template to fill mechanically.

## Product or business task

Default to two short sections: **Problem** and **Solution**, using the card's
language. Explain what goes wrong today, who it affects, and what should change
for them. A small improvement often needs just one paragraph per section.

Keep a business rule or limitation when omitting it would change the product
promise. Expand only when the user requests it or the outcome needs that detail.
Select the trigger and resulting experience rather than carrying over every rule
from the notes. Reusing an existing verifier, internal reuse windows, and similar
implementation choices stay in the technical card unless the stakeholder needs
their visible consequence to judge the product outcome. Phrasing a mechanism
without code identifiers does not make it product content.
Do not automatically append technical design, alternatives, acceptance
checklists, implementation plans, test reports, or development handoffs.

For example:

> **Problem**
>
> Operations discover broken account access while an export is already being
> processed, interrupting their work.
>
> **Solution**
>
> Check access automatically when the export is created and show a clear result,
> so operators can resolve access problems before processing the export.

Model and method names, internal fields, job orchestration, code paths, and
polling mechanics belong in the technical card. A useful source or PR link can
stay without turning the card into an execution record.

## Personal or technical reference

Write for future-you: someone returning without the conversation or the details
still in their head. Preserve enough context to understand the problem, what was
chosen or done, why it made sense, and how to continue or recheck the work.

Default to a concise memory aid, not an execution diary. Keep what changed,
why, consequential choices, and unresolved risks. Give a point one home.
Add deeper explanation only when future-you would otherwise misunderstand
the result or struggle to resume the work. Complexity permits more detail;
it does not require recording every mechanism or check.

Let the task determine the structure and depth. Preserve a useful existing shape
and evolve it as the work develops. A small change may need a few paragraphs; a
complex investigation or implementation may need detailed analysis and supporting
material. Choose headings and formats that make this particular work easy to
navigate. There is no required template, section list, or length ceiling.

Use that future-reader purpose to select consequential choices, constraints,
and tradeoffs. Link to code or supporting evidence rather than narrating it.
Include a command, diagram, contract, or reproducible check only when needed
to explain a non-obvious decision or continue the work; a requested
investigation or runbook can reasonably need more of that material. Preserve
precise risks even when they need more explanation than the main change.

Add unfinished work or a verification limitation when it changes what to do
next. Completed test inventories, manual-check stories, and merge-state
announcements usually belong in the completion report or tracker properties,
not an appended Status section. Quote UI copy only when the wording itself
is a requirement or consequential decision; do not append a Copy section
merely because the implementation introduced messages.

Keep the record coherent as understanding changes. Make the current direction
and result clear while preserving earlier reasoning that explains a changed
choice. Distinguish proposals, unresolved questions, decisions, and verified
outcomes. Ground factual details in the user's context and inspected sources;
ask about material unknowns or mark them as proposals.

Organize the selected context and decisions so they are easy to find.
Supporting links do not justify adding an unrequested technical appendix.
Before saving, remove detail whose absence would not change future-you's
understanding, decision, or next action.

Add an implementation plan when requested, following the planning guidance.
The reference can develop from an initial idea into a record of the completed
work without losing the reasoning that makes it useful later.

## When both versions are wanted

Adapt each card to its purpose using the same agreed scope. Product and technical
examples from unrelated tasks need not be treated as matching specifications.
Cross-link the actual paired cards when useful; keep implementation details in
the technical version even if the product card supports collapsible sections.
