# JavaScript Day 10: Loops - Introduction, for, while, and do-while

## Introduction

Loops are one of the most important concepts in programming. They allow you to repeat code multiple times without writing the same code again and again.

### Why Are Loops Important?

Loops are used everywhere in JavaScript:

1. **Array Manipulation** - Processing lists of data
2. **DOM Traversal** - Moving through webpage elements
3. **Event Handling** - Responding to user actions (clicks, typing)
4. **Animation Control** - Creating smooth animations
5. **Data Processing** - Working with large amounts of data
6. **Pattern Programming** - Creating visual patterns (interview questions)

---

## Part 1: Understanding the Need for Loops

### Problem: Printing Stars

Let's say you want to print 5 stars on the screen:

```
* * * * *
```

### Bad Approach: Copy-Paste

```javascript
console.log("*");
console.log("*");
console.log("*");
console.log("*");
console.log("*");
```

**Problems with this approach:**
- What if you need 10 stars? Copy 10 times?
- What if you need 100 stars? Copy 100 times?
- What if you need 1000 stars? Impossible!
- This is NOT how programmers work!

**Output:**
```
*
*
*
*
*
```

**Wait!** Stars are one below the other, not side by side. This is because `console.log()` automatically moves the cursor to the next line after printing.

### The Programmer's Way: Use Loops

A programmer writes code ONCE and makes the program repeat it automatically!

---

## Part 2: Types of Loops in JavaScript

JavaScript has 5 types of loops:

```
Loops in JavaScript
├── 1. for loop
├── 2. while loop
├── 3. do-while loop
├── 4. for-of loop (for arrays)
└── 5. for-in loop (for objects)
```

**Today's Focus:** for, while, and do-while loops

---

## Part 3: The for Loop

### What is a for Loop?

A **for loop** is used when you know EXACTLY how many times you want to repeat something.

### for Loop Syntax

```javascript
for (initialization; condition; increment/decrement) {
    // Body - code to repeat
}
```

### Four Components of Every Loop

Every loop has 4 essential parts:

1. **Initialization** - Where to start (happens once)
2. **Condition** - How many times to repeat (checked every time)
3. **Increment/Decrement** - How to move forward (happens after each iteration)
4. **Body** - What to repeat (the actual code)

---

## Part 4: for Loop - Step by Step

### Example: Print 5 Stars

```javascript
for (let i = 1; i <= 5; i++) {
    console.log("*");
}
```

### Breaking It Down

```
for (let i = 1; i <= 5; i++)
     ↓         ↓       ↓
  Initialize Condition Increment
```

- **let i = 1** - Start counting from 1
- **i <= 5** - Continue as long as i is less than or equal to 5
- **i++** - Increase i by 1 after each iteration

### How It Works - Visual Flow

```
Step 1: Initialize
i = 1

Step 2: Check Condition
Is 1 <= 5? Yes (true)
  ↓
Step 3: Execute Body
Print "*"
  ↓
Step 4: Increment
i becomes 2
  ↓
Step 5: Check Condition Again
Is 2 <= 5? Yes (true)
  ↓
Execute Body
Print "*"
  ↓
Increment
i becomes 3
  ↓
... continues ...
  ↓
When i = 6
Is 6 <= 5? No (false)
  ↓
STOP - Exit Loop
```

### Detailed Execution Table

| Iteration | i Value | Condition (i <= 5) | Action | Output |
|-----------|---------|-------------------|--------|--------|
| 1 | 1 | 1 <= 5 = true | Print "*" | * |
| 2 | 2 | 2 <= 5 = true | Print "*" | * |
| 3 | 3 | 3 <= 5 = true | Print "*" | * |
| 4 | 4 | 4 <= 5 = true | Print "*" | * |
| 5 | 5 | 5 <= 5 = true | Print "*" | * |
| 6 | 6 | 6 <= 5 = false | Exit loop | - |

**Final Output:**
```
*
*
*
*
*
```

---

## Part 5: for Loop Examples

### Example 1: Print 10 Stars

```javascript
for (let i = 1; i <= 10; i++) {
    console.log("*");
}
```

**Output:** 10 stars (one below the other)

### Example 2: Print Numbers 1 to 5

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
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

### Example 3: Print Even Numbers

```javascript
for (let i = 2; i <= 10; i = i + 2) {
    console.log(i);
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

### Example 4: Countdown

```javascript
for (let i = 5; i >= 1; i--) {
    console.log(i);
}
console.log("Blast off!");
```

**Output:**
```
5
4
3
2
1
Blast off!
```

---

## Part 6: Understanding i++

### What is i++?

`i++` is shorthand for "increase i by 1"

### Different Ways to Increment

```javascript
// All these do the same thing
i = i + 1;  // Long way
i += 1;     // Medium way
i++;        // Short way (most common)
```

### What is i--?

`i--` is shorthand for "decrease i by 1"

```javascript
// All these do the same thing
i = i - 1;  // Long way
i -= 1;     // Medium way
i--;        // Short way (most common)
```

---

## Part 7: The while Loop

### What is a while Loop?

A **while loop** is used when you DON'T know exactly how many times to repeat, but you know the CONDITION to stop.

### while Loop Syntax

```javascript
initialization;

while (condition) {
    // Body - code to repeat
    increment/decrement;
}
```

### Converting for Loop to while Loop

**for Loop:**
```javascript
for (let i = 1; i <= 5; i++) {
    console.log("*");
}
```

**Same thing with while Loop:**
```javascript
let i = 1;              // Initialization (outside)

while (i <= 5) {        // Condition (in parentheses)
    console.log("*");   // Body
    i++;                // Increment (inside body)
}
```

### How to Read a while Loop

Read it as: **"As long as this condition is true, keep doing this"**

```javascript
let i = 1;

while (i <= 5) {
    console.log("*");
    i++;
}
```

**Translation:** "As long as i is less than or equal to 5, print a star and increase i"

---

## Part 8: while Loop - Step by Step

### Example: Print 5 Stars

```javascript
let i = 1;

while (i <= 5) {
    console.log("*");
    i++;
}
```

### How It Works

```
Step 1: Initialize (outside loop)
i = 1

Step 2: Check Condition
Is 1 <= 5? Yes (true)
  ↓
Step 3: Execute Body
Print "*"
  ↓
Step 4: Increment
i becomes 2
  ↓
Step 5: Check Condition Again
Is 2 <= 5? Yes (true)
  ↓
Execute Body
Print "*"
  ↓
Increment
i becomes 3
  ↓
... continues ...
  ↓
When i = 6
Is 6 <= 5? No (false)
  ↓
STOP - Exit Loop
```

### Execution Table

| Check | i Value | Condition (i <= 5) | Action | Output |
|-------|---------|-------------------|--------|--------|
| 1 | 1 | 1 <= 5 = true | Print "*", i++ | * |
| 2 | 2 | 2 <= 5 = true | Print "*", i++ | * |
| 3 | 3 | 3 <= 5 = true | Print "*", i++ | * |
| 4 | 4 | 4 <= 5 = true | Print "*", i++ | * |
| 5 | 5 | 5 <= 5 = true | Print "*", i++ | * |
| 6 | 6 | 6 <= 5 = false | Exit loop | - |

**Output:** Same as for loop - 5 stars

---

## Part 9: while Loop Examples

### Example 1: Print Numbers

```javascript
let i = 1;

while (i <= 5) {
    console.log(i);
    i++;
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

### Example 2: User Input (Conceptual)

```javascript
let password = "";

while (password !== "secret") {
    // Ask user for password
    // This is just to show the concept
    console.log("Enter password");
}

console.log("Access granted");
```

**Use case:** Keep asking until correct password is entered

### Example 3: Sum of Numbers

```javascript
let i = 1;
let sum = 0;

while (i <= 5) {
    sum = sum + i;
    i++;
}

console.log("Sum: " + sum);
```

**Output:** Sum: 15 (1+2+3+4+5)

---

## Part 10: The do-while Loop

### What is a do-while Loop?

A **do-while loop** executes the body AT LEAST ONCE before checking the condition.

### do-while Loop Syntax

```javascript
initialization;

do {
    // Body - code to repeat
    increment/decrement;
} while (condition);
```

### Key Difference

- **while loop** - Check condition FIRST, then execute
- **do-while loop** - Execute FIRST, then check condition

### Converting to do-while Loop

**while Loop:**
```javascript
let i = 1;

while (i <= 5) {
    console.log("*");
    i++;
}
```

**Same thing with do-while Loop:**
```javascript
let i = 1;

do {
    console.log("*");
    i++;
} while (i <= 5);
```

---

## Part 11: do-while Loop - Step by Step

### Example: Print 5 Stars

```javascript
let i = 1;

do {
    console.log("*");
    i++;
} while (i <= 5);
```

### How It Works

```
Step 1: Initialize (outside loop)
i = 1

Step 2: DO (Execute body WITHOUT checking condition)
Print "*"
  ↓
Step 3: Increment
i becomes 2
  ↓
Step 4: NOW Check Condition (WHILE)
Is 2 <= 5? Yes (true)
  ↓
Step 5: Execute Body Again
Print "*"
  ↓
Increment
i becomes 3
  ↓
Check Condition
Is 3 <= 5? Yes (true)
  ↓
... continues ...
  ↓
When i = 6
Is 6 <= 5? No (false)
  ↓
STOP - Exit Loop
```

### Important: At Least Once Execution

```javascript
let i = 10;

do {
    console.log("This will print");
} while (i <= 5);
```

**Output:** "This will print"

**Why?** Even though 10 is NOT <= 5, the body executes ONCE before checking!

---

## Part 12: Comparing All Three Loops

### Side-by-Side Comparison

**for Loop:**
```javascript
for (let i = 1; i <= 5; i++) {
    console.log("*");
}
```

**while Loop:**
```javascript
let i = 1;
while (i <= 5) {
    console.log("*");
    i++;
}
```

**do-while Loop:**
```javascript
let i = 1;
do {
    console.log("*");
    i++;
} while (i <= 5);
```

**All three produce the same output!**

### Structure Comparison Table

| Component | for Loop | while Loop | do-while Loop |
|-----------|----------|------------|---------------|
| Initialization | Inside for() | Outside, before loop | Outside, before loop |
| Condition | Inside for() | Inside while() | Inside while() at end |
| Body | Inside { } | Inside { } | Inside { } after do |
| Increment | Inside for() | Inside body | Inside body |
| Min Executions | 0 (if condition false) | 0 (if condition false) | 1 (always at least once) |

---

## Part 13: When to Use Which Loop?

### Use for Loop When:

✅ You know EXACTLY how many times to repeat
✅ You're counting from start to end
✅ Working with arrays (later topic)

**Examples:**
- Print numbers 1 to 100
- Repeat something 10 times
- Process 50 items

### Use while Loop When:

✅ You DON'T know how many times to repeat
✅ You repeat UNTIL a condition becomes false
✅ Waiting for user input

**Examples:**
- Keep asking for password until correct
- Read file until end
- Game loop (until player loses)

### Use do-while Loop When:

✅ Body must execute AT LEAST ONCE
✅ User interaction required first
✅ Menu-driven programs

**Examples:**
- Show menu, then check if user wants to continue
- Ask question, then check if answer is correct
- ATM: Perform transaction, then ask if user wants another

---

## Part 14: Loop Components Breakdown

### Every Loop Has 4 Parts

```
┌─────────────────────────────────┐
│  1. INITIALIZATION              │
│     Where to start              │
│     (happens ONCE)              │
└─────────────────────────────────┘
           ↓
┌─────────────────────────────────┐
│  2. CONDITION                   │
│     When to stop                │
│     (checked EVERY time)        │
└─────────────────────────────────┘
           ↓
┌─────────────────────────────────┐
│  3. BODY                        │
│     What to repeat              │
│     (executes if condition true)│
└─────────────────────────────────┘
           ↓
┌─────────────────────────────────┐
│  4. INCREMENT/DECREMENT         │
│     How to move forward         │
│     (happens after body)        │
└─────────────────────────────────┘
           ↓
      (Loop back to Condition)
```

### Visual Representation

```
for (let i = 1; i <= 5; i++) {
     ↓         ↓       ↓
     1         2       4
     
    console.log("*");
         ↓
         3
}

1 = Initialization
2 = Condition
3 = Body
4 = Increment/Decrement
```

---

## Part 15: Common Loop Patterns

### Pattern 1: Count Up

```javascript
for (let i = 1; i <= 10; i++) {
    console.log(i);
}
```

**Output:** 1, 2, 3, 4, 5, 6, 7, 8, 9, 10

### Pattern 2: Count Down

```javascript
for (let i = 10; i >= 1; i--) {
    console.log(i);
}
```

**Output:** 10, 9, 8, 7, 6, 5, 4, 3, 2, 1

### Pattern 3: Skip Numbers (Step by 2)

```javascript
for (let i = 0; i <= 10; i = i + 2) {
    console.log(i);
}
```

**Output:** 0, 2, 4, 6, 8, 10

### Pattern 4: Multiplication Table

```javascript
let num = 5;

for (let i = 1; i <= 10; i++) {
    console.log(num + " x " + i + " = " + (num * i));
}
```

**Output:**
```
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
...
5 x 10 = 50
```

---

## Part 16: Real-World Examples

### Example 1: Sum of First N Numbers

```javascript
let n = 10;
let sum = 0;

for (let i = 1; i <= n; i++) {
    sum = sum + i;
}

console.log("Sum of first " + n + " numbers: " + sum);
```

**Output:** Sum of first 10 numbers: 55

### Example 2: Factorial

```javascript
let n = 5;
let factorial = 1;

for (let i = 1; i <= n; i++) {
    factorial = factorial * i;
}

console.log("Factorial of " + n + " is: " + factorial);
```

**Output:** Factorial of 5 is: 120

### Example 3: Print Pattern (Introduction)

```javascript
for (let i = 1; i <= 5; i++) {
    console.log("*");
}
```

**Output:**
```
*
*
*
*
*
```

**Note:** Pattern programming will be covered in detail in the next lessons!

---

## Part 17: Practice Exercises

### Exercise 1: Print Your Name 10 Times

```javascript
// Write a loop to print your name 10 times
```

### Exercise 2: Print Odd Numbers

```javascript
// Print all odd numbers from 1 to 20
```

### Exercise 3: Print Reverse

```javascript
// Print numbers from 20 to 1 in reverse
```

### Exercise 4: Sum of Even Numbers

```javascript
// Find sum of all even numbers from 1 to 50
```

### Exercise 5: Power Calculator

```javascript
// Calculate 2^10 (2 to the power 10) using a loop
```

---

## Part 18: Common Mistakes

### Mistake 1: Infinite Loop (Forgetting Increment)

```javascript
// Wrong ❌
let i = 1;
while (i <= 5) {
    console.log("*");
    // Forgot i++
}
// This will run FOREVER!

// Correct ✅
let i = 1;
while (i <= 5) {
    console.log("*");
    i++;  // Don't forget this!
}
```

### Mistake 2: Wrong Condition

```javascript
// Wrong ❌
for (let i = 1; i < 5; i++) {  // Will print 4 times, not 5
    console.log("*");
}

// Correct ✅
for (let i = 1; i <= 5; i++) {  // Will print 5 times
    console.log("*");
}
```

### Mistake 3: Starting from Wrong Number

```javascript
// If you want 5 iterations starting from 1
for (let i = 1; i <= 5; i++) {  // ✅ Correct

// Not this
for (let i = 0; i <= 5; i++) {  // ❌ This gives 6 iterations
```

---

## Part 19: Key Takeaways

### ✅ Remember These Points

1. **Loops** repeat code automatically - no copy-paste needed
2. **for loop** - Use when you know exact number of iterations
3. **while loop** - Use when you don't know exact number
4. **do-while loop** - Use when body must execute at least once
5. **Every loop has 4 parts**: initialization, condition, body, increment/decrement
6. **i++** means increase by 1, **i--** means decrease by 1
7. **Infinite loops** happen when you forget to increment/decrement
8. **console.log()** automatically moves cursor to next line
9. All three loops can produce the same output
10. Practice is the ONLY way to master loops!

### Syntax Summary

```javascript
// for Loop
for (initialization; condition; increment) {
    // body
}

// while Loop
initialization;
while (condition) {
    // body
    increment;
}

// do-while Loop
initialization;
do {
    // body
    increment;
} while (condition);
```

---

## What's Next?

In the next lessons, we'll learn:

### Coming Up: JavaScript Day 11

- Nested loops
- Pattern programming
- Creating stars, triangles, pyramids
- Interview pattern questions
- Advanced loop techniques

---

## Important Note

**To become a programmer, you MUST practice!**

- Watching videos alone won't make you a programmer
- You need to write at least 200-250 programs
- Practice changes the wiring in your brain
- Loops are the foundation - master them!

---

*Congratulations! You've completed JavaScript Day 10. You now understand the fundamentals of loops in JavaScript!*

---

**Get your hands dirty with code and see you in the next class!** 🚀
