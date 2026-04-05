---
name: backend-project-setup
description: Set up a backend project by selecting the server stack and applying sensible defaults for framework, API style, database, validation, authentication, and testing. Use when Codex needs to initialize or standardize a backend application, especially when the user has not fully specified the stack yet.
---

# Backend Project Setup

Set up the backend stack directly inside the target project.

Ask only the backend-specific questions that materially change the stack.
Prefer a small set of consistent defaults when the user does not choose explicitly.
Keep the selected stack coherent across dependencies, config, validation, and tests.

Default backend stack:

1. NestJS
2. REST
3. MongoDB
4. no ORM
5. authentication enabled
6. `class-validator`
7. tests with Jest and Nock

Do not mix incompatible backend choices without a reason.
Do not add an ORM by default when the chosen default is no ORM.
Do not replace an existing backend stack unless the user explicitly asks for migration.

## Workflow

1. Inspect the repository for an existing backend stack before asking questions.
2. If the stack is already clear, preserve it.
3. If the project is new or ambiguous, ask only the missing backend questions.
4. Apply the selected backend stack.
5. Align scripts, config, env files, README notes, and tests with the chosen backend decisions.

## Question Phase

Ask only if the repository does not already answer these:

1. Which backend framework should be used?
2. Should the API be REST or GraphQL?
3. Which database should be used?
4. Should an ORM or ODM be used?
5. Should authentication be included now?
6. Which validation approach should be used?
7. Should backend tests be included now?

If the user does not specify:

1. framework: NestJS
2. API style: REST
3. database: MongoDB
4. ORM/ODM: none
5. auth: yes
6. validation: `class-validator`
7. tests: Jest and Nock

## Default Stack Rules

When no clear preference is provided:

1. use NestJS as the server framework
2. use REST controllers
3. use MongoDB as the database
4. do not introduce an ORM or ODM by default
5. include authentication scaffolding when auth is in scope
6. use `class-validator` for DTO validation
7. use Jest and Nock for testing

Keep the implementation consistent with those defaults in:

1. dependencies
2. scripts
3. application structure
4. README instructions
5. CI commands

## Integration Rules

If the repository already uses a backend stack:

1. preserve the existing framework unless migration is explicitly requested
2. preserve the existing API style unless a change is requested
3. preserve the existing database choice unless a change is requested

If the project is full-stack:

1. apply this skill only to the backend slice
2. keep backend decisions isolated from frontend conventions

## Recommended Follow-Up Skills

After the backend stack is chosen, use these skills as needed:

1. `node-typescript-project-setup`
2. `package-manager-project-setup`
3. `env-project-setup`
4. `prettier-project-setup`
5. `eslint-project-setup`
6. `testing-project-setup`
7. `ci-project-setup`
8. `readme-project-setup`

## Common Pitfalls

- Do not add Prisma, TypeORM, Mongoose, or another ORM/ODM by default when the chosen default is none.
- Do not scaffold GraphQL if the selected API style is REST.
- Do not add auth dependencies if authentication is explicitly out of scope.
- Do not mix validation approaches unnecessarily when `class-validator` is the chosen default.
- Do not document backend commands that do not exist in the repository.
