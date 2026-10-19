# Write the task for its reader

Choose the card's purpose before its wording. Both versions should be concise.
A personal/technical card helps a developer resume implementation with the
important decisions in view. A product card explains the operational problem
and the intended outcome to a reader who does not need the implementation.

Preserve the destination's language unless requested otherwise. Language alone
does not establish the audience. The examples below are fictional and show the
same change in two styles; they are not templates to fill mechanically.

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

## Personal or technical working task

Write a compact implementation reference. State the intended change, when it
happens, and the concrete rules that matter. Include the existing entry points,
methods, fields, or shared behavior that explain where and how to implement it,
when those facts are known.

A short **Description** and **Design** often work well. Add **Alternatives
considered** only for choices actually discussed that are worth remembering.
Preserve their rationale briefly. The card can contain technical identifiers
without cataloguing every changed file or becoming an exhaustive design document.

For example:

> **Description**
>
> Verify account access when an export is created. Reuse the existing verifier,
> keep manual checks available, and skip connections verified successfully within
> the existing reuse window.
>
> **Design**
>
> Both export-creation paths meet in `ExportService.create`. Enqueue the existing
> `verify_access` job after the transaction commits at that shared point. Keep
> status updates, concurrent-attempt handling, and failure behavior in the verifier.
>
> **Alternatives considered**
>
> Fixed-interval verification would run checks even when no export needs processing.

These illustrative details are not requirements for other tasks. Ground actual
identifiers, rules, and alternatives in the user's context and inspected sources.
Ask about material unknowns or mark them as proposals.

Append an implementation plan only when requested. Routine test counts, commit
inventories, and execution logs belong in the execution report or linked records.

## When both versions are wanted

Adapt each card to its purpose using the same agreed scope. Product and technical
examples from unrelated tasks need not be treated as matching specifications.
Cross-link the actual paired cards when useful; keep implementation details in
the technical version even if the product card supports collapsible sections.
