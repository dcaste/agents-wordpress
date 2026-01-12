# CSS Guidelines (Harry Roberts) – AI Coding Cheatsheet

High-level advice for writing sane, manageable, scalable CSS.

## 1. Goals of the Styleguide

- Make CSS:
  - Maintainable and predictable.
  - Scalable for large teams and long-lived products.
  - Easy to onboard new developers.

## 2. Syntax and Formatting

- Two-space indents; no tabs.
- Multi-line style:
  - One selector per line.
  - One declaration per line.
- Keep lines under ~80 characters.
- Use whitespace to reveal structure.
- Split large codebases into multiple files and assemble via build tools.

## 3. Section Titling

- Use clear section titles and a table of contents:

```css
/*------------------------------------*\
  #SECTION-TITLE
\*------------------------------------*/
```

- Blank lines between sections and subsections to improve scanning.

## 4. Commenting

- High-level comments describe purpose of components or objects.
- Low-level comments explain specific hacks or tricky logic.
- Document *why* something exists, not just *what* it does.

## 5. Naming Conventions (BEM-style)

- Prefer hyphen-delimited names: `.site-header`, `.nav-primary`.
- Use BEM-like naming:
  - Block: `.site-nav`
  - Element: `.site-nav__item`
  - Modifier: `.site-nav--compact`
- Avoid presentational names; reflect the role in the UI.

## 6. Selectors

- Express intent, not DOM structure.
- Keep selectors shallow and location-independent.
- Avoid long descendant chains and over-qualification (`aside.widget`).
- Prefer classes over IDs for styling to avoid specificity issues.

## 7. JavaScript Hooks

- Use separate hooks for JS behaviour:
  - `data-js="toggle"` or `.js-toggle`.
- Do not rely on purely presentational classes for JS.

## 8. Specificity and !important

- Keep specificity low and flat; prefer composable utilities and components.
- Avoid `!important` except when absolutely necessary and document it.
- Refactor selectors instead of fighting specificity wars.

## 9. Architecture and Principles

- Object-oriented CSS mindset:
  - Build small, reusable “objects” or components.
- Single Responsibility Principle:
  - One clear purpose per object, utility, or module.
- Open/Closed Principle:
  - Extend via modifiers instead of rewriting core objects.
- DRY:
  - Avoid duplication by centralizing common patterns.
- Separation of concerns:
  - HTML for structure, CSS for appearance.
  - Classes form the contract between them; using classes does not break separation.

## 10. Misconceptions

- Class-based styling is not inherently bad; overloading descendant selectors can be worse.
- Do not encode DOM structure into CSS via deep nesting.
- Prioritize reusability and independence of components.

## 11. AI Usage Rules

When generating CSS, the AI must:

- Use BEM-like, hyphenated class names for components.
- Keep selectors short, reusable, and stable.
- Organize styles into objects, components, and utilities with clear section titles.
- Comment design decisions and non-obvious code.
