# Repository Commands

Only run commands supported by repository files. Do not invent validation commands.

## Detected commands

- No repository-native install/test/build commands were detected from root manifests. Use `git diff --check` for Markdown/governance-only validation and inspect repository docs before running application commands.

## Always-safe governance validation

- `git diff --check`
- `git status --short`

Do not run deployment, migration, production startup or destructive cleanup commands merely as validation.
