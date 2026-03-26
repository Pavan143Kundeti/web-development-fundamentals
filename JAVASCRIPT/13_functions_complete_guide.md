# JavaScript Day 13: Functions - Complete Guide

## Introduction

Functions are reusable blocks of code that perform specific tasks. They are one of the most important concepts in programming.

**Why use functions?**
- Write code once, use it many times
- Organize code into smaller parts
- Make code easier to read and maintain
- Avoid repeating the same code

---

## Part 1: What is a Function?

### Function Definition

A function is a block of code designed to perform a particular task. The code runs only when you call the function.

### Basic Structure

```
┌─────────────────────────────────────┐
│  function name(parameters) {        │
│      // code to execute             │
│      return result;                 │
│  }                                  │
└─────────────────────────────────────┘
```

### Simple Example

```javascript
function sayHello() {
    return "Hello World";
}
```

**Important:** This function doesn't run automatically. You must call it!

---

## Part 2: Creating Functions

### Function Syntax

```javascript
function functionName(parameter1, parameter2) {
    // code to execute
    return value;
}
```

### Parts of a Function

| Part | Description | Example |
|------|-------------|---------|
| `function` | Keyword to create function | `function` |
| Name | Function identifier | `sayHello` |
| Parameters | Input values (optional) | `(name)` |
| Body | Code to execute | `{ return "Hi"; }` |
| Return | Output value (optional) | `return result;` |

### Example: Simple Function

```javascript
function greet() {
    return "Hello!";
}
```

### Example: Function with Parameters

```javascript
function add(a, b) {
    return a + b;
}
```

---

## Part 3: Calling Functions

### How to Call a Function

Use the function name followed by parentheses `()`:

```javascript
function sayHello() {
    return "Hello World";
}

// Call the function
let message = sayHello();
console.log(message);  // Output: Hello World
```

### Visual: Function Flow

```
Define Function
      ↓
function sayHello() {
    return "Hello World";
}
      ↓
Call Function
      ↓
let message = sayHello();
      ↓
Function Executes
      ↓
Returns "Hello World"
      ↓
Store in Variable
      ↓
message = "Hello World"
```

### Important: () Means Execute

```javascript
function sayHello() {
    return "Hello World";
}

let x = sayHello;    // x = function itself (reference)
let y = sayHello();  // y = "Hello World" (result)
```

---

## Part 4: Function Parameters

### What are Parameters?

Parameters are names listed in the function definition. They act as placeholders for values.

```javascript
function multiply(a, b) {
    return a * b;
}
```

Here, `a` and `b` are parameters.

### Single Parameter

```javascript
function greet(name) {
    return "Hello " + name;
}

let message = greet("John");
console.log(message);  // Output: Hello John
```

### Multiple Parameters

```javascript
function fullName(firstName, lastName) {
    return firstName + " " + lastName;
}

let name = fullName("John", "Doe");
console.log(name);  // Output: John Doe
```

### Parameters vs Arguments

| Term | Definition | Example |
|------|------------|---------|
| Parameters | Names in function definition | `function add(a, b)` |
| Arguments | Actual values passed | `add(5, 3)` |

```javascript
function multiply(a, b) {  // a, b are parameters
    return a * b;
}

let result = multiply(4, 5);  // 4, 5 are arguments
```

---

## Part 5: Return Statement

### What is Return?

The `return` statement sends a value back from the function.

```javascript
function add(a, b) {
    return a + b;
}

let sum = add(5, 3);
console.log(sum);  // Output: 8
```

### Return Stops Execution

Code after `return` doesn't run:

```javascript
function test() {
    return "Done";
    console.log("This never runs");  // Never executes!
}
```

### Function Without Return

If no return statement, function returns `undefined`:

```javascript
function noReturn() {
    let x = 5 + 5;
}

let result = noReturn();
console.log(result);  // Output: undefined
```

### Early Return

Use return to exit function early:

```javascript
function checkAge(age) {
    if (age < 18) {
        return "Too young";
    }
    return "Access granted";
}

console.log(checkAge(15));  // Output: Too young
console.log(checkAge(25));  // Output: Access granted
```

---

## Part 6: Function Examples

### Example 1: Temperature Converter

```javascript
function toCelsius(fahrenheit) {
    return (5/9) * (fahrenheit - 32);
}

let temp = toCelsius(77);
console.log(temp);  // Output: 25
```

### Example 2: Calculate Area

```javascript
function calculateArea(width, height) {
    return width * height;
}

let area = calculateArea(5, 10);
console.log(area);  // Output: 50
```

### Example 3: Check Even or Odd

```javascript
function isEven(number) {
    if (number % 2 === 0) {
        return true;
    }
    return false;
}

console.log(isEven(4));  // Output: true
console.log(isEven(7));  // Output: false
```

---

## Part 7: Default Parameters

### What are Default Parameters?

Default values used when no argument is provided.

```javascript
function greet(name = "Guest") {
    return "Hello " + name;
}

console.log(greet("John"));  // Output: Hello John
console.log(greet());        // Output: Hello Guest
```

### Multiple Default Parameters

```javascript
function multiply(a, b = 1) {
    return a * b;
}

console.log(multiply(5, 2));  // Output: 10
console.log(multiply(5));     // Output: 5 (uses default b=1)
```

---

## Part 8: Local Variables

### What are Local Variables?

Variables declared inside a function are LOCAL - they only exist inside that function.

```javascript
function myFunction() {
    let carName = "Volvo";  // Local variable
    console.log(carName);   // Works here
}

myFunction();
console.log(carName);  // Error! carName doesn't exist here
```

### Visual: Variable Scope

```
┌─────────────────────────────────────┐
│  Global Scope                       │
│                                     │
│  ┌───────────────────────────────┐ │
│  │  Function Scope               │ │
│  │                               │ │
│  │  let x = 10;  // Local        │ │
│  │  Only accessible here         │ │
│  │                               │ │
│  └───────────────────────────────┘ │
│                                     │
│  Cannot access x here               │
└─────────────────────────────────────┘
```

---

## Part 9: Function Expressions

### What is a Function Expression?

A function stored in a variable.

### Regular Function

```javascript
function add(a, b) {
    return a + b;
}
```

### Function Expression

```javascript
const add = function(a, b) {
    return a + b;
};
```

### Using Function Expressions

```javascript
const multiply = function(a, b) {
    return a * b;
};

let result = multiply(4, 5);
console.log(result);  // Output: 20
```

### Anonymous Functions

Function expressions often don't have names:

```javascript
const greet = function(name) {
    return "Hello " + name;
};
```

---

## Part 10: Arrow Functions

### What are Arrow Functions?

A shorter way to write function expressions using `=>`.

### Regular Function Expression

```javascript
const add = function(a, b) {
    return a + b;
};
```

### Arrow Function

```javascript
const add = (a, b) => {
    return a + b;
};
```

### Even Shorter (One Statement)

```javascript
const add = (a, b) => a + b;
```

### Arrow Function Syntax Variations

```javascript
// Multiple parameters
const multiply = (a, b) => a * b;

// Single parameter (parentheses optional)
const square = x => x * x;

// No parameters (parentheses required)
const sayHello = () => "Hello World";

// Multiple statements (need curly braces and return)
const calculate = (a, b) => {
    let sum = a + b;
    return sum * 2;
};
```

---

## Part 11: Function Types Comparison

### Comparison Table

| Feature | Function Declaration | Function Expression | Arrow Function |
|---------|---------------------|---------------------|----------------|
| Syntax | `function name() {}` | `const name = function() {}` | `const name = () => {}` |
| Hoisting | ✅ Yes | ❌ No | ❌ No |
| Can be anonymous | ❌ No | ✅ Yes | ✅ Yes |
| Shorter syntax | ❌ No | ❌ No | ✅ Yes |

### Function Declaration

```javascript
function greet(name) {
    return "Hello " + name;
}
```

**Can be called before definition (hoisted)**

### Function Expression

```javascript
const greet = function(name) {
    return "Hello " + name;
};
```

**Cannot be called before definition**

### Arrow Function

```javascript
const greet = name => "Hello " + name;
```

**Shortest syntax, cannot be called before definition**

---

## Part 12: Hoisting

### What is Hoisting?

JavaScript moves function declarations to the top of the code before execution.

### Function Declaration (Hoisted)

```javascript
// This works! ✅
let result = add(5, 3);

function add(a, b) {
    return a + b;
}
```

### Function Expression (Not Hoisted)

```javascript
// This fails! ❌
let result = add(5, 3);  // Error!

const add = function(a, b) {
    return a + b;
};
```

### Visual: Hoisting

```
Your Code:
─────────────────
greet("John");

function greet(name) {
    return "Hello " + name;
}

JavaScript Sees:
─────────────────
function greet(name) {  ← Moved to top
    return "Hello " + name;
}

greet("John");
```

---

## Part 13: Reusing Functions

### Call Function Multiple Times

```javascript
function add(a, b) {
    return a + b;
}

let sum1 = add(5, 5);
let sum2 = add(10, 20);
let sum3 = add(100, 200);

console.log(sum1);  // Output: 10
console.log(sum2);  // Output: 30
console.log(sum3);  // Output: 300
```

### Functions Calling Functions

```javascript
function add(a, b) {
    return a + b;
}

function calculate() {
    let x = add(5, 3);
    let y = add(10, 20);
    return x + y;
}

let result = calculate();
console.log(result);  // Output: 38
```

---

## Part 14: Practical Examples

### Example 1: Calculate Discount

```javascript
function calculateDiscount(price, discount) {
    let discountAmount = price * (discount / 100);
    return price - discountAmount;
}

let finalPrice = calculateDiscount(100, 20);
console.log(finalPrice);  // Output: 80
```

### Example 2: Validate Email

```javascript
function isValidEmail(email) {
    if (email.includes("@") && email.includes(".")) {
        return true;
    }
    return false;
}

console.log(isValidEmail("user@example.com"));  // Output: true
console.log(isValidEmail("invalid"));           // Output: false
```

### Example 3: Find Maximum

```javascript
function findMax(a, b, c) {
    if (a >= b && a >= c) {
        return a;
    } else if (b >= a && b >= c) {
        return b;
    } else {
        return c;
    }
}

console.log(findMax(10, 25, 15));  // Output: 25
```

---

## Part 15: Common Mistakes

### Mistake 1: Forgetting Parentheses

```javascript
function sayHello() {
    return "Hello";
}

// Wrong ❌
let x = sayHello;  // x = function itself

// Correct ✅
let y = sayHello();  // y = "Hello"
```

### Mistake 2: Forgetting Return

```javascript
// Wrong ❌
function add(a, b) {
    a + b;  // No return!
}

let result = add(5, 3);
console.log(result);  // Output: undefined

// Correct ✅
function add(a, b) {
    return a + b;
}
```

### Mistake 3: Code After Return

```javascript
// Wrong ❌
function test() {
    return "Done";
    console.log("This never runs");  // Unreachable!
}
```

### Mistake 4: Wrong Parameter Order

```javascript
function divide(a, b) {
    return a / b;
}

console.log(divide(10, 2));  // Output: 5
console.log(divide(2, 10));  // Output: 0.2 (different!)
```

---

## Part 16: When to Use Which Function Type

### Use Function Declaration When:

✅ You need hoisting (call before definition)
✅ Creating general-purpose functions
✅ Function is used throughout the code

```javascript
function calculateTotal(price, tax) {
    return price + (price * tax);
}
```

### Use Function Expression When:

✅ Assigning functions to variables
✅ Passing functions as arguments
✅ Creating conditional functions

```javascript
const calculate = function(a, b) {
    return a + b;
};
```

### Use Arrow Function When:

✅ Writing short, simple functions
✅ Working with arrays (map, filter, etc.)
✅ Need concise syntax

```javascript
const double = x => x * 2;
```

---

## Part 17: Key Takeaways

### ✅ Remember These Points

1. **Functions** are reusable blocks of code
2. **Parameters** are names in definition, **arguments** are actual values
3. **return** sends value back and stops execution
4. **()** after function name executes it
5. **Function declarations** are hoisted
6. **Function expressions** are not hoisted
7. **Arrow functions** provide shorter syntax
8. **Local variables** only exist inside functions
9. **Default parameters** provide fallback values
10. Functions make code organized and reusable

### Function Syntax Summary

```javascript
// Function Declaration
function name(param1, param2) {
    return result;
}

// Function Expression
const name = function(param1, param2) {
    return result;
};

// Arrow Function
const name = (param1, param2) => result;

// Arrow Function (multiple statements)
const name = (param1, param2) => {
    // code
    return result;
};
```

---

## What's Next?

In the next lesson, we'll learn about:

### Coming Up: JavaScript Day 14

- Arrays introduction
- Creating and accessing arrays
- Array methods (push, pop, shift, unshift)
- Looping through arrays
- Array manipulation techniques

---

*Congratulations! You've completed JavaScript Day 13. You now understand functions in JavaScript!*

---

**Practice creating functions and see you in the next class!** 🚀
