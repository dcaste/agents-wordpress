# CSS Coding Standards (AI Coding Guidelines)

These rules adapt the WordPress CSS Coding Standards for AI-generated CSS.

## 1. General Principles

- Stylesheets should look as if written by a single author.
- Prioritize readability, consistency, and maintainability.
- Avoid overly complex selectors and magic numbers.

## 2. Structure and Formatting

- Use tabs to indent each property (or follow project convention).
- Use:
  - Two blank lines between major sections.
  - One blank line between rule blocks in a section.
- Place each selector on its own line.
- Opening brace on its own line; closing brace aligned with selector.

```css
#selector-1,
#selector-2 {
    background: #fff;
    color: #000;
}
```

## 3. Naming and Selectors

- Use lowercase and hyphen-separated names: `.comment-form`, not `.commentForm`.
- Avoid over-qualifying selectors:
  - Prefer `.container` over `div.container`.
- Use semantic names that describe purpose, not visual appearance.
- Attribute selectors use double quotes: `input[type="text"]`.

## 4. Properties and Values

- Format: `property: value;` with a single space after the colon.
- Properties and values lowercase, except font names or vendor-specific values.
- Colors:
  - Use hex (`#fff`) or `rgba()`.
- Use shorthand properties where appropriate (margin, padding, border, background, etc.).

Example:

```css
#selector-1 {
    display: block;
    margin: 0 0 20px 0;
    background: #fff;
    color: #000;
}
```

## 5. Property Ordering

Group properties logically; a common order:

1. Display.
2. Positioning.
3. Box model (margin, padding, width, height, etc.).
4. Colors and typography.
5. Other (transitions, animations, etc.).

Follow TRBL for directional properties (top, right, bottom, left).

## 6. Media Queries

- Place media queries near the end of the file or grouped per section in large files.
- Indent rule sets inside media queries by one level:

```css
@media all and (max-width: 699px) and (min-width: 520px) {
    .selector {
        /* styles */
    }
}
```

## 7. Comments

- Use a table of contents in long stylesheets.
- Section header:

```css
/**
 * 1.0 Section title
 *
 * Description.
 */
```

- Inline comments to explain non-obvious code:

```css
/* This positions the icon over the text */
.icon {
    position: absolute;
}
```

- Explain any use of `!important`.

## 8. Best Practices

- Remove redundant or conflicting rules rather than layering on more.
- Avoid magic numbers; document them when necessary.
- Do not restate default browser values unless needed for clarity or resets.

## 9. AI Usage Rules

When generating CSS, the AI must:

- Use semantic, hyphenated class names.
- Follow the formatting rules for selectors and properties.
- Group related properties and keep rule blocks compact and readable.
- Comment any special cases, hacks, or uses of `!important`.
