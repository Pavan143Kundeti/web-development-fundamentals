# React Phase 8: Routing - Complete Guide

## Part 1: What is React Router?

### React Router Definition

React Router is a library that handles navigation between different views in your React application.

**Think of React Router as a way to create multiple pages in your single-page application.**

### Key Facts

| Feature | Description |
|---------|-------------|
| Purpose | Navigate between views |
| Type | External library |
| Package | react-router-dom |
| Benefit | Multiple pages without page reload |

### What React Router Enables

- Multiple pages in single-page app
- URL parameters and query strings
- Browser history management
- Nested routes
- Protected routes

---

## Part 2: Install React Router

### Installation Command

```bash
npm install react-router-dom
```

**Run this in your project directory.**

---

## Part 3: BrowserRouter Setup

### Wrap Your App

Your app must be wrapped with `BrowserRouter`:

```jsx
import { BrowserRouter } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      {/* Your app content */}
    </BrowserRouter>
  );
}
```

**BrowserRouter enables routing for your entire application.**

---

## Part 4: Create Views

### Simple Page Components

```jsx
function Home() {
  return <h1>Home Page</h1>;
}

function About() {
  return <h1>About Page</h1>;
}

function Contact() {
  return <h1>Contact Page</h1>;
}
```

These are the pages we'll navigate between.

---

## Part 5: Basic Routing Components

### Three Main Components

| Component | Purpose |
|-----------|---------|
| `Link` | Creates navigation links |
| `Routes` | Container for route definitions |
| `Route` | Maps URL path to component |

### Visual: Routing Flow

```
User clicks <Link to="/about">
    ↓
URL changes to /about
    ↓
<Routes> finds matching <Route>
    ↓
Renders <About /> component
```

---

## Part 6: Basic Routing Example

### Complete Routing Setup

```jsx
import { BrowserRouter, Routes, Route, Link } from 'react-router-dom';

function Home() {
  return <h1>Home Page</h1>;
}

function About() {
  return <h1>About Page</h1>;
}

function Contact() {
  return <h1>Contact Page</h1>;
}

function App() {
  return (
    <BrowserRouter>
      {/* Navigation */}
      <nav>
        <Link to="/">Home</Link> |{" "}
        <Link to="/about">About</Link> |{" "}
        <Link to="/contact">Contact</Link>
      </nav>
      
      {/* Routes */}
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </BrowserRouter>
  );
}
```

**Result:** Clicking links changes the page without reloading.

---

## Part 7: Understanding Routes

### Route Syntax

```jsx
<Route path="/about" element={<About />} />
```

| Part | Description |
|------|-------------|
| `path` | URL path to match |
| `element` | Component to render |

### How It Works

```
URL: /about
    ↓
Matches: <Route path="/about" ... />
    ↓
Renders: <About />
```

---

## Part 8: Nested Routes Introduction

### What are Nested Routes?

Nested routes let you change part of the page while keeping other parts the same.

**Think of it as a page within a page.**

### Visual: Nested Routes

```
Products Page (stays visible)
    ├── Cars (changes)
    └── Bikes (changes)
```

---

## Part 9: Nested Routes Example

### Complete Nested Routes

```jsx
import { BrowserRouter, Routes, Route, Link, Outlet } from 'react-router-dom';

function Home() {
  return <h1>Home Page</h1>;
}

function Products() {
  return (
    <div>
      <h1>Products Page</h1>
      <nav style={{ marginBottom: '20px' }}>
        <Link to="/products/car">Cars</Link> |{" "}
        <Link to="/products/bike">Bikes</Link>
      </nav>
      
      <Outlet />
    </div>
  );
}

function CarProducts() {
  return (
    <div>
      <h2>Cars</h2>
      <ul>
        <li>Audi</li>
        <li>BMW</li>
        <li>Volvo</li>
      </ul>
    </div>
  );
}

function BikeProducts() {
  return (
    <div>
      <h2>Bikes</h2>
      <ul>
        <li>Yamaha</li>
        <li>Suzuki</li>
        <li>Honda</li>
      </ul>
    </div>
  );
}

function Contact() {
  return <h1>Contact Page</h1>;
}

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link> |{" "}
        <Link to="/products">Products</Link> |{" "}
        <Link to="/contact">Contact</Link>
      </nav>
      
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/products" element={<Products />}>
          <Route path="car" element={<CarProducts />} />
          <Route path="bike" element={<BikeProducts />} />
        </Route>
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

## Part 10: Understanding Outlet

### What is Outlet?

`<Outlet />` marks where child route content should appear.

### Visual: Outlet Flow

```
<Products>
  <h1>Products Page</h1>
  <Outlet />  ← Child content appears here
</Products>

URL: /products/car
    ↓
<Outlet /> shows <CarProducts />

URL: /products/bike
    ↓
<Outlet /> shows <BikeProducts />
```

---

## Part 11: Nested Routes URL Structure

### URL Paths

```jsx
<Route path="/products" element={<Products />}>
  <Route path="car" element={<CarProducts />} />
  <Route path="bike" element={<BikeProducts />} />
</Route>
```

### Resulting URLs

| URL | What Renders |
|-----|--------------|
| `/products` | Products only |
| `/products/car` | Products + CarProducts |
| `/products/bike` | Products + BikeProducts |

**Child paths are relative to parent path.**

---

## Part 12: NavLink for Active Styling

### What is NavLink?

`NavLink` is like `Link` but knows if it's active (current page).

### NavLink vs Link

```jsx
// Link - no active state
<Link to="/about">About</Link>

// NavLink - knows if active
<NavLink to="/about">About</NavLink>
```

---

## Part 13: Styling Active Links

### NavLink with Styles

```jsx
import { BrowserRouter, Routes, Route, NavLink } from 'react-router-dom';

const navLinkStyles = ({ isActive }) => ({
  color: isActive ? '#007bff' : '#333',
  textDecoration: isActive ? 'none' : 'underline',
  fontWeight: isActive ? 'bold' : 'normal',
  padding: '5px 10px'
});

function Home() {
  return <h1>Home Page</h1>;
}

function About() {
  return <h1>About Page</h1>;
}

function Contact() {
  return <h1>Contact Page</h1>;
}

function App() {
  return (
    <BrowserRouter>
      <nav style={{ marginBottom: '20px' }}>
        <NavLink to="/" style={navLinkStyles}>Home</NavLink> |{" "}
        <NavLink to="/about" style={navLinkStyles}>About</NavLink> |{" "}
        <NavLink to="/contact" style={navLinkStyles}>Contact</NavLink>
      </nav>
      
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </BrowserRouter>
  );
}
```

**Result:** Active link is blue and bold, others are gray and underlined.

---

## Part 14: URL Parameters Introduction

### What are URL Parameters?

URL parameters are variables in your URL path.

**Think of them as placeholders that can change.**

### Example URLs

```
/customer/Emil    ← "Emil" is the parameter
/customer/Tobias  ← "Tobias" is the parameter
/customer/Linus   ← "Linus" is the parameter
```

---

## Part 15: URL Parameters Example

### Using useParams Hook

```jsx
import { BrowserRouter, Routes, Route, Link, useParams } from 'react-router-dom';

function Info() {
  const { firstname } = useParams();
  return <h1>Hello, {firstname}!</h1>;
}

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/customer/Emil">Emil</Link> | 
        <Link to="/customer/Tobias">Tobias</Link> |
        <Link to="/customer/Linus">Linus</Link>
      </nav>
      
      <Routes>
        <Route path="/customer/:firstname" element={<Info />} />
      </Routes>
    </BrowserRouter>
  );
}
```

**Result:** Clicking "Emil" shows "Hello, Emil!", clicking "Tobias" shows "Hello, Tobias!"

---

## Part 16: Understanding URL Parameters

### Route with Parameter

```jsx
<Route path="/customer/:firstname" element={<Info />} />
```

| Part | Description |
|------|-------------|
| `:firstname` | Parameter placeholder |
| `useParams()` | Hook to access parameter |

### Visual: Parameter Flow

```
URL: /customer/John
    ↓
Route: /customer/:firstname
    ↓
useParams() returns: { firstname: "John" }
    ↓
Display: Hello, John!
```

---

## Part 17: Multiple URL Parameters

### Multiple Parameters Example

```jsx
function UserProfile() {
  const { userId, postId } = useParams();
  return (
    <div>
      <h1>User: {userId}</h1>
      <p>Post: {postId}</p>
    </div>
  );
}

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/user/:userId/post/:postId" element={<UserProfile />} />
      </Routes>
    </BrowserRouter>
  );
}
```

**URL:** `/user/123/post/456` shows "User: 123" and "Post: 456"

---

## Part 18: Key Concepts Summary

### Basic Routing

```jsx
<BrowserRouter>
  <Link to="/path">Link</Link>
  
  <Routes>
    <Route path="/path" element={<Component />} />
  </Routes>
</BrowserRouter>
```

### Nested Routes

```jsx
<Route path="/parent" element={<Parent />}>
  <Route path="child" element={<Child />} />
</Route>

// In Parent component:
<Outlet />
```

### URL Parameters

```jsx
// Route
<Route path="/user/:id" element={<User />} />

// Component
function User() {
  const { id } = useParams();
  return <h1>User {id}</h1>;
}
```

### NavLink

```jsx
<NavLink 
  to="/path" 
  style={({ isActive }) => ({
    color: isActive ? 'blue' : 'black'
  })}
>
  Link
</NavLink>
```

---

## Part 19: Quick Reference

### Installation

```bash
npm install react-router-dom
```

### Basic Setup

```jsx
import { BrowserRouter, Routes, Route, Link } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
      </nav>
      
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

### Nested Routes

```jsx
<Routes>
  <Route path="/products" element={<Products />}>
    <Route path="cars" element={<Cars />} />
  </Route>
</Routes>

// In Products:
<Outlet />
```

### URL Parameters

```jsx
<Route path="/user/:id" element={<User />} />

function User() {
  const { id } = useParams();
  return <div>User {id}</div>;
}
```

---

## Part 20: Common Patterns

### Navigation Menu

```jsx
function Navigation() {
  return (
    <nav>
      <NavLink to="/" style={navLinkStyles}>Home</NavLink>
      <NavLink to="/about" style={navLinkStyles}>About</NavLink>
      <NavLink to="/contact" style={navLinkStyles}>Contact</NavLink>
    </nav>
  );
}
```

### Layout with Nested Routes

```jsx
function Layout() {
  return (
    <div>
      <header>Header</header>
      <Outlet />
      <footer>Footer</footer>
    </div>
  );
}

<Route path="/" element={<Layout />}>
  <Route index element={<Home />} />
  <Route path="about" element={<About />} />
</Route>
```

### Dynamic Routes

```jsx
<Routes>
  <Route path="/blog/:postId" element={<BlogPost />} />
  <Route path="/user/:userId/settings" element={<UserSettings />} />
</Routes>
```

---

## What's Next?

In Phase 9, we'll learn about:

### Coming Up: Phase 9 - Styling

- CSS Styling in React

---

*Congratulations! You've completed React Phase 8: Routing. You now understand how to create multi-page navigation in React!*

---

**Keep practicing and see you in Phase 9!** ⚛️
