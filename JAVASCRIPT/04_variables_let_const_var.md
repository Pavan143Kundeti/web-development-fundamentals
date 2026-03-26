# JavaScript Day 04 Part 1: Variables - let, const, var

## Introduction

Variables are containers for storing data values. In JavaScript, you can declare variables using `let`, `const`, or `var`. Understanding how to use variables correctly is fundamental to programming.

**Think of variables as labeled boxes where you can store different types of information.**

---

## Part 1: What are Variables?

### Variables = Data Containers

Variables are containers that hold data values. They give names to data so you can use it in your program.

### Visual: Variable Concept

```
Variable Name: age
    ↓
┌─────────┐
│   25    │  ← Value stored
└─────────┘
```

### Basic Example

```javascript
let x = 5;
let y = 6;
let z = x + y;

console.log(z);  // Output: 11
```

---

## Part 2: Four Ways to Declare Variables

### Modern JavaScript (Recommended)

| Keyword | Description | When to Use |
|---------|-------------|-------------|
| `let` | Variable that can change | When value will change |
| `const` | Variable that cannot change | When value stays the same |

### Older JavaScript (Not Recommended)

| Keyword | Description | Why Not |
|---------|-------------|---------|
| `var` | Old way to declare variables | Has scope issues |
| Automatic | No keyword | Creates global variables |

### Example: Using let

```javascript
let x = 5;
let y = 6;
let z = x + y;

console.log(z);  // Output: 11
```

### Example: Using const

```javascript
const x = 5;
const y = 6;
const z = x + y;

console.log(z);  // Output: 11
```

---

## Part 3: Variable Names (Identifiers)

### Naming Rules

| Rule | Valid | Invalid |
|------|-------|---------|
| Start with letter, $, or _ | `name`, `$price`, `_value` | `1name`, `@value` |
| Can contain letters, digits, _, $ | `user1`, `total_price` | `user-name`, `total price` |
| Case sensitive | `Name` ≠ `name` | - |
| No reserved words | `myVar` | `let`, `function` |

### Valid Variable Names

```javascript
let name = "John";
let age = 25;
let firstName = "John";
let first_name = "John";
let $price = 100;
let _value = 50;
```

### Invalid Variable Names

```javascript
let 1name = "John";      // ❌ Cannot start with number
let first-name = "John"; // ❌ Cannot use hyphen
let first name = "John"; // ❌ Cannot have space
let let = "John";        // ❌ Cannot use reserved word
```

---

## Part 4: Using Underscore (_)

### Underscore as Letter

JavaScript treats underscore as a letter:

```javascript
let _lastName = "Johnson";
let _x = 2;
let _100 = 5;

console.log(_lastName);  // Output: Johnson
```

### Convention: Private Variables

Programmers often use underscore for "private" variables:

```javascript
let _privateValue = 100;  // Indicates internal use
let publicValue = 200;    // Indicates external use
```

---

## Part 5: Using Dollar Sign ($)

### Dollar Sign as Letter

JavaScript treats $ as a letter:

```javascript
let $ = "Hello World";
let $$$ = 2;
let $myMoney = 5;

console.log($);  // Output: Hello World
```

### Common Use: Libraries

$ is often used in JavaScript libraries (like jQuery):

```javascript
let $element = document.getElementById("demo");
```

---

## Part 6: Declaring Variables with let

### Basic Declaration

```javascript
let carName;  // Declare variable
```

After declaration, the variable is `undefined`:

```javascript
let carName;
console.log(carName);  // Output: undefined
```

### Assigning Value

```javascript
let carName;
carName = "Volvo";  // Assign value

console.log(carName);  // Output: Volvo
```

### Declare and Assign Together

```javascript
let carName = "Volvo";  // Declare and assign

console.log(carName);  // Output: Volvo
```

---

## Part 7: Declaring Variables with const

### Must Assign Value

```javascript
// Correct ✅
const PI = 3.14159;

// Wrong ❌
const PI;  // Error: Missing initializer
PI = 3.14159;
```

### Cannot Reassign

```javascript
const PI = 3.14159;
PI = 3.14;  // Error: Assignment to constant variable
```

### Example: Mixed Usage

```javascript
const price1 = 5;   // Won't change
const price2 = 6;   // Won't change
let total = price1 + price2;  // Can change

console.log(total);  // Output: 11

total = 20;  // This works
console.log(total);  // Output: 20
```

---

## Part 8: Declaring Variables with var (Not Recommended)

### Old Way

```javascript
var x = 5;
var y = 6;
var z = x + y;

console.log(z);  // Output: 11
```

### Why Not Use var?

- Has function scope (not block scope)
- Can be redeclared
- Gets hoisted
- Causes confusion

**Use `let` or `const` instead!**

---

## Part 9: Automatic Declaration (Not Recommended)

### Without Keyword

```javascript
x = 5;  // Automatically declared
y = 6;
z = x + y;

console.log(z);  // Output: 11
```

### Why Not?

- Creates global variables
- Hard to track
- Causes bugs
- Bad practice

**Always declare variables with `let` or `const`!**

---

## Part 10: When to Use var, let, or const?

### Best Practices

1. ✅ Always declare variables
2. ✅ Use `const` if value won't change
3. ✅ Use `const` for arrays and objects
4. ✅ Use `let` if you can't use `const`
5. ❌ Never use `var` if you can use `let` or `const`

### Decision Tree

```
Will the value change?
    ↓
   No → Use const
    ↓
   Yes → Use let
```

---

## Part 11: JavaScript Data Types

### Two Main Types

```javascript
// Numbers (no quotes)
const pi = 3.14;
let age = 25;

// Strings (with quotes)
let person = "John Doe";
let answer = 'Yes I am!';
```

### Number in Quotes = String

```javascript
let x = "5";  // String, not number
let y = 5;    // Number

console.log(typeof x);  // Output: string
console.log(typeof y);  // Output: number
```

---

## Part 12: Multiple Variables in One Statement

### Comma Separated

```javascript
let person = "John Doe", carName = "Volvo", price = 200;

console.log(person);   // Output: John Doe
console.log(carName);  // Output: Volvo
console.log(price);    // Output: 200
```

### Multiple Lines

```javascript
let person = "John Doe",
    carName = "Volvo",
    price = 200;
```

---

## Part 13: The Assignment Operator

### = is Assignment, Not Equality

```javascript
let x = 5;  // Assign 5 to x
```

### This Makes Sense in JavaScript

```javascript
let x = 5;
x = x + 5;  // x is now 10

console.log(x);  // Output: 10
```

### Visual: Assignment

```
x = x + 5

Step 1: Get value of x (5)
Step 2: Add 5 (5 + 5 = 10)
Step 3: Assign result to x (x = 10)
```

---

## Part 14: JavaScript Arithmetic

### With Numbers

```javascript
let x = 5 + 2 + 3;
console.log(x);  // Output: 10
```

### With Strings

```javascript
let x = "John" + " " + "Doe";
console.log(x);  // Output: John Doe
```

### Mixed: Number in Quotes

```javascript
let x = "5" + 2 + 3;
console.log(x);  // Output: 523 (string concatenation)

let y = 2 + 3 + "5";
console.log(y);  // Output: 55 (2+3=5, then "5"+"5"="55")
```

---

## Part 15: Block Scope (let and const)

### What is Block Scope?

Variables declared inside `{ }` cannot be accessed outside:

```javascript
{
    let x = 2;
    console.log(x);  // Output: 2
}

console.log(x);  // Error: x is not defined
```

### Example: if Statement

```javascript
if (true) {
    let x = 10;
    console.log(x);  // Output: 10
}

console.log(x);  // Error: x is not defined
```

### Visual: Block Scope

```
Outside block
    ↓
┌─────────────────┐
│  Inside block   │
│  let x = 2;     │ ← x only exists here
└─────────────────┘
    ↓
Outside block (x doesn't exist)
```

---

## Part 16: Function Scope

### All Variables Have Function Scope

```javascript
function myFunction() {
    var x = 1;
    let y = 2;
    const z = 3;
    
    console.log(x, y, z);  // Output: 1 2 3
}

myFunction();

// None of these work outside:
console.log(x);  // Error
console.log(y);  // Error
console.log(z);  // Error
```

---

## Part 17: Global Scope (var)

### var Has No Block Scope

```javascript
{
    var x = 2;
}

console.log(x);  // Output: 2 (works!)
```

### Problem with var

```javascript
var x = 10;  // x is 10

{
    var x = 2;  // This changes the outer x!
}

console.log(x);  // Output: 2 (not 10!)
```

### Solution: Use let

```javascript
let x = 10;  // x is 10

{
    let x = 2;  // This is a different x
}

console.log(x);  // Output: 10 (correct!)
```

---

## Part 18: Cannot Redeclare with let

### let Prevents Redeclaration

```javascript
let x = "John Doe";
let x = 0;  // Error: Identifier 'x' has already been declared
```

### var Allows Redeclaration (Problem!)

```javascript
var x = "John Doe";
var x = 0;  // No error (but confusing!)

console.log(x);  // Output: 0
```

---

## Part 19: Redeclaring in Different Blocks

### Same Block: Not Allowed

```javascript
let x = 2;
let x = 3;  // Error
```

### Different Block: Allowed

```javascript
let x = 2;  // x is 2

{
    let x = 3;  // Different x, allowed
    console.log(x);  // Output: 3
}

console.log(x);  // Output: 2
```

---

## Part 20: Hoisting

### var is Hoisted

```javascript
// This works (but shouldn't!)
carName = "Volvo";
var carName;

console.log(carName);  // Output: Volvo
```

### let is Not Initialized

```javascript
// This doesn't work
carName = "Saab";
let carName = "Volvo";  // Error: Cannot access before initialization
```

---

## Part 21: const with Arrays

### Can Change Elements

```javascript
const cars = ["Saab", "Volvo", "BMW"];

// Change element ✅
cars[0] = "Toyota";
console.log(cars);  // Output: ["Toyota", "Volvo", "BMW"]

// Add element ✅
cars.push("Audi");
console.log(cars);  // Output: ["Toyota", "Volvo", "BMW", "Audi"]
```

### Cannot Reassign Array

```javascript
const cars = ["Saab", "Volvo", "BMW"];

// Reassign ❌
cars = ["Toyota", "Volvo", "Audi"];  // Error!
```

---

## Part 22: const with Objects

### Can Change Properties

```javascript
const car = {type: "Fiat", model: "500", color: "white"};

// Change property ✅
car.color = "red";
console.log(car.color);  // Output: red

// Add property ✅
car.owner = "Johnson";
console.log(car.owner);  // Output: Johnson
```

### Cannot Reassign Object

```javascript
const car = {type: "Fiat", model: "500", color: "white"};

// Reassign ❌
car = {type: "Volvo", model: "EX60", color: "red"};  // Error!
```

---

## Part 23: Comparison Table

### var vs let vs const

| Feature | var | let | const |
|---------|-----|-----|-------|
| Block Scope | No | Yes | Yes |
| Can Redeclare | Yes | No | No |
| Can Reassign | Yes | Yes | No |
| Hoisted | Yes | Yes | Yes |
| Initialized when Hoisted | Yes | No | No |
| Binds to this | Yes | No | No |

---

## Part 24: Key Takeaways

### ✅ Remember These Points

1. **Variables** store data values
2. **let** for values that change
3. **const** for values that don't change
4. **var** is old, don't use it
5. **Always declare** variables
6. **Names** must start with letter, $, or _
7. **Block scope** with let and const
8. **const arrays/objects** can be modified
9. **Cannot reassign** const variables
10. **Use const by default**, let when needed

### Quick Reference

```javascript
// Declare with let (can change)
let age = 25;
age = 26;  // OK

// Declare with const (cannot change)
const PI = 3.14159;
PI = 3.14;  // Error!

// const with array (can modify)
const numbers = [1, 2, 3];
numbers.push(4);  // OK
numbers = [5, 6];  // Error!

// const with object (can modify)
const person = {name: "John"};
person.age = 30;  // OK
person = {name: "Jane"};  // Error!

// Multiple variables
let x = 5, y = 6, z = x + y;

// Block scope
{
    let x = 2;  // Only exists in this block
}
```

---

## What's Next?

In the next lesson, we'll learn about:

### Coming Up: JavaScript Day 04 Part 2

- Data types in detail
- Primitive vs reference types
- typeof operator
- Type checking
- Practical examples

---

*Congratulations! You've completed JavaScript Day 04 Part 1. You now understand variables in JavaScript!*

---

**Practice declaring variables and see you in the next class!** 🚀
