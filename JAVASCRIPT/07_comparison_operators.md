# JavaScript Day 7: Comparison Operators

## Introduction

Comparison operators are used almost every single day in programming. They allow us to compare two values and make decisions based on the result.

**Programming = Creating Logic**

Logic is often based on **conditions**:
- Is the age equal to 18?
- Is the password correct?
- Is the username valid?

---

## Part 1: What are Comparison Operators?

### Definition

**Comparison Operators** = Operators that compare two values and return `true` or `false`.

### Result is Always Boolean

```javascript
// Comparison always returns boolean
5 == 5    // true
5 == 10   // false
```

---

## Part 2: Two Types of Equality

### 1. Equality Operator (==)

**Symbol:** `==` (double equal)

**Compares:** Values only (ignores type)

### 2. Strict Equality Operator (===)

**Symbol:** `===` (triple equal)

**Compares:** Values AND types (both must match)

---

## Part 3: Basic Comparisons - Same Types

### Comparing Numbers

```javascript
let age = 18;
console.log(age == 18);    // true
console.log(age == 20);    // false
```

### Comparing Strings

```javascript
let actualUsername = "tapacademy";
let enteredUsername = "tapacad";

console.log(actualUsername == enteredUsername);  // false

// Fix the typo
enteredUsername = "tapacademy";
console.log(actualUsername == enteredUsername);  // true
```

### Comparing Booleans

```javascript
let hasPassport = true;
console.log(hasPassport == true);   // true

hasPassport = false;
console.log(hasPassport == true);   // false
```

---

## Part 4: Comparing Different Types

### Number vs String

```javascript
console.log(5 == "5");     // true
console.log(5 === "5");    // false
```

**What happens with `==`:**
```
Step 1: JavaScript sees number vs string
Step 2: Converts string to number
Step 3: "5" becomes 5
Step 4: 5 == 5 → true
```

**What happens with `===`:**
```
Step 1: JavaScript sees number vs string
Step 2: Types don't match
Step 3: Returns false (no conversion)
```

### Implicit Type Conversion (Type Coercion)

When JavaScript automatically converts types, it's called:
- **Implicit Type Casting**
- **Type Coercion**

```javascript
// Explicit (you write the code)
let a = Number("5");

// Implicit (JavaScript does it automatically)
5 == "5"  // JavaScript converts "5" to 5
```

---

## Part 5: Conversion Rules

### Rule 1: Number vs String

**When comparing number with string:**
- String is ALWAYS converted to number

```javascript
console.log(5 == "5");     // true
// "5" → 5, then 5 == 5

console.log(10 == "10");   // true
// "10" → 10, then 10 == 10
```

### Rule 2: Boolean vs Number

**When comparing boolean with number:**
- Boolean is ALWAYS converted to number
- `true` → 1
- `false` → 0

```javascript
console.log(true == 1);    // true
// true → 1, then 1 == 1

console.log(false == 0);   // false
// false → 0, then 0 == 0
```

### Rule 3: Boolean vs String

**When comparing boolean with string:**
- Two-step conversion:
  1. String → Number
  2. Boolean → Number

```javascript
console.log(true == "1");  // true
// Step 1: "1" → 1
// Step 2: true → 1
// Result: 1 == 1 → true
```

---

## Part 6: Special Cases

### null vs undefined

```javascript
// With == (equality)
console.log(null == undefined);   // true

// With === (strict equality)
console.log(null === undefined);  // false
```

**Rule:** `null` and `undefined` are treated as equal with `==`, but not with `===`.

### Empty String vs Zero

```javascript
console.log("" == 0);      // true
console.log("" === 0);     // false
```

**Why true with `==`?**
- Empty string is a **falsy value**
- Falsy values convert to 0
- 0 == 0 → true

### Boolean vs Empty String

```javascript
console.log(false == "");  // true
console.log(false === ""); // false
```

**Why true with `==`?**
- Empty string is falsy → converts to 0
- false → converts to 0
- 0 == 0 → true

### null vs false

```javascript
console.log(null == false);   // false
console.log(null === false);  // false
```

**Important:** `null` is NOT treated as `false`!

### undefined vs Zero

```javascript
console.log(undefined == 0);   // false
console.log(undefined === 0);  // false
```

**Important:** `undefined` is NOT treated as 0!

### NaN Comparisons

```javascript
console.log(NaN == NaN);    // false
console.log(NaN === NaN);   // false
```

**Important:** NaN is NEVER equal to anything, not even itself!

---

## Part 7: Comments in JavaScript

### Single Line Comment

```javascript
// This is a single line comment
let age = 18;  // This line executes
```

### Multi-line Comment

```javascript
/*
This is a
multi-line
comment
*/
let name = "John";
```

### Using Comments

```javascript
// Comparing null and undefined
console.log(null == undefined);   // true

/*
console.log(5 == "5");  // This won't execute
console.log(10 == 20);  // This won't execute
*/
```

---

## Part 8: Comprehensive Examples

### Example 1: String Numbers vs Numbers

```javascript
// Leading zeros in strings
console.log("001" == 1);    // true
// "001" → 1, then 1 == 1

console.log("010" == 10);   // true
// "010" → 10, then 10 == 10

// With strict equality
console.log("001" === 1);   // false (different types)
console.log("010" === 10);  // false (different types)
```

### Example 2: Boolean vs String "true"

```javascript
console.log(true == "true");   // false
console.log(true === "true");  // false
```

**Why false?**
```
Step 1: "true" (string) → Number("true") → NaN
Step 2: true → 1
Step 3: NaN == 1 → false
```

### Example 3: Zero vs null

```javascript
console.log(0 == null);    // false
console.log(0 === null);   // false
```

**Important:** 0 and null are NOT the same!

### Example 4: Zero vs undefined

```javascript
console.log(0 == undefined);   // false
console.log(0 === undefined);  // false
```

**Important:** 0 and undefined are NOT the same!

---

## Part 9: Complete Comparison Table

### == (Equality) Results

| Comparison | Result | Reason |
|------------|--------|--------|
| `5 == 5` | `true` | Same value, same type |
| `5 == "5"` | `true` | "5" → 5, then equal |
| `true == 1` | `true` | true → 1, then equal |
| `false == 0` | `true` | false → 0, then equal |
| `"" == 0` | `true` | "" → 0, then equal |
| `null == undefined` | `true` | Special rule |
| `null == false` | `false` | null ≠ false |
| `undefined == 0` | `false` | undefined ≠ 0 |
| `NaN == NaN` | `false` | NaN never equals anything |

### === (Strict Equality) Results

| Comparison | Result | Reason |
|------------|--------|--------|
| `5 === 5` | `true` | Same value, same type |
| `5 === "5"` | `false` | Different types |
| `true === 1` | `false` | Different types |
| `false === 0` | `false` | Different types |
| `"" === 0` | `false` | Different types |
| `null === undefined` | `false` | Different types |
| `null === false` | `false` | Different types |
| `undefined === 0` | `false` | Different types |
| `NaN === NaN` | `false` | NaN never equals anything |

---

## Part 10: When to Use == vs ===

### Use === (Strict Equality) - Recommended

```javascript
// Best practice - use strict equality
if (age === 18) {
    console.log("Exactly 18");
}

if (username === "admin") {
    console.log("Admin user");
}
```

**Why?**
- More predictable
- No unexpected type conversions
- Safer code
- Industry standard

### Use == (Equality) - Rare Cases

```javascript
// Only when you specifically want type coercion
if (value == null) {
    // Checks for both null AND undefined
    console.log("Value is null or undefined");
}
```

---

## Part 11: Practical Examples

### Example 1: Login Validation

```javascript
let actualPassword = "secret123";
let enteredPassword = "secret123";

if (actualPassword === enteredPassword) {
    console.log("Login successful!");
} else {
    console.log("Wrong password!");
}
// Output: Login successful!
```

### Example 2: Age Verification

```javascript
let age = 18;

if (age === 18) {
    console.log("Exactly 18 years old");
}

if (age == "18") {
    console.log("This also works but not recommended");
}
```

### Example 3: Form Validation

```javascript
let username = "john_doe";
let email = "john@example.com";

// Check if fields are not empty
if (username !== "" && email !== "") {
    console.log("Form is valid");
} else {
    console.log("Please fill all fields");
}
```

### Example 4: Checking for null or undefined

```javascript
let value = null;

// Check for both null and undefined
if (value == null) {
    console.log("Value is null or undefined");
}

// Check specifically for null
if (value === null) {
    console.log("Value is exactly null");
}
```

---

## Part 12: Common Mistakes

### Mistake 1: Using = instead of ==

```javascript
let age = 18;

// Wrong - assignment, not comparison
if (age = 20) {  // ❌ This assigns 20 to age!
    console.log("This always runs");
}

// Correct - comparison
if (age == 20) {  // ✅ This compares
    console.log("Age is 20");
}
```

### Mistake 2: Expecting NaN to equal NaN

```javascript
let result = "hello" / 2;  // NaN

// Wrong
if (result == NaN) {  // ❌ Always false!
    console.log("Is NaN");
}

// Correct
if (isNaN(result)) {  // ✅ Use isNaN() function
    console.log("Is NaN");
}
```

### Mistake 3: Confusing null with false

```javascript
let value = null;

// Wrong assumption
if (value == false) {  // ❌ false! null ≠ false
    console.log("This won't run");
}

// Correct
if (value === null) {  // ✅ Correct check
    console.log("Value is null");
}
```

---

## Part 13: Other Comparison Operators

### Not Equal (!=)

```javascript
console.log(5 != 10);      // true
console.log(5 != "5");     // false (type coercion)
```

### Strict Not Equal (!==)

```javascript
console.log(5 !== 10);     // true
console.log(5 !== "5");    // true (different types)
```

### Greater Than (>)

```javascript
console.log(10 > 5);       // true
console.log(5 > 10);       // false
```

### Less Than (<)

```javascript
console.log(5 < 10);       // true
console.log(10 < 5);       // false
```

### Greater Than or Equal (>=)

```javascript
console.log(10 >= 10);     // true
console.log(10 >= 5);      // true
console.log(5 >= 10);      // false
```

### Less Than or Equal (<=)

```javascript
console.log(5 <= 10);      // true
console.log(10 <= 10);     // true
console.log(10 <= 5);      // false
```

---

## Part 14: Practice Exercises

### Exercise 1: Predict the Output

```javascript
console.log(10 == "10");
console.log(10 === "10");
console.log(true == 1);
console.log(true === 1);
console.log(false == 0);
console.log("" == 0);
console.log(null == undefined);
console.log(null === undefined);
```

### Exercise 2: Fix the Code

```javascript
// Fix this code to use strict equality
let age = 18;
if (age == "18") {  // Change to ===
    console.log("Adult");
}
```

### Exercise 3: Login System

```javascript
let correctUsername = "admin";
let correctPassword = "pass123";

let enteredUsername = "admin";
let enteredPassword = "pass123";

// Write code to check if login is successful
// Use strict equality
```

### Exercise 4: Type Checking

```javascript
let value1 = 5;
let value2 = "5";

// Check if values are equal (ignoring type)
// Check if values are equal (including type)
// Print appropriate messages
```

---

## Part 15: Key Takeaways

### ✅ Remember These Points

1. **Comparison operators** return `true` or `false`
2. **== (equality)** compares values only (type coercion)
3. **=== (strict equality)** compares values AND types
4. **Always prefer ===** for safer code
5. **String → Number** when comparing number with string
6. **Boolean → Number** when comparing boolean with number
7. **true = 1, false = 0** in conversions
8. **null == undefined** is `true`
9. **null === undefined** is `false`
10. **NaN never equals anything**, not even itself

### Comparison Operators Summary

```javascript
==   // Equal (with type coercion)
===  // Strict equal (no type coercion)
!=   // Not equal (with type coercion)
!==  // Strict not equal (no type coercion)
>    // Greater than
<    // Less than
>=   // Greater than or equal
<=   // Less than or equal
```

---

## What's Next?

Now that you understand comparison operators, in the next lesson we'll learn about:

### Coming Up: JavaScript Day 8

- Logical operators (AND, OR, NOT)
- Combining conditions
- Complex decision making
- Operator precedence

---

*Congratulations! You've completed JavaScript Day 7. You now understand comparison operators and can make decisions in your code!*

---

**See you in the next class!** 🚀
