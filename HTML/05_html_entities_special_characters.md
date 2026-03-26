# HTML Entities - Special Characters and Symbols

## What are HTML Entities?

HTML entities are special codes used to display symbols and characters that:
- Cannot be typed directly on keyboard
- Have special meaning in HTML (like `<`, `>`, `&`)
- Are reserved characters in HTML
- Are special symbols (©, ®, ₹, etc.)

## Why Use HTML Entities?

When you want to display certain symbols or characters on a webpage, you cannot always type them directly. HTML entities provide a way to display these characters correctly in the browser.

---

## HTML Entity Structure

### Two Ways to Write Entities

#### 1. Entity Name (Named Entity)
```html
&entityname;
```

#### 2. Entity Number (Numeric Entity)
```html
&#number;
```

### Important Rules
- Always start with `&` (ampersand)
- End with `;` (semicolon)
- No spaces between characters

---

## Common HTML Entities

### Reserved Characters in HTML

These characters have special meaning in HTML, so we must use entities to display them.

| Character | Description | Entity Name | Entity Number | Display |
|-----------|-------------|-------------|---------------|---------|
| `<` | Less than | `&lt;` | `&#60;` | < |
| `>` | Greater than | `&gt;` | `&#62;` | > |
| `&` | Ampersand | `&amp;` | `&#38;` | & |
| `"` | Double quote | `&quot;` | `&#34;` | " |
| `'` | Single quote | `&apos;` | `&#39;` | ' |

#### Example: Displaying HTML Code
```html
<p>To create a paragraph, use &lt;p&gt; tag</p>
```

**Output:** To create a paragraph, use <p> tag

---

## Space Entities

### Non-Breaking Space

Regular spaces can collapse in HTML. Use non-breaking space to preserve spacing.

| Description | Entity Name | Entity Number |
|-------------|-------------|---------------|
| Non-breaking space | `&nbsp;` | `&#160;` |

#### Example: Multiple Spaces
```html
<!-- Regular spaces (will show as single space) -->
<p>Hello     World</p>

<!-- Non-breaking spaces (will preserve spacing) -->
<p>Hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;World</p>
```

**Output:**
- Hello World (regular)
- Hello     World (with &nbsp;)

---

## Copyright and Trademark Symbols

### Legal and Business Symbols

| Symbol | Description | Entity Name | Entity Number |
|--------|-------------|-------------|---------------|
| © | Copyright | `&copy;` | `&#169;` |
| ® | Registered trademark | `&reg;` | `&#174;` |
| ™ | Trademark | `&trade;` | `&#8482;` |

#### Example: Copyright Notice
```html
<p>&copy; 2024 Your Company. All rights reserved.</p>
<p>Brand Name&reg;</p>
<p>Product Name&trade;</p>
```

**Output:**
- © 2024 Your Company. All rights reserved.
- Brand Name®
- Product Name™

---

## Currency Symbols

### Common Currency Entities

| Symbol | Currency | Entity Name | Entity Number |
|--------|----------|-------------|---------------|
| ₹ | Indian Rupee | `&rupee;` | `&#8377;` |
| $ | Dollar | `&dollar;` | `&#36;` |
| € | Euro | `&euro;` | `&#8364;` |
| £ | Pound | `&pound;` | `&#163;` |
| ¥ | Yen | `&yen;` | `&#165;` |
| ¢ | Cent | `&cent;` | `&#162;` |

#### Example: Price Display
```html
<p>Price: &#8377;500</p>
<p>Price: &dollar;50</p>
<p>Price: &euro;45</p>
<p>Price: &pound;40</p>
```

**Output:**
- Price: ₹500
- Price: $50
- Price: €45
- Price: £40

---

## Mathematical Symbols

### Common Math Entities

| Symbol | Description | Entity Name | Entity Number |
|--------|-------------|-------------|---------------|
| + | Plus | `&plus;` | `&#43;` |
| − | Minus | `&minus;` | `&#8722;` |
| × | Multiplication | `&times;` | `&#215;` |
| ÷ | Division | `&divide;` | `&#247;` |
| = | Equals | `&equals;` | `&#61;` |
| ≠ | Not equal | `&ne;` | `&#8800;` |
| < | Less than | `&lt;` | `&#60;` |
| > | Greater than | `&gt;` | `&#62;` |
| ≤ | Less than or equal | `&le;` | `&#8804;` |
| ≥ | Greater than or equal | `&ge;` | `&#8805;` |
| ± | Plus-minus | `&plusmn;` | `&#177;` |
| ² | Superscript 2 | `&sup2;` | `&#178;` |
| ³ | Superscript 3 | `&sup3;` | `&#179;` |
| ½ | One half | `&frac12;` | `&#189;` |
| ¼ | One quarter | `&frac14;` | `&#188;` |
| ¾ | Three quarters | `&frac34;` | `&#190;` |

#### Example: Math Expressions
```html
<p>5 &times; 3 = 15</p>
<p>10 &divide; 2 = 5</p>
<p>x &ne; y</p>
<p>a &le; b</p>
<p>Area = length &times; width</p>
<p>Temperature: 25&deg;C &plusmn; 2&deg;</p>
```

**Output:**
- 5 × 3 = 15
- 10 ÷ 2 = 5
- x ≠ y
- a ≤ b
- Area = length × width
- Temperature: 25°C ± 2°

---

## Greek Letters

### Common Greek Letter Entities

| Symbol | Letter Name | Entity Name | Entity Number |
|--------|-------------|-------------|---------------|
| α | Alpha | `&alpha;` | `&#945;` |
| β | Beta | `&beta;` | `&#946;` |
| γ | Gamma | `&gamma;` | `&#947;` |
| δ | Delta | `&delta;` | `&#948;` |
| π | Pi | `&pi;` | `&#960;` |
| Σ | Sigma | `&Sigma;` | `&#931;` |
| Ω | Omega | `&Omega;` | `&#937;` |

#### Example: Scientific Notation
```html
<p>&alpha; particle</p>
<p>&beta; radiation</p>
<p>&pi; = 3.14159</p>
<p>&Sigma; (sum of values)</p>
```

---

## Arrow Symbols

### Directional Arrows

| Symbol | Description | Entity Name | Entity Number |
|--------|-------------|-------------|---------------|
| ← | Left arrow | `&larr;` | `&#8592;` |
| → | Right arrow | `&rarr;` | `&#8594;` |
| ↑ | Up arrow | `&uarr;` | `&#8593;` |
| ↓ | Down arrow | `&darr;` | `&#8595;` |
| ↔ | Left-right arrow | `&harr;` | `&#8596;` |

#### Example: Navigation
```html
<p>&larr; Previous</p>
<p>Next &rarr;</p>
<p>Scroll &uarr;</p>
<p>Download &darr;</p>
```

---

## Punctuation and Special Characters

### Common Punctuation Entities

| Symbol | Description | Entity Name | Entity Number |
|--------|-------------|-------------|---------------|
| " | Double quote | `&quot;` | `&#34;` |
| ' | Single quote | `&apos;` | `&#39;` |
| … | Ellipsis | `&hellip;` | `&#8230;` |
| – | En dash | `&ndash;` | `&#8211;` |
| — | Em dash | `&mdash;` | `&#8212;` |
| • | Bullet | `&bull;` | `&#8226;` |
| § | Section | `&sect;` | `&#167;` |
| ¶ | Paragraph | `&para;` | `&#182;` |

#### Example: Text Formatting
```html
<p>He said, &quot;Hello World&quot;</p>
<p>Loading&hellip;</p>
<p>Price range: &dollar;10 &ndash; &dollar;50</p>
<p>Main point &mdash; very important</p>
```

---

## Accented Characters

### Common Accented Letters

| Symbol | Description | Entity Name | Entity Number |
|--------|-------------|-------------|---------------|
| á | a with acute | `&aacute;` | `&#225;` |
| é | e with acute | `&eacute;` | `&#233;` |
| í | i with acute | `&iacute;` | `&#237;` |
| ó | o with acute | `&oacute;` | `&#243;` |
| ú | u with acute | `&uacute;` | `&#250;` |
| ñ | n with tilde | `&ntilde;` | `&#241;` |
| ü | u with umlaut | `&uuml;` | `&#252;` |

#### Example: Foreign Names
```html
<p>Caf&eacute;</p>
<p>Se&ntilde;or</p>
<p>Na&iuml;ve</p>
```

---

## Complete HTML Document Example

```html
<!DOCTYPE html>
<html>
<head>
    <title>HTML Entities Demo</title>
</head>
<body>
    <h1>HTML Entities Examples</h1>
    
    <!-- Copyright Notice -->
    <p>&copy; 2024 My Website. All Rights Reserved.</p>
    
    <!-- Price Information -->
    <h2>Product Pricing</h2>
    <p>Basic Plan: &#8377;500/month</p>
    <p>Pro Plan: &#8377;2000/month</p>
    
    <!-- Mathematical Expression -->
    <h2>Formula</h2>
    <p>Area of Circle = &pi; &times; r&sup2;</p>
    
    <!-- Code Display -->
    <h2>HTML Code Example</h2>
    <p>Use &lt;p&gt; tag for paragraphs</p>
    <p>Use &lt;h1&gt; for main heading</p>
    
    <!-- Special Spacing -->
    <h2>Spacing Example</h2>
    <p>Name:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;John Doe</p>
    <p>Age:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;25 years</p>
    
    <!-- Symbols -->
    <h2>Common Symbols</h2>
    <p>Registered Brand&reg;</p>
    <p>Trademark&trade;</p>
    <p>Temperature: 25&deg;C &plusmn; 2&deg;</p>
    
    <!-- Comparison -->
    <h2>Comparisons</h2>
    <p>5 &lt; 10</p>
    <p>20 &gt; 15</p>
    <p>x &ne; y</p>
    <p>a &le; b &le; c</p>
    
    <!-- Navigation -->
    <h2>Navigation</h2>
    <p>&larr; Go Back</p>
    <p>Continue &rarr;</p>
</body>
</html>
```

---

## Practical Use Cases

### 1. Displaying Code Snippets
```html
<p>To create a link: &lt;a href="url"&gt;Link Text&lt;/a&gt;</p>
```

### 2. Copyright Footer
```html
<footer>
    <p>&copy; 2024 Company Name. All rights reserved.</p>
</footer>
```

### 3. Price Lists
```html
<ul>
    <li>Product A: &#8377;1,000</li>
    <li>Product B: &#8377;2,500</li>
    <li>Product C: &#8377;5,000</li>
</ul>
```

### 4. Mathematical Content
```html
<p>Pythagorean Theorem: a&sup2; + b&sup2; = c&sup2;</p>
<p>Circle Area: A = &pi;r&sup2;</p>
```

### 5. Quotations
```html
<p>Einstein said, &quot;Imagination is more important than knowledge.&quot;</p>
```

---

## Best Practices

### 1. Use Entities for Reserved Characters
Always use entities for `<`, `>`, `&`, `"` when displaying them as text.

```html
<!-- Wrong -->
<p>Use <p> tag</p>

<!-- Correct -->
<p>Use &lt;p&gt; tag</p>
```

### 2. Consistent Spacing
Use `&nbsp;` for consistent spacing that won't collapse.

```html
<p>First Name:&nbsp;&nbsp;&nbsp;John</p>
<p>Last Name:&nbsp;&nbsp;&nbsp;&nbsp;Doe</p>
```

### 3. Proper Copyright Notices
Always use `&copy;` for copyright symbol.

```html
<p>&copy; 2024 Your Company</p>
```

### 4. Currency Display
Use proper currency entities for international content.

```html
<p>India: &#8377;500</p>
<p>USA: &dollar;50</p>
<p>Europe: &euro;45</p>
```

---

## Common Mistakes to Avoid

### 1. Forgetting Semicolon
```html
<!-- Wrong -->
<p>&copy 2024</p>

<!-- Correct -->
<p>&copy; 2024</p>
```

### 2. Using Spaces
```html
<!-- Wrong -->
<p>& copy ;</p>

<!-- Correct -->
<p>&copy;</p>
```

### 3. Not Escaping HTML Characters
```html
<!-- Wrong (will break HTML) -->
<p>if (x < 10 && y > 5)</p>

<!-- Correct -->
<p>if (x &lt; 10 &amp;&amp; y &gt; 5)</p>
```

---

## Quick Reference Table

### Most Used Entities

| Display | Entity Name | Entity Number | Use Case |
|---------|-------------|---------------|----------|
| < | `&lt;` | `&#60;` | Less than, code display |
| > | `&gt;` | `&#62;` | Greater than, code display |
| & | `&amp;` | `&#38;` | Ampersand |
| " | `&quot;` | `&#34;` | Quotation marks |
| © | `&copy;` | `&#169;` | Copyright |
| ® | `&reg;` | `&#174;` | Registered trademark |
| ₹ | `&rupee;` | `&#8377;` | Indian Rupee |
| × | `&times;` | `&#215;` | Multiplication |
| ÷ | `&divide;` | `&#247;` | Division |
|   | `&nbsp;` | `&#160;` | Non-breaking space |

---

## Practice Exercises

### Exercise 1: Copyright Footer
Create a footer with copyright symbol, year, and company name.

### Exercise 2: Price List
Create a product list with Indian Rupee symbols.

### Exercise 3: Code Display
Display HTML code examples using proper entities.

### Exercise 4: Mathematical Formula
Write mathematical expressions using proper symbols.

---

## Summary

- HTML entities display special characters and symbols
- Two formats: Entity name (`&name;`) and Entity number (`&#number;`)
- Always start with `&` and end with `;`
- Use entities for reserved HTML characters (`<`, `>`, `&`)
- Common uses: copyright symbols, currency, math symbols, special spacing
- Essential for displaying code snippets and special characters correctly

HTML entities ensure your content displays correctly across all browsers and devices!

---

*Next lesson: We'll learn about HTML forms and user input elements!*