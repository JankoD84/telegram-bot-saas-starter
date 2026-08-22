# Engineering Governance

- Preserve the documented framework/plugin boundary: reusable infrastructure stays separate from domain-specific bot behavior.
- Keep monetization semantics clear: subscription state, plan enforcement, Stripe checkout/webhooks, and rate limiting are security- and revenue-sensitive.
- Do not claim tests, commands, source layout, deployment automation, or dependency manifests exist unless verified in current repository files.
- Keep buyer-facing documentation accurate when product scope, stack, architecture, pricing, or support expectations change.
- Do not edit environment/secrets files, production deployment configuration, database/migration behavior, billing behavior, CI, or dependency files without explicit scope and approval.
- Do not introduce developer-agent model routing into repository governance.
