---
name: testing-project-setup
description: Set up automated testing in a new project with a minimal but real test runner configuration, sensible test scripts, and a small verification path that matches the stack. Use when Codex needs to initialize or standardize testing in a local JavaScript or TypeScript project.
---

# Testing Project Setup

Set up testing directly inside the target project.

Prefer a minimal real testing setup over a large speculative one.
Match the chosen test tool to the stack.
Keep commands simple and verifiable.

Do not add multiple test frameworks unless the user explicitly asks for them.
Do not create placeholder tests that prove nothing.
Do not document test commands that do not run.

## Workflow

1. Inspect the project stack, build tool, runtime, and existing dependencies.
2. Detect whether testing already exists.
3. If no framework exists, choose one that matches the project style.
4. Add the minimal config and scripts needed to run real tests.
5. Add one representative test only when it materially helps bootstrap the project.

## Framework Selection

Prefer these defaults:

1. `vitest` for Vite, modern frontend, and many TS-first app projects.
2. `jest` only when the project already uses Jest or has ecosystem-specific reasons.
3. Use `playwright` or similar only when the user explicitly asks for end-to-end testing.

If the project already has a test framework, keep it.

## Minimal Scripts

When using Vitest, prefer:

```json
{
    "scripts": {
        "test": "vitest run",
        "test:watch": "vitest"
    }
}
```

When using Jest, prefer:

```json
{
    "scripts": {
        "test": "jest --runInBand"
    }
}
```

## Representative Test

If a sample test is useful, keep it small and meaningful.

Good examples:

1. a pure utility function test
2. a config parser test
3. a simple component render test if UI testing is already in scope

Avoid artificial tests such as `expect(true).toBe(true)`.

## Validation

After setup:

1. Run the test command.
2. Confirm the script names match README and CI.
3. Confirm the chosen framework matches the stack.
4. Remove bootstrap tests that add noise and no confidence.

## Common Pitfalls

- Do not install both Vitest and Jest by default.
- Do not add browser-heavy test tools to a simple library without a clear need.
- Do not create test setup files that are never used.
- Do not leave broken snapshots or placeholder assertions.
