---
name: frontend-project-setup
description: Set up a frontend project by selecting the UI stack and applying sensible defaults for framework, build tool, styling, and related frontend decisions. Use when Codex needs to initialize or standardize a frontend application, especially when the user has not fully specified the stack yet.
---

# Frontend Project Setup

Set up the frontend stack directly inside the target project.

Ask only the frontend-specific questions that materially change the stack.
Prefer a small set of consistent defaults when the user does not choose explicitly.
Keep the selected stack coherent across tooling, scripts, and documentation.

Default frontend stack:

1. React
2. Vite
3. Tailwind CSS

Do not mix multiple frontend frameworks.
Do not add extra state, routing, or testing libraries unless the user asks for them or the project clearly needs them.
Do not override an existing frontend stack without a reason.

## Workflow

1. Inspect the repository for an existing frontend stack before asking questions.
2. If the stack is already clear, preserve it.
3. If the project is new or ambiguous, ask only the missing frontend questions.
4. Apply the selected frontend stack.
5. Align package scripts, config files, README notes, and testing choices with the selected stack.

## Question Phase

Ask only if the repository does not already answer these:

1. Which frontend framework should be used?
2. Which build tool should be used?
3. Which styling approach should be used?
4. Is client-side routing needed now?
5. Is frontend testing needed now?

If the user does not specify:

1. framework: React
2. build tool: Vite
3. styling: Tailwind CSS
4. routing: no
5. testing: no additional frontend-specific testing beyond the generic testing skill unless asked

## Default Stack Rules

When no clear preference is provided:

1. use React as the UI framework
2. use Vite as the build tool
3. use Tailwind CSS for styling

Keep the implementation consistent with those defaults in:

1. dependencies
2. scripts
3. project structure
4. README instructions
5. CI commands

## Integration Rules

If the repository already uses a frontend stack:

1. preserve the existing framework
2. preserve the existing build tool
3. preserve the existing styling approach unless the user explicitly asks for migration

If the project is full-stack:

1. apply this skill only to the frontend slice
2. keep frontend decisions isolated from backend conventions

## Recommended Follow-Up Skills

After the frontend stack is chosen, use these skills as needed:

1. `node-typescript-project-setup`
2. `package-manager-project-setup`
3. `prettier-project-setup`
4. `eslint-project-setup`
5. `testing-project-setup`
6. `ci-project-setup`
7. `readme-project-setup`

## Common Pitfalls

- Do not ask framework questions when the repository already contains a clear frontend stack.
- Do not scaffold React and then document Vue commands.
- Do not add Tailwind CSS and another styling system by default.
- Do not add routing or state libraries unless they are needed.
