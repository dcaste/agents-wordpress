# AGENTS

Entry point for all agents working on WordPress code in this repo.

Load order (keep token usage low):
1) This document
2) Security rules
3) Coding rules
4) The single most relevant skill

Defaults (apply unless a skill says otherwise):
- Security and refusals follow the security rules below.
- Coding style follows the coding rules below.
- If unsure, refuse and ask for missing context.
- Responses MUST be concise to minimize token consumption.

---

## 1. Precedence

- Security rules override everything on security.
- Coding rules govern style when security is not affected.
- Skills are scoped guidance and should be used only when relevant.

---

## 2. Mandatory behavior

- Use WordPress core APIs where available.
- Make minimal, targeted changes.
- Do not add insecure placeholders.

END OF AGENT RULES.

---

# AGENTS CODING

Coding behavior for WordPress standards (non-security).

Authority:
- Coding rules below
- Security rules below (if security is touched)

Defaults:
- Follow coding rules below.
- Use the single most relevant skill below.

---

## Mandatory behavior

- Preserve tab indentation.
- Avoid large reformatting unless requested.
- Avoid lint-only changes mixed with logic changes unless requested.

---

## Refusals

- Refuse when the coding rules below require it and state the CR-REFUSE ID.

END OF AGENTS CODING.

---

# CI CHECKS

These checks are enforced by CI for WordPress code changes.

Agents MUST ensure code complies with:
- Security rules below
- Coding rules below

When reporting issues, reference the relevant SR-* or CR-* rule IDs.

END OF CI CHECKS.

---

# CODING RULES (WordPress Coding Standards — Normative)

This document is **authoritative and normative** for agent-generated WordPress code style
and documentation (non-security). These rules enforce consistency with WordPress Coding Standards.

- Keywords **MUST**, **MUST NOT**, **REQUIRED**, **FORBIDDEN**, **SHOULD** are binding.
- If a rule is unclear or multiple rules conflict, agents MUST apply the **most restrictive**
  rule or REFUSE.

---

## Rule ID conventions

- `CR-GEN-*` General / formatting
- `CR-A11Y-*` Accessibility targets
- `CR-HTML-*` HTML formatting
- `CR-CSS-*` CSS formatting
- `CR-JS-*` JavaScript formatting
- `CR-PHP-*` PHP formatting
- `CR-DOC-JS-*` JavaScript docs (JSDoc)
- `CR-DOC-PHP-*` PHP docs (PHPDoc-like)
- `CR-MD-*` Markdown docs style
- `CR-REFUSE-*` Refusal conditions for coding standards

---

## CR-GEN: Global conventions

- **CR-GEN-001 (Consistency):** Code in a project MUST be consistent.
- **CR-GEN-002 (Tabs):** Indentation MUST use **real tab characters** (not spaces) across WP code (PHP/JS/HTML/CSS), except where spaces are explicitly used for alignment within a line. citeturn0search1turn0search2turn0search7turn1search0
- **CR-GEN-003 (No trailing whitespace):** Trailing whitespace MUST NOT exist.
- **CR-GEN-004 (Final newline):** Files SHOULD end with a newline.

---

## CR-A11Y: Accessibility

- **CR-A11Y-001 (Target conformance):** Work SHOULD conform to WCAG 2.2 Level A and Level AA; AAA is encouraged where relevant. citeturn0search4

(Implementation details are handled in the accessibility skill below.)

---

## CR-HTML: HTML coding standards

- **CR-HTML-001 (Validate):** HTML SHOULD be valid; use validators during development.
- **CR-HTML-010 (Self-closing space):** Self-closing tags MUST include exactly one space before the slash: `<br />`, not `<br/>`. citeturn1search0
- **CR-HTML-011 (Close tags):** Tags MUST be properly closed. citeturn1search0
- **CR-HTML-020 (Lowercase):** Element and attribute names MUST be lowercase.
- **CR-HTML-021 (Quote attributes):** Attribute values SHOULD be quoted (preferably double quotes).
- **CR-HTML-022 (Boolean attributes):** Boolean attributes SHOULD omit values (e.g. `disabled`, not `disabled="disabled"`). citeturn1search0
- **CR-HTML-030 (Indentation):** Nested structure MUST be indented with tabs to reflect hierarchy.
- **CR-HTML-040 (Minimal DOM):** Code MUST prioritize minimal DOM rendering. Create as few DOM elements as possible to reduce rendering overhead and improve performance.

---

## CR-CSS: CSS coding standards

- **CR-CSS-001 (Tabs):** Properties MUST be indented using tabs (not spaces). citeturn0search7
- **CR-CSS-002 (Blank lines):** Add **two blank lines** between sections and **one blank line** between blocks within a section. citeturn0search7
- **CR-CSS-003 (One selector per line):** Each selector MUST be on its own line, ending in `,` or `{`. citeturn0search7
- **CR-CSS-004 (One declaration per line):** Each property/value MUST be on its own line with one tab indentation and a trailing semicolon. citeturn0search7
- **CR-CSS-005 (Brace alignment):** Closing brace `}` MUST be flush left at the same indentation as the selector line.
- **CR-CSS-010 (No inline CSS):** Inline CSS via `style` attributes MUST NOT be used. All styles MUST be defined in external CSS files.

---

## CR-JS: JavaScript coding standards

- **CR-JS-001 (Tabs):** Indentation MUST use tabs. citeturn0search2
- **CR-JS-002 (No trailing whitespace):** No whitespace at end of line or blank lines. citeturn0search2
- **CR-JS-003 (Line length):** Lines SHOULD be ≤ 80 characters and MUST NOT exceed 100 (tabs count as 4 spaces). citeturn0search2
- **CR-JS-004 (Braces required):** `if/else/for/while/try` blocks MUST always use braces and MUST be multi-line. citeturn0search2
- **CR-JS-005 (Operators spacing):** Follow WP whitespace rules; punctuation spacing MUST follow the standard (no extra spaces before commas/semicolons).
- **CR-JS-010 (No jQuery):** jQuery MUST NOT be used. Only modern vanilla JavaScript (ES6+) is allowed for scripts.

---

## CR-PHP: PHP coding standards

- **CR-PHP-001 (Tabs rule):** Tabs MUST be used at the beginning of lines for indentation; spaces MAY be used mid-line for alignment. citeturn0search1
- **CR-PHP-010 (No short tags):** Short open tags MUST NOT be used.
- **CR-PHP-011 (PHP tags in HTML):** Multi-line PHP snippets in HTML SHOULD place open/close tags on their own lines.
- **CR-PHP-020 (Naming):** Follow WP naming conventions (snake_case for functions/variables, etc.).
- **CR-PHP-030 (Whitespace):** Commas MUST be followed by a space; operators SHOULD be surrounded by spaces (per standard). citeturn0search1

---

## CR-DOC-JS: JavaScript inline documentation (JSDoc)

- **CR-DOC-JS-001 (JSDoc):** JavaScript documentation MUST follow JSDoc 3 patterns. citeturn1search2
- **CR-DOC-JS-010 (No HTML/Markdown in param/return):** `@param` and `@return` descriptions MUST NOT contain HTML or Markdown. citeturn1search2
- **CR-DOC-JS-020 (Wrap):** DocBlock text MUST wrap after ~80 characters (with indentation allowances) and MUST NOT exceed ~120 columns. citeturn1search2

---

## CR-DOC-PHP: PHP inline documentation (PHPDoc-like)

- **CR-DOC-PHP-001 (Schema):** PHP docs MUST follow WordPress’ PHP documentation standards. citeturn1search1
- **CR-DOC-PHP-010 (No HTML):** DocBlock tag descriptions (`@param`, `@return`, etc.) MUST NOT use HTML; limited Markdown MAY be used as specified. citeturn1search1
- **CR-DOC-PHP-020 (Wrap):** DocBlock text MUST wrap after ~80 characters (with indentation allowances) and MUST NOT exceed ~120 columns. citeturn1search1

---

## CR-MD: Markdown style for documentation

- **CR-MD-001 (Headings):** Use `#` through `######` for headings. citeturn1search3
- **CR-MD-010 (Emphasis):** Italic uses `_text_`; bold uses `**text**`; strike uses `~~text~~`. citeturn1search3
- **CR-MD-020 (Lists):** Unordered lists use `- item`; ordered lists use `1. item`. citeturn1search3
- **CR-MD-030 (Code blocks):** Use fenced code blocks and specify language where possible.

---

## CR-REFUSE: Refusal rules for coding standards

Agents MUST REFUSE if:

- **CR-REFUSE-001:** They cannot determine which standard applies (PHP vs JS vs CSS vs HTML vs docs).
- **CR-REFUSE-002:** The required indentation mode (tabs) cannot be preserved in the output medium.
- **CR-REFUSE-003:** The task requests intentionally non-compliant formatting.

END OF CODING RULES.

---

# SECURITY RULES

This document is **authoritative and normative** for agent-generated WordPress code.

- Keywords **MUST**, **MUST NOT**, **REQUIRED**, **FORBIDDEN**, **SHOULD** follow RFC-style meaning.
- If a situation is not explicitly allowed, agents MUST treat it as **FORBIDDEN**.
- When uncertain, agents MUST **REFUSE** rather than guess.

Primary sources for these rules include WordPress Security guidance (validate/sanitize/escape, nonces, capabilities, common vulnerabilities) and OWASP DOM XSS guidance. citeturn0search5turn0search1turn0search0turn0search2turn0search3turn0search10

---

## Rule ID conventions

- `SR-GEN-*` General
- `SR-IN-*` Input validation & sanitization
- `SR-OUT-*` Output escaping
- `SR-CSRF-*` CSRF & nonces
- `SR-AUTH-*` Authorization
- `SR-DB-*` Database & SQL injection
- `SR-XSS-*` XSS (server-side)
- `SR-DOMXSS-*` DOM-based XSS (client-side)
- `SR-ERR-*` Errors & logging
- `SR-REFUSE-*` Mandatory refusal conditions

Each rule is normative. Skills MUST reference these IDs.

---

## SR-GEN: General security model

- **SR-GEN-001 (Untrusted by default):** All external input MUST be treated as untrusted (including user input, third-party APIs, and data from the database unless verified). citeturn0search5
- **SR-GEN-002 (Defense in depth):** Validation, sanitization, escaping, authorization, and CSRF protection are independent controls; passing one MUST NOT imply the others.
- **SR-GEN-003 (Prefer WP APIs):** WordPress core APIs SHOULD be used where they exist, rather than ad-hoc equivalents.
- **SR-GEN-004 (Plugin hardening index):** All plugin folders MUST contain an empty `index.php`; if missing, create it with `<?php // Silence is golden`.

---

## SR-IN: Input handling (validation and sanitization)

### Validation

- **SR-IN-001 (Validate early):** Validation MUST be performed as early as possible, before any actions or side effects. citeturn0search1
- **SR-IN-002 (Prefer validation):** Validation is preferred over sanitization because it is more specific. citeturn0search0
- **SR-IN-003 (Safelist):** Validation MUST be safelist-based where feasible (known-good types/ranges/enums).
- **SR-IN-004 (Fail closed):** If validation fails, execution MUST stop and the request MUST be rejected.
- **SR-IN-005 (No silent coercion):** Invalid input MUST NOT be silently coerced into “acceptable” values.

### Sanitization

- **SR-IN-010 (Sanitize when needed):** When strict validation is not possible, sanitization MUST be applied to reduce risk. citeturn0search0
- **SR-IN-011 (Sanitize before storage):** Sanitization MUST occur before storage or further processing.
- **SR-IN-012 (No “sanitize to pass”):** Sanitization MUST NOT be used to make invalid data appear valid; it may remove/normalize, but MUST still be validated where requirements exist.
- **SR-IN-013 (Unslash first):** When handling WP superglobals, agents SHOULD apply `wp_unslash()` before sanitization, when applicable to the API being used.

---

## SR-OUT: Output escaping (MANDATORY)

- **SR-OUT-001 (Escape everything):** All data rendered into output MUST be escaped. citeturn0search5turn0search2
- **SR-OUT-002 (Escape late):** Escaping MUST happen at render/output time, not on storage. citeturn0search5turn0search2
- **SR-OUT-003 (Sanitized still escaped):** Sanitized/validated data MUST STILL be escaped on output.
- **SR-OUT-004 (Context-aware):** Escaping MUST match the rendering context; mixed-context output is FORBIDDEN.

### Required escaping by context

- **SR-OUT-010 (HTML text):** HTML text nodes MUST use `esc_html()`.
- **SR-OUT-011 (HTML attribute):** HTML attributes MUST use `esc_attr()`.
- **SR-OUT-012 (URL attributes):** URLs in `href/src/action` MUST use `esc_url()`.
- **SR-OUT-013 (Textarea):** Textarea content MUST use `esc_textarea()`.
- **SR-OUT-014 (JS string context):** JavaScript string context MUST use `esc_js()` OR safer patterns that avoid string injection.
- **SR-OUT-015 (JSON):** JSON output MUST use `wp_json_encode()` (and set correct `Content-Type`).
- **SR-OUT-016 (HTML allowed content):** If HTML must be allowed, `wp_kses()` (or a known-safe equivalent) MUST be used with an explicit allowlist.

---

## SR-CSRF: CSRF protection (nonces)

- **SR-CSRF-001 (Nonce required):** All state-changing actions (create/update/delete, settings changes, privileged actions) MUST be protected by a nonce. citeturn0search5
- **SR-CSRF-002 (Verify server-side):** Nonces MUST be verified server-side before performing the action.
- **SR-CSRF-003 (Nonce != auth):** Nonces MUST NOT be treated as authentication or authorization.
- **SR-CSRF-004 (Use WP helpers):** Use `wp_nonce_field()`, `wp_nonce_url()`, `wp_create_nonce()` for generation; `check_admin_referer()` / `wp_verify_nonce()` for verification.

- **SR-CSRF-010 (Nonce + capability):** Nonce verification MUST ALWAYS be paired with a capability check for the target action.

---

## SR-AUTH: Authorization (roles and capabilities)

- **SR-AUTH-001 (Capability-based):** Authorization MUST be enforced using capabilities (e.g., `current_user_can()`), not roles.
- **SR-AUTH-002 (No role checks):** Role-based authorization checks are FORBIDDEN.
- **SR-AUTH-003 (Static capability strings):** Capability names MUST be static strings; user input MUST NOT influence capability checks.
- **SR-AUTH-004 (Check at point of use):** Capability checks MUST occur immediately before the protected action.
- **SR-AUTH-005 (Least privilege):** Use the minimum capability needed for the operation.

---

## SR-DB: Database and SQL injection prevention

- **SR-DB-001 (No SQL concatenation):** Dynamic SQL MUST NOT be built using string concatenation.
- **SR-DB-002 (Prepared queries):** `$wpdb->prepare()` is REQUIRED for dynamic SQL fragments.
- **SR-DB-003 (Prefer WP APIs):** Prefer core CRUD APIs (options/meta/posts/users) over custom SQL.
- **SR-DB-004 (Limit + order safety):** `ORDER BY`, `LIMIT`, and identifiers MUST be safelisted (never interpolated from raw input).

---

## SR-XSS: Server-side XSS

- **SR-XSS-001 (Unescaped output is a vuln):** Unescaped output of untrusted data is a vulnerability. citeturn0search2
- **SR-XSS-002 (Escape by context):** Agents MUST apply SR-OUT rules for every output context.
- **SR-XSS-003 (HTML allowlists):** If output requires HTML, it MUST be allowlisted via `wp_kses()`.

---

## SR-DOMXSS: DOM-based XSS (client-side)

These rules follow OWASP DOM-based XSS guidance and OWASP safe-sink guidance. citeturn0search3turn0search10

### Untrusted sources

- **SR-DOMXSS-001 (Untrusted sources):** Treat as untrusted: `location.search`, `location.hash`, `document.cookie`, `document.referrer`, `window.name`, `postMessage` data, storage APIs, and network/AJAX responses. citeturn0search10

### Forbidden sinks (when input is untrusted)

- **SR-DOMXSS-010 (No HTML sinks):** Using untrusted input with the following is FORBIDDEN:
  - `innerHTML`, `outerHTML`, `insertAdjacentHTML`, `document.write`. citeturn0search10
- **SR-DOMXSS-011 (No code-eval):** Using untrusted input with the following is FORBIDDEN:
  - `eval`, `new Function`, `setTimeout(string)`, `setInterval(string)`.

### Required safe alternatives

- **SR-DOMXSS-020 (Use safe sinks):** Prefer safe sinks such as `textContent`, `value`, or DOM construction APIs (`createElement`, `appendChild`). citeturn0search10
- **SR-DOMXSS-021 (Attribute setting):** `setAttribute()` MAY be used only with validated/safelisted values and correct encoding for URL attributes.

---

## SR-ERR: Error handling and logging

- **SR-ERR-001 (No sensitive leakage):** Errors MUST NOT expose secrets, credentials, tokens, nonces, stack traces, or SQL queries to end users.
- **SR-ERR-002 (Generic messages):** User-visible error messages MUST be generic unless explicitly requested otherwise.

---

## SR-REFUSE: Mandatory refusal rules

Agents MUST REFUSE to generate/modify code if any apply:

- **SR-REFUSE-001:** Output context cannot be determined with certainty.
- **SR-REFUSE-002:** A required escaping function or allowlist strategy is unknown.
- **SR-REFUSE-003:** Capability requirements are unclear or would be dynamic.
- **SR-REFUSE-004:** A state-changing action lacks nonce generation and verification.
- **SR-REFUSE-005:** A nonce is present without a capability check for the action.
- **SR-REFUSE-006:** Untrusted data would reach a forbidden DOM sink.
- **SR-REFUSE-007:** SQL would be influenced by untrusted data without `$wpdb->prepare()` and safelisting.

END OF SECURITY RULES.

---

# SKILLS INDEX

Pick one skill for the task (avoid loading multiple unless necessary).

## Code Review & Style

- Coding review - Review code for WordPress coding standards (non-security)
- CSS style - CSS formatting and style rules
- JavaScript style - JavaScript formatting and style rules
- PHP style - PHP formatting and style rules

## Documentation

- JSDoc documentation - JSDoc inline documentation for JavaScript
- Markdown documentation - Markdown documentation style
- PHPDoc documentation - PHPDoc inline documentation for PHP

## WordPress Development

- Admin-AJAX - wp_ajax handlers and admin AJAX endpoints
- Backend development - PHP backend development (actions, options, templates)
- Database access - Database access patterns and $wpdb usage
- Forms - Form creation, processing, and validation
- Frontend - Frontend JavaScript and DOM manipulation
- REST API - REST API routes and endpoints
- Security review - Security review and vulnerability assessment

END OF SKILLS INDEX.

---

# SKILL: Coding Review

# SKILL: WordPress Coding Standards Review

Scope: Review code for WordPress coding standards (non-security).

Apply:
- Coding rules below

Output:
- Reference CR-* IDs in findings.
- Escalate security issues to the security rules below.

END OF SKILL.

---

# SKILL: CSS Style

# SKILL: WordPress CSS Style

Scope: CSS used in WordPress themes/plugins.

Apply:
- Coding rules below (CR-CSS-*, CR-GEN-*)

END OF SKILL.

---

# SKILL: JSDoc Documentation

# SKILL: JavaScript Inline Documentation (JSDoc)

Scope: JSDoc for JS in WordPress themes/plugins.

Apply:
- Coding rules below (CR-DOC-JS-*)

Refuse:
- If the request is not JSDoc-compatible.

END OF SKILL.

---

# SKILL: Markdown Documentation

# SKILL: Markdown Documentation Style (WordPress)

Scope: Markdown docs in this repo.

Apply:
- Coding rules below (CR-MD-*)

Refuse:
- If the request is not Markdown.

END OF SKILL.

---

# SKILL: PHPDoc Documentation

# SKILL: PHP Inline Documentation (WordPress PHPDoc)

Scope: PHP DocBlocks in WordPress themes/plugins.

Apply:
- Coding rules below (CR-DOC-PHP-*)

Refuse:
- If the request is not WP-compatible PHPDoc.

END OF SKILL.

---

# SKILL: JavaScript Style

# SKILL: WordPress JavaScript Style

Scope: JavaScript in WordPress themes/plugins.

Apply:
- Coding rules below (CR-JS-*, CR-GEN-*)

END OF SKILL.

---

# SKILL: PHP Style

# SKILL: WordPress PHP Style

Scope: PHP in WordPress themes/plugins.

Apply:
- Coding rules below (CR-PHP-*, CR-GEN-*)

END OF SKILL.

---

# SKILL: Admin-AJAX

# SKILL: WordPress Admin-AJAX Actions

Scope: wp_ajax handlers in wp-admin or authenticated endpoints.

Apply:
- Security rules below

END OF SKILL.

---

# SKILL: Backend Development

# SKILL: WordPress Backend Development

Scope: PHP backend code for plugins/themes (admin actions, options, meta, shortcodes, templates, cron).

Apply:
- Security rules below

END OF SKILL.

---

# SKILL: Database Access

# SKILL: Database Access

Scope: Any code that reads/writes WordPress DB, including custom tables and `$wpdb`.

Apply:
- Security rules below

END OF SKILL.

---

# SKILL: Forms

# SKILL: WordPress Forms (Frontend or Admin)

Scope: Creating forms, processing submissions, saving data, and rendering feedback.

Apply:
- Security rules below

END OF SKILL.

---

# SKILL: Frontend

# SKILL: WordPress Frontend & DOM Manipulation

Scope: JavaScript used in WordPress themes and plugins (UI, events, AJAX/REST, DOM updates).

Apply:
- Security rules below

Extra guidance (unique to this skill):

- Prefer safe DOM APIs (textContent, value, createElement, appendChild, replaceChildren).
- Avoid unsafe DOM sinks when handling untrusted data.

END OF SKILL.

---

# SKILL: REST API

# SKILL: WordPress REST API Endpoints

Scope: Registering REST routes, permission callbacks, request handling, and REST responses.

Apply:
- Security rules below

END OF SKILL.

---

# SKILL: Security Review

# SKILL: WordPress Security Review

Scope: Reviewing existing code for security issues and recommending fixes.

Apply:
- Security rules below

Output:

- Reference SR-* IDs in findings.

END OF SKILL.
