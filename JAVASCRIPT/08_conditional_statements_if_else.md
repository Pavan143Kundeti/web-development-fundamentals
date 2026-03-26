# JavaScript Day 8: Conditional Statements (if, if-else, if-else-if)

## Introduction

So far, we've been writing programs that execute **sequentially** - one instruction after another, from top to bottom. But to create complex logic and real-world applications, we need to control the **flow of execution** based on conditions.

---

## Part 1: Understanding Program Flow

### Sequential Execution (What We've Done So Far)

```
Instruction 1
    ↓
Instruction 2
    ↓
Instruction 3
    ↓
Instruction 4
    ↓
Instruction 5
```

**Problem:** Every instruction executes, no matter what!

### Conditional Execution (What We Need)

```
Instruction 1
Instruction 2
Instruction 3
    ↓
  Condition?
    ↙    ↘
  True    False
    ↓      ↓
 Path A  Path B
    ↓      ↓
Instruction 4
Instruction 5
```

**Solution:** Execute different instructions based on conditions!

---

## Part 2: Control Structures

### What are Control Structures?

**Control Structures** = Mechanisms that control the flow of program execution.

### Two Main Types

```
Control Structures
├── 1. Conditional Statements
│   ├── if
│   ├── if-else
│   ├── if-else-if-else
│   ├── switch
│   ├── ternary operator
│   └── comparison operators
│
└── 2. Loops
    ├── for loop
    ├── while loop
    ├── do-while loop
    ├── for-of loop
    ├── for-in loop
    └── nested loops
```

**Today's Focus:** Conditional Statements (if, if-else, if-else-if-else)

---

## Part 3: The if Statement

### Syntax

```javascript
if (condition) {
    // Code executes ONLY if condition is true
}
```

### How it Works

```
Start
  ↓
Check condition
  ↓
Is it true?
  ↙    ↘
Yes     No
  ↓      ↓
Execute  Skip
block    block
  ↓      ↓
Continue program
```

### Example 1: Nightclub Security

```javascript
let age = 20;

if (age >= 18) {
    console.log("Welcome to the club!");
}
```

**Explanation:**
- Age is 20
- Is 20 >= 18? Yes (true)
- Execute the code block
- Output: "Welcome to the club!"

### Example 2: Underage Person

```javascript
let age = 15;

if (age >= 18) {
    console.log("Welcome to the club!");
}
```

**Explanation:**
- Age is 15
- Is 15 >= 18? No (false)
- Skip the code block
- Output: (nothing)

### Example 3: E-commerce Free Shipping

```javascript
let cartTotal = 12000;

if (cartTotal >= 10000) {
    console.log("You have qualified for free shipping!");
}
```

**Explanation:**
- Cart total is 12000
- Is 12000 >= 10000? Yes (true)
- Execute the code block
- Output: "You have qualified for free shipping!"

### Example 4: Not Qualified

```javascript
let cartTotal = 2000;

if (cartTotal >= 10000) {
    console.log("You have qualified for free shipping!");
}
```

**Explanation:**
- Cart total is 2000
- Is 2000 >= 10000? No (false)
- Skip the code block
- Output: (nothing)

---

## Part 4: The if-else Statement

### Syntax

```javascript
if (condition) {
    // Code executes if condition is TRUE
} else {
    // Code executes if condition is FALSE
}
```

### How it Works

```
Start
  ↓
Check condition
  ↓
Is it true?
  ↙    ↘
Yes     No
  ↓      ↓
Execute  Execute
if block else block
  ↓      ↓
Continue program
```

### Example 1: Airport Lounge Access

```javascript
let isVIP = true;

if (isVIP == true) {
    console.log("Welcome to the VIP lounge");
} else {
    console.log("Welcome to the regular lounge");
}
```

**Output:** "Welcome to the VIP lounge"

### Example 2: Regular Customer

```javascript
let isVIP = false;

if (isVIP == true) {
    console.log("Welcome to the VIP lounge");
} else {
    console.log("Welcome to the regular lounge");
}
```

**Output:** "Welcome to the regular lounge"

### Example 3: ATM Withdrawal

```javascript
let balance = 1000;
let withdrawAmount = 700;

if (balance >= withdrawAmount) {
    console.log("Transaction successful");
} else {
    console.log("Insufficient balance");
}
```

**Explanation:**
- Balance: 1000
- Withdraw: 700
- Is 1000 >= 700? Yes (true)
- Output: "Transaction successful"

### Example 4: Insufficient Funds

```javascript
let balance = 500;
let withdrawAmount = 700;

if (balance >= withdrawAmount) {
    console.log("Transaction successful");
} else {
    console.log("Insufficient balance");
}
```

**Explanation:**
- Balance: 500
- Withdraw: 700
- Is 500 >= 700? No (false)
- Output: "Insufficient balance"

---

## Part 5: The if-else-if-else Statement

### Syntax

```javascript
if (condition1) {
    // Executes if condition1 is TRUE
} else if (condition2) {
    // Executes if condition1 is FALSE and condition2 is TRUE
} else {
    // Executes if both conditions are FALSE
}
```

### How it Works

```
Start
  ↓
Check condition1
  ↓
Is it true?
  ↙    ↘
Yes     No
  ↓      ↓
Execute  Check condition2
block1     ↓
  ↓    Is it true?
  ↓      ↙    ↘
  ↓    Yes     No
  ↓     ↓      ↓
  ↓   Execute Execute
  ↓   block2  block3
  ↓     ↓      ↓
Continue program
```

### Example: Railway Ticket Pricing

**Rules:**
- Age < 12: Child ticket
- Age >= 12 and < 65: Adult ticket
- Age >= 65: Senior citizen ticket

### Visual Flow

```
Start
  ↓
Check: age < 12?
  ↙    ↘
Yes     No
  ↓      ↓
Child  Check: age >= 65?
ticket   ↙    ↘
  ↓    Yes     No
  ↓     ↓      ↓
  ↓   Senior  Adult
  ↓   ticket  ticket
  ↓     ↓      ↓
End program
```

### Code Example 1: Child

```javascript
let age = 10;

if (age < 12) {
    console.log("Child ticket price");
} else if (age >= 65) {
    console.log("Senior citizen ticket price");
} else {
    console.log("Adult ticket price");
}
```

**Explanation:**
- Age: 10
- Is 10 < 12? Yes (true)
- Execute first block
- Output: "Child ticket price"

### Code Example 2: Adult

```javascript
let age = 30;

if (age < 12) {
    console.log("Child ticket price");
} else if (age >= 65) {
    console.log("Senior citizen ticket price");
} else {
    console.log("Adult ticket price");
}
```

**Explanation:**
- Age: 30
- Is 30 < 12? No (false)
- Check next condition
- Is 30 >= 65? No (false)
- Execute else block
- Output: "Adult ticket price"

### Code Example 3: Senior Citizen

```javascript
let age = 70;

if (age < 12) {
    console.log("Child ticket price");
} else if (age >= 65) {
    console.log("Senior citizen ticket price");
} else {
    console.log("Adult ticket price");
}
```

**Explanation:**
- Age: 70
- Is 70 < 12? No (false)
- Check next condition
- Is 70 >= 65? Yes (true)
- Execute else-if block
- Output: "Senior citizen ticket price"

---

## Part 6: Multiple else-if Statements

### You Can Have Multiple else-if

```javascript
if (condition1) {
    // Block 1
} else if (condition2) {
    // Block 2
} else if (condition3) {
    // Block 3
} else if (condition4) {
    // Block 4
} else {
    // Default block
}
```

### Example: Grade Calculator

```javascript
let marks = 85;

if (marks >= 90) {
    console.log("Grade: A+");
} else if (marks >= 80) {
    console.log("Grade: A");
} else if (marks >= 70) {
    console.log("Grade: B");
} else if (marks >= 60) {
    console.log("Grade: C");
} else if (marks >= 50) {
    console.log("Grade: D");
} else {
    console.log("Grade: F (Fail)");
}
```

**Output:** "Grade: A"

---

## Part 7: Real-World Examples

### Example 1: Login System

```javascript
let username = "admin";
let password = "pass123";

let enteredUsername = "admin";
let enteredPassword = "pass123";

if (enteredUsername === username && enteredPassword === password) {
    console.log("Login successful!");
} else {
    console.log("Invalid credentials!");
}
```

### Example 2: Discount Calculator

```javascript
let purchaseAmount = 5000;
let discount = 0;

if (purchaseAmount >= 10000) {
    discount = 20;  // 20% discount
} else if (purchaseAmount >= 5000) {
    discount = 10;  // 10% discount
} else if (purchaseAmount >= 2000) {
    discount = 5;   // 5% discount
} else {
    discount = 0;   // No discount
}

console.log("You get " + discount + "% discount");
```

**Output:** "You get 10% discount"

### Example 3: Temperature Check

```javascript
let temperature = 35;

if (temperature > 40) {
    console.log("Extremely hot!");
} else if (temperature > 30) {
    console.log("Hot weather");
} else if (temperature > 20) {
    console.log("Pleasant weather");
} else if (temperature > 10) {
    console.log("Cold weather");
} else {
    console.log("Very cold!");
}
```

**Output:** "Hot weather"

### Example 4: Exam Result

```javascript
let marks = 45;
let attendance = 80;

if (marks >= 40 && attendance >= 75) {
    console.log("Pass");
} else {
    console.log("Fail");
}
```

**Output:** "Pass"

### Example 5: Age Category

```javascript
let age = 25;

if (age < 13) {
    console.log("Child");
} else if (age < 20) {
    console.log("Teenager");
} else if (age < 60) {
    console.log("Adult");
} else {
    console.log("Senior");
}
```

**Output:** "Adult"

---

## Part 8: Important Concepts

### Truthy and Falsy in Conditions

```javascript
// These are FALSY (treated as false)
if (0) { }           // Won't execute
if ("") { }          // Won't execute
if (null) { }        // Won't execute
if (undefined) { }   // Won't execute
if (NaN) { }         // Won't execute
if (false) { }       // Won't execute

// These are TRUTHY (treated as true)
if (1) { }           // Will execute
if ("hello") { }     // Will execute
if (true) { }        // Will execute
if ([]) { }          // Will execute
if ({}) { }          // Will execute
```

### Simplified Conditions

```javascript
let isLoggedIn = true;

// Long way
if (isLoggedIn == true) {
    console.log("Welcome");
}

// Short way (recommended)
if (isLoggedIn) {
    console.log("Welcome");
}
```

### Negation with !

```javascript
let isLoggedIn = false;

// Check if NOT logged in
if (!isLoggedIn) {
    console.log("Please login");
}
```

---

## Part 9: Common Mistakes

### Mistake 1: Using = instead of ==

```javascript
let age = 18;

// Wrong - assignment, not comparison
if (age = 20) {  // ❌ This assigns 20 to age!
    console.log("This always runs");
}

// Correct
if (age == 20) {  // ✅ This compares
    console.log("Age is 20");
}
```

### Mistake 2: Missing Curly Braces

```javascript
// Works but not recommended
if (age >= 18)
    console.log("Adult");

// Recommended - always use braces
if (age >= 18) {
    console.log("Adult");
}
```

### Mistake 3: Semicolon After if

```javascript
// Wrong
if (age >= 18); {  // ❌ Semicolon here!
    console.log("Adult");
}

// Correct
if (age >= 18) {   // ✅ No semicolon
    console.log("Adult");
}
```

---

## Part 10: Practice Exercises

### Exercise 1: Even or Odd

```javascript
let number = 7;

// Write code to check if number is even or odd
// Hint: Use % (modulo) operator
```

### Exercise 2: Voting Eligibility

```javascript
let age = 17;

// Write code to check if person can vote
// Voting age is 18
```

### Exercise 3: Password Strength

```javascript
let password = "abc123";

// Check password length
// Strong: >= 8 characters
// Weak: < 8 characters
```

### Exercise 4: BMI Calculator

```javascript
let bmi = 22;

// Classify BMI:
// < 18.5: Underweight
// 18.5 - 24.9: Normal
// 25 - 29.9: Overweight
// >= 30: Obese
```

### Exercise 5: Traffic Light

```javascript
let light = "red";

// red: Stop
// yellow: Slow down
// green: Go
```

---

## Part 11: Key Takeaways

### ✅ Remember These Points

1. **if statement** - Executes code only if condition is true
2. **if-else statement** - Executes one block or the other
3. **if-else-if-else** - Multiple conditions, multiple paths
4. **Conditions** return true or false (boolean)
5. **Curly braces** `{}` define code blocks
6. **Only ONE block** executes in if-else-if chain
7. **else is optional** - you can have just if
8. **Use ===** for strict comparison (recommended)
9. **Truthy/Falsy** values work in conditions
10. **Indentation** makes code readable

### Syntax Summary

```javascript
// if
if (condition) {
    // code
}

// if-else
if (condition) {
    // code
} else {
    // code
}

// if-else-if-else
if (condition1) {
    // code
} else if (condition2) {
    // code
} else {
    // code
}
```

---

## What's Next?

In the next lesson, we'll continue with:

### Coming Up: JavaScript Day 9

- Switch statement
- Ternary operator
- Nested if statements
- Logical operators (AND, OR, NOT)
- Complex conditions

---

*Congratulations! You've completed JavaScript Day 8. You now understand how to control program flow using conditional statements!*

---

**Practice what you've learned and see you in the next class!** 🚀
