# Security Policy

## Supported Versions

Only the latest release of `spellbookx-template-singlerepo` receives security updates.

| Version | Supported          |
| :------ | :----------------- |
| `0.1.x` | :white_check_mark: |
| `< 0.1` | :x:                |

## Reporting a Vulnerability

**Do not report security vulnerabilities through public GitHub issues, discussions, or pull requests.**

Instead, please report them privately using one of the following channels:

1. **GitHub Security Advisories (preferred)**: open a private report at [github.com/dcdavidev/spellbookx-template-singlerepo/security/advisories/new](https://github.com/dcdavidev/spellbookx-template-singlerepo/security/advisories/new).
2. **Email**: send details to `info@dcdavidev.me`.

### What to Include

To help us investigate and resolve the issue quickly, please include:

- A clear description of the vulnerability and its potential impact.
- Affected version(s), Node.js version, and pnpm version.
- Minimal steps to reproduce or a proof-of-concept.
- Any suggested fix or mitigation, if you have one.

## Response Process

- **Acknowledgment**: we aim to acknowledge receipt of your report within **3 business days**.
- **Assessment**: we will investigate the report, confirm the scope and severity, and keep you updated on progress.
- **Resolution & Disclosure**: once a fix is ready, we will publish a patched release and coordinate public disclosure (such as a GitHub Security Advisory) with you.

## Scope

This policy covers `spellbookx-template-singlerepo`, its configuration files, and its maintenance scripts in this repository. For vulnerabilities in upstream dependencies (such as ESLint, Prettier, Turborepo, or `spellbookx` preset packages), please also consider reporting them directly to the respective upstream project.
