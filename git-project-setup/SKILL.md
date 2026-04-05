---
name: git-project-setup
description: Set up Git in a new project with a clean repository structure, a sensible .gitignore, an initial commit workflow, and safe defaults for day-to-day development. Use when Codex needs to initialize or standardize Git setup in a new local project.
---

# Git Project Setup

Set up Git directly inside the target project.

Create a clean repository.
Add a sensible `.gitignore`.
Prepare the first commit without committing generated or secret files.

Do not add remote origins unless the user explicitly asks for them.
Do not commit secrets, environment files, certificates, or local databases.
Do not overwrite an existing `.gitignore` blindly.

## Workflow

1. Inspect the target project for an existing `.git` folder, `.gitignore`, `.env*` files, build folders, dependency folders, IDE files, and framework-specific outputs.
2. If Git is not initialized, run `git init`.
3. Create or update `.gitignore` with the baseline in this skill.
4. Review project-specific generated files and add ignore rules only when they are clearly local or generated.
5. Stage only the intended source files.
6. Create an initial commit only if the user asks for it, or if the task explicitly includes repository initialization through first commit.

## Baseline `.gitignore`

Use this as the default `.gitignore` for JavaScript, TypeScript, and general app projects.

Create `.gitignore` with this content when the project does not already have one:

```gitignore
# Dependencies
node_modules/

# Build outputs
dist/
build/
coverage/
.cache/
.turbo/
.next/
.nuxt/
.svelte-kit/
out/

# Environment and secrets
.env
.env.*
!.env.example

# Logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*

# OS files
.DS_Store
Thumbs.db

# Editors
.idea/
.vscode/

# Test and tooling artifacts
.eslintcache
*.tsbuildinfo

# Local databases and certificates
*.sqlite
*.sqlite3
*.db
*.pem
*.key
*.crt
```

If a `.gitignore` already exists:

1. Merge carefully instead of replacing it.
2. Keep existing project-specific ignore rules.
3. Remove duplicates when practical.

## Git Initialization

If the project has no Git repository:

```bash
git init
```

After initialization:

1. Check repository status with `git status`.
2. Verify that ignored files are really excluded.
3. Stage only intended files.

Useful commands:

```bash
git status
git add .
git add -A
git commit -m "chore: initial commit"
```

Prefer targeted staging when the project contains local files that might not yet be covered by `.gitignore`.

## Safe Defaults

When the user asks for a standard Git setup, prefer these conventions:

1. Use a clear default branch name if the environment supports it.
2. Keep commits small and descriptive.
3. Avoid checking in generated files unless the project explicitly relies on them.
4. Keep an `.env.example` file in version control when environment variables are needed, but never commit real `.env` files.

## Optional Local Config

Apply these only if the user asks for local Git preferences:

```bash
git config user.name "Your Name"
git config user.email "you@example.com"
git config core.autocrlf false
```

Do not set global Git config unless the user explicitly asks for global changes.

## Validation

After setup:

1. Run `git status`.
2. Confirm that dependency folders, build folders, logs, and `.env` files are ignored.
3. Confirm that source files and configuration files remain visible to Git.
4. If the user asked for a first commit, verify the staged file list before committing.

## Common Pitfalls

- Do not commit `.env`, `.env.local`, or similar secret-bearing files.
- Do not ignore lockfiles by default.
- Do not ignore source folders such as `src/`.
- Do not add `.vscode/` blindly if the project intentionally shares editor settings and the user wants them versioned.
- Do not stage everything automatically if the repository contains unclear local artifacts.
