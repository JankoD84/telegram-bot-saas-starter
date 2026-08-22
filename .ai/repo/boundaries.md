# Repository Boundaries

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

## Ownership boundaries

- Changes must stay within this repository's documented purpose and current implementation boundaries.
- Do not duplicate business logic into prompts, adapters or generated governance files.
- Do not silently change external API, schema, billing, auth, deployment or persistence behavior.

## High-risk integration boundaries

Ask before changing `.env*`, secrets, credentials, deployment/runtime configuration, billing/Stripe behavior, database or migration behavior, CI workflows, dependency files, or commercial/legal product claims.

Never expose secret values. Use placeholders in examples.
