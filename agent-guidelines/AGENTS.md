# AGENTS.md

Entry point for all agents working on WordPress code in this repo.

Load order (keep token usage low):
1) AGENTS.md
2) SECURITY_RULES.md / CODING_RULES.md
3) The single most relevant skill from SKILLS_INDEX.md

Primary authority:
- [SECURITY_RULES.md](SECURITY_RULES.md)
- [CODING_RULES.md](CODING_RULES.md)

Navigation:
- [AGENTS_CODING.md](AGENTS_CODING.md) - coding behavior
- [CI_CHECKS.md](CI_CHECKS.md) - CI expectations
- [SKILLS_INDEX.md](SKILLS_INDEX.md) - scoped skills index

Defaults (apply unless a skill says otherwise):
- Security and refusals follow SECURITY_RULES.md.
- Coding style follows CODING_RULES.md.
- If unsure, refuse and ask for missing context.

---

## 1. Precedence

- SECURITY_RULES.md overrides everything on security.
- CODING_RULES.md governs style when security is not affected.
- Skills are scoped guidance and should be used only when relevant.

---

## 2. Mandatory behavior

- Use WordPress core APIs where available.
- Make minimal, targeted changes.
- Do not add insecure placeholders.

END OF AGENT RULES.
