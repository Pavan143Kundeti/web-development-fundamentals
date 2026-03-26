# JavaScript Day 17: DOM - Document Object Model

## Introduction

The DOM (Document Object Model) is how JavaScript interacts with HTML. It allows you to change the content, structure, and style of a webpage dynamically.

**Think of the DOM as a bridge between HTML and JavaScript.**

---

## Part 1: What is the DOM?

### DOM Definition

The DOM is a tree-like representation of an HTML document that JavaScript can access and manipulate.

### Visual: DOM Tree

```
document
    ↓
  <html>
    ↓
  ┌─────┴─────┐
  ↓           ↓
<head>      <body>
  ↓           ↓
<title>    ┌──┴──┐
           ↓     ↓
         <h1>  <p>
           ↓     ↓
        "Title" "Text"
```

### DOM Nodes

Everything in the HTML document is a node:

| Node Type | Description | Example |
|-----------|-------------|---------|
| Document | The entire document | `document` |
| Element | HTML tags | `<div>`, `<p>`, `<h1>` |
| Text | Text content | "Hello World" |
| Attribute | Element attributes | `id="demo"` |

---

## Part 2: Accessing HTML Elements

### Method 1: getElementById()

Get element by its ID (most common):

```javascript
const element = document.getElementById("demo");
```

**HTML:**
```html
<p id="demo">Hello</p>
```

**JavaScript:**
```javascript
const para = document.getElementById("demo");
console.log(para);  // <p id="demo">Hello</p>
```

### Method 2: getElementsByClassName()

Get all elements with a specific class:

```javascript
const elements = document.getElementsByClassName("intro");
```

**HTML:**
```html
<p class="intro">First</p>
<p class="intro">Second</p>
```

**JavaScript:**
```javascript
const paras = document.getElementsByClassName("intro");
console.log(paras.length);  // 2
```

### Method 3: getElementsByTagName()

Get all elements with a specific tag:

```javascript
const elements = document.getElementsByTagName("p");
```

**HTML:**
```html
<p>First paragraph</p>
<p>Second paragraph</p>
```

**JavaScript:**
```javascript
const paras = document.getElementsByTagName("p");
console.log(paras.length);  // 2
```

### Method 4: querySelector()

Get the FIRST element matching a CSS selector:

```javascript
const element = document.querySelector(".intro");
```

**HTML:**
```html
<p class="intro">First</p>
<p class="intro">Second</p>
```

**JavaScript:**
```javascript
const para = document.querySelector(".intro");
console.log(para.textContent);  // First
```

### Method 5: querySelectorAll()

Get ALL elements matching a CSS selector:

```javascript
const elements = document.querySelectorAll(".intro");
```

**HTML:**
```html
<p class="intro">First</p>
<p class="intro">Second</p>
```

**JavaScript:**
```javascript
const paras = document.querySelectorAll(".intro");
console.log(paras.length);  // 2
```

---

## Part 3: Selection Methods Comparison

### Comparison Table

| Method | Returns | Selector Type | Example |
|--------|---------|---------------|---------|
| `getElementById()` | Single element | ID | `getElementById("demo")` |
| `getElementsByClassName()` | Collection | Class | `getElementsByClassName("intro")` |
| `getElementsByTagName()` | Collection | Tag | `getElementsByTagName("p")` |
| `querySelector()` | First match | CSS | `querySelector(".intro")` |
| `querySelectorAll()` | All matches | CSS | `querySelectorAll(".intro")` |

### When to Use What

```javascript
// Use getElementById for single element with ID
const element = document.getElementById("demo");

// Use querySelector for CSS selectors (modern way)
const element = document.querySelector("#demo");
const element = document.querySelector(".intro");
const element = document.querySelector("p.intro");

// Use querySelectorAll for multiple elements
const elements = document.querySelectorAll(".intro");
```

---

## Part 4: Changing HTML Content

### innerHTML Property

Change the HTML content inside an element:

```javascript
const element = document.getElementById("demo");
element.innerHTML = "New content!";
```

**HTML Before:**
```html
<p id="demo">Old content</p>
```

**JavaScript:**
```javascript
document.getElementById("demo").innerHTML = "New content!";
```

**HTML After:**
```html
<p id="demo">New content!</p>
```

### textContent Property

Change only the text (no HTML):

```javascript
const element = document.getElementById("demo");
element.textContent = "New text!";
```

### innerHTML vs textContent

```javascript
const element = document.getElementById("demo");

// innerHTML - interprets HTML tags
element.innerHTML = "<strong>Bold text</strong>";
// Result: Bold text (actually bold)

// textContent - treats everything as text
element.textContent = "<strong>Bold text</strong>";
// Result: <strong>Bold text</strong> (shows tags as text)
```

---

## Part 5: Changing Attributes

### Direct Attribute Access

```javascript
const img = document.getElementById("myImage");
img.src = "newimage.jpg";
img.alt = "New description";
```

**HTML:**
```html
<img id="myImage" src="old.jpg" alt="Old">
```

**JavaScript:**
```javascript
const img = document.getElementById("myImage");
img.src = "new.jpg";
img.alt = "New image";
```

### setAttribute() Method

```javascript
const element = document.getElementById("demo");
element.setAttribute("class", "highlight");
```

### getAttribute() Method

```javascript
const element = document.getElementById("demo");
let value = element.getAttribute("class");
console.log(value);
```

---

## Part 6: Changing CSS Styles

### style Property

Change CSS styles directly:

```javascript
const element = document.getElementById("demo");
element.style.color = "red";
element.style.fontSize = "20px";
element.style.backgroundColor = "yellow";
```

**HTML:**
```html
<p id="demo">Hello World</p>
```

**JavaScript:**
```javascript
const para = document.getElementById("demo");
para.style.color = "blue";
para.style.fontSize = "24px";
```

**Result:** Blue text, 24px size

### CSS Property Names in JavaScript

CSS properties with hyphens become camelCase:

| CSS Property | JavaScript Property |
|--------------|-------------------|
| `background-color` | `backgroundColor` |
| `font-size` | `fontSize` |
| `margin-top` | `marginTop` |
| `border-radius` | `borderRadius` |

### Example: Multiple Styles

```javascript
const element = document.getElementById("demo");
element.style.color = "white";
element.style.backgroundColor = "black";
element.style.padding = "10px";
element.style.borderRadius = "5px";
```

---

## Part 7: Adding and Removing Classes

### className Property

```javascript
const element = document.getElementById("demo");
element.className = "highlight";
```

### classList Property (Better)

```javascript
const element = document.getElementById("demo");

// Add class
element.classList.add("highlight");

// Remove class
element.classList.remove("highlight");

// Toggle class (add if not present, remove if present)
element.classList.toggle("highlight");

// Check if class exists
if (element.classList.contains("highlight")) {
    console.log("Has highlight class");
}
```

---

## Part 8: Creating and Adding Elements

### createElement()

Create a new element:

```javascript
const newPara = document.createElement("p");
newPara.textContent = "This is a new paragraph";
```

### appendChild()

Add element to the end:

```javascript
const newPara = document.createElement("p");
newPara.textContent = "New paragraph";

const container = document.getElementById("container");
container.appendChild(newPara);
```

### Complete Example

**HTML:**
```html
<div id="container">
    <p>Existing paragraph</p>
</div>
```

**JavaScript:**
```javascript
// Create new element
const newPara = document.createElement("p");
newPara.textContent = "New paragraph";
newPara.style.color = "blue";

// Add to container
const container = document.getElementById("container");
container.appendChild(newPara);
```

**Result:**
```html
<div id="container">
    <p>Existing paragraph</p>
    <p style="color: blue;">New paragraph</p>
</div>
```

---

## Part 9: Removing Elements

### removeChild()

```javascript
const parent = document.getElementById("container");
const child = document.getElementById("demo");
parent.removeChild(child);
```

### remove() (Modern Way)

```javascript
const element = document.getElementById("demo");
element.remove();
```

---

## Part 10: Event Handling

### What are Events?

Events are actions that happen in the browser:
- User clicks a button
- Page finishes loading
- User types in input field
- Mouse moves over element

### onclick Event

```javascript
const button = document.getElementById("myButton");
button.onclick = function() {
    alert("Button clicked!");
};
```

**HTML:**
```html
<button id="myButton">Click Me</button>
```

**JavaScript:**
```javascript
const button = document.getElementById("myButton");
button.onclick = function() {
    alert("Button clicked!");
};
```

### addEventListener() (Better Way)

```javascript
const button = document.getElementById("myButton");
button.addEventListener("click", function() {
    alert("Button clicked!");
});
```

### Common Events

| Event | Description | Example |
|-------|-------------|---------|
| `click` | Element is clicked | Button click |
| `mouseover` | Mouse moves over element | Hover effect |
| `mouseout` | Mouse leaves element | Hover ends |
| `keydown` | Key is pressed | Typing |
| `load` | Page finishes loading | Page ready |
| `change` | Input value changes | Form input |

---

## Part 11: Practical Examples

### Example 1: Change Text on Click

**HTML:**
```html
<p id="demo">Original text</p>
<button id="btn">Change Text</button>
```

**JavaScript:**
```javascript
const button = document.getElementById("btn");
button.addEventListener("click", function() {
    document.getElementById("demo").textContent = "Text changed!";
});
```

### Example 2: Toggle Visibility

**HTML:**
```html
<p id="demo">This text can be hidden</p>
<button id="toggleBtn">Toggle</button>
```

**JavaScript:**
```javascript
const button = document.getElementById("toggleBtn");
const para = document.getElementById("demo");

button.addEventListener("click", function() {
    if (para.style.display === "none") {
        para.style.display = "block";
    } else {
        para.style.display = "none";
    }
});
```

### Example 3: Change Color on Hover

**HTML:**
```html
<div id="box" style="width:100px; height:100px; background:blue;"></div>
```

**JavaScript:**
```javascript
const box = document.getElementById("box");

box.addEventListener("mouseover", function() {
    box.style.backgroundColor = "red";
});

box.addEventListener("mouseout", function() {
    box.style.backgroundColor = "blue";
});
```

### Example 4: Add Items to List

**HTML:**
```html
<input type="text" id="itemInput" placeholder="Enter item">
<button id="addBtn">Add Item</button>
<ul id="itemList"></ul>
```

**JavaScript:**
```javascript
const button = document.getElementById("addBtn");
const input = document.getElementById("itemInput");
const list = document.getElementById("itemList");

button.addEventListener("click", function() {
    const newItem = document.createElement("li");
    newItem.textContent = input.value;
    list.appendChild(newItem);
    input.value = "";  // Clear input
});
```

### Example 5: Form Validation

**HTML:**
```html
<form id="myForm">
    <input type="text" id="username" placeholder="Username">
    <button type="submit">Submit</button>
    <p id="error" style="color:red;"></p>
</form>
```

**JavaScript:**
```javascript
const form = document.getElementById("myForm");
const input = document.getElementById("username");
const error = document.getElementById("error");

form.addEventListener("submit", function(event) {
    if (input.value === "") {
        event.preventDefault();  // Stop form submission
        error.textContent = "Username is required!";
    }
});
```

---

## Part 12: DOM Traversal

### Parent, Child, Sibling

```javascript
const element = document.getElementById("demo");

// Parent
const parent = element.parentElement;

// Children
const children = element.children;
const firstChild = element.firstElementChild;
const lastChild = element.lastElementChild;

// Siblings
const nextSibling = element.nextElementSibling;
const prevSibling = element.previousElementSibling;
```

### Visual: DOM Relationships

```
        parent
           ↓
    ┌──────┴──────┐
    ↓             ↓
previous ←→ element ←→ next
sibling              sibling
    ↓
  child
```

---

## Part 13: Common Mistakes

### Mistake 1: Accessing Element Before It Exists

```javascript
// Wrong ❌ - Script runs before HTML loads
const element = document.getElementById("demo");
element.textContent = "Hello";
```

**Fix:** Put script at end of body or use DOMContentLoaded:

```javascript
// Correct ✅
document.addEventListener("DOMContentLoaded", function() {
    const element = document.getElementById("demo");
    element.textContent = "Hello";
});
```

### Mistake 2: Forgetting Quotes in getElementById

```javascript
// Wrong ❌
document.getElementById(demo)

// Correct ✅
document.getElementById("demo")
```

### Mistake 3: Using # in getElementById

```javascript
// Wrong ❌
document.getElementById("#demo")

// Correct ✅
document.getElementById("demo")

// Use # only in querySelector
document.querySelector("#demo")  // ✅
```

---

## Part 14: Key Takeaways

### ✅ Remember These Points

1. **DOM** is a tree representation of HTML
2. **getElementById()** gets element by ID
3. **querySelector()** uses CSS selectors (modern way)
4. **innerHTML** changes HTML content
5. **textContent** changes text only
6. **style** property changes CSS
7. **classList** manages classes
8. **addEventListener()** handles events
9. **createElement()** creates new elements
10. Always access DOM after page loads

### DOM Methods Quick Reference

```javascript
// Select elements
document.getElementById("demo")
document.querySelector(".class")
document.querySelectorAll(".class")

// Change content
element.innerHTML = "New HTML"
element.textContent = "New text"

// Change attributes
element.src = "image.jpg"
element.setAttribute("class", "highlight")

// Change styles
element.style.color = "red"
element.classList.add("highlight")

// Create/Remove elements
document.createElement("p")
parent.appendChild(child)
element.remove()

// Events
element.addEventListener("click", function() {
    // code
})
```

---

## What's Next?

In the next lesson, we'll learn about:

### Coming Up: JavaScript Day 18

- Advanced DOM manipulation
- Event delegation
- Working with forms
- Creating interactive web applications
- Best practices for DOM manipulation

---

*Congratulations! You've completed JavaScript Day 17. You now understand the DOM and how JavaScript interacts with HTML!*

---

**Practice DOM manipulation and see you in the next class!** 🚀
