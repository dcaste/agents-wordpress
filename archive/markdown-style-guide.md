# Markdown Style Guide (AI Writing Guidelines)

These rules adapt the WordPress Markdown Style Guide for AI-generated Markdown.

## 1. Headings

Use hash characters for headings:

```md
# Heading h1
## Heading h2
### Heading h3
#### Heading h4
##### Heading h5
###### Heading h6
```

- Prefer a single `#` H1 per document.
- Use heading levels to reflect document structure.

## 2. Emphasis

- Italic: wrap with single underscores:

```md
This is _italic text_.
```

- Bold: wrap with double asterisks:

```md
This is **bold text**.
```

- Strikethrough: wrap with double tildes:

```md
This is ~~strikethrough~~ text.
```

## 3. Links

- Basic link syntax:

```md
[Link text](https://example.com/)
```

- Text in `[]`, URL in `()`.

## 4. Blockquotes

- Use `>` at the start of the line:

```md
> Blockquote
>> Nested blockquote
```

- Additional `>` increase the nesting level.

## 5. Lists

- Unordered lists:
  - Use `-` for items; indent sub-items by two spaces.

```md
- Item
  - Subitem
- Another item
```

- Ordered lists:

```md
1. First
2. Second
3. Third
```

## 6. Horizontal Rules

- Use three dashes on a line by themselves:

```md
---
```

## 7. Tables

Basic table:

```md
| Column A | Column B |
| -------- | -------- |
| Alpha    | Bravo    |
```

- Use `-` under the header row.
- Use `|` as column separators.

## 8. Code

- Inline code:
  - Wrap with backticks:

```md
Use the `printf()` function.
```

- Code blocks:
  - Use fenced code blocks with language indicators when possible:

```md
```javascript
function example() {
  return true;
}
```
```

- Common languages: `javascript`, `json`, `css`, `scss`, `html`, `php`, `md`.

## 9. AI Usage Rules

When generating Markdown, the AI must:

- Use a clear heading hierarchy with at most one H1.
- Use `-` for unordered lists, properly indented for sub-items.
- Use fenced code blocks with correct language identifiers.
- Format tables, blockquotes, and links according to these patterns.
