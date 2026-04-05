---
name: dependency-change
description: Add, update, or remove dependencies carefully by checking necessity, compatibility, security impact, project fit, and follow-up changes in scripts, docs, or configuration. Use when Codex needs to change project dependencies during normal development.
---

# Dependency Change

Change dependencies carefully.

Add only what is needed.
Prefer compatibility and maintainability over novelty.
Check the impact on code, scripts, docs, and security.

Do not add a dependency when the standard library or current stack already solves the problem well.
Do not update versions blindly.
Do not remove a dependency without verifying that nothing still relies on it.

## Workflow

1. Identify whether the dependency change is an add, update, or removal.
2. Check whether the change is actually needed.
3. Inspect compatibility with the current project stack.
4. Apply the dependency change.
5. Update related code, config, scripts, and docs when needed.
6. Re-run the relevant validations.

## Add Rules

Before adding a dependency, prefer to ask:

1. does the project already have an equivalent utility
2. can the platform or standard library handle this cleanly
3. does the new package fit the existing stack and conventions

Add the dependency only when it provides clear value.

## Update Rules

When updating a dependency:

1. check for breaking changes
2. check peer dependency expectations
3. check config or API differences
4. update docs or scripts if the workflow changes

## Removal Rules

When removing a dependency:

1. verify it is no longer imported or referenced
2. verify scripts and config no longer depend on it
3. verify related docs stay accurate

## Verification

After a dependency change, use the relevant subset of:

1. install verification
2. lint
3. tests
4. type-check
5. build
6. security-minded review when the dependency is sensitive

## Common Pitfalls

- Do not add a heavy dependency for a tiny helper need.
- Do not upgrade major versions without checking migration impact.
- Do not ignore peer dependency compatibility.
- Do not forget README, CI, or config updates after changing tooling dependencies.
