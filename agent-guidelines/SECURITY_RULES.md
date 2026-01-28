# SECURITY_RULES.md

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

Each rule is normative. SKILLS MUST reference these IDs.

---

## SR-GEN: General security model

- **SR-GEN-001 (Untrusted by default):** All external input MUST be treated as untrusted (including user input, third-party APIs, and data from the database unless verified). citeturn0search5
- **SR-GEN-002 (Defense in depth):** Validation, sanitization, escaping, authorization, and CSRF protection are independent controls; passing one MUST NOT imply the others.
- **SR-GEN-003 (Prefer WP APIs):** WordPress core APIs SHOULD be used where they exist, rather than ad-hoc equivalents.

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
