# JavaScript Day 18: Events - Complete Guide

## Introduction

Events are actions that happen in the browser. When something happens (like a button click or key press), JavaScript can react and do something.

**Think of events as signals that tell JavaScript "something just happened!"**

---

## Part 1: What are Events?

### Event Definition

An event is an action or occurrence that happens in the browser that JavaScript can detect and respond to.

### Common Events Examples

| Event Type | What Happens | Example |
|------------|--------------|---------|
| Click | User clicks something | Button click |
| Load | Page finishes loading | Page ready |
| Mouseover | Mouse moves over element | Hover effect |
| Keydown | User presses a key | Typing |
| Change | Input value changes | Form field edited |

### Visual: Event Flow

```
User Action → Browser detects → Event fires → JavaScript responds
    ↓              ↓                ↓              ↓
  Click         onclick          Event          Code runs
```

---

## Part 2: Three Ways to Handle Events

### Method 1: Inline HTML Attribute (Not Recommended)

```html
<button onclick="alert('Clicked!')">Click Me</button>
```

### Method 2: DOM Property

```html
<button id="myBtn">Click Me</button>

<script>
document.getElementById("myBtn").onclick = function() {
    alert("Clicked!");
};
</script>
```

### Method 3: addEventListener() (Best Way)

```html
<button id="myBtn">Click Me</button>

<script>
const btn = document.getElementById("myBtn");
btn.addEventListener("click", function() {
    alert("Clicked!");
});
</script>
```

### Comparison Table

| Method | Pros | Cons | Recommended |
|--------|------|------|-------------|
| Inline HTML | Quick | Mixes HTML and JS | ❌ No |
| DOM Property | Simple | Only one handler | ⚠️ Sometimes |
| addEventListener | Clean, multiple handlers | Slightly longer | ✅ Yes |

---

## Part 3: Mouse Events

### Common Mouse Events

| Event | When It Fires |
|-------|---------------|
| `click` | Mouse button clicked and released |
| `dblclick` | Mouse button double-clicked |
| `mousedown` | Mouse button pressed down |
| `mouseup` | Mouse button released |
| `mouseover` | Mouse enters element |
| `mouseout` | Mouse leaves element |
| `mouseenter` | Mouse enters element (no bubbling) |
| `mouseleave` | Mouse leaves element (no bubbling) |
| `mousemove` | Mouse moves over element |

### Example 1: Click Event

```html
<button id="btn">Click Me</button>
<p id="demo"></p>

<script>
const btn = document.getElementById("btn");
btn.addEventListener("click", function() {
    document.getElementById("demo").innerHTML = "Button was clicked!";
});
</script>
```

### Example 2: Mouseover and Mouseout

```html
<div id="box" style="width:200px; height:100px; background:blue;">
    Move mouse here
</div>

<script>
const box = document.getElementById("box");

box.addEventListener("mouseover", function() {
    box.style.backgroundColor = "red";
    box.innerHTML = "Mouse is over me!";
});

box.addEventListener("mouseout", function() {
    box.style.backgroundColor = "blue";
    box.innerHTML = "Mouse left!";
});
</script>
```

### Example 3: Mouse Position

```html
<p id="demo">Move mouse to see coordinates</p>

<script>
document.addEventListener("mousemove", function(event) {
    document.getElementById("demo").innerHTML = 
        "X: " + event.clientX + " Y: " + event.clientY;
});
</script>
```

### Visual: Mouse Event Order

```
User clicks mouse:
    ↓
1. mousedown (button pressed)
    ↓
2. mouseup (button released)
    ↓
3. click (complete click)
```

---

## Part 4: Keyboard Events

### Keyboard Events Types

| Event | When It Fires |
|-------|---------------|
| `keydown` | Key is pressed down |
| `keyup` | Key is released |
| `keypress` | Key is pressed (deprecated) |

### Example 1: Detect Key Press

```html
<input type="text" id="myInput" placeholder="Type something">
<p id="demo"></p>

<script>
const input = document.getElementById("myInput");

input.addEventListener("keydown", function(event) {
    document.getElementById("demo").innerHTML = 
        "You pressed: " + event.key;
});
</script>
```

### Example 2: Detect Enter Key

```html
<input type="text" id="myInput" placeholder="Press Enter">
<p id="demo"></p>

<script>
const input = document.getElementById("myInput");

input.addEventListener("keydown", function(event) {
    if (event.code === "Enter") {
        document.getElementById("demo").innerHTML = "Enter was pressed!";
    }
});
</script>
```

### Keyboard Event Properties

| Property | Description | Example |
|----------|-------------|---------|
| `event.key` | The key value | "a", "Enter", "Shift" |
| `event.code` | Physical key code | "KeyA", "Enter", "ShiftLeft" |
| `event.ctrlKey` | Ctrl key pressed? | true/false |
| `event.shiftKey` | Shift key pressed? | true/false |
| `event.altKey` | Alt key pressed? | true/false |

### Example 3: Detect Key Combinations

```html
<input type="text" id="myInput" placeholder="Try Ctrl+S">
<p id="demo"></p>

<script>
const input = document.getElementById("myInput");

input.addEventListener("keydown", function(event) {
    if (event.ctrlKey && event.key === "s") {
        event.preventDefault();  // Stop browser save
        document.getElementById("demo").innerHTML = "Ctrl+S detected!";
    }
});
</script>
```

---

## Part 5: Load Events

### Load Events Types

| Event | When It Fires |
|-------|---------------|
| `DOMContentLoaded` | HTML loaded, DOM ready |
| `load` | Everything loaded (images, CSS, etc.) |

### DOMContentLoaded Event

Fires when HTML is parsed and DOM is ready (doesn't wait for images).

```html
<p id="demo"></p>

<script>
document.addEventListener("DOMContentLoaded", function() {
    document.getElementById("demo").innerHTML = "DOM is ready!";
});
</script>
```

### Window Load Event

Fires when everything is fully loaded (including images).

```html
<p id="demo"></p>

<script>
window.addEventListener("load", function() {
    document.getElementById("demo").innerHTML = "Page fully loaded!";
});
</script>
```

### Visual: Load Event Timeline

```
Browser starts loading
    ↓
HTML parsed
    ↓
DOMContentLoaded fires ← Use this for DOM manipulation
    ↓
Images/CSS load
    ↓
load event fires ← Use this when you need all resources
```

### Example: Image Load Event

```html
<img id="myImg" src="image.jpg" width="200">
<p id="demo"></p>

<script>
const img = document.getElementById("myImg");

img.addEventListener("load", function() {
    document.getElementById("demo").innerHTML = "Image loaded!";
});
</script>
```

---

## Part 6: Form Events

### Common Form Events

| Event | When It Fires |
|-------|---------------|
| `submit` | Form is submitted |
| `change` | Input value changes (after blur) |
| `input` | Input value changes (immediately) |
| `focus` | Element gets focus |
| `blur` | Element loses focus |

### Example 1: Form Submit

```html
<form id="myForm">
    <input type="text" id="username" placeholder="Username">
    <button type="submit">Submit</button>
</form>
<p id="demo"></p>

<script>
const form = document.getElementById("myForm");

form.addEventListener("submit", function(event) {
    event.preventDefault();  // Stop form submission
    const username = document.getElementById("username").value;
    document.getElementById("demo").innerHTML = "Hello, " + username;
});
</script>
```

### Example 2: Input Event (Real-time)

```html
<input type="text" id="myInput" placeholder="Type here">
<p id="demo"></p>

<script>
const input = document.getElementById("myInput");

input.addEventListener("input", function() {
    document.getElementById("demo").innerHTML = 
        "You typed: " + input.value;
});
</script>
```

### Example 3: Change Event (After Blur)

```html
<input type="text" id="myInput" placeholder="Type and click away">
<p id="demo"></p>

<script>
const input = document.getElementById("myInput");

input.addEventListener("change", function() {
    document.getElementById("demo").innerHTML = 
        "Value changed to: " + input.value;
});
</script>
```

### input vs change

| Event | When It Fires | Use Case |
|-------|---------------|----------|
| `input` | Every keystroke | Real-time validation |
| `change` | After losing focus | Final validation |

---

## Part 7: Timing Events

### Timing Functions

| Function | Description | Runs |
|----------|-------------|------|
| `setTimeout()` | Run after delay | Once |
| `setInterval()` | Run repeatedly | Multiple times |
| `clearTimeout()` | Cancel setTimeout | - |
| `clearInterval()` | Cancel setInterval | - |

### setTimeout() - Run Once

```javascript
setTimeout(function, delay);
```

**Example:**

```html
<button id="btn">Start</button>
<p id="demo"></p>

<script>
const btn = document.getElementById("btn");

btn.addEventListener("click", function() {
    setTimeout(function() {
        document.getElementById("demo").innerHTML = "Hello after 2 seconds!";
    }, 2000);
});
</script>
```

### setInterval() - Run Repeatedly

```javascript
setInterval(function, delay);
```

**Example: Simple Clock**

```html
<p id="clock"></p>

<script>
setInterval(function() {
    const now = new Date();
    document.getElementById("clock").innerHTML = 
        now.getHours() + ":" + 
        now.getMinutes() + ":" + 
        now.getSeconds();
}, 1000);
</script>
```

### Example: Start and Stop Counter

```html
<button id="start">Start</button>
<button id="stop">Stop</button>
<p id="counter">0</p>

<script>
let myInterval;
let count = 0;

document.getElementById("start").addEventListener("click", function() {
    myInterval = setInterval(function() {
        count++;
        document.getElementById("counter").innerHTML = count;
    }, 1000);
});

document.getElementById("stop").addEventListener("click", function() {
    clearInterval(myInterval);
});
</script>
```

### Visual: setTimeout vs setInterval

```
setTimeout:
Start → Wait 2s → Run once → Done

setInterval:
Start → Wait 1s → Run → Wait 1s → Run → Wait 1s → Run → ...
```

---

## Part 8: Event Object

### What is the Event Object?

When an event fires, JavaScript creates an event object with information about the event.

### Common Event Object Properties

| Property | Description | Example |
|----------|-------------|---------|
| `event.type` | Type of event | "click", "keydown" |
| `event.target` | Element that triggered event | `<button>` |
| `event.clientX` | Mouse X coordinate | 150 |
| `event.clientY` | Mouse Y coordinate | 200 |
| `event.key` | Key pressed | "a", "Enter" |
| `event.code` | Physical key code | "KeyA" |

### Example: Using Event Object

```html
<button id="btn">Click Me</button>
<p id="demo"></p>

<script>
const btn = document.getElementById("btn");

btn.addEventListener("click", function(event) {
    document.getElementById("demo").innerHTML = 
        "Event type: " + event.type + "<br>" +
        "Target: " + event.target.tagName;
});
</script>
```

---

## Part 9: Event Methods

### preventDefault()

Stops the default action of an event.

**Example: Prevent Link**

```html
<a href="https://www.example.com" id="myLink">Click Me</a>
<p id="demo"></p>

<script>
const link = document.getElementById("myLink");

link.addEventListener("click", function(event) {
    event.preventDefault();  // Stop navigation
    document.getElementById("demo").innerHTML = "Link blocked!";
});
</script>
```

### stopPropagation()

Stops event from bubbling up to parent elements.

```html
<div id="parent" style="padding:20px; background:blue;">
    <button id="child">Click Me</button>
</div>

<script>
document.getElementById("parent").addEventListener("click", function() {
    alert("Parent clicked");
});

document.getElementById("child").addEventListener("click", function(event) {
    event.stopPropagation();  // Stop bubbling to parent
    alert("Child clicked");
});
</script>
```

---

## Part 10: Event Bubbling and Capturing

### Event Propagation

When an event happens on an element, it propagates (travels) through the DOM.

### Two Phases

| Phase | Direction | Order |
|-------|-----------|-------|
| Capturing | Top to bottom | Parent → Child |
| Bubbling | Bottom to top | Child → Parent |

### Visual: Event Propagation

```
HTML Structure:
<div id="parent">
    <button id="child">Click</button>
</div>

Capturing Phase (top to bottom):
document → html → body → div → button

Bubbling Phase (bottom to top):
button → div → body → html → document
```

### Example: Bubbling (Default)

```html
<div id="parent" style="padding:20px; background:lightblue;">
    Parent
    <button id="child">Child</button>
</div>
<p id="demo"></p>

<script>
document.getElementById("parent").addEventListener("click", function() {
    document.getElementById("demo").innerHTML += "Parent clicked<br>";
});

document.getElementById("child").addEventListener("click", function() {
    document.getElementById("demo").innerHTML += "Child clicked<br>";
});
</script>
```

**When you click the button:**
```
Child clicked
Parent clicked  ← Event bubbled up
```

### Example: Capturing

```javascript
// Third parameter true = use capturing
element.addEventListener("click", function() {
    // code
}, true);
```

---

## Part 11: Adding and Removing Event Listeners

### Adding Event Listener

```javascript
element.addEventListener("click", myFunction);
```

### Removing Event Listener

```javascript
element.removeEventListener("click", myFunction);
```

**Important:** Must use the same named function!

### Example: Add and Remove

```html
<button id="add">Add Listener</button>
<button id="remove">Remove Listener</button>
<button id="test">Test Click</button>
<p id="demo"></p>

<script>
const test = document.getElementById("test");

function myFunction() {
    document.getElementById("demo").innerHTML += "Clicked!<br>";
}

document.getElementById("add").addEventListener("click", function() {
    test.addEventListener("click", myFunction);
});

document.getElementById("remove").addEventListener("click", function() {
    test.removeEventListener("click", myFunction);
});
</script>
```

---

## Part 12: Multiple Event Handlers

### Same Element, Multiple Handlers

You can add multiple event listeners to the same element:

```html
<button id="btn">Click Me</button>
<p id="demo"></p>

<script>
const btn = document.getElementById("btn");

btn.addEventListener("click", function() {
    document.getElementById("demo").innerHTML = "First handler<br>";
});

btn.addEventListener("click", function() {
    document.getElementById("demo").innerHTML += "Second handler<br>";
});

btn.addEventListener("click", function() {
    document.getElementById("demo").innerHTML += "Third handler<br>";
});
</script>
```

**Output when clicked:**
```
First handler
Second handler
Third handler
```

---

## Part 13: Practical Examples

### Example 1: Toggle Button

```html
<button id="toggleBtn">Show</button>
<p id="content" style="display:none;">This is hidden content</p>

<script>
const btn = document.getElementById("toggleBtn");
const content = document.getElementById("content");

btn.addEventListener("click", function() {
    if (content.style.display === "none") {
        content.style.display = "block";
        btn.textContent = "Hide";
    } else {
        content.style.display = "none";
        btn.textContent = "Show";
    }
});
</script>
```

### Example 2: Character Counter

```html
<textarea id="myText" maxlength="100"></textarea>
<p id="counter">0 / 100</p>

<script>
const textarea = document.getElementById("myText");

textarea.addEventListener("input", function() {
    const length = textarea.value.length;
    document.getElementById("counter").innerHTML = length + " / 100";
});
</script>
```

### Example 3: Form Validation

```html
<form id="myForm">
    <input type="text" id="username" placeholder="Username (min 3 chars)">
    <button type="submit">Submit</button>
    <p id="error" style="color:red;"></p>
</form>

<script>
const form = document.getElementById("myForm");
const input = document.getElementById("username");
const error = document.getElementById("error");

form.addEventListener("submit", function(event) {
    if (input.value.length < 3) {
        event.preventDefault();
        error.textContent = "Username must be at least 3 characters!";
    } else {
        error.textContent = "";
    }
});
</script>
```

### Example 4: Dropdown Menu

```html
<button id="menuBtn">Menu</button>
<div id="dropdown" style="display:none; background:#f1f1f1; padding:10px;">
    <a href="#">Home</a><br>
    <a href="#">About</a><br>
    <a href="#">Contact</a>
</div>

<script>
const menuBtn = document.getElementById("menuBtn");
const dropdown = document.getElementById("dropdown");

menuBtn.addEventListener("click", function() {
    if (dropdown.style.display === "none") {
        dropdown.style.display = "block";
    } else {
        dropdown.style.display = "none";
    }
});

// Close dropdown when clicking outside
document.addEventListener("click", function(event) {
    if (event.target !== menuBtn && event.target.parentElement !== dropdown) {
        dropdown.style.display = "none";
    }
});
</script>
```

### Example 5: Image Gallery

```html
<div>
    <img class="thumbnail" src="img1.jpg" width="100">
    <img class="thumbnail" src="img2.jpg" width="100">
    <img class="thumbnail" src="img3.jpg" width="100">
</div>
<img id="mainImage" src="img1.jpg" width="400">

<script>
const thumbnails = document.querySelectorAll(".thumbnail");
const mainImage = document.getElementById("mainImage");

thumbnails.forEach(function(thumb) {
    thumb.addEventListener("click", function() {
        mainImage.src = thumb.src;
    });
});
</script>
```

---

## Part 14: Common Mistakes

### Mistake 1: Using "on" Prefix

```javascript
// Wrong ❌
element.addEventListener("onclick", myFunction);

// Correct ✅
element.addEventListener("click", myFunction);
```

### Mistake 2: Forgetting preventDefault()

```javascript
// Form will submit and refresh page ❌
form.addEventListener("submit", function() {
    alert("Submitted");
});

// Correct ✅
form.addEventListener("submit", function(event) {
    event.preventDefault();
    alert("Submitted");
});
```

### Mistake 3: Anonymous Function in removeEventListener

```javascript
// This won't work ❌
element.addEventListener("click", function() {
    alert("Hi");
});
element.removeEventListener("click", function() {
    alert("Hi");
});

// Correct ✅
function myFunction() {
    alert("Hi");
}
element.addEventListener("click", myFunction);
element.removeEventListener("click", myFunction);
```

### Mistake 4: Not Using Event Parameter

```javascript
// Missing event parameter ❌
input.addEventListener("keydown", function() {
    if (code === "Enter") {  // code is undefined
        // ...
    }
});

// Correct ✅
input.addEventListener("keydown", function(event) {
    if (event.code === "Enter") {
        // ...
    }
});
```

---

## Part 15: Event Reference Table

### Complete Event List

| Category | Events |
|----------|--------|
| Mouse | click, dblclick, mousedown, mouseup, mouseover, mouseout, mouseenter, mouseleave, mousemove |
| Keyboard | keydown, keyup |
| Form | submit, change, input, focus, blur, reset |
| Window | load, resize, scroll, unload |
| Document | DOMContentLoaded |
| Clipboard | copy, cut, paste |
| Drag | drag, dragstart, dragend, dragover, drop |

---

## Part 16: Key Takeaways

### ✅ Remember These Points

1. **addEventListener()** is the best way to handle events
2. **Event object** contains information about the event
3. **preventDefault()** stops default behavior
4. **stopPropagation()** stops event bubbling
5. **Mouse events**: click, mouseover, mouseout
6. **Keyboard events**: keydown, keyup
7. **Form events**: submit, input, change
8. **Load events**: DOMContentLoaded, load
9. **setTimeout()** runs once, **setInterval()** runs repeatedly
10. Use named functions for removeEventListener

### Event Handling Quick Reference

```javascript
// Add event listener
element.addEventListener("click", function(event) {
    // Your code here
});

// Remove event listener (must use named function)
function myFunction(event) {
    // Your code
}
element.addEventListener("click", myFunction);
element.removeEventListener("click", myFunction);

// Prevent default action
event.preventDefault();

// Stop bubbling
event.stopPropagation();

// Timing events
setTimeout(function() {
    // Run once after delay
}, 2000);

let interval = setInterval(function() {
    // Run repeatedly
}, 1000);
clearInterval(interval);  // Stop interval
```

---

## What's Next?

In the next lesson, we'll learn about:

### Coming Up: JavaScript Day 19

- Advanced array methods (map, filter, reduce)
- Array iteration techniques
- Working with array of objects
- Practical array applications
- Performance considerations

---

*Congratulations! You've completed JavaScript Day 18. You now understand events and how to make interactive web pages!*

---

**Practice event handling and see you in the next class!** 🚀
