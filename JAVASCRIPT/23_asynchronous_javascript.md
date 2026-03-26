# JavaScript Day 23: Asynchronous JavaScript

## Introduction

Asynchronous JavaScript allows your code to do multiple things at once without freezing the page. It's essential for tasks like fetching data from servers, waiting for timers, or handling user events.

**Think of async code like ordering food at a restaurant: you place your order and do other things while the chef prepares it, then you're notified when it's ready.**

---

## Part 1: What is Asynchronous Programming?

### Synchronous vs Asynchronous

| Type | Description | Example |
|------|-------------|---------|
| Synchronous | Code runs line by line, one at a time | Normal JavaScript |
| Asynchronous | Code can run while waiting for other tasks | fetch(), setTimeout() |

### Synchronous Code (Normal Flow)

```javascript
console.log("A");
console.log("B");
console.log("C");
```

**Output:**
```
A
B
C
```

Code runs in order, top to bottom.

### Asynchronous Code

```javascript
console.log("A");

setTimeout(function() {
    console.log("B");
}, 1000);

console.log("C");
```

**Output:**
```
A
C
B
```

"B" appears last because setTimeout is asynchronous!

---

## Part 2: Why Async Code?

### The Problem: Blocking Code

Some tasks take time:
- Fetching data from a server
- Reading files
- Waiting for user input
- Timers

If JavaScript waited for these tasks, the page would freeze.

### The Solution: Async Code

Async code lets the program continue while waiting for slow tasks.

### Visual: Async Flow

```
Synchronous (Blocking):
Task 1 → Wait → Task 2 → Wait → Task 3
(Page frozen while waiting)

Asynchronous (Non-blocking):
Task 1 → Task 2 → Task 3
  ↓        ↓        ↓
Wait    Wait    Wait
  ↓        ↓        ↓
Done    Done    Done
(Page stays responsive)
```

---

## Part 3: The Timing Problem

### Common Beginner Confusion

```javascript
let result;

setTimeout(function() {
    result = 5;
}, 1000);

console.log(result);  // Output: undefined
```

**Why?** The `console.log` runs before the timeout finishes!

### Visual: Timing Issue

```
Line 1: result = undefined
Line 3: setTimeout starts (waits 1 second)
Line 7: console.log(result) → undefined
        ↓
After 1 second: result = 5 (too late!)
```

---

## Part 4: Callbacks - The First Solution

### What is a Callback?

A callback is a function passed as an argument to another function. It runs later when a task finishes.

### Basic Callback Example

```javascript
function done(value) {
    console.log("Result:", value);
}

setTimeout(function() {
    done(5);
}, 1000);
```

**Output (after 1 second):**
```
Result: 5
```

### Callback with Parameters

```javascript
function myDisplayer(value) {
    console.log(value);
}

function myCalculator(num1, num2, callback) {
    let sum = num1 + num2;
    callback(sum);
}

myCalculator(5, 5, myDisplayer);
```

**Output:**
```
10
```

---

## Part 5: Callback Patterns

### Event Handling with Callbacks

```javascript
document.getElementById("myButton").addEventListener("click", function() {
    console.log("Button clicked!");
});
```

### setTimeout with Callback

```javascript
setTimeout(function() {
    console.log("I love You!");
}, 3000);
```

### Error-First Callback Pattern

```javascript
function getData(callback) {
    let ok = true;
    
    if (ok) {
        callback(null, "Data loaded");
    } else {
        callback("Something failed", null);
    }
}

getData(function(error, data) {
    if (error) {
        console.log("Error:", error);
        return;
    }
    console.log("Success:", data);
});
```

**Output:**
```
Success: Data loaded
```

---

## Part 6: Callback Hell

### The Problem with Deep Callbacks

```javascript
step1(function(r1) {
    step2(r1, function(r2) {
        step3(r2, function(r3) {
            step4(r3, function(r4) {
                console.log(r4);
            });
        });
    });
});
```

This is called "callback hell" or "pyramid of doom".

### Visual: Callback Hell

```
step1(function(r1) {
    step2(r1, function(r2) {
        step3(r2, function(r3) {
            ← Code moves right
            ← Hard to read
            ← Hard to debug
        });
    });
});
```

---

## Part 7: Promises - A Better Solution

### What is a Promise?

A Promise represents a value that will be available in the future. It can be in one of three states:

| State | Description |
|-------|-------------|
| Pending | Operation started, not finished |
| Fulfilled | Operation completed successfully |
| Rejected | Operation failed |

### Creating a Promise

```javascript
let myPromise = new Promise(function(resolve, reject) {
    let ok = true;
    
    if (ok) {
        resolve("Success!");
    } else {
        reject("Error!");
    }
});
```

### Using a Promise

```javascript
myPromise
    .then(function(value) {
        console.log(value);  // Success case
    })
    .catch(function(error) {
        console.log(error);  // Error case
    });
```

**Output:**
```
Success!
```

---

## Part 8: Promise States

### Visual: Promise States

```
Promise Created
    ↓
┌─────────────┐
│   Pending   │ ← Operation in progress
└──────┬──────┘
       ↓
   ┌───┴───┐
   ↓       ↓
Fulfilled  Rejected
(Success)  (Error)
```

### Promise State Example

```javascript
let myPromise = new Promise(function(resolve, reject) {
    setTimeout(function() {
        resolve("Done!");
    }, 2000);
});

console.log("Promise state: pending");

myPromise.then(function(value) {
    console.log("Promise state: fulfilled");
    console.log(value);
});
```

**Output:**
```
Promise state: pending
(after 2 seconds)
Promise state: fulfilled
Done!
```

---

## Part 9: Promise Chaining

### Chaining Promises

```javascript
function step1() {
    return Promise.resolve("A");
}

function step2(value) {
    return Promise.resolve(value + "B");
}

function step3(value) {
    return Promise.resolve(value + "C");
}

step1()
    .then(function(value) {
        return step2(value);
    })
    .then(function(value) {
        return step3(value);
    })
    .then(function(value) {
        console.log(value);
    });
```

**Output:**
```
ABC
```

### Visual: Promise Chain

```
step1() → "A"
    ↓
.then() → step2("A") → "AB"
    ↓
.then() → step3("AB") → "ABC"
    ↓
.then() → console.log("ABC")
```

---

## Part 10: Error Handling with Promises

### Single catch() for All Errors

```javascript
step1()
    .then(function(value) {
        return step2(value);
    })
    .then(function(value) {
        return step3(value);
    })
    .catch(function(error) {
        console.log("Error:", error);
    });
```

One `catch()` handles errors from any step above it.

### Example with Error

```javascript
function step1() {
    return Promise.resolve("A");
}

function step2(value) {
    return Promise.reject("Failed at step 2");
}

function step3(value) {
    return Promise.resolve(value + "C");
}

step1()
    .then(step2)
    .then(step3)
    .catch(function(error) {
        console.log(error);
    });
```

**Output:**
```
Failed at step 2
```

---

## Part 11: async/await - The Modern Way

### What is async/await?

`async` and `await` make promises easier to read and write. They let you write async code that looks like normal synchronous code.

### The async Keyword

```javascript
async function myFunction() {
    return "Hello";
}

// Same as:
function myFunction() {
    return Promise.resolve("Hello");
}
```

An `async` function always returns a promise.

### The await Keyword

```javascript
async function myFunction() {
    let promise = Promise.resolve("Hello");
    let result = await promise;
    console.log(result);
}

myFunction();
```

**Output:**
```
Hello
```

`await` pauses the function until the promise resolves.

---

## Part 12: async/await Examples

### Example 1: Simple async/await

```javascript
function step1() {
    return Promise.resolve("A");
}

async function run() {
    let value = await step1();
    console.log(value);
}

run();
```

**Output:**
```
A
```

### Example 2: Multiple Steps

```javascript
function step1() {
    return Promise.resolve("A");
}

function step2(value) {
    return Promise.resolve(value + "B");
}

function step3(value) {
    return Promise.resolve(value + "C");
}

async function run() {
    let v1 = await step1();
    let v2 = await step2(v1);
    let v3 = await step3(v2);
    console.log(v3);
}

run();
```

**Output:**
```
ABC
```

Much cleaner than promise chains!

---

## Part 13: Error Handling with try...catch

### Using try...catch

```javascript
function fail() {
    return Promise.reject("Failed!");
}

async function run() {
    try {
        let value = await fail();
        console.log(value);
    } catch (error) {
        console.log("Error:", error);
    }
}

run();
```

**Output:**
```
Error: Failed!
```

### Example with Multiple Steps

```javascript
async function loadData() {
    try {
        let step1Result = await step1();
        let step2Result = await step2(step1Result);
        let step3Result = await step3(step2Result);
        console.log(step3Result);
    } catch (error) {
        console.log("Something went wrong:", error);
    }
}
```

---

## Part 14: Sequential vs Parallel

### Sequential (One After Another)

```javascript
async function run() {
    let a = await step1();  // Wait for step1
    let b = await step2();  // Then wait for step2
    console.log(a, b);
}
```

Total time: step1 time + step2 time

### Parallel (At the Same Time)

```javascript
async function run() {
    let p1 = step1();  // Start step1
    let p2 = step2();  // Start step2 (don't wait)
    
    let values = await Promise.all([p1, p2]);  // Wait for both
    console.log(values);
}
```

Total time: max(step1 time, step2 time)

### Visual: Sequential vs Parallel

```
Sequential:
step1 → wait → step2 → wait → done
(2 seconds + 2 seconds = 4 seconds)

Parallel:
step1 → wait ↘
              → done
step2 → wait ↗
(max(2 seconds, 2 seconds) = 2 seconds)
```

---

## Part 15: The fetch() API

### What is fetch()?

`fetch()` is the modern way to request data from a server. It returns a promise.

### Basic fetch() Example

```javascript
fetch("data.json")
    .then(function(response) {
        return response.json();
    })
    .then(function(data) {
        console.log(data);
    })
    .catch(function(error) {
        console.log("Error:", error);
    });
```

### fetch() with async/await (Recommended)

```javascript
async function loadData() {
    try {
        let response = await fetch("data.json");
        let data = await response.json();
        console.log(data);
    } catch (error) {
        console.log("Error:", error);
    }
}

loadData();
```

---

## Part 16: Understanding fetch() Response

### fetch() Returns a Response Object

```javascript
async function loadData() {
    let response = await fetch("data.json");
    console.log(response);  // Response object, not data!
}
```

### Getting JSON Data

```javascript
async function loadData() {
    let response = await fetch("data.json");
    let data = await response.json();  // Parse JSON
    console.log(data);  // Now you have the data
}
```

### Visual: fetch() Flow

```
fetch("data.json")
    ↓
Response object
    ↓
response.json()
    ↓
Actual data
```

---

## Part 17: Handling HTTP Errors

### Important: fetch() Doesn't Reject on 404

```javascript
async function loadData() {
    let response = await fetch("missing.json");
    
    if (!response.ok) {
        console.log("HTTP Error:", response.status);
        return;
    }
    
    let data = await response.json();
    console.log(data);
}
```

### Checking Response Status

```javascript
async function loadData() {
    try {
        let response = await fetch("data.json");
        
        if (!response.ok) {
            throw new Error("HTTP Error: " + response.status);
        }
        
        let data = await response.json();
        console.log(data);
    } catch (error) {
        console.log(error);
    }
}
```

---

## Part 18: Network Errors vs HTTP Errors

### Two Types of Errors

| Error Type | When It Happens | Example |
|------------|-----------------|---------|
| Network Error | Can't reach server | Offline, DNS error |
| HTTP Error | Server responds with error | 404, 500 |

### Handling Both Types

```javascript
async function loadData() {
    try {
        let response = await fetch("data.json");
        
        // Check HTTP errors
        if (!response.ok) {
            console.log("HTTP Error:", response.status);
            return;
        }
        
        let data = await response.json();
        console.log(data);
    } catch (error) {
        // Network errors
        console.log("Network Error:", error);
    }
}
```

---

## Part 19: Common Mistakes

### Mistake 1: Forgetting await

```javascript
// Wrong ❌
async function loadData() {
    let response = await fetch("data.json");
    let data = response.json();  // Missing await!
    console.log(data);  // Logs a Promise, not data
}

// Correct ✅
async function loadData() {
    let response = await fetch("data.json");
    let data = await response.json();
    console.log(data);
}
```

### Mistake 2: Not Checking response.ok

```javascript
// Wrong ❌
async function loadData() {
    let response = await fetch("missing.json");
    let data = await response.json();  // Will fail!
    console.log(data);
}

// Correct ✅
async function loadData() {
    let response = await fetch("missing.json");
    if (!response.ok) {
        console.log("Error:", response.status);
        return;
    }
    let data = await response.json();
    console.log(data);
}
```

### Mistake 3: Using await Outside async Function

```javascript
// Wrong ❌
function loadData() {
    let response = await fetch("data.json");  // Error!
}

// Correct ✅
async function loadData() {
    let response = await fetch("data.json");
}
```

### Mistake 4: Not Handling Errors

```javascript
// Wrong ❌
async function loadData() {
    let response = await fetch("data.json");
    let data = await response.json();
    console.log(data);
}

// Correct ✅
async function loadData() {
    try {
        let response = await fetch("data.json");
        let data = await response.json();
        console.log(data);
    } catch (error) {
        console.log("Error:", error);
    }
}
```

---

## Part 20: Promise Static Methods

### Promise.all()

Wait for all promises to complete:

```javascript
let p1 = Promise.resolve(1);
let p2 = Promise.resolve(2);
let p3 = Promise.resolve(3);

Promise.all([p1, p2, p3]).then(function(values) {
    console.log(values);  // [1, 2, 3]
});
```

### Promise.race()

Return the first promise that completes:

```javascript
let p1 = new Promise(resolve => setTimeout(() => resolve(1), 1000));
let p2 = new Promise(resolve => setTimeout(() => resolve(2), 500));

Promise.race([p1, p2]).then(function(value) {
    console.log(value);  // 2 (finishes first)
});
```

### Promise.allSettled()

Wait for all promises, regardless of success/failure:

```javascript
let p1 = Promise.resolve(1);
let p2 = Promise.reject("Error");
let p3 = Promise.resolve(3);

Promise.allSettled([p1, p2, p3]).then(function(results) {
    console.log(results);
});
```

**Output:**
```
[
  {status: "fulfilled", value: 1},
  {status: "rejected", reason: "Error"},
  {status: "fulfilled", value: 3}
]
```

---

## Part 21: Practical Examples

### Example 1: Loading User Data

```javascript
async function loadUser(userId) {
    try {
        let response = await fetch(`https://api.example.com/users/${userId}`);
        
        if (!response.ok) {
            throw new Error("User not found");
        }
        
        let user = await response.json();
        console.log(user);
    } catch (error) {
        console.log("Error:", error);
    }
}

loadUser(123);
```

### Example 2: Multiple API Calls

```javascript
async function loadAllData() {
    try {
        let [users, posts, comments] = await Promise.all([
            fetch("api/users").then(r => r.json()),
            fetch("api/posts").then(r => r.json()),
            fetch("api/comments").then(r => r.json())
        ]);
        
        console.log(users, posts, comments);
    } catch (error) {
        console.log("Error:", error);
    }
}
```

### Example 3: Retry Logic

```javascript
async function fetchWithRetry(url, retries = 3) {
    for (let i = 0; i < retries; i++) {
        try {
            let response = await fetch(url);
            if (response.ok) {
                return await response.json();
            }
        } catch (error) {
            if (i === retries - 1) throw error;
            console.log(`Retry ${i + 1}...`);
        }
    }
}
```

---

## Part 22: Debugging Async Code

### Debugging Checklist

1. Check the console for errors
2. Add `try...catch` around async code
3. Check `response.ok` and `response.status`
4. Use the Network tab in DevTools
5. Use breakpoints on `await` lines
6. Log responses before parsing

### Debugging Example

```javascript
async function loadData() {
    try {
        console.log("1. Starting fetch...");
        let response = await fetch("data.json");
        
        console.log("2. Response received:", response.status);
        console.log("3. Content-Type:", response.headers.get("content-type"));
        
        if (!response.ok) {
            console.log("4. HTTP Error:", response.status);
            return;
        }
        
        console.log("5. Parsing JSON...");
        let data = await response.json();
        
        console.log("6. Data loaded:", data);
    } catch (error) {
        console.log("7. Error caught:", error);
    }
}
```

---

## Part 23: Key Takeaways

### ✅ Remember These Points

1. **Async code** doesn't block the page
2. **Callbacks** were the first solution (can cause callback hell)
3. **Promises** represent future values (pending, fulfilled, rejected)
4. **async/await** makes promises easier to read
5. **fetch()** returns a promise for HTTP requests
6. **await** only works inside `async` functions
7. **try...catch** handles errors in async/await
8. **response.ok** must be checked (fetch doesn't reject on 404)
9. **Promise.all()** runs promises in parallel
10. Always handle errors in async code

### Async Quick Reference

```javascript
// Callback
setTimeout(function() {
    console.log("Done");
}, 1000);

// Promise
let promise = new Promise((resolve, reject) => {
    resolve("Done");
});
promise.then(value => console.log(value));

// async/await
async function run() {
    try {
        let result = await someAsyncFunction();
        console.log(result);
    } catch (error) {
        console.log(error);
    }
}

// fetch
async function loadData() {
    try {
        let response = await fetch("data.json");
        if (!response.ok) throw new Error("HTTP Error");
        let data = await response.json();
        console.log(data);
    } catch (error) {
        console.log(error);
    }
}
```

---

## What's Next?

In the next lesson, we'll learn about:

### Coming Up: JavaScript Day 24

- ES6+ features (let, const, arrow functions)
- Template literals
- Spread and rest operators
- Default parameters
- Modern JavaScript best practices

---

*Congratulations! You've completed JavaScript Day 23. You now understand asynchronous JavaScript!*

---

**Practice with async code and see you in the next class!** 🚀
