---
name: git-workflow
description: Use Git safely during day-to-day development with clean staging, conventional commit messages, and strict guardrails around commit, push, amend, and history-rewriting actions. Use when Codex needs to work in a Git repository after project setup.
---

# Git Workflow

Use Git safely during normal development work.

Stage intentionally.
Keep commits focused.
Respect commit message conventions.

Do not commit unless the user explicitly asks for a commit.
Do not push unless the user explicitly asks for a push.
Do not amend, rebase, reset, or force-push unless the user explicitly asks for it.
Do not revert unrelated user changes.

## Workflow

1. Inspect `git status` before staging or preparing a commit.
2. Separate relevant changes from unrelated changes.
3. Stage only the files that belong to the requested work.
4. If the user asks for a commit, write a clear conventional-style commit message.
5. If the user does not ask for a commit, leave the working tree ready but uncommitted.

## Commit Message Guidance

Prefer conventional commit style:

1. `feat: ...`
2. `fix: ...`
3. `docs: ...`
4. `refactor: ...`
5. `test: ...`
6. `chore: ...`

Keep the subject short and specific.
Describe the user-facing or maintenance-facing change, not the implementation trivia.

Good examples:

1. `feat: add backend project setup skill`
2. `fix: align bootstrap skill with fullstack orchestration`
3. `docs: document skill installation workflow`

## Staging Rules

1. Review changed files before staging.
2. Stage only files relevant to the current task.
3. Avoid bundling unrelated refactors, formatting-only churn, or accidental local files.

If unrelated changes already exist:

1. leave them untouched unless the user explicitly asks to include them
2. commit only the relevant subset when possible

## Validation Before Commit

Before creating a commit, prefer to verify:

1. tests relevant to the change
2. lint if code changed
3. formatting if style-sensitive files changed
4. docs if user-facing behavior or setup changed

Use the dedicated quality or verification skills when needed.

## Common Pitfalls

- Do not auto-commit at the end of a task.
- Do not auto-push after committing.
- Do not use destructive history edits without explicit approval.
- Do not include unrelated files just because they are already modified.
