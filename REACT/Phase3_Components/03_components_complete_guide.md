# React Phase 3: Components - Complete Guide

## Part 1: What are Components?

### Components Definition

Components are independent and reusable pieces of code. They work like JavaScript functions but return HTML.

**Think of components as building blocks - each component is a piece of your website that you can use again and again.**

### Key Facts

| Feature | Description |
|---------|-------------|
| Purpose | Reusable UI pieces |
| Work Like | JavaScript functions |
| Return | HTML elements |
| Independence | Work in isolation |
| Types | Function Components (modern), Class Components (old) |

### Component Types

```
Function Components (Modern) ✅
- Simple and easy
- Use with Hooks
- Recommended for new code

Class Components (Old) ⚠️
- Complex syntax
- Still supported
- Found in older code
```

**We will use Function Components in this guide!**

---

## Part 2: Create Your First Component

### Component Rules

1. Component name MUST start with uppercase letter
2. Component returns HTML code

### Example: Simple Component

```jsx
function Car() {
  return (
    <h2>Hi, I am a Car!</h2>
  );
}
```

### Visual: Component Structure

```
function ComponentName() {
    ↓
  return (
    <HTML code here />
  );
    ↓
}
```

---

## Part 3: Rendering a Component

### Using a Component

To use a component, write it like an HTML tag with uppercase first letter:

```jsx
<Car />
```

### Example: Render Component

```jsx
function Car() {
  return (
    <h2>Hi, I am a Car!</h2>
  );
}

createRoot(document.getElementById('root')).render(
  <Car />
);
```

**Result:**
```
Hi, I am a Car!
```

### How It Works

```
1. Create component function
    ↓
2. Return HTML from component
    ↓
3. Use <ComponentName /> to render
    ↓
4. Displays in browser
```

---

## Part 4: Components in Components

### Nesting Components

You can use components inside other components:

```jsx
function Car() {
  return (
    <h2>I am a Car!</h2>
  );
}

function Garage() {
  return (
    <>
      <h1>Who lives in my Garage?</h1>
      <Car />
    </>
  );
}

createRoot(document.getElementById('root')).render(
  <Garage />
);
```

**Result:**
```
Who lives in my Garage?
I am a Car!
```

### Visual: Component Tree

```
<Garage>
  ├── <h1>Who lives in my Garage?</h1>
  └── <Car>
        └── <h2>I am a Car!</h2>
```

---

## Part 5: Rendering Components Multiple Times

### Reusing Components

You can use the same component multiple times:

```jsx
function Car() {
  return (
    <h2>I am a Car!</h2>
  );
}

function Garage() {
  return (
    <>
      <h1>Who lives in my Garage?</h1>
      <Car />
      <Car />
    </>
  );
}

createRoot(document.getElementById('root')).render(
  <Garage />
);
```

**Result:**
```
Who lives in my Garage?
I am a Car!
I am a Car!
```

---

## Part 6: Introduction to Props

### What are Props?

Props (properties) are arguments passed into components. They work like function parameters.

**Think of props as a way to send data to a component.**

### Example: Component with Props

```jsx
function Car(props) {
  return (
    <h2>I am a {props.brand}!</h2>
  );
}

function Garage() {
  return (
    <>
      <h1>Who lives in my Garage?</h1>
      <Car brand="Ford" />
      <Car brand="BMW" />
    </>
  );
}

createRoot(document.getElementById('root')).render(
  <Garage />
);
```

**Result:**
```
Who lives in my Garage?
I am a Ford!
I am a BMW!
```

### How Props Work

```
<Car brand="Ford" />
    ↓
function Car(props) {
  props.brand = "Ford"
    ↓
  return <h2>I am a {props.brand}!</h2>
}
    ↓
Result: I am a Ford!
```

---

## Part 7: Components in Separate Files

### Why Separate Files?

React is about reusing code. Splitting components into separate files makes code organized and reusable.

### File Rules

1. Create `.jsx` file in `src` folder
2. Filename must start with uppercase
3. Export the component
4. Import where you need it

### Example: Vehicle.jsx

```jsx
function Car() {
  return (
    <h2>Hi, I am a Car!</h2>
  );
}

export default Car;
```

### Example: main.jsx

```jsx
import { createRoot } from 'react-dom/client'
import Car from './Vehicle.jsx';

createRoot(document.getElementById('root')).render(
  <Car />
);
```

### Visual: Import/Export Flow

```
Vehicle.jsx
  └── export default Car
        ↓
main.jsx
  └── import Car from './Vehicle.jsx'
        ↓
  └── <Car /> can be used
```

---

## Part 8: Props - Passing Data

### Props Syntax

Props are passed like HTML attributes:

```jsx
<Car brand="Ford" />
```

### Receiving Props

The component receives props as an object:

```jsx
function Car(props) {
  return (
    <h2>I am a {props.brand}!</h2>
  );
}

createRoot(document.getElementById('root')).render(
  <Car brand="Ford" />
);
```

**Result:**
```
I am a Ford!
```

### Props Object Name

You can name the props object anything:

```jsx
function Car(myobj) {
  return (
    <h2>I am a {myobj.brand}!</h2>
  );
}
```

**Convention:** Use `props` as the standard name.

---

## Part 9: Multiple Props

### Passing Multiple Properties

You can send as many props as you want:

```jsx
createRoot(document.getElementById('root')).render(
  <Car brand="Ford" model="Mustang" color="red" />
);
```

### Using Multiple Props

```jsx
function Car(props) {
  return (
    <h2>I am a {props.color} {props.brand} {props.model}!</h2>
  );
}
```

**Result:**
```
I am a red Ford Mustang!
```

### Visual: Multiple Props

```
<Car brand="Ford" model="Mustang" color="red" />
    ↓
props = {
  brand: "Ford",
  model: "Mustang",
  color: "red"
}
```

---

## Part 10: Props - Different Data Types

### Data Type Rules

| Data Type | Syntax |
|-----------|--------|
| String | `brand="Ford"` (quotes) |
| Number | `year={1969}` (curly braces) |
| Variable | `brand={x}` (curly braces) |
| Object | `carinfo={obj}` (curly braces) |
| Array | `years={arr}` (curly braces) |

### Example: Number Props

```jsx
createRoot(document.getElementById('root')).render(
  <Car year={1969} />
);
```

### Example: Variable Props

```jsx
let x = "Ford";

createRoot(document.getElementById('root')).render(
  <Car brand={x} />
);
```

### Example: Object and Array Props

```jsx
let x = [1964, 1965, 1966];
let y = {name: "Ford", model: "Mustang"};

createRoot(document.getElementById('root')).render(
  <Car years={x} carinfo={y} />
);
```

---

## Part 11: Object Props

### Accessing Object Properties

Use dot notation to access object properties:

```jsx
function Car(props) {
  return (
    <>
      <h2>My {props.carinfo.name} {props.carinfo.model}!</h2>
      <p>It is {props.carinfo.color} and it is from {props.carinfo.year}!</p>
    </>
  );
}

const carInfo = {
  name: "Ford",
  model: "Mustang",
  color: "red",
  year: 1969
};

createRoot(document.getElementById('root')).render(
  <Car carinfo={carInfo} />
);
```

**Result:**
```
My Ford Mustang!
It is red and it is from 1969!
```

---

## Part 12: Array Props

### Accessing Array Elements

Use indexes to access array elements:

```jsx
function Car(props) {
  return (
    <h2>My car is a {props.carinfo[0]} {props.carinfo[1]}!</h2>
  );
}

const carInfo = ["Ford", "Mustang"];

createRoot(document.getElementById('root')).render(
  <Car carinfo={carInfo} />
);
```

**Result:**
```
My car is a Ford Mustang!
```

---

## Part 13: Props Between Components

### Passing Props Through Components

You can pass props from one component to another:

```jsx
function Car(props) {
  return (
    <h2>I am a {props.brand}!</h2>
  );
}

function Garage() {
  return (
    <>
      <h1>Who lives in my garage?</h1>
      <Car brand="Ford" />
    </>
  );
}

createRoot(document.getElementById('root')).render(
  <Garage />
);
```

**Result:**
```
Who lives in my garage?
I am a Ford!
```

### Visual: Props Flow

```
<Garage>
    ↓
  <Car brand="Ford" />
    ↓
function Car(props) {
  props.brand = "Ford"
}
```

---

## Part 14: Props are Read-Only

### Important Rule

React Props are read-only! You cannot change their value.

### Wrong ❌

```jsx
function Car(props) {
  props.brand = "Toyota";  // ERROR!
  return (
    <h2>I am a {props.brand}!</h2>
  );
}
```

### Correct ✅

```jsx
function Car(props) {
  // Just use props, don't modify them
  return (
    <h2>I am a {props.brand}!</h2>
  );
}
```

---

## Part 15: Props Destructuring - Basic

### What is Destructuring?

Destructuring lets you extract specific properties from props directly in the function parameter.

### Without Destructuring

```jsx
function Car(props) {
  return (
    <h2>My car is {props.color}!</h2>
  );
}
```

### With Destructuring

```jsx
function Car({color}) {
  return (
    <h2>My car is {color}!</h2>
  );
}

createRoot(document.getElementById('root')).render(
  <Car brand="Ford" model="Mustang" color="red" year={1969} />
);
```

**Result:**
```
My car is red!
```

### Visual: Destructuring

```
Without:
props.color

With:
{color}  ← Extract color directly
```

---

## Part 16: Props Destructuring - Inside Component

### Destructuring Inside Function

You can also destructure inside the component:

```jsx
function Car(props) {
  const {brand, model} = props;
  
  return (
    <h2>I love my {brand} {model}!</h2>
  );
}

createRoot(document.getElementById('root')).render(
  <Car brand="Ford" model="Mustang" color="red" year={1969} />
);
```

**Result:**
```
I love my Ford Mustang!
```

### Two Ways to Destructure

```jsx
// Way 1: In parameter
function Car({brand, model}) {
  return <h2>{brand} {model}</h2>;
}

// Way 2: Inside function
function Car(props) {
  const {brand, model} = props;
  return <h2>{brand} {model}</h2>;
}
```

---

## Part 17: Props Destructuring - Rest Operator

### Using ...rest

When you don't know how many props you'll receive, use `...rest`:

```jsx
function Car({color, brand, ...rest}) {
  return (
    <h2>My {brand} {rest.model} is {color}!</h2>
  );
}

createRoot(document.getElementById('root')).render(
  <Car brand="Ford" model="Mustang" color="red" year={1969} />
);
```

**Result:**
```
My Ford Mustang is red!
```

### How ...rest Works

```
Props received:
{brand: "Ford", model: "Mustang", color: "red", year: 1969}
    ↓
Destructured:
color = "red"
brand = "Ford"
rest = {model: "Mustang", year: 1969}
```

---

## Part 18: Props Destructuring - Default Values

### Setting Default Values

You can set default values for props:

```jsx
function Car({color = "blue", brand}) {
  return (
    <h2>My {color} {brand}!</h2>
  );
}

createRoot(document.getElementById('root')).render(
  <Car brand="Ford" />
);
```

**Result:**
```
My blue Ford!
```

### When Defaults are Used

```
If prop is provided:
<Car color="red" brand="Ford" />
Result: My red Ford!

If prop is NOT provided:
<Car brand="Ford" />
Result: My blue Ford!  ← Uses default
```

### Multiple Defaults

```jsx
function Car({color = "blue", brand = "Unknown", year = 2024}) {
  return (
    <h2>{year} {color} {brand}</h2>
  );
}
```

---

## Part 19: Props Children

### What is props.children?

`props.children` contains the content between opening and closing tags of a component.

### Example: Basic Children

```jsx
function Son(props) {
  return (
    <div style={{background: 'lightgreen'}}>
      <h2>Son</h2>
      <div>{props.children}</div>
    </div>
  );
}

function Daughter(props) {
  return (
    <div style={{background: 'lightblue'}}>
      <h2>Daughter</h2>
      <div>{props.children}</div>
    </div>
  );
}

function Parent() {
  return (
    <div>
      <h1>My two Children</h1>
      <Son>
        <p>
          This was written in the Parent component,
          but displayed as a part of the Son component
        </p>
      </Son>
      <Daughter>
        <p>
          This was written in the Parent component,
          but displayed as a part of the Daughter component
        </p>
      </Daughter>
    </div>
  );
}

createRoot(document.getElementById('root')).render(
  <Parent />
);
```

### Visual: props.children Flow

```
<Son>
  <p>Content here</p>  ← This is props.children
</Son>
    ↓
function Son(props) {
  return (
    <div>
      {props.children}  ← Content appears here
    </div>
  );
}
```

---

## Part 20: Props Children - Practical Example

### Example: Card Component

```jsx
function Card(props) {
  return (
    <div style={{
      border: '2px solid black',
      padding: '20px',
      margin: '10px'
    }}>
      {props.children}
    </div>
  );
}

function App() {
  return (
    <>
      <Card>
        <h2>Card 1</h2>
        <p>This is the first card</p>
      </Card>
      <Card>
        <h2>Card 2</h2>
        <p>This is the second card</p>
      </Card>
    </>
  );
}
```

**Result:**
```
┌─────────────────────┐
│ Card 1              │
│ This is the first   │
│ card                │
└─────────────────────┘

┌─────────────────────┐
│ Card 2              │
│ This is the second  │
│ card                │
└─────────────────────┘
```

---

## Part 21: Key Concepts Summary

### Components

```jsx
// Create component (uppercase first letter)
function ComponentName() {
  return <h1>Hello</h1>;
}

// Use component
<ComponentName />
```

### Props

```jsx
// Pass props
<Car brand="Ford" year={1969} />

// Receive props
function Car(props) {
  return <h2>{props.brand} {props.year}</h2>;
}
```

### Props Destructuring

```jsx
// In parameter
function Car({brand, model}) {
  return <h2>{brand} {model}</h2>;
}

// Inside function
function Car(props) {
  const {brand, model} = props;
  return <h2>{brand} model}</h2>;
}

// With default values
function Car({color = "blue"}) {
  return <h2>{color}</h2>;
}

// With rest operator
function Car({brand, ...rest}) {
  return <h2>{brand} {rest.model}</h2>;
}
```

### Props Children

```jsx
function Box(props) {
  return <div>{props.children}</div>;
}

<Box>
  <p>Content here</p>
</Box>
```

---

## Part 22: Quick Reference

### Component Structure

```jsx
// Simple component
function MyComponent() {
  return <h1>Hello</h1>;
}

// Component with props
function MyComponent(props) {
  return <h1>Hello {props.name}</h1>;
}

// Component with destructured props
function MyComponent({name, age}) {
  return <h1>Hello {name}, age {age}</h1>;
}

// Component with children
function MyComponent(props) {
  return (
    <div>
      {props.children}
    </div>
  );
}
```

### Using Components

```jsx
// Render component
<MyComponent />

// Pass props
<MyComponent name="John" age={25} />

// Pass children
<MyComponent>
  <p>Child content</p>
</MyComponent>

// Nest components
function Parent() {
  return (
    <div>
      <Child1 />
      <Child2 />
    </div>
  );
}
```

### Props Patterns

```jsx
// String prop
<Car brand="Ford" />

// Number prop
<Car year={1969} />

// Variable prop
<Car brand={myVariable} />

// Object prop
<Car info={myObject} />

// Array prop
<Car years={myArray} />

// Multiple props
<Car brand="Ford" model="Mustang" year={1969} />
```

---

## What's Next?

In Phase 4, we'll learn about:

### Coming Up: Phase 4 - Interactivity

- Handling Events
- Using useState Hook

---

*Congratulations! You've completed React Phase 3: Components. You now understand how to create reusable components and pass data using props!*

---

**Keep practicing and see you in Phase 4!** ⚛️
