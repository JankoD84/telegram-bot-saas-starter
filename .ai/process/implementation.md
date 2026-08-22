# Implementation Process

1. Identify the task and work mode.
2. Run Git preflight from the repository root:

   ```bash
   git status --short
   git branch --show-current
   git log -1 --oneline
   git diff --stat
   ```

3. Read `AGENTS.md`, `.ai/repo/context.md`, `.ai/governance/engineering.md`, `README.md`, `ARCHITECTURE.md`, and relevant `docs/` files.
4. Verify current repository files before assuming source layout, tests, deployment assets, or dependency manifests exist.
5. Make the smallest safe change within the requested scope.
6. Avoid production, deployment, billing, credential, database/migration, CI, and dependency changes unless explicitly requested.
7. Derive validation commands from actual repository configuration. Do not invent missing scripts.
8. Update documentation when architecture, commands, billing behavior, deployment expectations, or buyer-facing contracts change.
9. Run `git diff --check` and inspect the exact diff.
10. Report files changed, validation, risks, and commit message.

## Baseline validation

For governance/documentation-only changes:

```bash
git diff --check
```
