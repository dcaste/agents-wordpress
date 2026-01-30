# CODING_RULES.md (WordPress Coding Standards — Normative)

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

(Implementation details are handled in SKILLS/a11y.md.)

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
