---
name: test-implementation
description: Add or update meaningful automated tests after project setup, choosing unit, integration, or functional coverage based on the type of change and the existing test stack. Use when Codex needs to implement tests during normal project development.
---

# Test Implementation

Add or update tests that provide real confidence.

Choose the smallest useful test level.
Match the existing test framework and project conventions.
Add tests when they materially reduce regression risk.

Do not add placeholder tests.
Do not force tests for trivial changes that gain no meaningful coverage.
Do not introduce a second test framework unless the user explicitly asks for it.

## Workflow

1. Inspect the existing test setup and current project conventions.
2. Determine whether the change needs tests.
3. Choose the appropriate level: unit, integration, or functional.
4. Add or update only the tests that materially improve confidence.
5. Run the relevant test commands after editing.

## Test Selection Rules

Prefer unit tests when:

1. the change is local and deterministic
2. business logic or utilities changed
3. edge cases can be covered without full app wiring

Prefer integration tests when:

1. multiple modules collaborate
2. API handlers, services, repositories, or config wiring changed
3. the bug risk lies in interaction between components

Prefer functional or end-to-end style tests when:

1. the behavior matters across the full request or user flow
2. route-level, screen-level, or workflow-level regressions are likely
3. the existing project already has that layer of testing

## When Not To Add Tests

Tests may be unnecessary when:

1. the change is purely documentation
2. the change is a harmless rename with no behavior change and existing coverage is already strong
3. the project area is intentionally outside test scope and the user does not want test expansion

If you skip tests, be able to explain why.

## Test Quality Rules

1. Test behavior, not implementation noise.
2. Prefer one clear assertion set over many redundant tests.
3. Keep fixtures small.
4. Avoid brittle snapshot-style coverage unless already established by the project.
5. Extend existing test files when that improves locality.

## Common Pitfalls

- Do not add `expect(true).toBe(true)` style filler.
- Do not duplicate coverage across multiple test layers without a reason.
- Do not test framework internals.
- Do not skip running the relevant tests after adding them.
