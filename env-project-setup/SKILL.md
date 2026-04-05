---
name: env-project-setup
description: Set up environment variable handling in a new project with a safe .env strategy, a committed .env.example, and clear separation between local secrets and versioned configuration. Use when Codex needs to initialize or standardize environment configuration in a local project.
---

# Env Project Setup

Set up environment variable handling directly inside the target project.

Keep secrets out of version control.
Document required variables clearly.
Commit examples, not real values.

Do not commit real `.env` files.
Do not put secrets in `README.md`.
Do not invent environment variables that the codebase does not use.

## Workflow

1. Inspect the project for existing `.env*` files, config loaders, deployment config, and code references to environment variables.
2. Identify which variables are required, optional, local-only, or deployment-specific.
3. Create or update `.env.example` with placeholder values only.
4. Ensure `.gitignore` excludes real `.env` files.
5. Document environment usage in README only at a high level.

## Baseline Files

Prefer this approach:

1. Keep `.env` local and ignored.
2. Commit `.env.example`.
3. Optionally support `.env.local` for developer overrides when the stack uses it.

Example `.env.example`:

```dotenv
NODE_ENV=development
PORT=3000
API_BASE_URL=http://localhost:3000
```

Use realistic placeholders, never real credentials.

## `.gitignore` Rules

Ensure these rules exist unless the project intentionally uses a different convention:

```gitignore
.env
.env.*
!.env.example
```

If the repository intentionally versions non-secret env files such as `.env.test`, preserve that convention only when it is clearly safe and already established.

## Documentation Rules

When documenting environment variables:

1. State what each variable is for.
2. Mention defaults only if they are real.
3. Explain required format briefly when needed.
4. Keep examples sanitized.

## Validation

After setup:

1. Confirm that `.env.example` exists when environment variables are required.
2. Confirm that real `.env` files are ignored.
3. Confirm that placeholder values are safe.
4. Confirm that the project can still start with the documented setup when enough variables are provided.

## Common Pitfalls

- Do not commit secrets.
- Do not commit production endpoints, tokens, or private keys.
- Do not leave `.env.example` empty when the app requires configuration.
- Do not document environment variables that do not exist in code or runtime config.
