# Agents WordPress

Coding and documentation standards for WordPress development, organized for both humans and AI agents.

Author: Dax Castellon - daxcastellon@pm.me

## What This Repo Contains

This repo provides a token-efficient, human-readable ruleset for working on WordPress code.
All guidelines now live in a single file.

Key file:

- `AGENTS.md` - entry point, rules, skills, and CI expectations

## How To Use (Humans)

1. Read `AGENTS.md` first.
2. Use the security rules section for security guidance.
3. Use the coding rules section for style guidance.
4. If you need task-specific guidance, use the skills index and relevant skill sections in `AGENTS.md`.

## How To Use (AI Agents)

Load order (lowest token usage):
1. `AGENTS.md`
2. Security rules and/or coding rules sections inside `AGENTS.md`
3. One relevant skill section inside `AGENTS.md`

Notes:
- Skills are intentionally short and do not repeat the canonical rules.
- When reporting issues, reference SR-* or CR-* rule IDs from the canonical files.

### Example instructions for an AI agent

Example 1 - security-sensitive backend change:
"Read `AGENTS.md`, then the security rules section, and use the Backend Development skill section
before editing code. Follow security rules strictly and reference SR-* IDs in any findings."

Example 2 - CSS cleanup:
"Use `AGENTS.md`, then the coding rules section, and apply the CSS Style skill section for any CSS
changes. Keep changes minimal and follow the WordPress style rules."

Example 3 - REST endpoint review:
"Open `AGENTS.md`, then the security rules section, and the REST API skill section. Review the
endpoint for security issues and cite SR-* rule IDs in the report."

## Why This Structure

- Single source of truth for rules (reduces drift)
- Minimal duplication (reduces agent token usage)
- Clear navigation for humans

## Maintenance

- Update rules only in `AGENTS.md`.
- Keep skills short and scoped.
- If you add a skill, list it in the skills index section in `AGENTS.md`.
