# JavaScript Day 11: Strings - Complete Guide

## Introduction

Strings are one of the most commonly used data types in JavaScript. A string is simply text - any sequence of characters like letters, numbers, symbols, or spaces.

**Examples of strings:**
- "Hello World"
- "JavaScript"
- "My age is 25"
- "user@email.com"

---

## Part 1: Creating Strings

### Three Ways to Create Strings

JavaScript allows you to create strings using three different quote types:

| Method | Syntax | Example |
|--------|--------|---------|
| Double Quotes | `"text"` | `"Hello World"` |
| Single Quotes | `'text'` | `'Hello World'` |
| Backticks (Template Literals) | `` `text` `` | `` `Hello World` `` |

### Example: All Three Methods

```javascript
let name1 = "John Doe";        // Double quotes
let name2 = 'John Doe';        // Single quotes
let name3 = `John Doe`;        // Backticks (template literal)

console.log(name1);  // Output: John Doe
console.log(name2);  // Output: John Doe
console.log(name3);  // Output: John Doe
```

**Important:** Single and double quotes work exactly the same. There is no difference between them.

---

## Part 2: Quotes Inside Strings

### The Problem

What if you need quotes inside your string?

```javascript
// This will cause an ERROR ❌
let text = "He said "Hello"";
```

**Why error?** JavaScript thinks the string ends at the second quote!

### Solution 1: Mix Quote Types

Use single quotes inside double quotes, or vice versa:

```javascript
let text1 = "It's alright";              // Single quote inside double
let text2 = "He is called 'Johnny'";     // Single quotes inside double
let text3 = 'He is called "Johnny"';     // Double quotes inside single
```

### Solution 2: Escape Characters

Use backslash `\` before the quote:

```javascript
let text1 = "He said \"Hello\"";         // \" = double quote
let text2 = 'It\'s alright';             // \' = single quote
```

### Solution 3: Template Literals (Best)

Use backticks - they allow both quote types:

```javascript
let text = `He's often called "Johnny"`;  // Both quotes work!
```

---

## Part 3: Escape Characters

### What Are Escape Characters?

The backslash `\` turns special characters into string characters.

### Common Escape Sequences

| Code | Result | Description |
|------|--------|-------------|
| `\'` | ' | Single quote |
| `\"` | " | Double quote |
| `\\` | \ | Backslash |
| `\n` | New line | Move to next line |
| `\t` | Tab | Horizontal tab space |

### Examples

```javascript
// Double quote inside string
let text1 = "We are the so-called \"Vikings\" from the north.";
console.log(text1);
// Output: We are the so-called "Vikings" from the north.

// Single quote inside string
let text2 = 'It\'s alright.';
console.log(text2);
// Output: It's alright.

// Backslash in string
let text3 = "The character \\ is called backslash.";
console.log(text3);
// Output: The character \ is called backslash.

// New line
let text4 = "Hello\nWorld";
console.log(text4);
// Output:
// Hello
// World

// Tab space
let text5 = "Name:\tJohn";
console.log(text5);
// Output: Name:    John
```

---

## Part 4: String Length

### The length Property

Every string has a `length` property that tells you how many characters it contains.

### Syntax

```javascript
string.length
```

### Examples

```javascript
let text1 = "Hello";
console.log(text1.length);  // Output: 5

let text2 = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
console.log(text2.length);  // Output: 26

let text3 = "Hello World";
console.log(text3.length);  // Output: 11 (space counts!)

let text4 = "";
console.log(text4.length);  // Output: 0 (empty string)
```

**Important:** Spaces, numbers, and special characters all count as characters!

---

## Part 5: Template Literals (Backticks)

### What Are Template Literals?

Template literals are strings created with backticks (`` ` ``). They have special powers that regular strings don't have!

### Power 1: Multiline Strings

```javascript
// Regular strings - ERROR ❌
let text1 = "The quick
brown fox";

// Template literals - Works! ✅
let text2 = `The quick
brown fox
jumps over
the lazy dog`;

console.log(text2);
```

### Power 2: Variable Interpolation

Insert variables directly into strings using `${variable}`:

```javascript
let firstName = "John";
let lastName = "Doe";

// Old way (concatenation)
let greeting1 = "Welcome " + firstName + " " + lastName + "!";

// New way (template literal)
let greeting2 = `Welcome ${firstName} ${lastName}!`;

console.log(greeting2);  // Output: Welcome John Doe!
```

### Power 3: Expression Interpolation

You can put calculations inside `${}`:

```javascript
let price = 100;
let quantity = 3;

let message = `Total cost: $${price * quantity}`;
console.log(message);  // Output: Total cost: $300

let a = 5;
let b = 10;
let result = `${a} + ${b} = ${a + b}`;
console.log(result);  // Output: 5 + 10 = 15
```

---

## Part 6: String Methods - Extracting Parts

### Method Comparison Table

| Method | Syntax | Negative Index | Description |
|--------|--------|----------------|-------------|
| `slice()` | `slice(start, end)` | ✅ Yes | Extracts part of string |
| `substring()` | `substring(start, end)` | ❌ No (treats as 0) | Similar to slice |
| `substr()` | `substr(start, length)` | ✅ Yes | ⚠️ Deprecated - don't use |

### slice() Method

Extracts a part of a string and returns it.

```javascript
let text = "Apple, Banana, Kiwi";

// Extract from position 7 to 13
let part1 = text.slice(7, 13);
console.log(part1);  // Output: Banana

// Extract from position 7 to end
let part2 = text.slice(7);
console.log(part2);  // Output: Banana, Kiwi

// Negative index (from end)
let part3 = text.slice(-4);
console.log(part3);  // Output: Kiwi

// Negative start and end
let part4 = text.slice(-12, -6);
console.log(part4);  // Output: Banana
```

### Visual: How slice() Works

```
String: "Apple, Banana, Kiwi"
Index:   0123456789...

slice(7, 13):
         ↓start    ↓end
"Apple, Banana, Kiwi"
        ^^^^^^
        Result: "Banana"
```

### substring() Method

Similar to slice, but doesn't support negative indexes:

```javascript
let text = "Apple, Banana, Kiwi";

let part1 = text.substring(7, 13);
console.log(part1);  // Output: Banana

let part2 = text.substring(7);
console.log(part2);  // Output: Banana, Kiwi
```

---

## Part 7: String Methods - Case Conversion

### toUpperCase() and toLowerCase()

| Method | Description | Example |
|--------|-------------|---------|
| `toUpperCase()` | Converts to UPPERCASE | "hello" → "HELLO" |
| `toLowerCase()` | Converts to lowercase | "HELLO" → "hello" |

### Examples

```javascript
let text = "Hello World";

let upper = text.toUpperCase();
console.log(upper);  // Output: HELLO WORLD

let lower = text.toLowerCase();
console.log(lower);  // Output: hello world

// Original string unchanged
console.log(text);   // Output: Hello World
```

**Important:** String methods don't change the original string. They return a NEW string!

---

## Part 8: String Methods - Trimming Whitespace

### Trim Methods

| Method | Description | Example |
|--------|-------------|---------|
| `trim()` | Remove spaces from both sides | `"  hi  "` → `"hi"` |
| `trimStart()` | Remove spaces from start only | `"  hi  "` → `"hi  "` |
| `trimEnd()` | Remove spaces from end only | `"  hi  "` → `"  hi"` |

### Examples

```javascript
let text = "     Hello World!     ";

console.log(text.trim());       // Output: "Hello World!"
console.log(text.trimStart());  // Output: "Hello World!     "
console.log(text.trimEnd());    // Output: "     Hello World!"
```

### Use Case: User Input

```javascript
let username = "  john123  ";
let cleanUsername = username.trim();
console.log(cleanUsername);  // Output: "john123"
```

---

## Part 9: String Methods - Replacing Content

### replace() Method

Replaces the FIRST occurrence of a value:

```javascript
let text = "Please visit Microsoft!";
let newText = text.replace("Microsoft", "Google");
console.log(newText);  // Output: Please visit Google!

// Only replaces FIRST match
let text2 = "Microsoft and Microsoft";
let newText2 = text2.replace("Microsoft", "Google");
console.log(newText2);  // Output: Google and Microsoft
```

### replaceAll() Method

Replaces ALL occurrences:

```javascript
let text = "I love cats. Cats are amazing. Cats are cute.";
let newText = text.replaceAll("Cats", "Dogs");
console.log(newText);
// Output: I love cats. Dogs are amazing. Dogs are cute.

// Case sensitive!
let newText2 = text.replaceAll("cats", "dogs");
console.log(newText2);
// Output: I love dogs. Cats are amazing. Cats are cute.
```

---

## Part 10: String Methods - Searching

### indexOf() Method

Finds the FIRST occurrence and returns its position:

```javascript
let text = "Please locate where 'locate' occurs!";

let position = text.indexOf("locate");
console.log(position);  // Output: 7

// Not found returns -1
let position2 = text.indexOf("xyz");
console.log(position2);  // Output: -1
```

### lastIndexOf() Method

Finds the LAST occurrence:

```javascript
let text = "Please locate where 'locate' occurs!";

let position = text.lastIndexOf("locate");
console.log(position);  // Output: 21
```

### includes() Method

Checks if string contains a value (returns true/false):

```javascript
let text = "Hello world, welcome to the universe.";

console.log(text.includes("world"));     // Output: true
console.log(text.includes("goodbye"));   // Output: false
```

### startsWith() and endsWith()

```javascript
let text = "Hello world";

console.log(text.startsWith("Hello"));   // Output: true
console.log(text.startsWith("world"));   // Output: false

console.log(text.endsWith("world"));     // Output: true
console.log(text.endsWith("Hello"));     // Output: false
```

---

## Part 11: String Methods - Character Access

### Four Ways to Access Characters

| Method | Syntax | Returns if Not Found |
|--------|--------|---------------------|
| `charAt()` | `string.charAt(index)` | Empty string `""` |
| `charCodeAt()` | `string.charCodeAt(index)` | Unicode code |
| `at()` | `string.at(index)` | undefined |
| `[]` | `string[index]` | undefined |

### Examples

```javascript
let text = "HELLO";

// charAt()
console.log(text.charAt(0));      // Output: H
console.log(text.charAt(4));      // Output: O

// at() - supports negative index
console.log(text.at(0));          // Output: H
console.log(text.at(-1));         // Output: O (last character)

// Property access []
console.log(text[0]);             // Output: H
console.log(text[4]);             // Output: O

// charCodeAt() - returns Unicode
console.log(text.charCodeAt(0));  // Output: 72 (Unicode for 'H')
```

---

## Part 12: String Methods - Splitting

### split() Method

Converts a string into an array:

```javascript
let text = "Apple,Banana,Kiwi";

// Split by comma
let fruits = text.split(",");
console.log(fruits);  // Output: ["Apple", "Banana", "Kiwi"]

// Split by space
let sentence = "Hello World JavaScript";
let words = sentence.split(" ");
console.log(words);  // Output: ["Hello", "World", "JavaScript"]

// Split into characters
let word = "Hello";
let letters = word.split("");
console.log(letters);  // Output: ["H", "e", "l", "l", "o"]
```

---

## Part 13: String Methods - Other Useful Methods

### concat() Method

Joins strings together:

```javascript
let text1 = "Hello";
let text2 = "World";
let text3 = text1.concat(" ", text2);
console.log(text3);  // Output: Hello World

// Same as using +
let text4 = text1 + " " + text2;
console.log(text4);  // Output: Hello World
```

### repeat() Method

Repeats a string multiple times:

```javascript
let text = "Hello! ";
let repeated = text.repeat(3);
console.log(repeated);  // Output: Hello! Hello! Hello! 
```

### padStart() and padEnd()

Adds padding to reach a certain length:

```javascript
let text = "5";

// Pad with zeros at start
let padded1 = text.padStart(4, "0");
console.log(padded1);  // Output: 0005

// Pad with x at end
let padded2 = text.padEnd(4, "x");
console.log(padded2);  // Output: 5xxx
```

---

## Part 14: String Methods Summary Table

### Essential String Methods

| Method | Purpose | Example | Result |
|--------|---------|---------|--------|
| `length` | Get string length | `"Hello".length` | `5` |
| `toUpperCase()` | Convert to uppercase | `"hello".toUpperCase()` | `"HELLO"` |
| `toLowerCase()` | Convert to lowercase | `"HELLO".toLowerCase()` | `"hello"` |
| `trim()` | Remove whitespace | `"  hi  ".trim()` | `"hi"` |
| `slice(start, end)` | Extract part | `"Hello".slice(0, 2)` | `"He"` |
| `replace(old, new)` | Replace first match | `"hi hi".replace("hi", "bye")` | `"bye hi"` |
| `replaceAll(old, new)` | Replace all matches | `"hi hi".replaceAll("hi", "bye")` | `"bye bye"` |
| `split(separator)` | Convert to array | `"a,b,c".split(",")` | `["a","b","c"]` |
| `indexOf(text)` | Find position | `"Hello".indexOf("e")` | `1` |
| `includes(text)` | Check if contains | `"Hello".includes("ell")` | `true` |
| `startsWith(text)` | Check start | `"Hello".startsWith("He")` | `true` |
| `endsWith(text)` | Check end | `"Hello".endsWith("lo")` | `true` |
| `charAt(index)` | Get character | `"Hello".charAt(0)` | `"H"` |
| `repeat(count)` | Repeat string | `"Hi".repeat(3)` | `"HiHiHi"` |

---

## Part 15: Important String Concepts

### Strings Are Immutable

Strings CANNOT be changed. Methods return NEW strings:

```javascript
let text = "Hello";
text.toUpperCase();
console.log(text);  // Output: Hello (unchanged!)

// You must save the result
let newText = text.toUpperCase();
console.log(newText);  // Output: HELLO
```

### Strings vs String Objects

```javascript
// Primitive string (normal way) ✅
let x = "John";

// String object (don't use) ❌
let y = new String("John");

console.log(typeof x);  // Output: string
console.log(typeof y);  // Output: object

// Comparison issues
console.log(x == y);    // Output: true (value same)
console.log(x === y);   // Output: false (type different)
```

**Important:** Always use primitive strings, NOT String objects!

---

## Part 16: Practical Examples

### Example 1: Email Validation Check

```javascript
let email = "user@example.com";

if (email.includes("@") && email.includes(".")) {
    console.log("Valid email format");
} else {
    console.log("Invalid email format");
}
```

### Example 2: Username Cleanup

```javascript
let username = "  JohnDoe123  ";
let cleanUsername = username.trim().toLowerCase();
console.log(cleanUsername);  // Output: johndoe123
```

### Example 3: Extract File Extension

```javascript
let filename = "document.pdf";
let extension = filename.slice(-3);
console.log(extension);  // Output: pdf
```

### Example 4: Count Words

```javascript
let sentence = "JavaScript is awesome";
let words = sentence.split(" ");
let wordCount = words.length;
console.log("Word count: " + wordCount);  // Output: Word count: 3
```

### Example 5: Create Initials

```javascript
let firstName = "John";
let lastName = "Doe";
let initials = firstName.charAt(0) + lastName.charAt(0);
console.log(initials);  // Output: JD
```

---

## Part 17: Key Takeaways

### ✅ Remember These Points

1. **Three ways to create strings**: double quotes, single quotes, backticks
2. **Template literals** (backticks) allow variables with `${}`
3. **Escape character** `\` for special characters
4. **Strings are immutable** - methods return new strings
5. **length property** gives number of characters
6. **slice()** extracts parts of strings
7. **toUpperCase()** and **toLowerCase()** change case
8. **trim()** removes whitespace
9. **replace()** and **replaceAll()** change content
10. **split()** converts string to array
11. **includes()**, **startsWith()**, **endsWith()** for searching
12. **indexOf()** finds position of text

---

## What's Next?

In the next lesson, we'll learn about:

### Coming Up: JavaScript Day 12

- Arrays introduction
- Creating and accessing arrays
- Array methods
- Looping through arrays
- Multi-dimensional arrays

---

*Congratulations! You've completed JavaScript Day 11. You now have a solid understanding of strings in JavaScript!*

---

**Practice string methods and see you in the next class!** 🚀
