# JavaScript Day 12: Numbers and BigInt

## Introduction

Numbers are fundamental to programming. In JavaScript, working with numbers is straightforward, but there are important concepts you need to understand to use them correctly.

---

## Part 1: JavaScript Number Type

### One Number Type

Unlike many programming languages, JavaScript has only ONE type of number.

**Other languages have:**
- byte, short, int, long (integers)
- float, double (decimals)

**JavaScript has:**
- Just "Number" (for everything)

### Creating Numbers

```javascript
let x = 3.14;      // Number with decimals
let y = 3;         // Number without decimals
let z = 100;       // Another whole number
```

**Important:** Both integers and decimals are the same type in JavaScript!

---

## Part 2: How JavaScript Stores Numbers

### 64-bit Floating Point

All JavaScript numbers are stored as 64-bit floating-point numbers (IEEE 754 standard).

### Visual: 64-bit Structure

```
┌─────────────────────────────────────────────────────────────┐
│                    64 bits total                             │
├──────────────────────────────────┬──────────────┬───────────┤
│     Value (Mantissa)             │   Exponent   │   Sign    │
│        52 bits                   │   11 bits    │   1 bit   │
│      (bits 0-51)                 │  (bits 52-62)│  (bit 63) │
└──────────────────────────────────┴──────────────┴───────────┘
```

**What this means:**
- JavaScript can store very large and very small numbers
- But there are limits to precision

---

## Part 3: Scientific Notation

### Writing Large or Small Numbers

Use `e` for scientific notation:

```javascript
let large = 123e5;      // 12300000
let small = 123e-5;     // 0.00123

console.log(large);     // Output: 12300000
console.log(small);     // Output: 0.00123
```

### How Scientific Notation Works

| Notation | Meaning | Result |
|----------|---------|--------|
| `123e5` | 123 × 10⁵ | 12300000 |
| `123e-5` | 123 × 10⁻⁵ | 0.00123 |
| `5e3` | 5 × 10³ | 5000 |
| `2e-3` | 2 × 10⁻³ | 0.002 |

---

## Part 4: Number Precision

### Integer Precision

Integers are accurate up to 15 digits:

```javascript
let x = 999999999999999;    // 15 digits - accurate ✅
console.log(x);             // Output: 999999999999999

let y = 9999999999999999;   // 16 digits - NOT accurate ❌
console.log(y);             // Output: 10000000000000000 (rounded!)
```

### Floating Point Precision

Decimal arithmetic is not always 100% accurate:

```javascript
let x = 0.2 + 0.1;
console.log(x);  // Output: 0.30000000000000004 (not 0.3!)
```

**Why?** Computers store numbers in binary, and some decimals can't be represented exactly.

### Solution: Multiply and Divide

```javascript
let x = (0.2 * 10 + 0.1 * 10) / 10;
console.log(x);  // Output: 0.3 ✅
```

---

## Part 5: Adding Numbers vs Strings

### The + Operator Problem

The `+` operator works for BOTH addition and concatenation.

### Number + Number = Addition

```javascript
let x = 10;
let y = 20;
let z = x + y;
console.log(z);  // Output: 30
```

### String + String = Concatenation

```javascript
let x = "10";
let y = "20";
let z = x + y;
console.log(z);  // Output: "1020" (text, not number!)
```

### Number + String = Concatenation

```javascript
let x = 10;        // Number
let y = "20";      // String
let z = x + y;
console.log(z);    // Output: "1020" (becomes string!)
```

### Common Mistake

```javascript
let x = 10;
let y = 20;
let z = "The result is: " + x + y;
console.log(z);  // Output: "The result is: 1020" ❌
```

**Why?** JavaScript reads left to right:
1. "The result is: " + 10 = "The result is: 10" (string)
2. "The result is: 10" + 20 = "The result is: 1020" (string)

### Correct Way

```javascript
let x = 10;
let y = 20;
let z = "The result is: " + (x + y);
console.log(z);  // Output: "The result is: 30" ✅
```

---

## Part 6: Other Numeric Operations

### Subtraction, Multiplication, Division

JavaScript automatically converts strings to numbers for these operations:

```javascript
// Subtraction
let x = "100" - "10";
console.log(x);  // Output: 90 (number)

// Multiplication
let y = "100" * "10";
console.log(y);  // Output: 1000 (number)

// Division
let z = "100" / "10";
console.log(z);  // Output: 10 (number)
```

**But addition doesn't work this way!**

```javascript
let result = "100" + "10";
console.log(result);  // Output: "10010" (string concatenation)
```

---

## Part 7: NaN - Not a Number

### What is NaN?

NaN means "Not a Number" - it appears when a math operation fails.

```javascript
let x = 100 / "Apple";
console.log(x);  // Output: NaN
```

### Checking for NaN

Use `isNaN()` function:

```javascript
let x = 100 / "Apple";
console.log(isNaN(x));  // Output: true

let y = 100 / "10";
console.log(isNaN(y));  // Output: false (result is 10)
```

### NaN in Operations

```javascript
let x = NaN;
let y = 5;
let z = x + y;
console.log(z);  // Output: NaN (NaN spreads!)

let a = NaN;
let b = "5";
let c = a + b;
console.log(c);  // Output: "NaN5" (string concatenation)
```

### Interesting Fact

```javascript
console.log(typeof NaN);  // Output: "number"
```

NaN is technically a number type!

---

## Part 8: Infinity

### What is Infinity?

Infinity appears when a number exceeds JavaScript's limits.

```javascript
let x = 2 / 0;
console.log(x);  // Output: Infinity

let y = -2 / 0;
console.log(y);  // Output: -Infinity
```

### Infinity in Loops

```javascript
let myNumber = 2;
while (myNumber != Infinity) {
    myNumber = myNumber * myNumber;
    console.log(myNumber);
}
// Eventually reaches Infinity and stops
```

### Type of Infinity

```javascript
console.log(typeof Infinity);  // Output: "number"
```

---

## Part 9: Number Systems

### Hexadecimal (Base 16)

Use `0x` prefix:

```javascript
let hex = 0xFF;
console.log(hex);  // Output: 255
```

### Converting Between Bases

Use `toString()` method:

```javascript
let num = 32;

console.log(num.toString(2));   // Binary: "100000"
console.log(num.toString(8));   // Octal: "40"
console.log(num.toString(10));  // Decimal: "32"
console.log(num.toString(16));  // Hexadecimal: "20"
```

### Number System Table

| Base | Name | Digits Used | Example |
|------|------|-------------|---------|
| 2 | Binary | 0-1 | 1010 |
| 8 | Octal | 0-7 | 52 |
| 10 | Decimal | 0-9 | 42 |
| 16 | Hexadecimal | 0-9, A-F | 2A |

---

## Part 10: Number Methods

### toString()

Convert number to string:

```javascript
let x = 123;
let text = x.toString();
console.log(text);        // Output: "123"
console.log(typeof text); // Output: "string"
```

### toFixed()

Format number with specific decimal places:

```javascript
let x = 9.656;

console.log(x.toFixed(0));  // Output: "10"
console.log(x.toFixed(2));  // Output: "9.66"
console.log(x.toFixed(4));  // Output: "9.6560"
```

**Perfect for money:**

```javascript
let price = 19.5;
console.log(price.toFixed(2));  // Output: "19.50"
```

### toExponential()

Convert to scientific notation:

```javascript
let x = 9.656;

console.log(x.toExponential(2));  // Output: "9.66e+0"
console.log(x.toExponential(4));  // Output: "9.6560e+0"
```

### toPrecision()

Format to specific total length:

```javascript
let x = 9.656;

console.log(x.toPrecision(2));  // Output: "9.7"
console.log(x.toPrecision(4));  // Output: "9.656"
console.log(x.toPrecision(6));  // Output: "9.65600"
```

---

## Part 11: Converting to Numbers

### Three Conversion Methods

| Method | Description | Example |
|--------|-------------|---------|
| `Number()` | Converts to number | `Number("10")` → `10` |
| `parseInt()` | Converts to integer | `parseInt("10.5")` → `10` |
| `parseFloat()` | Converts to decimal | `parseFloat("10.5")` → `10.5` |

### Number() Method

```javascript
console.log(Number("10"));       // Output: 10
console.log(Number("10.33"));    // Output: 10.33
console.log(Number("  10  "));   // Output: 10 (trims spaces)
console.log(Number("10 20"));    // Output: NaN (invalid)
console.log(Number("John"));     // Output: NaN (not a number)

// Booleans
console.log(Number(true));       // Output: 1
console.log(Number(false));      // Output: 0
```

### parseInt() Method

Extracts integer from string:

```javascript
console.log(parseInt("10"));        // Output: 10
console.log(parseInt("10.33"));     // Output: 10 (removes decimal)
console.log(parseInt("10 20 30"));  // Output: 10 (first number only)
console.log(parseInt("10 years"));  // Output: 10
console.log(parseInt("years 10"));  // Output: NaN (must start with number)
```

### parseFloat() Method

Extracts decimal from string:

```javascript
console.log(parseFloat("10"));        // Output: 10
console.log(parseFloat("10.33"));     // Output: 10.33
console.log(parseFloat("10 20 30"));  // Output: 10
console.log(parseFloat("10 years"));  // Output: 10
console.log(parseFloat("years 10"));  // Output: NaN
```

---

## Part 12: Number Properties

### Important Number Constants

| Property | Description | Value |
|----------|-------------|-------|
| `Number.MAX_VALUE` | Largest possible number | 1.7976931348623157e+308 |
| `Number.MIN_VALUE` | Smallest positive number | 5e-324 |
| `Number.MAX_SAFE_INTEGER` | Largest safe integer | 9007199254740991 |
| `Number.MIN_SAFE_INTEGER` | Smallest safe integer | -9007199254740991 |
| `Number.POSITIVE_INFINITY` | Positive infinity | Infinity |
| `Number.NEGATIVE_INFINITY` | Negative infinity | -Infinity |
| `Number.NaN` | Not a Number | NaN |

### Examples

```javascript
console.log(Number.MAX_VALUE);         // Largest number
console.log(Number.MIN_VALUE);         // Smallest positive number
console.log(Number.MAX_SAFE_INTEGER);  // 9007199254740991
console.log(Number.MIN_SAFE_INTEGER);  // -9007199254740991
```

### Safe Integer Range

```
Safe Integers Range:
├─────────────────────────────────────────────────────────┤
-9007199254740991                                9007199254740991
(MIN_SAFE_INTEGER)                              (MAX_SAFE_INTEGER)
```

---

## Part 13: Number Validation Methods

### Number.isInteger()

Check if value is an integer:

```javascript
console.log(Number.isInteger(10));      // Output: true
console.log(Number.isInteger(10.5));    // Output: false
console.log(Number.isInteger("10"));    // Output: false (string)
```

### Number.isFinite()

Check if value is a finite number:

```javascript
console.log(Number.isFinite(123));      // Output: true
console.log(Number.isFinite(Infinity)); // Output: false
console.log(Number.isFinite(NaN));      // Output: false
```

### Number.isNaN()

Check if value is NaN:

```javascript
console.log(Number.isNaN(NaN));         // Output: true
console.log(Number.isNaN(123));         // Output: false
console.log(Number.isNaN("hello"));     // Output: false (not NaN, just not a number)
```

### Number.isSafeInteger()

Check if integer is within safe range:

```javascript
console.log(Number.isSafeInteger(10));                    // Output: true
console.log(Number.isSafeInteger(9007199254740991));      // Output: true
console.log(Number.isSafeInteger(9007199254740992));      // Output: false
```

---

## Part 14: Introduction to BigInt

### The Problem with Large Numbers

JavaScript numbers lose precision beyond 15 digits:

```javascript
let x = 9007199254740991;    // Safe ✅
let y = 9007199254740992;    // Unsafe ❌ (loses precision)

console.log(x);  // Output: 9007199254740991
console.log(y);  // Output: 9007199254740992 (might be inaccurate)
```

### What is BigInt?

BigInt is a special data type for handling very large integers.

**Key Points:**
- Can represent integers of ANY size
- Limited only by available memory
- Used for cryptography, large IDs, timestamps

---

## Part 15: Creating BigInt

### Two Ways to Create BigInt

**Method 1: Add `n` suffix**

```javascript
let big1 = 123456789012345678901234567890n;
console.log(big1);
```

**Method 2: Use `BigInt()` constructor**

```javascript
let big2 = BigInt("123456789012345678901234567890");
console.log(big2);
```

### BigInt Type

```javascript
let x = 123n;
console.log(typeof x);  // Output: "bigint"
```

---

## Part 16: BigInt Operations

### Arithmetic with BigInt

```javascript
let x = 9007199254740995n;
let y = 9007199254740995n;
let z = x * y;
console.log(z);  // Accurate result!
```

### Supported Operations

| Operation | Symbol | Example |
|-----------|--------|---------|
| Addition | `+` | `10n + 5n` |
| Subtraction | `-` | `10n - 5n` |
| Multiplication | `*` | `10n * 5n` |
| Division | `/` | `10n / 5n` |
| Modulus | `%` | `10n % 3n` |
| Exponentiation | `**` | `2n ** 10n` |

---

## Part 17: BigInt Limitations

### Cannot Mix BigInt and Number

```javascript
let x = 10n;
let y = 5;
let z = x + y;  // ❌ TypeError!
```

### Solution: Convert First

```javascript
let x = 10n;
let y = 5;

// Convert BigInt to Number
let z1 = Number(x) + y;
console.log(z1);  // Output: 15

// Convert Number to BigInt
let z2 = x + BigInt(y);
console.log(z2);  // Output: 15n
```

### No Decimals in BigInt

```javascript
let x = 1.5n;  // ❌ SyntaxError!
```

BigInt only works with whole numbers!

### Division Truncates

```javascript
let x = 5n / 2n;
console.log(x);  // Output: 2n (not 2.5n)
```

---

## Part 18: BigInt Comparisons

### Comparison Operators Work

```javascript
console.log(10n > 5n);      // Output: true
console.log(10n < 20n);     // Output: true
console.log(10n === 10n);   // Output: true
```

### Comparing BigInt with Number

```javascript
console.log(10n == 10);     // Output: true (loose equality)
console.log(10n === 10);    // Output: false (different types)
```

---

## Part 19: BigInt in Different Bases

### Hexadecimal, Octal, Binary

```javascript
let decimal = 256n;
let hex = 0x100n;
let octal = 0o400n;
let binary = 0b100000000n;

console.log(decimal);  // Output: 256n
console.log(hex);      // Output: 256n
console.log(octal);    // Output: 256n
console.log(binary);   // Output: 256n
```

---

## Part 20: When to Use What?

### Use Number When:

✅ Working with normal calculations
✅ Decimals are needed
✅ Numbers are within safe range (-9007199254740991 to 9007199254740991)
✅ Using Math functions

### Use BigInt When:

✅ Working with very large integers
✅ Need exact precision for large numbers
✅ Cryptography calculations
✅ Large ID numbers
✅ Timestamps in nanoseconds

---

## Part 21: Key Takeaways

### ✅ Remember These Points

1. **JavaScript has ONE number type** - 64-bit floating point
2. **Integers accurate up to 15 digits**
3. **Decimal math not always precise** (0.1 + 0.2 ≠ 0.3)
4. **+ operator** adds numbers, concatenates strings
5. **NaN** means "Not a Number" (but typeof is "number")
6. **Infinity** is a special number value
7. **Safe integer range**: -9007199254740991 to 9007199254740991
8. **BigInt** for very large integers (add `n` suffix)
9. **Cannot mix BigInt and Number** without conversion
10. **BigInt has no decimals** - integers only

### Number vs BigInt Summary

| Feature | Number | BigInt |
|---------|--------|--------|
| Max safe value | 9007199254740991 | Unlimited |
| Decimals | ✅ Yes | ❌ No |
| Math functions | ✅ Yes | ❌ No |
| Mix with other type | ✅ Auto-converts | ❌ Must convert |
| Suffix | None | `n` |

---

## What's Next?

In the next lesson, we'll learn about:

### Coming Up: JavaScript Day 13

- Arrays introduction
- Creating and accessing arrays
- Array methods (push, pop, shift, unshift)
- Looping through arrays
- Array manipulation

---

*Congratulations! You've completed JavaScript Day 12. You now understand numbers and BigInt in JavaScript!*

---

**Practice with numbers and see you in the next class!** 🚀
