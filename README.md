# kaneky-skills

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-marketplace-6C4FF7)](https://docs.claude.com/en/docs/claude-code)
[![Published](https://img.shields.io/badge/skills-14-brightgreen)](#the-skills)
[![Config](https://img.shields.io/badge/config-zero-brightgreen)](#install)

Claude Code skills about **failures that look like success**.

Fourteen are written; **thirteen are published**. The unpublished one is listed
below without a link, because a link to a repository that does not exist is the
same defect these skills are about — and so is a count that has drifted from
what is actually on GitHub, which is what this line said before it was checked.

Not a tutorial collection. Every one is written from an incident where every
check passed and the system was wrong anyway — Argo reporting `Synced` while the
cluster diverged, a test suite green because it tested the previous build, a
model returning a perfectly-formed record it invented, a job retrying thousands
of times while its controller recorded zero failures.

## Install

```sh
/plugin marketplace add kan3ky/kaneky-skills
/plugin install kaneky-gitops
```

Or install any single skill directly:

```sh
/plugin install kaneky-agent-guardrails@kaneky-skills
```

No configuration, no dependencies. Each skill loads itself when the work
matches it.

## The skills

### Operating what you shipped

| Skill | The failure it exists for |
|---|---|
| [kaneky-gitops](https://github.com/kan3ky/kaneky-gitops) | The deploy reported success and the cluster is quietly wrong. Orphans after a decommission, secret paths that 403 silently, a tag that is not a version and not a deploy. |
| [kaneky-diagnosis](https://github.com/kan3ky/kaneky-diagnosis) | The symptom is nowhere near the cause. How to search when the obvious answer was already checked and was fine. |
| [kaneky-integrations](https://github.com/kan3ky/kaneky-integrations) | An empty result and a dead source look identical. Yours has to tell them apart, because the source will not. |
| [kaneky-auth](https://github.com/kan3ky/kaneky-auth) | A control is only as good as where it is evaluated. Move it one hop and it stops being a control while still looking like one. |
| [kaneky-capability-honesty](https://github.com/kan3ky/kaneky-capability-honesty) | A system's account of what it can do drifts from what it can do. A tool listed without its credential, an option selectable but unroutable, a feature announced at boot that its own filter can never reach. |

### Testing and verification

| Skill | The failure it exists for |
|---|---|
| [kaneky-e2e](https://github.com/kan3ky/kaneky-e2e) | The suite runs and gates nothing. Credential-free by construction, deterministic, honest about which build it tested. |
| [kaneky-visual-loop](https://github.com/kan3ky/kaneky-visual-loop) | An assertion checks what you thought to measure. Looking catches what you did not — and a still frame has blind spots of its own. |

### Building with models

| Skill | The failure it exists for |
|---|---|
| [kaneky-agent-guardrails](https://github.com/kan3ky/kaneky-agent-guardrails) | A capability that does not exist cannot be talked into firing. Command policy, tool surfaces, escape hatches. |
| [kaneky-agent-memory](https://github.com/kan3ky/kaneky-agent-memory) | Every failure in a memory subsystem returns a plausible value instead of an error. |
| [kaneky-extraction](https://github.com/kan3ky/kaneky-extraction) | A model asked for a field will always return one. Fabrication and success are the same shape. |
| [kaneky-providers](https://github.com/kan3ky/kaneky-providers) | A provider abstraction is a claim that two things are interchangeable, and every bug is that claim being false. |
| [kaneky-delegation](https://github.com/kan3ky/kaneky-delegation) | Delegated work is untrusted until you check it yourself, and the report is not the check. |

### Data

| Skill | The failure it exists for |
|---|---|
| [kaneky-corpus](https://github.com/kan3ky/kaneky-corpus) | Past a few thousand records, a corpus's quality is exactly what your automated checks assert and nothing more. |

## Why they share a shape

Each skill was written after the same experience: a green result that was
false. That pattern turns out to have a small number of causes, and they repeat
across domains that look unrelated —

- **A system reports on the action it took, not the state it produced.** Argo
  applied the manifests; the workload is still wrong. A linter exited 0; it
  never acquired its lock. A tag exists; no image was published.
- **Absence and failure share a representation.** Zero results, an empty list, a
  null field — the same value whether nothing matched or nothing could be
  asked.
- **A check measures what someone thought to measure.** Everything the check
  does not express is unprotected, and quietly so.

Recognising which of those you are looking at is usually most of the diagnosis.

## Scope

These skills review, explain and design. They do not mutate infrastructure, and
they are written to say what they could not verify rather than assume it.

## Contributing

Failure reports are the most useful contribution — especially ones where every
check stayed green. Include the symptom, the root cause, and the check that
would have caught it. Open an issue on the relevant skill's repository.

## Licence

MIT.
