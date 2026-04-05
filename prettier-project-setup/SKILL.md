---
name: prettier-project-setup
description: Configure Prettier in a new JavaScript or TypeScript project with the same formatting rules and compatibility constraints as this skill. Use when Codex needs to set up this Prettier baseline directly in another project without relying on a shared package.
---

# Prettier Project Setup

Apply the Prettier baseline described in this skill directly inside the target project.

Do not invent new formatting rules.
Do not simplify the rule set.
Do not add plugins unless the user explicitly asks for them.

## Workflow

1. Inspect the target project for `package.json`, existing Prettier config files, and whether a shared formatting setup already exists.
2. If the project already has Prettier configured, preserve unrelated project-specific settings and merge carefully.
3. Install the dependency version below.
4. Create or update the Prettier config file to match this skill.
5. Validate by formatting at least one representative file.

## Dependency Set

Install this package in the target project:

```bash
npm install -D prettier@^3.8.1
```

## Files To Create

Create `.prettierrc.json` in the target project, or merge the contents below into the project's existing Prettier config.

## Prettier Config

Create `.prettierrc.json` with this content:

```json
{
    "printWidth": 100,
    "semi": false,
    "tabWidth": 4,
    "singleQuote": true,
    "overrides": [
        {
            "files": ["*.yml", "*.yaml"],
            "options": {
                "bracketSpacing": false,
                "tabWidth": 2
            }
        },
        {
            "files": ["*.json"],
            "options": {
                "trailingComma": "all"
            }
        }
    ]
}
```

## Integration Rules

If the target project already has a Prettier config:

1. Keep the values above unchanged unless the user explicitly requests a formatting change.
2. Preserve unrelated project-specific settings.
3. Do not convert this into a JS config file unless the project already standardizes on JS-based tooling configs.

If the target project has no formatting ignore file and contains generated or vendor content:

1. Consider creating `.prettierignore`.
2. Add only obvious non-source paths such as `dist/`, `build/`, `coverage/`, or `node_modules/`.
3. Do not guess extra ignore rules when the project structure is unclear.

## Validation

After setup:

1. Run Prettier on at least one representative file such as a TS, JS, JSON, or YAML file.
2. Fix only integration issues such as missing dependencies or wrong config file placement.
3. Do not weaken rules to make validation pass unless the user explicitly requests that.

Useful commands:

```bash
npx prettier --check .
npx prettier --write .
```

## Common Pitfalls

- Do not add Prettier plugins that are not required by this baseline.
- Do not switch the config to another file format unless the target project already uses that convention.
- Do not remove the YAML override: it changes `tabWidth` to `2` and `bracketSpacing` to `false`.
- Do not remove the JSON override: it enforces `trailingComma: all` for JSON files.
