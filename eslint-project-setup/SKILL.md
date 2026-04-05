---
name: eslint-project-setup
description: Configure ESLint in a new JavaScript or TypeScript project with the same flat-config rules and compatibility constraints as this skill. Use when Codex needs to set up this ESLint baseline in another project without relying on a shared package.
---

# ESLint Project Setup

Apply the ESLint baseline described in this skill directly inside the target project.

Do not invent new lint rules.
Do not simplify the rule set.

## Workflow

1. Inspect the target project for `package.json`, existing `eslint.config.*`, `tsconfig.json`, Jest usage, and whether the project uses ESM.
2. If the project already has ESLint configured, preserve unrelated project-specific settings and merge this skill's config carefully.
3. Prefer ESLint 9.x, not 10.x.
4. Install the dependency set below.
5. Create or update the flat config file to match the config in this skill.
6. Validate by running ESLint on at least one TS or JS file.

## Dependency Set

Install these packages in the target project.

```bash
npm install -D eslint@^9.39.4 @eslint/js@^9.39.4 typescript-eslint@^8.58.0 @stylistic/eslint-plugin@^5.10.0 eslint-config-prettier@^10.1.8 eslint-plugin-jest@^29.15.1 eslint-plugin-perfectionist@^5.8.0 eslint-plugin-prettier@^5.5.5 eslint-plugin-promise@^7.2.1 eslint-plugin-regexp@^3.1.0 eslint-plugin-security@^4.0.0 globals@^17.4.0 @darraghor/eslint-plugin-nestjs-typed@^7.1.28 prettier@^3.8.1
```

If the project uses TypeScript, ensure `typescript` is installed.

If the project uses Jest rules, ensure `jest` is installed.

If the project uses NestJS typed rules in files that depend on `class-validator`, install `class-validator`.

Reason for ESLint 9.x: this rule stack is currently aligned on ESLint 9 compatibility, and `eslint-plugin-promise@7.2.1` does not advertise ESLint 10 support.

## Files To Create

Create `eslint.config.mjs` in the target project, or merge the contents below into the project's existing flat config.

## Main Flat Config

Create `eslint.config.mjs` with this content:

```js
import eslintNestJs from '@darraghor/eslint-plugin-nestjs-typed'
import eslint from '@eslint/js'
import eslintPluginStylistic from '@stylistic/eslint-plugin'
import jestPlugin from 'eslint-plugin-jest'
import perfectionist from 'eslint-plugin-perfectionist'
import eslintPluginPrettierRecommended from 'eslint-plugin-prettier/recommended'
import eslintPluginPromise from 'eslint-plugin-promise'
import * as eslintPluginRegexp from 'eslint-plugin-regexp'
import eslintPluginSecurity from 'eslint-plugin-security'
import globals from 'globals'
import tseslint from 'typescript-eslint'

export default tseslint.config(
    {
        ignores: ['**/build/**', '**/dist/**', '**/node_modules/**', '**/coverage/**'],
    },
    eslint.configs.recommended,
    tseslint.configs.strictTypeChecked,
    eslintPluginStylistic.configs['all'],
    eslintPluginPromise.configs['flat/recommended'],
    eslintPluginRegexp.configs['flat/recommended'],
    eslintPluginSecurity.configs.recommended,
    perfectionist.configs['recommended-natural'],
    eslintPluginPrettierRecommended,
    {
        languageOptions: {
            globals: {
                ...globals.node,
                ...globals.jest,
            },
            parser: tseslint.parser,
            parserOptions: {
                projectService: true,
            },
        },
        plugins: {
            '@typescript-eslint': tseslint.plugin,
            'eslint-plugin-nestjs-typed': eslintNestJs.plugin,
            jest: jestPlugin,
        },
        rules: {
            '@stylistic/comma-dangle': ['error', 'always-multiline'],
            '@stylistic/indent': 'off',
            '@stylistic/lines-around-comment': 'off',
            '@stylistic/member-delimiter-style': ['error', { multiline: { delimiter: 'none' } }],
            '@stylistic/no-extra-parens': ['error', 'functions'],
            '@stylistic/object-curly-spacing': ['error', 'always'],
            '@stylistic/object-property-newline': ['error', { allowAllPropertiesOnSameLine: true }],
            '@stylistic/quote-props': ['error', 'as-needed'],
            '@stylistic/quotes': [
                'error',
                'single',
                { allowTemplateLiterals: 'always', avoidEscape: true },
            ],
            '@stylistic/semi': ['error', 'never'],
            '@stylistic/space-before-function-paren': [
                'error',
                { anonymous: 'never', asyncArrow: 'always', named: 'never' },
            ],
            '@typescript-eslint/no-misused-spread': 'off',
            '@typescript-eslint/no-unsafe-argument': 'warn',
            '@typescript-eslint/no-unsafe-assignment': 'warn',
            '@typescript-eslint/no-unsafe-call': 'warn',
            '@typescript-eslint/no-unsafe-enum-comparison': 'warn',
            '@typescript-eslint/no-unsafe-member-access': 'warn',
            '@typescript-eslint/no-unsafe-return': 'warn',
            '@typescript-eslint/restrict-template-expressions': 'warn',
            'no-console': ['error', { allow: ['warn', 'error', 'info'] }],
        },
    },
    {
        files: ['**/*.controller.ts'],
        rules: {
            'perfectionist/sort-classes': 'off',
        },
    },
    {
        files: ['**/*.dto.ts', '**/*.config.ts'],
        rules: {
            'perfectionist/sort-modules': 'off',
        },
    },
    {
        files: ['**/*.module.ts'],
        rules: {
            '@typescript-eslint/no-extraneous-class': 'off',
        },
    },
    {
        files: ['**/global.d.ts'],
        rules: {
            '@typescript-eslint/no-namespace': 'off',
            'no-var': 'off',
        },
    },
    {
        extends: [tseslint.configs.disableTypeChecked],
        files: ['**/*.js', '**/*.mjs'],
        rules: {
            '@typescript-eslint/no-require-imports': 'off',
            '@typescript-eslint/no-var-requires': 'off',
        },
    },
    {
        extends: [jestPlugin.configs['flat/recommended']],
        files: ['test/**/*.ts'],
        rules: {
            '@typescript-eslint/no-misused-spread': 'off',
            '@typescript-eslint/no-unsafe-assignment': 'off',
            '@typescript-eslint/unbound-method': 'off',
        },
    },
)
```

## Integration Rules

If the target project already has a flat config:

1. Merge imports rather than duplicating them.
2. Keep the rule values above unchanged.
3. Preserve unrelated project overrides.

If the target project still uses legacy `.eslintrc*`:

1. Migrate to flat config instead of trying to force this setup into legacy format.
2. Put the main config into `eslint.config.mjs`.

If the target project is JavaScript-only:

1. Keep the same config structure.
2. Install `typescript-eslint` anyway because this configuration depends on it.
3. If the project has no `tsconfig.json`, create a minimal one only if required for ESLint to resolve `projectService`.

## Validation

After setup:

1. Run ESLint against one TS or JS file.
2. Fix only integration issues such as path mistakes, missing dependencies, or flat-config wiring mistakes.
3. Do not weaken rules to make validation pass unless the user explicitly requests that.

Useful commands:

```bash
npx eslint .
```

## Common Pitfalls

- Do not use ESLint 10 with this stack unless you re-verify every plugin.
- Do not point the main entry file to `index.js` when the project uses `.mjs`.
- Do not remove `projectService: true` unless the user explicitly wants a different TypeScript ESLint strategy.
