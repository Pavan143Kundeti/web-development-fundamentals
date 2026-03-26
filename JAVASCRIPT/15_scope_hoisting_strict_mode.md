# JavaScript Day 15: Scope, Hoisting, and Strict Mode

## Introduction

Understanding scope, hoisting, and strict mode is essential for writing clean, bug-free JavaScript code. These concepts control where variables can be accessed and how JavaScript executes your code.

---

## Part 1: What is Scope?

### Scope Definition

Scope determines where variables can be accessed in your code. It's like asking: "Where is this variable visible?"

### Three Types of Scope

```
JavaScript Scope
├── 1. Global Scope (accessible everywhere)
├── 2. Function Scope (accessible inside function)
└── 3. Block Scope (accessible inside block {})
```

---

## Part 2: Global Scope

### What is Global Scope?

Variables declared outside any function or block have global scope - they can be accessed from anywhere.

```javascript
let name = "John";  // Global variable

function greet() {
    console.log(name);  // Can access global variable
}

greet();  // Output: John
console.log(name);  // Output: John
```

### Visual: Global Scope

```
┌─────────────────────────────────────┐
│  Global Scope                       │
│                                     │
│  let x = 10;  ← Accessible          │
│                 everywhere          │
│  ┌───────────────────────────────┐ │
│  │  Function                     │ │
│  │  console.log(x);  ← Works!    │ │
│  └───────────────────────────────┘ │
│                                     │
│  console.log(x);  ← Works!          │
└─────────────────────────────────────┘
```

### All Three Keywords Work the Same Globally

```javascript
var x = 1;    // Global scope
let y = 2;    // Global scope
const z = 3;  // Global scope

// All accessible everywhere
```

---

## Part 3: Function Scope

### What is Function Scope?

Variables declared inside a function are LOCAL - they only exist inside that function.

```javascript
function myFunction() {
    let carName = "Volvo";  // Local variable
    console.log(carName);   // Works here
}

myFunction();
console.log(carName);  // Error! carName doesn't exist here
```

### Visual: Function Scope

```
┌─────────────────────────────────────┐
│  Global Scope                       │
│                                     │
│  ┌───────────────────────────────┐ │
│  │  Function Scope               │ │
│  │                               │ │
│  │  let x = 10;  ← Only          │ │
│  │               accessible      │ │
│  │               inside          │ │
│  │               function        │ │
│  └───────────────────────────────┘ │
│                                     │
│  console.log(x);  ← Error!          │
└─────────────────────────────────────┘
```

### All Three Keywords Work the Same in Functions

```javascript
function test1() {
    var x = 1;  // Function scope
}

function test2() {
    let y = 2;  // Function scope
}

function test3() {
    const z = 3;  // Function scope
}
```

### Same Variable Name in Different Functions

```javascript
function func1() {
    let name = "John";
    console.log(name);  // Output: John
}

function func2() {
    let name = "Jane";  // Different variable!
    console.log(name);  // Output: Jane
}

func1();
func2();
```

---

## Part 4: Block Scope

### What is Block Scope?

A block is code inside curly braces `{}`. Variables declared with `let` and `const` inside a block are only accessible inside that block.

```javascript
{
    let x = 10;
    console.log(x);  // Works here
}

console.log(x);  // Error! x doesn't exist here
```

### let and const Have Block Scope

```javascript
{
    let x = 2;
    const y = 3;
}

// x and y cannot be used here
```

### var Does NOT Have Block Scope

```javascript
{
    var x = 2;
}

// x CAN be used here (not recommended!)
console.log(x);  // Output: 2
```

### Comparison Table

| Keyword | Global Scope | Function Scope | Block Scope |
|---------|--------------|----------------|-------------|
| `var` | ✅ Yes | ✅ Yes | ❌ No |
| `let` | ✅ Yes | ✅ Yes | ✅ Yes |
| `const` | ✅ Yes | ✅ Yes | ✅ Yes |

---

## Part 5: Block Scope Examples

### Example 1: if Statement

```javascript
if (true) {
    let x = 10;
    console.log(x);  // Output: 10
}

console.log(x);  // Error! x not accessible
```

### Example 2: for Loop

```javascript
for (let i = 0; i < 3; i++) {
    console.log(i);  // Works
}

console.log(i);  // Error! i not accessible
```

### Example 3: Standalone Block

```javascript
{
    let x = 10;
    let y = 20;
    let area = x * y;
    console.log(area);  // Output: 200
}

console.log(x);  // Error! x not accessible
```

**Why use standalone blocks?**
- Keep variables temporary
- Avoid polluting global scope
- Prevent name conflicts

---

## Part 6: Scope Chain

### How JavaScript Looks for Variables

JavaScript searches for variables from inner to outer scope:

```javascript
let global = "Global";

function outer() {
    let outerVar = "Outer";
    
    function inner() {
        let innerVar = "Inner";
        
        console.log(innerVar);   // Found in inner scope
        console.log(outerVar);   // Found in outer scope
        console.log(global);     // Found in global scope
    }
    
    inner();
}

outer();
```

### Visual: Scope Chain

```
┌─────────────────────────────────────┐
│  Global Scope                       │
│  let global = "Global"              │
│                                     │
│  ┌───────────────────────────────┐ │
│  │  Outer Function Scope         │ │
│  │  let outerVar = "Outer"       │ │
│  │                               │ │
│  │  ┌─────────────────────────┐ │ │
│  │  │  Inner Function Scope   │ │ │
│  │  │  let innerVar = "Inner" │ │ │
│  │  │                         │ │ │
│  │  │  Can access:            │ │ │
│  │  │  - innerVar ✅          │ │ │
│  │  │  - outerVar ✅          │ │ │
│  │  │  - global ✅            │ │ │
│  │  └─────────────────────────┘ │ │
│  └───────────────────────────────┘ │
└─────────────────────────────────────┘
```

---

## Part 7: Hoisting

### What is Hoisting?

Hoisting is JavaScript's behavior of moving declarations to the top of the scope before code execution.

### var is Hoisted

```javascript
console.log(x);  // Output: undefined (not error!)
var x = 5;
```

**JavaScript sees it as:**

```javascript
var x;           // Declaration moved to top
console.log(x);  // undefined
x = 5;           // Assignment stays here
```

### let and const Are NOT Hoisted (Temporal Dead Zone)

```javascript
console.log(x);  // Error! Cannot access before initialization
let x = 5;
```

### Hoisting Comparison

| Keyword | Hoisted? | Can Use Before Declaration? |
|---------|----------|----------------------------|
| `var` | ✅ Yes | ✅ Yes (value is undefined) |
| `let` | ❌ No | ❌ No (ReferenceError) |
| `const` | ❌ No | ❌ No (SyntaxError) |

---

## Part 8: Hoisting Examples

### Example 1: var Hoisting

```javascript
// What you write
x = 5;
console.log(x);  // Output: 5
var x;

// What JavaScript executes
var x;
x = 5;
console.log(x);
```

### Example 2: Function Hoisting

```javascript
// This works! ✅
greet();

function greet() {
    console.log("Hello");
}
```

**Functions are fully hoisted!**

### Example 3: let Not Hoisted

```javascript
// This fails! ❌
console.log(x);  // ReferenceError
let x = 5;
```

---

## Part 9: Best Practices for Scope

### Rule 1: Always Declare Variables at the Top

```javascript
// Good ✅
function myFunction() {
    let x = 10;
    let y = 20;
    
    // Use variables
    console.log(x + y);
}

// Bad ❌
function myFunction() {
    console.log(x + y);
    
    let x = 10;  // Declared too late
    let y = 20;
}
```

### Rule 2: Use let and const, Not var

```javascript
// Good ✅
let x = 10;
const y = 20;

// Bad ❌
var x = 10;
```

### Rule 3: Avoid Global Variables

```javascript
// Bad ❌
let globalVar = 10;

function test() {
    globalVar = 20;  // Modifying global
}

// Good ✅
function test() {
    let localVar = 10;  // Keep it local
    return localVar;
}
```

---

## Part 10: Strict Mode

### What is Strict Mode?

Strict mode makes JavaScript stricter and catches common mistakes.

### How to Enable Strict Mode

```javascript
"use strict";

// Your code here
```

### Strict Mode in Functions

```javascript
function myFunction() {
    "use strict";
    // Strict mode only in this function
}
```

---

## Part 11: Strict Mode Rules

### Rule 1: Must Declare Variables

```javascript
"use strict";

x = 10;  // Error! x is not declared
```

### Rule 2: Cannot Delete Variables

```javascript
"use strict";

let x = 10;
delete x;  // Error! Cannot delete variable
```

### Rule 3: No Duplicate Parameters

```javascript
"use strict";

function test(a, a) {  // Error! Duplicate parameter
    return a;
}
```

### Rule 4: Cannot Use Reserved Words

```javascript
"use strict";

let public = 10;  // Error! 'public' is reserved
```

---

## Part 12: Why Use Strict Mode?

### Benefits of Strict Mode

| Benefit | Description |
|---------|-------------|
| Catches errors | Prevents silent errors |
| Prevents bad syntax | Disallows problematic code |
| Safer code | Reduces bugs |
| Better performance | Easier for engines to optimize |

### Example: Catching Typos

```javascript
"use strict";

let userName = "John";
usrName = "Jane";  // Error! Typo caught!
```

Without strict mode, this creates a new global variable!

---

## Part 13: Practical Examples

### Example 1: Counter with Closure

```javascript
function createCounter() {
    let count = 0;  // Private variable
    
    return function() {
        count++;
        return count;
    };
}

const counter = createCounter();
console.log(counter());  // Output: 1
console.log(counter());  // Output: 2
console.log(counter());  // Output: 3
```

### Example 2: Module Pattern

```javascript
const calculator = (function() {
    let result = 0;  // Private
    
    return {
        add: function(x) {
            result += x;
            return result;
        },
        subtract: function(x) {
            result -= x;
            return result;
        },
        getResult: function() {
            return result;
        }
    };
})();

console.log(calculator.add(5));       // Output: 5
console.log(calculator.add(3));       // Output: 8
console.log(calculator.subtract(2));  // Output: 6
```

### Example 3: Loop with Block Scope

```javascript
// Using let (block scope) ✅
for (let i = 0; i < 3; i++) {
    setTimeout(function() {
        console.log(i);
    }, 1000);
}
// Output: 0, 1, 2

// Using var (function scope) ❌
for (var i = 0; i < 3; i++) {
    setTimeout(function() {
        console.log(i);
    }, 1000);
}
// Output: 3, 3, 3 (not what we want!)
```

---

## Part 14: Common Mistakes

### Mistake 1: Forgetting to Declare

```javascript
function test() {
    x = 10;  // Creates global variable! ❌
}

test();
console.log(x);  // Output: 10 (global pollution)
```

**Fix:**

```javascript
function test() {
    let x = 10;  // Local variable ✅
}
```

### Mistake 2: Using var in Loops

```javascript
// Wrong ❌
for (var i = 0; i < 3; i++) {
    // i leaks outside loop
}
console.log(i);  // Output: 3

// Correct ✅
for (let i = 0; i < 3; i++) {
    // i stays inside loop
}
console.log(i);  // Error! i not defined
```

### Mistake 3: Accessing Before Declaration

```javascript
// Wrong ❌
console.log(x);  // Error!
let x = 10;

// Correct ✅
let x = 10;
console.log(x);  // Output: 10
```

---

## Part 15: Scope Summary Table

### Variable Accessibility

| Declaration | Global | Function | Block | Hoisted |
|-------------|--------|----------|-------|---------|
| `var` | ✅ | ✅ | ❌ | ✅ Yes |
| `let` | ✅ | ✅ | ✅ | ❌ No |
| `const` | ✅ | ✅ | ✅ | ❌ No |

---

## Part 16: Key Takeaways

### ✅ Remember These Points

1. **Scope** determines where variables can be accessed
2. **Global scope** - accessible everywhere
3. **Function scope** - accessible only inside function
4. **Block scope** - accessible only inside block `{}`
5. **let and const** have block scope
6. **var** does NOT have block scope (avoid it!)
7. **Hoisting** moves declarations to top
8. **var is hoisted**, let and const are not
9. **Strict mode** catches common mistakes
10. Always declare variables at the top

### Best Practices

```javascript
"use strict";  // Always use strict mode

// Declare at top
let x = 10;
const y = 20;

function myFunction() {
    // Declare at top of function
    let a = 5;
    let b = 10;
    
    // Use variables
    return a + b;
}
```

---

## What's Next?

In the next lesson, we'll learn about:

### Coming Up: JavaScript Day 16

- Arrays introduction
- Creating and accessing arrays
- Array methods (push, pop, shift, unshift)
- Looping through arrays
- Array manipulation

---

*Congratulations! You've completed JavaScript Day 15. You now understand scope, hoisting, and strict mode!*

---

**Practice with scope and see you in the next class!** 🚀
