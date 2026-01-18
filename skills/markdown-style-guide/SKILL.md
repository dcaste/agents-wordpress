---
name: markdown-style-guide
description: Guidelines for writing consistent, well-formatted Markdown documents. Use when creating or editing Markdown files, including headings, emphasis, lists, links, code blocks, tables, and other formatting elements.
---

# Markdown Style Guide

Guidelines for writing clean, consistent Markdown documents.

## Headings

- **Hash-prefixed headings**: Use `#` through `######` for headings
- **Single H1**: Use only one `<h1>` (single `#`) per document
- **Logical hierarchy**: Maintain proper heading levels without skipping
  - Correct: `#` → `##` → `###`
  - Incorrect: `#` → `###` (skipped `##`)
- **Spacing**: Add a blank line before and after headings

**Example**:
```markdown
# Main Title

## Section Heading

### Subsection Heading
```

## Emphasis

- **Italic**: Use underscores `_text_` for italic text
  - Example: `_emphasized text_` → _emphasized text_
- **Bold**: Use double asterisks `**text**` for bold text
  - Example: `**strong text**` → **strong text**
- **Strikethrough**: Use double tildes `~~text~~` for strikethrough
  - Example: `~~deleted text~~` → ~~deleted text~~
- **Combined**: Can combine emphasis styles
  - Example: `**_bold and italic_**` → **_bold and italic_**

## Lists

### Unordered Lists

- Use `-` (hyphen) for unordered list items
- Indent sub-items by two spaces
- Add blank line before and after lists

**Example**:
```markdown
- First item
- Second item
  - Nested item
  - Another nested item
- Third item
```

### Ordered Lists

- Use `1.`, `2.`, `3.`, etc. for ordered lists
- Indent sub-items by two spaces
- Can use `1.` for all items (auto-numbering)

**Example**:
```markdown
1. First step
2. Second step
   1. Sub-step
   2. Another sub-step
3. Third step
```

## Links & References

### Inline Links

- **Format**: `[link text](https://example.com/)`
- **Descriptive text**: Use meaningful link text, not "click here"
- **Relative links**: Use relative paths for internal links

**Example**:
```markdown
Visit the [documentation](https://example.com/docs) for more information.
```

### Reference Links

- **Format**: `[link text][reference]` with `[reference]: URL` at bottom
- **Useful for**: Repeated links or keeping text readable

**Example**:
```markdown
Check out [Google][1] and [GitHub][2].

[1]: https://google.com
[2]: https://github.com
```

## Blockquotes

- **Format**: Start lines with `>`
- **Nesting**: Add more `>` for nested quotes
- **Spacing**: Add blank line before and after blockquotes

**Example**:
```markdown
> This is a blockquote.
> It can span multiple lines.
>
> > This is a nested blockquote.
```

## Code

### Inline Code

- **Format**: Wrap code in single backticks
- **Use for**: Variable names, function names, short code snippets

**Example**:
```markdown
Use the `console.log()` function to debug.
```

### Fenced Code Blocks

- **Format**: Use triple backticks with language identifier
- **Language tags**: Specify language for syntax highlighting
- **Common languages**: `javascript`, `python`, `php`, `css`, `html`, `bash`, `json`

**Example**:
````markdown
```javascript
function greet(name) {
    console.log(`Hello, ${name}!`);
}
```
````

### Indented Code Blocks

- **Format**: Indent code by 4 spaces or 1 tab
- **Preference**: Use fenced code blocks instead for better control

## Tables

- **Format**: Use pipes `|` to separate columns
- **Header separator**: Use hyphens `-` in the second row
- **Alignment**: Use colons `:` for alignment
  - Left: `:---`
  - Center: `:---:`
  - Right: `---:`

**Example**:
```markdown
| Name    | Age | City       |
|---------|-----|------------|
| Alice   | 30  | New York   |
| Bob     | 25  | London     |
| Charlie | 35  | Tokyo      |
```

**With alignment**:
```markdown
| Left    | Center | Right |
|:--------|:------:|------:|
| Text    | Text   | Text  |
```

## Horizontal Rules

- **Format**: Three or more hyphens `---` on a line by itself
- **Spacing**: Add blank lines before and after

**Example**:
```markdown
Section one content.

---

Section two content.
```

## Images

- **Format**: `![alt text](image-url)`
- **Alt text**: Always include descriptive alt text
- **Relative paths**: Use relative paths for local images

**Example**:
```markdown
![Screenshot of the dashboard](./images/dashboard.png)
```

## Task Lists

- **Format**: Use `- [ ]` for unchecked, `- [x]` for checked
- **Useful for**: Checklists, to-do lists

**Example**:
```markdown
- [x] Completed task
- [ ] Pending task
- [ ] Another pending task
```

## Best Practices

### Spacing

- Add blank line before and after:
  - Headings
  - Lists
  - Code blocks
  - Blockquotes
  - Tables
  - Horizontal rules
- Don't add trailing spaces at end of lines (unless for line breaks)

### Line Length

- Keep lines reasonably short (80-100 characters when possible)
- Break long paragraphs into multiple lines for better diff viewing

### Consistency

- Choose one style and stick to it throughout the document
- Use consistent heading styles
- Use consistent list markers
- Use consistent emphasis markers

## AI Requirements

When generating Markdown documents, you must:

- Keep heading hierarchy clear with a single H1
- Use `-` for unordered lists
- Prefer fenced code blocks with language tags over indented blocks
- Follow link, blockquote, and table patterns consistently
- Include descriptive alt text for all images
- Add appropriate blank lines for readability
- Use semantic emphasis (italic for emphasis, bold for strong importance)
- Maintain consistent formatting throughout the document
- Use proper heading levels without skipping
- Include language identifiers in code blocks for syntax highlighting
