---
name: readme-project-setup
description: Create or improve a project README.md with a clear structure, practical setup steps, usage instructions, and maintenance-friendly sections. Use when Codex needs to add or rewrite a README for a new or existing software project.
---

# README Project Setup

Create or update `README.md` directly inside the target project.

Write for humans first.
Prefer clarity over marketing.
Keep setup and usage accurate to the actual repository.

Do not invent commands, scripts, features, or deployment steps.
Do not claim support for tools or workflows that are not present in the project.
Do not leave placeholder sections unless the user explicitly wants a template.

## Workflow

1. Inspect the project before writing the README.
2. Read `package.json`, main config files, entrypoints, and existing docs if they exist.
3. Identify what the project does, how to install it, how to run it, and how to contribute or maintain it.
4. Write a concise README that matches the real repository state.
5. Prefer a complete short README over a long speculative one.

## Core Structure

Use this structure when it fits the project:

```markdown
# Project Name

Short description of what the project does.

## Prerequisites

List required tools or runtime versions if they are known.

## Installation

Show how to install dependencies.

## Usage

Show how to run, build, test, or lint the project using real commands.

## Project Structure

Briefly describe the main folders only if it helps orientation.

## Configuration

Explain important environment variables, config files, or setup decisions when they are real and relevant.

## Scripts

List important package scripts if the project uses them.

## Contributing

Explain the local workflow briefly if contribution guidance is useful.
```

Remove sections that are not relevant.
Add sections only when they are supported by the repository.

## Writing Rules

1. Start with the project name and a one- or two-sentence description.
2. Use real commands copied from the repository when possible.
3. Prefer short sections with direct headings.
4. Explain unfamiliar setup requirements briefly.
5. Keep maintenance information practical.
6. Avoid vague filler such as "robust", "powerful", or "scalable" unless the repository proves it.

## Project Inspection Checklist

Before writing or rewriting the README, inspect these when relevant:

1. `package.json`
2. `README.md` if one already exists
3. lockfiles such as `package-lock.json`, `pnpm-lock.yaml`, or `yarn.lock`
4. app entrypoints such as `src/main.*`, `src/index.*`, `server.*`, or `app.*`
5. config files such as `vite.config.*`, `tsconfig.json`, `eslint.config.*`, `.prettierrc*`, Docker files, or CI files
6. environment examples such as `.env.example`

If the repository is too small for some sections, keep the README minimal.

## README Template Guidance

When the repository is a library or shared config package, prefer:

1. What it is
2. Installation
3. Usage example
4. Compatibility notes

When the repository is an app, prefer:

1. What it does
2. Prerequisites
3. Installation
4. Development commands
5. Build and run commands
6. Configuration notes

When the repository is internal tooling or automation, prefer:

1. Purpose
2. Required environment
3. Commands or invocation examples
4. Expected inputs and outputs

## Validation

After writing the README:

1. Re-check every command against the repository.
2. Re-check every mentioned tool or script.
3. Make sure the README does not describe deleted files or missing folders.
4. Make sure the opening description matches the repository's actual purpose.

## Common Pitfalls

- Do not document scripts that do not exist.
- Do not include secret values or real credentials.
- Do not add installation steps for package managers the project does not use.
- Do not create a huge architecture section for a small project.
- Do not leave TODO markers in the final README unless the user asks for a scaffold.
