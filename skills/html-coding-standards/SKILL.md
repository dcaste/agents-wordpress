---
name: html-coding-standards
description: Guidelines for writing valid, semantic, and accessible HTML following WordPress standards. Use when generating or reviewing HTML markup, including proper structure, element usage, accessibility requirements, and formatting conventions.
---

# HTML Coding Standards

Guidelines distilled from WordPress HTML coding standards.

## Validity & Structure

- **W3C validation**: Generate W3C-valid HTML markup
- **Well-nested elements**: Ensure all elements are properly nested
- **Properly closed tags**: Close all tags that require closing
- **Semantic elements**: Use HTML5 semantic elements appropriately:
  - `<main>` for main content
  - `<nav>` for navigation
  - `<section>` for thematic grouping
  - `<article>` for self-contained content
  - `<aside>` for tangentially related content
  - `<header>` and `<footer>` for page/section headers and footers

## Self-Closing Syntax

- **Void elements**: Include a space before `/>` for void elements
  - Correct: `<img src="image.jpg" alt="Description" />`
  - Correct: `<br />`
  - Correct: `<input type="text" />`
  - Correct: `<meta charset="utf-8" />`

## Tags & Attributes

- **Lowercase names**: Use lowercase for all tag and attribute names
  - Correct: `<div class="container">`
  - Incorrect: `<DIV CLASS="container">`
- **Quote attribute values**: Always quote attribute values (single or double quotes consistently)
  - Correct: `<a href="page.html" class="link">`
  - Incorrect: `<a href=page.html class=link>`
- **Machine-readable values**: Use lowercase for machine-readable values
  - Correct: `<meta charset="utf-8">`
  - Correct: `<input type="email">`
- **Human-readable text**: Natural case is acceptable for human-readable content
  - Acceptable: `<img alt="Product Image" />`

## Indentation & Readability

- **Consistent indentation**: Indent nested content consistently (tabs or spaces per project)
- **Avoid unnecessary nesting**: Don't nest elements unnecessarily
- **No table layouts**: Avoid using tables for layout purposes
- **Break lines**: Break lines to keep structure scannable and readable
- **Logical structure**: Maintain a clear, logical document structure

## Accessibility

- **Alt attributes**: Always include `alt` attributes on images
  - Decorative images: `alt=""`
  - Meaningful images: `alt="Descriptive text"`
- **Keyboard accessibility**: Ensure interactive elements are keyboard accessible
  - Use `<button>` for buttons
  - Use `<a href="...">` for links
  - Include appropriate ARIA attributes when needed
- **Heading hierarchy**: Use logical heading hierarchy (`<h1>` through `<h6>`)
  - One `<h1>` per page
  - Don't skip heading levels
- **Form labels**: Associate labels with form inputs
  - Use `<label for="input-id">` with matching `id` on input
  - Or wrap input inside `<label>`
- **Semantic markup**: Use semantic HTML elements over generic `<div>` and `<span>` when appropriate

## AI Requirements

When generating HTML code, you must:

- Produce valid, accessible HTML markup
- Use clean, consistent indentation
- Quote all attribute values
- Include correct self-closing spacing for void elements
- Prefer semantic tags over generic wrappers
- Include proper `alt` attributes on all images
- Ensure keyboard accessibility for interactive elements
- Maintain logical heading hierarchy
- Follow lowercase naming for tags and attributes
