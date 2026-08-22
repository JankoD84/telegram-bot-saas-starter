# Safety Policy

## Mandatory start for implementation work

Check and report:

```bash
git status
git branch --show-current
git diff --stat
```

Then read:

- `AGENTS.md`
- `.ai/repo/profile.md`
- `.ai/repo/boundaries.md`
- `.ai/repo/commands.md`

## Protected areas

Ask before changing `.env*`, secrets, credentials, deployment/runtime configuration, billing/Stripe behavior, database or migration behavior, CI workflows, dependency files, or commercial/legal product claims.

Never expose secret values. Use placeholders in examples.

## Prohibited during normal AI implementation

- Do not expose or print secret values.
- Do not edit `.env*`, credentials or private keys.
- Do not run deployments, migrations or destructive cleanup commands without explicit approval.
- Do not modify provider credentials, model routing, LiteLLM, MCP runtime configuration, OAuth, AWS, Azure or ChatGPT subscription settings as part of AI-standards work.
- Do not commit, push, force-push, reset or stash automatically.
- Preserve unrelated working-tree changes.
