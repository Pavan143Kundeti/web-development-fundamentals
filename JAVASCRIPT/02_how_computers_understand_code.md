# JavaScript Day 2: How Computers Understand Code

## Introduction

Before we dive deep into JavaScript programming, it's essential to understand how computers actually work and how they understand the code we write. This knowledge will make you a better programmer.

---

## Part 1: Understanding Computer Hardware

### Main Components of a Computer

```
Computer Hardware
├── Microprocessor (CPU) - Brain of the computer
├── Hard Disk - Storage
├── RAM - Temporary memory
└── GPU - Graphics processing
```

### The Microprocessor - The Brain

The **microprocessor** (also called CPU - Central Processing Unit) is the most important component of a computer. Everything that happens on your computer is because of this device:

- Listening to music
- Watching videos
- Typing documents
- Moving your mouse
- Running programs

**Common Microprocessors:**
- Intel: i3, i5, i7, i9
- Apple: M1, M2, M3
- AMD: Ryzen series

---

## Part 2: How Microprocessors Work

### Semiconductor Technology

Microprocessors are made using **semiconductor technology**.

### Inside a Microprocessor - Transistors

If you look at a microprocessor under a microscope, you'll see:

```
Microprocessor
    ↓
Billions of tiny devices
    ↓
Called: TRANSISTORS
```

**Types of Transistors:**
1. NPN Transistor
2. PNP Transistor

### What is a Transistor?

A transistor is a tiny device that can store **voltage** in only TWO states:

```
State 1: +5 Volts (ON)
State 2: 0 Volts (OFF)
```

### Visual Representation

```
Transistor 1: +5V (ON)
Transistor 2: 0V (OFF)
Transistor 3: +5V (ON)
Transistor 4: 0V (OFF)
Transistor 5: +5V (ON)
```

---

## Part 3: Binary - The Language of Computers

### Simplifying Voltage

To make things simple, computer scientists decided:

```
+5 Volts = 1 (ONE)
0 Volts = 0 (ZERO)
```

### What Microprocessors Understand

```
Microprocessor understands:
❌ Hindi
❌ English
❌ Kannada
❌ Tamil
❌ Telugu
❌ Marathi
❌ C, C++, Java, Python, JavaScript
✅ Only 0s and 1s (Binary)
```

### Binary = Machine Level Language

**Binary** is also called **Machine Level Language** because it's the language that machines (computers) understand.

```
Example Binary:
1 0 1 1 0 0 1 0 1 1 1 0 0 0 1 1
```

---

## Part 4: What is a Program?

### The Microprocessor is "Dumb"

Despite being powerful, the microprocessor has one big limitation:

**It cannot think on its own!**

- It will not do anything without instructions
- It needs to be told what to do
- It follows instructions exactly

### Humans Give Instructions

Only **human beings** have the power to think and give instructions to the microprocessor.

### Examples of Instructions

```
Instruction 1: Add two numbers
Instruction 2: Subtract two numbers
Instruction 3: Multiply two numbers
Instruction 4: Divide two numbers
```

### Definition of Key Terms

| Term | Definition |
|------|------------|
| **Program** | Collection of instructions for the microprocessor |
| **Programming/Coding** | Process of writing instructions (creating a program) |
| **Programmer/Coder** | Person who writes these instructions |

```
Program = Collection of Instructions
Programming = Writing Instructions
Programmer = Person who writes instructions
```

---

## Part 5: Programming Languages Evolution

### The Problem with Machine Level Language

To add two numbers and store in a variable, you need to write code in binary (0s and 1s):

```
Machine Level Code (Binary):
10110001 00000101
10110010 00000011
00000011 11000010
10001000 00010110
```

**Problems:**
- Extremely difficult to write
- Hard to read
- Easy to make mistakes
- Not human-friendly

**Result:** In the 1930s, 90% of people didn't want to become programmers because of this!

---

## Part 6: Assembly Level Language

### The Solution - Use Words!

By the end of 1930s, someone had a brilliant idea:

**"Why not use words instead of numbers?"**

### Mnemonics - Word-based Instructions

```
Operation          Word (Mnemonic)
─────────────────────────────────
Addition      →    ADD
Subtraction   →    SUB
Multiplication →   MUL
Division      →    DIV
```

### Assembly Level Language

Writing code using these words is called **Assembly Level Language**.

### Example: Addition in Assembly

```assembly
MOV AX, 5
MOV BX, 3
ADD AX, BX
MOV C, AX
```

**Much better than binary!** But still difficult.

---

## Part 7: The Translation Problem

### The Big Question

```
You write code in Assembly Level
        ↓
Give it to Microprocessor
        ↓
Will it understand?
        ↓
    NO! ❌
```

**Why?** Because microprocessor only understands **binary (0s and 1s)**!

### The Translator Analogy

```
Indian Prime Minister (speaks Hindi)
        ↓
    TRANSLATOR
        ↓
French Prime Minister (speaks French)
```

The translator knows both languages and converts between them!

### The Solution - Assembler

```
Assembly Level Code
        ↓
    ASSEMBLER (Software)
        ↓
Machine Level Code (Binary)
        ↓
Microprocessor understands!
```

### What is an Assembler?

**Assembler** is a software that:
1. Takes Assembly Level Language as input
2. Converts it line by line into Machine Level Language
3. Outputs binary code that microprocessor understands

```
Input: Assembly Code (ADD, SUB, MUL)
Process: Line by line conversion
Output: Machine Code (0s and 1s)
```

---

## Part 8: High Level Languages

### Humans Are Lazy (In a Good Way!)

Throughout history, humans have made communication easier:

```
Ancient Times: Horse messengers
        ↓
    Trained pigeons
        ↓
    Telephone (wired)
        ↓
    Cordless phone
        ↓
    Mobile phone
        ↓
Future: Brain chip (Elon Musk's Neuralink)
```

### The Same Happened with Programming

Someone said: **"Assembly is also hard! I want to write code like I write English!"**

### High Level Language

Code that looks like English with symbols:

```javascript
// High Level Language (JavaScript)
let a = 5;
let b = 3;
let c = a + b;
console.log(c);
```

**Symbols used:**
- `+` for addition
- `-` for subtraction
- `*` for multiplication
- `/` for division
- `if`, `else`, `print` - English words

### Characteristics of High Level Language

```
High Level Language:
├── Uses English-like words
├── Uses mathematical symbols
├── Easy to read
├── Easy to write
└── Human-friendly
```

---

## Part 9: Compiler - The Modern Translator

### The Same Problem Again

```
You write code in High Level Language
        ↓
Give it to Microprocessor
        ↓
Will it understand?
        ↓
    NO! ❌
```

**Why?** Microprocessor ONLY understands binary!

### The Solution - Compiler

```
High Level Code
        ↓
    COMPILER (Software)
        ↓
Machine Level Code (Binary)
        ↓
Microprocessor understands!
```

### What is a Compiler?

**Compiler** is a software that:
1. Takes High Level Language as input
2. Converts it line by line into Machine Level Language
3. Outputs binary code that microprocessor understands

```
Input: High Level Code (JavaScript, Python, Java)
Process: Line by line conversion
Output: Machine Code (0s and 1s)
```

---

## Part 10: Complete Flow Diagram

### How Your Code Runs

```
┌─────────────────────────────────────────┐
│  You Write Code in High Level Language  │
│  (JavaScript, Python, Java, C++, etc.)  │
└──────────────────┬──────────────────────┘
                   ↓
         ┌─────────────────┐
         │    COMPILER     │
         │   (Software)    │
         └────────┬────────┘
                  ↓
    ┌──────────────────────────┐
    │  Machine Level Language  │
    │      (0s and 1s)         │
    └───────────┬──────────────┘
                ↓
      ┌──────────────────┐
      │  MICROPROCESSOR  │
      │   Understands!   │
      └────────┬─────────┘
               ↓
         ┌──────────┐
         │  OUTPUT  │
         └──────────┘
```

---

## Part 11: Types of Programming Languages

### Three Levels of Languages

| Level | Language | Understood By | Difficulty | Used Today? |
|-------|----------|---------------|------------|-------------|
| **Low Level** | Machine Language (Binary) | Microprocessor | Very Hard | ❌ No |
| **Low Level** | Assembly Language | Needs Assembler | Hard | ❌ Rarely |
| **High Level** | JavaScript, Python, Java, C++ | Needs Compiler | Easy | ✅ Yes |

### Modern Programming Languages (All High Level)

```
High Level Languages:
├── JavaScript ✅
├── Python ✅
├── Java ✅
├── C ✅
├── C++ ✅
├── C# ✅
├── Ruby ✅
├── PHP ✅
├── Go ✅
└── Rust ✅
```

**All modern programming is done in High Level Languages!**

---

## Part 12: Why This Matters for JavaScript

### JavaScript is a High Level Language

```javascript
// This is JavaScript (High Level)
let firstName = "John";
let age = 25;
let isStudent = true;

console.log("Name: " + firstName);
console.log("Age: " + age);
```

**Easy to read and write!**

### Behind the Scenes

```
Your JavaScript Code
        ↓
JavaScript Engine (Compiler/Interpreter)
        ↓
Machine Code (Binary)
        ↓
Microprocessor executes
        ↓
You see output in browser
```

### JavaScript Engines (Compilers)

Remember from Day 1:

| Browser | JavaScript Engine |
|---------|-------------------|
| Chrome | V8 |
| Firefox | SpiderMonkey |
| Safari | JavaScriptCore |

These engines convert your JavaScript to machine code!

---

## Part 13: Summary Diagram

### Complete Picture

```
┌─────────────────────────────────────────────────┐
│           PROGRAMMING LANGUAGE LEVELS            │
└─────────────────────────────────────────────────┘

Level 1: MACHINE LEVEL (1930s)
┌──────────────────────────────────┐
│  10110001 00000101 10110010      │  ← Binary (0s and 1s)
│  Understood by: Microprocessor   │
│  Difficulty: Very Hard ❌        │
└──────────────────────────────────┘
                ↑
           ASSEMBLER
                ↑
Level 2: ASSEMBLY LEVEL (Late 1930s)
┌──────────────────────────────────┐
│  MOV AX, 5                       │  ← Words (Mnemonics)
│  ADD AX, BX                      │
│  Difficulty: Hard ❌             │
└──────────────────────────────────┘
                ↑
            COMPILER
                ↑
Level 3: HIGH LEVEL (Modern)
┌──────────────────────────────────┐
│  let a = 5;                      │  ← English-like
│  let b = 3;                      │
│  let c = a + b;                  │
│  Difficulty: Easy ✅             │
│  Languages: JavaScript, Python,  │
│  Java, C++, etc.                 │
└──────────────────────────────────┘
```

---

## Part 14: Key Concepts to Remember

### 1. Microprocessor

```
✅ Brain of the computer
✅ Made of billions of transistors
✅ Understands ONLY binary (0s and 1s)
✅ Cannot think on its own
✅ Needs instructions from humans
```

### 2. Transistor

```
✅ Tiny device inside microprocessor
✅ Stores voltage in two states
✅ +5V = 1 (ON)
✅ 0V = 0 (OFF)
```

### 3. Binary (Machine Level Language)

```
✅ Language of computers
✅ Only 0s and 1s
✅ Directly understood by microprocessor
✅ Very hard for humans to write
```

### 4. Program

```
✅ Collection of instructions
✅ Tells microprocessor what to do
✅ Written by programmers
```

### 5. Assembler

```
✅ Software that converts Assembly → Machine code
✅ Line by line conversion
```

### 6. Compiler

```
✅ Software that converts High Level → Machine code
✅ Line by line conversion
✅ Makes programming easy
```

### 7. High Level Language

```
✅ English-like programming language
✅ Easy to read and write
✅ JavaScript, Python, Java, C++, etc.
✅ Needs compiler to convert to machine code
```

---

## Part 15: Practical Understanding

### Example: Adding Two Numbers

#### Machine Level (Binary)
```
10110001 00000101
10110010 00000011
00000011 11000010
```
**Difficulty:** 😱😱😱 Extremely Hard

#### Assembly Level
```assembly
MOV AX, 5
MOV BX, 3
ADD AX, BX
```
**Difficulty:** 😟😟 Hard

#### High Level (JavaScript)
```javascript
let a = 5;
let b = 3;
let c = a + b;
```
**Difficulty:** 😊 Easy!

---

## Part 16: Why We Use High Level Languages

### Advantages

```
High Level Languages:
├── ✅ Easy to learn
├── ✅ Easy to read
├── ✅ Easy to write
├── ✅ Easy to debug (find errors)
├── ✅ Faster development
├── ✅ Human-friendly
└── ✅ Portable (works on different computers)
```

### The Trade-off

```
Easy for Humans ✅
        ↓
Needs Compiler/Interpreter
        ↓
Converts to Machine Code
        ↓
Microprocessor Understands ✅
```

---

## Part 17: Important Definitions

### Terms You Must Know

| Term | Definition |
|------|------------|
| **Microprocessor** | Brain of computer, executes instructions |
| **Transistor** | Tiny device that stores voltage (ON/OFF) |
| **Binary** | Number system with only 0s and 1s |
| **Machine Level Language** | Binary code (0s and 1s) |
| **Assembly Level Language** | Code using mnemonics (ADD, SUB, etc.) |
| **High Level Language** | English-like programming language |
| **Program** | Collection of instructions |
| **Programming** | Process of writing instructions |
| **Programmer** | Person who writes programs |
| **Assembler** | Converts Assembly → Machine code |
| **Compiler** | Converts High Level → Machine code |

---

## Part 18: Historical Timeline

```
1930s
├── Microprocessor invented
├── Programming in Machine Level (Binary)
└── Very difficult, few programmers

Late 1930s
├── Assembly Level Language created
├── Used mnemonics (words)
└── Still difficult

1950s-1960s
├── High Level Languages invented
├── FORTRAN, COBOL, C
└── Programming became easier

1990s
├── JavaScript invented (1995)
├── Web programming revolution
└── Programming for everyone

2020s
├── JavaScript everywhere
├── Millions of programmers
└── You are learning now! 🎉
```

---

## Part 19: Connection to JavaScript

### Why This Matters

Understanding how computers work helps you:

1. **Write better code** - Know what happens behind the scenes
2. **Debug faster** - Understand how code executes
3. **Optimize performance** - Know what's efficient
4. **Appreciate JavaScript** - Realize how easy modern programming is

### JavaScript's Journey

```
You write JavaScript code
        ↓
JavaScript Engine (V8, SpiderMonkey)
        ↓
Converts to Machine Code
        ↓
Microprocessor executes
        ↓
Browser shows result
```

---

## Part 20: Practice Questions

### Test Your Understanding

**Question 1:** What does a microprocessor understand?
- A) English
- B) JavaScript
- C) Binary (0s and 1s) ✅
- D) Assembly

**Question 2:** What is a program?
- A) A software
- B) Collection of instructions ✅
- C) A computer
- D) A website

**Question 3:** What converts High Level Language to Machine Level?
- A) Assembler
- B) Compiler ✅
- C) Microprocessor
- D) Transistor

**Question 4:** Which is easier to write?
- A) Machine Level
- B) Assembly Level
- C) High Level ✅
- D) All are same

**Question 5:** JavaScript is a:
- A) Machine Level Language
- B) Assembly Level Language
- C) High Level Language ✅
- D) None of these

---

## Part 21: Visual Summary

### The Big Picture

```
┌─────────────────────────────────────────────┐
│              YOU (PROGRAMMER)                │
│         Write JavaScript Code                │
└──────────────────┬──────────────────────────┘
                   ↓
         ┌─────────────────────┐
         │  JAVASCRIPT ENGINE  │
         │    (Compiler)       │
         └──────────┬──────────┘
                    ↓
         ┌─────────────────────┐
         │   MACHINE CODE      │
         │   (0s and 1s)       │
         └──────────┬──────────┘
                    ↓
         ┌─────────────────────┐
         │   MICROPROCESSOR    │
         │   (Executes)        │
         └──────────┬──────────┘
                    ↓
         ┌─────────────────────┐
         │      OUTPUT         │
         │  (What you see)     │
         └─────────────────────┘
```

---

## Key Takeaways

### ✅ Remember These Points

1. **Microprocessor** is the brain of the computer
2. Microprocessor understands **ONLY binary** (0s and 1s)
3. **Transistors** store voltage in two states (ON/OFF = 1/0)
4. **Program** = Collection of instructions
5. **Programming** = Writing instructions
6. **Programmer** = Person who writes programs
7. **Machine Level** = Binary (very hard)
8. **Assembly Level** = Mnemonics (hard)
9. **High Level** = English-like (easy) ✅
10. **Compiler** converts High Level → Machine Level
11. **JavaScript is a High Level Language** ✅
12. All modern programming is done in **High Level Languages**

---

## What's Next?

Now that you understand how computers work and how they understand code, in the next lesson we'll start writing actual JavaScript code!

### Coming Up: JavaScript Day 3

- Variables and Data Types
- How to store data in JavaScript
- Different types of data (numbers, text, boolean)
- Your first real JavaScript programs

---

*Congratulations! You've completed JavaScript Day 2. You now understand how computers work, what programming languages are, and why we use high-level languages like JavaScript!*

---

## Final Thought

```
You are learning JavaScript (High Level Language)
        ↓
This is the EASIEST way to program
        ↓
Be grateful you're not programming in binary! 😅
        ↓
Now let's start coding! 🚀
```

**See you in the next class!**
