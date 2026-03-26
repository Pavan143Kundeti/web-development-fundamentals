# JavaScript Day 6: Type Conversion (Type Casting)

## Introduction

In JavaScript, we work with different data types: Number, String, Boolean, etc. Sometimes, we need to convert one type of data into another type. This process is called **Type Conversion** or **Type Casting**.

---

## Part 1: What is Type Conversion?

### Definition

**Type Conversion (Type Casting)** = Converting one data type into another data type.

### Examples of Conversion

```
Number → String
String → Number
Boolean → String
Number → Boolean
String → Boolean
```

### Why Do We Need Type Conversion?

In real-world programming, you often need to:
- Convert user input (string) to numbers for calculations
- Convert numbers to strings for display
- Convert values to boolean for conditions

---

## Part 2: Most Common Data Types

### The Big Three

99% of the time, you'll work with these three types:

```
1. Number   - for calculations
2. String   - for text
3. Boolean  - for true/false conditions
```

---

## Part 3: Converting Number to String

### Using String() Function

```javascript
let a = 123;
console.log(a);              // Output: 123
console.log(typeof a);       // Output: number

// Convert to string
let b = String(a);
console.log(b);              // Output: 123
console.log(typeof b);       // Output: string
```

### Important Memory Concept

```
STACK Memory:

Step 1: Create variable a
┌─────────┐
│   123   │ ← a (number)
└─────────┘

Step 2: String(a) creates a COPY
┌─────────┐     ┌─────────┐
│   123   │ ← a │  "123"  │ ← copy (string)
└─────────┘     └─────────┘

Step 3: Store copy in b
┌─────────┐     ┌─────────┐
│   123   │ ← a │  "123"  │ ← b (string)
└─────────┘     └─────────┘
```

### Common Mistake

```javascript
let a = 123;

// Wrong - doesn't store the result
String(a);
console.log(typeof a);       // Still "number"!

// Correct - store in a variable
let b = String(a);
console.log(typeof b);       // "string" ✅
```

### Complete Example

```javascript
// Original number
let age = 23;
console.log(age);            // 23
console.log(typeof age);     // number

// Convert to string
let ageString = String(age);
console.log(ageString);      // 23
console.log(typeof ageString); // string

// Original is unchanged
console.log(typeof age);     // still number
```

---

## Part 4: Converting Boolean to String

### Using String() Function

```javascript
let a = false;
console.log(a);              // Output: false
console.log(typeof a);       // Output: boolean

// Convert to string
let b = String(a);
console.log(b);              // Output: false
console.log(typeof b);       // Output: string
```

### Memory Visualization

```
STACK Memory:

┌─────────┐     ┌─────────┐
│  false  │ ← a │ "false" │ ← b
│(boolean)│     │(string) │
└─────────┘     └─────────┘
```

### Examples

```javascript
// true to string
let isActive = true;
let activeString = String(isActive);
console.log(activeString);       // "true"
console.log(typeof activeString); // string

// false to string
let hasPermission = false;
let permString = String(hasPermission);
console.log(permString);         // "false"
console.log(typeof permString);  // string
```

---

## Part 5: Converting String to Number

### Using Number() Function

```javascript
let a = "123";
console.log(a);              // Output: 123
console.log(typeof a);       // Output: string

// Convert to number
let b = Number(a);
console.log(b);              // Output: 123
console.log(typeof b);       // Output: number
```

### What Happens with Invalid Strings?

```javascript
let a = "123tap";
let b = Number(a);
console.log(b);              // Output: NaN (Not a Number)
console.log(typeof b);       // Output: number
```

**Important:** NaN (Not a Number) is still of type "number"!

---

## Part 6: Using parseInt() Function

### What is parseInt()?

**parseInt()** converts a string to an integer by reading from left to right and stopping at the first non-numeric character.

### How parseInt() Works

```
Process:
1. Start from left
2. Check each character
3. If numeric or space → continue
4. If non-numeric → STOP
5. Return what was collected
```

### Example 1: "123tap"

```javascript
let a = "123tap";
let b = parseInt(a);
console.log(b);              // Output: 123
console.log(typeof b);       // Output: number
```

**How it works:**
```
"123tap"
 ↓
'1' → numeric ✅ → take it
'2' → numeric ✅ → take it
'3' → numeric ✅ → take it
't' → non-numeric ❌ → STOP
Result: 123
```

### Example 2: "tap123"

```javascript
let a = "tap123";
let b = parseInt(a);
console.log(b);              // Output: NaN
```

**How it works:**
```
"tap123"
 ↓
't' → non-numeric ❌ → STOP immediately
Result: NaN (nothing collected)
```

### Example 3: " 123tap" (space at start)

```javascript
let a = " 123tap";
let b = parseInt(a);
console.log(b);              // Output: 123
```

**How it works:**
```
" 123tap"
 ↓
' ' → space ✅ → can skip
'1' → numeric ✅ → take it
'2' → numeric ✅ → take it
'3' → numeric ✅ → take it
't' → non-numeric ❌ → STOP
Result: 123
```

### Example 4: "1 2 3" (spaces between)

```javascript
let a = "1 2 3";
let b = parseInt(a);
console.log(b);              // Output: 1
```

**How it works:**
```
"1 2 3"
 ↓
'1' → numeric ✅ → take it
' ' → space after number ❌ → STOP
Result: 1
```

### parseInt() Rules Summary

```
✅ Allowed before numbers:
   - Leading spaces

✅ Allowed as numbers:
   - Digits 0-9

❌ Stops at:
   - First non-numeric character
   - Space after a number
   - Any letter or special character
```

---

## Part 7: Number() vs parseInt()

### Comparison

| Feature | Number() | parseInt() |
|---------|----------|------------|
| "123" | 123 | 123 |
| "123tap" | NaN | 123 |
| "tap123" | NaN | NaN |
| " 123tap" | NaN | 123 |
| "1 2 3" | NaN | 1 |

### When to Use What?

```javascript
// Use Number() when:
// - String contains ONLY numbers
let a = "123";
Number(a);  // 123 ✅

// Use parseInt() when:
// - String might have non-numeric characters
let b = "123px";
parseInt(b);  // 123 ✅
Number(b);    // NaN ❌
```

---

## Part 8: Converting Boolean to Number

### Conversion Rules

```
true  → 1
false → 0
```

### Examples

```javascript
// true to number
let a = true;
let b = Number(a);
console.log(b);              // Output: 1
console.log(typeof b);       // Output: number

// false to number
let c = false;
let d = Number(c);
console.log(d);              // Output: 0
console.log(typeof d);       // Output: number
```

### Practical Example

```javascript
let isLoggedIn = true;
let loginStatus = Number(isLoggedIn);
console.log(loginStatus);    // 1

let hasPermission = false;
let permissionStatus = Number(hasPermission);
console.log(permissionStatus); // 0
```

---

## Part 9: Converting Number to Boolean

### Conversion Rules

```
Any non-zero number → true
Zero (0)            → false
```

### Examples

```javascript
// Positive numbers
console.log(Boolean(1));       // true
console.log(Boolean(123));     // true
console.log(Boolean(456));     // true

// Negative numbers
console.log(Boolean(-1));      // true
console.log(Boolean(-123));    // true

// Zero
console.log(Boolean(0));       // false

// Special values
console.log(Boolean(Infinity));  // true
console.log(Boolean(-Infinity)); // true
console.log(Boolean(NaN));       // false
```

### Complete Example

```javascript
let a = 1;
console.log(Boolean(a));       // true

let b = 0;
console.log(Boolean(b));       // false

let c = -123;
console.log(Boolean(c));       // true

let d = 123456;
console.log(Boolean(d));       // true
```

---

## Part 10: Converting String to Boolean

### Conversion Rules

```
Non-empty string → true
Empty string ""  → false
```

### Examples

```javascript
// Non-empty strings
console.log(Boolean("Tap Academy")); // true
console.log(Boolean("123"));         // true
console.log(Boolean("hello"));       // true
console.log(Boolean(" "));           // true (space is a character!)

// Empty string
console.log(Boolean(""));            // false
```

### Important: Space vs Empty

```javascript
// Empty string
let a = "";
console.log(Boolean(a));       // false

// String with space (NOT empty!)
let b = " ";
console.log(Boolean(b));       // true
```

---

## Part 11: Truthy and Falsy Values

### Truthy Values (Convert to true)

```javascript
// Numbers (non-zero)
Boolean(1)           // true
Boolean(123)         // true
Boolean(-456)        // true
Boolean(Infinity)    // true
Boolean(-Infinity)   // true

// Strings (non-empty)
Boolean("hello")     // true
Boolean("123")       // true
Boolean(" ")         // true (space counts!)

// Arrays (non-empty)
Boolean([1, 2, 3])   // true
```

### Falsy Values (Convert to false)

```javascript
// Zero
Boolean(0)           // false

// NaN
Boolean(NaN)         // false

// Empty string
Boolean("")          // false

// Null
Boolean(null)        // false

// Undefined
Boolean(undefined)   // false

// Empty array
Boolean([])          // false
```

### Truthy vs Falsy Summary

```
TRUTHY VALUES:
├── Any non-zero number (1, -1, 123, -456)
├── Infinity and -Infinity
├── Non-empty strings ("hello", "123", " ")
└── Non-empty arrays ([1, 2, 3])

FALSY VALUES:
├── 0 (zero)
├── NaN (Not a Number)
├── "" (empty string)
├── null
├── undefined
└── [] (empty array)
```

---

## Part 12: Practical Examples

### Example 1: User Input Conversion

```javascript
// User enters age as string
let userInput = "25";
console.log(typeof userInput);  // string

// Convert to number for calculation
let age = Number(userInput);
console.log(typeof age);        // number

// Now can do math
let nextYear = age + 1;
console.log(nextYear);          // 26
```

### Example 2: Form Validation

```javascript
// Check if input is empty
let username = "";
if (Boolean(username)) {
    console.log("Valid username");
} else {
    console.log("Username cannot be empty");
}
// Output: Username cannot be empty
```

### Example 3: Parsing Pixel Values

```javascript
// CSS returns "100px"
let width = "100px";

// Extract number
let widthNum = parseInt(width);
console.log(widthNum);          // 100

// Can now do calculations
let newWidth = widthNum + 50;
console.log(newWidth + "px");   // "150px"
```

### Example 4: Boolean Flags

```javascript
// Convert number to boolean for conditions
let errorCount = 0;

if (Boolean(errorCount)) {
    console.log("Has errors");
} else {
    console.log("No errors");
}
// Output: No errors
```

---

## Part 13: Type Conversion Summary Table

### All Conversions

| From | To | Function | Example | Result |
|------|----|---------| --------|--------|
| Number | String | `String()` | `String(123)` | `"123"` |
| Boolean | String | `String()` | `String(true)` | `"true"` |
| String | Number | `Number()` | `Number("123")` | `123` |
| String | Number | `parseInt()` | `parseInt("123px")` | `123` |
| Boolean | Number | `Number()` | `Number(true)` | `1` |
| Number | Boolean | `Boolean()` | `Boolean(1)` | `true` |
| String | Boolean | `Boolean()` | `Boolean("hi")` | `true` |

---

## Part 14: Common Mistakes

### Mistake 1: Not Storing Result

```javascript
// Wrong
let a = 123;
String(a);
console.log(typeof a);  // still "number" ❌

// Correct
let a = 123;
let b = String(a);
console.log(typeof b);  // "string" ✅
```

### Mistake 2: Expecting parseInt() to Parse Everything

```javascript
// Wrong expectation
let a = "tap123";
let b = parseInt(a);
console.log(b);  // NaN (not 123!) ❌

// Correct understanding
let c = "123tap";
let d = parseInt(c);
console.log(d);  // 123 ✅
```

### Mistake 3: Forgetting Space is a Character

```javascript
// Wrong assumption
let a = " ";
console.log(Boolean(a));  // true (not false!) ❌

// Correct - empty string
let b = "";
console.log(Boolean(b));  // false ✅
```

---

## Part 15: Practice Exercises

### Exercise 1: Number to String

```javascript
let age = 25;
let height = 5.9;
let weight = 68.5;

// Convert all to strings
let ageStr = String(age);
let heightStr = String(height);
let weightStr = String(weight);

console.log(typeof ageStr);
console.log(typeof heightStr);
console.log(typeof weightStr);
```

### Exercise 2: String to Number

```javascript
let price1 = "99";
let price2 = "49.99";
let price3 = "100px";

// Convert to numbers
let num1 = Number(price1);
let num2 = Number(price2);
let num3 = parseInt(price3);

console.log(num1);
console.log(num2);
console.log(num3);
```

### Exercise 3: Boolean Conversions

```javascript
// To boolean
console.log(Boolean(1));
console.log(Boolean(0));
console.log(Boolean("hello"));
console.log(Boolean(""));
console.log(Boolean(null));

// From boolean
console.log(Number(true));
console.log(Number(false));
console.log(String(true));
console.log(String(false));
```

### Exercise 4: parseInt() Practice

```javascript
console.log(parseInt("123"));
console.log(parseInt("123abc"));
console.log(parseInt("abc123"));
console.log(parseInt(" 123"));
console.log(parseInt("1 2 3"));
```

---

## Part 16: Key Takeaways

### ✅ Remember These Points

1. **Type Conversion** = Converting one data type to another
2. **String()** converts to string
3. **Number()** converts to number (strict)
4. **parseInt()** converts string to integer (flexible)
5. **Boolean()** converts to boolean
6. **Truthy values** convert to `true`
7. **Falsy values** convert to `false`
8. **Always store** conversion result in a variable
9. **parseInt()** stops at first non-numeric character
10. **Empty string** is falsy, **space** is truthy

### Conversion Functions

```javascript
String()    // → string
Number()    // → number (strict)
parseInt()  // → integer (flexible)
Boolean()   // → boolean
```

---

## What's Next?

Now that you understand type conversion, in the next lesson we'll learn about:

### Coming Up: JavaScript Day 7

- Operators (arithmetic, comparison, logical)
- Working with different data types
- Expressions and statements
- Operator precedence

---

*Congratulations! You've completed JavaScript Day 6. You now understand how to convert between different data types in JavaScript!*

---

**See you in the next class!** 🚀
