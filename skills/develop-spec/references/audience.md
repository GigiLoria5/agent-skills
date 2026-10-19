# Write for the card's reader

Choose content by the reader's decisions and needs, rather than changing only
the wording of the same technical document. Preserve the destination's language
unless the user requests another one. English does not imply technical, and
Italian does not imply product.

## Product or business

Default to a short problem and solution. Add acceptance criteria, a material
business rule, or a scope boundary when it helps a stakeholder understand the
outcome or make a decision. Use the vocabulary of the people doing the work.
Let the size of the change determine the length; a brief improvement may need
only two short paragraphs.

Explain who experiences the problem, its consequence, and what will change for
them. Keep details such as supported cases or who can perform an action when
they affect the product promise. Translate technical constraints into their
visible consequence.

Keep model and method names, repository paths, database migrations, API and
polling mechanics, branch plans, commit hashes, test counts, and engineering
handoffs in the technical reference. Preserve a concise PR or technical-spec
link when useful or already present, without expanding it into a progress log.
Use supporting metrics only when established, relevant to a decision, and worth
the reader's attention. A product card should remain readable as a product card
after implementation starts.

For example, a product brief about checking a saved integration could say:

> Today, access problems are discovered only when the team tries to use the
> integration, delaying their work. Check access when the connection details
> are saved and show a clear result, so problems can be resolved immediately.

## Personal or technical reference

Keep enough detail to resume the work and understand why decisions were made.
Cover intended behavior, relevant business rules, architectural choices,
interfaces, important edge cases, scope, and verification where they matter.
Include precise code references when useful and grounded in inspected code.
Separate implemented facts from proposed approaches and open decisions.

The same integration change might record where updates enter the application,
when a background check starts, what constitutes an unsupported integration,
how its result is displayed, and how the behavior will be verified. Add those
details only when established; the example is not an instruction to use a
background job for every integration.

Put an agreed implementation plan at the end. Detailed test output and changing
commit inventories can stay in linked execution artifacts instead of making
the reference harder to read.

## Both versions

Use the same agreed requirements. Write the product version around the problem
and resulting behavior, and the technical version around decisions and execution.
Cross-link them when requested or consistent with their established use. Avoid
copying the technical version into a product card under collapsible headings;
the audience boundary concerns content, not its initial visibility.
