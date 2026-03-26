# CSS Day 4: CSS Units and Positioning

## Introduction

In this lesson, we'll learn about CSS units for measurements and how to position elements on a webpage. Understanding units and positioning is essential for creating precise and responsive layouts.

---

## Part 1: CSS Units

CSS units are used to specify sizes, distances, and measurements for properties like width, height, padding, margin, font-size, etc.

### Types of Units

1. **Absolute Units** - Fixed size, same everywhere
2. **Relative Units** - Size relative to something else

---

## Absolute Units

Absolute units have a fixed size and don't change based on other elements.

### Common Absolute Units

| Unit | Name | Description | Use Case |
|------|------|-------------|----------|
| **px** | Pixels | Most common unit | Screen designs |
| **pt** | Points | 1pt = 1/72 inch | Print media |
| **cm** | Centimeters | Physical measurement | Print media |
| **mm** | Millimeters | Physical measurement | Print media |
| **in** | Inches | Physical measurement | Print media |

### Pixels (px) - Most Common

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .box1 {
            width: 200px;
            height: 100px;
            padding: 20px;
            margin: 10px;
            font-size: 16px;
            background-color: lightblue;
            border: 2px solid navy;
        }
    </style>
</head>
<body>
    <div class="box1">
        This box uses pixels for all measurements
    </div>
</body>
</html>
```

**When to use px:**
- Fixed layouts
- Borders
- Small, precise measurements
- When you need exact control

---

## Relative Units

Relative units change based on other values (parent element, viewport, font size).

### Common Relative Units

| Unit | Relative To | Description | Use Case |
|------|-------------|-------------|----------|
| **%** | Parent element | Percentage of parent | Responsive widths |
| **em** | Parent font-size | Multiplier of parent font | Scalable spacing |
| **rem** | Root font-size | Multiplier of root font | Consistent sizing |
| **vw** | Viewport width | 1vw = 1% of viewport width | Full-width sections |
| **vh** | Viewport height | 1vh = 1% of viewport height | Full-height sections |
| **vmin** | Smaller viewport dimension | Responsive to smallest side | Square elements |
| **vmax** | Larger viewport dimension | Responsive to largest side | Special effects |

---

### Percentage (%)

Percentage is relative to the parent element's size.

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .parent {
            width: 500px;
            height: 300px;
            background-color: lightgray;
            padding: 20px;
        }
        
        .child {
            width: 50%;        /* 50% of 500px = 250px */
            height: 60%;       /* 60% of 300px = 180px */
            padding: 5%;       /* 5% of 500px = 25px */
            background-color: lightblue;
            border: 2px solid navy;
        }
    </style>
</head>
<body>
    <div class="parent">
        <div class="child">
            Child is 50% width and 60% height of parent
        </div>
    </div>
</body>
</html>
```

**When to use %:**
- Responsive layouts
- Fluid widths
- Relative sizing to parent

---

### em Unit

`em` is relative to the parent element's font-size.

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .parent {
            font-size: 20px;
            background-color: lightgray;
            padding: 10px;
        }
        
        .child {
            font-size: 1.5em;    /* 1.5 × 20px = 30px */
            padding: 1em;        /* 1 × 30px = 30px (uses own font-size) */
            margin: 0.5em;       /* 0.5 × 30px = 15px */
            background-color: lightblue;
        }
        
        .grandchild {
            font-size: 1.2em;    /* 1.2 × 30px = 36px */
            padding: 1em;        /* 1 × 36px = 36px */
            background-color: lightcoral;
        }
    </style>
</head>
<body>
    <div class="parent">
        Parent: 20px
        <div class="child">
            Child: 30px (1.5em)
            <div class="grandchild">
                Grandchild: 36px (1.2em)
            </div>
        </div>
    </div>
</body>
</html>
```

**Problem with em:** Compounds with nesting (gets bigger and bigger)

**When to use em:**
- Padding/margin relative to font-size
- Scalable components
- When you want inheritance

---

### rem Unit (Root em)

`rem` is relative to the ROOT element's font-size (html element), usually 16px.

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        html {
            font-size: 16px;  /* Root font-size */
        }
        
        .parent {
            font-size: 20px;
            background-color: lightgray;
            padding: 10px;
        }
        
        .child {
            font-size: 1.5rem;   /* 1.5 × 16px = 24px (from root) */
            padding: 1rem;       /* 1 × 16px = 16px (from root) */
            margin: 0.5rem;      /* 0.5 × 16px = 8px (from root) */
            background-color: lightblue;
        }
        
        .grandchild {
            font-size: 2rem;     /* 2 × 16px = 32px (from root) */
            padding: 1rem;       /* 1 × 16px = 16px (from root) */
            background-color: lightcoral;
        }
    </style>
</head>
<body>
    <div class="parent">
        Parent: 20px
        <div class="child">
            Child: 24px (1.5rem from root)
            <div class="grandchild">
                Grandchild: 32px (2rem from root)
            </div>
        </div>
    </div>
</body>
</html>
```

**Advantage:** No compounding, consistent sizing

**When to use rem:**
- Font sizes
- Consistent spacing
- Modern responsive design
- **Most recommended for new projects**

---

### Viewport Units (vw, vh)

Viewport units are relative to the browser window size.

- **1vw** = 1% of viewport width
- **1vh** = 1% of viewport height

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        body {
            margin: 0;
            padding: 0;
        }
        
        .full-width {
            width: 100vw;        /* 100% of viewport width */
            height: 50vh;        /* 50% of viewport height */
            background-color: lightblue;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 5vw;      /* Font scales with viewport */
        }
        
        .full-screen {
            width: 100vw;
            height: 100vh;       /* Full screen height */
            background-color: lightcoral;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .box {
            width: 50vw;         /* Half viewport width */
            height: 30vh;        /* 30% viewport height */
            background-color: lightgreen;
            padding: 2vw;
        }
    </style>
</head>
<body>
    <div class="full-width">
        50% Viewport Height
    </div>
    
    <div class="box">
        Responsive Box: 50vw × 30vh
    </div>
</body>
</html>
```

**When to use vw/vh:**
- Full-screen sections
- Hero banners
- Responsive typography
- Layouts that adapt to screen size

---

### vmin and vmax

- **vmin** = 1% of the smaller viewport dimension
- **vmax** = 1% of the larger viewport dimension

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .square-vmin {
            width: 50vmin;
            height: 50vmin;
            background-color: lightblue;
            margin: 20px;
        }
        
        .square-vmax {
            width: 30vmax;
            height: 30vmax;
            background-color: lightcoral;
            margin: 20px;
        }
    </style>
</head>
<body>
    <div class="square-vmin">
        Always square (50vmin)
    </div>
    
    <div class="square-vmax">
        Always square (30vmax)
    </div>
</body>
</html>
```

**When to use:**
- Creating perfect squares
- Responsive elements that maintain aspect ratio

---

## Unit Comparison Example

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        html {
            font-size: 16px;
        }
        
        .container {
            width: 800px;
            padding: 20px;
            background-color: #f0f0f0;
        }
        
        .box {
            margin: 10px 0;
            padding: 10px;
            background-color: white;
            border: 2px solid #333;
        }
        
        .px-box {
            width: 400px;
            font-size: 20px;
        }
        
        .percent-box {
            width: 50%;          /* 50% of 800px = 400px */
            font-size: 20px;
        }
        
        .em-box {
            width: 25em;         /* 25 × 16px = 400px */
            font-size: 1.25em;   /* 1.25 × 16px = 20px */
        }
        
        .rem-box {
            width: 25rem;        /* 25 × 16px = 400px */
            font-size: 1.25rem;  /* 1.25 × 16px = 20px */
        }
        
        .vw-box {
            width: 50vw;         /* 50% of viewport width */
            font-size: 2vw;      /* 2% of viewport width */
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="box px-box">Pixels: 400px width, 20px font</div>
        <div class="box percent-box">Percent: 50% width, 20px font</div>
        <div class="box em-box">Em: 25em width, 1.25em font</div>
        <div class="box rem-box">Rem: 25rem width, 1.25rem font</div>
        <div class="box vw-box">Viewport: 50vw width, 2vw font</div>
    </div>
</body>
</html>
```

---

## Which Unit to Use?

### Recommended Modern Approach

```css
/* Root font size */
html {
    font-size: 16px;
}

/* Font sizes - use rem */
h1 { font-size: 2.5rem; }      /* 40px */
h2 { font-size: 2rem; }        /* 32px */
p { font-size: 1rem; }         /* 16px */

/* Spacing - use rem */
.section {
    padding: 2rem;             /* 32px */
    margin: 1rem 0;            /* 16px 0 */
}

/* Widths - use % or vw */
.container {
    width: 90%;
    max-width: 1200px;
}

/* Borders - use px */
.box {
    border: 1px solid black;
}

/* Full screen - use vh/vw */
.hero {
    height: 100vh;
    width: 100vw;
}
```

### Quick Reference

| Property | Recommended Unit | Why |
|----------|------------------|-----|
| Font size | rem | Consistent, accessible |
| Padding/Margin | rem | Scales with font |
| Width (container) | % or max-width | Responsive |
| Width (full) | vw | Full viewport |
| Height (full) | vh | Full viewport |
| Border | px | Precise control |
| Box shadow | px | Precise control |
| Media queries | em or rem | Accessibility |

---

## Part 2: CSS Positioning

CSS positioning controls where elements appear on the page.

### Position Property Values

1. **static** (default)
2. **relative**
3. **absolute**
4. **fixed**
5. **sticky**

### Positioning Properties

Once position is set (except static), you can use:

```css
top: 10px;
right: 20px;
bottom: 30px;
left: 40px;
```

---

## Position: Static (Default)

Elements follow normal document flow. Top, right, bottom, left have NO effect.

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .box {
            width: 200px;
            height: 100px;
            background-color: lightblue;
            border: 2px solid navy;
            margin: 10px;
            position: static;  /* Default */
        }
    </style>
</head>
<body>
    <div class="box">Box 1 (static)</div>
    <div class="box">Box 2 (static)</div>
    <div class="box">Box 3 (static)</div>
</body>
</html>
```

**Result:** Elements stack normally, one after another

---

## Position: Relative

Element positioned relative to its NORMAL position.

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .box {
            width: 150px;
            height: 100px;
            background-color: lightblue;
            border: 2px solid navy;
            margin: 10px;
            display: inline-block;
        }
        
        .relative {
            position: relative;
            top: 20px;         /* Move down 20px */
            left: 30px;        /* Move right 30px */
            background-color: lightcoral;
        }
    </style>
</head>
<body>
    <div class="box">Box 1</div>
    <div class="box relative">Box 2 (relative)</div>
    <div class="box">Box 3</div>
</body>
</html>
```

**Key Points:**
- Moves from its normal position
- Original space is PRESERVED (other elements don't move)
- Can use top, right, bottom, left
- Often used as parent for absolute positioning

---

## Position: Absolute

Element positioned relative to its nearest POSITIONED ancestor (parent with position: relative/absolute/fixed).

If no positioned ancestor, it's relative to the document body.

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .container {
            position: relative;  /* Parent is positioned */
            width: 400px;
            height: 300px;
            background-color: lightgray;
            border: 2px solid black;
            margin: 50px;
        }
        
        .box {
            width: 100px;
            height: 80px;
            background-color: lightblue;
            border: 2px solid navy;
        }
        
        .absolute {
            position: absolute;
            background-color: lightcoral;
        }
        
        .top-left {
            top: 0;
            left: 0;
        }
        
        .top-right {
            top: 0;
            right: 0;
        }
        
        .bottom-left {
            bottom: 0;
            left: 0;
        }
        
        .bottom-right {
            bottom: 0;
            right: 0;
        }
        
        .center {
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="box absolute top-left">Top Left</div>
        <div class="box absolute top-right">Top Right</div>
        <div class="box absolute bottom-left">Bottom Left</div>
        <div class="box absolute bottom-right">Bottom Right</div>
        <div class="box absolute center">Center</div>
    </div>
</body>
</html>
```

**Key Points:**
- Removed from normal flow (doesn't take space)
- Positioned relative to nearest positioned parent
- Other elements act like it doesn't exist
- Perfect for overlays, tooltips, dropdowns

---

## Position: Fixed

Element positioned relative to the VIEWPORT (browser window). Stays in place when scrolling.

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        body {
            height: 2000px;  /* Make page scrollable */
            margin: 0;
            padding-top: 80px;
        }
        
        .header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 60px;
            background-color: #333;
            color: white;
            display: flex;
            align-items: center;
            padding: 0 20px;
            z-index: 1000;
        }
        
        .back-to-top {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 50px;
            height: 50px;
            background-color: #4CAF50;
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
        }
        
        .content {
            padding: 20px;
        }
    </style>
</head>
<body>
    <div class="header">
        Fixed Header - Scroll down to see effect
    </div>
    
    <div class="content">
        <h1>Scroll Down</h1>
        <p>Content here...</p>
        <p>More content...</p>
        <p>Keep scrolling...</p>
    </div>
    
    <div class="back-to-top">↑</div>
</body>
</html>
```

**Key Points:**
- Fixed to viewport, not page
- Stays in place when scrolling
- Removed from normal flow
- Perfect for headers, footers, floating buttons

---

## Position: Sticky

Element switches between relative and fixed based on scroll position.

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
        }
        
        .header {
            background-color: #333;
            color: white;
            padding: 20px;
            text-align: center;
        }
        
        .nav {
            position: sticky;
            top: 0;
            background-color: #4CAF50;
            padding: 15px;
            text-align: center;
            color: white;
            font-weight: bold;
            z-index: 100;
        }
        
        .section {
            padding: 20px;
            height: 500px;
        }
        
        .section:nth-child(odd) {
            background-color: #f0f0f0;
        }
    </style>
</head>
<body>
    <div class="header">
        <h1>Sticky Navigation Demo</h1>
        <p>Scroll down to see the navigation stick</p>
    </div>
    
    <div class="nav">
        Navigation Bar (Sticky)
    </div>
    
    <div class="section">Section 1</div>
    <div class="section">Section 2</div>
    <div class="section">Section 3</div>
    <div class="section">Section 4</div>
</body>
</html>
```

**Key Points:**
- Acts like relative until scroll threshold
- Then becomes fixed
- Perfect for navigation bars, table headers
- Requires top, bottom, left, or right value

---

## Z-Index (Stacking Order)

Controls which element appears on top when elements overlap.

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .box {
            width: 200px;
            height: 200px;
            position: absolute;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 24px;
            font-weight: bold;
        }
        
        .box1 {
            background-color: red;
            top: 50px;
            left: 50px;
            z-index: 1;
        }
        
        .box2 {
            background-color: blue;
            top: 100px;
            left: 100px;
            z-index: 3;  /* Highest, appears on top */
        }
        
        .box3 {
            background-color: green;
            top: 150px;
            left: 150px;
            z-index: 2;
        }
    </style>
</head>
<body>
    <div style="position: relative; height: 400px;">
        <div class="box box1">Z: 1</div>
        <div class="box box2">Z: 3</div>
        <div class="box box3">Z: 2</div>
    </div>
</body>
</html>
```

**Key Points:**
- Higher z-index = appears on top
- Only works on positioned elements (not static)
- Default z-index is 0
- Can be negative

---

## Practical Examples

### Example 1: Modal/Overlay

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1000;
        }
        
        .modal {
            position: relative;
            width: 90%;
            max-width: 500px;
            background-color: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
        }
        
        .close {
            position: absolute;
            top: 10px;
            right: 10px;
            width: 30px;
            height: 30px;
            background-color: #f44336;
            color: white;
            border: none;
            border-radius: 50%;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="overlay">
        <div class="modal">
            <button class="close">×</button>
            <h2>Modal Title</h2>
            <p>This is a modal dialog using fixed positioning.</p>
        </div>
    </div>
</body>
</html>
```

### Example 2: Card with Badge

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .card {
            position: relative;
            width: 300px;
            padding: 20px;
            margin: 50px;
            background-color: white;
            border: 1px solid #ddd;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        
        .badge {
            position: absolute;
            top: -10px;
            right: -10px;
            width: 40px;
            height: 40px;
            background-color: #f44336;
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
        }
        
        .ribbon {
            position: absolute;
            top: 20px;
            left: -10px;
            background-color: #4CAF50;
            color: white;
            padding: 5px 15px;
            font-size: 14px;
        }
    </style>
</head>
<body>
    <div class="card">
        <div class="badge">NEW</div>
        <div class="ribbon">SALE</div>
        <h3>Product Card</h3>
        <p>This card has absolutely positioned badges.</p>
    </div>
</body>
</html>
```

### Example 3: Sticky Sidebar

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
        }
        
        .container {
            display: flex;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .sidebar {
            width: 250px;
            padding: 20px;
            background-color: #f0f0f0;
        }
        
        .sidebar-content {
            position: sticky;
            top: 20px;
        }
        
        .main {
            flex: 1;
            padding: 20px;
        }
        
        .section {
            margin-bottom: 30px;
            padding: 20px;
            background-color: white;
            border: 1px solid #ddd;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="sidebar">
            <div class="sidebar-content">
                <h3>Navigation</h3>
                <ul>
                    <li>Section 1</li>
                    <li>Section 2</li>
                    <li>Section 3</li>
                    <li>Section 4</li>
                </ul>
            </div>
        </div>
        
        <div class="main">
            <div class="section"><h2>Section 1</h2><p>Content...</p></div>
            <div class="section"><h2>Section 2</h2><p>Content...</p></div>
            <div class="section"><h2>Section 3</h2><p>Content...</p></div>
            <div class="section"><h2>Section 4</h2><p>Content...</p></div>
        </div>
    </div>
</body>
</html>
```

---

## Position Comparison Table

| Position | Flow | Relative To | Scrolls | Use Case |
|----------|------|-------------|---------|----------|
| **static** | Normal | - | Yes | Default |
| **relative** | Normal (space preserved) | Self | Yes | Small adjustments, parent for absolute |
| **absolute** | Removed | Positioned parent | Yes | Overlays, tooltips, badges |
| **fixed** | Removed | Viewport | No | Headers, footers, floating buttons |
| **sticky** | Normal → Fixed | Viewport | Switches | Navigation bars, table headers |

---

## Best Practices

### ✅ Do This

1. Use rem for font sizes and spacing
2. Use % for responsive widths
3. Use vw/vh for full-screen sections
4. Use px for borders and small details
5. Use position: relative on parent for absolute children
6. Use z-index sparingly and systematically
7. Always set top/bottom/left/right with positioned elements

### ❌ Avoid This

1. Don't use em for everything (compounds)
2. Don't use px for font sizes (not accessible)
3. Don't forget to set position on parent for absolute
4. Don't use excessive z-index values (9999)
5. Don't use fixed positioning for everything
6. Don't forget sticky needs a threshold value

---

## Summary

### Units Quick Guide
- **px** - Precise, fixed measurements
- **%** - Relative to parent
- **rem** - Relative to root font (best for most cases)
- **em** - Relative to parent font (compounds)
- **vw/vh** - Relative to viewport

### Positioning Quick Guide
- **static** - Normal flow (default)
- **relative** - Offset from normal position
- **absolute** - Positioned relative to parent
- **fixed** - Fixed to viewport
- **sticky** - Relative until threshold, then fixed

---

## Practice Exercises

### Exercise 1: Responsive Card
Create a card that:
- Uses rem for padding and font sizes
- Uses % for width
- Has an absolutely positioned badge
- Is centered on the page

### Exercise 2: Fixed Header
Create a header that:
- Stays at top when scrolling
- Uses 100vw width
- Has z-index to stay on top
- Contains navigation links

### Exercise 3: Sticky Navigation
Create a navigation that:
- Starts below header
- Becomes sticky when scrolling
- Uses rem for spacing
- Has smooth transition

### Exercise 4: Modal Dialog
Create a modal that:
- Uses fixed positioning
- Centers with absolute positioning
- Has semi-transparent overlay
- Uses proper z-index

---

## Next Steps

In the next lesson, we'll learn about:
- Colors and backgrounds
- Gradients and shadows
- Text styling and fonts
- CSS transitions and animations

---

*Congratulations! You've completed CSS Day 4. You now understand CSS units and positioning for creating precise and responsive layouts!*
