# JavaScript Day 9: Switch Statement, Ternary Operator, and Logical Operators

## Introduction

In Day 8, we learned about if-else statements for controlling program flow. Today, we'll learn three more powerful tools:

1. **Switch Statement** - Better way to handle multiple conditions
2. **Ternary Operator** - Shorthand for simple if-else
3. **Logical Operators** - Combine multiple conditions

---

## Part 1: The Switch Statement

### What is a Switch Statement?

A **switch statement** is used when you need to compare ONE value against MANY possible values.

### When to Use Switch vs if-else-if

```javascript
// Using if-else-if (repetitive)
if (day == 1) {
    console.log("Monday");
} else if (day == 2) {
    console.log("Tuesday");
} else if (day == 3) {
    console.log("Wednesday");
} else if (day == 4) {
    console.log("Thursday");
} else if (day == 5) {
    console.log("Friday");
}

// Using switch (cleaner)
switch (day) {
    case 1:
        console.log("Monday");
        break;
    case 2:
        console.log("Tuesday");
        break;
    case 3:
        console.log("Wednesday");
        break;
    case 4:
        console.log("Thursday");
        break;
    case 5:
        console.log("Friday");
        break;
}
```

### Switch Statement Syntax

```javascript
switch (expression) {
    case value1:
        // Code executes if expression === value1
        break;
    case value2:
        // Code executes if expression === value2
        break;
    case value3:
        // Code executes if expression === value3
        break;
    default:
        // Code executes if no case matches
}
```

### How Switch Works - Visual Flow

```
Start
  ↓
Evaluate expression
  ↓
Compare with case 1
  ↓
Match? → Yes → Execute case 1 → break → End
  ↓ No
Compare with case 2
  ↓
Match? → Yes → Execute case 2 → break → End
  ↓ No
Compare with case 3
  ↓
Match? → Yes → Execute case 3 → break → End
  ↓ No
Execute default
  ↓
End
```

---

## Part 2: Switch Statement Examples

### Example 1: User Role System (Real-World)

Let's understand with a real platform example. Imagine a learning platform where different users have different permissions:

- **Admin** - Full access to the system
- **Editor** - Can edit content
- **Author** - Can create content
- **Subscriber/Student** - Can only view content

```javascript
let userRole = "admin";

switch (userRole) {
    case "admin":
        console.log("Full access granted");
        break;
    case "editor":
        console.log("Editor access granted");
        break;
    case "author":
        console.log("Author access granted");
        break;
    case "student":
        console.log("Student access granted");
        break;
    default:
        console.log("Access denied");
}
```

**Output:** "Full access granted"

**Why Switch is Better Here:**

Compare this with if-else-if approach:

```javascript
let userRole = "editor";

if (userRole === "admin") {
    console.log("Full access granted");
} else if (userRole === "editor") {
    console.log("Editor access granted");
} else if (userRole === "author") {
    console.log("Author access granted");
} else if (userRole === "student") {
    console.log("Student access granted");
} else {
    console.log("Access denied");
}
```

**Notice:** Switch is much cleaner and more readable!

### Example 2: Days of the Week

```javascript
let day = 3;

switch (day) {
    case 1:
        console.log("Monday");
        break;
    case 2:
        console.log("Tuesday");
        break;
    case 3:
        console.log("Wednesday");
        break;
    case 4:
        console.log("Thursday");
        break;
    case 5:
        console.log("Friday");
        break;
    case 6:
        console.log("Saturday");
        break;
    case 7:
        console.log("Sunday");
        break;
    default:
        console.log("Invalid day");
}
```

**Output:** "Wednesday"

### Example 3: Traffic Light System

```javascript
let light = "red";

switch (light) {
    case "red":
        console.log("Stop");
        break;
    case "yellow":
        console.log("Slow down");
        break;
    case "green":
        console.log("Go");
        break;
    default:
        console.log("Invalid light color");
}
```

**Output:** "Stop"

### Example 4: Grade System

```javascript
let grade = "B";

switch (grade) {
    case "A":
        console.log("Excellent! 90-100%");
        break;
    case "B":
        console.log("Good! 80-89%");
        break;
    case "C":
        console.log("Average! 70-79%");
        break;
    case "D":
        console.log("Below Average! 60-69%");
        break;
    case "F":
        console.log("Fail! Below 60%");
        break;
    default:
        console.log("Invalid grade");
}
```

**Output:** "Good! 80-89%"

---

## Part 3: The break Statement

### What is break?

The **break** statement exits the switch block immediately after executing a case.

### Important: Switch Uses Strict Equality (===)

When switch compares values, it uses **strict equality (===)**, which means:
- Both VALUE and TYPE must match
- `switch(5)` will NOT match `case "5"` (number vs string)

```javascript
let value = 5;

switch (value) {
    case "5":
        console.log("String 5");
        break;
    case 5:
        console.log("Number 5");
        break;
}
```

**Output:** "Number 5" (because 5 === 5, not 5 === "5")

### Without break - Fall Through

```javascript
let day = 2;

switch (day) {
    case 1:
        console.log("Monday");
    case 2:
        console.log("Tuesday");
    case 3:
        console.log("Wednesday");
    case 4:
        console.log("Thursday");
}
```

**Output:**
```
Tuesday
Wednesday
Thursday
```

**Why?** Without break, execution continues to the next cases!

### With break - Correct Behavior

```javascript
let day = 2;

switch (day) {
    case 1:
        console.log("Monday");
        break;
    case 2:
        console.log("Tuesday");
        break;
    case 3:
        console.log("Wednesday");
        break;
    case 4:
        console.log("Thursday");
        break;
}
```

**Output:**
```
Tuesday
```

**Correct!** break stops execution after matching case.

---

## Part 4: Multiple Cases with Same Code

### Grouping Cases

Sometimes multiple cases should execute the same code:

```javascript
let day = 6;

switch (day) {
    case 1:
    case 2:
    case 3:
    case 4:
    case 5:
        console.log("Weekday - Go to work");
        break;
    case 6:
    case 7:
        console.log("Weekend - Relax!");
        break;
    default:
        console.log("Invalid day");
}
```

**Output:** "Weekend - Relax!"

### Real Example: Weekend Message System

From the video transcript - a complete weekend checker:

```javascript
let day = 0;  // 0 = Sunday, 1 = Monday, ..., 6 = Saturday

switch (day) {
    case 0:
    case 6:
        console.log("Happy Weekend");
        break;
    case 1:
        console.log("Happy Monday");
        break;
    case 2:
    case 3:
    case 4:
        console.log("Happy Midweek");
        break;
    case 5:
        console.log("Thank God It's Friday");
        break;
    default:
        console.log("Invalid day");
}
```

**Explanation:**
- **Case 0 and 6** (Sunday and Saturday) - Grouped together for weekend message
- **Case 1** (Monday) - Separate message
- **Case 2, 3, 4** (Tuesday, Wednesday, Thursday) - Grouped for midweek
- **Case 5** (Friday) - Special TGIF message!

**Output:** "Happy Weekend"

### Example: Month Days

```javascript
let month = 2;

switch (month) {
    case 1:
    case 3:
    case 5:
    case 7:
    case 8:
    case 10:
    case 12:
        console.log("This month has 31 days");
        break;
    case 4:
    case 6:
    case 9:
    case 11:
        console.log("This month has 30 days");
        break;
    case 2:
        console.log("This month has 28 or 29 days");
        break;
    default:
        console.log("Invalid month");
}
```

**Output:** "This month has 28 or 29 days"

---

## Part 5: The default Case

### What is default?

The **default** case executes when NO other case matches. It's like the **else** in if-else.

### Example: Calculator

```javascript
let operator = "%";

switch (operator) {
    case "+":
        console.log("Addition");
        break;
    case "-":
        console.log("Subtraction");
        break;
    case "*":
        console.log("Multiplication");
        break;
    case "/":
        console.log("Division");
        break;
    default:
        console.log("Unknown operator");
}
```

**Output:** "Unknown operator"

### default is Optional

```javascript
let color = "blue";

switch (color) {
    case "red":
        console.log("Stop");
        break;
    case "green":
        console.log("Go");
        break;
    // No default - nothing happens if no match
}
```

**Output:** (nothing)

---

## Part 6: The Ternary Operator

### What is the Ternary Operator?

The **ternary operator** is a shorthand way to write simple if-else statements in ONE line.

### Syntax

```javascript
condition ? valueIfTrue : valueIfFalse
```

### Visual Comparison

```javascript
// Using if-else (multiple lines)
let age = 20;
let message;
if (age >= 18) {
    message = "Can vote";
} else {
    message = "Cannot vote";
}

// Using ternary operator (1 line)
let age = 20;
let message = age >= 18 ? "Can vote" : "Cannot vote";
```

**Both produce the same result, but ternary is more concise!**

### How Ternary Works

```
condition ? value1 : value2
    ↓
Is condition true?
    ↙        ↘
  Yes         No
    ↓          ↓
Return      Return
value1      value2
```

### Breaking Down the Ternary

```javascript
let age = 20;
let message = age >= 18 ? "Can vote" : "Cannot vote";
```

**Step-by-step:**
1. Check condition: Is age >= 18?
2. Age is 20, so 20 >= 18 is TRUE
3. Since TRUE, take the first value: "Can vote"
4. Assign "Can vote" to message
5. Result: message = "Can vote"

**If age was 16:**
1. Check condition: Is 16 >= 18?
2. 16 >= 18 is FALSE
3. Since FALSE, take the second value: "Cannot vote"
4. Assign "Cannot vote" to message
5. Result: message = "Cannot vote"

---

## Part 7: Ternary Operator Examples

### Example 1: Voting Eligibility

```javascript
let age = 17;
let canVote = age >= 18 ? "Yes" : "No";
console.log(canVote);
```

**Output:** "No"

### Example 2: Pass or Fail

```javascript
let marks = 45;
let result = marks >= 40 ? "Pass" : "Fail";
console.log(result);
```

**Output:** "Pass"

### Example 3: Even or Odd

```javascript
let number = 7;
let type = number % 2 == 0 ? "Even" : "Odd";
console.log(type);
```

**Output:** "Odd"

### Example 4: Discount Eligibility

```javascript
let purchaseAmount = 5000;
let discount = purchaseAmount >= 3000 ? "10% discount" : "No discount";
console.log(discount);
```

**Output:** "10% discount"

### Example 5: Temperature Message

```javascript
let temp = 35;
let message = temp > 30 ? "It's hot!" : "It's pleasant";
console.log(message);
```

**Output:** "It's hot!"

---

## Part 8: Nested Ternary (Advanced)

### You Can Nest Ternary Operators

```javascript
let marks = 85;
let grade = marks >= 90 ? "A" : marks >= 80 ? "B" : marks >= 70 ? "C" : "D";
console.log(grade);
```

**Output:** "B"

### Warning: Don't Overuse Nested Ternary

```javascript
// Hard to read ❌
let result = a > b ? a > c ? a : c : b > c ? b : c;

// Better: Use if-else ✅
let result;
if (a > b) {
    if (a > c) {
        result = a;
    } else {
        result = c;
    }
} else {
    if (b > c) {
        result = b;
    } else {
        result = c;
    }
}
```

---

## Part 9: Logical Operators

### What are Logical Operators?

**Logical operators** combine multiple conditions to create complex logic.

### Three Logical Operators

| Operator | Name | Symbol | Description |
|----------|------|--------|-------------|
| AND | Logical AND | `&&` | Both conditions must be true |
| OR | Logical OR | `\|\|` | At least one condition must be true |
| NOT | Logical NOT | `!` | Reverses the condition |

---

## Part 10: AND Operator (&&)

### How AND Works

```
Condition1 && Condition2
    ↓
Both true? → Yes → Result: true
    ↓
   No → Result: false
```

### Truth Table for AND

| Condition1 | Condition2 | Result |
|------------|------------|--------|
| true | true | true |
| true | false | false |
| false | true | false |
| false | false | false |

**Rule:** BOTH must be true for result to be true

### Example 1: Login System

```javascript
let username = "admin";
let password = "pass123";

let enteredUser = "admin";
let enteredPass = "pass123";

if (enteredUser === username && enteredPass === password) {
    console.log("Login successful");
} else {
    console.log("Login failed");
}
```

**Output:** "Login successful"

### Example 2: Exam Pass Criteria

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

### Example 3: Age Range Check

```javascript
let age = 25;

if (age >= 18 && age <= 60) {
    console.log("Eligible for job");
} else {
    console.log("Not eligible");
}
```

**Output:** "Eligible for job"

---

## Part 11: OR Operator (||)

### How OR Works

```
Condition1 || Condition2
    ↓
At least one true? → Yes → Result: true
    ↓
   No → Result: false
```

### Truth Table for OR

| Condition1 | Condition2 | Result |
|------------|------------|--------|
| true | true | true |
| true | false | true |
| false | true | true |
| false | false | false |

**Rule:** At least ONE must be true for result to be true

### Example 1: Weekend Check

```javascript
let day = "Saturday";

if (day === "Saturday" || day === "Sunday") {
    console.log("It's weekend!");
} else {
    console.log("It's a weekday");
}
```

**Output:** "It's weekend!"

### Example 2: Discount Eligibility

```javascript
let isVIP = false;
let purchaseAmount = 6000;

if (isVIP || purchaseAmount >= 5000) {
    console.log("You get a discount");
} else {
    console.log("No discount");
}
```

**Output:** "You get a discount"

### Example 3: Emergency Contact

```javascript
let isParent = false;
let isGuardian = true;

if (isParent || isGuardian) {
    console.log("Can pick up child");
} else {
    console.log("Cannot pick up child");
}
```

**Output:** "Can pick up child"

---

## Part 12: NOT Operator (!)

### How NOT Works

```
!condition
    ↓
Reverse the result
    ↓
true → false
false → true
```

### Truth Table for NOT

| Condition | Result |
|-----------|--------|
| true | false |
| false | true |

**Rule:** Reverses the boolean value

### Example 1: Check if NOT Logged In

```javascript
let isLoggedIn = false;

if (!isLoggedIn) {
    console.log("Please login");
} else {
    console.log("Welcome");
}
```

**Output:** "Please login"

### Example 2: Check if NOT Empty

```javascript
let username = "";

if (!username) {
    console.log("Username is required");
} else {
    console.log("Username accepted");
}
```

**Output:** "Username is required"

### Example 3: Toggle State

```javascript
let isVisible = true;
isVisible = !isVisible;  // Toggle
console.log(isVisible);
```

**Output:** false

---

## Part 13: Combining Logical Operators

### You Can Combine Multiple Operators

```javascript
let age = 25;
let hasLicense = true;
let hasInsurance = true;

if (age >= 18 && hasLicense && hasInsurance) {
    console.log("Can drive");
} else {
    console.log("Cannot drive");
}
```

**Output:** "Can drive"

### Example: Complex Condition

```javascript
let marks = 85;
let attendance = 70;
let hasProject = true;

if ((marks >= 40 && attendance >= 75) || hasProject) {
    console.log("Pass");
} else {
    console.log("Fail");
}
```

**Explanation:**
- marks >= 40? Yes (85 >= 40)
- attendance >= 75? No (70 < 75)
- First part: true && false = false
- hasProject? Yes (true)
- Final: false || true = true
- **Output:** "Pass"

### Example: Loan Eligibility

```javascript
let age = 30;
let income = 50000;
let creditScore = 700;

if ((age >= 21 && age <= 60) && income >= 30000 && creditScore >= 650) {
    console.log("Loan approved");
} else {
    console.log("Loan rejected");
}
```

**Output:** "Loan approved"

---

## Part 14: Operator Precedence

### Order of Evaluation

When multiple operators are used, JavaScript evaluates them in this order:

1. **NOT (!)** - Highest priority
2. **AND (&&)** - Medium priority
3. **OR (||)** - Lowest priority

### Example

```javascript
let result = true || false && false;
console.log(result);
```

**Evaluation:**
1. First: false && false = false (AND has higher priority than OR)
2. Then: true || false = true
3. **Output:** true

### Use Parentheses for Clarity

```javascript
// Without parentheses (confusing)
let result = true || false && false;

// With parentheses (clear)
let result = true || (false && false);
```

---

## Part 15: Real-World Examples

### Example 1: ATM Withdrawal

```javascript
let balance = 5000;
let withdrawAmount = 3000;
let dailyLimit = 10000;
let hasCard = true;
let pinCorrect = true;

if (hasCard && pinCorrect && withdrawAmount <= balance && withdrawAmount <= dailyLimit) {
    console.log("Transaction successful");
    balance = balance - withdrawAmount;
    console.log("Remaining balance: " + balance);
} else {
    console.log("Transaction failed");
}
```

**Output:**
```
Transaction successful
Remaining balance: 2000
```

### Example 2: Movie Ticket Booking

```javascript
let age = 16;
let hasParent = false;
let movieRating = "A";  // A = Adult only

if (movieRating === "U" || (movieRating === "A" && (age >= 18 || hasParent))) {
    console.log("Ticket booked");
} else {
    console.log("Not allowed");
}
```

**Output:** "Not allowed"

### Example 3: E-commerce Checkout

```javascript
let cartTotal = 2000;
let hasPromoCode = true;
let isFirstOrder = false;

let discount = 0;

if (cartTotal >= 5000) {
    discount = 20;
} else if (cartTotal >= 3000 || hasPromoCode || isFirstOrder) {
    discount = 10;
}

console.log("Discount: " + discount + "%");
```

**Output:** "Discount: 10%"

---

## Part 16: Comparison Table

### When to Use What?

| Scenario | Best Choice | Reason |
|----------|-------------|--------|
| Comparing one value against many | Switch | Cleaner, more readable |
| Simple true/false decision | if-else | Clear and straightforward |
| One-line simple condition | Ternary | Concise and elegant |
| Multiple conditions together | Logical operators | Combine conditions |
| Range checking | if-else with && | More flexible |

---

## Part 17: Practice Exercises

### Exercise 1: Calculator with Switch

```javascript
let num1 = 10;
let num2 = 5;
let operator = "+";

// Use switch to perform calculation
// +, -, *, /
```

### Exercise 2: Season Finder

```javascript
let month = 7;

// Use switch to find season
// 12, 1, 2: Winter
// 3, 4, 5: Spring
// 6, 7, 8: Summer
// 9, 10, 11: Autumn
```

### Exercise 3: Ternary for Discount

```javascript
let isMember = true;
let purchaseAmount = 2000;

// Use ternary to give 15% discount if member, else 5%
```

### Exercise 4: Login with Logical Operators

```javascript
let username = "user123";
let password = "pass456";
let captcha = true;

// Check all three conditions using &&
```

### Exercise 5: Complex Eligibility

```javascript
let age = 22;
let education = "Graduate";
let experience = 1;

// Eligible if:
// (age >= 21 AND age <= 30) AND
// (education is "Graduate" OR experience >= 2)
```

---

## Part 18: Common Mistakes

### Mistake 1: Forgetting break in Switch

```javascript
// Wrong ❌
switch (day) {
    case 1:
        console.log("Monday");
    case 2:
        console.log("Tuesday");
}

// Correct ✅
switch (day) {
    case 1:
        console.log("Monday");
        break;
    case 2:
        console.log("Tuesday");
        break;
}
```

### Mistake 2: Using = in Ternary

```javascript
// Wrong ❌
let result = age >= 18 = "Adult" : "Minor";

// Correct ✅
let result = age >= 18 ? "Adult" : "Minor";
```

### Mistake 3: Confusing && and ||

```javascript
// Wrong logic ❌
if (age >= 18 || age <= 60) {  // This is always true!
    console.log("Eligible");
}

// Correct ✅
if (age >= 18 && age <= 60) {
    console.log("Eligible");
}
```

---

## Part 19: Key Takeaways

### ✅ Remember These Points

1. **Switch** is best for comparing one value against many
2. **break** is essential in switch to prevent fall-through
3. **default** in switch is like else in if-else
4. **Ternary operator** is shorthand for simple if-else
5. **&&** requires ALL conditions to be true
6. **||** requires AT LEAST ONE condition to be true
7. **!** reverses the boolean value
8. Use **parentheses** for complex conditions
9. **Operator precedence**: ! > && > ||
10. Choose the right tool for readability

### Syntax Summary

```javascript
// Switch
switch (expression) {
    case value1:
        // code
        break;
    case value2:
        // code
        break;
    default:
        // code
}

// Ternary
condition ? valueIfTrue : valueIfFalse

// Logical Operators
condition1 && condition2  // AND
condition1 || condition2  // OR
!condition                // NOT
```

---

## What's Next?

In the next lesson, we'll learn about:

### Coming Up: JavaScript Day 10

- Loops introduction
- for loop
- while loop
- do-while loop
- Loop control statements (break, continue)

---

*Congratulations! You've completed JavaScript Day 9. You now have powerful tools to write complex conditional logic!*

---

**Practice these concepts and see you in the next class!** 🚀
