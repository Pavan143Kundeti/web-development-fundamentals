# React Phase 6: Forms - Complete Guide

## Part 1: Forms Introduction

### What are Forms?

Forms allow users to interact with your web page by entering data like names, emails, passwords, etc.

**Think of forms as a way to collect information from users.**

### Key Facts

| Feature | Description |
|---------|-------------|
| Purpose | Collect user input |
| Elements | input, textarea, select |
| React Way | Controlled components |
| State | Managed by React, not DOM |

### HTML Forms vs React Forms

| HTML Forms | React Forms |
|------------|-------------|
| DOM manages value | React state manages value |
| Page refreshes on submit | Prevent default, handle in React |
| Uncontrolled | Controlled components |

---

## Part 2: Basic Form in React

### Simple Form Example

```jsx
function MyForm() {
  return (
    <form>
      <label>Enter your name:
        <input type="text" />
      </label>
    </form>
  )
}

createRoot(document.getElementById('root')).render(
  <MyForm />
);
```

### The Problem

This form works, but when submitted:
- Page refreshes
- Data is lost
- Not the React way

**We need React to control the form!**

---

## Part 3: Controlled Components

### What are Controlled Components?

In controlled components, form data is handled by React component state, not the DOM.

### Visual: Controlled vs Uncontrolled

```
Uncontrolled (HTML way):
User types → DOM stores value

Controlled (React way):
User types → onChange event → Update state → Display value
```

### Key Concept

```
React state = Single source of truth
```

All form data lives in React state, making it easy to:
- Access values
- Validate input
- Submit data
- Reset forms

---

## Part 4: Creating a Controlled Input

### Using useState for Form Control

```jsx
import { useState } from 'react';
import { createRoot } from 'react-dom/client';

function MyForm() {
  const [name, setName] = useState("");
  
  function handleChange(e) {
    setName(e.target.value);
  }
  
  return (
    <form>
      <label>Enter your name:
        <input
          type="text"
          value={name}
          onChange={handleChange}
        />
      </label>
      <p>Current value: {name}</p>
    </form>
  )
}

createRoot(document.getElementById('root')).render(
  <MyForm />
);
```

**Result:** As you type, the current value displays below the input.

---

## Part 5: Understanding Controlled Input

### Step-by-Step Breakdown

```jsx
// Step 1: Import useState
import { useState } from 'react';

// Step 2: Create state variable
const [name, setName] = useState("");

// Step 3: Create change handler
function handleChange(e) {
  setName(e.target.value);
}

// Step 4: Connect to input
<input
  type="text"
  value={name}           // Read from state
  onChange={handleChange} // Update state
/>

// Step 5: Display value
<p>Current value: {name}</p>
```

### Visual: Data Flow

```
User types "A"
    ↓
onChange event fires
    ↓
handleChange(e) runs
    ↓
setName(e.target.value) updates state
    ↓
name = "A"
    ↓
Component re-renders
    ↓
Input shows "A"
```

---

## Part 6: Initial Values

### Setting Default Input Value

```jsx
function MyForm() {
  const [name, setName] = useState("John");
  
  function handleChange(e) {
    setName(e.target.value);
  }
  
  return (
    <form>
      <label>Enter your name:
        <input
          type="text"
          value={name}
          onChange={handleChange}
        />
      </label>
    </form>
  )
}
```

**Result:** Input field starts with "John" already filled in.

---

## Part 7: Form Submit

### Handling Form Submission

To handle form submission, add `onSubmit` to the form element:

```jsx
import { useState } from 'react';
import { createRoot } from 'react-dom/client';

function MyForm() {
  const [name, setName] = useState("");
  
  function handleChange(e) {
    setName(e.target.value);
  }
  
  function handleSubmit(e) {
    e.preventDefault();
    alert(name);
  }
  
  return (
    <form onSubmit={handleSubmit}>
      <label>Enter your name:
        <input
          type="text"
          value={name}
          onChange={handleChange}
        />
      </label>
      <input type="submit" />
    </form>
  )
}

createRoot(document.getElementById('root')).render(
  <MyForm />
);
```

**Result:** When you click submit, an alert shows the name (page doesn't refresh).

---

## Part 8: Understanding e.preventDefault()

### Why e.preventDefault()?

```jsx
function handleSubmit(e) {
  e.preventDefault();  // Prevents page refresh
  alert(name);
}
```

### Without e.preventDefault()

```
User clicks submit
    ↓
Form submits to server
    ↓
Page refreshes
    ↓
All state is lost
```

### With e.preventDefault()

```
User clicks submit
    ↓
e.preventDefault() stops default behavior
    ↓
handleSubmit runs
    ↓
Page stays, state preserved
```

---

## Part 9: Multiple Input Fields - Separate States

### Method 1: Individual States

```jsx
function MyForm() {
  const [firstName, setFirstName] = useState("");
  const [lastName, setLastName] = useState("");
  const [email, setEmail] = useState("");
  
  return (
    <form>
      <input
        type="text"
        value={firstName}
        onChange={(e) => setFirstName(e.target.value)}
      />
      <input
        type="text"
        value={lastName}
        onChange={(e) => setLastName(e.target.value)}
      />
      <input
        type="email"
        value={email}
        onChange={(e) => setEmail(e.target.value)}
      />
    </form>
  );
}
```

### Problem with This Approach

- Too many state variables
- Repetitive code
- Hard to manage large forms

---

## Part 10: Multiple Input Fields - Single State Object

### Method 2: Single State Object (Recommended)

```jsx
import { useState } from 'react';
import { createRoot } from 'react-dom/client';

function MyForm() {
  const [inputs, setInputs] = useState({});
  
  const handleChange = (e) => {
    const name = e.target.name;
    const value = e.target.value;
    setInputs(values => ({...values, [name]: value}))
  }
  
  return (
    <form>
      <label>First name:
      <input
        type="text"
        name="firstname"
        value={inputs.firstname || ""}
        onChange={handleChange}
      />
      </label>
      <label>Last name:
        <input
          type="text"
          name="lastname"
          value={inputs.lastname || ""}
          onChange={handleChange}
        />
      </label>
      <p>Current values: {inputs.firstname} {inputs.lastname}</p>
    </form>
  )
}

createRoot(document.getElementById('root')).render(
  <MyForm />
);
```

---

## Part 11: Understanding Multiple Inputs

### Step-by-Step Breakdown

```jsx
// Step 1: Single state object
const [inputs, setInputs] = useState({});

// Step 2: Single change handler for all inputs
const handleChange = (e) => {
  const name = e.target.name;    // Get input name
  const value = e.target.value;  // Get input value
  setInputs(values => ({...values, [name]: value}))
}

// Step 3: Each input has unique name attribute
<input
  type="text"
  name="firstname"              // Unique name
  value={inputs.firstname || ""}
  onChange={handleChange}       // Same handler
/>

<input
  type="text"
  name="lastname"               // Different name
  value={inputs.lastname || ""}
  onChange={handleChange}       // Same handler
/>
```

---

## Part 12: Bracket Notation Explained

### Dynamic Property Names

```jsx
setInputs(values => ({...values, [name]: value}))
```

### How It Works

```jsx
// If name = "firstname" and value = "John"
{...values, [name]: value}
    ↓
{...values, ["firstname"]: "John"}
    ↓
{...values, firstname: "John"}
```

### Visual: Spread and Update

```
Original state:
inputs = {firstname: "John"}

User types "Doe" in lastname:
name = "lastname"
value = "Doe"
    ↓
{...inputs, [name]: value}
    ↓
{...inputs, lastname: "Doe"}
    ↓
{firstname: "John", lastname: "Doe"}
```

---

## Part 13: Multiple Inputs with Initial Values

### Setting Default Values

```jsx
function MyForm() {
  const [inputs, setInputs] = useState({
    firstname: 'John',
    lastname: 'Doe'
  });
  
  const handleChange = (e) => {
    const name = e.target.name;
    const value = e.target.value;
    setInputs(values => ({...values, [name]: value}))
  }
  
  return (
    <form>
      <label>First name:
      <input
        type="text"
        name="firstname"
        value={inputs.firstname || ""}
        onChange={handleChange}
      />
      </label>
      <label>Last name:
        <input
          type="text"
          name="lastname"
          value={inputs.lastname || ""}
          onChange={handleChange}
        />
      </label>
    </form>
  )
}
```

**Result:** Form starts with "John" and "Doe" already filled in.

---

## Part 14: Complete Form Example

### Full Form with Submit

```jsx
import { useState } from 'react';
import { createRoot } from 'react-dom/client';

function MyForm() {
  const [inputs, setInputs] = useState({});
  
  const handleChange = (e) => {
    const name = e.target.name;
    const value = e.target.value;
    setInputs(values => ({...values, [name]: value}))
  }
  
  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(inputs);
    alert(`Name: ${inputs.firstname} ${inputs.lastname}\nEmail: ${inputs.email}`);
  }
  
  return (
    <form onSubmit={handleSubmit}>
      <label>First name:
        <input
          type="text"
          name="firstname"
          value={inputs.firstname || ""}
          onChange={handleChange}
        />
      </label>
      <label>Last name:
        <input
          type="text"
          name="lastname"
          value={inputs.lastname || ""}
          onChange={handleChange}
        />
      </label>
      <label>Email:
        <input
          type="email"
          name="email"
          value={inputs.email || ""}
          onChange={handleChange}
        />
      </label>
      <input type="submit" value="Submit" />
    </form>
  )
}

createRoot(document.getElementById('root')).render(
  <MyForm />
);
```

---

## Part 15: Different Input Types

### Text, Email, Password, Number

```jsx
function MyForm() {
  const [inputs, setInputs] = useState({});
  
  const handleChange = (e) => {
    const name = e.target.name;
    const value = e.target.value;
    setInputs(values => ({...values, [name]: value}))
  }
  
  return (
    <form>
      <input
        type="text"
        name="username"
        placeholder="Username"
        value={inputs.username || ""}
        onChange={handleChange}
      />
      
      <input
        type="email"
        name="email"
        placeholder="Email"
        value={inputs.email || ""}
        onChange={handleChange}
      />
      
      <input
        type="password"
        name="password"
        placeholder="Password"
        value={inputs.password || ""}
        onChange={handleChange}
      />
      
      <input
        type="number"
        name="age"
        placeholder="Age"
        value={inputs.age || ""}
        onChange={handleChange}
      />
    </form>
  );
}
```

---

## Part 16: Textarea in React

### Controlled Textarea

```jsx
function MyForm() {
  const [inputs, setInputs] = useState({});
  
  const handleChange = (e) => {
    const name = e.target.name;
    const value = e.target.value;
    setInputs(values => ({...values, [name]: value}))
  }
  
  return (
    <form>
      <label>Message:
        <textarea
          name="message"
          value={inputs.message || ""}
          onChange={handleChange}
          rows="4"
        />
      </label>
    </form>
  );
}
```

### Important Note

In React, textarea uses `value` attribute (not children like HTML):

```jsx
// React way ✅
<textarea value={inputs.message} onChange={handleChange} />

// HTML way (don't use in React) ❌
<textarea>{inputs.message}</textarea>
```

---

## Part 17: Select Dropdown in React

### Controlled Select

```jsx
function MyForm() {
  const [inputs, setInputs] = useState({});
  
  const handleChange = (e) => {
    const name = e.target.name;
    const value = e.target.value;
    setInputs(values => ({...values, [name]: value}))
  }
  
  return (
    <form>
      <label>Choose a car:
        <select
          name="car"
          value={inputs.car || ""}
          onChange={handleChange}
        >
          <option value="">Select...</option>
          <option value="ford">Ford</option>
          <option value="bmw">BMW</option>
          <option value="audi">Audi</option>
        </select>
      </label>
      <p>Selected: {inputs.car}</p>
    </form>
  );
}
```

---

## Part 18: Checkbox in React

### Controlled Checkbox

```jsx
function MyForm() {
  const [inputs, setInputs] = useState({
    agree: false
  });
  
  const handleChange = (e) => {
    const name = e.target.name;
    const value = e.target.type === 'checkbox' ? e.target.checked : e.target.value;
    setInputs(values => ({...values, [name]: value}))
  }
  
  return (
    <form>
      <label>
        <input
          type="checkbox"
          name="agree"
          checked={inputs.agree || false}
          onChange={handleChange}
        />
        I agree to terms
      </label>
      <p>Agreed: {inputs.agree ? "Yes" : "No"}</p>
    </form>
  );
}
```

### Key Differences for Checkbox

```jsx
// Use 'checked' instead of 'value'
checked={inputs.agree || false}

// Get value from e.target.checked
const value = e.target.type === 'checkbox' ? e.target.checked : e.target.value;
```

---

## Part 19: Radio Buttons in React

### Controlled Radio Buttons

```jsx
function MyForm() {
  const [inputs, setInputs] = useState({});
  
  const handleChange = (e) => {
    const name = e.target.name;
    const value = e.target.value;
    setInputs(values => ({...values, [name]: value}))
  }
  
  return (
    <form>
      <p>Choose your favorite color:</p>
      <label>
        <input
          type="radio"
          name="color"
          value="red"
          checked={inputs.color === "red"}
          onChange={handleChange}
        />
        Red
      </label>
      <label>
        <input
          type="radio"
          name="color"
          value="blue"
          checked={inputs.color === "blue"}
          onChange={handleChange}
        />
        Blue
      </label>
      <label>
        <input
          type="radio"
          name="color"
          value="green"
          checked={inputs.color === "green"}
          onChange={handleChange}
        />
        Green
      </label>
      <p>Selected: {inputs.color}</p>
    </form>
  );
}
```

---

## Part 20: Key Concepts Summary

### Controlled Component Pattern

```jsx
// 1. State
const [value, setValue] = useState("");

// 2. Handler
const handleChange = (e) => {
  setValue(e.target.value);
}

// 3. Input
<input
  value={value}
  onChange={handleChange}
/>
```

### Multiple Inputs Pattern

```jsx
// 1. State object
const [inputs, setInputs] = useState({});

// 2. Single handler
const handleChange = (e) => {
  const name = e.target.name;
  const value = e.target.value;
  setInputs(values => ({...values, [name]: value}))
}

// 3. Inputs with unique names
<input name="field1" value={inputs.field1 || ""} onChange={handleChange} />
<input name="field2" value={inputs.field2 || ""} onChange={handleChange} />
```

### Form Submit Pattern

```jsx
const handleSubmit = (e) => {
  e.preventDefault();
  // Process form data
  console.log(inputs);
}

<form onSubmit={handleSubmit}>
  {/* inputs */}
  <input type="submit" />
</form>
```

---

## Part 21: Quick Reference

### Basic Form

```jsx
function BasicForm() {
  const [name, setName] = useState("");
  
  return (
    <form onSubmit={(e) => {
      e.preventDefault();
      alert(name);
    }}>
      <input
        type="text"
        value={name}
        onChange={(e) => setName(e.target.value)}
      />
      <button type="submit">Submit</button>
    </form>
  );
}
```

### Multi-Field Form

```jsx
function MultiFieldForm() {
  const [inputs, setInputs] = useState({});
  
  const handleChange = (e) => {
    const name = e.target.name;
    const value = e.target.value;
    setInputs(values => ({...values, [name]: value}))
  }
  
  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(inputs);
  }
  
  return (
    <form onSubmit={handleSubmit}>
      <input name="name" value={inputs.name || ""} onChange={handleChange} />
      <input name="email" value={inputs.email || ""} onChange={handleChange} />
      <textarea name="message" value={inputs.message || ""} onChange={handleChange} />
      <select name="option" value={inputs.option || ""} onChange={handleChange}>
        <option value="">Select...</option>
        <option value="1">Option 1</option>
      </select>
      <button type="submit">Submit</button>
    </form>
  );
}
```

---

## Part 22: Common Patterns

### Reset Form

```jsx
function FormWithReset() {
  const [inputs, setInputs] = useState({});
  
  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(inputs);
    setInputs({});  // Reset form
  }
  
  return (
    <form onSubmit={handleSubmit}>
      <input name="name" value={inputs.name || ""} onChange={handleChange} />
      <button type="submit">Submit</button>
      <button type="button" onClick={() => setInputs({})}>Reset</button>
    </form>
  );
}
```

### Form Validation

```jsx
function ValidatedForm() {
  const [inputs, setInputs] = useState({});
  const [errors, setErrors] = useState({});
  
  const handleSubmit = (e) => {
    e.preventDefault();
    
    const newErrors = {};
    if (!inputs.name) {
      newErrors.name = "Name is required";
    }
    if (!inputs.email) {
      newErrors.email = "Email is required";
    }
    
    if (Object.keys(newErrors).length > 0) {
      setErrors(newErrors);
      return;
    }
    
    console.log("Form is valid:", inputs);
  }
  
  return (
    <form onSubmit={handleSubmit}>
      <input name="name" value={inputs.name || ""} onChange={handleChange} />
      {errors.name && <span style={{color: 'red'}}>{errors.name}</span>}
      
      <input name="email" value={inputs.email || ""} onChange={handleChange} />
      {errors.email && <span style={{color: 'red'}}>{errors.email}</span>}
      
      <button type="submit">Submit</button>
    </form>
  );
}
```

---

## What's Next?

In Phase 7, we'll learn about:

### Coming Up: Phase 7 - Side Effects

- useEffect Hook

---

*Congratulations! You've completed React Phase 6: Forms. You now understand how to create controlled forms and handle user input!*

---

**Keep practicing and see you in Phase 7!** ⚛️
