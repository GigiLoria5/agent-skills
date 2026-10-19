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

Let the task determine the structure and depth. Preserve a useful existing shape
and evolve it as the work develops. A small change may need a few paragraphs; a
complex investigation or implementation may need detailed analysis and supporting
material. Choose headings and formats that make this particular work easy to
navigate. There is no required template, section list, or length ceiling.

Use that future-reader purpose to decide what earns space. Explain consequential
choices, constraints, alternatives and their tradeoffs when they influenced the
result. Retain concrete behavior, technical contracts, examples, diagrams, code
references, commands, verification evidence, or operational instructions when
they help someone understand, reproduce, validate, or continue the work. These
are options, not a checklist to populate for every task. More complexity warrants
more detail; a short card is useful only if it preserves what matters.

Keep the record coherent as understanding changes. Make the current direction
and result clear while preserving earlier reasoning that explains a changed
choice. Distinguish proposals, unresolved questions, decisions, and verified
outcomes. Ground factual details in the user's context and inspected sources;
ask about material unknowns or mark them as proposals.

Organize detail so the important context and decisions are easy to find. Use
links or collapsible supporting material when helpful. Keep meaningful findings
and reproducible checks; summarize repetitive progress chatter and raw logs
unless their exact contents are needed later. Avoid duplicating information
without adding context or an explanation.

Add an implementation plan when requested, following the planning guidance.
The reference can develop from an initial idea into a record of the completed
work without losing the reasoning that makes it useful later.

## When both versions are wanted

Adapt each card to its purpose using the same agreed scope. Product and technical
examples from unrelated tasks need not be treated as matching specifications.
Cross-link the actual paired cards when useful; keep implementation details in
the technical version even if the product card supports collapsible sections.
