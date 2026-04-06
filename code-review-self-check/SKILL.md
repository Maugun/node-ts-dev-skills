---
name: code-review-self-check
description: Perform a self-review on completed work by looking for bugs, regressions, missing tests, documentation drift, maintainability issues, and risky assumptions before handing the work off. Use when Codex needs a reviewer mindset on its own changes during development.
---

# Code Review Self Check

Review your own work before handing it off.

Adopt a reviewer mindset.
Look for bugs, regressions, missing tests, unclear code, and stale documentation.
When the change touches frontend UI, review whether desktop, tablet, and mobile behavior still make sense.
Prefer concrete findings over generic approval language.

Do not assume the code is correct because it compiles.
Do not treat self-review as a formatting pass only.
Do not skip risky assumptions or missing verification.

## Workflow

1. Inspect the changed files and the surrounding context.
2. Review behavior first, then tests, then documentation, then maintainability.
3. Look for what could break in real usage.
4. Report concrete findings clearly.
5. If no issues are found, say so explicitly and mention any remaining validation gaps.

## Review Priorities

Review in roughly this order:

1. behavioral bugs
2. regressions
3. missing or weak tests
4. security-sensitive mistakes
5. documentation drift
6. maintainability or readability issues

## Questions To Ask

1. Does this change actually solve the intended problem?
2. Could this break an existing path?
3. Is there missing validation, error handling, or edge-case handling?
4. Are the tests sufficient for the risk of the change?
5. Does the documentation still match the implementation?
6. Did the change introduce unnecessary complexity?
7. If this touched frontend UI, could it have broken responsive behavior on desktop, tablet, or mobile?

## Reporting Rules

When issues are found:

1. report the most severe findings first
2. prefer concrete file-level observations
3. distinguish confirmed problems from residual risks

When no issues are found:

1. say that explicitly
2. mention what was checked
3. mention what was not verified if important checks were not run

## Common Pitfalls

- Do not stop at style comments if there may be behavioral issues.
- Do not ignore missing tests after non-trivial logic changes.
- Do not mark work as safe if important checks were skipped.
- Do not confuse "looks clean" with "is correct".
- Do not assume a frontend change is safe if it was only considered on one viewport size.


