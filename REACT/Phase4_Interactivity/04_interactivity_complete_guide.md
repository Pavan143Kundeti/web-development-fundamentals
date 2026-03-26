# React Phase 4: Interactivity - Complete Guide

## Part 1: React Events Introduction

### What are Events?

Events are actions that happen in your application, like clicking a button, typing in a text box, or moving the mouse.

**Think of events as ways to make your React app respond to user actions.**

### Key Facts

| Feature | Description |
|---------|-------------|
| Purpose | Respond to user actions |
| Types | Click, change, mouseover, etc. |
| Syntax | camelCase (onClick, onChange) |
| Handler | Written inside curly braces |

### React vs HTML Events

| HTML | React |
|------|-------|
| `onclick` | `onClick` |
| `onchange` | `onChange` |
| `onmouseover` | `onMouseOver` |
| `onclick="shoot()"` | `onClick={shoot}` |

---

## Part 2: Adding Events

### Event Syntax

React events use camelCase and curly braces:

```jsx
// HTML way
<button onclick="shoot()">Take the Shot!</button>

// React way
<button onClick={shoot}>Take the Shot!</button>
```

### Example: Click Event

```jsx
function Football() {
  const shoot = () => {
    alert("Great Shot!");
  }
  
  return (
    <button onClick={shoot}>Take the shot!</button>
  );
}

createRoot(document.getElementById('root')).render(
  <Football />
);
```

**Result:** When you click the button, an alert shows "Great Shot!"

### Visual: Event Flow

```
User clicks button
    ↓
onClick={shoot} triggers
    ↓
shoot function runs
    ↓
alert("Great Shot!") displays
```

---

## Part 3: Event Handler Rules

### Important Rules

1. Use camelCase for event names
2. Pass function reference, not function call
3. Wrap handler in curly braces

### Correct vs Wrong

```jsx
// Correct ✅
<button onClick={shoot}>Click</button>

// Wrong ❌ - calls function immediately
<button onClick={shoot()}>Click</button>

// Wrong ❌ - lowercase
<button onclick={shoot}>Click</button>

// Wrong ❌ - quotes instead of braces
<button onClick="shoot">Click</button>
```

---

## Part 4: Passing Arguments to Events

### Using Arrow Functions

To pass arguments to an event handler, use an arrow function:

```jsx
function Football() {
  const shoot = (a) => {
    alert(a);
  }
  
  return (
    <button onClick={() => shoot("Goal!")}>Take the shot!</button>
  );
}

createRoot(document.getElementById('root')).render(
  <Football />
);
```

**Result:** When you click the button, an alert shows "Goal!"

### Why Arrow Function?

```jsx
// Without arrow function - calls immediately ❌
<button onClick={shoot("Goal!")}>Click</button>

// With arrow function - calls on click ✅
<button onClick={() => shoot("Goal!")}>Click</button>
```

### Visual: Arrow Function Flow

```
<button onClick={() => shoot("Goal!")}>
    ↓
User clicks
    ↓
Arrow function runs
    ↓
shoot("Goal!") is called
    ↓
alert("Goal!") displays
```

---

## Part 5: Event Object

### Accessing Event Object

Event handlers automatically receive the event object:

```jsx
function Football() {
  const shoot = (a, b) => {
    alert(b.type);
    // 'b' is the React event object
    // b.type will be 'click'
  }
  
  return (
    <button onClick={(event) => shoot("Goal!", event)}>Take the shot!</button>
  );
}

createRoot(document.getElementById('root')).render(
  <Football />
);
```

**Result:** Alert shows "click"

### Event Object Properties

| Property | Description |
|----------|-------------|
| `event.type` | Type of event (click, change, etc.) |
| `event.target` | Element that triggered event |
| `event.target.value` | Value of input element |
| `event.preventDefault()` | Prevent default behavior |

---

## Part 6: Common Event Types

### Mouse Events

```jsx
function EventExamples() {
  return (
    <div>
      <button onClick={() => alert('Clicked!')}>
        onClick
      </button>
      
      <button onDoubleClick={() => alert('Double clicked!')}>
        onDoubleClick
      </button>
      
      <div onMouseOver={() => console.log('Mouse over!')}>
        onMouseOver
      </div>
      
      <div onMouseOut={() => console.log('Mouse out!')}>
        onMouseOut
      </div>
    </div>
  );
}
```

### Form Events

```jsx
function FormEvents() {
  return (
    <div>
      <input onChange={(e) => console.log(e.target.value)} />
      
      <form onSubmit={(e) => e.preventDefault()}>
        <button type="submit">Submit</button>
      </form>
      
      <input onFocus={() => console.log('Focused!')} />
      
      <input onBlur={() => console.log('Lost focus!')} />
    </div>
  );
}
```

---

## Part 7: React Hooks Introduction

### What are Hooks?

Hooks are functions that let you use React features in function components.

**Think of Hooks as special tools that give your components superpowers.**

### Key Facts

| Feature | Description |
|---------|-------------|
| Purpose | Add React features to function components |
| Naming | Always start with "use" (useState, useEffect) |
| Where | Only in function components |
| When | At the top level of component |

### Hook Rules

```
✅ DO:
- Call Hooks inside function components
- Call Hooks at the top level
- Call Hooks in the same order every time

❌ DON'T:
- Call Hooks in class components
- Call Hooks inside conditions
- Call Hooks inside loops
```

---

## Part 8: useState Hook Introduction

### What is useState?

`useState` is a Hook that lets you add state to function components.

**State is data that can change over time in your component.**

### Basic Concept

```
State = Data that changes
useState = Tool to manage changing data
```

### Visual: State Example

```
Initial State: color = "red"
    ↓
User clicks button
    ↓
State Updates: color = "blue"
    ↓
Component re-renders with new color
```

---

## Part 9: Import useState

### Importing useState

Before using useState, you must import it:

```jsx
import { useState } from "react";
```

### Why Curly Braces?

```jsx
// Named export - needs curly braces
import { useState } from "react";

// Default export - no curly braces
import React from "react";
```

---

## Part 10: Initialize useState

### useState Syntax

```jsx
const [state, setState] = useState(initialValue);
```

### Breaking It Down

```jsx
const [color, setColor] = useState("red");
```

| Part | Description |
|------|-------------|
| `color` | Current state value |
| `setColor` | Function to update state |
| `useState("red")` | Initialize state to "red" |
| `[color, setColor]` | Array destructuring |

### Example: Initialize State

```jsx
import { useState } from "react";

function FavoriteColor() {
  const [color, setColor] = useState("red");
  
  // color = "red"
  // setColor = function to update color
}
```

---

## Part 11: Read State

### Using State in Component

```jsx
import { useState } from 'react';
import { createRoot } from 'react-dom/client';

function FavoriteColor() {
  const [color, setColor] = useState("red");
  
  return <h1>My favorite color is {color}!</h1>
}

createRoot(document.getElementById('root')).render(
  <FavoriteColor />
);
```

**Result:**
```
My favorite color is red!
```

### How It Works

```
1. useState("red") creates state
    ↓
2. color = "red"
    ↓
3. {color} displays "red"
    ↓
4. Shows: My favorite color is red!
```

---

## Part 12: Update State

### Using State Updater Function

```jsx
import { useState } from 'react';
import { createRoot } from 'react-dom/client';

function FavoriteColor() {
  const [color, setColor] = useState("red");
  
  return (
    <>
      <h1>My favorite color is {color}!</h1>
      <button
        type="button"
        onClick={() => setColor("blue")}
      >Blue</button>
    </>
  )
}

createRoot(document.getElementById('root')).render(
  <FavoriteColor />
);
```

### Important Rule

```jsx
// Correct ✅ - Use setState function
setColor("blue");

// Wrong ❌ - Never directly modify state
color = "blue";
```

**Never directly update state! Always use the setState function.**

---

## Part 13: Multiple State Updates

### Example: Color Buttons

```jsx
import { useState } from 'react';
import { createRoot } from 'react-dom/client';

function FavoriteColor() {
  const [color, setColor] = useState("red");
  
  return (
    <>
      <h1>My favorite color is {color}!</h1>
      <button
        type="button"
        onClick={() => setColor("blue")}
      >Blue</button>
      <button
        type="button"
        onClick={() => setColor("red")}
      >Red</button>
      <button
        type="button"
        onClick={() => setColor("pink")}
      >Pink</button>
      <button
        type="button"
        onClick={() => setColor("green")}
      >Green</button>
    </>
  );
}

createRoot(document.getElementById('root')).render(
  <FavoriteColor />
);
```

**Result:** Clicking any button updates the color displayed.

---

## Part 14: Multiple State Variables

### Creating Multiple States

You can create multiple state variables:

```jsx
import { useState } from 'react';
import { createRoot } from 'react-dom/client';

function MyCar() {
  const [brand, setBrand] = useState("Ford");
  const [model, setModel] = useState("Mustang");
  const [year, setYear] = useState("1964");
  const [color, setColor] = useState("red");
  
  return (
    <>
      <h1>My {brand}</h1>
      <p>
        It is a {color} {model} from {year}.
      </p>
    </>
  )
}

createRoot(document.getElementById('root')).render(
  <MyCar />
);
```

**Result:**
```
My Ford
It is a red Mustang from 1964.
```

---

## Part 15: State with Objects

### Single State Object

Instead of multiple states, you can use one state with an object:

```jsx
import { useState } from 'react';
import { createRoot } from 'react-dom/client';

function MyCar() {
  const [car, setCar] = useState({
    brand: "Ford",
    model: "Mustang",
    year: "1964",
    color: "red"
  });
  
  return (
    <>
      <h1>My {car.brand}</h1>
      <p>
        It is a {car.color} {car.model} from {car.year}.
      </p>
    </>
  )
}

createRoot(document.getElementById('root')).render(
  <MyCar />
);
```

### Accessing Object State

```jsx
// Access properties with dot notation
car.brand
car.model
car.year
car.color
```

---

## Part 16: Updating Object State

### The Problem

When updating object state, the entire state gets overwritten:

```jsx
// Wrong ❌ - This removes other properties
setCar({color: "blue"});
// Now car = {color: "blue"} only!
```

### The Solution: Spread Operator

Use the spread operator `...` to keep existing properties:

```jsx
const updateColor = () => {
  setCar(previousState => {
    return { ...previousState, color: "blue" }
  });
}
```

### How Spread Operator Works

```jsx
// Original state
car = {brand: "Ford", model: "Mustang", year: "1964", color: "red"}

// Update with spread
{...previousState, color: "blue"}
    ↓
{brand: "Ford", model: "Mustang", year: "1964", color: "blue"}
```

### Visual: Spread Operator

```
...previousState
    ↓
Copies all existing properties
    ↓
{brand: "Ford", model: "Mustang", year: "1964", color: "red"}
    ↓
Then overwrites: color: "blue"
    ↓
{brand: "Ford", model: "Mustang", year: "1964", color: "blue"}
```

---

## Part 17: Complete Object Update Example

### Full Example

```jsx
import { useState } from 'react';
import { createRoot } from 'react-dom/client';

function MyCar() {
  const [car, setCar] = useState({
    brand: "Ford",
    model: "Mustang",
    year: "1964",
    color: "red"
  });
  
  const updateColor = () => {
    setCar(previousState => {
      return { ...previousState, color: "blue" }
    });
  }
  
  return (
    <>
      <h1>My {car.brand}</h1>
      <p>
        It is a {car.color} {car.model} from {car.year}.
      </p>
      <button
        type="button"
        onClick={updateColor}
      >Change Color</button>
    </>
  )
}

createRoot(document.getElementById('root')).render(
  <MyCar />
);
```

---

## Part 18: State with Arrays

### Array State Example

```jsx
import { useState } from 'react';

function TodoList() {
  const [todos, setTodos] = useState(["Task 1", "Task 2"]);
  
  const addTodo = () => {
    setTodos(previousTodos => {
      return [...previousTodos, "New Task"]
    });
  }
  
  return (
    <>
      <ul>
        {todos.map((todo, index) => (
          <li key={index}>{todo}</li>
        ))}
      </ul>
      <button onClick={addTodo}>Add Todo</button>
    </>
  );
}
```

### Array Update Methods

```jsx
// Add item to end
setArray([...array, newItem]);

// Add item to beginning
setArray([newItem, ...array]);

// Remove item by index
setArray(array.filter((item, i) => i !== indexToRemove));

// Update item by index
setArray(array.map((item, i) => 
  i === indexToUpdate ? newValue : item
));
```

---

## Part 19: Key Concepts Summary

### Events

```jsx
// Event syntax
<button onClick={handleClick}>Click</button>

// Pass arguments
<button onClick={() => handleClick("arg")}>Click</button>

// Access event object
<button onClick={(e) => handleClick("arg", e)}>Click</button>
```

### useState Hook

```jsx
// Import
import { useState } from "react";

// Initialize
const [state, setState] = useState(initialValue);

// Read state
<h1>{state}</h1>

// Update state
setState(newValue);
```

### Update Object State

```jsx
// Use spread operator
setState(prev => ({...prev, property: newValue}));
```

### Update Array State

```jsx
// Use spread operator
setState(prev => [...prev, newItem]);
```

---

## Part 20: Quick Reference

### Event Handlers

```jsx
function MyComponent() {
  // Simple handler
  const handleClick = () => {
    console.log('Clicked!');
  }
  
  // Handler with parameter
  const handleClickWithParam = (message) => {
    console.log(message);
  }
  
  // Handler with event object
  const handleChange = (event) => {
    console.log(event.target.value);
  }
  
  return (
    <>
      <button onClick={handleClick}>Click</button>
      <button onClick={() => handleClickWithParam("Hello")}>Click</button>
      <input onChange={handleChange} />
    </>
  );
}
```

### useState Patterns

```jsx
function StateExamples() {
  // String state
  const [name, setName] = useState("John");
  
  // Number state
  const [count, setCount] = useState(0);
  
  // Boolean state
  const [isActive, setIsActive] = useState(false);
  
  // Object state
  const [user, setUser] = useState({
    name: "John",
    age: 25
  });
  
  // Array state
  const [items, setItems] = useState([1, 2, 3]);
  
  // Update object
  const updateUser = () => {
    setUser(prev => ({...prev, age: 26}));
  }
  
  // Update array
  const addItem = () => {
    setItems(prev => [...prev, 4]);
  }
  
  return <div>State examples</div>;
}
```

---

## What's Next?

In Phase 5, we'll learn about:

### Coming Up: Phase 5 - Rendering Data

- Conditional Rendering
- Rendering Lists

---

*Congratulations! You've completed React Phase 4: Interactivity. You now understand how to handle events and manage state with useState!*

---

**Keep practicing and see you in Phase 5!** ⚛️
