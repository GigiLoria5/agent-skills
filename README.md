# Keep your brain in the loop

AI can write the code. **You're still responsible for what ships.**

These are the skills I use to turn a rough idea into reviewed, understandable
software. Usually I want to think through the decisions myself, with an agent
that helps me see the options. Sometimes I deliberately hand over more of the
work. Both are valid choices. The delegation should be yours.

## Choose how you work

| | Driver mode | `dev-brain-rot` |
| --- | --- | --- |
| You bring | A draft, a problem, or a task to work through | A goal and a place to build it |
| Decisions | You own consequential choices; the agent researches and recommends | You explicitly delegate routine choices and coordination |
| Missing context | The agent asks for intent it cannot retrieve | The agent makes reasonable choices within scope; asks when the goal or a consequential boundary is missing |
| Pace | Discuss, understand, decide, then continue | Spec, plan, build, review, cleanup, and PR preparation flow together |
| Review | Choose your own review, CTO review, cleanup, or a combination | The agent coordinates review and resolves supported findings within the delegated scope |
| Responsibility | Yours | Still yours |

Both modes work for developers and nontechnical teammates. Driver mode does not
require a technical quiz, and delegated mode does not require pretending to know
every implementation detail.

## Driver mode: stay involved

Start with a rough draft in Notion, an issue, a document, or chat.

1. **Discuss with `develop-spec`.** Clarify the problem through a conversation.
   The agent brings facts, options, and recommendations. When intent or a material
   tradeoff is missing, it asks you instead of silently deciding.
2. **Agree and save the spec.** The agent offers to update your chosen card and
   establishes its audience: technical reference, product/business, or two linked
   versions. Clear destination context can establish the audience; ambiguity
   brings a question. Product cards stay focused on the problem and outcome.
3. **Choose whether to plan.** Once the spec is settled, the agent asks whether
   you want an implementation plan. The plan defines useful slices, validation,
   branch/PR boundaries, dependencies, and Conventional Commit preferences.
4. **Implement and understand.** Use the repository's implementation guidance.
   Work in slices, inspect the result, ask for explanations, and iterate until
   you are satisfied. An agreed spec or plan is not an automatic instruction to
   start coding.
5. **Choose review and cleanup.** Review it yourself, use `cto-code-review`,
   run `simplify-and-cleanup`, or combine them. CTO review lets you accept,
   reject, or defer findings, then choose fixes here, a subagent, a handoff
   prompt, or fixing them yourself.
6. **Prepare delivery.** Revisit branch boundaries if implementation changed the
   plan, finish coherent Conventional Commits, and use `write-pr` for concise
   PR wording. Complete the commit/push/PR actions you actually requested.

Relevant documentation evolves with implementation. Use review feedback and
real corrections to improve the skills and checks afterward.

```text
Use $develop-spec to talk through this draft: <card or idea>.
I want to understand the choices and stay in the driver's seat.
```

A short brief is not permission to invent your product decisions. You can
explicitly delegate an individual choice with “you decide” or “go automatically”
without handing over the entire workflow.

## Dev Brain Rot: deliberately hand over the wheel

For a nontechnical teammate, a familiar task, or a day when you want to delegate,
invoke `dev-brain-rot` explicitly. It coordinates the companion skills and the
repository's implementation conventions from spec through PR preparation.

It records the plan and meaningful decisions, implements and verifies the work,
coordinates review and fixes, simplifies the result, and prepares the requested
delivery. You get an understandable result, useful evidence, and anything that
still needs your decision.

```text
Use $dev-brain-rot to implement <goal or card> in <repository>.
Choose routine implementation details and open a PR when ready.
```

This mode is explicit-only. It does not activate because you gave a short prompt
or because you are not a developer. It can still need a real goal, access, or a
decision outside the delegated scope. You can take the wheel back at any time.

## The workflow

```mermaid
flowchart TD
    A["Draft: Notion, issue, document, or chat"] --> B{"How do you want to work?"}
    B -->|Driver mode| C["develop-spec: discuss and clarify"]
    C --> D["Agree the spec and its audience"]
    D --> E{"Save or update the card?"}
    E -->|Yes| F["Update the chosen destination"]
    E -->|Keep in chat| G{"Create an implementation plan?"}
    F --> G
    G -->|Later| H["Keep the agreed spec"]
    G -->|Yes| I["Plan slices, branch boundaries, and dependencies"]
    I --> J["Implement and verify with repository conventions"]
    J --> K{"Choose review or cleanup"}
    K --> L["Your review"]
    K --> M["cto-code-review"]
    K --> N["simplify-and-cleanup"]
    L --> O["Understand, decide, and fix"]
    M --> O
    N --> O
    O -->|Iterate| J
    O -->|Ready| P["Finalize branch split and Conventional Commits"]
    K -->|Ready| P
    P --> Q["write-pr"]
    Q --> R["Requested PR delivery"]
    B -->|Explicit delegation| S["dev-brain-rot"]
    S --> T["Spec, plan, implement, review, cleanup, and PR preparation"]
    T --> R
    R --> U["Documentation and useful lessons"]
```

## The skills

| Skill | Reach for it when |
| --- | --- |
| [develop-spec](skills/develop-spec/SKILL.md) | You want to think through a change and write the right spec for its audience. |
| [cto-code-review](skills/cto-code-review/SKILL.md) | You want evidence-based scrutiny of correctness, security, performance, and structural simplicity. |
| [simplify-and-cleanup](skills/simplify-and-cleanup/SKILL.md) | You want less complexity and boilerplate, plus a useful check of delivery boundaries. |
| [write-pr](skills/write-pr/SKILL.md) | You want the outcome and essential reviewer context, with implementation bookkeeping left in the diff. |
| [dev-brain-rot](skills/dev-brain-rot/SKILL.md) | You explicitly want the whole workflow coordinated for you. |

## Install

The repository is currently private while the first release is prepared.
After public release, install the collection with the [Skills CLI](https://skills.sh/docs):

```sh
npx skills add GigiLoria5/agent-skills
```

Install the collection to give `dev-brain-rot` its companion skills. For an
individual tool:

```sh
npx skills add GigiLoria5/agent-skills --skill write-pr
```

Each skill is a portable `SKILL.md` directory. Codex metadata lives in
`agents/openai.yaml`. Available tools, repository access, and host permissions
determine which actions can actually run.

## Authored here, published deliberately

This is my authored collection. [PROVENANCE.md](PROVENANCE.md) records origins
and inspiration; third-party downloads stay with their original sources.

Skill folders are ignored by default. The five folders above are explicitly
allowlisted in [.gitignore](.gitignore); other skills can live in the same local
checkout without joining the publication set. Adding a skill to the public
collection is a deliberate whitelist change.

Use Conventional Commits for this repository, with an optional meaningful scope.
Improve instructions from real use: what decision did the agent get wrong, and
what small change would help it get that decision right next time?

[MIT license](LICENSE). Built by Gigi Loria.
