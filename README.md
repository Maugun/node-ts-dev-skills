# Project Setup Skills

This repository contains a set of reusable Codex skills to bootstrap and standardize software projects.

The skills are designed to work together:

- `project-bootstrap` acts as the orchestrator
- stack-specific skills handle frontend, backend, and full-stack choices
- transversal skills handle tooling such as Git, Node.js, TypeScript, ESLint, Prettier, tests, CI, and README setup

## Repository Structure

Each folder contains a single `SKILL.md` file:

- `project-bootstrap`
- `fullstack-project-setup`
- `frontend-project-setup`
- `backend-project-setup`
- `git-project-setup`
- `readme-project-setup`
- `node-typescript-project-setup`
- `package-manager-project-setup`
- `env-project-setup`
- `prettier-project-setup`
- `eslint-project-setup`
- `testing-project-setup`
- `ci-project-setup`

## Skill Overview

### Orchestration

- `project-bootstrap`: inspects a repository, asks a few high-impact questions when needed, then applies the relevant setup skills in a sensible order.
- `fullstack-project-setup`: coordinates shared decisions for projects that contain both frontend and backend slices.

### Stack Selection

- `frontend-project-setup`: frontend setup defaults to React, Vite, and Tailwind CSS unless the user chooses otherwise.
- `backend-project-setup`: backend setup defaults to NestJS, REST, MongoDB, no ORM, auth, `class-validator`, and tests with Jest and Nock unless the user chooses otherwise.

### Tooling

- `git-project-setup`: initializes Git hygiene, including `.gitignore` and first-commit guidance.
- `node-typescript-project-setup`: sets up Node.js using the latest LTS line and TypeScript using the current stable release.
- `package-manager-project-setup`: standardizes `npm`, `pnpm`, or `yarn` and avoids mixed lockfiles.
- `env-project-setup`: sets up safe environment variable handling with `.env.example`.
- `prettier-project-setup`: applies the shared Prettier baseline.
- `eslint-project-setup`: applies the shared ESLint baseline.
- `testing-project-setup`: adds a minimal but real testing setup aligned with the project stack.
- `ci-project-setup`: adds a minimal CI workflow aligned with the real project scripts.
- `readme-project-setup`: creates or rewrites `README.md` based on the actual project state.

## Recommended Usage

## Installing The Skills In A Project

To use these skills in another project, copy the skill folders into a Codex-discoverable skills directory.

The usual location is:

```text
~/.codex/skills/
```

Each skill must stay in its own folder and must contain its `SKILL.md` file.

Example target structure:

```text
~/.codex/skills/
  project-bootstrap/
    SKILL.md
  fullstack-project-setup/
    SKILL.md
  frontend-project-setup/
    SKILL.md
  backend-project-setup/
    SKILL.md
  git-project-setup/
    SKILL.md
  readme-project-setup/
    SKILL.md
  node-typescript-project-setup/
    SKILL.md
  package-manager-project-setup/
    SKILL.md
  env-project-setup/
    SKILL.md
  prettier-project-setup/
    SKILL.md
  eslint-project-setup/
    SKILL.md
  testing-project-setup/
    SKILL.md
  ci-project-setup/
    SKILL.md
```

If you want to install only the main entrypoint, start by copying:

1. `project-bootstrap`
2. the stack skill you expect to need most often: `frontend-project-setup`, `backend-project-setup`, or `fullstack-project-setup`
3. the transversal tooling skills used by the bootstrap flow

To keep everything working together, the simplest option is to copy all folders as-is.

## Using The Skills From A Project

Once the folders are placed in the skills directory, open the target project and invoke the skill by name.

Examples:

```text
Use $project-bootstrap to set up this project.
Use $frontend-project-setup to define the frontend stack.
Use $backend-project-setup to define the backend stack.
Use $readme-project-setup to write the README.
```

If you maintain a dedicated internal skills repository, keep the folder names unchanged so the skill names remain consistent.

For a new project, start with:

```text
Use $project-bootstrap to set up this project.
```

The bootstrap skill is designed to:

1. inspect the repository first
2. infer as much as possible from existing files
3. ask only the questions that materially affect the setup
4. apply the relevant skills in order

For more targeted work, use a specific skill directly:

- `Use $frontend-project-setup to define the frontend stack`
- `Use $backend-project-setup to define the backend stack`
- `Use $git-project-setup to initialize the repository`
- `Use $readme-project-setup to write the README`

## Typical Setup Flow

For a generic new project, the usual flow is:

1. `project-bootstrap`
2. `frontend-project-setup`, `backend-project-setup`, or `fullstack-project-setup` when relevant
3. `package-manager-project-setup`
4. `node-typescript-project-setup`
5. `env-project-setup`
6. `prettier-project-setup`
7. `eslint-project-setup`
8. `testing-project-setup`
9. `ci-project-setup`
10. `readme-project-setup`

## Notes

- The skills are written to avoid unnecessary questions when the repository already contains the answer.
- The stack defaults are opinionated but overridable.
- The bootstrap layer is intended to keep setup coherent instead of applying every skill blindly.
