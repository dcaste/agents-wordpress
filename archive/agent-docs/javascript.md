# JavaScript Agent Rules

Guidelines distilled from `js-coding-standards.md` and `js-documentation-standards.md`.

- **Style & formatting**: Space after keywords and around operators; spaces after commas; braces on same line, closing brace on its own line; keep lines reasonable (<100 chars). Always terminate statements with semicolons.
- **Variables & naming**: Prefer `const`, then `let`; reserve `var` for legacy needs. Use `camelCase` for vars/functions, `PascalCase` for classes, `UPPER_SNAKE_CASE` for constants. Declare variables at top of scope; use descriptive names.
- **Equality & types**: Use `===`/`!==`; recommended checks include `typeof value === 'string'|'number'|'boolean'|'object'`, `Array.isArray()`, `value === null`, `value == null` for null/undefined, `typeof value === 'undefined'`.
- **Strings & structures**: Default to single quotes; escape internal quotes. Prefer literals for arrays (`[]`) and objects (`{}`); use dot notation when possible. Use higher-order helpers (`map`, `forEach`) appropriately.
- **Control flow**: Indent `case` inside `switch`; use `break` unless intentionally falling through (comment it).
- **Comments & docs**: Use `//` or `/* ... */` for inline comments. JSDoc (`/** ... */`) for public APIs, classes, methods, events, namespaces, important objects, and files. Summaries are one-sentence, third-person singular; align tags; wrap ~80 chars; include `@param`/`@return`/`@since` as needed.
- **Linting & libraries**: Follow project lint config (ESLint/JSHint); use project-standard libraries consistently.
- **AI must**: Emit clear, lintable JS that follows spacing, naming, and semicolon rules; use strict equality and recommended type checks; avoid clever one-liners. Add JSDoc for exported/public APIs with consistent tag order and formatting.
