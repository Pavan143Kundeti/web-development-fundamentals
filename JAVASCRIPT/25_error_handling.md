# JavaScript Day 25: Error Handling

## Introduction

Errors happen in programming. Good error handling prevents your program from crashing and helps you find and fix bugs. JavaScript provides tools to catch and handle errors gracefully.

**Think of error handling like a safety net: it catches problems before they crash your entire program.**

---

## Part 1: Types of JavaScript Errors

### Common Error Types

| Error Type | Description | Example |
|------------|-------------|---------|
| ReferenceError | Using undefined variable | `x = y + 1` (y doesn't exist) |
| TypeError | Wrong type or invalid operation | `num.toUpperCase()` (number has no toUpperCase) |
| RangeError | Value out of valid range | `new Array(-1)` |
| URIError | Invalid URI characters | `decodeURI("%%%")` |
| SyntaxError | Invalid JavaScript syntax | `let x = "hello;` (missing quote) |
| EvalError | Error in eval() (deprecated) | Rarely used |

### Visual: Error Flow

```
Code runs
    ↓
Error occurs
    ↓
┌─────────────────┐
│ Error caught?   │
└────┬────────┬───┘
     │        │
    Yes      No
     ↓        ↓
Handle it  Program crashes
```

---

## Part 2: ReferenceError

### What is ReferenceError?

A ReferenceError occurs when you try to use a variable that doesn't exist.

### Example 1: Variable Doesn't Exist

```javascript
let x = 5;

try {
    x = y + 1;  // y doesn't exist!
} catch(err) {
    console.log(err.name);  // Output: ReferenceError
    console.log(err.message);  // Output: y is not defined
}
```

### Example 2: Using Before Declaration

```javascript
try {
    let x = y;  // Using y before it's declared
    let y = 5;
} catch(err) {
    console.log(err.name);  // Output: ReferenceError
    console.log(err.message);  // Output: Cannot access 'y' before initialization
}
```

---

## Part 3: TypeError

### What is TypeError?

A TypeError occurs when a value is the wrong type or an operation is invalid.

### Example 1: Not a Function

```javascript
let anna = 5;

try {
    anna(5);  // anna is a number, not a function!
} catch(err) {
    console.log(err.name);  // Output: TypeError
    console.log(err.message);  // Output: anna is not a function
}
```

### Example 2: Invalid Method

```javascript
let num = 1;

try {
    num.toUpperCase();  // Numbers don't have toUpperCase!
} catch(err) {
    console.log(err.name);  // Output: TypeError
    console.log(err.message);  // Output: num.toUpperCase is not a function
}
```

---

## Part 4: RangeError

### What is RangeError?

A RangeError occurs when a value is outside its valid range.

### Example 1: Invalid Array Length

```javascript
try {
    new Array(-1);  // Array length can't be negative!
} catch(err) {
    console.log(err.name);  // Output: RangeError
    console.log(err.message);  // Output: Invalid array length
}
```

### Example 2: Invalid Precision

```javascript
let num = 1;

try {
    num.toPrecision(500);  // Precision must be 1-100!
} catch(err) {
    console.log(err.name);  // Output: RangeError
    console.log(err.message);  // Output: toPrecision() argument must be between 1 and 100
}
```

---

## Part 5: URIError

### What is URIError?

A URIError occurs when using illegal characters in URI functions.

### Example: Invalid URI

```javascript
try {
    decodeURI("%%%");  // Invalid URI characters!
} catch(err) {
    console.log(err.name);  // Output: URIError
    console.log(err.message);  // Output: URI malformed
}
```

---

## Part 6: SyntaxError

### What is SyntaxError?

A SyntaxError occurs when code violates JavaScript's grammar rules.

### Example 1: Missing Quote

```javascript
// This causes a SyntaxError
let fname = "John;  // Missing closing quote
```

**Output:**
```
Uncaught SyntaxError: Invalid or unexpected token
```

### Example 2: Missing Parenthesis

```javascript
// This causes a SyntaxError
Math.round(4.6;  // Missing closing parenthesis
```

**Output:**
```
Uncaught SyntaxError: missing ) after argument list
```

### Important: Syntax Errors Can't Be Caught

```javascript
try {
    let x = Math.round(4.6;)  // Syntax error!
} catch(err) {
    console.log(err.name);  // This won't run!
}
```

**Why?** Syntax errors happen before the code runs. The `try...catch` never executes.

---

## Part 7: The try...catch Statement

### Basic Syntax

```javascript
try {
    // Code that might cause an error
} catch(err) {
    // Code to handle the error
}
```

### How It Works

```
1. Code in try block runs
    ↓
2. If error occurs → jump to catch block
    ↓
3. If no error → skip catch block
    ↓
4. Continue with rest of program
```

### Example: Basic try...catch

```javascript
try {
    let x = y + 1;  // y doesn't exist
    console.log(x);
} catch(err) {
    console.log("Error caught!");
    console.log("Error name:", err.name);
    console.log("Error message:", err.message);
}

console.log("Program continues...");
```

**Output:**
```
Error caught!
Error name: ReferenceError
Error message: y is not defined
Program continues...
```

---

## Part 8: The Error Object

### Error Object Properties

| Property | Description |
|----------|-------------|
| `name` | Type of error (ReferenceError, TypeError, etc.) |
| `message` | Description of the error |

### Using Error Properties

```javascript
try {
    let x = y + 1;
} catch(err) {
    console.log("Error Type:", err.name);
    console.log("Error Message:", err.message);
    console.log("Full Error:", err);
}
```

**Output:**
```
Error Type: ReferenceError
Error Message: y is not defined
Full Error: ReferenceError: y is not defined
```

---

## Part 9: The throw Statement

### Creating Custom Errors

```javascript
throw "Too big";      // Throw a string
throw 500;            // Throw a number
throw true;           // Throw a boolean
throw {msg: "Error"}; // Throw an object
```

### Example: Input Validation

```javascript
function checkAge(age) {
    if (age < 0) {
        throw "Age cannot be negative";
    }
    if (age > 150) {
        throw "Age is too high";
    }
    return "Age is valid";
}

try {
    console.log(checkAge(-5));
} catch(err) {
    console.log("Error:", err);
}
```

**Output:**
```
Error: Age cannot be negative
```

---

## Part 10: Input Validation Example

### Complete Validation

```html
<input id="demo" type="text" placeholder="Enter number 5-10">
<button onclick="myFunction()">Test Input</button>
<p id="p01"></p>

<script>
function myFunction() {
    const message = document.getElementById("p01");
    message.innerHTML = "";
    let x = document.getElementById("demo").value;
    
    try {
        if (x.trim() == "") throw "empty";
        if (isNaN(x)) throw "not a number";
        x = Number(x);
        if (x < 5) throw "too low";
        if (x > 10) throw "too high";
        message.innerHTML = "Input is valid!";
    } catch(err) {
        message.innerHTML = "Input is " + err;
    }
}
</script>
```

### Visual: Validation Flow

```
Get input
    ↓
Is empty? → throw "empty"
    ↓
Is not number? → throw "not a number"
    ↓
Is < 5? → throw "too low"
    ↓
Is > 10? → throw "too high"
    ↓
Valid input!
```

---

## Part 11: The finally Block

### Syntax

```javascript
try {
    // Code that might cause error
} catch(err) {
    // Handle error
} finally {
    // Always runs, no matter what
}
```

### When finally Runs

| Scenario | finally Runs? |
|----------|---------------|
| No error | Yes |
| Error caught | Yes |
| Error not caught | Yes (then program crashes) |

### Example: Cleanup with finally

```javascript
function processData() {
    let file = "data.txt";
    
    try {
        console.log("Opening file:", file);
        // Process file
        throw "File error";
    } catch(err) {
        console.log("Error:", err);
    } finally {
        console.log("Closing file:", file);
    }
}

processData();
```

**Output:**
```
Opening file: data.txt
Error: File error
Closing file: data.txt
```

---

## Part 12: Practical Examples

### Example 1: Safe Division

```javascript
function safeDivide(a, b) {
    try {
        if (b === 0) {
            throw "Cannot divide by zero";
        }
        return a / b;
    } catch(err) {
        console.log("Error:", err);
        return null;
    }
}

console.log(safeDivide(10, 2));  // Output: 5
console.log(safeDivide(10, 0));  // Output: Error: Cannot divide by zero, null
```

### Example 2: JSON Parsing

```javascript
function parseJSON(jsonString) {
    try {
        return JSON.parse(jsonString);
    } catch(err) {
        console.log("Invalid JSON:", err.message);
        return null;
    }
}

console.log(parseJSON('{"name":"John"}'));  // Output: {name: "John"}
console.log(parseJSON('{invalid}'));        // Output: Invalid JSON: ..., null
```

### Example 3: Array Access

```javascript
function getElement(arr, index) {
    try {
        if (!Array.isArray(arr)) {
            throw new TypeError("First argument must be an array");
        }
        if (index < 0 || index >= arr.length) {
            throw new RangeError("Index out of bounds");
        }
        return arr[index];
    } catch(err) {
        console.log(err.name + ":", err.message);
        return undefined;
    }
}

const numbers = [1, 2, 3];
console.log(getElement(numbers, 1));   // Output: 2
console.log(getElement(numbers, 10));  // Output: RangeError: Index out of bounds, undefined
console.log(getElement("not array", 0)); // Output: TypeError: First argument must be an array, undefined
```

---

## Part 13: Silent Errors

### What are Silent Errors?

Silent errors don't throw exceptions but cause unexpected behavior.

### Example 1: Assignment Instead of Comparison

```javascript
let isActive = false;

// Wrong: Assignment (=) instead of comparison (==)
if (isActive = true) {
    console.log("Active!");  // This always runs!
}
```

### Example 2: NaN (Not a Number)

```javascript
const result = parseInt("abc");
console.log(result);  // Output: NaN (no error thrown)

// Check for NaN
if (isNaN(result)) {
    console.log("Invalid number");
}
```

### Example 3: Undefined Property

```javascript
const user = {};
console.log(user.name);  // Output: undefined (no error)

// Check before using
if (user.name !== undefined) {
    console.log(user.name);
} else {
    console.log("Name not found");
}
```

### Example 4: Type Coercion

```javascript
console.log('5' + '2');  // Output: "52" (string concatenation)
console.log('5' - '2');  // Output: 3 (numeric subtraction)

// Be explicit
console.log(Number('5') + Number('2'));  // Output: 7
```

---

## Part 14: Error Handling Best Practices

### Best Practice 1: Be Specific

```javascript
// Bad ❌
try {
    // Lots of code
} catch(err) {
    console.log("Error");
}

// Good ✅
try {
    let data = JSON.parse(jsonString);
} catch(err) {
    console.log("JSON parsing failed:", err.message);
}
```

### Best Practice 2: Don't Catch Everything

```javascript
// Bad ❌
try {
    // Everything in try block
    let x = 1;
    let y = 2;
    let z = x + y;
} catch(err) {
    // Unnecessary
}

// Good ✅
let x = 1;
let y = 2;
try {
    // Only risky code
    let data = JSON.parse(jsonString);
} catch(err) {
    console.log("Error:", err.message);
}
```

### Best Practice 3: Provide Helpful Messages

```javascript
// Bad ❌
throw "Error";

// Good ✅
throw new Error("User ID must be a positive number");
```

### Best Practice 4: Use finally for Cleanup

```javascript
function loadData() {
    let loading = true;
    
    try {
        // Load data
        throw "Network error";
    } catch(err) {
        console.log("Error:", err);
    } finally {
        loading = false;  // Always cleanup
        console.log("Loading finished");
    }
}
```

---

## Part 15: Creating Custom Error Types

### Using Error Constructor

```javascript
throw new Error("Something went wrong");
throw new TypeError("Expected a number");
throw new RangeError("Value out of range");
```

### Example: Custom Error

```javascript
function validateEmail(email) {
    if (!email.includes("@")) {
        throw new Error("Invalid email: missing @");
    }
    if (!email.includes(".")) {
        throw new Error("Invalid email: missing domain");
    }
    return true;
}

try {
    validateEmail("john");
} catch(err) {
    console.log(err.message);  // Output: Invalid email: missing @
}
```

---

## Part 16: Nested try...catch

### Multiple Error Levels

```javascript
try {
    console.log("Outer try");
    
    try {
        console.log("Inner try");
        throw "Inner error";
    } catch(err) {
        console.log("Inner catch:", err);
        throw "Outer error";
    }
} catch(err) {
    console.log("Outer catch:", err);
}
```

**Output:**
```
Outer try
Inner try
Inner catch: Inner error
Outer catch: Outer error
```

---

## Part 17: Async Error Handling

### Errors in Promises

```javascript
fetch("data.json")
    .then(response => response.json())
    .catch(err => {
        console.log("Error:", err.message);
    });
```

### Errors in async/await

```javascript
async function loadData() {
    try {
        let response = await fetch("data.json");
        let data = await response.json();
        console.log(data);
    } catch(err) {
        console.log("Error:", err.message);
    }
}
```

---

## Part 18: Common Mistakes

### Mistake 1: Empty catch Block

```javascript
// Bad ❌
try {
    riskyOperation();
} catch(err) {
    // Silent failure - hard to debug!
}

// Good ✅
try {
    riskyOperation();
} catch(err) {
    console.error("Operation failed:", err);
}
```

### Mistake 2: Catching Syntax Errors

```javascript
// This won't work ❌
try {
    let x = "hello;  // Syntax error
} catch(err) {
    console.log(err);  // Never runs
}
```

### Mistake 3: Not Re-throwing

```javascript
// Bad ❌
try {
    criticalOperation();
} catch(err) {
    console.log("Error occurred");
    // Error is hidden
}

// Good ✅
try {
    criticalOperation();
} catch(err) {
    console.log("Error occurred:", err);
    throw err;  // Re-throw for caller to handle
}
```

---

## Part 19: Debugging Errors

### Using console.error()

```javascript
try {
    throw new Error("Something went wrong");
} catch(err) {
    console.error(err);  // Shows error with stack trace
}
```

### Logging Stack Trace

```javascript
try {
    throw new Error("Test error");
} catch(err) {
    console.log("Error:", err.message);
    console.log("Stack:", err.stack);
}
```

### Browser DevTools

1. Open Console (F12)
2. Check for red error messages
3. Click error to see stack trace
4. Set breakpoints in Sources tab

---

## Part 20: Key Takeaways

### ✅ Remember These Points

1. **try...catch** prevents program crashes
2. **Error types**: ReferenceError, TypeError, RangeError, URIError, SyntaxError
3. **throw** creates custom errors
4. **finally** always runs (cleanup code)
5. **Error object** has `name` and `message` properties
6. **Syntax errors** can't be caught
7. **Silent errors** don't throw exceptions
8. **Be specific** in error handling
9. **Log errors** for debugging
10. **Use finally** for cleanup

### Error Handling Quick Reference

```javascript
// Basic try...catch
try {
    // Risky code
    let x = y + 1;
} catch(err) {
    console.log("Error:", err.name);
    console.log("Message:", err.message);
}

// With finally
try {
    // Risky code
} catch(err) {
    // Handle error
} finally {
    // Always runs
}

// Throw custom error
if (age < 0) {
    throw new Error("Age cannot be negative");
}

// Input validation
try {
    if (input === "") throw "empty";
    if (isNaN(input)) throw "not a number";
} catch(err) {
    console.log("Invalid input:", err);
}

// Async error handling
async function loadData() {
    try {
        let data = await fetch("data.json");
        return await data.json();
    } catch(err) {
        console.error("Failed to load:", err);
    }
}
```

---

## What's Next?

In the next lesson, we'll learn about:

### Coming Up: JavaScript Day 26

- JSON (JavaScript Object Notation)
- Parsing and stringifying JSON
- Working with JSON data
- JSON vs JavaScript objects
- Practical JSON examples

---

*Congratulations! You've completed JavaScript Day 25. You now understand error handling in JavaScript!*

---

**Practice error handling and see you in the next class!** 🚀
