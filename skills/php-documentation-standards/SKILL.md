---
name: php-documentation-standards
description: Guidelines for writing PHPDoc documentation following WordPress standards. Use when documenting PHP code, including functions, classes, methods, properties, hooks, and inline comments with proper formatting and tag usage.
---

# PHP Documentation Standards

Guidelines distilled from WordPress PHP documentation standards.

## DocBlock Scope

Use PHPDoc comments for:

- **Functions and methods**: All public functions and methods
- **Classes, interfaces, and traits**: Class definitions
- **Properties and constants**: Class properties and constants
- **Hooks**: WordPress actions and filters (`do_action`, `apply_filters`)
- **Global variables**: Notable global variables
- **File includes**: `include`, `require` statements when relevant
- **File headers**: Non-trivial file headers with purpose and context

## Voice & Content

- **Summary**: Write as single-sentence, third-person singular statements
  - Correct: "Retrieves the user's email address."
  - Incorrect: "Retrieve the user's email address."
  - Incorrect: "This function retrieves the user's email address."
- **No HTML/Markdown in summaries**: Keep summaries as plain text
- **Long descriptions**: Optional; may use Markdown and examples for complex behavior
- **Be concise**: Focus on what the code does and why it matters

## Placement & Formatting

- **Direct placement**: Place DocBlocks directly above the element they document
- **No code between**: Don't put code between the DocBlock and the element
- **Line wrapping**: Wrap lines at approximately 80 characters
- **Consistent spacing**: Use consistent spacing between tags

## Baseline Structure

```php
/**
 * Summary sentence.
 *
 * Optional longer description with more details.
 *
 * @since x.x.x
 *
 * @param type $var Description.
 * @param type $var Description.
 * @return type Description.
 */
```

## Common Tags

### @since

- **Required**: Include `@since x.x.x` for all documented elements
- **Version format**: Use semantic versioning (e.g., `1.0.0`, `2.1.3`)
- **Unknown version**: Use `@since Unknown` if version is not known
- **Changelog**: Add new `@since` lines for behavioral changes
  ```php
  /**
   * Retrieves user data.
   *
   * @since 1.0.0
   * @since 2.0.0 Added $include_meta parameter.
   *
   * @param int  $user_id      User ID.
   * @param bool $include_meta Whether to include metadata.
   * @return array User data.
   */
  ```

### @param

- **Format**: `@param type $variable Description.`
- **Type**: Specify the parameter type (string, int, bool, array, object, mixed, etc.)
- **Variable name**: Include the `$` prefix
- **Description**: Brief description ending with a period
- **Multiple types**: Use pipe separator: `string|int`
- **Arrays**: Be specific when possible: `array`, `int[]`, `string[]`

**Example**:
```php
/**
 * Updates user profile.
 *
 * @since 1.0.0
 *
 * @param int    $user_id User ID.
 * @param array  $data    User data to update.
 * @param bool   $notify  Whether to send notification. Default false.
 * @return bool True on success, false on failure.
 */
```

### @return

- **Format**: `@return type Description.`
- **Omit if void**: Don't include `@return` for functions that don't return a value
- **Be specific**: Describe what is returned, not just the type
- **Multiple types**: Use pipe separator for multiple possible return types

### @deprecated

- **Format**: `@deprecated version Use alternative().`
- **Include replacement**: Always suggest the replacement function/method
- **Keep other tags**: Maintain `@param` and `@return` tags for deprecated items
- **Optional @see**: Add `@see` tag to reference the replacement

**Example**:
```php
/**
 * Retrieves user email.
 *
 * @since 1.0.0
 * @deprecated 2.0.0 Use get_user_email() instead.
 *
 * @param int $user_id User ID.
 * @return string User email address.
 */
```

## Documenting Hooks

WordPress actions and filters should be documented:

```php
/**
 * Fires after user login.
 *
 * @since 1.0.0
 *
 * @param int    $user_id User ID.
 * @param object $user    User object.
 */
do_action( 'after_user_login', $user_id, $user );

/**
 * Filters the user display name.
 *
 * @since 1.0.0
 *
 * @param string $display_name User display name.
 * @param int    $user_id      User ID.
 * @return string Filtered display name.
 */
$display_name = apply_filters( 'user_display_name', $display_name, $user_id );
```

## Inline Comments

- **Single-line**: Use `//` for brief inline comments
- **Multi-line**: Use `/* ... */` (single asterisk) for longer inline notes
- **Proximity**: Keep comments close to the relevant code
- **Purpose**: Explain why, not what (the code shows what)

**Example**:
```php
// Prevent duplicate submissions
if ( isset( $submitted_ids[ $id ] ) ) {
    continue;
}

/* 
 * We need to flush the cache here because the data
 * may have been modified by an external process.
 */
wp_cache_flush();
```

## Class Documentation

```php
/**
 * User authentication handler.
 *
 * Manages user login, logout, and session validation.
 *
 * @since 1.0.0
 */
class User_Auth {
    
    /**
     * Maximum login attempts.
     *
     * @since 1.0.0
     * @var int
     */
    const MAX_ATTEMPTS = 5;
    
    /**
     * Current user ID.
     *
     * @since 1.0.0
     * @var int
     */
    private $user_id;
}
```

## AI Requirements

When documenting PHP code, you must:

- Add consistent PHPDoc to all public APIs and hooks
- Use clean tag order: summary, description, `@since`, `@param`, `@return`
- Write summaries in third-person singular
- Avoid HTML in summaries, `@param`, and `@return` text
- Use long descriptions for complex behavior or examples
- Include `@since` tag for all documented elements
- Properly format `@param` with type, variable name, and description
- Include `@return` for functions that return values
- Document all WordPress hooks with their parameters
- Use inline comments to explain non-obvious logic
- Keep formatting consistent with approximately 80-character line wrapping
