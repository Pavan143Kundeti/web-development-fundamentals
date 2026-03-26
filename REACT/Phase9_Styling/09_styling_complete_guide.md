# React Phase 9: Styling - Complete Guide

## Part 1: Styling Methods in React

### Three Common Ways

React offers multiple ways to style components:

| Method | Description |
|--------|-------------|
| Inline Styling | Style attribute with JavaScript object |
| CSS Stylesheets | External .css files |
| CSS Modules | Scoped CSS files |

**We'll cover all three methods in this guide.**

---

## Part 2: Inline Styling Basics

### Inline Style Syntax

In React, inline styles use a JavaScript object:

```jsx
const Header = () => {
  return (
    <>
      <h1 style={{color: "red"}}>Hello Style!</h1>
      <p>Add a little style!</p>
    </>
  );
}
```

**Result:** Text appears in red.

### Why Double Curly Braces?

```jsx
style={{color: "red"}}
```

```
Outer braces { } → JSX expression
Inner braces { } → JavaScript object
```

---

## Part 3: camelCase Property Names

### CSS vs React Syntax

CSS properties with hyphens must use camelCase in React:

| CSS | React |
|-----|-------|
| `background-color` | `backgroundColor` |
| `font-size` | `fontSize` |
| `border-radius` | `borderRadius` |
| `margin-top` | `marginTop` |

### Example

```jsx
const Header = () => {
  return (
    <>
      <h1 style={{backgroundColor: "lightblue"}}>Hello Style!</h1>
      <p>Add a little style!</p>
    </>
  );
}
```

---

## Part 4: Style Objects

### Creating Style Object

Instead of inline, create a style object:

```jsx
const Header = () => {
  const myStyle = {
    color: "white",
    backgroundColor: "DodgerBlue",
    padding: "10px",
    fontFamily: "Sans-Serif"
  };
  
  return (
    <>
      <h1 style={myStyle}>Hello Style!</h1>
      <p>Add a little style!</p>
    </>
  );
}
```

### Benefits

- Reusable styles
- Cleaner JSX
- Easier to read

---

## Part 5: Multiple Style Objects

### Combining Styles

```jsx
const Header = () => {
  const baseStyle = {
    padding: "10px",
    fontFamily: "Sans-Serif"
  };
  
  const headingStyle = {
    ...baseStyle,
    color: "white",
    backgroundColor: "DodgerBlue"
  };
  
  const paragraphStyle = {
    ...baseStyle,
    color: "gray"
  };
  
  return (
    <>
      <h1 style={headingStyle}>Hello Style!</h1>
      <p style={paragraphStyle}>Add a little style!</p>
    </>
  );
}
```

---

## Part 6: Dynamic Inline Styles

### Conditional Styling

```jsx
function Button({ isPrimary }) {
  const buttonStyle = {
    backgroundColor: isPrimary ? "blue" : "gray",
    color: "white",
    padding: "10px 20px",
    border: "none",
    borderRadius: "5px"
  };
  
  return <button style={buttonStyle}>Click me</button>;
}
```

---

## Part 7: CSS Stylesheets

### External CSS File

Create a separate CSS file:

**MyStylesheet.css:**
```css
body {
  background-color: #282c34;
  color: white;
  padding: 40px;
  font-family: Sans-Serif;
  text-align: center;
}
```

### Import CSS File

**index.js:**
```jsx
import { createRoot } from 'react-dom/client';
import './MyStylesheet.css';

const Header = () => {
  return (
    <>
      <h1>Hello Style!</h1>
      <p>Add a little style!</p>
    </>
  );
}

createRoot(document.getElementById('root')).render(
  <Header />
);
```

---

## Part 8: Using CSS Classes

### CSS File with Classes

**styles.css:**
```css
.header {
  color: blue;
  font-size: 24px;
}

.button {
  background-color: green;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
}
```

### Apply Classes

```jsx
import './styles.css';

function MyComponent() {
  return (
    <>
      <h1 className="header">Hello</h1>
      <button className="button">Click</button>
    </>
  );
}
```

**Remember:** Use `className`, not `class`!

---

## Part 9: CSS Modules Introduction

### What are CSS Modules?

CSS Modules are CSS files where class names are scoped locally by default.

### Benefits

- No naming conflicts
- Component-specific styles
- Automatic unique class names

### File Naming

```
Regular CSS: styles.css
CSS Module: styles.module.css
```

---

## Part 10: Creating CSS Modules

### CSS Module File

**my-style.module.css:**
```css
.bigred {
  color: Tomato;
  padding: 40px;
  font-family: Sans-Serif;
  text-align: center;
}
```

### Import and Use

**index.jsx:**
```jsx
import { createRoot } from 'react-dom/client';
import styles from './my-style.module.css';

const Car = () => {
  return <h1 className={styles.bigred}>Hello Car!</h1>;
}

createRoot(document.getElementById('root')).render(
  <Car />
);
```

---

## Part 11: CSS Modules Syntax

### How It Works

```jsx
import styles from './my-style.module.css';

<h1 className={styles.bigred}>Hello</h1>
```

### Visual: CSS Modules

```
CSS file: .bigred { color: red; }
    ↓
Import: import styles from './file.module.css'
    ↓
Use: className={styles.bigred}
    ↓
Renders: <h1 class="bigred_abc123">Hello</h1>
```

**React adds unique suffix to prevent conflicts!**

---

## Part 12: Multiple Classes in CSS Modules

### Multiple Classes

**styles.module.css:**
```css
.card {
  border: 1px solid #ddd;
  padding: 20px;
}

.title {
  color: blue;
  font-size: 24px;
}

.content {
  color: gray;
}
```

### Using Multiple Classes

```jsx
import styles from './styles.module.css';

function Card() {
  return (
    <div className={styles.card}>
      <h2 className={styles.title}>Title</h2>
      <p className={styles.content}>Content</p>
    </div>
  );
}
```

---

## Part 13: Combining Classes

### Multiple Classes on One Element

```jsx
import styles from './styles.module.css';

function Button() {
  return (
    <button className={`${styles.button} ${styles.primary}`}>
      Click me
    </button>
  );
}
```

### With Conditional Classes

```jsx
function Button({ isPrimary }) {
  const buttonClass = isPrimary 
    ? `${styles.button} ${styles.primary}` 
    : `${styles.button} ${styles.secondary}`;
  
  return <button className={buttonClass}>Click me</button>;
}
```

---

## Part 14: Comparing Styling Methods

### When to Use Each

| Method | Best For |
|--------|----------|
| Inline Styles | Dynamic styles, small components |
| CSS Stylesheets | Global styles, simple projects |
| CSS Modules | Component-specific styles, large projects |

### Inline Styles

```jsx
// Good for dynamic values
<div style={{width: `${progress}%`}}>
```

### CSS Stylesheets

```jsx
// Good for global styles
import './global.css';
```

### CSS Modules

```jsx
// Good for component isolation
import styles from './Button.module.css';
```

---

## Part 15: Key Concepts Summary

### Inline Styling

```jsx
// Direct inline
<h1 style={{color: "red", fontSize: "20px"}}>Hello</h1>

// Style object
const myStyle = {color: "red", fontSize: "20px"};
<h1 style={myStyle}>Hello</h1>
```

### CSS Stylesheets

```jsx
// Import CSS
import './styles.css';

// Use className
<h1 className="header">Hello</h1>
```

### CSS Modules

```jsx
// Import module
import styles from './styles.module.css';

// Use styles object
<h1 className={styles.header}>Hello</h1>
```

---

## Part 16: Quick Reference

### Inline Styles

```jsx
function Component() {
  const style = {
    color: "blue",
    backgroundColor: "lightgray",
    padding: "10px",
    borderRadius: "5px"
  };
  
  return <div style={style}>Content</div>;
}
```

### CSS Stylesheet

**styles.css:**
```css
.container {
  padding: 20px;
}

.title {
  color: blue;
}
```

**Component:**
```jsx
import './styles.css';

function Component() {
  return (
    <div className="container">
      <h1 className="title">Title</h1>
    </div>
  );
}
```

### CSS Module

**styles.module.css:**
```css
.container {
  padding: 20px;
}

.title {
  color: blue;
}
```

**Component:**
```jsx
import styles from './styles.module.css';

function Component() {
  return (
    <div className={styles.container}>
      <h1 className={styles.title}>Title</h1>
    </div>
  );
}
```

---

## Part 17: Common Patterns

### Conditional Styling

```jsx
function Alert({ type }) {
  const alertStyle = {
    padding: "10px",
    borderRadius: "5px",
    backgroundColor: type === "error" ? "red" : "green",
    color: "white"
  };
  
  return <div style={alertStyle}>Alert message</div>;
}
```

### Hover Effects (CSS Module)

**Button.module.css:**
```css
.button {
  background-color: blue;
  color: white;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
}

.button:hover {
  background-color: darkblue;
}
```

**Button.jsx:**
```jsx
import styles from './Button.module.css';

function Button() {
  return <button className={styles.button}>Hover me</button>;
}
```

---

## Part 18: Best Practices

### 1. Use camelCase for Inline Styles

```jsx
// Correct ✅
style={{backgroundColor: "blue"}}

// Wrong ❌
style={{"background-color": "blue"}}
```

### 2. Use className, Not class

```jsx
// Correct ✅
<div className="container">

// Wrong ❌
<div class="container">
```

### 3. CSS Modules for Components

```jsx
// Good ✅ - Scoped styles
import styles from './Button.module.css';
<button className={styles.primary}>Click</button>

// Avoid ❌ - Global conflicts
import './Button.css';
<button className="primary">Click</button>
```

### 4. Keep Styles Organized

```
src/
  components/
    Button/
      Button.jsx
      Button.module.css
    Card/
      Card.jsx
      Card.module.css
```

---

## Part 19: Complete Example

### Component with All Methods

```jsx
import { useState } from 'react';
import styles from './Example.module.css';
import './global.css';

function Example() {
  const [isActive, setIsActive] = useState(false);
  
  // Inline style object
  const inlineStyle = {
    padding: "10px",
    margin: "5px"
  };
  
  return (
    <div className="global-container">
      {/* Inline style */}
      <h1 style={{color: "blue"}}>Inline Style</h1>
      
      {/* Style object */}
      <p style={inlineStyle}>Style Object</p>
      
      {/* CSS Module */}
      <div className={styles.card}>
        <h2 className={styles.title}>CSS Module</h2>
      </div>
      
      {/* Dynamic inline style */}
      <button 
        style={{
          backgroundColor: isActive ? "green" : "gray",
          color: "white",
          padding: "10px"
        }}
        onClick={() => setIsActive(!isActive)}
      >
        Toggle
      </button>
    </div>
  );
}

export default Example;
```

---

## Part 20: Summary

### Three Styling Methods

1. **Inline Styles** - JavaScript objects, dynamic values
2. **CSS Stylesheets** - External files, global styles
3. **CSS Modules** - Scoped styles, no conflicts

### Key Points

- Use `style={{}}` for inline styles
- Use camelCase for CSS properties
- Use `className` instead of `class`
- CSS Modules use `.module.css` extension
- Import CSS Modules as objects

---

*Congratulations! You've completed React Phase 9: Styling. You now understand all three methods of styling React components!*

---

**You've completed all 9 phases of the React course! Keep building amazing React applications!** ⚛️🎉
