# JavaScript Coding Standards (AI Coding Guidelines)

These rules adapt the WordPress JavaScript Coding Standards for AI-generated JS.

## 1. General Style

- Code should look as if written by a single person.
- Do not submit whitespace-only refactors to legacy files.
- New or changed code must conform to these standards and pass linting.

## 2. Spacing & Formatting

- Space after keywords and around operators:

```js
if ( condition ) {
    result = a + b;
}
```

- Spaces after commas in arguments and arrays.
- Opening brace on the same line; closing brace on its own line.
- Keep lines at a reasonable length (ideally under 100 characters).

## 3. Semicolons

- Always terminate statements with semicolons.

## 4. Variables and Scope

- Prefer `const` for non-reassigned values.
- Use `let` for reassignable locals.
- Limit `var` to legacy code or when required by project constraints.
- Declare variables at the top of their scope.

## 5. Naming Conventions

- Variables and functions: `camelCase`.
- Constructors and classes: `PascalCase`.
- Constants: `UPPER_SNAKE_CASE`.
- Use descriptive names; avoid unnecessary abbreviations.

## 6. Comments

- Single-line comments: `// Comment`.
- Multi-line comments: `/* Comment */`.
- JSDoc blocks: `/** ... */` (see JS documentation standards).
- Avoid noisy or redundant comments; focus on explaining complex logic.

## 7. Equality and Type Checks

- Use strict equality: `===` and `!==`.
- Recommended checks:
  - `typeof value === 'string'`
  - `typeof value === 'number'`
  - `typeof value === 'boolean'`
  - `typeof value === 'object'` or helper utilities.
  - `Array.isArray( value )` or library helpers.
  - `value === null` for `null`.
  - `value == null` for `null` or `undefined`.
  - `typeof value === 'undefined'` for `undefined`.

## 8. Strings

- Use single quotes by default:

```js
var title = 'My title';
```

- Escape internal single quotes: `'Don\'t do that.'`.

## 9. Switch Statements

- Use when they improve clarity.
- Indent `case` one level inside `switch`.
- Use `break` unless intentionally falling through (comment that).

```js
switch ( event.keyCode ) {
    case ENTER:
    case SPACE:
        result = 'commit';
        break;
    case ESCAPE:
        result = 'exit';
        break;
    default:
        result = 'default';
}
```

## 10. Arrays, Objects, Iteration

- Arrays:
  - Use `[]` instead of `new Array()`.
- Objects:
  - Use `{}` and dot notation (`obj.prop`) where possible.
- Loops:
  - Cache collection length before iterating when needed.
  - Use higher-order functions or library helpers (`forEach`, `map`) when appropriate.

## 11. Libraries and Tools

- Use the project’s standard libraries (jQuery, Underscore, etc.) consistently.
- Run JSHint/ESLint (based on project config) and fix all lint errors.

## 12. AI Usage Rules

When generating JavaScript, the AI must:

- Follow spacing, naming, and brace style rules.
- Use strict equality and recommended type checks.
- Use literal array and object syntax.
- Avoid overly clever or terse one-liners; prefer clarity.
- Add JSDoc comments for public or exported APIs as per JS documentation standards.
