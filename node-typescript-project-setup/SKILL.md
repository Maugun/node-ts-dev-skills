---
name: node-typescript-project-setup
description: Set up Node.js and TypeScript in a new project using the latest Node.js LTS line and the current stable TypeScript release, with version verification before installation. Use when Codex needs to initialize or standardize a local JavaScript or TypeScript project runtime and compiler setup.
---

# Node TypeScript Project Setup

Set up Node.js and TypeScript directly inside the target project.

Use the latest Node.js LTS release line.
Use the current stable TypeScript release.
Verify both versions before installation because they change over time.

Do not hardcode stale versions if fresher official versions are available.
Do not install prerelease or beta TypeScript unless the user explicitly asks for it.
Do not switch to a non-LTS Node.js release unless the user explicitly asks for it.

## Current Reference Versions

As of 2026-04-05:

1. Node.js latest LTS line: `v24`, with `v24.14.0` shown as latest LTS on the official Node.js releases page.
2. TypeScript current stable version: `6.0.2`, verified from the npm registry.

Treat these as reference values, not eternal constants.
Re-check before installing if network access is available.

## Workflow

1. Inspect the target project for an existing Node.js version file such as `.nvmrc`, `.node-version`, `package.json`, `tsconfig.json`, or an existing `typescript` dependency.
2. Verify the latest Node.js LTS version from the official Node.js releases page when possible.
3. Verify the latest stable TypeScript version from the npm registry when possible.
4. Install or align Node.js to the latest LTS line.
5. Install `typescript` as a dev dependency.
6. Create a baseline `tsconfig.json` only if the project does not already have one.
7. Validate with `node -v`, `npx tsc -v`, and a TypeScript no-emit check when relevant.

## Version Verification

Before installing, prefer these checks:

1. Check the official Node.js releases page for the latest LTS branch and patch.
2. Check `npm view typescript version` for the latest stable TypeScript release.

If browsing or registry access is unavailable:

1. Use the reference versions in this skill.
2. State clearly that the versions were not re-verified online.

## Node.js Setup

Prefer a version manager when possible.

If the project uses `.nvmrc`, write the current LTS major or exact LTS version there depending on team convention.

Examples:

```bash
node -v
```

If `nvm` is available:

```bash
nvm install 24
nvm use 24
```

If the user wants exact patch pinning and the verified version is `24.14.0`:

```bash
nvm install 24.14.0
nvm use 24.14.0
```

If the project has no Node version file, consider adding one of these if it matches local conventions:

1. `.nvmrc`
2. `.node-version`

Prefer the simplest value that matches team conventions:

```text
24
```

or

```text
24.14.0
```

## TypeScript Setup

Install TypeScript as a dev dependency:

```bash
npm install -D typescript@latest
```

If you already verified the current stable version and need reproducibility, prefer the exact version:

```bash
npm install -D typescript@6.0.2
```

Do not use `@beta`, `@next`, or prerelease tags unless the user explicitly asks for them.

## Baseline `tsconfig.json`

If the target project does not already have a `tsconfig.json`, create a minimal baseline:

```json
{
    "compilerOptions": {
        "target": "ES2022",
        "module": "ESNext",
        "moduleResolution": "Bundler",
        "strict": true,
        "skipLibCheck": true,
        "noEmit": true
    },
    "include": ["src"]
}
```

Adjust `module` or `moduleResolution` only if the repository already uses a different runtime model such as NodeNext.

## Integration Rules

If the project already has Node or TypeScript configured:

1. Preserve existing project-specific compiler options unless they are clearly broken.
2. Avoid downgrading Node.js or TypeScript automatically.
3. Avoid rewriting `tsconfig.json` from scratch when a targeted edit is enough.
4. Keep version files and `package.json` aligned.

If the project is JavaScript-only but the user still asks for TypeScript setup:

1. Install TypeScript only if requested.
2. Create `tsconfig.json` only if it serves a real purpose such as type-checking JS or preparing TS adoption.

## Validation

After setup:

1. Run `node -v` and confirm it matches the selected LTS line.
2. Run `npx tsc -v` and confirm it matches the selected TypeScript version.
3. If the project has TS sources or a `tsconfig.json`, run:

```bash
npx tsc --noEmit
```

4. Fix only integration issues such as missing config, mismatched module settings, or missing dependencies.

## Common Pitfalls

- Do not install a Current Node.js release when the task asks for LTS.
- Do not assume the latest LTS major is stable forever; re-check it.
- Do not install a TypeScript beta by mistake.
- Do not overwrite an existing `tsconfig.json` without reading it first.
- Do not force `moduleResolution: Bundler` into back-end Node projects that clearly need `NodeNext` or another model.
