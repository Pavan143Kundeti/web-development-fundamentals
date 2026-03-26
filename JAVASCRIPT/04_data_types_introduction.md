# JavaScript Day 4: Understanding Data Types

## Introduction

Before we start writing JavaScript code, we need to understand a fundamental concept: **What is a Data Type?**

You've probably heard words like:
- Number
- String
- Boolean
- Object

These are all examples of data types, but what exactly IS a data type? Let's find out!

---

## Part 1: Understanding Computer Memory (RAM)

### Main Hardware Components

Your computer has three main components:

```
Computer Hardware:
├── Hard Disk (Storage)
├── RAM (Memory)
└── Processor (CPU - Brain)
```

### How They Connect

```
Hard Disk ←→ RAM ←→ Processor
```

**Important:** The processor executes programs, and all executing programs store their data in **RAM**.

---

## Part 2: What is RAM?

### RAM Specifications

You've heard terms like:
- 2 GB RAM
- 4 GB RAM
- 8 GB RAM
- 16 GB RAM

### What Does GB Mean?

```
GB = Gigabytes
G = Giga = 10^9 (1 followed by 9 zeros)
B = Bytes

2 GB = 2 × 10^9 bytes
     = 2,000,000,000 bytes
     = 200 crore bytes
```

### RAM is a Collection of Bytes

```
RAM (2 GB)
┌─────────────────────────────────┐
│ Byte 1 │ Byte 2 │ ... │ Byte 200 crore │
└─────────────────────────────────┘
```

**Key Point:** RAM is a collection of bytes!

---

## Part 3: What is a Byte?

### Inside a Byte

A **byte** is made of 8 smaller parts called **bits**.

```
1 Byte = 8 Bits

Byte:
┌───┬───┬───┬───┬───┬───┬───┬───┐
│ 1 │ 0 │ 1 │ 1 │ 0 │ 0 │ 1 │ 0 │
└───┴───┴───┴───┴───┴───┴───┴───┘
  Bit Bit Bit Bit Bit Bit Bit Bit
```

### Calculating Total Bits

```
2 GB RAM = 200 crore bytes
1 Byte = 8 bits

Total bits = 8 × 200 crore
           = 1,600 crore bits
```

---

## Part 4: What is a Bit?

### Inside a Bit - Transistors

A **bit** is made of 2 transistors:
1. NPN Transistor
2. PNP Transistor

### What Transistors Store

Transistors can store **voltage** in only TWO states:

```
State 1: High Voltage (+5V) = 1
State 2: Low Voltage (0V)   = 0
```

### The Complete Picture

```
RAM
 ↓
Collection of Bytes
 ↓
Collection of Bits
 ↓
Collection of Transistors
 ↓
Can store only: 0s and 1s (Binary)
```

**Conclusion:** RAM can ONLY store binary (0s and 1s)!

---

## Part 5: Real World Data

### Types of Data in the Real World

Let's imagine we meet a person and ask them questions:

| Question | Answer | Data Type |
|----------|--------|-----------|
| What is your age? | 23 | Integer |
| What is your height? | 5.11 feet | Real Number (Decimal) |
| What is your name? | Rajkumar | Characters/Text |
| Are you placed? | Yes | Boolean (Yes/No) |
| What are you listening to? | Song | Audio |
| What are you watching? | Movie | Video |
| Take a selfie | Photo | Image |

### Seven Categories of Data

```
Real World Data:
├── 1. Integer (whole numbers)
├── 2. Real Numbers (decimals)
├── 3. Characters/Text
├── 4. Boolean (Yes/No, True/False)
├── 5. Audio
├── 6. Video
└── 7. Images
```

**99.9% of world's data falls into these categories!**

---

## Part 6: The Problem - Data Mismatch

### The Mismatch

```
Real World Data:
├── Age: 23 (not binary)
├── Height: 5.11 (not binary)
├── Name: "Rajkumar" (not binary)
└── Placed: Yes (not binary)

RAM can store:
└── Only 0s and 1s (binary)
```

### The Question

**How do we store real-world data (which is NOT binary) into RAM (which ONLY understands binary)?**

---

## Part 7: The Solution - Data Types!

### What is a Data Type?

**Data Type** = A converter that transforms real-world data into binary (0s and 1s) so it can be stored in RAM.

```
Real World Data
        ↓
   DATA TYPE (Converter)
        ↓
   Binary (0s and 1s)
        ↓
   Stored in RAM
```

### Why We Need Data Types

```
Without Data Types:
Real World Data → RAM ❌ (Cannot store directly)

With Data Types:
Real World Data → Data Type → Binary → RAM ✅
```

---

## Part 8: JavaScript Data Types

### Primitive Data Types (7 types)

JavaScript has **7 primitive data types**:

```
JavaScript Data Types:
├── 1. Number (integers and decimals)
├── 2. String (text/characters)
├── 3. Boolean (true/false)
├── 4. Undefined
├── 5. Null
├── 6. Symbol (ES6)
└── 7. BigInt (ES2020)
```

### Non-Primitive Data Types

```
Non-Primitive:
├── Object
├── Array
└── Function
```

---

## Part 9: Number Data Type

### What is Number?

In JavaScript, **Number** handles BOTH integers and decimals (unlike Java which has separate types).

### Examples

```javascript
// Integers
let age = 23;
let students = 50;
let population = 1400000000;

// Decimals (Real Numbers)
let height = 5.11;
let weight = 65.5;
let cgpa = 8.6;
let price = 99.99;

// All are "Number" type in JavaScript!
```

### How It Works

```
Real World: 23
        ↓
Number Data Type converts to binary
        ↓
Binary: 00010111
        ↓
Stored in RAM
```

---

## Part 10: String Data Type

### What is String?

**String** stores text, characters, words, sentences.

### Examples

```javascript
// Names
let firstName = "Rajkumar";
let lastName = "Sharma";

// Sentences
let message = "Hello, World!";
let address = "123 Main Street, Bangalore";

// Single character
let grade = "A";

// Empty string
let empty = "";
```

### String Syntax

```javascript
// Three ways to create strings:
let name1 = "John";      // Double quotes
let name2 = 'Jane';      // Single quotes
let name3 = `Jack`;      // Backticks (template literals)
```

### How It Works

```
Real World: "Rajkumar"
        ↓
String Data Type converts each character to binary
        ↓
Binary: 01010010 01100001 01101010... (for each letter)
        ↓
Stored in RAM
```

---

## Part 11: Boolean Data Type

### What is Boolean?

**Boolean** stores only TWO values: `true` or `false`

### Examples

```javascript
// Yes/No questions
let isPlaced = true;
let isRaining = false;

// Comparisons
let isAdult = age >= 18;
let isPassed = marks >= 40;

// Status
let isLoggedIn = true;
let hasPermission = false;
```

### How It Works

```
Real World: Yes/No
        ↓
Boolean Data Type
        ↓
true = 1 (binary)
false = 0 (binary)
        ↓
Stored in RAM
```

---

## Part 12: Undefined Data Type

### What is Undefined?

**Undefined** means a variable has been declared but not assigned a value.

### Examples

```javascript
let name;
console.log(name);  // Output: undefined

let age;
console.log(age);   // Output: undefined
```

### When It Occurs

```javascript
// Variable declared but not initialized
let x;
console.log(x);  // undefined

// After initialization
x = 10;
console.log(x);  // 10
```

---

## Part 13: Null Data Type

### What is Null?

**Null** means intentionally empty or no value.

### Undefined vs Null

```javascript
// Undefined - not assigned yet
let a;
console.log(a);  // undefined

// Null - intentionally empty
let b = null;
console.log(b);  // null
```

### Use Cases

```javascript
// Resetting a variable
let user = "John";
user = null;  // User logged out

// Initial empty state
let selectedItem = null;
```

---

## Part 14: Symbol Data Type (Advanced)

### What is Symbol?

**Symbol** creates unique identifiers (ES6 feature).

### Example

```javascript
let id1 = Symbol("id");
let id2 = Symbol("id");

console.log(id1 === id2);  // false (always unique)
```

**Note:** Symbols are advanced and rarely used by beginners.

---

## Part 15: BigInt Data Type (Advanced)

### What is BigInt?

**BigInt** stores very large integers that exceed Number's limit.

### Example

```javascript
// Regular number limit
let bigNumber = 9007199254740991;  // Max safe integer

// BigInt for larger numbers
let veryBig = 9007199254740991n;  // Note the 'n' at end
let huge = BigInt("123456789012345678901234567890");
```

**Note:** BigInt is for special cases with very large numbers.

---

## Part 16: Checking Data Types

### Using typeof Operator

```javascript
// Number
console.log(typeof 23);           // "number"
console.log(typeof 5.11);         // "number"

// String
console.log(typeof "Hello");      // "string"
console.log(typeof 'World');      // "string"

// Boolean
console.log(typeof true);         // "boolean"
console.log(typeof false);        // "boolean"

// Undefined
let x;
console.log(typeof x);            // "undefined"

// Null (special case - bug in JavaScript!)
console.log(typeof null);         // "object" (this is a bug!)

// Symbol
console.log(typeof Symbol("id")); // "symbol"

// BigInt
console.log(typeof 123n);         // "bigint"
```

---

## Part 17: Practical Examples

### Example 1: Student Information

```javascript
// Student data using different types
let studentName = "Rajkumar";        // String
let age = 23;                        // Number
let height = 5.11;                   // Number
let cgpa = 8.6;                      // Number
let isPlaced = true;                 // Boolean
let company = null;                  // Null (not placed yet)
```

### Example 2: E-commerce Product

```javascript
let productName = "Laptop";          // String
let price = 45999.99;                // Number
let inStock = true;                  // Boolean
let rating = 4.5;                    // Number
let reviews = 1250;                  // Number
let discount = null;                 // Null (no discount)
```

### Example 3: User Profile

```javascript
let username = "john_doe";           // String
let email = "john@example.com";      // String
let age = 25;                        // Number
let isVerified = false;              // Boolean
let profilePicture = null;           // Null (no picture uploaded)
let bio;                             // Undefined (not set yet)
```

---

## Part 18: Data Type Conversion

### Automatic Conversion (Type Coercion)

```javascript
// Number + String = String
console.log(5 + "5");        // "55" (string)

// String - Number = Number
console.log("10" - 5);       // 5 (number)

// Boolean to Number
console.log(true + 1);       // 2 (true = 1)
console.log(false + 1);      // 1 (false = 0)
```

### Manual Conversion

```javascript
// String to Number
let str = "123";
let num = Number(str);
console.log(num);            // 123 (number)

// Number to String
let age = 25;
let ageStr = String(age);
console.log(ageStr);         // "25" (string)

// To Boolean
console.log(Boolean(1));     // true
console.log(Boolean(0));     // false
console.log(Boolean(""));    // false
console.log(Boolean("Hi"));  // true
```

---

## Part 19: Special Data - Audio, Video, Images

### How JavaScript Handles Media

JavaScript doesn't have built-in data types for:
- Audio
- Video
- Images

Instead, we use **libraries** and **APIs**:

```javascript
// Images - using DOM
let img = document.createElement('img');
img.src = 'photo.jpg';

// Audio - using HTML5 Audio API
let audio = new Audio('song.mp3');
audio.play();

// Video - using HTML5 Video API
let video = document.createElement('video');
video.src = 'movie.mp4';
```

**Libraries** = Using code written by other programmers

---

## Part 20: Summary Diagram

### Complete Picture

```
┌─────────────────────────────────────────┐
│         REAL WORLD DATA                  │
├─────────────────────────────────────────┤
│ Age: 23                                  │
│ Name: "Rajkumar"                         │
│ Height: 5.11                             │
│ Placed: true                             │
└──────────────┬──────────────────────────┘
               ↓
┌─────────────────────────────────────────┐
│         DATA TYPES (Converters)          │
├─────────────────────────────────────────┤
│ Number → converts 23 to binary           │
│ String → converts "Rajkumar" to binary   │
│ Number → converts 5.11 to binary         │
│ Boolean → converts true to binary        │
└──────────────┬──────────────────────────┘
               ↓
┌─────────────────────────────────────────┐
│         BINARY (0s and 1s)               │
├─────────────────────────────────────────┤
│ 00010111 (23 in binary)                  │
│ 01010010... (Rajkumar in binary)         │
│ 01000001... (5.11 in binary)             │
│ 00000001 (true in binary)                │
└──────────────┬──────────────────────────┘
               ↓
┌─────────────────────────────────────────┐
│              RAM                         │
├─────────────────────────────────────────┤
│ Stores all data as 0s and 1s             │
└─────────────────────────────────────────┘
```

---

## Part 21: Key Concepts

### What is a Data Type?

**Data Type** = A converter that transforms real-world data into binary so it can be stored in RAM.

### Why Do We Need Data Types?

```
Problem: RAM can only store binary (0s and 1s)
Real World: Data is NOT in binary
Solution: Data Types convert real-world data to binary
```

### JavaScript's 7 Primitive Data Types

```
1. Number    - integers and decimals
2. String    - text and characters
3. Boolean   - true or false
4. Undefined - not assigned
5. Null      - intentionally empty
6. Symbol    - unique identifiers
7. BigInt    - very large integers
```

---

## Part 22: Important Definitions

| Term | Definition |
|------|------------|
| **RAM** | Memory where executing programs store data |
| **Byte** | Collection of 8 bits |
| **Bit** | Smallest unit, stores 0 or 1 |
| **Binary** | Number system with only 0s and 1s |
| **Data Type** | Converter from real-world data to binary |
| **Number** | Stores integers and decimals |
| **String** | Stores text and characters |
| **Boolean** | Stores true or false |
| **Undefined** | Variable declared but not assigned |
| **Null** | Intentionally empty value |

---

## Part 23: Practice Exercises

### Exercise 1: Identify Data Types

What data type would you use for:
```javascript
// Your answers:
let studentAge = ?;           // Number
let studentName = ?;          // String
let isPassed = ?;             // Boolean
let grade = ?;                // String or Number
let phoneNumber = ?;          // String (can have +, -)
```

### Exercise 2: Check Types

```javascript
console.log(typeof 42);
console.log(typeof "Hello");
console.log(typeof true);
console.log(typeof undefined);
console.log(typeof null);
```

### Exercise 3: Create Variables

Create variables for a person:
```javascript
let name = "Your Name";
let age = 25;
let height = 5.8;
let isStudent = true;
let company = null;
let hobby;  // undefined
```

---

## Key Takeaways

### ✅ Remember These Points

1. **RAM** stores data as binary (0s and 1s)
2. **Real-world data** is NOT in binary
3. **Data Types** convert real-world data to binary
4. JavaScript has **7 primitive data types**
5. **Number** handles both integers and decimals
6. **String** stores text (use quotes)
7. **Boolean** stores true or false
8. **Undefined** = not assigned yet
9. **Null** = intentionally empty
10. Use **typeof** to check data type

---

## What's Next?

Now that you understand data types, in the next lesson we'll learn about:

### Coming Up: JavaScript Day 5

- Variables - How to store data
- Declaring variables (let, const, var)
- Naming rules
- Working with different data types
- Your first real programs!

---

*Congratulations! You've completed JavaScript Day 4. You now understand what data types are, why we need them, and the different types available in JavaScript!*

---

**See you in the next class!** 🚀
