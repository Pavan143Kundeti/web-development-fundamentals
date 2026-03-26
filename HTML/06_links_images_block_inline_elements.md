# Day 6: Links, Images, Block & Inline Elements

## Overview

This lesson covers four essential HTML concepts:
1. **Anchor Tags** - Creating hyperlinks between pages
2. **Images** - Adding visual content to webpages
3. **Block vs Inline Elements** - Understanding element behavior
4. **Div vs Span** - Organizing and styling content sections

---

# Part 1: Anchor Tags (Hyperlinks)

## What are Anchor Tags?

Anchor tags create **hyperlinks** - clickable links that connect different web pages. This is what makes the web "hypertext" - interconnected documents.

### Basic Syntax

```html
<a href="destination">Link Text</a>
```

| Component | Purpose |
|-----------|---------|
| `<a>` | Anchor tag (opening) |
| `href` | Hypertext reference - specifies destination |
| Link Text | Visible clickable text |
| `</a>` | Closing tag |

---

## Types of Links

### 1. External Links (Other Websites)

Links to websites outside your project.

```html
<!-- Link to Twitter -->
<a href="https://www.twitter.com">Visit Twitter</a>

<!-- Link to Amazon -->
<a href="https://www.amazon.in">Shop on Amazon</a>

<!-- Link to Google -->
<a href="https://www.google.com">Search Google</a>
```

**Important:** Always include `https://` or `http://` for external links.

### 2. Internal Links (Same Website)

Links to other pages within your own website.

#### Same Folder
```html
<!-- Both files in same folder -->
<a href="about.html">About Us</a>
<a href="contact.html">Contact</a>
<a href="services.html">Our Services</a>
```

#### Different Folders

**Project Structure:**
```
project/
├── index.html
├── pages/
│   ├── about.html
│   └── contact.html
└── products/
    └── items.html
```

**From index.html to pages folder:**
```html
<a href="pages/about.html">About Us</a>
<a href="pages/contact.html">Contact</a>
```

**From pages/about.html back to index.html:**
```html
<a href="../index.html">Home</a>
```

**From pages/about.html to products/items.html:**
```html
<a href="../products/items.html">Products</a>
```

### Path Navigation Rules

| Path | Meaning | Example |
|------|---------|---------|
| `file.html` | Same folder | `about.html` |
| `folder/file.html` | Go into folder | `pages/about.html` |
| `../file.html` | Go up one level | `../index.html` |
| `../../file.html` | Go up two levels | `../../home.html` |

---

## Target Attribute

Controls where the link opens.

### Open in New Tab

```html
<a href="https://www.google.com" target="_blank">Open Google in New Tab</a>
```

### Target Values

| Value | Behavior |
|-------|----------|
| `_self` | Same tab (default) |
| `_blank` | New tab/window |
| `_parent` | Parent frame |
| `_top` | Full window |

---

## Email and Phone Links

### Email Links
```html
<a href="mailto:contact@example.com">Send Email</a>
<a href="mailto:support@company.com?subject=Help Request">Email Support</a>
```

### Phone Links
```html
<a href="tel:+919876543210">Call Us</a>
<a href="tel:+911234567890">Customer Service</a>
```

---

## Styling Links

### Basic Link Styling

```html
<a href="page.html" style="color: blue; text-decoration: none;">Styled Link</a>
<a href="page.html" style="color: red; font-weight: bold;">Bold Red Link</a>
```

### Common Link Styles

```html
<!-- Remove underline -->
<a href="#" style="text-decoration: none;">No Underline</a>

<!-- Change color -->
<a href="#" style="color: green;">Green Link</a>

<!-- Add background -->
<a href="#" style="background-color: yellow; padding: 5px;">Highlighted Link</a>
```

---

## Complete Example: Navigation Menu

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Website</title>
</head>
<body>
    <h1>Welcome to My Website</h1>
    
    <!-- Navigation Menu -->
    <nav>
        <a href="index.html">Home</a> |
        <a href="pages/about.html">About</a> |
        <a href="pages/services.html">Services</a> |
        <a href="pages/contact.html">Contact</a>
    </nav>
    
    <h2>External Links</h2>
    <ul>
        <li><a href="https://www.google.com" target="_blank">Google</a></li>
        <li><a href="https://www.twitter.com" target="_blank">Twitter</a></li>
        <li><a href="https://www.amazon.in" target="_blank">Amazon</a></li>
    </ul>
    
    <h2>Contact Information</h2>
    <p>Email: <a href="mailto:info@example.com">info@example.com</a></p>
    <p>Phone: <a href="tel:+919876543210">+91 98765 43210</a></p>
</body>
</html>
```

---

# Part 2: Images in HTML

## What are Image Tags?

The `<img>` tag embeds images into web pages. It's a **self-closing tag** (no closing tag needed).

### Basic Syntax

```html
<img src="image-location" alt="description">
```

| Attribute | Purpose | Required |
|-----------|---------|----------|
| `src` | Source/location of image | Yes |
| `alt` | Alternative text (if image fails) | Yes |
| `width` | Image width | No |
| `height` | Image height | No |

---

## Image Sources

### 1. Local Images (Your Computer)

#### Same Folder
```html
<img src="photo.jpg" alt="My Photo">
<img src="logo.png" alt="Company Logo">
```

#### Images Folder
```html
<!-- Project structure:
     index.html
     images/
       photo.jpg
       logo.png
-->

<img src="images/photo.jpg" alt="My Photo">
<img src="images/logo.png" alt="Logo">
```

#### Parent Folder
```html
<!-- From subfolder to parent folder -->
<img src="../photo.jpg" alt="Photo">
```

### 2. External Images (Web URLs)

```html
<img src="https://www.example.com/image.jpg" alt="External Image">
```

**Example with real URL:**
```html
<img src="https://via.placeholder.com/300x200" alt="Placeholder Image">
```

---

## Image Dimensions

### Setting Width and Height

```html
<!-- Using pixels -->
<img src="photo.jpg" alt="Photo" width="300" height="200">

<!-- Using percentages -->
<img src="photo.jpg" alt="Photo" width="50%" height="auto">
```

### Maintaining Aspect Ratio

```html
<!-- Set only width, height adjusts automatically -->
<img src="photo.jpg" alt="Photo" width="400">

<!-- Set only height, width adjusts automatically -->
<img src="photo.jpg" alt="Photo" height="300">
```

---

## Alternative Text (alt)

### Why alt is Important

1. **Accessibility** - Screen readers read alt text for visually impaired users
2. **SEO** - Search engines use alt text to understand images
3. **Broken Images** - Shows text when image fails to load

### Good vs Bad Alt Text

```html
<!-- Bad: Not descriptive -->
<img src="photo.jpg" alt="image">

<!-- Good: Descriptive -->
<img src="photo.jpg" alt="Sunset over mountains">

<!-- Bad: Too long -->
<img src="logo.jpg" alt="This is our company logo which represents our brand identity and values">

<!-- Good: Concise -->
<img src="logo.jpg" alt="Company Logo">
```

---

## Image as a Link (Clickable Image)

Nest `<img>` inside `<a>` tag to make images clickable.

### Syntax

```html
<a href="destination">
    <img src="image.jpg" alt="description">
</a>
```

### Examples

```html
<!-- Click image to go to website -->
<a href="https://www.google.com">
    <img src="google-logo.png" alt="Google Logo" width="200">
</a>

<!-- Click image to open another page -->
<a href="products.html">
    <img src="shop-now.jpg" alt="Shop Now" width="300">
</a>

<!-- Click image to open in new tab -->
<a href="https://www.amazon.in" target="_blank">
    <img src="amazon-banner.jpg" alt="Amazon Banner">
</a>
```

---

## Complete Image Example

```html
<!DOCTYPE html>
<html>
<head>
    <title>Image Gallery</title>
</head>
<body>
    <h1>My Photo Gallery</h1>
    
    <!-- Local image -->
    <h2>Profile Picture</h2>
    <img src="images/profile.jpg" alt="Profile Picture" width="200" height="200">
    
    <!-- Image with link -->
    <h2>Click to Visit Website</h2>
    <a href="https://www.example.com" target="_blank">
        <img src="images/banner.jpg" alt="Website Banner" width="400">
    </a>
    
    <!-- Multiple images -->
    <h2>Product Images</h2>
    <img src="images/product1.jpg" alt="Product 1" width="150">
    <img src="images/product2.jpg" alt="Product 2" width="150">
    <img src="images/product3.jpg" alt="Product 3" width="150">
    
    <!-- External image -->
    <h2>Placeholder Image</h2>
    <img src="https://via.placeholder.com/300x200" alt="Placeholder" width="300">
</body>
</html>
```

---

# Part 3: Block vs Inline Elements

## Understanding Element Behavior

HTML elements are classified into two main categories based on how they display on a webpage.

---

## Block-Level Elements

### Characteristics

1. **Full Width** - Takes up entire width of parent container
2. **New Line** - Always starts on a new line
3. **Forces Break** - Next element goes to new line
4. **Can Contain** - Other block and inline elements

### Common Block Elements

| Element | Purpose |
|---------|---------|
| `<h1>` to `<h6>` | Headings |
| `<p>` | Paragraphs |
| `<div>` | Division/container |
| `<ul>`, `<ol>` | Lists |
| `<li>` | List items |
| `<table>` | Tables |
| `<form>` | Forms |
| `<header>` | Header section |
| `<footer>` | Footer section |
| `<section>` | Content section |

### Block Element Example

```html
<h1>This is a heading</h1>
<p>This is a paragraph.</p>
<p>This is another paragraph.</p>
```

**Result:**
```
This is a heading
This is a paragraph.
This is another paragraph.
```

Each element takes full width and starts on a new line.

---

## Inline Elements

### Characteristics

1. **Only Necessary Width** - Takes only as much space as needed
2. **Same Line** - Stays on same line with other inline elements
3. **No Line Break** - Doesn't force next element to new line
4. **Cannot Contain** - Block elements (usually)

### Common Inline Elements

| Element | Purpose |
|---------|---------|
| `<a>` | Links |
| `<img>` | Images |
| `<span>` | Inline container |
| `<strong>` | Bold text |
| `<em>` | Italic text |
| `<b>` | Bold |
| `<i>` | Italic |
| `<u>` | Underline |
| `<br>` | Line break |

### Inline Element Example

```html
<p>This is <strong>bold</strong> and this is <em>italic</em> text.</p>
```

**Result:**
```
This is bold and this is italic text.
```

All elements stay on the same line.

---

## Visual Comparison

### Block Elements
```html
<h2>Heading 1</h2>
<h2>Heading 2</h2>
<p>Paragraph 1</p>
<p>Paragraph 2</p>
```

**Display:**
```
Heading 1
Heading 2
Paragraph 1
Paragraph 2
```

### Inline Elements
```html
<a href="#">Link 1</a>
<a href="#">Link 2</a>
<strong>Bold</strong>
<em>Italic</em>
```

**Display:**
```
Link 1 Link 2 Bold Italic
```

---

## Practical Examples

### Example 1: Mixed Elements

```html
<!DOCTYPE html>
<html>
<head>
    <title>Block vs Inline</title>
</head>
<body>
    <!-- Block elements -->
    <h1>Main Heading</h1>
    <p>This is a paragraph with <strong>bold text</strong> and <em>italic text</em>.</p>
    <p>This is another paragraph.</p>
    
    <!-- Inline elements in a row -->
    <a href="#">Home</a>
    <a href="#">About</a>
    <a href="#">Contact</a>
</body>
</html>
```

### Example 2: Navigation with Links

```html
<!-- Block element containing inline elements -->
<div>
    <a href="home.html">Home</a> |
    <a href="about.html">About</a> |
    <a href="services.html">Services</a> |
    <a href="contact.html">Contact</a>
</div>
```

### Example 3: List with Links

```html
<!-- Block list with inline links -->
<ul>
    <li><a href="page1.html">Page 1</a></li>
    <li><a href="page2.html">Page 2</a></li>
    <li><a href="page3.html">Page 3</a></li>
</ul>
```

---

## Key Differences Table

| Feature | Block Elements | Inline Elements |
|---------|----------------|-----------------|
| Width | Full width available | Only content width |
| Line Break | Starts on new line | Stays on same line |
| Next Element | Goes to new line | Stays on same line |
| Height/Width | Can be set | Limited control |
| Contains | Block & inline | Only inline |
| Examples | `<div>`, `<p>`, `<h1>` | `<span>`, `<a>`, `<strong>` |

---

# Part 4: Div and Span Tags

## What are Div and Span?

Both are **container elements** used to group and style content, but they behave differently.

---

## Div Tag (Block-Level Container)

### Characteristics

- **Block-level element**
- Takes full width
- Starts on new line
- Used to group large sections of content

### Basic Syntax

```html
<div>
    Content goes here
</div>
```

### When to Use Div

- Creating page sections (header, footer, sidebar)
- Grouping related content
- Applying styles to multiple elements
- Creating layouts

### Div Examples

#### Example 1: Simple Div

```html
<div>
    <h2>Section Title</h2>
    <p>This is content inside a div.</p>
</div>
```

#### Example 2: Styled Div

```html
<div style="background-color: lightblue; padding: 20px;">
    <h2>Welcome Section</h2>
    <p>This div has a light blue background.</p>
</div>
```

#### Example 3: Multiple Divs

```html
<div style="background-color: lightgreen; padding: 10px;">
    <h3>Section 1</h3>
    <p>Content for section 1</p>
</div>

<div style="background-color: lightyellow; padding: 10px;">
    <h3>Section 2</h3>
    <p>Content for section 2</p>
</div>

<div style="background-color: lightcoral; padding: 10px;">
    <h3>Section 3</h3>
    <p>Content for section 3</p>
</div>
```

---

## Span Tag (Inline Container)

### Characteristics

- **Inline element**
- Takes only necessary width
- Stays on same line
- Used to style small portions of text

### Basic Syntax

```html
<span>Content goes here</span>
```

### When to Use Span

- Styling specific words or phrases
- Applying color to part of text
- Highlighting specific content
- Inline formatting

### Span Examples

#### Example 1: Simple Span

```html
<p>This is <span style="color: red;">red text</span> in a paragraph.</p>
```

#### Example 2: Multiple Spans

```html
<p>
    I love <span style="color: blue;">blue</span>, 
    <span style="color: green;">green</span>, and 
    <span style="color: red;">red</span> colors.
</p>
```

#### Example 3: Styled Spans

```html
<p>
    The price is 
    <span style="font-size: 24px; color: red; font-weight: bold;">₹500</span>
    only!
</p>
```

---

## Div vs Span Comparison

### Visual Difference

```html
<!-- Div (Block) -->
<div style="background-color: lightblue;">Div 1</div>
<div style="background-color: lightgreen;">Div 2</div>

<!-- Span (Inline) -->
<span style="background-color: lightblue;">Span 1</span>
<span style="background-color: lightgreen;">Span 2</span>
```

**Result:**
```
Div 1
Div 2
Span 1 Span 2
```

### Comparison Table

| Feature | Div | Span |
|---------|-----|------|
| Type | Block-level | Inline |
| Width | Full width | Content width only |
| Line Break | Yes | No |
| Use Case | Large sections | Small text portions |
| Contains | Any elements | Inline elements |

---

## Practical Examples

### Example 1: Page Layout with Div

```html
<!DOCTYPE html>
<html>
<head>
    <title>Page Layout</title>
</head>
<body>
    <!-- Header -->
    <div style="background-color: navy; color: white; padding: 20px;">
        <h1>My Website</h1>
    </div>
    
    <!-- Navigation -->
    <div style="background-color: lightgray; padding: 10px;">
        <a href="#">Home</a> |
        <a href="#">About</a> |
        <a href="#">Contact</a>
    </div>
    
    <!-- Main Content -->
    <div style="background-color: white; padding: 20px; min-height: 400px;">
        <h2>Welcome</h2>
        <p>This is the main content area.</p>
    </div>
    
    <!-- Footer -->
    <div style="background-color: darkgray; color: white; padding: 10px; text-align: center;">
        <p>&copy; 2024 My Website</p>
    </div>
</body>
</html>
```

### Example 2: Text Highlighting with Span

```html
<!DOCTYPE html>
<html>
<head>
    <title>Span Examples</title>
</head>
<body>
    <h1>Product Information</h1>
    
    <p>
        Product Name: <span style="font-weight: bold; color: blue;">Laptop</span>
    </p>
    
    <p>
        Price: <span style="font-size: 20px; color: red;">₹45,000</span>
    </p>
    
    <p>
        Status: <span style="background-color: lightgreen; padding: 5px;">In Stock</span>
    </p>
    
    <p>
        Rating: 
        <span style="color: gold;">★★★★★</span>
        <span style="color: gray;">(4.5/5)</span>
    </p>
</body>
</html>
```

### Example 3: Combined Div and Span

```html
<!DOCTYPE html>
<html>
<head>
    <title>Div and Span Together</title>
</head>
<body>
    <div style="border: 2px solid black; padding: 15px; margin: 10px;">
        <h2>Special Offer!</h2>
        <p>
            Get <span style="color: red; font-size: 24px; font-weight: bold;">50% OFF</span>
            on all products this week!
        </p>
        <p>
            Use code: <span style="background-color: yellow; padding: 3px;">SAVE50</span>
        </p>
    </div>
    
    <div style="border: 2px solid green; padding: 15px; margin: 10px;">
        <h2>Customer Review</h2>
        <p>
            <span style="font-weight: bold;">John Doe</span> says:
            "This product is <span style="color: green;">excellent</span>!"
        </p>
    </div>
</body>
</html>
```

---

## Complete Day 6 Project

### Project: Simple Website with All Concepts

```html
<!DOCTYPE html>
<html>
<head>
    <title>Day 6 Complete Example</title>
</head>
<body>
    <!-- Header Section (Div) -->
    <div style="background-color: #333; color: white; padding: 20px; text-align: center;">
        <h1>Welcome to <span style="color: #4CAF50;">My Website</span></h1>
    </div>
    
    <!-- Navigation (Div with Inline Links) -->
    <div style="background-color: #f1f1f1; padding: 10px; text-align: center;">
        <a href="index.html" style="margin: 0 10px; text-decoration: none;">Home</a>
        <a href="about.html" style="margin: 0 10px; text-decoration: none;">About</a>
        <a href="gallery.html" style="margin: 0 10px; text-decoration: none;">Gallery</a>
        <a href="contact.html" style="margin: 0 10px; text-decoration: none;">Contact</a>
    </div>
    
    <!-- Main Content (Div) -->
    <div style="padding: 20px;">
        <!-- Image Section -->
        <div style="text-align: center; margin: 20px 0;">
            <h2>Featured Image</h2>
            <a href="https://www.example.com" target="_blank">
                <img src="https://via.placeholder.com/400x300" alt="Featured Image" width="400">
            </a>
            <p><em>Click image to visit website</em></p>
        </div>
        
        <!-- Content Section -->
        <div style="background-color: #e7f3fe; padding: 15px; margin: 20px 0; border-left: 6px solid #2196F3;">
            <h3>About Our Services</h3>
            <p>
                We provide <span style="font-weight: bold; color: #2196F3;">high-quality</span> 
                services at <span style="color: red; font-size: 18px;">affordable prices</span>.
            </p>
            <p>
                Contact us at: 
                <a href="mailto:info@example.com">info@example.com</a> or 
                <a href="tel:+919876543210">+91 98765 43210</a>
            </p>
        </div>
        
        <!-- Image Gallery -->
        <div style="margin: 20px 0;">
            <h3>Our Gallery</h3>
            <img src="https://via.placeholder.com/150" alt="Image 1" width="150" style="margin: 5px;">
            <img src="https://via.placeholder.com/150" alt="Image 2" width="150" style="margin: 5px;">
            <img src="https://via.placeholder.com/150" alt="Image 3" width="150" style="margin: 5px;">
        </div>
        
        <!-- External Links -->
        <div style="background-color: #fff3cd; padding: 15px; margin: 20px 0;">
            <h3>Follow Us</h3>
            <p>
                <a href="https://www.twitter.com" target="_blank" style="margin-right: 15px;">Twitter</a>
                <a href="https://www.facebook.com" target="_blank" style="margin-right: 15px;">Facebook</a>
                <a href="https://www.instagram.com" target="_blank">Instagram</a>
            </p>
        </div>
    </div>
    
    <!-- Footer (Div) -->
    <div style="background-color: #333; color: white; padding: 15px; text-align: center;">
        <p>&copy; 2024 My Website. All Rights Reserved.</p>
        <p>
            <span style="color: #4CAF50;">Designed with ❤️</span>
        </p>
    </div>
</body>
</html>
```

---

## Summary

### Anchor Tags (Links)
- Use `<a href="url">` to create links
- `target="_blank"` opens in new tab
- Use proper paths for internal navigation
- Can link to emails and phone numbers

### Images
- Use `<img src="location" alt="description">`
- Always include alt text
- Control size with width and height
- Nest in `<a>` tag to make clickable

### Block vs Inline
- **Block**: Full width, new line (div, p, h1)
- **Inline**: Content width, same line (span, a, strong)

### Div and Span
- **Div**: Block container for sections
- **Span**: Inline container for text portions
- Both used for grouping and styling

---

## Practice Exercises

### Exercise 1: Navigation Menu
Create a navigation menu with 5 links, styled with colors and no underlines.

### Exercise 2: Image Gallery
Create a gallery with 6 images, each linking to a different page.

### Exercise 3: Styled Sections
Create 3 div sections with different background colors, each containing headings and paragraphs with span-styled text.

### Exercise 4: Complete Webpage
Build a complete webpage using all concepts: header, navigation, content with images and links, and footer.

---

*Congratulations! You've completed Day 6. Next, we'll learn about HTML Forms and user input!*