# HTML Agent Rules

Guidelines distilled from `html-coding-standards.md`.

- **Validity & structure**: Generate W3C-valid, well-nested, and properly closed markup. Use semantic elements (`main`, `nav`, `section`, etc.) appropriately.
- **Self-closing syntax**: Include a space before `/>` for void elements (`<img ... />`, `<br />`).
- **Tags & attributes**: Lowercase tag and attribute names; always quote attribute values (single or double consistently). Machine-readable values lowercase (`utf-8`), human text may be natural case.
- **Indentation & readability**: Indent nested content consistently; avoid unnecessary nesting and table-based layouts. Break lines to keep structure scannable.
- **Accessibility**: Always set `alt` on images; ensure interactive elements are keyboard accessible (`button`, `a[href]`, appropriate ARIA). Use logical heading hierarchy.
- **AI must**: Produce valid, accessible HTML with clean indentation, quoted attributes, and correct self-closing spacing. Prefer semantic tags over generic wrappers.
