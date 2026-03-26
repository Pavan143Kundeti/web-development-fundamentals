# CSS Day 1: Introduction to CSS and Three Ways to Apply Styles

## What is CSS?

**CSS** stands for **Cascading Style Sheets**

CSS is used to make websites look beautiful and professional. Without CSS, websites would look plain and boring with just black text on white background.

### What CSS Does

- Changes colors (text, background, borders)
- Changes fonts (size, style, family)
- Creates layouts (positioning, spacing)
- Adds animations and effects
- Makes websites responsive (mobile-friendly)

---

## Why Use CSS?

### Before CSS (Plain HTML)
```html
<h1>Welcome</h1>
<p>This is plain text.</p>
```
**Result:** Black text, default font, no styling

### After CSS
```html
<h1 style="color: blue; font-size: 36px;">Welcome</h1>
<p style="color: gray; font-size: 18px;">This is styled text.</p>
```
**Result:** Colorful, sized, professional-looking text

---

## CSS Syntax

CSS follows a simple pattern:

```css
selector {
    property: value;
    property: value;
}
```

### Parts Explained

| Part | Purpose | Example |
|------|---------|---------|
| **Selector** | What to style | `h1`, `p`, `.class`, `#id` |
| **Property** | What to change | `color`, `font-size`, `background` |
| **Value** | How to change it | `red`, `20px`, `blue` |

### Example

```css
h1 {
    color: blue;
    font-size: 30px;
}
```

**Reads as:** "Make all h1 headings blue with 30px font size"

---

# Three Ways to Apply CSS

There are three methods to add CSS to HTML:

1. **Inline CSS** - Inside HTML tags
2. **Internal CSS** - Inside `<style>` tag in same file
3. **External CSS** - Separate CSS file

---

## Method 1: Inline CSS

### What is Inline CSS?

CSS written directly inside HTML tags using the `style` attribute.

### Syntax

```html
<tagname style="property: value; property: value;">Content</tagname>
```

### Examples

#### Example 1: Change Text Color

```html
<h1 style="color: red;">Red Heading</h1>
<p style="color: blue;">Blue paragraph</p>
```

#### Example 2: Multiple Properties

```html
<h1 style="color: green; font-size: 40px; text-align: center;">
    Styled Heading
</h1>
```

#### Example 3: Background Color

```html
<p style="background-color: yellow; padding: 10px;">
    Highlighted text
</p>
```

#### Example 4: Complete Example

```html
<!DOCTYPE html>
<html>
<head>
    <title>Inline CSS Example</title>
</head>
<body>
    <h1 style="color: navy; text-align: center;">Welcome to My Website</h1>
    
    <p style="color: gray; font-size: 18px;">
        This paragraph uses inline CSS for styling.
    </p>
    
    <p style="background-color: lightblue; padding: 15px; border: 2px solid blue;">
        This paragraph has background color, padding, and border.
    </p>
</body>
</html>
```

### Advantages of Inline CSS

✅ Quick and easy for small changes
✅ Highest priority (overrides other styles)
✅ Good for testing styles

### Disadvantages of Inline CSS

❌ Hard to maintain for large websites
❌ Repeats code (not reusable)
❌ Mixes HTML and CSS (not clean)
❌ Cannot use some CSS features (like hover effects)

### When to Use Inline CSS

- Quick fixes or tests
- Email templates
- Single element styling
- Overriding other styles

---

## Method 2: Internal CSS

### What is Internal CSS?

CSS written inside `<style>` tag in the `<head>` section of HTML document.

### Syntax

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        selector {
            property: value;
        }
    </style>
</head>
<body>
    <!-- HTML content -->
</body>
</html>
```

### Examples

#### Example 1: Basic Internal CSS

```html
<!DOCTYPE html>
<html>
<head>
    <title>Internal CSS</title>
    <style>
        h1 {
            color: blue;
            text-align: center;
        }
        
        p {
            color: green;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <h1>This heading is blue and centered</h1>
    <p>This paragraph is green with 18px font size.</p>
    <p>All paragraphs get the same style automatically.</p>
</body>
</html>
```

#### Example 2: Multiple Elements

```html
<!DOCTYPE html>
<html>
<head>
    <title>Internal CSS Example</title>
    <style>
        body {
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
        }
        
        h1 {
            color: darkblue;
            text-align: center;
            font-size: 36px;
        }
        
        h2 {
            color: darkgreen;
            font-size: 28px;
        }
        
        p {
            color: #333;
            font-size: 16px;
            line-height: 1.6;
        }
        
        a {
            color: blue;
            text-decoration: none;
        }
    </style>
</head>
<body>
    <h1>Welcome to CSS Tutorial</h1>
    <h2>What is CSS?</h2>
    <p>CSS stands for Cascading Style Sheets.</p>
    <p>It is used to style web pages.</p>
    <a href="#">Learn More</a>
</body>
</html>
```

#### Example 3: With Classes

```html
<!DOCTYPE html>
<html>
<head>
    <title>Classes Example</title>
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
    <div class="box">
        <p>This content is inside a box.</p>
    </div>
</body>
</html>
```

### Advantages of Internal CSS

✅ All styles in one place (same file)
✅ Can style multiple elements at once
✅ No need for separate file
✅ Good for single-page websites

### Disadvantages of Internal CSS

❌ Styles only work for one HTML file
❌ Cannot reuse styles across multiple pages
❌ Makes HTML file larger
❌ Hard to maintain for multi-page websites

### When to Use Internal CSS

- Single-page websites
- Small projects
- Testing and development
- When you don't want separate files

---

## Method 3: External CSS

### What is External CSS?

CSS written in a separate `.css` file and linked to HTML documents.

### How It Works

1. Create a separate CSS file (e.g., `style.css`)
2. Write all CSS rules in that file
3. Link the CSS file to HTML using `<link>` tag

### Syntax

**HTML File (index.html):**
```html
<!DOCTYPE html>
<html>
<head>
    <title>External CSS</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>Heading</h1>
    <p>Paragraph</p>
</body>
</html>
```

**CSS File (style.css):**
```css
h1 {
    color: blue;
    text-align: center;
}

p {
    color: green;
    font-size: 18px;
}
```

### Link Tag Explained

```html
<link rel="stylesheet" href="style.css">
```

| Attribute | Purpose | Value |
|-----------|---------|-------|
| `rel` | Relationship | `stylesheet` |
| `href` | File location | `style.css` or path |

---

### Complete External CSS Example

#### Step 1: Create HTML File (index.html)

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Website</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Welcome to My Website</h1>
        <nav>
            <a href="#">Home</a>
            <a href="#">About</a>
            <a href="#">Contact</a>
        </nav>
    </header>
    
    <main>
        <h2>About CSS</h2>
        <p>CSS makes websites beautiful and professional.</p>
        <p class="highlight">This is highlighted text.</p>
    </main>
    
    <footer>
        <p>&copy; 2024 My Website</p>
    </footer>
</body>
</html>
```

#### Step 2: Create CSS File (style.css)

```css
/* Reset and Body Styles */
body {
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
    background-color: #f5f5f5;
}

/* Header Styles */
header {
    background-color: #333;
    color: white;
    padding: 20px;
    text-align: center;
}

header h1 {
    margin: 0;
    font-size: 36px;
}

/* Navigation Styles */
nav {
    margin-top: 10px;
}

nav a {
    color: white;
    text-decoration: none;
    margin: 0 15px;
    font-size: 18px;
}

nav a:hover {
    color: #4CAF50;
}

/* Main Content Styles */
main {
    max-width: 800px;
    margin: 40px auto;
    padding: 20px;
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

h2 {
    color: #333;
    border-bottom: 2px solid #4CAF50;
    padding-bottom: 10px;
}

p {
    color: #666;
    font-size: 16px;
    line-height: 1.6;
}

.highlight {
    background-color: yellow;
    padding: 5px;
    font-weight: bold;
}

/* Footer Styles */
footer {
    background-color: #333;
    color: white;
    text-align: center;
    padding: 20px;
    margin-top: 40px;
}

footer p {
    margin: 0;
    color: white;
}
```

---

### Multiple HTML Pages with One CSS File

**Advantage:** Change one CSS file, update all pages!

#### Page 1 (index.html)
```html
<!DOCTYPE html>
<html>
<head>
    <title>Home</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>Home Page</h1>
    <p>Welcome to our website.</p>
</body>
</html>
```

#### Page 2 (about.html)
```html
<!DOCTYPE html>
<html>
<head>
    <title>About</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>About Page</h1>
    <p>Learn more about us.</p>
</body>
</html>
```

#### Page 3 (contact.html)
```html
<!DOCTYPE html>
<html>
<head>
    <title>Contact</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>Contact Page</h1>
    <p>Get in touch with us.</p>
</body>
</html>
```

#### One CSS File (style.css)
```css
body {
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
}

h1 {
    color: navy;
    text-align: center;
}

p {
    color: #333;
    font-size: 18px;
}
```

**Result:** All three pages look the same! Change `style.css` once, all pages update automatically.

---

### Advantages of External CSS

✅ **Reusable** - One CSS file for multiple HTML pages
✅ **Easy Maintenance** - Update one file, change entire website
✅ **Clean Code** - Separates HTML and CSS
✅ **Faster Loading** - Browser caches CSS file
✅ **Team Work** - Different people can work on HTML and CSS
✅ **Professional** - Industry standard approach

### Disadvantages of External CSS

❌ Requires separate file
❌ Extra HTTP request (slightly slower first load)
❌ Need to manage file paths

### When to Use External CSS

- Multi-page websites (Recommended!)
- Large projects
- Professional websites
- When working in teams
- When you want clean, maintainable code

---

## Comparison of Three Methods

| Feature | Inline CSS | Internal CSS | External CSS |
|---------|-----------|--------------|--------------|
| **Location** | Inside HTML tag | Inside `<style>` tag | Separate `.css` file |
| **Reusability** | ❌ No | ⚠️ Same page only | ✅ Multiple pages |
| **Maintenance** | ❌ Hard | ⚠️ Medium | ✅ Easy |
| **Code Cleanliness** | ❌ Mixed | ⚠️ Okay | ✅ Clean |
| **File Size** | Small | Medium | Large project |
| **Best For** | Quick fixes | Single page | Multi-page sites |
| **Priority** | Highest | Medium | Lowest |
| **Professional Use** | Rarely | Sometimes | Always |

---

## CSS Priority (Specificity)

When multiple styles target the same element, which one wins?

### Priority Order (Highest to Lowest)

1. **Inline CSS** (highest priority)
2. **Internal CSS**
3. **External CSS** (lowest priority)

### Example

```html
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="style.css">
    <style>
        p {
            color: green;  /* Internal CSS */
        }
    </style>
</head>
<body>
    <p style="color: red;">What color am I?</p>
</body>
</html>
```

**style.css:**
```css
p {
    color: blue;  /* External CSS */
}
```

**Result:** Text is RED (inline wins!)

---

## Best Practices

### ✅ Do This

1. **Use External CSS** for multi-page websites
2. **Use Internal CSS** for single-page sites
3. **Use Inline CSS** only for quick tests
4. **Organize CSS** - Group related styles together
5. **Use Comments** - Explain your CSS code
6. **Use Meaningful Names** - Clear class and ID names

### ❌ Avoid This

1. Don't mix all three methods unnecessarily
2. Don't use inline CSS for entire website
3. Don't forget to link CSS file properly
4. Don't use too many external CSS files
5. Don't write messy, unorganized CSS

---

## Common Mistakes and Solutions

### Mistake 1: CSS Not Working

**Problem:**
```html
<link rel="stylesheet" href="styles.css">
```
But file is named `style.css`

**Solution:** Match file names exactly!
```html
<link rel="stylesheet" href="style.css">
```

### Mistake 2: Wrong File Path

**Problem:**
```html
<link rel="stylesheet" href="style.css">
```
But CSS file is in `css` folder

**Solution:** Include folder path
```html
<link rel="stylesheet" href="css/style.css">
```

### Mistake 3: Forgetting Semicolon

**Problem:**
```css
h1 {
    color: blue
    font-size: 30px;
}
```

**Solution:** Add semicolon after each property
```css
h1 {
    color: blue;
    font-size: 30px;
}
```

### Mistake 4: Wrong Syntax

**Problem:**
```css
h1 {
    color = blue;
}
```

**Solution:** Use colon, not equals
```css
h1 {
    color: blue;
}
```

---

## Practice Exercise

### Exercise 1: Inline CSS
Create an HTML page with:
- Red heading
- Blue paragraph
- Yellow background on another paragraph

### Exercise 2: Internal CSS
Create an HTML page with internal CSS that styles:
- All headings blue
- All paragraphs gray
- Links green with no underline

### Exercise 3: External CSS
Create:
1. Three HTML pages (home, about, contact)
2. One CSS file
3. Style all pages with same design

---

## Summary

### What We Learned

1. **CSS** makes websites beautiful
2. **Three ways** to apply CSS:
   - Inline (inside tags)
   - Internal (in `<style>` tag)
   - External (separate file)
3. **External CSS** is best for real websites
4. **CSS syntax**: selector { property: value; }
5. **Priority**: Inline > Internal > External

### Key Points

- CSS separates design from content
- One CSS file can style many HTML pages
- External CSS is professional and maintainable
- Always link CSS file in `<head>` section
- Use proper file paths

---

## Next Steps

In the next lesson, we'll learn about:
- CSS Selectors (element, class, ID)
- Colors and backgrounds
- Text styling
- Box model

---

*Congratulations! You've completed CSS Day 1. You now understand the three ways to apply CSS and when to use each method!*