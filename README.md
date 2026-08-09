# Guardrails Engineering (`gre`)

A focused BMad module for code architecture, database architecture and design, application security, infrastructure and operations, and AI application design. Every recommendation includes the cost of ignoring it.

This is a focused BMad module in the [Guardrails](https://github.com/mlarese/bmad-module-guardrails)
bundle. It keeps the same behavior and shared memory while installing only the figures and
workflows for the engineering area.

> **Generated.** This repository is produced by `tools/build_modules.py` in the
> [bmad-module-guardrails](https://github.com/mlarese/bmad-module-guardrails) repository.
> Make changes there and regenerate; local changes here will be overwritten.

## Agents

| Agent | Role | Skill | Focus |
| ----- | ---- | ----- | ----- |
| 🔐 Kai | Application Security Engineer | `grl-agent-security` | APIs, authentication, authorization, secrets, dependencies, CVEs, and LLM attack surfaces. |
| 🧱 Otto | Code Architect | `grl-agent-architecture` | Boundaries, folders, dependencies, interfaces, factories, and architectural layers. |
| 🗄️ Dario | Database Architect & Designer | `grl-agent-database` | Data models, PostgreSQL, Oracle, MongoDB, Redis/Valkey, distributed SQL, NoSQL, search, analytics, time-series, graph, vector, and hybrid search. |
| 🖥️ Bruno | Infrastructure & Ops Engineer | `grl-agent-ops` | Servers, VPS, Docker, CI/CD, deployment, TLS, backups, logs, and incidents. |
| 🧠 Enzo | AI Engineer | `grl-agent-ai` | LLMs, prompts, RAG, embeddings, tool calling, evaluations, costs, and latency. |

## Skills and workflows

| Skill | Purpose |
| ----- | ------- |
| `gre-profile` | Project profile | Collects the project context shared by every installed figure. |
| `gre-board` | Multidisciplinary review | Convenes the relevant figures on one artifact and returns a review summary or release verdict. |
| `grl-automation` | Controlled automation | Routes work from read-only checks through dry-run to observable execution, with explicit approvals and rollback. |

## Installation

```
bmad install gre
```

As a first step, run `gre-profile`. It collects the project profile — sector, data,
market, stack, and criticality — so each figure can calibrate its review. Without a profile,
the default remains `normal` and the figures start without context.

## Shared memory

The profile lives in `{project-root}/_bmad/memory/grl-shared/project-profile.md`, together
with `decisions.md` and `accepted-risks.md`. All Guardrails modules use the same path, so two
installed modules still share one profile.

## Using it with the bundle

This module installs skills with **the same names** as the `grl` bundle — `grl-agent-security`
is identical in both. Do not install the full bundle and thematic modules in the same project:
choose the complete bundle, or only the thematic modules you need.

## License

MIT.
