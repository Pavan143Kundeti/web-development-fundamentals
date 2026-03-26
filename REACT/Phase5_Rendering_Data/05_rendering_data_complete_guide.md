# React Phase 5: Rendering Data - Complete Guide

## Part 1: Conditional Rendering Introduction

### What is Conditional Rendering?

Conditional rendering means showing different components or content based on conditions.

**Think of it like an if statement - show this component if true, show that component if false.**

### Key Facts

| Feature | Description |
|---------|-------------|
| Purpose | Show different content based on conditions |
| Methods | if statement, && operator, ternary operator |
| Use Cases | Show/hide elements, display different components |

### Visual: Conditional Rendering

```
Condition: isLoggedIn = true
    ↓
Show: <Dashboard />

Condition: isLoggedIn = false
    ↓
Show: <Login />
```

---

## Part 2: Conditional Rendering with if Statement

### Using if Statement

You can use regular JavaScript if statements to decide which component to render.

### Example: Two Components

```jsx
function MissedGoal() {
  return <h1>MISSED!</h1>;
}

function MadeGoal() {
  return <h1>Goal!</h1>;
}
```

### Example: Conditional Component

```jsx
function Goal(props) {
  const isGoal = props.isGoal;
  
  if (isGoal) {
    return <MadeGoal/>;
  }
  return <MissedGoal/>;
}

createRoot(document.getElementById('root')).render(
  <Goal isGoal={false} />
);
```

**Result:**
```
MISSED!
```

### Change to true

```jsx
createRoot(document.getElementById('root')).render(
  <Goal isGoal={true} />
);
```

**Result:**
```
Goal!
```

### Visual: if Statement Flow

```
isGoal = true?
    ↓
   Yes → return <MadeGoal />
    ↓
   No → return <MissedGoal />
```

---

## Part 3: Conditional Rendering with && Operator

### Logical && Operator

The && operator only renders the right side if the left side is true.

### Syntax

```jsx
{condition && <Component />}
```

### Example: Show if Brand Exists

```jsx
function Car(props) {
  return (
    <>
      {props.brand && <h1>My car is a {props.brand}!</h1>}
    </>
  );
}

createRoot(document.getElementById('root')).render(
  <Car brand="Ford" />
);
```

**Result:**
```
My car is a Ford!
```

### Example: Empty Brand

```jsx
createRoot(document.getElementById('root')).render(
  <Car />
);
```

**Result:** Nothing is displayed (brand is undefined, so condition is false)

### How && Works

```
props.brand && <h1>...</h1>
    ↓
If props.brand is truthy → render <h1>
If props.brand is falsy → render nothing
```

### Visual: && Operator

```
Left side true?
    ↓
   Yes → Show right side
    ↓
   No → Show nothing
```

---

## Part 4: Conditional Rendering with Ternary Operator

### Ternary Operator Syntax

```jsx
condition ? valueIfTrue : valueIfFalse
```

### Example: Goal with Ternary

```jsx
function Goal(props) {
  const isGoal = props.isGoal;
  
  return (
    <>
      { isGoal ? <MadeGoal/> : <MissedGoal/> }
    </>
  );
}

createRoot(document.getElementById('root')).render(
  <Goal isGoal={false} />
);
```

**Result:**
```
MISSED!
```

### Visual: Ternary Flow

```
isGoal ? <MadeGoal/> : <MissedGoal/>
    ↓
isGoal = true → <MadeGoal/>
isGoal = false → <MissedGoal/>
```

---

## Part 5: Comparing Conditional Methods

### Three Methods Comparison

```jsx
// Method 1: if statement
function Example1(props) {
  if (props.show) {
    return <h1>Visible</h1>;
  }
  return <h1>Hidden</h1>;
}

// Method 2: && operator
function Example2(props) {
  return (
    <>
      {props.show && <h1>Visible</h1>}
    </>
  );
}

// Method 3: Ternary operator
function Example3(props) {
  return (
    <>
      {props.show ? <h1>Visible</h1> : <h1>Hidden</h1>}
    </>
  );
}
```

### When to Use Each

| Method | Best For |
|--------|----------|
| if statement | Complex logic, multiple conditions |
| && operator | Show/hide single element |
| Ternary operator | Choose between two options |

---

## Part 6: Practical Conditional Examples

### Example: Login Status

```jsx
function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  }
  return <h1>Please sign in.</h1>;
}
```

### Example: Show/Hide Button

```jsx
function UserPanel(props) {
  return (
    <div>
      <h1>User Panel</h1>
      {props.isAdmin && <button>Delete User</button>}
    </div>
  );
}
```

### Example: Status Message

```jsx
function Status(props) {
  return (
    <div>
      {props.isOnline ? 
        <span style={{color: 'green'}}>Online</span> : 
        <span style={{color: 'red'}}>Offline</span>
      }
    </div>
  );
}
```

---

## Part 7: Lists Introduction

### What are Lists?

Lists are collections of items rendered using loops, typically with the `map()` method.

**Think of lists as a way to display multiple similar items from an array.**

### Key Facts

| Feature | Description |
|---------|-------------|
| Purpose | Render multiple items from array |
| Method | JavaScript `map()` |
| Requirement | Each item needs a unique `key` |

### Visual: List Rendering

```
Array: ['Ford', 'BMW', 'Audi']
    ↓
map() loops through each item
    ↓
Returns: <li>Ford</li>, <li>BMW</li>, <li>Audi</li>
```

---

## Part 8: Rendering Lists with map()

### Basic List Example

```jsx
function MyCars() {
  const cars = ['Ford', 'BMW', 'Audi'];
  
  return (
    <>
      <h1>My Cars:</h1>
      <ul>
        {cars.map((car) => <li>I am a {car}</li>)}
      </ul>
    </>
  );
}

createRoot(document.getElementById('root')).render(
  <MyCars />
);
```

**Result:**
```
My Cars:
• I am a Ford
• I am a BMW
• I am a Audi
```

### Warning

This code works but shows a warning: "Each child in a list should have a unique key prop"

---

## Part 9: Keys in React Lists

### What are Keys?

Keys help React identify which items have changed, been added, or removed.

**Think of keys as unique IDs for list items - they help React track changes efficiently.**

### Key Rules

```
✅ DO:
- Use unique IDs as keys
- Keep keys consistent
- Use keys on the outermost element in map()

❌ DON'T:
- Use array index as key (unless list is static)
- Use random values as keys
- Omit keys in lists
```

### Visual: Why Keys Matter

```
Without keys:
Item changes → React re-renders entire list

With keys:
Item changes → React re-renders only that item
```

---

## Part 10: Lists with Unique ID Keys

### Best Practice: Use Unique IDs

```jsx
function MyCars() {
  const cars = [
    {id: 1001, brand: 'Ford'},
    {id: 1002, brand: 'BMW'},
    {id: 1003, brand: 'Audi'}
  ];
  
  return (
    <>
      <h1>My Cars:</h1>
      <ul>
        {cars.map((car) => <li key={car.id}>I am a {car.brand}</li>)}
      </ul>
    </>
  );
}

createRoot(document.getElementById('root')).render(
  <MyCars />
);
```

**Result:**
```
My Cars:
• I am a Ford
• I am a BMW
• I am a Audi
```

No warning! Each item has a unique key.

---

## Part 11: Using Array Index as Keys

### When to Use Index

Array index can be used as a key only when:

1. List is static (won't change)
2. List will never be reordered or filtered
3. Items have no unique IDs

### Example: Index as Key

```jsx
function MyCars() {
  const cars = ['Ford', 'BMW', 'Audi'];
  
  return (
    <>
      <h1>My Cars:</h1>
      <ul>
        {cars.map((car, index) => <li key={index}>I am a {car}</li>)}
      </ul>
    </>
  );
}

createRoot(document.getElementById('root')).render(
  <MyCars />
);
```

### Why Index is Not Recommended

```
Original list:
0: Ford
1: BMW
2: Audi

User deletes BMW:
0: Ford
1: Audi  ← Index changed! React gets confused

With unique IDs:
1001: Ford
1003: Audi  ← IDs stay same, React tracks correctly
```

---

## Part 12: Complex List Examples

### Example: List with Multiple Properties

```jsx
function UserList() {
  const users = [
    {id: 1, name: 'John', age: 25},
    {id: 2, name: 'Sarah', age: 30},
    {id: 3, name: 'Mike', age: 28}
  ];
  
  return (
    <>
      <h1>Users:</h1>
      <ul>
        {users.map((user) => (
          <li key={user.id}>
            {user.name} - Age: {user.age}
          </li>
        ))}
      </ul>
    </>
  );
}
```

**Result:**
```
Users:
• John - Age: 25
• Sarah - Age: 30
• Mike - Age: 28
```

---

## Part 13: Lists with Components

### Rendering Component Lists

```jsx
function Car(props) {
  return <li>I am a {props.brand}</li>;
}

function Garage() {
  const cars = [
    {id: 1, brand: 'Ford'},
    {id: 2, brand: 'BMW'},
    {id: 3, brand: 'Audi'}
  ];
  
  return (
    <>
      <h1>My Garage:</h1>
      <ul>
        {cars.map((car) => <Car key={car.id} brand={car.brand} />)}
      </ul>
    </>
  );
}
```

**Important:** The key goes on the component in the map(), not inside the component!

---

## Part 14: Conditional Lists

### Combining Conditionals and Lists

```jsx
function ProductList(props) {
  const products = [
    {id: 1, name: 'Laptop', inStock: true},
    {id: 2, name: 'Phone', inStock: false},
    {id: 3, name: 'Tablet', inStock: true}
  ];
  
  return (
    <>
      <h1>Products:</h1>
      <ul>
        {products.map((product) => (
          <li key={product.id}>
            {product.name} - 
            {product.inStock ? 
              <span style={{color: 'green'}}> Available</span> : 
              <span style={{color: 'red'}}> Out of Stock</span>
            }
          </li>
        ))}
      </ul>
    </>
  );
}
```

**Result:**
```
Products:
• Laptop - Available
• Phone - Out of Stock
• Tablet - Available
```

---

## Part 15: Filtering Lists

### Filter Before Mapping

```jsx
function TodoList() {
  const todos = [
    {id: 1, task: 'Buy milk', completed: false},
    {id: 2, task: 'Clean room', completed: true},
    {id: 3, task: 'Study React', completed: false}
  ];
  
  const incompleteTodos = todos.filter(todo => !todo.completed);
  
  return (
    <>
      <h1>Incomplete Tasks:</h1>
      <ul>
        {incompleteTodos.map((todo) => (
          <li key={todo.id}>{todo.task}</li>
        ))}
      </ul>
    </>
  );
}
```

**Result:**
```
Incomplete Tasks:
• Buy milk
• Study React
```

---

## Part 16: Empty Lists

### Handling Empty Arrays

```jsx
function MessageList(props) {
  const messages = props.messages;
  
  if (messages.length === 0) {
    return <p>No messages to display</p>;
  }
  
  return (
    <ul>
      {messages.map((message) => (
        <li key={message.id}>{message.text}</li>
      ))}
    </ul>
  );
}
```

### Alternative with Ternary

```jsx
function MessageList(props) {
  const messages = props.messages;
  
  return (
    <>
      {messages.length === 0 ? (
        <p>No messages to display</p>
      ) : (
        <ul>
          {messages.map((message) => (
            <li key={message.id}>{message.text}</li>
          ))}
        </ul>
      )}
    </>
  );
}
```

---

## Part 17: Nested Lists

### Lists Inside Lists

```jsx
function CategoryList() {
  const categories = [
    {
      id: 1,
      name: 'Fruits',
      items: ['Apple', 'Banana', 'Orange']
    },
    {
      id: 2,
      name: 'Vegetables',
      items: ['Carrot', 'Broccoli', 'Spinach']
    }
  ];
  
  return (
    <>
      {categories.map((category) => (
        <div key={category.id}>
          <h2>{category.name}</h2>
          <ul>
            {category.items.map((item, index) => (
              <li key={index}>{item}</li>
            ))}
          </ul>
        </div>
      ))}
    </>
  );
}
```

**Result:**
```
Fruits
• Apple
• Banana
• Orange

Vegetables
• Carrot
• Broccoli
• Spinach
```

---

## Part 18: Key Concepts Summary

### Conditional Rendering

```jsx
// if statement
if (condition) {
  return <ComponentA />;
}
return <ComponentB />;

// && operator
{condition && <Component />}

// Ternary operator
{condition ? <ComponentA /> : <ComponentB />}
```

### Lists

```jsx
// Basic list
{array.map((item) => <li key={item.id}>{item.name}</li>)}

// List with component
{array.map((item) => <Component key={item.id} data={item} />)}

// Filtered list
{array.filter(condition).map((item) => <li key={item.id}>{item}</li>)}
```

### Keys

```jsx
// Best: Unique ID
<li key={item.id}>{item.name}</li>

// Last resort: Index (static lists only)
<li key={index}>{item}</li>
```

---

## Part 19: Quick Reference

### Conditional Patterns

```jsx
function ConditionalExamples(props) {
  // Show/hide single element
  return (
    <>
      {props.show && <div>Visible</div>}
    </>
  );
  
  // Choose between two elements
  return (
    <>
      {props.isActive ? <ActiveView /> : <InactiveView />}
    </>
  );
  
  // Multiple conditions
  if (props.status === 'loading') {
    return <Loading />;
  }
  if (props.status === 'error') {
    return <Error />;
  }
  return <Content />;
}
```

### List Patterns

```jsx
function ListExamples() {
  const items = [
    {id: 1, name: 'Item 1', active: true},
    {id: 2, name: 'Item 2', active: false}
  ];
  
  // Simple list
  return (
    <ul>
      {items.map(item => (
        <li key={item.id}>{item.name}</li>
      ))}
    </ul>
  );
  
  // List with conditional styling
  return (
    <ul>
      {items.map(item => (
        <li 
          key={item.id}
          style={{color: item.active ? 'green' : 'gray'}}
        >
          {item.name}
        </li>
      ))}
    </ul>
  );
  
  // Filtered list
  const activeItems = items.filter(item => item.active);
  return (
    <ul>
      {activeItems.map(item => (
        <li key={item.id}>{item.name}</li>
      ))}
    </ul>
  );
}
```

---

## Part 20: Common Patterns

### Loading State

```jsx
function DataDisplay(props) {
  if (props.isLoading) {
    return <p>Loading...</p>;
  }
  
  if (props.error) {
    return <p>Error: {props.error}</p>;
  }
  
  return (
    <ul>
      {props.data.map(item => (
        <li key={item.id}>{item.name}</li>
      ))}
    </ul>
  );
}
```

### Toggle Visibility

```jsx
function ToggleContent() {
  const [isVisible, setIsVisible] = useState(false);
  
  return (
    <>
      <button onClick={() => setIsVisible(!isVisible)}>
        {isVisible ? 'Hide' : 'Show'}
      </button>
      {isVisible && (
        <div>
          <p>This content can be toggled</p>
        </div>
      )}
    </>
  );
}
```

### Dynamic List with State

```jsx
function DynamicList() {
  const [items, setItems] = useState([
    {id: 1, text: 'Item 1'},
    {id: 2, text: 'Item 2'}
  ]);
  
  const addItem = () => {
    const newItem = {
      id: items.length + 1,
      text: `Item ${items.length + 1}`
    };
    setItems([...items, newItem]);
  };
  
  return (
    <>
      <button onClick={addItem}>Add Item</button>
      <ul>
        {items.map(item => (
          <li key={item.id}>{item.text}</li>
        ))}
      </ul>
    </>
  );
}
```

---

## What's Next?

In Phase 6, we'll learn about:

### Coming Up: Phase 6 - Forms

- Form Handling
- Form Submit
- Multiple Inputs

---

*Congratulations! You've completed React Phase 5: Rendering Data. You now understand how to conditionally render components and display lists!*

---

**Keep practicing and see you in Phase 6!** ⚛️
