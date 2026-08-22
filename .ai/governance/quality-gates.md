# Quality Gates

Use targeted validation appropriate to the change.

## Repository validation

This repository currently does not expose a verified test runner or dependency manifest in the inspected root files. For governance/documentation changes, use:

```bash
git diff --check
```

If source/runtime files are added later, derive validation commands from actual repository configuration before running or documenting them.

## Governance-only validation

```bash
git diff --check
git status --short
```

Before completion, inspect the diff and confirm:

- `AGENTS.md` remains the universal AI entrypoint.
- `.ai/` remains IDE-neutral.
- IDE-specific files are adapters only and do not redefine repository standards.
- No secrets, provider credentials, production configuration, migrations or deployment behavior were changed.
- Repository-specific safety and architecture rules are preserved.
