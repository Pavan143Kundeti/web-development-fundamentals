# JavaScript Day 22: Iterators and Generators

## Introduction

Iterators and Generators are powerful features that allow you to create custom ways to loop through data. They give you control over how data is accessed one piece at a time.

**Think of an iterator as a bookmark that remembers where you are in a book, and a generator as a function that can pause and resume.**

---

## Part 1: What is an Iterable?

### Iterable Definition

An iterable is an object that can be looped over using `for...of`. Common iterables include strings, arrays, Sets, and Maps.

### Built-in Iterables

| Type | Example |
|------|---------|
| String | `"Hello"` |
| Array | `[1, 2, 3]` |
| Set | `new Set([1, 2, 3])` |
| Map | `new Map([["a", 1]])` |
| TypedArray | `new Uint8Array([1, 2])` |

### The for...of Loop

The `for...of` loop works with any iterable:

```javascript
// Iterating over a string
const name = "W3Schools";
for (const char of name) {
    console.log(char);
}
```

**Output:**
```
W
3
S
c
h
o
o
l
s
```

---

## Part 2: Iterating Over Different Types

### Iterating Over a String

```javascript
const name = "Hello";

for (const char of name) {
    console.log(char);
}
```

**Output:**
```
H
e
l
l
o
```

### Iterating Over an Array

```javascript
const numbers = [2, 4, 6, 8];

for (const num of numbers) {
    console.log(num);
}
```

**Output:**
```
2
4
6
8
```

### Iterating Over a Set

```javascript
const letters = new Set(["a", "b", "c"]);

for (const letter of letters) {
    console.log(letter);
}
```

**Output:**
```
a
b
c
```

### Iterating Over a Map

```javascript
const fruits = new Map([
    ["apples", 500],
    ["bananas", 300],
    ["oranges", 200]
]);

for (const [key, value] of fruits) {
    console.log(key + " = " + value);
}
```

**Output:**
```
apples = 500
bananas = 300
oranges = 200
```

---

## Part 3: What is an Iterator?

### Iterator Definition

An iterator is an object that provides a `next()` method. Each call to `next()` returns an object with two properties:
- `value`: The next value
- `done`: `true` if finished, `false` otherwise

### Iterator Protocol

```javascript
{
    value: someValue,  // The current value
    done: false        // true when finished
}
```

### Visual: Iterator Concept

```
Iterator:
┌─────────────────┐
│  next() method  │
└────────┬────────┘
         ↓
    Returns object:
    {value: 1, done: false}
         ↓
    {value: 2, done: false}
         ↓
    {value: 3, done: true}
```

---

## Part 4: Creating a Custom Iterator

### Home Made Iterator

```javascript
// Create a custom iterator
function myNumbers() {
    let n = 0;
    return {
        next: function() {
            n += 10;
            return {value: n, done: false};
        }
    };
}

// Use the iterator
const numbers = myNumbers();

console.log(numbers.next());  // {value: 10, done: false}
console.log(numbers.next());  // {value: 20, done: false}
console.log(numbers.next());  // {value: 30, done: false}
```

### Iterator with Done State

```javascript
function myNumbers() {
    let n = 0;
    return {
        next: function() {
            n += 10;
            if (n > 30) {
                return {value: undefined, done: true};
            }
            return {value: n, done: false};
        }
    };
}

const numbers = myNumbers();

console.log(numbers.next());  // {value: 10, done: false}
console.log(numbers.next());  // {value: 20, done: false}
console.log(numbers.next());  // {value: 30, done: false}
console.log(numbers.next());  // {value: undefined, done: true}
```

---

## Part 5: Symbol.iterator

### Making Objects Iterable

To make an object work with `for...of`, add a `Symbol.iterator` method:

```javascript
// Create an object
const myNumbers = {};

// Make it iterable
myNumbers[Symbol.iterator] = function() {
    let n = 0;
    let done = false;
    return {
        next() {
            n += 10;
            if (n === 100) {
                done = true;
            }
            return {value: n, done: done};
        }
    };
};

// Now you can use for...of
for (const num of myNumbers) {
    console.log(num);
}
```

**Output:**
```
10
20
30
40
50
60
70
80
90
```

### Manual Iteration

You can also call the iterator manually:

```javascript
const myNumbers = {};

myNumbers[Symbol.iterator] = function() {
    let n = 0;
    return {
        next() {
            n += 10;
            if (n > 30) {
                return {done: true};
            }
            return {value: n, done: false};
        }
    };
};

// Manual iteration
const iterator = myNumbers[Symbol.iterator]();

while (true) {
    const result = iterator.next();
    if (result.done) break;
    console.log(result.value);
}
```

**Output:**
```
10
20
30
```

---

## Part 6: Iterator Helper Methods (ES2025)

### New Iterator Methods

JavaScript 2025 introduced helper methods for iterators:

| Method | Description |
|--------|-------------|
| `from()` | Create iterator from iterable |
| `drop()` | Skip specified number of elements |
| `take()` | Take specified number of elements |
| `filter()` | Filter elements |
| `map()` | Transform elements |
| `find()` | Find first matching element |
| `every()` | Test if all elements match |
| `some()` | Test if any element matches |
| `reduce()` | Reduce to single value |
| `forEach()` | Execute function for each element |
| `flatMap()` | Map and flatten results |

---

## Part 7: Iterator.from()

### Create Iterator from Iterable

```javascript
// Create an iterator from array
const myIterator = Iterator.from([1, 2, 3, 4, 5]);

// Iterate over elements
let text = "";
for (const x of myIterator) {
    text += x + " ";
}

console.log(text);  // Output: 1 2 3 4 5
```

---

## Part 8: drop() and take()

### The drop() Method

Skip specified number of elements:

```javascript
// Create iterator
const myIterator = Iterator.from([1, 2, 3, 4, 5, 6]);

// Skip first 3 elements
const remaining = myIterator.drop(3);

for (const x of remaining) {
    console.log(x);
}
```

**Output:**
```
4
5
6
```

### The take() Method

Take only specified number of elements:

```javascript
// Create iterator
const myIterator = Iterator.from([1, 2, 3, 4, 5, 6]);

// Take first 3 elements
const firstThree = myIterator.take(3);

for (const x of firstThree) {
    console.log(x);
}
```

**Output:**
```
1
2
3
```

---

## Part 9: filter() and map()

### The filter() Method

Filter elements based on condition:

```javascript
// Create iterator
const myIterator = Iterator.from([32, 33, 16, 40]);

// Filter elements greater than 18
const filtered = myIterator.filter(x => x > 18);

for (const x of filtered) {
    console.log(x);
}
```

**Output:**
```
32
33
40
```

### The map() Method

Transform each element:

```javascript
// Create iterator
const myIterator = Iterator.from([1, 2, 3, 4, 5]);

// Double each value
const doubled = myIterator.map(x => x * 2);

for (const x of doubled) {
    console.log(x);
}
```

**Output:**
```
2
4
6
8
10
```

---

## Part 10: find(), every(), some()

### The find() Method

Find first element matching condition:

```javascript
// Create iterator
const myIterator = Iterator.from([3, 10, 18, 30, 20]);

// Find first greater than 18
const result = myIterator.find(x => x > 18);

console.log(result);  // Output: 30
```

### The every() Method

Test if all elements match:

```javascript
// Create iterator
const myIterator = Iterator.from([8, 9, 10]);

// Are all greater than 7?
const result = myIterator.every(x => x > 7);

console.log(result);  // Output: true
```

### The some() Method

Test if any element matches:

```javascript
// Create iterator
const myIterator = Iterator.from([1, 2, 3, 8, 9]);

// Is any greater than 7?
const result = myIterator.some(x => x > 7);

console.log(result);  // Output: true
```

---

## Part 11: reduce() and forEach()

### The reduce() Method

Reduce to single value:

```javascript
// Create iterator
const myIterator = Iterator.from([175, 50, 25]);

// Sum all values
const result = myIterator.reduce((acc, val) => acc + val, 0);

console.log(result);  // Output: 250
```

### The forEach() Method

Execute function for each element:

```javascript
// Create iterator
const myIterator = Iterator.from([1, 2, 3, 4, 5]);

// Print each element
myIterator.forEach(x => console.log(x));
```

**Output:**
```
1
2
3
4
5
```

---

## Part 12: What are Generators?

### Generator Definition

A generator is a special function that can pause and resume execution. It's defined using `function*` syntax and uses the `yield` keyword.

### Key Features

| Feature | Description |
|---------|-------------|
| Syntax | `function*` (with asterisk) |
| Keyword | `yield` to pause and return value |
| Returns | Generator object (iterator) |
| State | Maintains state between calls |
| Control | Can pause and resume |

### Visual: Generator Flow

```
Generator Function:
function* myGen() {
    yield 1;  ← Pause here, return 1
    yield 2;  ← Resume, pause here, return 2
    yield 3;  ← Resume, pause here, return 3
}

Calling:
gen.next() → {value: 1, done: false}
gen.next() → {value: 2, done: false}
gen.next() → {value: 3, done: false}
gen.next() → {value: undefined, done: true}
```

---

## Part 13: Creating Generators

### Basic Generator

```javascript
function* myGenerator() {
    yield 1;
    yield 2;
    yield 3;
}

// Create generator object
const gen = myGenerator();

console.log(gen.next());  // {value: 1, done: false}
console.log(gen.next());  // {value: 2, done: false}
console.log(gen.next());  // {value: 3, done: false}
console.log(gen.next());  // {value: undefined, done: true}
```

### Generator with for...of

```javascript
function* myGenerator() {
    yield 1;
    yield 2;
    yield 3;
}

// Use with for...of
for (const value of myGenerator()) {
    console.log(value);
}
```

**Output:**
```
1
2
3
```

---

## Part 14: yield vs return

### Using return

```javascript
function* myStream() {
    yield 1;
    yield 2;
    return 3;  // return stops iteration
}

for (const value of myStream()) {
    console.log(value);
}
```

**Output:**
```
1
2
```

**Note:** `return` ends the generator, and the value is not included in `for...of`.

### Using yield for All Values

```javascript
function* myStream() {
    yield 1;
    yield 2;
    yield 3;  // Use yield, not return
}

for (const value of myStream()) {
    console.log(value);
}
```

**Output:**
```
1
2
3
```

---

## Part 15: Generator Examples

### Example 1: ID Generator

```javascript
function* idGenerator() {
    let id = 1;
    while (true) {
        yield id++;
    }
}

const gen = idGenerator();

console.log(gen.next().value);  // 1
console.log(gen.next().value);  // 2
console.log(gen.next().value);  // 3
```

### Example 2: Range Generator

```javascript
function* range(start, end) {
    for (let i = start; i <= end; i++) {
        yield i;
    }
}

for (const num of range(1, 5)) {
    console.log(num);
}
```

**Output:**
```
1
2
3
4
5
```

### Example 3: Fibonacci Generator

```javascript
function* fibonacci() {
    let a = 0, b = 1;
    while (true) {
        yield a;
        [a, b] = [b, a + b];
    }
}

const fib = fibonacci();

console.log(fib.next().value);  // 0
console.log(fib.next().value);  // 1
console.log(fib.next().value);  // 1
console.log(fib.next().value);  // 2
console.log(fib.next().value);  // 3
console.log(fib.next().value);  // 5
```

### Example 4: Array Chunks

```javascript
function* chunkArray(array, size) {
    for (let i = 0; i < array.length; i += size) {
        yield array.slice(i, i + size);
    }
}

const numbers = [1, 2, 3, 4, 5, 6, 7, 8];

for (const chunk of chunkArray(numbers, 3)) {
    console.log(chunk);
}
```

**Output:**
```
[1, 2, 3]
[4, 5, 6]
[7, 8]
```

---

## Part 16: Generator Methods

### Generator Object Methods

| Method | Description |
|--------|-------------|
| `next()` | Resume execution, get next value |
| `return()` | Finish execution, return value |
| `throw()` | Throw exception in generator |

### The next() Method

```javascript
function* myGen() {
    yield 1;
    yield 2;
    yield 3;
}

const gen = myGen();

console.log(gen.next());  // {value: 1, done: false}
console.log(gen.next());  // {value: 2, done: false}
console.log(gen.next());  // {value: 3, done: false}
console.log(gen.next());  // {value: undefined, done: true}
```

### The return() Method

```javascript
function* myGen() {
    yield 1;
    yield 2;
    yield 3;
}

const gen = myGen();

console.log(gen.next());    // {value: 1, done: false}
console.log(gen.return(99)); // {value: 99, done: true}
console.log(gen.next());    // {value: undefined, done: true}
```

---

## Part 17: Practical Use Cases

### Use Case 1: Lazy Evaluation

Generators compute values on demand, saving memory:

```javascript
function* infiniteNumbers() {
    let n = 0;
    while (true) {
        yield n++;
    }
}

const numbers = infiniteNumbers();

// Only generates values when needed
console.log(numbers.next().value);  // 0
console.log(numbers.next().value);  // 1
```

### Use Case 2: Data Streaming

Process large datasets without loading everything into memory:

```javascript
function* readLines(text) {
    const lines = text.split('\n');
    for (const line of lines) {
        yield line;
    }
}

const data = "Line 1\nLine 2\nLine 3";

for (const line of readLines(data)) {
    console.log(line);
}
```

### Use Case 3: State Machines

```javascript
function* trafficLight() {
    while (true) {
        yield "Red";
        yield "Yellow";
        yield "Green";
    }
}

const light = trafficLight();

console.log(light.next().value);  // Red
console.log(light.next().value);  // Yellow
console.log(light.next().value);  // Green
console.log(light.next().value);  // Red (cycles)
```

---

## Part 18: Iterators vs Generators

### Comparison Table

| Feature | Iterator | Generator |
|---------|----------|-----------|
| Syntax | Object with `next()` | `function*` |
| Creation | Manual | Automatic |
| State | Manual management | Automatic |
| Complexity | More code | Less code |
| Flexibility | Full control | Simpler |

### Iterator Example

```javascript
function createIterator() {
    let n = 0;
    return {
        next() {
            n++;
            if (n > 3) {
                return {done: true};
            }
            return {value: n, done: false};
        }
    };
}
```

### Generator Example (Simpler)

```javascript
function* createGenerator() {
    yield 1;
    yield 2;
    yield 3;
}
```

---

## Part 19: Common Mistakes

### Mistake 1: Forgetting Asterisk

```javascript
// Wrong ❌
function myGenerator() {
    yield 1;  // Error!
}

// Correct ✅
function* myGenerator() {
    yield 1;
}
```

### Mistake 2: Using return Instead of yield

```javascript
function* myGen() {
    yield 1;
    yield 2;
    return 3;  // Won't appear in for...of
}

for (const val of myGen()) {
    console.log(val);  // Only prints 1, 2
}
```

### Mistake 3: Reusing Generator

```javascript
function* myGen() {
    yield 1;
    yield 2;
}

const gen = myGen();

// First iteration
for (const val of gen) {
    console.log(val);  // 1, 2
}

// Second iteration - nothing!
for (const val of gen) {
    console.log(val);  // Nothing (generator exhausted)
}

// Need to create new generator
const gen2 = myGen();
for (const val of gen2) {
    console.log(val);  // 1, 2
}
```

---

## Part 20: Key Takeaways

### ✅ Remember These Points

1. **Iterables** can be looped with `for...of`
2. **Iterators** have a `next()` method
3. **Symbol.iterator** makes objects iterable
4. **Generators** use `function*` syntax
5. **yield** pauses and returns values
6. **Generators** maintain state between calls
7. **return** ends generator (value not in for...of)
8. **Iterator helpers** (ES2025) provide useful methods
9. **Generators** are simpler than manual iterators
10. Use generators for lazy evaluation and data streaming

### Iterator Quick Reference

```javascript
// Create custom iterator
const myIterator = {
    [Symbol.iterator]() {
        let n = 0;
        return {
            next() {
                n++;
                if (n > 3) return {done: true};
                return {value: n, done: false};
            }
        };
    }
};

// Use with for...of
for (const val of myIterator) {
    console.log(val);  // 1, 2, 3
}
```

### Generator Quick Reference

```javascript
// Create generator
function* myGenerator() {
    yield 1;
    yield 2;
    yield 3;
}

// Use with for...of
for (const val of myGenerator()) {
    console.log(val);  // 1, 2, 3
}

// Manual iteration
const gen = myGenerator();
console.log(gen.next());  // {value: 1, done: false}
console.log(gen.next());  // {value: 2, done: false}
console.log(gen.next());  // {value: 3, done: false}
console.log(gen.next());  // {value: undefined, done: true}
```

---

## What's Next?

In the next lesson, we'll learn about:

### Coming Up: JavaScript Day 23

- Promises and asynchronous JavaScript
- async/await syntax
- Handling asynchronous operations
- Error handling in async code
- Practical async examples

---

*Congratulations! You've completed JavaScript Day 22. You now understand Iterators and Generators in JavaScript!*

---

**Practice with iterators and generators and see you in the next class!** 🚀
