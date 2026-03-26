# CSS Day 2: Complete Guide to CSS Selectors

## What are CSS Selectors?

Selectors are patterns used to select and style specific HTML elements. They tell CSS which elements to apply styles to.

### Basic Concept

```css
selector {
    property: value;
}
```

**Selector** = Which element to style
**Property** = What to change
**Value** = How to change it

---

# Part 1: Simple Selectors

Simple selectors target elements based on their name, ID, or class.

## 1. Element Selector (Tag Selector)

Selects all elements of a specific type.

### Syntax

```css
tagname {
    property: value;
}
```

### Examples

```css
/* Style all paragraphs */
p {
    color: blue;
    font-size: 16px;
}

/* Style all headings */
h1 {
    color: red;
    text-align: center;
}

/* Style all links */
a {
    color: green;
    text-decoration: none;
}
```

### Complete Example

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        h1 {
            color: navy;
            text-align: center;
        }
        
        p {
            color: gray;
            font-size: 18px;
        }
        
        a {
            color: blue;
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <h1>Welcome</h1>
    <p>This is a paragraph.</p>
    <p>This is another paragraph.</p>
    <a href="#">Click here</a>
</body>
</html>
```

**Result:** All h1, p, and a elements get styled

---

## 2. ID Selector

Selects a single element with a specific ID. IDs must be unique on a page.

### Syntax

```css
#idname {
    property: value;
}
```

### Examples

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        #header {
            background-color: navy;
            color: white;
            padding: 20px;
        }
        
        #main-content {
            width: 80%;
            margin: 0 auto;
        }
        
        #footer {
            background-color: gray;
            text-align: center;
            padding: 10px;
        }
    </style>
</head>
<body>
    <div id="header">
        <h1>My Website</h1>
    </div>
    
    <div id="main-content">
        <p>Main content goes here.</p>
    </div>
    
    <div id="footer">
        <p>&copy; 2024</p>
    </div>
</body>
</html>
```

**Important:** Each ID can only be used once per page!

---

## 3. Class Selector

Selects all elements with a specific class. Classes can be reused multiple times.

### Syntax

```css
.classname {
    property: value;
}
```

### Examples

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .highlight {
            background-color: yellow;
            padding: 5px;
        }
        
        .important {
            color: red;
            font-weight: bold;
        }
        
        .box {
            border: 2px solid black;
            padding: 20px;
            margin: 10px;
        }
    </style>
</head>
<body>
    <p class="highlight">This text is highlighted.</p>
    <p class="important">This is important text.</p>
    <p class="highlight important">This has both classes.</p>
    
    <div class="box">
        <p>Content inside a box.</p>
    </div>
    
    <div class="box">
        <p>Another box with same style.</p>
    </div>
</body>
</html>
```

**Multiple Classes:** Separate with space
```html
<p class="highlight important">Text</p>
```

---

## 4. Universal Selector

Selects all elements on the page.

### Syntax

```css
* {
    property: value;
}
```

### Example

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

**Use case:** Reset default browser styles

---

## 5. Grouping Selector

Applies same styles to multiple selectors.

### Syntax

```css
selector1, selector2, selector3 {
    property: value;
}
```

### Example

```css
h1, h2, h3 {
    color: navy;
    font-family: Arial, sans-serif;
}

p, li, span {
    color: gray;
    line-height: 1.6;
}
```

---

# Part 2: Combinator Selectors

Combinator selectors target elements based on their relationship with other elements.

## 1. Descendant Selector (Space)

Selects all elements inside another element (at any level).

### Syntax

```css
parent descendant {
    property: value;
}
```

### Examples

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        /* All paragraphs inside div */
        div p {
            color: blue;
        }
        
        /* All links inside nav */
        nav a {
            color: white;
            text-decoration: none;
        }
    </style>
</head>
<body>
    <div>
        <p>This paragraph is blue.</p>
        <section>
            <p>This is also blue (nested deeper).</p>
        </section>
    </div>
    
    <p>This paragraph is NOT blue (outside div).</p>
    
    <nav>
        <a href="#">Link 1</a>
        <a href="#">Link 2</a>
    </nav>
</body>
</html>
```

---

## 2. Child Selector (>)

Selects direct children only (not grandchildren).

### Syntax

```css
parent > child {
    property: value;
}
```

### Example

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        /* Only direct children */
        div > p {
            color: red;
        }
    </style>
</head>
<body>
    <div>
        <p>This is RED (direct child).</p>
        <section>
            <p>This is NOT red (grandchild).</p>
        </section>
    </div>
</body>
</html>
```

---

## 3. Adjacent Sibling Selector (+)

Selects the element immediately after another element (same parent).

### Syntax

```css
element1 + element2 {
    property: value;
}
```

### Example

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        /* Paragraph immediately after h2 */
        h2 + p {
            color: green;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <h2>Heading</h2>
    <p>This is GREEN (immediately after h2).</p>
    <p>This is normal (not immediately after h2).</p>
    
    <h2>Another Heading</h2>
    <p>This is also GREEN.</p>
</body>
</html>
```

---

## 4. General Sibling Selector (~)

Selects all siblings after an element (same parent).

### Syntax

```css
element1 ~ element2 {
    property: value;
}
```

### Example

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        /* All paragraphs after h2 */
        h2 ~ p {
            color: purple;
        }
    </style>
</head>
<body>
    <p>This is normal (before h2).</p>
    <h2>Heading</h2>
    <p>This is PURPLE (after h2).</p>
    <p>This is also PURPLE (after h2).</p>
    <p>All these are PURPLE (after h2).</p>
</body>
</html>
```

---

# Part 3: Pseudo-Class Selectors

Pseudo-classes select elements based on their state or position.

## Common Pseudo-Classes

### 1. :hover

Applies when mouse hovers over element.

```css
a:hover {
    color: red;
    text-decoration: underline;
}

button:hover {
    background-color: blue;
    cursor: pointer;
}
```

### 2. :active

Applies when element is being clicked.

```css
button:active {
    background-color: darkblue;
}
```

### 3. :focus

Applies when element has focus (input fields).

```css
input:focus {
    border: 2px solid blue;
    outline: none;
}
```

### 4. :visited

Applies to visited links.

```css
a:visited {
    color: purple;
}
```

### 5. :link

Applies to unvisited links.

```css
a:link {
    color: blue;
}
```

---

## Position-Based Pseudo-Classes

### :first-child

Selects first child of parent.

```css
p:first-child {
    font-weight: bold;
}
```

### :last-child

Selects last child of parent.

```css
p:last-child {
    color: red;
}
```

### :nth-child(n)

Selects specific child by number.

```css
/* Second child */
li:nth-child(2) {
    color: blue;
}

/* Even children */
li:nth-child(even) {
    background-color: lightgray;
}

/* Odd children */
li:nth-child(odd) {
    background-color: white;
}

/* Every 3rd child */
li:nth-child(3n) {
    color: red;
}
```

### Complete Example

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        /* Link states */
        a:link {
            color: blue;
        }
        
        a:visited {
            color: purple;
        }
        
        a:hover {
            color: red;
            text-decoration: none;
        }
        
        a:active {
            color: orange;
        }
        
        /* Button hover */
        button:hover {
            background-color: green;
            color: white;
            cursor: pointer;
        }
        
        /* Input focus */
        input:focus {
            border: 2px solid blue;
            background-color: lightyellow;
        }
        
        /* List styling */
        li:first-child {
            font-weight: bold;
        }
        
        li:last-child {
            color: red;
        }
        
        li:nth-child(even) {
            background-color: #f0f0f0;
        }
    </style>
</head>
<body>
    <a href="https://www.google.com">Visit Google</a>
    <br><br>
    
    <button>Hover Over Me</button>
    <br><br>
    
    <input type="text" placeholder="Click to focus">
    <br><br>
    
    <ul>
        <li>First item (bold)</li>
        <li>Second item (gray background)</li>
        <li>Third item</li>
        <li>Fourth item (gray background)</li>
        <li>Last item (red)</li>
    </ul>
</body>
</html>
```

---

# Part 4: Pseudo-Element Selectors

Pseudo-elements style specific parts of an element.

## Syntax

```css
selector::pseudo-element {
    property: value;
}
```

**Note:** Use double colon (::) for pseudo-elements

---

## 1. ::first-letter

Styles the first letter of text.

### Example

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        p::first-letter {
            font-size: 40px;
            color: red;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <p>This paragraph has a large first letter. This is commonly used in magazines and books.</p>
</body>
</html>
```

**Result:** "T" is large and red

---

## 2. ::first-line

Styles the first line of text.

### Example

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        p::first-line {
            color: blue;
            font-weight: bold;
            text-transform: uppercase;
        }
    </style>
</head>
<body>
    <p>This is the first line and it will be blue and bold. The rest of the paragraph will have normal styling. This continues on multiple lines.</p>
</body>
</html>
```

---

## 3. ::before

Inserts content before an element.

### Syntax

```css
selector::before {
    content: "text or symbol";
    /* other styles */
}
```

### Examples

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        h2::before {
            content: "📌 ";
            color: red;
        }
        
        .important::before {
            content: "⚠️ Important: ";
            font-weight: bold;
            color: red;
        }
        
        a::before {
            content: "🔗 ";
        }
    </style>
</head>
<body>
    <h2>Section Title</h2>
    <p class="important">Read this carefully!</p>
    <a href="#">Click here</a>
</body>
</html>
```

---

## 4. ::after

Inserts content after an element.

### Examples

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        h2::after {
            content: " ✓";
            color: green;
        }
        
        .required::after {
            content: " *";
            color: red;
        }
        
        a::after {
            content: " →";
            color: blue;
        }
    </style>
</head>
<body>
    <h2>Completed Task</h2>
    <label class="required">Name</label>
    <a href="#">Read More</a>
</body>
</html>
```

---

## 5. ::selection

Styles text when user selects/highlights it.

### Example

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        ::selection {
            background-color: yellow;
            color: black;
        }
        
        p::selection {
            background-color: lightblue;
            color: white;
        }
    </style>
</head>
<body>
    <h1>Try selecting this text</h1>
    <p>Select this paragraph to see different colors.</p>
</body>
</html>
```

**Try it:** Select text with mouse to see the effect!

---

## Complete Pseudo-Element Example

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        /* First letter styling */
        .article::first-letter {
            font-size: 50px;
            color: #c00;
            float: left;
            line-height: 1;
            margin-right: 5px;
        }
        
        /* First line styling */
        .article::first-line {
            font-weight: bold;
            color: #333;
        }
        
        /* Add icon before headings */
        h2::before {
            content: "📖 ";
        }
        
        /* Add decorative line after headings */
        h2::after {
            content: "";
            display: block;
            width: 50px;
            height: 3px;
            background-color: #4CAF50;
            margin-top: 5px;
        }
        
        /* Custom text selection */
        ::selection {
            background-color: #4CAF50;
            color: white;
        }
        
        /* Required field indicator */
        .required::after {
            content: " *";
            color: red;
        }
    </style>
</head>
<body>
    <h2>Article Title</h2>
    
    <p class="article">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
        This is the first line of the article. The first letter is 
        styled differently. Select any text to see custom selection colors.
    </p>
    
    <form>
        <label class="required">Email</label><br>
        <input type="email">
    </form>
</body>
</html>
```

---

# Part 5: Attribute Selectors

Attribute selectors target elements based on their attributes or attribute values.

## 1. [attribute]

Selects elements with a specific attribute.

### Example

```css
/* All elements with title attribute */
[title] {
    color: blue;
    cursor: help;
}

/* All inputs with required attribute */
input[required] {
    border: 2px solid red;
}
```

```html
<p title="This is a tooltip">Hover over me</p>
<input type="text" required>
```

---

## 2. [attribute="value"]

Selects elements with exact attribute value.

### Example

```css
/* Only text inputs */
input[type="text"] {
    background-color: lightyellow;
}

/* Only email inputs */
input[type="email"] {
    background-color: lightblue;
}

/* Only password inputs */
input[type="password"] {
    background-color: lightpink;
}
```

```html
<input type="text" placeholder="Text">
<input type="email" placeholder="Email">
<input type="password" placeholder="Password">
```

---

## 3. [attribute^="value"]

Selects elements where attribute starts with specific value.

### Example

```css
/* Links starting with https */
a[href^="https"] {
    color: green;
}

/* Links starting with http (not secure) */
a[href^="http://"] {
    color: red;
}

/* Classes starting with "btn" */
[class^="btn"] {
    padding: 10px 20px;
    border-radius: 5px;
}
```

```html
<a href="https://secure-site.com">Secure Link</a>
<a href="http://old-site.com">Old Link</a>
<button class="btn-primary">Button</button>
<button class="btn-secondary">Button</button>
```

---

## 4. [attribute$="value"]

Selects elements where attribute ends with specific value.

### Example

```css
/* Links ending with .pdf */
a[href$=".pdf"] {
    color: red;
}

a[href$=".pdf"]::after {
    content: " 📄";
}

/* Links ending with .zip */
a[href$=".zip"]::after {
    content: " 📦";
}

/* Images ending with .png */
img[src$=".png"] {
    border: 2px solid blue;
}
```

```html
<a href="document.pdf">Download PDF</a>
<a href="files.zip">Download ZIP</a>
<img src="logo.png" alt="Logo">
```

---

## 5. [attribute*="value"]

Selects elements where attribute contains specific value anywhere.

### Example

```css
/* Links containing "google" */
a[href*="google"] {
    color: #4285f4;
}

/* Paragraphs with title containing "important" */
p[title*="important"] {
    background-color: yellow;
    font-weight: bold;
}

/* Classes containing "alert" */
[class*="alert"] {
    padding: 15px;
    border-radius: 5px;
}
```

```html
<a href="https://www.google.com">Google</a>
<p title="This is important information">Important text</p>
<div class="alert-warning">Warning message</div>
<div class="alert-danger">Danger message</div>
```

---

## 6. [attribute~="value"]

Selects elements where attribute contains specific word (space-separated).

### Example

```css
/* Title containing word "tutorial" */
[title~="tutorial"] {
    color: blue;
}
```

```html
<p title="CSS tutorial guide">This matches</p>
<p title="tutorial">This also matches</p>
<p title="tutorials">This does NOT match (plural)</p>
```

---

## 7. [attribute|="value"]

Selects elements where attribute starts with value followed by hyphen.

### Example

```css
/* Language codes */
[lang|="en"] {
    color: blue;
}
```

```html
<p lang="en">English</p>
<p lang="en-US">American English (matches)</p>
<p lang="en-GB">British English (matches)</p>
<p lang="fr">French (doesn't match)</p>
```

---

## Complete Attribute Selector Example

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        /* All inputs with placeholder */
        input[placeholder] {
            border: 1px solid #ccc;
            padding: 8px;
        }
        
        /* Text inputs */
        input[type="text"] {
            background-color: #fff9e6;
        }
        
        /* Email inputs */
        input[type="email"] {
            background-color: #e6f3ff;
        }
        
        /* Required inputs */
        input[required] {
            border-left: 3px solid red;
        }
        
        /* Links to PDFs */
        a[href$=".pdf"]::after {
            content: " 📄 PDF";
            color: red;
            font-size: 12px;
        }
        
        /* External links (starting with http) */
        a[href^="http"]::before {
            content: "🔗 ";
        }
        
        /* Links containing "google" */
        a[href*="google"] {
            color: #4285f4;
            font-weight: bold;
        }
        
        /* Elements with title attribute */
        [title] {
            cursor: help;
            border-bottom: 1px dotted #999;
        }
    </style>
</head>
<body>
    <h2>Form with Attribute Selectors</h2>
    
    <form>
        <input type="text" placeholder="Name" required><br><br>
        <input type="email" placeholder="Email" required><br><br>
        <input type="password" placeholder="Password"><br><br>
    </form>
    
    <h2>Links with Attribute Selectors</h2>
    
    <a href="document.pdf">Download PDF</a><br>
    <a href="https://www.google.com">Visit Google</a><br>
    <a href="report.pdf">Annual Report</a><br>
    
    <h2>Elements with Title</h2>
    
    <p title="This is a helpful tooltip">Hover over me for help</p>
    <span title="More information">Info icon</span>
</body>
</html>
```

---

## Selector Priority (Specificity)

When multiple selectors target the same element, which one wins?

### Priority Order (Highest to Lowest)

1. **Inline styles** (highest)
2. **ID selectors** (#id)
3. **Class selectors** (.class), attribute selectors, pseudo-classes
4. **Element selectors** (tag), pseudo-elements
5. **Universal selector** (*) (lowest)

### Examples

```css
/* Specificity: 1 (element) */
p {
    color: blue;
}

/* Specificity: 10 (class) */
.highlight {
    color: green;
}

/* Specificity: 100 (ID) */
#special {
    color: red;
}

/* Specificity: 1000 (inline) */
<p style="color: purple;">Text</p>
```

**Result:** Inline > ID > Class > Element

---

## Summary Table

| Selector Type | Syntax | Example | Use Case |
|---------------|--------|---------|----------|
| **Element** | `tag` | `p { }` | Style all tags |
| **Class** | `.class` | `.box { }` | Reusable styles |
| **ID** | `#id` | `#header { }` | Unique elements |
| **Universal** | `*` | `* { }` | All elements |
| **Descendant** | `A B` | `div p { }` | Nested elements |
| **Child** | `A > B` | `div > p { }` | Direct children |
| **Adjacent** | `A + B` | `h2 + p { }` | Next sibling |
| **General Sibling** | `A ~ B` | `h2 ~ p { }` | All siblings after |
| **:hover** | `:hover` | `a:hover { }` | Mouse over |
| **:focus** | `:focus` | `input:focus { }` | Element focused |
| **:nth-child** | `:nth-child(n)` | `li:nth-child(2) { }` | Specific position |
| **::before** | `::before` | `h2::before { }` | Insert before |
| **::after** | `::after` | `h2::after { }` | Insert after |
| **::first-letter** | `::first-letter` | `p::first-letter { }` | First letter |
| **::first-line** | `::first-line` | `p::first-line { }` | First line |
| **::selection** | `::selection` | `::selection { }` | Selected text |
| **[attr]** | `[attribute]` | `[title] { }` | Has attribute |
| **[attr="val"]** | `[attribute="value"]` | `[type="text"] { }` | Exact match |
| **[attr^="val"]** | `[attribute^="value"]` | `[href^="https"] { }` | Starts with |
| **[attr$="val"]** | `[attribute$="value"]` | `[href$=".pdf"] { }` | Ends with |
| **[attr*="val"]** | `[attribute*="value"]` | `[href*="google"] { }` | Contains |

---

## Practice Exercises

### Exercise 1: Simple Selectors
Create a page with:
- All h1 elements blue
- All paragraphs with class "highlight" yellow background
- Element with ID "main" centered

### Exercise 2: Combinators
Style:
- All paragraphs inside div
- Direct children of ul
- Paragraph immediately after h2

### Exercise 3: Pseudo-Classes
Create:
- Links that change color on hover
- Even list items with gray background
- First and last child styling

### Exercise 4: Pseudo-Elements
Add:
- Large first letter to paragraphs
- Icon before all headings
- Custom selection color

### Exercise 5: Attribute Selectors
Style:
- All required inputs with red border
- Links to PDFs with icon
- Text inputs with yellow background

---

## Best Practices

### ✅ Do This

1. Use **classes** for reusable styles
2. Use **IDs** for unique elements
3. Use **element selectors** for global styles
4. Use **pseudo-classes** for interactive states
5. Use **attribute selectors** for form styling
6. Keep selectors simple and readable

### ❌ Avoid This

1. Don't overuse ID selectors
2. Don't make selectors too specific
3. Don't use inline styles (except testing)
4. Don't forget browser compatibility
5. Don't nest selectors too deeply

---

## Next Steps

In the next lesson, we'll learn about:
- Colors and backgrounds
- Text styling and fonts
- Box model (margin, padding, border)
- Display and positioning

---

*Congratulations! You've completed CSS Day 2. You now understand all types of CSS selectors and how to target any element on your webpage!*