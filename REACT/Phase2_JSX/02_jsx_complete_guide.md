# React Phase 2: JSX - Complete Guide

## Part 1: What is JSX?

### JSX Definition

JSX stands for JavaScript XML. It allows us to write HTML directly in React code.

**Think of JSX as a way to write HTML inside JavaScript - making React code easier to read and write.**

### Key Facts

| Feature | Description |
|---------|-------------|
| Full Name | JavaScript XML |
| Purpose | Write HTML in React |
| Benefit | Easier to write React applications |
| Based On | ES6 JavaScript |
| Converted To | Regular JavaScript at runtime |

---

## Part 2: JSX vs Without JSX

### With JSX (Easy Way)

```jsx
const myElement = <h1>I Love JSX!</h1>;

createRoot(document.getElementById('root')).render(
  myElement
);
```

### Without JSX (Hard Way)

```jsx
const myElement = React.createElement('h1', {}, 'I do not use JSX!');

createRoot(document.getElementById('root')).render(
  myElement
);
```

### Visual: JSX Advantage

```
With JSX:
<h1>Hello</h1>  ← Looks like HTML, easy to read

Without JSX:
React.createElement('h1', {}, 'Hello')  ← Complex, hard to read
```

**JSX makes React code much easier to write and understand!**

---

## Part 3: JSX Expressions

### Using Curly Braces { }

You can write JavaScript expressions inside JSX using curly braces `{ }`.

### Example: Math Expression

```jsx
const myElement = <h1>React is {5 + 5} times better with JSX</h1>;
```

**Result:**
```
React is 10 times better with JSX
```

### How It Works

```
JSX sees { }
    ↓
Evaluates JavaScript inside
    ↓
Replaces { } with result
    ↓
Displays in browser
```

---

## Part 4: Multiple Lines of HTML

### Using Parentheses

To write HTML on multiple lines, wrap it in parentheses `( )`:

```jsx
const myElement = (
  <ul>
    <li>Apples</li>
    <li>Bananas</li>
    <li>Cherries</li>
  </ul>
);
```

**Result:**
```
• Apples
• Bananas
• Cherries
```

---

## Part 5: One Top Level Element Rule

### The Rule

HTML code must be wrapped in ONE top level element.

### Wrong ❌

```jsx
const myElement = (
  <p>I am a paragraph.</p>
  <p>I am a paragraph too.</p>
);
```

This will cause an error!

### Correct ✅ - Using div

```jsx
const myElement = (
  <div>
    <p>I am a paragraph.</p>
    <p>I am a paragraph too.</p>
  </div>
);
```

### Correct ✅ - Using Fragment

```jsx
const myElement = (
  <>
    <p>I am a paragraph.</p>
    <p>I am a paragraph too.</p>
  </>
);
```

### What is a Fragment?

A fragment `<>...</>` is an empty HTML tag that wraps elements without adding extra nodes to the DOM.

**Use fragments when you don't want an extra div in your HTML!**

---

## Part 6: Elements Must Be Closed

### XML Rules

JSX follows XML rules - all elements must be properly closed.

### Self-Closing Tags

```jsx
// Correct ✅
const myElement = <input type="text" />;

// Wrong ❌
const myElement = <input type="text">;
```

### Visual: Closing Tags

```
HTML (allows):
<input type="text">  ← No closing needed

JSX (requires):
<input type="text" />  ← Must close with />
```

---

## Part 7: className Instead of class

### The Problem

`class` is a reserved word in JavaScript, so you cannot use it in JSX.

### The Solution

Use `className` instead of `class`:

```jsx
// Correct ✅
const myElement = <h1 className="myclass">Hello World</h1>;

// Wrong ❌
const myElement = <h1 class="myclass">Hello World</h1>;
```

### How It Works

```
You write: className="myclass"
    ↓
JSX converts to: class="myclass"
    ↓
Browser sees: <h1 class="myclass">Hello World</h1>
```

---

## Part 8: Comments in JSX

### JSX Comment Syntax

```jsx
const myElement = <h1>Hello {/* Wonderful */} World</h1>;
```

**Result:**
```
Hello World
```

The comment `{/* Wonderful */}` is not displayed.

### Comment Format

```jsx
{/* Your comment here */}
```

Must be inside curly braces with `/* */`!

---

## Part 9: JSX in React Components

### What are Components?

Components are independent, reusable pieces of code that return HTML.

### Basic Component

```jsx
function Car() {
  return (
    <>
      <h2>My Car</h2>
      <p>It is a Ford Mustang.</p>
    </>
  );
}

createRoot(document.getElementById('root')).render(
  <Car />
);
```

**Result:**
```
My Car
It is a Ford Mustang.
```

### Component with Logic

```jsx
function Car() {
  const brand = "Ford";
  const model = "Mustang";
  
  return (
    <>
      <h2>My Car</h2>
      <p>It is a {brand} {model}.</p>
    </>
  );
}

createRoot(document.getElementById('root')).render(
  <Car />
);
```

**Result:**
```
My Car
It is a Ford Mustang.
```

---

## Part 10: JSX Expressions - Variables

### Using Variables

You can use variables inside JSX with curly braces:

```jsx
function Car() {
  const hp = 218 * 1.36;
  
  return (
    <>
      <h1>My car</h1>
      <p>It has {hp} horsepower</p>
    </>
  );
}
```

**Result:**
```
My car
It has 296.48 horsepower
```

---

## Part 11: JSX Expressions - Math Operations

### Direct Calculations

```jsx
function Car() {
  return (
    <>
      <h1>My car</h1>
      <p>It has {218 * 1.36} horsepower</p>
    </>
  );
}
```

**Result:**
```
My car
It has 296.48 horsepower
```

---

## Part 12: JSX Expressions - Function Calls

### Calling Functions

```jsx
function kwtohp(kw) {
  return kw * 1.36;
}

function Car() {
  return (
    <>
      <h1>My car</h1>
      <p>It has {kwtohp(218)} horsepower</p>
    </>
  );
}
```

**Result:**
```
My car
It has 296.48 horsepower
```

---

## Part 13: JSX Expressions - Object Properties

### Accessing Object Properties

```jsx
function Car() {
  const myobj = {
    name: "Fiat",
    model: "500",
    color: "white"
  };
  
  return (
    <>
      <h1>My car is a {myobj.color} {myobj.name} {myobj.model}</h1>
    </>
  );
}
```

**Result:**
```
My car is a white Fiat 500
```

---

## Part 14: JSX Attributes - className

### Using className

```jsx
function Car() {
  return (
    <h1 className="myclass">Hello World</h1>
  );
}
```

This creates:
```html
<h1 class="myclass">Hello World</h1>
```

---

## Part 15: JSX Attributes - Dynamic Values

### Expressions as Attributes

```jsx
function Car() {
  const x = "myclass";
  
  return (
    <h1 className={x}>Hello World</h1>
  );
}
```

### Important Rule

```jsx
// Correct ✅ - No quotes around { }
<h1 className={x}>Hello World</h1>

// Wrong ❌ - Quotes make it a string
<h1 className="{x}">Hello World</h1>
```

**Don't use quotes when using expressions!**

---

## Part 16: JSX Attributes - Event Handlers

### camelCase Event Names

Event attributes in JSX use camelCase:

```jsx
function Car() {
  const myfunc = () => {
    alert('Hello World');
  };
  
  return (
    <button onClick={myfunc}>Click me</button>
  );
}
```

### Common Events

| HTML | JSX |
|------|-----|
| `onclick` | `onClick` |
| `onchange` | `onChange` |
| `onsubmit` | `onSubmit` |
| `onmouseover` | `onMouseOver` |

---

## Part 17: JSX Attributes - Boolean Values

### Boolean Attributes

```jsx
// True (button is disabled)
<button onClick={myfunc} disabled>Click me</button>

// Also true (button is disabled)
<button onClick={myfunc} disabled={true}>Click me</button>

// False (button is NOT disabled)
<button onClick={myfunc} disabled={false}>Click me</button>
```

### Visual: Boolean Attributes

```
disabled          → true (disabled)
disabled={true}   → true (disabled)
disabled={false}  → false (NOT disabled)
```

---

## Part 18: JSX Attributes - Style

### Style as Object

The `style` attribute accepts a JavaScript object with camelCase CSS properties:

```jsx
function Car() {
  const mystyles = {
    color: "red",
    fontSize: "20px",
    backgroundColor: "lightyellow"
  };
  
  return (
    <>
      <h1 style={mystyles}>My car</h1>
    </>
  );
}
```

### Important Differences

| CSS | JSX Style |
|-----|-----------|
| `font-size` | `fontSize` |
| `background-color` | `backgroundColor` |
| `border-radius` | `borderRadius` |
| String value | Object with camelCase |

### Example Comparison

```css
/* CSS */
h1 {
  font-size: 20px;
  background-color: lightyellow;
}
```

```jsx
/* JSX */
const mystyles = {
  fontSize: "20px",
  backgroundColor: "lightyellow"
};
```

---

## Part 19: Conditional Rendering - if Statements

### Option 1: if Outside JSX

```jsx
function Fruit() {
  const x = 5;
  let y = "Apple";
  
  if (x < 10) {
    y = "Banana";
  }
  
  return (
    <h1>{y}</h1>
  );
}
```

**Result:**
```
Banana
```

### Why Outside?

if statements cannot be used directly inside JSX. They must be outside the return statement.

---

## Part 20: Conditional Rendering - Ternary Operator

### Option 2: Ternary Inside JSX

```jsx
function Fruit() {
  const x = 5;
  
  return (
    <h1>{(x) < 10 ? "Banana" : "Apple"}</h1>
  );
}
```

**Result:**
```
Banana
```

### Ternary Syntax

```jsx
{condition ? valueIfTrue : valueIfFalse}
```

### Visual: Ternary Flow

```
x < 10 ?
    ↓
   Yes → "Banana"
    ↓
   No → "Apple"
```

### More Examples

```jsx
// Example 1: Show message based on condition
function Greeting() {
  const isLoggedIn = true;
  
  return (
    <h1>{isLoggedIn ? "Welcome back!" : "Please log in"}</h1>
  );
}

// Example 2: Show number or text
function Status() {
  const count = 5;
  
  return (
    <p>{count > 0 ? `You have ${count} messages` : "No messages"}</p>
  );
}
```

---

## Part 21: Key Concepts Summary

### JSX Rules

1. ✅ Write HTML in JavaScript
2. ✅ Use `{ }` for expressions
3. ✅ Wrap multiple lines in `( )`
4. ✅ One top level element (or fragment)
5. ✅ Close all elements with `/>`
6. ✅ Use `className` instead of `class`
7. ✅ Comments: `{/* comment */}`

### JSX Expressions

```jsx
{5 + 5}              // Math
{variable}           // Variables
{myFunction()}       // Function calls
{object.property}    // Object properties
```

### JSX Attributes

```jsx
className={value}    // Dynamic class
onClick={handler}    // Event handler
disabled={true}      // Boolean
style={styleObject}  // Style object
```

### Conditional Rendering

```jsx
// Outside JSX
if (condition) {
  value = "A";
}

// Inside JSX
{condition ? "A" : "B"}
```

---

## Part 22: Quick Reference

### Basic JSX

```jsx
// Simple element
const element = <h1>Hello</h1>;

// With expression
const element = <h1>Result: {5 + 5}</h1>;

// Multiple lines
const element = (
  <div>
    <h1>Title</h1>
    <p>Paragraph</p>
  </div>
);

// Fragment
const element = (
  <>
    <h1>Title</h1>
    <p>Paragraph</p>
  </>
);
```

### JSX in Components

```jsx
function MyComponent() {
  const name = "John";
  const age = 25;
  
  return (
    <>
      <h1>Hello {name}</h1>
      <p>You are {age} years old</p>
    </>
  );
}
```

### Conditional JSX

```jsx
function MyComponent() {
  const isActive = true;
  
  return (
    <h1>{isActive ? "Active" : "Inactive"}</h1>
  );
}
```

### Styled JSX

```jsx
function MyComponent() {
  const styles = {
    color: "blue",
    fontSize: "20px"
  };
  
  return (
    <h1 style={styles} className="title">Hello</h1>
  );
}
```

---

## What's Next?

In Phase 3, we'll learn about:

### Coming Up: Phase 3 - Components

- Creating Components
- Using Props
- Props Destructuring
- Props Children

---

*Congratulations! You've completed React Phase 2: JSX. You now understand how to write HTML in React using JSX!*

---

**Keep practicing and see you in Phase 3!** ⚛️
