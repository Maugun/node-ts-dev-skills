---
name: security-review
description: Review a code change for common application security issues and repository safety risks, with attention to the project type and affected surfaces. Use when Codex needs to check that a change respects security expectations during development.
---

# Security Review

Review code and repository changes for practical security risks.

Focus on real attack surfaces.
Match the review depth to the changed area.
Prefer concrete findings over vague warnings.

Do not claim full security certification.
Do not invent vulnerabilities without evidence.
Do not ignore secrets, auth, input validation, or dependency-driven risks when they are in scope.

## Review Workflow

1. Identify the changed surface: frontend, backend, API, auth, env, CI, docs, or dependencies.
2. Inspect the affected files and their surrounding flow.
3. Check for common security mistakes relevant to that surface.
4. Report concrete risks first.
5. If no issues are found, state that explicitly and mention residual gaps if any.

## Common Checks

Review for issues such as:

1. secrets committed in code, docs, examples, or env files
2. missing input validation
3. unsafe auth or authorization changes
4. trust of client input without server checks
5. unsafe command execution or file handling
6. insecure defaults in config or CI
7. sensitive data leakage through logs or errors
8. unsafe dependency additions or updates

## Contextual Guidance

For backend and API changes, pay extra attention to:

1. auth and permission boundaries
2. DTO or schema validation
3. request handling and error exposure
4. database query safety

For frontend changes, pay extra attention to:

1. unsafe rendering or injection risks
2. token handling
3. exposure of secrets in client code

For repository and tooling changes, pay extra attention to:

1. committed credentials
2. unsafe CI workflow behavior
3. `.env` handling

## Common Pitfalls

- Do not ignore security review just because lint passes.
- Do not treat type safety as a security guarantee.
- Do not expose secret values in documentation or examples.
- Do not assume auth is safe because a route is hidden in the UI.
