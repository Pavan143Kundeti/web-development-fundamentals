# JavaScript Day 16: Arrays - Complete Guide

## Introduction

An array is a special variable that can store multiple values in a single variable. Instead of creating separate variables for each item, you can store them all in one array.

**Example:**
```javascript
// Without array (bad)
let car1 = "Volvo";
let car2 = "BMW";
let car3 = "Toyota";

// With array (good)
const cars = ["Volvo", "BMW", "Toyota"];
```

---

## Part 1: What is an Array?

### Array Definition

An array is an ordered collection of values stored under a single variable name.

### Key Characteristics

| Feature | Description |
|---------|-------------|
| Ordered | Elements have a specific position (index) |
| Zero-indexed | First element is at index 0 |
| Dynamic | Can grow or shrink in size |
| Heterogeneous | Can store different data types |

### Visual: Array Structure

```
Array: cars
┌─────┬─────┬─────┬─────┐
│  0  │  1  │  2  │  3  │  ← Index
├─────┼─────┼─────┼─────┤
│Volvo│ BMW │Audi │Ford │  ← Values
└─────┴─────┴─────┴─────┘
```

---

## Part 2: Creating Arrays

### Method 1: Array Literal (Recommended)

```javascript
const fruits = ["Apple", "Banana", "Orange"];
```

### Method 2: Multiple Lines

```javascript
const fruits = [
    "Apple",
    "Banana",
    "Orange"
];
```

### Method 3: Empty Array, Add Later

```javascript
const fruits = [];
fruits[0] = "Apple";
fruits[1] = "Banana";
fruits[2] = "Orange";
```

### Method 4: new Array() (Not Recommended)

```javascript
const fruits = new Array("Apple", "Banana", "Orange");
```

**Note:** Always use array literal `[]` - it's simpler and faster!

---

## Part 3: Accessing Array Elements

### Using Index Numbers

```javascript
const fruits = ["Apple", "Banana", "Orange"];

console.log(fruits[0]);  // Output: Apple
console.log(fruits[1]);  // Output: Banana
console.log(fruits[2]);  // Output: Orange
```

### Index Starts at 0

```
Index:  0        1         2
       ┌────┬─────────┬────────┐
Array: │Apple│ Banana  │ Orange │
       └────┴─────────┴────────┘
```

### Accessing First Element

```javascript
const fruits = ["Apple", "Banana", "Orange"];
let first = fruits[0];
console.log(first);  // Output: Apple
```

### Accessing Last Element

```javascript
const fruits = ["Apple", "Banana", "Orange"];
let last = fruits[fruits.length - 1];
console.log(last);  // Output: Orange
```

---

## Part 4: Array Length

### The length Property

```javascript
const fruits = ["Apple", "Banana", "Orange"];
console.log(fruits.length);  // Output: 3
```

### Visual: Length

```
Array: ["Apple", "Banana", "Orange"]
        ↓        ↓         ↓
      Index 0  Index 1  Index 2
      
Length = 3 (total number of elements)
```

---

## Part 5: Changing Array Elements

### Modify Existing Element

```javascript
const fruits = ["Apple", "Banana", "Orange"];
fruits[1] = "Mango";
console.log(fruits);  // Output: ["Apple", "Mango", "Orange"]
```

### Add Element at Specific Index

```javascript
const fruits = ["Apple", "Banana"];
fruits[2] = "Orange";
console.log(fruits);  // Output: ["Apple", "Banana", "Orange"]
```

---

## Part 6: Adding Elements

### push() - Add to End

```javascript
const fruits = ["Apple", "Banana"];
fruits.push("Orange");
console.log(fruits);  // Output: ["Apple", "Banana", "Orange"]
```

### unshift() - Add to Beginning

```javascript
const fruits = ["Banana", "Orange"];
fruits.unshift("Apple");
console.log(fruits);  // Output: ["Apple", "Banana", "Orange"]
```

### Using length Property

```javascript
const fruits = ["Apple", "Banana"];
fruits[fruits.length] = "Orange";
console.log(fruits);  // Output: ["Apple", "Banana", "Orange"]
```

---

## Part 7: Removing Elements

### pop() - Remove from End

```javascript
const fruits = ["Apple", "Banana", "Orange"];
let removed = fruits.pop();
console.log(removed);  // Output: Orange
console.log(fruits);   // Output: ["Apple", "Banana"]
```

### shift() - Remove from Beginning

```javascript
const fruits = ["Apple", "Banana", "Orange"];
let removed = fruits.shift();
console.log(removed);  // Output: Apple
console.log(fruits);   // Output: ["Banana", "Orange"]
```

### Visual: Push, Pop, Shift, Unshift

```
Original: ["Apple", "Banana", "Orange"]

push("Mango"):
["Apple", "Banana", "Orange", "Mango"]  ← Added to end

pop():
["Apple", "Banana"]  ← Removed from end

unshift("Grape"):
["Grape", "Apple", "Banana"]  ← Added to beginning

shift():
["Apple", "Banana"]  ← Removed from beginning
```

---

## Part 8: Array Methods Summary

### Essential Array Methods

| Method | Description | Example | Result |
|--------|-------------|---------|--------|
| `push()` | Add to end | `arr.push("x")` | Adds "x" to end |
| `pop()` | Remove from end | `arr.pop()` | Removes last element |
| `unshift()` | Add to beginning | `arr.unshift("x")` | Adds "x" to start |
| `shift()` | Remove from beginning | `arr.shift()` | Removes first element |
| `length` | Get array size | `arr.length` | Returns number of elements |

---

## Part 9: Looping Through Arrays

### Method 1: for Loop

```javascript
const fruits = ["Apple", "Banana", "Orange"];

for (let i = 0; i < fruits.length; i++) {
    console.log(fruits[i]);
}
```

**Output:**
```
Apple
Banana
Orange
```

### Method 2: for...of Loop

```javascript
const fruits = ["Apple", "Banana", "Orange"];

for (let fruit of fruits) {
    console.log(fruit);
}
```

**Output:**
```
Apple
Banana
Orange
```

### Method 3: forEach()

```javascript
const fruits = ["Apple", "Banana", "Orange"];

fruits.forEach(function(fruit) {
    console.log(fruit);
});
```

**Output:**
```
Apple
Banana
Orange
```

---

## Part 10: Array Methods - Searching

### indexOf() - Find Position

```javascript
const fruits = ["Apple", "Banana", "Orange"];
let position = fruits.indexOf("Banana");
console.log(position);  // Output: 1
```

Returns `-1` if not found:

```javascript
const fruits = ["Apple", "Banana", "Orange"];
let position = fruits.indexOf("Mango");
console.log(position);  // Output: -1
```

### includes() - Check if Exists

```javascript
const fruits = ["Apple", "Banana", "Orange"];

console.log(fruits.includes("Banana"));  // Output: true
console.log(fruits.includes("Mango"));   // Output: false
```

---

## Part 11: Array Methods - Joining and Splitting

### join() - Array to String

```javascript
const fruits = ["Apple", "Banana", "Orange"];
let text = fruits.join(", ");
console.log(text);  // Output: Apple, Banana, Orange
```

### toString() - Array to String

```javascript
const fruits = ["Apple", "Banana", "Orange"];
let text = fruits.toString();
console.log(text);  // Output: Apple,Banana,Orange
```

---

## Part 12: Array Methods - Slicing and Splicing

### slice() - Extract Part

```javascript
const fruits = ["Apple", "Banana", "Orange", "Mango", "Kiwi"];
let citrus = fruits.slice(1, 3);
console.log(citrus);  // Output: ["Banana", "Orange"]
console.log(fruits);  // Original unchanged
```

### splice() - Add/Remove Elements

```javascript
const fruits = ["Apple", "Banana", "Orange"];

// Remove 1 element at index 1
fruits.splice(1, 1);
console.log(fruits);  // Output: ["Apple", "Orange"]

// Add elements at index 1
fruits.splice(1, 0, "Mango", "Kiwi");
console.log(fruits);  // Output: ["Apple", "Mango", "Kiwi", "Orange"]
```

**Syntax:** `array.splice(start, deleteCount, item1, item2, ...)`

---

## Part 13: Array Methods - Combining

### concat() - Merge Arrays

```javascript
const fruits = ["Apple", "Banana"];
const vegetables = ["Carrot", "Potato"];
const food = fruits.concat(vegetables);

console.log(food);
// Output: ["Apple", "Banana", "Carrot", "Potato"]
```

### Spread Operator (...)

```javascript
const fruits = ["Apple", "Banana"];
const vegetables = ["Carrot", "Potato"];
const food = [...fruits, ...vegetables];

console.log(food);
// Output: ["Apple", "Banana", "Carrot", "Potato"]
```

---

## Part 14: Array Methods - Sorting

### sort() - Sort Alphabetically

```javascript
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.sort();
console.log(fruits);
// Output: ["Apple", "Banana", "Mango", "Orange"]
```

### reverse() - Reverse Order

```javascript
const fruits = ["Apple", "Banana", "Orange"];
fruits.reverse();
console.log(fruits);
// Output: ["Orange", "Banana", "Apple"]
```

### Sorting Numbers

```javascript
const numbers = [40, 100, 1, 5, 25, 10];

// Wrong way (sorts as strings)
numbers.sort();
console.log(numbers);  // Output: [1, 10, 100, 25, 40, 5]

// Correct way (sorts as numbers)
numbers.sort(function(a, b) {
    return a - b;
});
console.log(numbers);  // Output: [1, 5, 10, 25, 40, 100]
```

---

## Part 15: Array Methods - Filtering and Mapping

### filter() - Filter Elements

```javascript
const numbers = [45, 4, 9, 16, 25];
const over18 = numbers.filter(function(value) {
    return value > 18;
});

console.log(over18);  // Output: [45, 25]
```

### map() - Transform Elements

```javascript
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map(function(value) {
    return value * 2;
});

console.log(doubled);  // Output: [2, 4, 6, 8, 10]
```

---

## Part 16: Arrays vs Objects

### Comparison Table

| Feature | Array | Object |
|---------|-------|--------|
| Index | Numbers (0, 1, 2...) | Names (keys) |
| Order | Ordered | Not guaranteed |
| Access | `arr[0]` | `obj.name` or `obj["name"]` |
| Use when | List of items | Properties with names |

### Array Example

```javascript
const person = ["John", "Doe", 30];
console.log(person[0]);  // Output: John
```

### Object Example

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30
};
console.log(person.firstName);  // Output: John
```

---

## Part 17: Arrays with const

### Can Change Elements

```javascript
const fruits = ["Apple", "Banana", "Orange"];

// This works ✅
fruits[0] = "Mango";
fruits.push("Kiwi");
console.log(fruits);  // Output: ["Mango", "Banana", "Orange", "Kiwi"]
```

### Cannot Reassign Array

```javascript
const fruits = ["Apple", "Banana", "Orange"];

// This fails ❌
fruits = ["Mango", "Kiwi"];  // Error!
```

---

## Part 18: Practical Examples

### Example 1: Shopping Cart

```javascript
const cart = [];

// Add items
cart.push("Laptop");
cart.push("Mouse");
cart.push("Keyboard");

console.log("Cart:", cart);
// Output: Cart: ["Laptop", "Mouse", "Keyboard"]

// Remove last item
cart.pop();
console.log("Cart:", cart);
// Output: Cart: ["Laptop", "Mouse"]
```

### Example 2: Student Grades

```javascript
const grades = [85, 90, 78, 92, 88];

// Calculate average
let sum = 0;
for (let grade of grades) {
    sum += grade;
}
let average = sum / grades.length;
console.log("Average:", average);  // Output: Average: 86.6
```

### Example 3: Todo List

```javascript
const todos = ["Buy groceries", "Clean room", "Study JavaScript"];

// Display todos
console.log("Todo List:");
for (let i = 0; i < todos.length; i++) {
    console.log((i + 1) + ". " + todos[i]);
}
```

**Output:**
```
Todo List:
1. Buy groceries
2. Clean room
3. Study JavaScript
```

---

## Part 19: Common Mistakes

### Mistake 1: Accessing Non-existent Index

```javascript
const fruits = ["Apple", "Banana"];
console.log(fruits[5]);  // Output: undefined (not error)
```

### Mistake 2: Confusing length with Index

```javascript
const fruits = ["Apple", "Banana", "Orange"];

// Wrong ❌
console.log(fruits[fruits.length]);  // undefined

// Correct ✅
console.log(fruits[fruits.length - 1]);  // Orange
```

### Mistake 3: Creating Holes in Array

```javascript
const fruits = ["Apple", "Banana"];
fruits[5] = "Orange";
console.log(fruits);
// Output: ["Apple", "Banana", empty × 3, "Orange"]
console.log(fruits.length);  // Output: 6
```

---

## Part 20: Key Takeaways

### ✅ Remember These Points

1. **Arrays** store multiple values in one variable
2. **Index starts at 0** - first element is `arr[0]`
3. **length property** gives number of elements
4. **push()** adds to end, **pop()** removes from end
5. **unshift()** adds to start, **shift()** removes from start
6. **for loop** or **for...of** to iterate through arrays
7. **const arrays** can be modified but not reassigned
8. **indexOf()** finds position, **includes()** checks existence
9. **slice()** extracts without changing original
10. **splice()** adds/removes and changes original

### Array Methods Quick Reference

```javascript
const arr = ["A", "B", "C"];

// Add/Remove
arr.push("D");        // Add to end
arr.pop();            // Remove from end
arr.unshift("Z");     // Add to start
arr.shift();          // Remove from start

// Access
arr[0]                // First element
arr[arr.length - 1]   // Last element
arr.length            // Number of elements

// Search
arr.indexOf("B")      // Find position
arr.includes("B")     // Check if exists

// Transform
arr.join(", ")        // Array to string
arr.slice(1, 3)       // Extract part
arr.concat(arr2)      // Merge arrays
```

---

## What's Next?

In the next lesson, we'll learn about:

### Coming Up: JavaScript Day 17

- Advanced array methods
- Array iteration methods (forEach, map, filter, reduce)
- Working with nested arrays
- Array destructuring
- Practical array applications

---

*Congratulations! You've completed JavaScript Day 16. You now understand arrays in JavaScript!*

---

**Practice with arrays and see you in the next class!** 🚀
