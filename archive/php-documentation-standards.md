# PHP Documentation Standards (AI Coding Guidelines)

These rules adapt the WordPress PHP inline documentation standards for AI-generated PHP docs.

## 1. General Principles

- Use PHPDoc-style DocBlocks for public functions, methods, classes, hooks, and constants.
- Document what something does and when it runs, not deep business logic.
- Write in third-person singular:
  - "Displays the last modified date."
- Do not refactor code unrelated to the documentation change.

## 2. What Must Be Documented

Create DocBlocks for:

- Functions and class methods.
- Classes, interfaces, traits.
- Class properties and constants.
- Hooks (`do_action()`, `apply_filters()`).
- Global variables with non-obvious meaning.
- Includes and requires when relevant.
- File headers for non-trivial files.

## 3. Language, Grammar, Style

- Summaries:
  - Short, one sentence, no HTML or Markdown.
  - Explain the purpose of the symbol.
- Long descriptions:
  - Optional, can use Markdown and code examples.
  - Use complete sentences.

Examples:

- Functions: “Retrieves the post title.”
- Actions: “Fires after the post is saved.”
- Filters: “Filters the content of the post.”

## 4. DocBlock Placement & Formatting

- Place DocBlocks directly above the element they document.
- No code between DocBlock and declaration.
- Wrap lines at about 80 characters.

Baseline structure:

```php
/**
 * Summary.
 *
 * Description. Optional, more detailed explanation.
 *
 * @since x.x.x
 * @param type $var Description.
 * @return type Description.
 */
function function_name( $var ) {
}
```

- No HTML in summaries, `@param`, or `@return` descriptions.
- Use Markdown lists and fenced code blocks in long descriptions when useful.

## 5. @since and Changelog

- Each function, method, class, and hook should have an `@since` tag when versioning applies.
- Version format: `3.9.0`.
- When behaviour changes, add additional `@since` lines:

```php
/**
 * Summary.
 *
 * @since 3.0.0
 * @since 3.8.0 Added the `$foo` parameter.
 * @since 4.1.0 The `$force` parameter is now optional.
 */
```

- If unknown: `@since Unknown`.

## 6. Deprecated Items

Deprecated functions, methods, or hooks:

```php
/**
 * Summary.
 *
 * Description.
 *
 * @since      x.x.x
 * @deprecated y.y.y Use new_function_name().
 * @see        new_function_name()
 *
 * @param type $var Description.
 * @return type Description.
 */
```

## 7. Classes, Properties, Constants

Classes:

```php
/**
 * Short summary.
 *
 * Longer description.
 *
 * @since x.x.x
 */
class My_Class {
}
```

Properties and constants:

```php
/**
 * Description.
 *
 * @since x.x.x
 * @var   type $property Description.
 */
protected $property;
```

## 8. Hooks (Actions & Filters)

For actions:

```php
/**
 * Fires after the post content is filtered.
 *
 * @since 4.0.0
 *
 * @param string $content The filtered post content.
 */
do_action( 'the_content', $content );
```

For filters:

```php
/**
 * Filters the post title.
 *
 * @since 1.0.0
 *
 * @param string $title   The post title.
 * @param int    $post_id The post ID.
 */
$title = apply_filters( 'the_title', $title, $post_id );
```

## 9. Inline Comments

- Single-line: `// Comment text.`
- Multi-line: `/* Comment text. */` (single asterisk).
- Keep them close to the code they describe.

## 10. File Headers

Sample header:

```php
/**
 * Widgets API: WP_Widget class.
 *
 * Description of what this file provides.
 *
 * @link    https://example.com/
 * @package Package_Name
 * @subpackage Subpackage_Name
 * @since   x.x.x
 */
```

## 11. Common Tags

Use:

- `@since`
- `@param`
- `@return`
- `@see`
- `@link`
- `@global`
- `@deprecated`
- `@var`
- `@throws` (when exceptions are used)

Avoid adding `@author` for core-like or shared code.

## 12. AI Usage Rules

When generating PHP with documentation, the AI must:

- Add DocBlocks to all public APIs and hooks.
- Use consistent tag ordering, versioning, and formatting.
- Avoid HTML in summaries and parameter descriptions.
- Use long descriptions for complex behaviour, examples, and notes.
