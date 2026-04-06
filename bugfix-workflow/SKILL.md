---
name: bugfix-workflow
description: Fix bugs methodically by reproducing the issue, identifying the root cause, implementing the smallest safe correction, and verifying non-regression. Use when Codex needs to correct broken behavior during normal project development.
---

# Bugfix Workflow

Fix bugs methodically.

Reproduce first when possible.
Understand the root cause before changing code.
Prefer the smallest safe fix that resolves the real issue.

Do not patch symptoms blindly.
Do not widen the scope into a refactor unless necessary.
Do not claim a bug is fixed without verification.

## Workflow

1. Inspect the failing behavior, error report, or bug description.
2. Reproduce the problem when possible.
3. Trace the issue to the most likely root cause.
4. Apply the smallest safe fix.
5. If the bug touches frontend UI, check that the fix does not break desktop, tablet, or mobile behavior.
6. Add or update tests when they would meaningfully prevent regression.
7. Re-run the relevant checks after the fix.


## Root Cause Rules

Prefer fixing:

1. the incorrect assumption
2. the broken branch or condition
3. the missing validation or missing guard
4. the incorrect data flow

Avoid stopping at:

1. cosmetic symptom suppression
2. generic try/catch wrapping without understanding the failure
3. unrelated cleanup disguised as a fix

## Testing Guidance

Add or update tests when:

1. the bug is reproducible in an automated way
2. the affected behavior is important
3. the fix could regress later

If no test is added, be able to explain why.

## Verification

After the fix:

1. verify the original issue is resolved
2. run relevant tests
3. run lint or type checks if code paths changed
4. check for nearby regressions
5. if the bug touched frontend UI, check that responsive behavior still works across desktop, tablet, and mobile

## Common Pitfalls

- Do not fix a bug by hiding its output alone.
- Do not skip reproduction when it is realistically possible.
- Do not refactor large areas just because the bug touched them.
- Do not forget regression coverage when the failure pattern is testable.
- Do not fix one viewport-specific UI bug by accidentally breaking another viewport.


