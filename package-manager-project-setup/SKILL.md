---
name: package-manager-project-setup
description: Set up a package manager in a new JavaScript or TypeScript project, choose npm, pnpm, or yarn intentionally, keep one lockfile, and align scripts and metadata with the chosen tool. Use when Codex needs to initialize or standardize package manager setup in a local project.
---

# Package Manager Project Setup

Set up the package manager directly inside the target project.

Choose one package manager intentionally.
Keep only one lockfile.
Align commands, scripts, and documentation with the selected tool.

Do not mix `npm`, `pnpm`, and `yarn` in the same project unless the user explicitly asks for it.
Do not leave multiple lockfiles in the repository.
Do not switch package managers silently if the project is already standardized.

## Workflow

1. Inspect the target project for `package.json`, existing lockfiles, workspace files, and CI or README commands.
2. Detect whether the project already uses `npm`, `pnpm`, or `yarn`.
3. If there is no existing standard, prefer `npm` by default unless the user asks for another tool.
4. Keep or create the correct lockfile for the selected package manager.
5. Align scripts and docs with the selected tool.
6. If relevant, add the `packageManager` field to `package.json`.

## Selection Rules

Prefer these rules:

1. If `package-lock.json` exists, keep `npm`.
2. If `pnpm-lock.yaml` exists, keep `pnpm`.
3. If `yarn.lock` exists, keep `yarn`.
4. If nothing exists, default to `npm`.

Only migrate between package managers when the user explicitly asks for migration.

## Lockfiles

Keep exactly one of these:

1. `package-lock.json` for `npm`
2. `pnpm-lock.yaml` for `pnpm`
3. `yarn.lock` for `yarn`

If multiple lockfiles exist:

1. Ask whether the project is intentionally migrating.
2. If no migration is intended, keep the lockfile that matches the established project tool and remove the others only if the user wants cleanup.

## `packageManager` Field

When the project already has `package.json`, consider adding:

```json
{
    "packageManager": "npm@11"
}
```

Use the actual selected tool and major version if known.
Prefer adding this when the team benefits from reproducibility.

Examples:

1. `npm@11`
2. `pnpm@10`
3. `yarn@4`

## Script Alignment

Keep package scripts package-manager-agnostic when possible.

Good scripts:

```json
{
    "scripts": {
        "build": "tsc -p tsconfig.json",
        "dev": "vite",
        "lint": "eslint .",
        "format": "prettier --write .",
        "test": "vitest run"
    }
}
```

Avoid embedding another package manager inside scripts unless there is a strong reason.

## Workspaces

If the project is a monorepo:

1. Preserve existing workspace configuration.
2. Use the package manager's native workspace file or `package.json` workspace field.
3. Do not invent a monorepo layout unless the user explicitly asks for one.

## Validation

After setup:

1. Verify that exactly one lockfile is present.
2. Verify that install commands match the selected package manager.
3. Verify that README and CI commands do not mention a different tool.
4. If possible, run the package manager install command once.

## Common Pitfalls

- Do not keep multiple lockfiles.
- Do not document `pnpm` in README if the repo actually uses `npm`.
- Do not add `packageManager` with a guessed tool that conflicts with the lockfile.
- Do not migrate package managers silently.
