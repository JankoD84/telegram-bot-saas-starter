# telegram-bot-saas-starter / Agent Entry Gate

## Repository purpose

`telegram-bot-saas-starter` is a commercial Telegram Bot SaaS starter-kit repository. The current repository documentation describes a Python framework for monetized Telegram bots using aiogram, FastAPI, PostgreSQL, Redis/Celery, Stripe, Docker Compose, and nginx.

This repository is a product starter kit and documentation/scaffold for buyers to build their own bot business logic. It is not the authority for external production infrastructure, buyer Stripe account state, Telegram account state, or unrelated Dulvarn platform governance.

## Architecture boundaries

Owned here:

- Starter-kit documentation and architecture guidance for Telegram Bot SaaS products.
- Framework boundaries described by `README.md`, `ARCHITECTURE.md`, and `docs/stack.md`.
- The distinction between reusable infrastructure/framework responsibilities and domain-specific bot extensions.
- Buyer-facing setup, stack, and product claims present in this repository.

Do not silently change:

- Billing/subscription semantics, rate-limit/plan-gating claims, deployment topology, plugin-extension guidance, or buyer-facing commercial promises.
- Environment/secrets handling, Stripe webhook expectations, database/migration expectations, or production operations guidance.
- Runtime/source architecture that is not actually present in the repository without first verifying current files.

## Mandatory preflight

Before implementation, run and report:

```bash
git status --short
git branch --show-current
git log -1 --oneline
git diff --stat
```

Do not work directly on `main` unless explicitly requested. Do not push, force-push, or modify Git metadata beyond the requested local branch/commit workflow.

## Progressive disclosure

Use this order for repository context:

1. `AGENTS.md` — entry gate and safety rules.
2. `.ai/README.md` — Standards V2 Lite hierarchy and authority boundaries.
3. `.ai/repo/context.md` — repository-specific architecture and ownership context.
4. `.ai/governance/engineering.md` — durable engineering constraints.
5. `.ai/process/implementation.md` — implementation workflow and reporting contract.
6. Existing `README.md`, `ARCHITECTURE.md`, and `docs/stack.md` for product/runtime details.

`docs/ai/` is compatibility/reference material only and must not override `AGENTS.md` or `.ai/`.

## Validation

This repository currently does not expose a verified test runner or dependency manifest in the inspected root files. For governance/documentation changes, use:

```bash
git diff --check
```

If source/runtime files are added later, derive validation commands from actual repository configuration before running or documenting them.

## Protected files and data

Ask before changing `.env*`, secrets, credentials, deployment/runtime configuration, billing/Stripe behavior, database or migration behavior, CI workflows, dependency files, or commercial/legal product claims.

Never expose secret values. Use placeholders in examples.

## Completion report

For implementation work, report repository, branch, HEAD, files changed, why changed, validation run, risks/rollback notes, and a concise commit message.

## Universal AI Governance Contract

`AGENTS.md` is the universal AI-agent entrypoint for Devin, Windsurf/Cascade, Cursor, VS Code + Roo Code, and Zed. Repository-specific rules in this file override generic ecosystem guidance.

Before implementation work, check and report:

```bash
git status
git branch --show-current
git diff --stat
```

Then read the repository AI context that is relevant to the task:

- `.ai/repo/profile.md`
- `.ai/repo/boundaries.md`
- `.ai/repo/commands.md`
- `.ai/governance/source-of-truth.md`
- `.ai/governance/safety-policy.md`
- `.ai/governance/quality-gates.md`

Source-of-truth precedence:

1. Current repository source code
2. Current tests, schemas and contracts
3. Current runtime / Git state
4. Repository `AGENTS.md`
5. Canonical repository documentation
6. `.ai/repo/` navigation/context
7. Task-specific `.agents/skills/`, when present
8. Historical reports, summaries, RAG output and chat context

Canonical AI governance lives in `AGENTS.md`, `.ai/`, and `.agents/skills/` when skills exist. IDE-specific directories such as `.zed/`, `.cursor/`, `.roo/`, `.windsurf/`, and `.vscode/` are execution adapters only and must not redefine repository engineering standards.

Do not modify provider credentials, model routing, LiteLLM, MCP runtime configuration, OAuth, AWS, Azure, ChatGPT subscription settings, production infrastructure, secrets, or `.env*` files as part of repository-governance work.
