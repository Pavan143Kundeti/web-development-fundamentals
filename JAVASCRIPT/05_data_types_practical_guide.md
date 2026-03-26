# JavaScript Day 5: Data Types - Practical Guide with Examples

## Introduction

In the last class, we learned WHAT data types are and WHY we need them. Today, we'll learn HOW to actually use them in JavaScript with practical examples!

---

## Part 1: Memory Recap - Stack and Heap

### Computer Memory

```
Computer Memory:
├── Hard Disk (Secondary Memory)
│   ├── Slow
│   └── Permanent storage
│
└── RAM (Primary/Main Memory)
    ├── Fast
    └── Temporary storage
```

### RAM Partitions for JavaScript

When JavaScript code executes, RAM is divided into two parts:

```
┌─────────────────────────────┐
│           RAM               │
├──────────────┬──────────────┤
│    STACK     │     HEAP     │
│   Memory     │   Memory     │
└──────────────┴──────────────┘
```

**Important:** All variables are stored in the **STACK** memory.

---

## Part 2: Variables - Storing Data

### What is a Variable?

A **variable** is a box (piece of memory) in the stack where you can store data.

### Visual Representation

```
STACK Memory:
┌─────────┐
│   23    │ ← Variable named "a"
└─────────┘
```

### Creating a Variable

```javascript
let a = 23;
```

**Breakdown:**
- `let` = keyword to create variable
- `a` = variable name (identifier)
- `=` = assignment operator (give value to)
- `23` = value to store
- `;` = semicolon (end of statement)

### Printing a Variable

```javascript
let a = 23;
console.log(a);        // Output: 23
```

**Important:** Don't use quotes when printing variables!

```javascript
console.log("a");      // Output: a (prints letter)
console.log(a);        // Output: 23 (prints value)
```

---

## Part 3: Number Data Type

### What is Number?

In JavaScript, **Number** stores BOTH integers and decimals (unlike Java/C++ which have separate types).

### Storing Integers

```javascript
// Age
let age = 23;
console.log(age);              // Output: 23

// Number of employees
let employees = 2000;
console.log(employees);        // Output: 2000

// Population
let population = 1400000000;
console.log(population);       // Output: 1400000000
```

### Storing Decimals (Real Numbers)

```javascript
// Height
let height = 5.9;
console.log(height);           // Output: 5.9

// Weight
let weight = 68.2;
console.log(weight);           // Output: 68.2

// Price
let price = 99.99;
console.log(price);            // Output: 99.99
```

### Checking Data Type

Use the `typeof` operator:

```javascript
let age = 23;
console.log(typeof age);       // Output: number

let height = 5.9;
console.log(typeof height);    // Output: number
```

**Key Point:** Both integers and decimals are type "number"!

---

## Part 4: JavaScript is Loosely Typed

### What Does "Loosely Typed" Mean?

You DON'T have to tell JavaScript what type of data you're storing. JavaScript figures it out automatically!

### JavaScript (Loosely Typed)

```javascript
let a = 23;        // Stores integer
let a = 5.9;       // Stores decimal
let a = "Hello";   // Stores string

// Same variable can store different types!
```

### Java (Strongly Typed) - For Comparison

```java
int a = 23;        // Must specify "int"
float b = 5.9;     // Must specify "float"
String c = "Hello"; // Must specify "String"

// Cannot change types!
```

**Advantage of JavaScript:** Easier to write, more flexible!

---

## Part 5: Special Numeric Values

### 1. Infinity

```javascript
let a = 1 / 0;
console.log(a);              // Output: Infinity
console.log(typeof a);       // Output: number
```

### 2. Negative Infinity

```javascript
let a = -1 / 0;
console.log(a);              // Output: -Infinity
console.log(typeof a);       // Output: number
```

### 3. NaN (Not a Number)

```javascript
let a = "Hello" / 2;
console.log(a);              // Output: NaN
console.log(typeof a);       // Output: number
```

**Important:** Even though it says "Not a Number", its type is still "number"!

### Summary of Special Values

```javascript
// All these are type "number":
let a = 23;           // Regular number
let b = 5.9;          // Decimal number
let c = Infinity;     // Infinity
let d = -Infinity;    // Negative Infinity
let e = NaN;          // Not a Number

console.log(typeof a); // number
console.log(typeof b); // number
console.log(typeof c); // number
console.log(typeof d); // number
console.log(typeof e); // number
```

---

## Part 6: BigInt Data Type

### Why BigInt?

Numbers have a **range limit**:

```
Number Range:
Minimum: -9,007,199,254,740,991  (-2^53 - 1)
Maximum:  9,007,199,254,740,991  (2^53 - 1)
```

**Problem:** What if you need to store larger numbers?

**Solution:** Use BigInt!

### Creating BigInt

Add `n` at the end of the number:

```javascript
let bigNumber = 9007199254740991n;
console.log(bigNumber);           // Output: 9007199254740991n
console.log(typeof bigNumber);    // Output: bigint
```

### BigInt Examples

```javascript
// Regular number (within range)
let a = 100;
console.log(a);                   // Output: 100
console.log(typeof a);            // Output: number

// BigInt (can be any size)
let b = 100n;
console.log(b);                   // Output: 100n
console.log(typeof b);            // Output: bigint

// Very large BigInt
let huge = 123456789012345678901234567890n;
console.log(huge);                // Stores exact value!
```

### BigInt Rules

#### ✅ Rule 1: Only Integers

```javascript
// Correct
let a = 100n;                     // ✅ Works

// Wrong
let b = 100.5n;                   // ❌ Error! No decimals allowed
```

#### ✅ Rule 2: BigInt Arithmetic

```javascript
// BigInt + BigInt = Works!
let a = 100n;
let b = 200n;
console.log(a + b);               // Output: 300n

// BigInt + Number = Error!
let c = 100n;
let d = 200;
console.log(c + d);               // ❌ Error! Cannot mix types
```

### BigInt Summary

```
BigInt:
├── For numbers outside Number range
├── Add 'n' suffix to create
├── Only for integers (no decimals)
├── Can do math with other BigInts
└── Cannot mix with regular Numbers
```

---

## Part 7: String Data Type

### What is a String?

A **string** is a series of characters (text).

### Creating Strings

Use quotes (double or single):

```javascript
// Double quotes
let name = "Tap Academy";
console.log(name);                // Output: Tap Academy

// Single quotes
let city = 'Bangalore';
console.log(city);                // Output: Bangalore

// Backticks (template literals)
let message = `Hello World`;
console.log(message);             // Output: Hello World
```

### String Examples

```javascript
// Names
let firstName = "Rohit";
let lastName = "Sharma";

// Company
let company = "Tap Academy";

// Address
let address = "BTM Layout, Bangalore";

// Password
let password = "mySecret123";

// All are strings!
console.log(typeof firstName);    // Output: string
console.log(typeof company);      // Output: string
```

### Checking Type

```javascript
let name = "Tap Academy";
console.log(name);                // Output: Tap Academy
console.log(typeof name);         // Output: string
```

**Note:** We'll learn more about strings in a separate detailed lesson!

---

## Part 8: Boolean Data Type

### What is Boolean?

**Boolean** stores only TWO values: `true` or `false` (Yes or No)

### Boolean Examples

```javascript
// Has passport?
let hasPassport = true;
console.log(hasPassport);         // Output: true
console.log(typeof hasPassport);  // Output: boolean

// Is raining?
let isRaining = false;
console.log(isRaining);           // Output: false
console.log(typeof isRaining);    // Output: boolean
```

### Real-World Boolean Examples

```javascript
// User status
let isLoggedIn = true;
let isVerified = false;

// Conditions
let isAdult = true;
let hasLicense = false;

// Permissions
let canEdit = true;
let canDelete = false;

// All are boolean type
console.log(typeof isLoggedIn);   // Output: boolean
```

### Boolean Use Cases

```
Boolean is used for:
├── Yes/No questions
├── True/False conditions
├── On/Off states
├── Enabled/Disabled status
└── Pass/Fail results
```

---

## Part 9: Undefined Data Type

### What is Undefined?

**Undefined** means a variable has been declared but NOT assigned a value.

### Creating Undefined

```javascript
// Declare variable without value
let a;
console.log(a);                   // Output: undefined
console.log(typeof a);            // Output: undefined
```

### Undefined Examples

```javascript
// Variable declared, not assigned
let name;
console.log(name);                // Output: undefined

let age;
console.log(age);                 // Output: undefined

let city;
console.log(city);                // Output: undefined
```

### Undefined vs Assigned

```javascript
// Before assignment
let x;
console.log(x);                   // Output: undefined

// After assignment
x = 10;
console.log(x);                   // Output: 10
```

### Key Point

```
Undefined:
├── Variable exists
├── But no value assigned
├── Automatic default value
└── Both value AND type are "undefined"
```

---

## Part 10: Null and Symbol (Brief Introduction)

### Null

**Null** means intentionally empty (we'll learn in detail later with objects).

```javascript
let user = null;
console.log(user);                // Output: null
```

### Symbol

**Symbol** creates unique identifiers (we'll learn in detail later).

```javascript
let id = Symbol("id");
console.log(typeof id);           // Output: symbol
```

**Note:** These will be covered in depth when we learn Object-Oriented Programming!

---

## Part 11: Complete Data Types Summary

### JavaScript's 7 Primitive Data Types

```javascript
// 1. Number
let age = 23;
let price = 99.99;

// 2. BigInt
let huge = 123456789012345678901234567890n;

// 3. String
let name = "Rohit";

// 4. Boolean
let isActive = true;

// 5. Undefined
let x;

// 6. Null
let user = null;

// 7. Symbol
let id = Symbol("id");
```

### Type Checking

```javascript
console.log(typeof 23);           // number
console.log(typeof 100n);         // bigint
console.log(typeof "Hello");      // string
console.log(typeof true);         // boolean
console.log(typeof undefined);    // undefined
console.log(typeof null);         // object (JavaScript bug!)
console.log(typeof Symbol("x"));  // symbol
```

---

## Part 12: Practical Examples

### Example 1: Student Information

```javascript
// Create file: student.js

let studentName = "Rajkumar";
let age = 23;
let height = 5.9;
let cgpa = 8.6;
let isPlaced = true;
let company;  // undefined (not placed yet)

console.log("Name:", studentName);
console.log("Age:", age);
console.log("Height:", height);
console.log("CGPA:", cgpa);
console.log("Placed:", isPlaced);
console.log("Company:", company);
```

**Execute:**
```bash
node student.js
```

**Output:**
```
Name: Rajkumar
Age: 23
Height: 5.9
CGPA: 8.6
Placed: true
Company: undefined
```

### Example 2: E-commerce Product

```javascript
// Create file: product.js

let productName = "Laptop";
let price = 45999.99;
let inStock = true;
let quantity = 50;
let discount = null;  // No discount currently
let rating = 4.5;

console.log("Product:", productName);
console.log("Price:", price);
console.log("In Stock:", inStock);
console.log("Quantity:", quantity);
console.log("Discount:", discount);
console.log("Rating:", rating);
```

### Example 3: Type Checking

```javascript
// Create file: types.js

let num = 42;
let text = "Hello";
let flag = true;
let nothing;
let empty = null;
let big = 100n;

console.log("num type:", typeof num);
console.log("text type:", typeof text);
console.log("flag type:", typeof flag);
console.log("nothing type:", typeof nothing);
console.log("empty type:", typeof empty);
console.log("big type:", typeof big);
```

**Output:**
```
num type: number
text type: string
flag type: boolean
nothing type: undefined
empty type: object
big type: bigint
```

---

## Part 13: Common Mistakes to Avoid

### Mistake 1: Quotes with Variables

```javascript
let name = "John";

// Wrong
console.log("name");              // Output: name (prints text)

// Correct
console.log(name);                // Output: John (prints value)
```

### Mistake 2: BigInt with Decimals

```javascript
// Wrong
let a = 100.5n;                   // ❌ Error!

// Correct
let b = 100n;                     // ✅ Works
```

### Mistake 3: Mixing BigInt and Number

```javascript
// Wrong
let a = 100n + 200;               // ❌ Error!

// Correct
let b = 100n + 200n;              // ✅ Works
```

### Mistake 4: Forgetting Semicolons

```javascript
// Not recommended
let a = 10
let b = 20

// Recommended
let a = 10;
let b = 20;
```

---

## Part 14: Practice Exercises

### Exercise 1: Create Variables

Create variables for a person:
```javascript
let name = "Your Name";
let age = 25;
let height = 5.8;
let weight = 68.5;
let isStudent = true;
let university;
let scholarship = null;

// Print all variables
console.log(name);
console.log(age);
console.log(height);
console.log(weight);
console.log(isStudent);
console.log(university);
console.log(scholarship);
```

### Exercise 2: Check Types

```javascript
let a = 100;
let b = "Hello";
let c = true;
let d;
let e = null;
let f = 999n;

console.log(typeof a);
console.log(typeof b);
console.log(typeof c);
console.log(typeof d);
console.log(typeof e);
console.log(typeof f);
```

### Exercise 3: Special Values

```javascript
let infinity = 1 / 0;
let negInfinity = -1 / 0;
let notNumber = "text" / 2;

console.log(infinity);
console.log(negInfinity);
console.log(notNumber);

console.log(typeof infinity);
console.log(typeof negInfinity);
console.log(typeof notNumber);
```

### Exercise 4: BigInt Practice

```javascript
let small = 100;
let big = 100n;

console.log(small);
console.log(big);

console.log(typeof small);
console.log(typeof big);

// Try arithmetic
let result = 50n + 50n;
console.log(result);
```

---

## Part 15: Key Takeaways

### ✅ Remember These Points

1. **Variables** store data in stack memory
2. Use `let` keyword to create variables
3. **Number** stores integers AND decimals
4. JavaScript is **loosely typed** (no need to specify type)
5. **Special numeric values:** Infinity, -Infinity, NaN
6. **BigInt** for numbers outside Number range (add `n` suffix)
7. **String** for text (use quotes)
8. **Boolean** for true/false
9. **Undefined** = declared but not assigned
10. Use `typeof` to check data type

### Data Type Quick Reference

| Type | Example | typeof Result |
|------|---------|---------------|
| Number | `let a = 23;` | "number" |
| Number | `let b = 5.9;` | "number" |
| BigInt | `let c = 100n;` | "bigint" |
| String | `let d = "Hi";` | "string" |
| Boolean | `let e = true;` | "boolean" |
| Undefined | `let f;` | "undefined" |
| Null | `let g = null;` | "object" (bug) |
| Symbol | `let h = Symbol();` | "symbol" |

---

## What's Next?

Now that you understand data types and how to use them, in the next lesson we'll learn about:

### Coming Up: JavaScript Day 6

- Variables in depth (let, const, var)
- Variable naming rules
- Variable scope
- Constants vs variables
- Best practices

---

*Congratulations! You've completed JavaScript Day 5. You now know how to use all JavaScript data types with practical examples!*

---

**See you in the next class!** 🚀
