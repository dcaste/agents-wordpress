# CSS Agent Rules

Guidelines distilled from `css-coding-standards.md` and `css-guidelines-harry-roberts.md`.

- **Formatting**: One selector per line, one declaration per line, braces on new lines; keep lines ~80 chars; two blank lines between major sections and one between rule blocks. Indent consistently (project default; tabs in WP guides, two spaces in Harry Roberts).
- **Naming & selectors**: Lowercase, hyphenated class names; prefer BEM-style (`block__element--modifier`). Avoid IDs for styling, over-qualification, and deep descendant chains; keep selectors short and reusable.
- **Properties & order**: `property: value;` with one space after the colon; use lowercase values (except fonts/vendor). Group logically: display → positioning → box model → colors/typography → other (transitions/animations). Favor shorthands and TRBL ordering.
- **Comments**: Use section headers and TOCs in large files. Comment intent and any hacks; explain all `!important` usages. Document why when something is non-obvious.
- **Architecture**: Aim for maintainable, scalable CSS. Build reusable components/objects/utilities; keep specificity low; avoid magic numbers and document any that remain. Keep JS hooks separate (`data-js`, `.js-`).
- **Media queries**: Group near the end or per section; indent nested rules one level.
- **AI must**: Emit valid, readable CSS with hyphenated/BEM-friendly names, low specificity, and sensible grouping. Comment special cases and any `!important`. Use semantic class names over presentational ones.
