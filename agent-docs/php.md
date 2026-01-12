# PHP Agent Documentation Rules

Guidelines distilled from `php-documentation-standards.md`.

- **DocBlock scope**: Use PHPDoc for public functions/methods, classes/interfaces/traits, properties/constants, hooks (`do_action`/`apply_filters`), notable globals, includes/requires when relevant, and non-trivial file headers.
- **Voice & content**: Write summaries as single-sentence, third-person singular statements (no HTML/Markdown). Long descriptions are optional and may use Markdown/examples for complex behavior.
- **Placement & formatting**: Place DocBlocks directly above the element; no code between. Wrap lines ~80 chars. Baseline structure includes summary, optional description, `@since`, `@param` (type, `$var`, description), and `@return` when applicable.
- **@since & changelog**: Include `@since x.x.x`; add new `@since` lines for behavioral changes. If unknown, use `@since Unknown`.
- **Deprecated items**: Include `@deprecated version Replacement().` and optional `@see`; keep `@param`/`@return` present.
- **Hooks**: Document actions/filters with purpose, `@since`, and parameter tags matching the hook signature.
- **Inline comments**: Use `//` or `/* ... */` (single asterisk) for inline notes; keep them close to relevant code.
- **AI must**: Add consistent PHPDoc to all public APIs and hooks, with clean tag order and formatting; avoid HTML in summaries/param/return text; use long descriptions for complex behavior or examples.
