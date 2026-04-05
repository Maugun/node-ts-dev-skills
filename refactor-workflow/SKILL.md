---
name: refactor-workflow
description: Refactor code safely by preserving behavior, reducing risk, and validating each structural change against the existing project conventions and test coverage. Use when Codex needs to improve code structure during normal project development.
---

# Refactor Workflow

Refactor code safely.

Preserve behavior.
Reduce complexity or improve structure intentionally.
Keep the change understandable and verifiable.

Do not turn a refactor into an accidental feature change.
Do not mix broad stylistic cleanup with structural refactoring unless necessary.
Do not remove useful tests or verification during the refactor.

## Workflow

1. Define the reason for the refactor.
2. Identify the behavior that must stay unchanged.
3. Prefer small structural steps over one large rewrite.
4. Keep tests and verification close to the changed behavior.
5. Re-run relevant checks after the refactor.

## Good Reasons To Refactor

1. duplicated logic
2. unclear module boundaries
3. overly large functions or classes
4. tangled responsibilities
5. maintainability pain that blocks future changes

## Refactor Rules

1. Preserve inputs, outputs, and user-visible behavior unless the user explicitly asks for change.
2. Keep naming aligned with the project conventions.
3. Prefer extracting clear units over inventing abstract layers too early.
4. Keep unrelated cleanup out of the refactor unless it is required for safety.

## Verification

After the refactor:

1. run relevant tests
2. run lint and formatting checks when applicable
3. run type-check or build when architecture-sensitive code changed
4. confirm behavior remains the same

## Common Pitfalls

- Do not mix refactor and feature work without making that explicit.
- Do not rewrite everything just because one file is messy.
- Do not remove regression coverage while restructuring code.
- Do not claim a refactor is safe without verification.
