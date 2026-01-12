# JavaScript Documentation Standards (AI Coding Guidelines)

These rules adapt the WordPress JavaScript Documentation Standards for AI-generated code comments.

## 1. General Principles

- Use JSDoc 3 style for all JavaScript documentation.
- Prefer formatted docblocks over ad-hoc comments for public APIs.
- Focus on **what** and **when**, not the high-level *why*.
- Do not refactor code solely because you are editing documentation.

## 2. What Must Be Documented

Add docblocks for:

- Public functions and methods.
- Classes and prototypes.
- Class members and properties.
- Namespaces and modules.
- Events (fired or listened to).
- Important objects, closures, and object properties.
- Non-trivial files (file-level headers).

## 3. Language & Grammar

- Write summaries as single sentences in third-person singular:
  - "Handles click events on the submit button."
- Use clear English and avoid business context unless needed.
- Short description:
  - One sentence.
  - No HTML or Markdown.
- Long description (optional):
  - May use Markdown lists and inline code.
  - Only when more detail is necessary.

## 4. Docblock Formatting

- Place docblock directly above the symbol it documents.
- Wrap text at around 80 characters.
- Align related tags vertically.

Example:

```js
/**
 * Short summary.
 *
 * Longer description if needed.
 *
 * @since  x.x.x
 * @param  {Type} paramName Description.
 * @return {Type}           Description.
 */
function doSomething( paramName ) {
}
```

Guidelines:

- `@param` and `@return` descriptions must not contain HTML or Markdown.
- Refer to HTML elements descriptively (e.g. "image element", "link tag").
- Keep alignment consistent in a file.

## 5. Functions & Methods

For any function or method:

- Include:
  - Summary line.
  - Optional long description.
  - `@since` (when versioning matters).
  - `@param` for each parameter.
  - `@return` when returning a value.
- Mark deprecated APIs with:

```js
/**
 * Summary.
 *
 * @since      x.x.x
 * @deprecated y.y.y Use otherFunction() instead.
 */
```

## 6. Classes, Members, Namespaces

Classes:

```js
/**
 * Short description.
 *
 * Longer description.
 *
 * @since x.x.x
 */
class MyClass {
}
```

Members:

```js
/**
 * Description.
 *
 * @since x.x.x
 * @type  {Type}
 */
MyClass.prototype.member = value;
```

Namespaces:

```js
/**
 * Short description.
 *
 * @namespace myNamespace
 * @since     x.x.x
 *
 * @property {Type} key Description.
 */
```

## 7. Inline Comments & File Headers

Inline comments:

- Single-line: `// Explain complex or non-obvious logic.`
- Multi-line: `/* ... */` (single asterisk).
- Never start inline multi-line comments with `/**` (reserved for JSDoc).

File headers:

```js
/**
 * Summary.
 *
 * Description.
 *
 * @file   Description of what this file defines.
 * @since  x.x.x
 */
```

## 8. Supported Tags

Prefer canonical JSDoc tags:

- `@class`, `@function`, `@param`, `@return`, `@since`,
  `@namespace`, `@member`, `@property`, `@event`, `@fires`, `@typedef`, `@enum`.

Avoid unsupported or duplicate synonyms like `@returns` or `@method`.

## 9. AI Usage Rules

When generating JavaScript with documentation, the AI must:

- Use `/** ... */` for docblocks and `/* ... */` or `//` for plain comments.
- Provide docblocks for all public or exported APIs.
- Keep summaries to one sentence, with no markup, ending with a period.
- Use consistent tag ordering and alignment throughout the file.
