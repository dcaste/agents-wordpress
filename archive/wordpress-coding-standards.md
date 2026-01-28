# WordPress Coding Standards (Cheat Sheet)

Source references (canonical):
- Accessibility: https://developer.wordpress.org/coding-standards/ :contentReference[oaicite:0]{index=0}standards/accessibility/ 
- CSS: https://developer.wordpress.org/coding- :contentReference[oaicite:2]{index=2}tandards/css/ 
- HTML: https://developer.wordpress.org/coding-s :contentReference[oaicite:4]{index=4}andards/html/ 
- JavaScript: https://developer.wordpress.org/coding-standar :contentReference[oaicite:6]{index=6}s/javascript/ 
- PHP: https://developer.wordpress.org/coding- :contentReference[oaicite:8]{index=8}ss-coding-standards/php/ 
- JS inline docs (JSDoc): https://developer.wordpress.org/coding-standards/i :contentReference[oaicite:10]{index=10}s/javascript/ 
- PHP inline docs (PHPDoc): https://developer.wordpress.org/coding-stan :contentReference[oaicite:12]{index=12}tandards/php/ 
- Markdown style guide (for documentation): https://developer.w :contentReference[oaicite:14]{index=14}ng-standards/styleguide/ 

---

## Global principles

- Consistency: code in a project should loo:contentReference[oaicite:16]{index=16}ingle person. 
- Prefer readability and maintainability over cleverness and “wh:contentReference[oaicite:18]{index=18}legacy files. 
- Use tooling where pos:contentReference[oaicite:20]{index=20}HP_CodeSniffer for PHP). 

---

## Accessibility (A11y)

### Target conformance

- WordPress targets WCAG 2.2 **Level A** and **Leve:contentReference[oaicite:22]{index=22}couraged where relevant. 

### WCAG principles to keep in mind (POUR)

- :contentReference[oaicite:24]{index=24}alternatives)   
-:contentReference[oaicite:26]{index=26}d accessible)   
- **Understandabl:contentReference[oaicite:28]{index=28}eadable text)   
- **Robust:contentReference[oaicite:30]{index=30}sistive tech)   

### Practical checklist (use alongside WCAG criteria)

- Provide text alternatives f:contentReference[oaicite:32]{index=32}nt (images/icons/media). 
- Ensure all fu:contentReference[oaicite:34]{index=34}ailable from a keyboard. 
- Provide cle:contentReference[oaicite:36]{index=36} ways to locate content. 
- Provide input assi:contentReference[oaicite:38]{index=38}recovery where relevant. 
- Validate with automated + human test:contentReference[oaicite:40]{index=40}sting remains important. 

---

## HTML

### Validation

- Validate pages with the W3C validator to catch machine-detectable mark:contentReference[oaicite:42]{index=42}replacement for review). 

### Self-closing tags

- Use exactly one space before the self-closin:contentReference[oaicite:44]{index=44}`<br />`  
  - ❌ `<br/>` 

### Attributes and quoting

:contentReference[oaicite:46]{index=46}attributes in lowercase. 
- Quote :contentReference[oaicite:48]{index=48} avoid security issues). 
- Boolean attributes: omit t:contentReference[oaicite:50]{index=50}use `"true"`/`"false"`).   
  - ✅ `<input disabled />`  
  - ❌ `<input disabled="true" />`

### Indentation

- Indent to reflect log:contentReference[oaicite:52]{index=52}se **tabs**, not spaces. 
- When mixing PHP and HTML, indent PHP blocks to match surrounding HTML; c:contentReference[oaicite:54]{index=54} align with opening PHP. 

---

## CSS

### Structure

- Use **tab:contentReference[oaicite:56]{index=56}to indent each property. 
- Add **two blank lines** between sections; **one blan:contentReference[oaicite:58]{index=58}blocks within a section. 
- Each selector on its own line, ending in `,` or `{`. Each property/value on its own line with one tab indentation and a tr:contentReference[oaicite:60]{index=60} closing `}` flush left. 

### Selectors

- Prefer lowercase; separate words with **hyphens**; avoid came:contentReference[oaicite:62]{index=62}ores for selector names. 
- Use human-readable:contentReference[oaicite:64]{index=64}escribe what they style. 
- Attribute selector values should use:contentReference[oaicite:66]{index=66}*: `input[type="text"]`. 
- Avoid over-qualified selector:contentReference[oaicite:68]{index=68}tainer` → `.container`). 

### Properties

:contentReference[oaicite:70]{index=70}value;` (colon + space). 
- Lowercase property/value names (except fo:contentReference[oaicite:72]{index=72}or-specific properties). 
- Prefer hex colors (`#fff`) or `rgba()` for opaci:contentReference[oaicite:74]{index=74}se and avoid RGB format. 
- Use shorthand where possible (background/border/font/list:contentReference[oaicite:76]{index=76}ding) unless overriding. 

### Property ordering

- Use a consistent system (example shows TRBL order for related properties), or alphabeti:contentReference[oaicite:78]{index=78}h are shown as options). 

### Vendor prefixes

- WordPress uses Autoprefixer; if writing prefixes manually, order longe:contentReference[oaicite:80]{index=80}o shortest (unprefixed). 

### Values

- No spaces padding parentheses: `rgba(:contentReference[oaicite:82]{index=82}pace after commas only). :contentReference[oaicite:84]{index=84}ations with a semicolon. 
- Prefer double quotes when quoting is need:contentReference[oaicite:86]{index=86}ent` values). 
- Prefer n:contentReference[oaicite:88]{index=88}400`, `700`). 
- Avoid units on zero values (except when:contentReference[oaicite:90]{index=90} properties). 

### Media queries

- Generally group media queries at the bottom of the styleshee:contentReference[oaicite:92]{index=92}s an exception in core). 
- I:contentReference[oaicite:94]{index=94} rule sets one level in. 

---

## JavaScript

### General

- WordPress JS standards are adapted from the jQuery style guide, with differences such as sin:contentReference[oaicite:96]{index=96}espace rules. 
- Avoid “w:contentReference[oaicite:98]{index=98}efactors in older files. 

### Spacing & whitespace rul:contentReference[oaicite:100]{index=100}
- Indent with **tabs**. 
- No trailing :contentReference[oaicite:102]{index=102}itespace on blank lines. 
- Line length: usually ≤ 80; should:contentReference[oaicite:104]{index=104}tabs count as 4 spaces). 
- Always use braces for `if/else/for/w:contentReference[oaicite:106]{index=106}ways use multiple lines. 
- No space before `,` or `;`; :contentReference[oaicite:108]{index=108}ting `;` at end of line. 
- Terna:contentReference[oaicite:110]{index=110}ve spaces on both sides. 
- No filler spaces:contentReference[oaicite:112]{index=112}cts: `{}`, `[]`, `fn()`. :contentReference[oaicite:114]{index=114} Newline at end of file. 
- `!` negation operator should hav:contentReference[oaicite:116]{index=116}ce (WordPress-specific). 

### Indentation & line breaks

- Use one extra tab indentatio:contentReference[oaicite:118]{index=118} a file wrapper/closure. 
- For long statements, break after:contentReference[oaicite:120]{index=120}logical groups together. 
- For long conditionals: each operand of a logical operator should appear on its own line and be indented relative to the parentheses (per the J:contentReference[oaicite:122]{index=122}ne statements guidance). 

### Semicolo:contentReference[oaicite:124]{index=124}ons; do not rely on ASI. 

---

## PHP

### General

- Standards apply broadly across the WP ecosystem (core/themes/plugins), including best practices for interop:contentReference[oaicite:126]{index=126}and security. 
- Use WPCS tooling :contentReference[oaicite:128]{index=128}er for automated checks. 

### PHP tags

- Multi-line PHP snippets in HTML: op:contentReference[oaicite:130]{index=130}t be on their own lines. 
- :contentReference[oaicite:132]{index=132}nd tags (`<?` or `<?=`). 

### Quotes

- Use single quotes for literal strings; alternate q:contentReference[oaicite:134]{index=134}tead of escaping quotes. 
- Escape text going into HTML/XML attributes to :contentReference[oaicite:136]{index=136}kup and security issues. 

### require/include

- Do not wrap paths in parentheses; use ex:contentReference[oaicite:138]{index=138}etween keyword and path. 
- Prefer `require[_once]:contentReference[oaicite:140]{index=140}al includes (fail fast). 

### Naming

- Variables, functions, hooks: lowercase + underscores; avoid ca:contentReference[oaicite:142]{index=142}necessary abbreviations. 
- Classes/traits/interfaces/enums: capitalized words sep:contentReference[oaicite:144]{index=144}ores; acronyms all caps. :contentReference[oaicite:146]{index=146}ercase with underscores. 
- Files: lowercase with hyphens. Class file names: prefix `class-`, replace underscores with hyphens (:contentReference[oaicite:148]{index=148}→ `class-wp-error.php`). 
- Dynamic hooks: prefer interpolation over concatenation, e.g. `do_action( "{:contentReference[oaicite:150]{index=150}st->post_type}", ... )`. 

### Whitespace & indentation

- Space after commas and around logical/arithmeti:contentReference[oaicite:152]{index=152}ng/assignment operators. 
- Spaces inside control-structure parentheses: `if :contentReference[oaicite:154]{index=154}oreach ( $a as $b ) {}`. 
- Array index spacing: no spaces for literal keys/indic:contentReference[oaicite:156]{index=156}hen index is a variable. 
- Indent with **tabs**; use:contentReference[oaicite:158]{index=158}alignment within a line. 
- Associative arrays with more than one item: one i:contentReference[oaicite:160]{index=160}iling comma recommended. 
- Remove trailing spaces; omitting the :contentReference[oaicite:162]{index=162}nd of file is preferred. 

### Braces

- Use braces for :contentReference[oaicite:164]{index=164}w the shown brace style. 

---

## Inline documentation standards

### JavaScript (JSDoc 3)

- Word:contentReference[oaicite:166]{index=166}oc 3 for inline JS docs. 
- Document: functions/methods, objects, closures, object pr:contentReference[oaicite:168]{index=168}s, events, file headers. 
- `@since`: use a 3-digit version for initial introduction; add additional `@since` tags f:contentReference[oaicite:170]{index=170}gelog style). 
- Inline comments:
  - Single line: `// Comment.`
  - Multi-line: use `/*:contentReference[oaicite:172]{index=172}not** begin with `/**`). 

### PHP (PHPDoc-like, customized for WP)

- WordPress uses a customized s:contentReference[oaicite:174]{index=174} PHPDoc (phpDocumentor). 
- Document: functions/methods, classes, class members, requires/includes, hooks, :contentReference[oaicite:176]{index=176}file headers, constants. 
- DocBlocks should directly precede what they docu:contentReference[oaicite:178]{index=178}d tags/code in between). 
- Summary: no HTML/Markdown; use plain t:contentReference[oaicite:180]{index=180}g element” not `<img>`). 
- Use multiple `@since` tags for significant changes a:contentReference[oaicite:182]{index=182}t description per entry. 
- Wrap DocBlock text after ~80 characters (with allowances for i:contentReference[oaicite:184]{index=184}d overly wide DocBlocks. 

---

## Documentation Markdown style

Use WordPress’ Markdown conventions when writing project docs/readmes.

- Headings: `#` through `######`; note that h1–h4 appear:contentReference[oaicite:186]{index=186}e of Contents on DevHub. 
- Emphasis:
  - Italic: `_text_`
  - Bold:​:contentReference[oaicite:188]{index=188}trikethrough: `~~text~~` 
- Lists:
  - Unordered: `:contentReference[oaicite:190]{index=190} indented by two spaces):contentReference[oaicite:191]{index=191}
  - Ordered: `1. item` 
- Code examples: fenced code bloc:contentReference[oaicite:194]{index=194}specifier when possible. 

---

## Appendix: “do this by default” checklist

- **T:contentReference[oaicite:196]{index=196}
- Avoid trail:contentReference[oaicite:198]{index=198}th a newline. 
:contentReference[oaicite:200]{index=200}idate markup. 
- Prefer readability over refactors th:contentReference[oaicite:202]{index=202}rmatting in legacy code. :contentReference[oaicite:203]{index=203}