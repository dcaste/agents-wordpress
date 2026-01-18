---
name: javascript-coding-standards
description: Guidelines for writing clean, maintainable JavaScript code following WordPress standards. Use when generating or reviewing JavaScript, including style, formatting, variable declarations, type checking, control flow, JSDoc documentation, and best practices.
---

# JavaScript Coding Standards

Guidelines distilled from WordPress JavaScript coding standards and documentation standards.

## Style & Formatting

- **Spacing**: Include spaces after keywords and around operators
  - Correct: `if (condition) {`
  - Correct: `x = y + z`
- **Commas**: Space after commas in arrays and function arguments
  - Correct: `[1, 2, 3]`
  - Correct: `function(a, b, c)`
- **Braces**: Opening brace on same line, closing brace on its own line
  ```javascript
  if (condition) {
      // code
  }
  ```
- **Line length**: Keep lines reasonable (under 100 characters when possible)
- **Semicolons**: Always terminate statements with semicolons

## Variables & Naming

- **Variable declarations**: 
  - Prefer `const` for values that won't be reassigned
  - Use `let` for values that will change
  - Reserve `var` for legacy code or specific scoping needs
- **Naming conventions**:
  - `camelCase` for variables and functions
  - `PascalCase` for classes and constructors
  - `UPPER_SNAKE_CASE` for constants
- **Scope**: Declare variables at the top of their scope
- **Descriptive names**: Use clear, descriptive variable and function names

## Equality & Type Checking

- **Strict equality**: Use `===` and `!==` instead of `==` and `!=`
- **Recommended type checks**:
  - String: `typeof value === 'string'`
  - Number: `typeof value === 'number'`
  - Boolean: `typeof value === 'boolean'`
  - Object: `typeof value === 'object'`
  - Array: `Array.isArray(value)`
  - Null: `value === null`
  - Null or undefined: `value == null`
  - Undefined: `typeof value === 'undefined'`

## Strings & Data Structures

- **String quotes**: Default to single quotes for strings
  - Correct: `const message = 'Hello world';`
  - Escape internal quotes: `const quote = 'He said, \'Hello\'';`
- **Array literals**: Use `[]` instead of `new Array()`
- **Object literals**: Use `{}` instead of `new Object()`
- **Property access**: Prefer dot notation when possible
  - Correct: `object.property`
  - Use bracket notation for dynamic keys: `object[key]`
- **Array methods**: Use higher-order functions appropriately
  - `map()`, `filter()`, `reduce()`, `forEach()`, etc.

## Control Flow

- **Switch statements**: Indent `case` inside `switch`
  ```javascript
  switch (value) {
      case 'a':
          // code
          break;
      case 'b':
          // code
          break;
      default:
          // code
  }
  ```
- **Break statements**: Always use `break` unless intentionally falling through
- **Fall-through comments**: Comment intentional fall-throughs
  ```javascript
  case 'a':
      // Falls through
  case 'b':
      // code
  ```

## Comments & Documentation

### Inline Comments

- Use `//` for single-line comments
- Use `/* ... */` for multi-line comments
- Keep comments close to relevant code

### JSDoc Comments

Use JSDoc (`/** ... */`) for:
- Public APIs
- Classes and constructors
- Methods and functions
- Events
- Namespaces
- Important objects
- File headers (when relevant)

**JSDoc formatting**:
- Summaries are one sentence, third-person singular
- Align tags vertically
- Wrap lines at approximately 80 characters
- Include `@param`, `@return`, `@since` as needed

**Example**:
```javascript
/**
 * Calculates the sum of two numbers.
 *
 * @since 1.0.0
 *
 * @param {number} a - The first number.
 * @param {number} b - The second number.
 * @return {number} The sum of a and b.
 */
function add(a, b) {
    return a + b;
}
```

**Common JSDoc tags**:
- `@param {type} name - Description` - Function parameters
- `@return {type} Description` - Return value
- `@since version` - Version introduced
- `@deprecated version Use alternative()` - Deprecated items
- `@see Reference` - Related items
- `@example` - Usage examples
- `@throws {ErrorType} Description` - Exceptions thrown

## Linting & Libraries

- **Linting**: Follow project lint configuration (ESLint, JSHint, etc.)
- **Libraries**: Use project-standard libraries consistently
- **Dependencies**: Keep dependencies up to date and minimal

## AI Requirements

When generating JavaScript code, you must:

- Emit clear, lintable JavaScript that follows spacing and naming rules
- Use strict equality (`===`, `!==`) and recommended type checks
- Terminate all statements with semicolons
- Prefer `const` and `let` over `var`
- Avoid clever one-liners; prioritize readability
- Add JSDoc comments for exported/public APIs with consistent tag order
- Use descriptive variable and function names
- Follow proper indentation and brace placement
- Include appropriate error handling
- Use modern JavaScript features appropriately (ES6+)
