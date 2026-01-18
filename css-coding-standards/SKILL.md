---
name: css-coding-standards
description: Guidelines for writing clean, maintainable CSS code following WordPress and Harry Roberts best practices. Use when generating or reviewing CSS code, including formatting, naming conventions, BEM methodology, selector specificity, property ordering, and architectural patterns.
---

# CSS Coding Standards

Guidelines distilled from WordPress CSS coding standards and Harry Roberts CSS guidelines.

## Formatting

- **One selector per line**: Each selector should be on its own line for better readability
- **One declaration per line**: Each CSS property should be on its own line
- **Braces on new lines**: Opening and closing braces should be on their own lines
- **Line length**: Keep lines around 80 characters when possible
- **Spacing**: Two blank lines between major sections, one blank line between rule blocks
- **Indentation**: Use consistent indentation (tabs for WordPress projects, two spaces for others)

## Naming & Selectors

- **Class names**: Use lowercase, hyphenated class names (e.g., `.main-header`, `.nav-item`)
- **BEM methodology**: Prefer BEM-style naming (`block__element--modifier`)
  - Block: `.card`
  - Element: `.card__title`
  - Modifier: `.card--featured`
- **Avoid IDs for styling**: Use classes instead of IDs for styling purposes
- **Avoid over-qualification**: Don't unnecessarily qualify selectors (e.g., use `.nav` instead of `ul.nav`)
- **Avoid deep nesting**: Keep descendant chains short and selectors reusable
- **Specificity**: Keep selector specificity as low as possible

## Properties & Order

- **Syntax**: `property: value;` with one space after the colon
- **Lowercase values**: Use lowercase for all values except font names and vendor-specific values
- **Logical grouping**: Group related properties together in this order:
  1. Display & positioning (`display`, `position`, `top`, `right`, `bottom`, `left`, `z-index`)
  2. Box model (`width`, `height`, `margin`, `padding`, `border`)
  3. Colors & typography (`color`, `background`, `font-family`, `font-size`, `line-height`)
  4. Other properties (`transition`, `animation`, `transform`)
- **Shorthand properties**: Favor shorthand properties when appropriate
- **TRBL ordering**: Use Top-Right-Bottom-Left order for directional properties

## Comments

- **Section headers**: Use clear section headers in large files
- **Table of contents**: Include a TOC at the top of large CSS files
- **Intent documentation**: Comment the intent and reasoning, not just what the code does
- **Explain hacks**: Document any CSS hacks or workarounds
- **!important usage**: Always explain why `!important` is necessary

## Architecture

- **Maintainability**: Write CSS that is easy to maintain and scale
- **Reusable components**: Build reusable components, objects, and utilities
- **Low specificity**: Keep specificity as low as possible to avoid conflicts
- **Avoid magic numbers**: Don't use arbitrary values; document any that are necessary
- **Separate concerns**: Keep JavaScript hooks separate using `data-js` attributes or `.js-` prefixed classes

## Media Queries

- **Placement**: Group media queries near the end of the file or within their relevant sections
- **Indentation**: Indent nested rules one level inside media queries

## AI Requirements

When generating CSS code, you must:

- Emit valid, readable CSS with proper formatting
- Use hyphenated, BEM-friendly class names
- Keep selector specificity low
- Group properties logically
- Comment special cases and any `!important` usage
- Use semantic class names over presentational ones
- Follow the formatting and naming conventions outlined above
