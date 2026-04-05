---
name: documentation-maintenance
description: Add or update Markdown documentation during normal development when code, setup, scripts, workflows, or user-facing behavior change. Use when Codex needs to keep project documentation accurate after implementation work.
---

# Documentation Maintenance

Keep Markdown documentation aligned with the codebase.

Update docs when behavior, setup, commands, configuration, or workflows change.
Prefer targeted documentation updates over speculative rewrites.

Do not invent undocumented features.
Do not update docs that are unaffected by the change.
Do not leave stale commands or references behind.

## Workflow

1. Identify whether the current change affects user-facing behavior, developer workflows, setup, or operations.
2. Inspect relevant Markdown files such as `README.md`, setup guides, architecture notes, or changelog-style docs.
3. Update only the sections affected by the change.
4. Re-check commands, paths, filenames, and examples against the real repository.

## When To Update Docs

Update docs when the change affects:

1. installation or setup
2. commands or scripts
3. configuration or environment variables
4. API usage or behavior
5. project structure developers need to understand
6. new required tools or dependencies

Docs are often not needed when the change is:

1. a purely internal refactor with no workflow impact
2. invisible cleanup with unchanged behavior
3. a tiny fix already covered by existing accurate docs

## Documentation Rules

1. Keep Markdown concise and factual.
2. Use real commands only.
3. Keep examples synchronized with the current code.
4. Prefer updating existing docs over creating new files unless a new file is clearly warranted.

## Common Pitfalls

- Do not leave README instructions pointing to removed files.
- Do not forget `.env.example`, CI docs, or setup docs after changing workflows.
- Do not add broad architecture prose for a tiny implementation change.
