# HTML Coding Standards (AI Coding Guidelines)

These rules adapt the WordPress HTML Coding Standards for AI-generated markup.

## 1. Validation and Structure

- Generate HTML that is valid according to W3C standards.
- Ensure tags are properly nested and closed.
- Use meaningful, semantic elements (`<main>`, `<nav>`, `<section>`, etc.) where appropriate.

## 2. Self-Closing Elements

- Include a space before the slash in self-closing tags:

```html
<br />
<img src="image.jpg" alt="Description" />
```

## 3. Tags and Attributes

- Tag names and attribute names must be lowercase:

```html
<a href="https://example.com" title="Example link">Example</a>
```

- Attribute values:
  - Lowercase for machine-readable values (`"text/html"`, `"utf-8"`).
  - Human-readable text can use normal capitalization.

## 4. Quotes

- Always quote attribute values.
- Use either single or double quotes, but be consistent within a project.

Correct:

```html
<input type="text" name="email" disabled="disabled" />
<input type='text' name='email' disabled='disabled' />
```

Incorrect:

```html
<input type=text name=email disabled>
```

## 5. Indentation and Readability

- Indent nested elements consistently (tabs or spaces per project).
- Use line breaks to make the structure easy to scan.
- Avoid unnecessary nesting and complicated table-based layouts.

## 6. Accessibility Considerations

- Always include `alt` attributes on images.
- Ensure interactive elements are keyboard accessible (`<button>`, `<a>` with `href`, proper ARIA as needed).
- Use headings in a logical hierarchy.

## 7. AI Usage Rules

When generating HTML, the AI must:

- Produce valid, well-formed, and accessible markup.
- Use proper self-closing syntax with a space before `/>`.
- Keep tags and attribute names lowercase; attribute values always quoted.
- Maintain clean indentation and readable structures.
