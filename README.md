# spellbookx-template-singlerepo

[![CI](https://github.com/dcdavidev/spellbookx-template-singlerepo/actions/workflows/code-quality-tests-build.yml/badge.svg)](https://github.com/dcdavidev/spellbookx-template-singlerepo/actions/workflows/code-quality-tests-build.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)

Opinionated single-repo TypeScript starter powered by [Spellbookx](https://github.com/dcdavidev/spellbookx): zero setup, start coding right away.

## What's Included

- **TypeScript & ESM**: Targets `ES2024` with `NodeNext` module resolution, strict type-checking ([`tsconfig.json`](./tsconfig.json)), and clean `dist/` builds with type declarations and source maps ([`tsconfig.build.json`](./tsconfig.build.json)).
- **Code Quality & Formatting**: Preconfigured [Spellbookx](https://github.com/dcdavidev/spellbookx) presets for ESLint (`eslint-plugin-spellbookx` with `recommended-spellcheck`), Prettier (`prettier-config-spellbookx/base`), and CSpell (`cspell-config-spellbookx` with a project dictionary at [`.config/cspell/custom.txt`](./.config/cspell/custom.txt)).
- **Conventional Commits & Git Hooks**: Commitlint (`commitlint-config-spellbookx`), an interactive `czg` commit prompt (`cz-config-spellbookx`), and [Lefthook](./.config/lefthook.yml) hooks that auto-fix staged files on `pre-commit` and validate commit messages on `commit-msg`.
- **Testing & Task Caching**: [Vitest](https://vitest.dev/) with V8 coverage and [Turborepo](https://turborepo.com/) ([`turbo.json`](./turbo.json)) for cached, parallel local verification (`pnpm check`, `pnpm lint`).
- **Versioning & Changelogs**: [Changesets](https://github.com/changesets/changesets) with `@changesets/changelog-github` and `changeset-conventional-commits`.
- **CI & Automated Maintenance**: GitHub Actions for build, commit validation, linting, formatting, spell-checking, type-checking, and tests ([`code-quality-tests-build.yml`](./.github/workflows/code-quality-tests-build.yml)), plus weekly Dependabot updates ([`dependabot.yml`](./.github/dependabot.yml)) and scheduled Node.js LTS and Turborepo update workflows.
- **Editor & AI Tooling**: Ready-to-use VS Code workspace settings and recommended extensions ([`.vscode/`](./.vscode)), [`.editorconfig`](./.editorconfig), and Spellbookx skills for AI coding assistants ([`.agents/skills/`](./.agents/skills)).

## Requirements

- **Node.js `26.x`** (pinned in [`.nvmrc`](./.nvmrc))
- **pnpm `12.x`** (pinned via `packageManager` and `devEngines` in [`package.json`](./package.json))

## Quick Start

1. **Create a repository from this template** by clicking **Use this template** on GitHub, or using the GitHub CLI:

   ```bash
   gh repo create my-project --template dcdavidev/spellbookx-template-singlerepo --clone
   cd my-project
   ```

2. **Use the pinned Node.js version** (if using `nvm`):

   ```bash
   nvm install
   nvm use
   ```

3. **Install dependencies** (this also installs the Lefthook Git hooks via `prepare`):

   ```bash
   pnpm install
   ```

4. **Run the full verification suite**:

   ```bash
   pnpm check
   ```

### Template Customization Checklist

After creating a new project from this template:

- Update package metadata (`name`, `version`, `description`, `keywords`, `homepage`, `bugs`, `repository`, `author`) in [`package.json`](./package.json).
- Update the GitHub repository slug (`changelog[1].repo`) in [`.changeset/config.json`](./.changeset/config.json).
- Update the copyright holder in [`LICENSE`](./LICENSE) if needed.
- Replace the starter code in [`src/index.ts`](./src/index.ts) and [`tests/index.test.ts`](./tests/index.test.ts).
- Add project-specific terms to [`.config/cspell/custom.txt`](./.config/cspell/custom.txt) and update `README.md` and [`docs/`](./docs).

## Project Structure

```text
.
├── .agents/skills/          # Spellbookx skills for AI coding assistants
├── .changeset/              # Changesets configuration and pending release notes
├── .config/                 # CSpell and Lefthook configuration files
├── .github/                 # CI workflows, scheduled maintenance, and Dependabot
├── .vscode/                 # Recommended VS Code extensions and workspace settings
├── docs/                    # Contributing guide, security policy, and contributor docs
├── scripts/                 # Maintenance scripts (update-node.ts, update-turbo.ts)
├── src/                     # Library TypeScript source code
├── tests/                   # Vitest unit and integration tests
├── commitlint.config.mjs    # Commitlint configuration
├── cz.config.mjs            # Interactive czg commit prompt configuration
├── eslint.config.mjs        # ESLint flat configuration
├── package.json             # Package metadata, exports, scripts, and dependencies
├── pnpm-workspace.yaml      # pnpm build allow-list, engine strictness, and hoisting
├── prettier.config.mjs      # Prettier configuration
├── tsconfig.build.json      # TypeScript emit configuration for dist/
├── tsconfig.json            # Base TypeScript configuration for type-checking
└── turbo.json               # Turborepo task caching configuration
```

For full details on configuration placement, build outputs, and tooling, see the [Architecture](./docs/contribute/architecture.md) guide.

## Available Scripts

| Script              | What it does                                                                                 |
| :------------------ | :------------------------------------------------------------------------------------------- |
| `build`             | Compiles `src/` to `dist/` with `tsc -p tsconfig.build.json`.                                |
| `changeset`         | Creates a changeset interactively.                                                           |
| `changeset:commits` | Generates changesets from Conventional Commits (`changeset-conventional`).                   |
| `changeset:version` | Consumes pending changesets, bumps `package.json`, and updates `CHANGELOG.md`.               |
| `check`             | Runs `build`, `lint:code`, `lint:spelling`, `lint:types`, `fmt:check`, and `test` via Turbo. |
| `commit`            | Launches the interactive `czg` Conventional Commits prompt.                                  |
| `fmt`               | Formats all supported files with Prettier.                                                   |
| `fmt:check`         | Verifies Prettier formatting without modifying files.                                        |
| `lint`              | Runs `lint:code` and `lint:spelling` via Turborepo.                                          |
| `lint:code`         | Lints the repository with ESLint.                                                            |
| `lint:code:fix`     | Lints the repository with ESLint and applies automatic fixes.                                |
| `lint:commits`      | Validates the latest commit message with Commitlint (`HEAD~1`).                              |
| `lint:spelling`     | Checks spelling across the repository with CSpell.                                           |
| `lint:types`        | Type-checks `src/`, `tests/`, and `scripts/` with `tsc --noEmit`.                            |
| `prepare`           | Installs Lefthook Git hooks.                                                                 |
| `test`              | Runs Vitest once with V8 coverage.                                                           |
| `update:node`       | Syncs `.nvmrc` and `@types/node` with the latest active Node.js LTS release.                 |
| `update:turbo`      | Upgrades `turbo` and runs `@turbo/codemod` migrations.                                       |

Run any script with `pnpm <script>` (for example, `pnpm check` or `pnpm check --force` to bypass the Turborepo cache).

## Documentation

- [Contributing Guide](./docs/CONTRIBUTING.md)
- [Development Environment](./docs/contribute/development-environment.md)
- [Architecture](./docs/contribute/architecture.md)
- [Code Conventions](./docs/contribute/code-conventions.md)
- [Commit Message Style](./docs/contribute/commit-style.md)
- [Package.json Scripts Naming Conventions](./docs/contribute/package-json-scripts-naming-conventions.md)
- [Tests](./docs/contribute/tests.md)
- [Security Policy](./docs/SECURITY.md)

## Contributing

Contributions are welcome! Please read the [Contributing Guide](./docs/CONTRIBUTING.md) before opening an issue or pull request.

## Security

To report a security vulnerability privately, please follow the [Security Policy](./docs/SECURITY.md).

## License

MIT © [Davide Di Criscito](./LICENSE)
