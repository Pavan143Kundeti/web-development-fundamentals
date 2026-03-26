# HTML Fundamentals - Getting Started

## What is HTML?

**HTML** stands for **HyperText Markup Language**
- It's the standard language for creating web pages
- Uses **tags** to structure and format content
- Every web page you see is built with HTML

## Setting Up Your Development Environment

### Recommended Text Editors

| Editor | Best For | Features |
|--------|----------|----------|
| **VS Code** | Beginners & Professionals | Free, extensions, auto-complete |
| **Notepad++** | Simple editing | Lightweight, syntax highlighting |
| **Sublime Text** | Fast editing | Quick, powerful features |
| **Atom** | Customization | Highly customizable |

### Why Use a Code Editor?
- **Syntax highlighting** - Colors make code easier to read
- **Auto-completion** - Suggests tags and attributes
- **Error detection** - Highlights mistakes
- **File management** - Organize your project files

## HTML Document Structure

### Basic HTML Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My First Web Page</title>
</head>
<body>
    <h1>Welcome to My Website</h1>
    <p>This is my first HTML page!</p>
</body>
</html>
```

### Essential Document Tags

#### 1. DOCTYPE Declaration
```html
<!DOCTYPE html>
```
- **Purpose**: Tells browser this is HTML5 document
- **Must be**: First line of every HTML file
- **Case**: Not case-sensitive but use lowercase

#### 2. HTML Root Element
```html
<html lang="en">
</html>
```
- **Purpose**: Contains all other HTML elements
- **lang attribute**: Specifies language for accessibility
- **Closing tag**: Required at end of document

#### 3. Head Section
```html
<head>
    <!-- Metadata goes here -->
</head>
```
- **Purpose**: Contains information about the document
- **Not visible**: Content doesn't appear on web page
- **Contains**: Title, meta tags, links to CSS/JavaScript

#### 4. Body Section
```html
<body>
    <!-- Visible content goes here -->
</body>
```
- **Purpose**: Contains all visible content
- **What users see**: Everything inside body appears on web page

## Understanding HTML Tags

### Tag Structure

#### Opening and Closing Tags
```html
<tagname>Content goes here</tagname>
```

| Component | Example | Purpose |
|-----------|---------|---------|
| Opening tag | `<h1>` | Starts the element |
| Content | `Hello World` | The actual text/content |
| Closing tag | `</h1>` | Ends the element |

#### Self-Closing Tags
```html
<br>     <!-- Line break -->
<hr>     <!-- Horizontal rule -->
<img>    <!-- Image -->
<input>  <!-- Form input -->
```

### Common HTML Tags

#### Headings (6 Levels)
```html
<h1>Main Heading - Largest</h1>
<h2>Section Heading</h2>
<h3>Subsection Heading</h3>
<h4>Minor Heading</h4>
<h5>Small Heading</h5>
<h6>Smallest Heading</h6>
```

#### Paragraphs and Text
```html
<p>This is a paragraph of text.</p>
<p>This is another paragraph.</p>
```

#### Text Formatting
```html
<strong>Bold text (important)</strong>
<b>Bold text (visual only)</b>
<em>Italic text (emphasis)</em>
<i>Italic text (visual only)</i>
<u>Underlined text</u>
<mark>Highlighted text</mark>
```

#### Line Breaks and Spacing
```html
<br>     <!-- Single line break -->
<hr>     <!-- Horizontal line -->
&nbsp;   <!-- Non-breaking space -->
```

## Hyperlinks - Connecting Pages

### Basic Link Structure
```html
<a href="destination">Link Text</a>
```

### Types of Links

#### 1. External Links
```html
<a href="https://www.google.com">Visit Google</a>
<a href="https://www.youtube.com" target="_blank">Open YouTube in New Tab</a>
```

#### 2. Internal Links (Same Website)
```html
<a href="about.html">About Us</a>
<a href="contact.html">Contact</a>
```

#### 3. Email Links
```html
<a href="mailto:someone@example.com">Send Email</a>
```

#### 4. Phone Links
```html
<a href="tel:+1234567890">Call Us</a>
```

## Metadata and SEO

### Important Meta Tags

#### Character Encoding
```html
<meta charset="UTF-8">
```
- **Purpose**: Defines character set for proper text display
- **UTF-8**: Supports all languages and special characters

#### Viewport (Mobile Responsiveness)
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
- **Purpose**: Makes website mobile-friendly
- **Essential**: For responsive design

#### Page Description
```html
<meta name="description" content="Learn HTML basics with step-by-step tutorials">
```
- **Purpose**: Search engines use this for search results
- **Length**: Keep under 160 characters

#### Keywords
```html
<meta name="keywords" content="HTML, web development, tutorial, beginner">
```
- **Purpose**: Helps search engines understand page content
- **Note**: Less important than description

### Page Title
```html
<title>HTML Basics - Web Development Tutorial</title>
```
- **Appears**: In browser tab and search results
- **Important**: For SEO and user experience
- **Length**: Keep under 60 characters

## W3C Standards

### What is W3C?
- **W3C** = World Wide Web Consortium
- **Purpose**: Creates web standards and guidelines
- **Why Important**: Ensures websites work across all browsers

### Following Standards
- **Valid HTML**: Use proper tag structure
- **Semantic HTML**: Use tags for their intended purpose
- **Accessibility**: Make websites usable for everyone
- **Cross-browser compatibility**: Works in all browsers

### HTML Validation
- **Tool**: W3C Markup Validator
- **Purpose**: Check if your HTML follows standards
- **Benefits**: Better performance, fewer bugs

## Best Practices

### 1. Document Structure
- Always include DOCTYPE
- Use proper nesting of tags
- Close all tags that need closing
- Use lowercase for tag names

### 2. Content Organization
- Use headings in logical order (h1, then h2, then h3)
- One h1 per page
- Use paragraphs for text blocks
- Group related content

### 3. Accessibility
- Add alt text to images
- Use semantic HTML tags
- Provide proper heading structure
- Include lang attribute

### 4. SEO Optimization
- Write descriptive titles
- Use meta descriptions
- Structure content with headings
- Use meaningful link text

## Common Mistakes to Avoid

1. **Forgetting closing tags**
   ```html
   <!-- Wrong -->
   <p>Text without closing tag
   
   <!-- Correct -->
   <p>Text with proper closing tag</p>
   ```

2. **Improper nesting**
   ```html
   <!-- Wrong -->
   <p><strong>Bold text</p></strong>
   
   <!-- Correct -->
   <p><strong>Bold text</strong></p>
   ```

3. **Missing DOCTYPE**
   ```html
   <!-- Always start with -->
   <!DOCTYPE html>
   ```

## Practice Exercise

Create a simple HTML page with:
- Proper document structure
- A main heading
- Two paragraphs of text
- One bold word and one italic word
- A link to your favorite website

## Next Steps

In the next lesson, we'll learn about:
- HTML lists (ordered and unordered)
- Images and multimedia
- Tables for data presentation
- Forms for user input

---

*Remember: HTML is the foundation of web development. Master these basics before moving to CSS and JavaScript.*