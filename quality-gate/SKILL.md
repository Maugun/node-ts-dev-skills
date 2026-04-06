---
name: quality-gate
description: Perform a verification pass before a commit or after an important implementation step by checking tests, lint, formatting, documentation alignment, and security-sensitive changes. Use when Codex needs a final quality check on project work.
---

# Quality Gate

Run a practical verification pass before a commit or after a meaningful development step.

Check what changed.
Run the relevant validations.
Call out remaining risks clearly.

Do not run irrelevant checks just for ceremony.
Do not skip important checks when the changed surface is risky.
Do not claim success if important validations were not run.

## Workflow

1. Inspect the changed files.
2. Determine which checks are relevant.
3. Run the relevant validations.
4. Summarize failures, gaps, and residual risks clearly.

## Core Checks

Use the relevant subset of these:

1. lint
2. formatting
3. tests
4. build or type-check
5. documentation alignment
6. security-sensitive review
7. responsive UI verification when frontend screens or layouts changed
8. frontend asset sourcing verification when scripts, styles, fonts, or linked assets changed

## Decision Rules

Always prefer relevant checks over exhaustive ritual.

For code changes, usually check:

1. lint
2. tests relevant to the change
3. type-check or build when applicable
4. local asset sourcing when frontend scripts, styles, fonts, or linked assets changed

For setup or workflow changes, usually check:

1. docs alignment
2. config validity
3. CI or script consistency

For auth, API, env, dependency, or CI changes, add a security-minded review pass.

## Reporting Rules

When reporting the outcome:

1. say what was verified
2. say what failed
3. say what was not verified
4. say whether the change is ready or still risky

## Common Pitfalls

- Do not say everything is good if tests were never run.
- Do not ignore documentation drift after changing setup or commands.
- Do not skip security-sensitive review for auth, env, CI, or dependency changes.
- Do not run a huge battery of checks when only a small relevant subset is needed.
- Do not skip responsive verification when frontend layout, spacing, navigation, or components changed.
- Do not skip checking for unintended external frontend `<script>` or `<link>` dependencies when frontend asset sourcing changed.




