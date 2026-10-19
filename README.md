# Agent skills

Gigi Loria's reusable development skills. This repository contains authored skills;
downloaded third-party skills stay with their original sources.

The repository is being prepared for public release. The installed skill folders
have not yet been redirected here.

## Skills

| Skill | Purpose |
| --- | --- |
| [cto-code-review](skills/cto-code-review/SKILL.md) | Evidence-based review of correctness, security, performance, and structural simplicity; selected findings become a concise fix handoff. |
| [simplify-and-cleanup](skills/simplify-and-cleanup/SKILL.md) | Behavior-preserving simplification and removal of unnecessary comments, wrappers, and defensive boilerplate. |
| [write-pr](skills/write-pr/SKILL.md) | Concise PR titles and descriptions, using the smallest format that explains the change. |

## Install after public release

Install the collection with the [Skills CLI](https://skills.sh/docs):

```sh
npx skills add GigiLoria5/agent-skills
```

Or select one skill:

```sh
npx skills add GigiLoria5/agent-skills --skill cto-code-review
```

Each skill is a portable `SKILL.md` directory. The `agents/openai.yaml` files add
Codex display metadata. Review uses the host's available subagents or its documented
sequential fallback; PR publication uses the host's available GitHub tools.

## Ownership and updates

[PROVENANCE.md](PROVENANCE.md) distinguishes authored skills from adaptations and
inspiration. Repository-specific skills and private work examples belong in their
own repositories, outside this public collection.

Use conventional commit messages, with an optional meaningful scope, for example
`feat: add a spec conversation skill` or `fix(cleanup): preserve error assertions`.
Skill revisions should address observed behavior or a concrete preference.

## License

[MIT](LICENSE).
