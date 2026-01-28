# Agents WordPress

Coding and documentation standards for WordPress development, organized for both humans and AI agents.

Author: Dax Castellon - daxcastellon@pm.me

## What This Repo Contains

This repo provides a token-efficient, human-readable ruleset for working on WordPress code.
The canonical rules live in two files; everything else points back to them.

Key files and folders:

- `agent-guidelines/AGENTS.md` - entry point for agents and humans
- `agent-guidelines/SECURITY_RULES.md` - authoritative security rules
- `agent-guidelines/CODING_RULES.md` - authoritative coding style rules
- `agent-guidelines/SKILLS_INDEX.md` - list of scoped skills
- `agent-guidelines/SKILLS/` - task-specific skills (each file is short and points to the canonical rules)
- `agent-guidelines/CI_CHECKS.md` - what CI enforces

## How To Use (Humans)

1. Read `agent-guidelines/AGENTS.md` first.
2. For security rules, open `agent-guidelines/SECURITY_RULES.md`.
3. For style rules, open `agent-guidelines/CODING_RULES.md`.
4. If you need task-specific guidance, open `agent-guidelines/SKILLS_INDEX.md` and choose one skill.

## How To Use (AI Agents)

Load order (lowest token usage):
1. `agent-guidelines/AGENTS.md`
2. `agent-guidelines/SECURITY_RULES.md` and/or `agent-guidelines/CODING_RULES.md`
3. One relevant file from `agent-guidelines/SKILLS/`

Notes:
- Skills are intentionally short and do not repeat the canonical rules.
- When reporting issues, reference SR-* or CR-* rule IDs from the canonical files.

### Example instructions for an AI agent

Example 1 - security-sensitive backend change:
"Read `agent-guidelines/AGENTS.md`, then `agent-guidelines/SECURITY_RULES.md`, and use the skill
`agent-guidelines/SKILLS/wordpress-backend.md` before editing code. Follow security rules strictly
and reference SR-* IDs in any findings."

Example 2 - CSS cleanup:
"Use `agent-guidelines/AGENTS.md`, then `agent-guidelines/CODING_RULES.md`, and apply the skill
`agent-guidelines/SKILLS/css-style.md` for any CSS changes. Keep changes minimal and follow the
WordPress style rules."

Example 3 - REST endpoint review:
"Open `agent-guidelines/AGENTS.md`, then `agent-guidelines/SECURITY_RULES.md`, and the skill
`agent-guidelines/SKILLS/wordpress-rest-api.md`. Review the endpoint for security issues and cite
SR-* rule IDs in the report."

## Why This Structure

- Single source of truth for rules (reduces drift)
- Minimal duplication (reduces agent token usage)
- Clear navigation for humans

## Maintenance

- Update rules only in `SECURITY_RULES.md` and `CODING_RULES.md`.
- Keep skills short; they should point back to the canonical rules.
- If you add a skill, list it in `agent-guidelines/SKILLS_INDEX.md`.
