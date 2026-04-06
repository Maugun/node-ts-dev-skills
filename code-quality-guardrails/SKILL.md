---
name: code-quality-guardrails
description: Keep implementation work aligned with project coding conventions, local structure, readability expectations, and configured linting and formatting rules. Use when Codex needs to write or update code during normal project development.
---

# Code Quality Guardrails

Write code that fits the project.

Respect the existing architecture.
Respect local naming and file organization.
Respect ESLint and Prettier configuration.
When the change touches frontend UI, preserve responsive behavior across desktop, tablet, and mobile.
When the change touches frontend UI text, prefer the project's content or config source over hardcoded component strings.
When the change touches frontend assets or integrations, prefer local bundled files over external `<link>` and `<script>` dependencies.

Do not rewrite large areas without a reason.
Do not introduce style drift from nearby code.
Do not rely on lint fixes alone as a substitute for thoughtful implementation.

## Workflow

1. Inspect nearby files before editing.
2. Match local patterns unless they are clearly broken and the user wants cleanup.
3. Keep changes as small and understandable as possible.
4. Run the relevant formatter and linter checks after editing when available.

## Coding Rules

1. Prefer consistency with neighboring code over abstract stylistic ideals.
2. Keep functions, modules, and components focused.
3. Avoid cleverness that harms readability.
4. Use the established abstractions before inventing new ones.
5. Respect configured ESLint and Prettier rules.
6. When changing frontend UI, maintain responsive behavior across desktop, tablet, and mobile.
7. When changing frontend copy, keep text in a dedicated content or config source whenever the project supports that pattern.
8. When changing frontend assets or integrations, prefer local bundled and, when useful, minimized files over external hosted dependencies.

## Change Scope Rules

1. Fix the requested problem first.
2. Avoid opportunistic refactors unless they are necessary to complete the task safely.
3. Keep unrelated cleanup separate from functional work.

## Common Pitfalls

- Do not introduce a new naming convention in one file.
- Do not reformat unrelated files without a reason.
- Do not ignore warnings that point to real maintainability issues.
- Do not bypass lint or formatting rules instead of working with them.
- Do not ship frontend UI changes that only work on one viewport when the project is expected to be responsive.
- Do not hardcode new frontend copy in components when the project expects centralized content for dynamic rendering or translation.
- Do not introduce external `<script>` or `<link>` dependencies into frontend code when local bundled assets are practical.
- Do not depend on third-party hosted frontend assets by default when a local minimized version can be kept in the project.






