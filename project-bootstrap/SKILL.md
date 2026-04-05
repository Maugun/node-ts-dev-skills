---
name: project-bootstrap
description: Bootstrap a new local project by asking a few high-impact setup questions first, then orchestrating Git, README, Node.js, TypeScript, package manager, environment, formatting, linting, testing, and CI skills in a sensible order. Use when Codex needs to initialize or standardize a project foundation end to end.
---

# Project Bootstrap

Bootstrap the target project in a structured way.

Start by inspecting the repository.
Ask a few short questions only when the answers materially change the setup.
Then apply the relevant setup skills in a sensible order.

Do not ask unnecessary questions when the repository already answers them.
Do not front-load too many decisions.
Do not run every setup skill blindly if some are irrelevant.

## Available Companion Skills

Use these skills from the current workspace when relevant:

1. [../git-project-setup/SKILL.md](../git-project-setup/SKILL.md)
2. [../frontend-project-setup/SKILL.md](../frontend-project-setup/SKILL.md)
3. [../backend-project-setup/SKILL.md](../backend-project-setup/SKILL.md)
4. [../fullstack-project-setup/SKILL.md](../fullstack-project-setup/SKILL.md)
5. [../readme-project-setup/SKILL.md](../readme-project-setup/SKILL.md)
6. [../node-typescript-project-setup/SKILL.md](../node-typescript-project-setup/SKILL.md)
7. [../package-manager-project-setup/SKILL.md](../package-manager-project-setup/SKILL.md)
8. [../env-project-setup/SKILL.md](../env-project-setup/SKILL.md)
9. [../prettier-project-setup/SKILL.md](../prettier-project-setup/SKILL.md)
10. [../eslint-project-setup/SKILL.md](../eslint-project-setup/SKILL.md)
11. [../testing-project-setup/SKILL.md](../testing-project-setup/SKILL.md)
12. [../ci-project-setup/SKILL.md](../ci-project-setup/SKILL.md)

Load only the skills that are actually needed.

## Bootstrap Workflow

1. Inspect the repository first.
2. Infer as much as possible from existing files.
3. Ask only the missing high-impact questions.
4. Summarize the setup plan briefly.
5. Apply the selected skills in order.
6. Validate the resulting setup with the project's real commands.

## Initial Inspection

Inspect these when present:

1. `.git/`
2. `package.json`
3. lockfiles
4. `README.md`
5. `.gitignore`
6. `.env.example`
7. `eslint.config.*`
8. `.prettierrc*`
9. `tsconfig.json`
10. `.github/workflows/*`
11. existing test files or test dependencies

Use repository evidence to avoid redundant questions.

## Question Phase

Ask questions only if the repository does not already answer them clearly.

Prefer 3 to 5 short questions maximum.

High-impact questions to ask when needed:

1. What kind of project is this: app, library, or internal tooling?
2. Which package manager should be used: npm, pnpm, or yarn?
3. Should the project use TypeScript?
4. Should testing be included now?
5. Should CI be included now?

Optional questions only if necessary:

1. Is this frontend, backend, or full-stack?
2. Should Git be initialized and should an initial commit be prepared?
3. Is GitHub Actions the intended CI platform?

Do not ask about choices already visible in the repository.

## Default Assumptions

If the user does not specify and the repository does not decide:

1. treat the project as an app
2. if the project is frontend, use React + Vite + Tailwind CSS
3. if the project is backend, use NestJS + REST + MongoDB + no ORM + auth + `class-validator` + Jest + Nock
4. use `npm`
5. use TypeScript for new Node/JS projects
6. include Prettier
7. include ESLint
8. include Git setup
9. include a README
10. defer testing and CI only if the user seems to want a very minimal bootstrap

State the assumptions before applying them.

## Recommended Order

Apply setup in this general order:

1. Git
2. frontend or backend stack selection when needed
3. package manager
4. Node.js and TypeScript
5. env handling
6. Prettier
7. ESLint
8. testing
9. CI
10. README

Adjust the order when the repository already contains some of these pieces.

## Skill Orchestration Rules

Use `git-project-setup` when:

1. there is no `.gitignore`
2. Git is not initialized
3. repository hygiene needs cleanup

Use `package-manager-project-setup` when:

1. there is no clear package manager
2. lockfiles conflict
3. scripts and docs need alignment

Use `frontend-project-setup` when:

1. the project is a frontend app
2. the project is full-stack and the frontend slice needs stack decisions
3. the user has not fully specified the frontend stack

Use `backend-project-setup` when:

1. the project is a backend app
2. the project is full-stack and the backend slice needs stack decisions
3. the user has not fully specified the backend stack

Use `fullstack-project-setup` when:

1. the project is explicitly full-stack
2. both frontend and backend slices need coordination
3. shared structure and shared tooling decisions matter before slice-specific setup

Use `node-typescript-project-setup` when:

1. Node.js or TypeScript versions are missing
2. `tsconfig.json` is missing but TypeScript is intended
3. version files such as `.nvmrc` are missing and useful

Use `env-project-setup` when:

1. the app depends on environment variables
2. `.env.example` is missing
3. `.gitignore` does not properly protect env files

Use `prettier-project-setup` when:

1. formatting is not configured
2. the repository wants a shared formatting baseline

Use `eslint-project-setup` when:

1. linting is not configured
2. the project is JavaScript or TypeScript and wants a lint baseline

Use `testing-project-setup` when:

1. the user wants tests now
2. the repository already contains tests but setup is incomplete

Use `ci-project-setup` when:

1. the user wants CI now
2. the repository already has quality scripts worth enforcing in CI

Use `readme-project-setup` when:

1. `README.md` is missing
2. `README.md` is outdated
3. the bootstrap materially changes project setup

## Planning Message

Before editing, provide a short summary like this:

```text
I inspected the repository and found A, B, and C.
I still need decisions on X, Y, and Z.
After that, I will apply the relevant setup skills in this order: ...
```

After the user answers, provide a short execution plan.

## Validation

After bootstrap:

1. Re-run the key local commands that were introduced.
2. Confirm docs match scripts and tool choices.
3. Confirm ignored files are actually ignored.
4. Confirm config files do not contradict each other.

## Common Pitfalls

- Do not ask ten setup questions when three are enough.
- Do not apply CI before scripts exist.
- Do not document package manager commands that differ from the chosen tool.
- Do not create TypeScript config if the user explicitly wants a JS-only project.
- Do not overwrite existing project conventions without a reason.
