# React Phase 1: Basics - Complete Guide

## Part 1: React Introduction

### What is React?

React is a front-end JavaScript library for building user interfaces. It was developed by Facebook Software Engineer Jordan Walke and is also known as React.js or ReactJS.

**Think of React as a tool that helps you build interactive websites by creating reusable UI components.**

### Key Facts

| Feature | Description |
|---------|-------------|
| Type | JavaScript Library |
| Purpose | Building UI Components |
| Created By | Jordan Walke (Facebook) |
| First Used | 2011 (Facebook Newsfeed) |
| Public Release | July 2013 (v0.3.0) |
| Latest Version | 19.0.0 (December 2024) |

---

## Part 2: How React Works

### The Virtual DOM

React creates a VIRTUAL DOM in memory instead of manipulating the browser's DOM directly.

### Visual: Virtual DOM Process

```
1. React creates Virtual DOM in memory
    ↓
2. React does all changes in Virtual DOM
    ↓
3. React compares Virtual DOM with Real DOM
    ↓
4. React updates ONLY what changed in Real DOM
```

### Why This Matters

React only changes what needs to be changed! This makes React applications fast and efficient.

**Example:**
```
If you change one button's text:
- Old way: Reload entire page
- React way: Update only that button
```

---

## Part 3: Prerequisites

Before learning React, you should understand:

✅ HTML - Structure of web pages
✅ CSS - Styling web pages
✅ JavaScript - Programming logic

If you need to learn these first, review the HTML, CSS, and JavaScript sections of this course.

---

## Part 4: Getting Started with React

### Step 1: Check Node.js Installation

First, make sure Node.js is installed. Open your terminal and run:

```bash
node -v
```

**Expected Output:**
```
v22.15.0
```

If you don't see a version number, you need to install Node.js from [nodejs.org](https://nodejs.org).

---

## Part 5: Install Build Tool (Vite)

### What is Vite?

Vite is a build tool that helps you create and run React applications quickly.

### Install Vite

Run this command in your terminal:

```bash
npm install -g create-vite
```

**Expected Output:**
```
added 1 package in 649ms
```

---

## Part 6: Create Your First React App

### Create Application

Run this command to create a React app named `my-react-app`:

```bash
npm create vite@latest my-react-app -- --template react
```

**You might see this message:**
```
Need to install the following packages: create-vite@6.5.0
Ok to proceed? (y)
```

Press `y` and Enter to continue.

**Expected Output:**
```
Scaffolding project in C:\Users\...\my-react-app...
Done. Now run:
  cd my-react-app
  npm install
  npm run dev
```

---

## Part 7: Install Dependencies

### Navigate to Your App

```bash
cd my-react-app
```

### Install Required Packages

```bash
npm install
```

**Expected Output:**
```
added 154 packages, and audited 155 packages in 8s
33 packages are looking for funding
  run `npm fund` for details
found 0 vulnerabilities
```

---

## Part 8: Run Your React App

### Start Development Server

```bash
npm run dev
```

**Expected Output:**
```
VITE v6.3.5  ready in 217 ms
➜ Local: http://localhost:5173/
➜ Network: use --host to expose
➜ press h + enter to show help
```

### View Your App

Open your browser and go to: `http://localhost:5173/`

You'll see the default React app running!

---

## Part 9: Your First React App - Hello World

### Project Structure

```
my-react-app/
├── src/
│   ├── App.jsx       ← Main component
│   └── main.jsx      ← Entry point
├── index.html        ← HTML container
└── package.json
```

### Default App.jsx

The default `src/App.jsx` file looks like this:

```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from '/vite.svg'
import './App.css'

function App() {
  const [count, setCount] = useState(0)

  return (
    <>
      <div>
        <a href="https://vitejs.dev" target="_blank">
          <img src={viteLogo} className="logo" alt="Vite logo" />
        </a>
        <a href="https://react.dev" target="_blank">
          <img src={reactLogo} className="logo react" alt="React logo" />
        </a>
      </div>
      <h1>Vite + React</h1>
      <div className="card">
        <button onClick={() => setCount((count) => count + 1)}>
          count is {count}
        </button>
        <p>
          Edit <code>src/App.jsx</code> and save to test HMR
        </p>
      </div>
      <p className="read-the-docs">
        Click on the Vite and React logos to learn more
      </p>
    </>
  )
}

export default App
```

---

## Part 10: Modify Your First React App

### Replace App.jsx Content

Open `src/App.jsx` and replace ALL content with:

```jsx
function App() {
  return (
    <div className="App">
      <h1>Hello World!</h1>
    </div>
  );
}

export default App;
```

### Save and See Changes

When you save the file, the browser automatically updates! You'll see:

```
Hello World!
```

**No need to reload the browser!** This is called Hot Module Replacement (HMR).

---

## Part 11: React Render HTML

### How React Renders HTML

React renders HTML to a web page using:
1. A container (HTML element)
2. The `createRoot()` function

### Visual: Rendering Process

```
index.html (Container)
    ↓
<div id="root"></div>
    ↓
main.jsx (createRoot)
    ↓
Renders React Component
    ↓
Displays in Browser
```

---

## Part 12: The Container

### index.html File

The default `index.html` in your project root:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite + React</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
```

### Simplified Version

For learning, we can simplify it to:

```html
<!doctype html>
<html lang="en">
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
```

**Key Element:** `<div id="root"></div>` - This is where React renders your app!

---

## Part 13: The createRoot Function

### main.jsx File

The default `src/main.jsx` file:

```jsx
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import App from './App.jsx'

createRoot(document.getElementById('root')).render(
  <StrictMode>
    <App />
  </StrictMode>
)
```

### What createRoot Does

```javascript
createRoot(document.getElementById('root'))
```

- Takes an HTML element as argument
- Defines WHERE React component should display
- Creates a "root" for your React app

---

## Part 14: Simplified Example

### Basic Hello React

Simplify `src/main.jsx` to:

```jsx
import { createRoot } from 'react-dom/client'

createRoot(document.getElementById('root')).render(
  <h1>Hello React!</h1>
)
```

**Result in browser:**
```
Hello React!
```

---

## Part 15: The render Method

### What is render()?

The `render()` method defines WHAT to display in the HTML container.

### Example: Render a Paragraph

```jsx
import { createRoot } from 'react-dom/client'

createRoot(document.getElementById('root')).render(
  <p>Welcome!</p>
)
```

**Result:**
```
Welcome!
```

The content is displayed inside `<div id="root">`.

---

## Part 16: HTML in JavaScript (JSX)

### What is JSX?

JSX allows you to write HTML tags inside JavaScript code.

### Example: Variable with HTML

```jsx
import { createRoot } from 'react-dom/client'

const myelement = (
  <table>
    <tr>
      <th>Name</th>
    </tr>
    <tr>
      <td>John</td>
    </tr>
    <tr>
      <td>Elsa</td>
    </tr>
  </table>
);

createRoot(document.getElementById('root')).render(
  myelement
)
```

**Result:**
```
Name
John
Elsa
```

Don't worry about JSX syntax yet - we'll learn it in Phase 2!

---

## Part 17: The Root Node

### What is a Root Node?

The root node is the HTML element where React displays content. It's like a container managed by React.

### Important Facts

| Fact | Description |
|------|-------------|
| Element Type | Can be any HTML element (div, header, main, etc.) |
| ID Name | Can be any name (not just "root") |
| Convention | "root" is standard but not required |

### Example: Different Root Element

**index.html:**
```html
<!doctype html>
<html lang="en">
  <body>
    <header id="sandy"></header>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
```

**main.jsx:**
```jsx
import { createRoot } from 'react-dom/client'

createRoot(document.getElementById('sandy')).render(
  <h1>Hello from Sandy!</h1>
)
```

This works perfectly! The ID can be anything you want.

---

## Part 18: Key Concepts Summary

### React Basics

1. **React** is a JavaScript library for building UIs
2. **Virtual DOM** makes React fast and efficient
3. **Node.js** is required to run React
4. **Vite** is the build tool we use
5. **npm** manages packages and dependencies

### File Structure

```
my-react-app/
├── index.html          ← Container with root element
├── src/
│   ├── main.jsx        ← Entry point, uses createRoot()
│   └── App.jsx         ← Main component
```

### Core Functions

```jsx
// Create root and render
createRoot(document.getElementById('root')).render(
  <YourContent />
)
```

---

## Part 19: Quick Reference

### Commands

```bash
# Check Node.js version
node -v

# Install Vite
npm install -g create-vite

# Create React app
npm create vite@latest my-react-app -- --template react

# Navigate to app
cd my-react-app

# Install dependencies
npm install

# Run development server
npm run dev
```

### Basic React Structure

```jsx
// main.jsx
import { createRoot } from 'react-dom/client'

createRoot(document.getElementById('root')).render(
  <h1>Your Content Here</h1>
)
```

```jsx
// App.jsx
function App() {
  return (
    <div>
      <h1>Hello World!</h1>
    </div>
  );
}

export default App;
```

---

## What's Next?

In Phase 2, we'll learn about:

### Coming Up: Phase 2 - JSX

- What is JSX?
- JSX Expressions
- JSX Attributes
- JSX Conditional Statements

---

*Congratulations! You've completed React Phase 1: Basics. You now understand how React works and how to create your first React application!*

---

**Keep practicing and see you in Phase 2!** ⚛️
