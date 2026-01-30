# WordPress & OWASP Security Best Practices (Cheat Sheet)

## Source references (canonical)

- Sanitizing Data  
  https://developer.wordpress.org/apis/security/sanitizing/

- Data Validation  
  https://developer.wordpress.org/apis/security/data-validation/

- Escaping Output  
  https://developer.wordpress.org/apis/security/escaping/

- Nonces  
  https://developer.wordpress.org/apis/security/nonces/

- User Roles & Capabilities  
  https://developer.wordpress.org/apis/security/user-roles-and-capabilities/

- Common Vulnerabilities  
  https://developer.wordpress.org/apis/security/common-vulnerabilities/

- OWASP DOM-Based XSS Prevention  
  https://cheatsheetseries.owasp.org/cheatsheets/DOM_based_XSS_Prevention_Cheat_Sheet.html

---

## 1. Core Security Principles

- Never trust user input.
- Validate input early.
- Sanitize input when strict validation is not possible.
- Escape output as late as possible.
- Enforce authorization with roles and capabilities.
- Prefer WordPress core APIs over custom implementations.

---

## 2. Data Sanitization

**Purpose:**  
Remove or neutralize unsafe characters before storing or processing data.

**When to use:**  
- Free-form user input
- Data being stored in the database
- Data passing between systems

**Common functions:**

- `sanitize_text_field()`
- `sanitize_email()`
- `sanitize_textarea_field()`
- `sanitize_key()`
- `esc_url_raw()`

**Example:**

```php
$title = sanitize_text_field( $_POST['title'] );
```

---

## 3. Data Validation

**Purpose:**  
Ensure data matches strict expectations before use.

**Recommended approaches:**

- Safelisting (preferred)
- Type checking
- Format enforcement (regex, enums)

**Example:**

```php
if ( ! in_array( $status, array( 'draft', 'publish' ), true ) ) {
    return;
}
```

**Rule:**  
Validate before sanitizing when possible.

---

## 4. Escaping Output

**Purpose:**  
Prevent XSS by encoding output for its rendering context.

**Escape at render time, not on storage.**

**Context-specific functions:**

- HTML text: `esc_html()`
- HTML attributes: `esc_attr()`
- URLs: `esc_url()`
- JavaScript: `esc_js()`
- Textareas: `esc_textarea()`

**Example:**

```php
echo esc_html( $post_title );
```

---

## 5. Nonces (CSRF Protection)

**Purpose:**  
Protect state-changing actions from Cross-Site Request Forgery.

**Key points:**

- Nonces are time-based, not truly single-use.
- Nonces do NOT replace capability checks.

**Workflow:**

1. Generate nonce:
```php
wp_nonce_field( 'save_settings', 'settings_nonce' );
```

2. Verify nonce:
```php
check_admin_referer( 'save_settings', 'settings_nonce' );
```

---

## 6. User Roles & Capabilities

**Roles:**  
Groups of capabilities (Subscriber, Author, Editor, Administrator).

**Capabilities:**  
Atomic permissions (e.g. `edit_posts`, `manage_options`).

**Best practice:**  
Always check capabilities, never roles.

**Example:**

```php
if ( current_user_can( 'manage_options' ) ) {
    // Allowed action
}
```

---

## 7. Common WordPress Vulnerabilities

### SQL Injection
- Caused by unprepared SQL queries.
- Use `$wpdb->prepare()` or core APIs.

### Cross-Site Scripting (XSS)
- Caused by unescaped output.
- Always escape for context.

### Cross-Site Request Forgery (CSRF)
- Caused by missing nonce checks.
- Always verify nonces on POST/GET actions.

### Privilege Escalation
- Caused by missing capability checks.
- Always verify permissions.

---

## 8. OWASP DOM-Based XSS Prevention

**Definition:**  
DOM-based XSS occurs when untrusted data reaches unsafe DOM sinks.

### Avoid unsafe sinks

- `innerHTML`
- `outerHTML`
- `document.write()`

### Prefer safe APIs

- `textContent`
- `createElement()`
- `setAttribute()` (with validated input)

### Example (safe)

```js
element.textContent = userInput;
```

---

## 9. Security Checklist

- [ ] Validate all input
- [ ] Sanitize untrusted data
- [ ] Escape all output
- [ ] Verify nonces on actions
- [ ] Check capabilities
- [ ] Avoid unsafe DOM APIs
- [ ] Use WordPress core security APIs

---
