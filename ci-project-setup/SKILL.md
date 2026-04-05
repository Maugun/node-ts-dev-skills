---
name: ci-project-setup
description: Set up continuous integration for a local project with a minimal workflow that installs dependencies and runs the real quality checks such as lint, test, and build. Use when Codex needs to initialize or standardize CI in a repository, especially with GitHub Actions.
---

# CI Project Setup

Set up continuous integration directly inside the target repository.

Keep CI minimal, fast, and truthful.
Run only checks that the repository actually supports.
Prefer one clean workflow over many speculative ones.

Do not add CI steps for scripts that do not exist.
Do not add deploy jobs unless the user explicitly asks for deployment automation.
Do not pretend a matrix is needed when one runtime is enough.

## Workflow

1. Inspect the project for package manager, Node version, scripts, test setup, lint setup, and build tooling.
2. Detect whether CI already exists under `.github/workflows/` or another system.
3. If no CI exists, create a minimal GitHub Actions workflow unless the repository clearly uses another CI platform.
4. Run install, lint, test, and build only when corresponding scripts exist.
5. Keep the workflow aligned with the selected package manager and Node version.

## Default Workflow Shape

Prefer a single workflow such as `.github/workflows/ci.yml`.

Use these steps conceptually:

1. checkout
2. setup Node.js
3. install dependencies
4. run lint if available
5. run test if available
6. run build if available

## GitHub Actions Example

Use this as a baseline when the project uses `npm` and has `lint`, `test`, and `build` scripts:

```yaml
name: CI

on:
  push:
    branches: [main]
  pull_request:

jobs:
  ci:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 24
          cache: npm

      - name: Install dependencies
        run: npm ci

      - name: Lint
        run: npm run lint

      - name: Test
        run: npm run test

      - name: Build
        run: npm run build
```

Adapt:

1. `node-version` to the selected LTS line or the repository version file
2. install command to `pnpm install --frozen-lockfile` or `yarn install --immutable` when relevant
3. steps to omit unsupported scripts

## Alignment Rules

1. Keep CI commands identical to local scripts where possible.
2. Reuse the selected package manager.
3. Use one Node version by default unless a matrix adds real value.
4. Keep workflow names and job names short.

## Validation

After setup:

1. Confirm every CI command exists locally.
2. Confirm the workflow uses the correct package manager cache and install command.
3. Confirm the selected Node version matches project setup.
4. If possible, run the same commands locally before trusting the workflow.

## Common Pitfalls

- Do not use `npm install` in CI when `npm ci` is appropriate.
- Do not hardcode the wrong package manager.
- Do not add a build step if the repository has no build script.
- Do not create a large matrix without a real reason.
