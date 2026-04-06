---
name: frontend-project-setup
description: Set up a frontend project by selecting the UI stack and applying sensible defaults for framework, build tool, styling, and related frontend decisions. Use when Codex needs to initialize or standardize a frontend application, especially when the user has not fully specified the stack yet.
---

# Frontend Project Setup

Set up the frontend stack directly inside the target project.

Ask only the frontend-specific questions that materially change the stack.
Prefer a small set of consistent defaults when the user does not choose explicitly.
Keep the selected stack coherent across tooling, scripts, and documentation.
Ensure the frontend is responsive across desktop, tablet, and mobile by default.
Keep UI text in a dedicated content or config source instead of hardcoding strings inside components.
Avoid external frontend asset dependencies when possible, especially third-party `<link>` and `<script>` tags.

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
5. Ensure the frontend implementation handles desktop, tablet, and mobile layouts appropriately.
6. Align package scripts, config files, README notes, and testing choices with the selected stack.

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
4. store frontend copy in a dedicated content or config layer rather than inline in components

Keep the implementation consistent with those defaults in:

1. dependencies
2. scripts
3. project structure
4. README instructions
5. CI commands
6. responsive behavior across desktop, tablet, and mobile
7. content sourcing for UI text
8. local asset sourcing instead of external frontend links and scripts

## Content And Text Rules

When building frontend UI:

1. keep user-facing text in a dedicated content or config source
2. avoid scattering hardcoded copy across components
3. prefer a structure that supports dynamic rendering and future translation
4. prefer a typed content module when the project already uses TypeScript heavily
5. a JSON file is acceptable when the project wants plain content files and minimal logic
6. prefer local, bundled frontend assets over externally hosted assets when practical
7. prefer minimized local assets when the project benefits from shipping them directly
8. treat third-party CDN `<script>` and `<link>` usage as an exception, not a default
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
- Do not treat responsive behavior as optional for frontend work unless the user explicitly narrows the target surface.
- Do not hardcode large amounts of UI copy directly inside components when a dedicated content/config source would make dynamic rendering and translation easier.
- Do not rely by default on external `<script>` or `<link>` dependencies when local bundled assets would work.
- Do not introduce external frontend assets without a good reason when a local minimized version is possible.





