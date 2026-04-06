---
name: fullstack-project-setup
description: Set up a full-stack project by coordinating frontend and backend stack decisions, shared project structure, shared tooling, and app-to-api integration choices. Use when Codex needs to initialize or standardize a project that contains both a frontend and a backend.
---

# Fullstack Project Setup

Set up the full-stack project directly inside the target repository.

Treat frontend and backend as separate slices with shared conventions.
Ask only the cross-cutting questions that materially affect both sides.
Keep the chosen frontend and backend stacks coherent with shared tooling.
Ensure the frontend slice remains responsive across desktop, tablet, and mobile by default.
Keep frontend user-facing text in a dedicated content or config source instead of scattering strings through components.

Default full-stack baseline:

1. frontend: React + Vite + Tailwind CSS
2. backend: NestJS + REST + MongoDB + no ORM + auth + `class-validator` + Jest + Nock
3. package manager: `npm`
4. language: TypeScript

Do not blur frontend and backend responsibilities.
Do not force a monorepo layout unless the user wants one.
Do not assume deployment architecture unless the user asks for it.

## Workflow

1. Inspect the repository for existing frontend and backend slices.
2. Determine whether the project is already split or still needs structure decisions.
3. Ask only the missing high-impact full-stack questions.
4. Decide the shared conventions first.
5. Then delegate frontend-specific and backend-specific setup to the dedicated skills.
6. Ensure the frontend slice handles desktop, tablet, and mobile layouts appropriately.
7. Align shared tooling across both slices.

## Cross-Cutting Questions

Ask only if the repository does not already answer them:

1. Should the project be a single repository with `frontend/` and `backend/` folders, or another structure?
2. Should frontend and backend share the same package manager?
3. Should both slices use TypeScript?
4. Should the frontend call the backend through a local REST API now?
5. Should CI validate both slices together?

If the user does not specify:

1. use one repository
2. use `frontend/` and `backend/` folders when a split is needed
3. use one package manager for both slices
4. use TypeScript for both
5. assume the frontend consumes the backend REST API
6. validate both slices in CI

## Shared Structure Guidance

When the repository is new and needs a split, prefer:

```text
frontend/
backend/
```

Only use another structure if the user or repository already defines it.

## Shared Tooling Rules

Keep these aligned across the full-stack project unless there is a strong reason not to:

1. package manager
2. Node.js version
3. TypeScript baseline
4. formatting rules
5. linting rules
6. CI entrypoint
7. README structure

## Delegation Rules

Use `frontend-project-setup` for frontend-specific decisions:

1. framework
2. build tool
3. styling
4. routing
5. frontend-specific testing

Use `backend-project-setup` for backend-specific decisions:

1. framework
2. API style
3. database
4. ORM/ODM choice
5. auth
6. validation
7. backend-specific testing

Use the generic companion skills after stack decisions are made:

1. `package-manager-project-setup`
2. `node-typescript-project-setup`
3. `env-project-setup`
4. `prettier-project-setup`
5. `eslint-project-setup`
6. `testing-project-setup`
7. `ci-project-setup`
8. `readme-project-setup`
9. `git-project-setup`

## Integration Guidance

When both slices are present:

1. document how the frontend reaches the backend
2. keep env handling separated when variables are slice-specific
3. align scripts so root documentation stays understandable
4. avoid duplicating contradictory setup instructions
5. ensure the frontend slice is responsive across desktop, tablet, and mobile
6. keep frontend copy centralized so dynamic components and future translation remain manageable

## Validation

After setup:

1. confirm both slices exist or are intentionally combined
2. confirm shared tooling choices are aligned
3. confirm frontend and backend commands are documented clearly
4. confirm CI and README reflect the two-slice structure

## Common Pitfalls

- Do not apply frontend defaults to the backend slice.
- Do not apply backend defaults to the frontend slice.
- Do not create two unrelated package manager conventions in one repository.
- Do not leave the project structure ambiguous after setup.
- Do not document integration paths that are not implemented.
- Do not treat responsive frontend behavior as optional in full-stack app setup unless the user explicitly says otherwise.
- Do not spread frontend UI strings across components when a dedicated content/config source would keep the full-stack frontend easier to evolve and translate.



