# JavaScript Day 14: Objects - Complete Guide

## Introduction

Objects are one of the most important concepts in JavaScript. An object is a collection of related data and functions stored together.

**Think of objects like real-world things:**
- A car has properties (color, model) and actions (start, stop)
- A person has properties (name, age) and actions (walk, talk)

---

## Part 1: What is an Object?

### Object Definition

An object is a variable that can store multiple values as properties and functions as methods.

### Real-World Example: Car

```
Car Object
├── Properties (data)
│   ├── brand: "Toyota"
│   ├── model: "Camry"
│   ├── color: "Blue"
│   └── year: 2023
│
└── Methods (actions)
    ├── start()
    ├── drive()
    ├── brake()
    └── stop()
```

### Simple Object Example

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30
};
```

---

## Part 2: Creating Objects

### Method 1: Object Literal (Most Common)

```javascript
const car = {
    brand: "Toyota",
    model: "Camry",
    year: 2023
};
```

### Method 2: Multiple Lines (More Readable)

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30,
    city: "New York"
};
```

### Method 3: Empty Object, Add Later

```javascript
const person = {};

person.firstName = "John";
person.lastName = "Doe";
person.age = 30;
```

### Method 4: Using new Object() (Not Recommended)

```javascript
const person = new Object();
person.firstName = "John";
person.lastName = "Doe";
```

**Note:** Always use object literal `{}` - it's simpler and faster!

---

## Part 3: Object Properties

### What are Properties?

Properties are key-value pairs that store data in an object.

### Property Syntax

```javascript
const person = {
    firstName: "John",    // key: value
    lastName: "Doe",      // key: value
    age: 30               // key: value
};
```

### Visual: Object Structure

```
person Object
┌─────────────────────────────┐
│  firstName: "John"          │  ← Property
│  lastName: "Doe"            │  ← Property
│  age: 30                    │  ← Property
└─────────────────────────────┘
```

---

## Part 4: Accessing Properties

### Two Ways to Access Properties

| Method | Syntax | Example |
|--------|--------|---------|
| Dot Notation | `object.property` | `person.firstName` |
| Bracket Notation | `object["property"]` | `person["firstName"]` |

### Dot Notation (Preferred)

```javascript
const person = {
    firstName: "John",
    age: 30
};

console.log(person.firstName);  // Output: John
console.log(person.age);        // Output: 30
```

### Bracket Notation

```javascript
const person = {
    firstName: "John",
    age: 30
};

console.log(person["firstName"]);  // Output: John
console.log(person["age"]);        // Output: 30
```

### When to Use Bracket Notation

Use brackets when:
- Property name is in a variable
- Property name has spaces or special characters

```javascript
const person = {
    firstName: "John",
    "last name": "Doe"  // Has space
};

// Property in variable
let prop = "firstName";
console.log(person[prop]);  // Output: John

// Property with space
console.log(person["last name"]);  // Output: Doe
```

---

## Part 5: Modifying Properties

### Changing Property Values

```javascript
const person = {
    firstName: "John",
    age: 30
};

// Change age
person.age = 31;
console.log(person.age);  // Output: 31
```

### Adding New Properties

```javascript
const person = {
    firstName: "John",
    age: 30
};

// Add new property
person.city = "New York";
console.log(person.city);  // Output: New York
```

### Deleting Properties

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30
};

// Delete property
delete person.age;
console.log(person.age);  // Output: undefined
```

---

## Part 6: Object Methods

### What are Methods?

Methods are functions stored inside objects.

### Creating Methods

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    fullName: function() {
        return this.firstName + " " + this.lastName;
    }
};
```

### Calling Methods

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    fullName: function() {
        return this.firstName + " " + this.lastName;
    }
};

// Call method with ()
let name = person.fullName();
console.log(name);  // Output: John Doe
```

### Method vs Property

```javascript
const person = {
    firstName: "John",
    fullName: function() {
        return this.firstName;
    }
};

// Without () - returns function itself
console.log(person.fullName);
// Output: function() { return this.firstName; }

// With () - executes function
console.log(person.fullName());
// Output: John
```

---

## Part 7: The this Keyword

### What is this?

In an object method, `this` refers to the object itself.

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    fullName: function() {
        return this.firstName + " " + this.lastName;
    }
};
```

**Here, `this` = `person` object**

### Visual: this in Objects

```
person Object
┌─────────────────────────────────┐
│  firstName: "John"              │
│  lastName: "Doe"                │
│                                 │
│  fullName: function() {         │
│      return this.firstName      │ ← this = person
│             ↑                   │
│             └─ refers to person │
│  }                              │
└─────────────────────────────────┘
```

### Example: Using this

```javascript
const car = {
    brand: "Toyota",
    model: "Camry",
    getInfo: function() {
        return this.brand + " " + this.model;
    }
};

console.log(car.getInfo());  // Output: Toyota Camry
```

---

## Part 8: Nested Objects

### Objects Inside Objects

```javascript
const person = {
    firstName: "John",
    age: 30,
    address: {
        street: "123 Main St",
        city: "New York",
        country: "USA"
    }
};
```

### Accessing Nested Properties

```javascript
const person = {
    firstName: "John",
    address: {
        city: "New York"
    }
};

// Dot notation
console.log(person.address.city);  // Output: New York

// Bracket notation
console.log(person["address"]["city"]);  // Output: New York
```

### Visual: Nested Object Structure

```
person
├── firstName: "John"
├── age: 30
└── address (object)
    ├── street: "123 Main St"
    ├── city: "New York"
    └── country: "USA"
```

---

## Part 9: Checking if Property Exists

### Using the in Operator

```javascript
const person = {
    firstName: "John",
    age: 30
};

console.log("firstName" in person);  // Output: true
console.log("lastName" in person);   // Output: false
```

---

## Part 10: Looping Through Objects

### for...in Loop

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30
};

for (let key in person) {
    console.log(key + ": " + person[key]);
}
```

**Output:**
```
firstName: John
lastName: Doe
age: 30
```

### Important: Use Bracket Notation in Loops

```javascript
// Correct ✅
for (let key in person) {
    console.log(person[key]);
}

// Wrong ❌
for (let key in person) {
    console.log(person.key);  // undefined!
}
```

---

## Part 11: Object Methods - Built-in

### Object.keys()

Get all property names as an array:

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30
};

let keys = Object.keys(person);
console.log(keys);
// Output: ["firstName", "lastName", "age"]
```

### Object.values()

Get all property values as an array:

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30
};

let values = Object.values(person);
console.log(values);
// Output: ["John", "Doe", 30]
```

### Object.entries()

Get key-value pairs as arrays:

```javascript
const person = {
    firstName: "John",
    age: 30
};

let entries = Object.entries(person);
console.log(entries);
// Output: [["firstName", "John"], ["age", 30]]
```

---

## Part 12: Displaying Objects

### Problem: Direct Display

```javascript
const person = {
    firstName: "John",
    age: 30
};

console.log(person);
// Output: [object Object] (not helpful!)
```

### Solution 1: Display Individual Properties

```javascript
const person = {
    firstName: "John",
    age: 30,
    city: "New York"
};

let text = person.firstName + ", " + person.age + ", " + person.city;
console.log(text);
// Output: John, 30, New York
```

### Solution 2: JSON.stringify()

```javascript
const person = {
    firstName: "John",
    age: 30,
    city: "New York"
};

let text = JSON.stringify(person);
console.log(text);
// Output: {"firstName":"John","age":30,"city":"New York"}
```

### Solution 3: Loop Through Properties

```javascript
const person = {
    firstName: "John",
    age: 30,
    city: "New York"
};

let text = "";
for (let key in person) {
    text += person[key] + " ";
}
console.log(text);
// Output: John 30 New York
```

---

## Part 13: Object Constructor Functions

### What is a Constructor?

A constructor is a function that creates multiple objects of the same type.

### Creating a Constructor

```javascript
function Person(first, last, age) {
    this.firstName = first;
    this.lastName = last;
    this.age = age;
}
```

**Note:** Constructor names start with capital letter!

### Using Constructor

```javascript
function Person(first, last, age) {
    this.firstName = first;
    this.lastName = last;
    this.age = age;
}

// Create objects
const person1 = new Person("John", "Doe", 30);
const person2 = new Person("Jane", "Smith", 25);

console.log(person1.firstName);  // Output: John
console.log(person2.firstName);  // Output: Jane
```

### Adding Methods to Constructor

```javascript
function Person(first, last) {
    this.firstName = first;
    this.lastName = last;
    this.fullName = function() {
        return this.firstName + " " + this.lastName;
    };
}

const person = new Person("John", "Doe");
console.log(person.fullName());  // Output: John Doe
```

---

## Part 14: Practical Examples

### Example 1: Student Object

```javascript
const student = {
    name: "Alice",
    age: 20,
    grade: "A",
    subjects: ["Math", "Science", "English"],
    getInfo: function() {
        return this.name + " is " + this.age + " years old";
    }
};

console.log(student.getInfo());
// Output: Alice is 20 years old
```

### Example 2: Bank Account

```javascript
const account = {
    accountNumber: "12345",
    balance: 1000,
    deposit: function(amount) {
        this.balance = this.balance + amount;
        return "New balance: " + this.balance;
    },
    withdraw: function(amount) {
        if (amount <= this.balance) {
            this.balance = this.balance - amount;
            return "New balance: " + this.balance;
        }
        return "Insufficient funds";
    }
};

console.log(account.deposit(500));   // Output: New balance: 1500
console.log(account.withdraw(200));  // Output: New balance: 1300
```

### Example 3: Product Catalog

```javascript
const product = {
    name: "Laptop",
    price: 999,
    inStock: true,
    getPrice: function() {
        return "$" + this.price;
    },
    applyDiscount: function(percent) {
        this.price = this.price - (this.price * percent / 100);
        return this.getPrice();
    }
};

console.log(product.getPrice());        // Output: $999
console.log(product.applyDiscount(10)); // Output: $899.1
```

---

## Part 15: Common Mistakes

### Mistake 1: Forgetting this

```javascript
// Wrong ❌
const person = {
    firstName: "John",
    lastName: "Doe",
    fullName: function() {
        return firstName + " " + lastName;  // Error!
    }
};

// Correct ✅
const person = {
    firstName: "John",
    lastName: "Doe",
    fullName: function() {
        return this.firstName + " " + this.lastName;
    }
};
```

### Mistake 2: Forgetting () for Methods

```javascript
const person = {
    firstName: "John",
    greet: function() {
        return "Hello";
    }
};

// Wrong ❌
console.log(person.greet);  // Returns function, not result

// Correct ✅
console.log(person.greet());  // Returns "Hello"
```

### Mistake 3: Using Dot Notation in Loops

```javascript
const person = {
    firstName: "John",
    age: 30
};

// Wrong ❌
for (let key in person) {
    console.log(person.key);  // undefined
}

// Correct ✅
for (let key in person) {
    console.log(person[key]);  // Works!
}
```

---

## Part 16: Object vs Primitive

### Comparison Table

| Feature | Primitive | Object |
|---------|-----------|--------|
| Stores | Single value | Multiple values |
| Mutable | No | Yes |
| Example | `let x = 5` | `let obj = {x: 5}` |
| Type | string, number, boolean | object |

### Primitives

```javascript
let x = 5;
let y = x;
y = 10;

console.log(x);  // Output: 5 (unchanged)
console.log(y);  // Output: 10
```

### Objects (Reference Type)

```javascript
let obj1 = {value: 5};
let obj2 = obj1;
obj2.value = 10;

console.log(obj1.value);  // Output: 10 (changed!)
console.log(obj2.value);  // Output: 10
```

---

## Part 17: Key Takeaways

### ✅ Remember These Points

1. **Objects** store multiple values as properties
2. **Properties** are key-value pairs
3. **Methods** are functions inside objects
4. **this** refers to the object itself
5. **Dot notation** is preferred: `object.property`
6. **Bracket notation** for variables: `object[variable]`
7. **for...in loop** to iterate through properties
8. **Constructor functions** create multiple similar objects
9. **JSON.stringify()** converts object to string
10. Objects are **reference types**, not copied by value

### Object Syntax Summary

```javascript
// Create object
const person = {
    firstName: "John",
    age: 30,
    greet: function() {
        return "Hello " + this.firstName;
    }
};

// Access property
person.firstName
person["firstName"]

// Change property
person.age = 31;

// Add property
person.city = "New York";

// Delete property
delete person.age;

// Call method
person.greet();

// Loop through
for (let key in person) {
    console.log(person[key]);
}
```

---

## What's Next?

In the next lesson, we'll learn about:

### Coming Up: JavaScript Day 15

- Arrays introduction
- Creating and accessing arrays
- Array methods (push, pop, shift, unshift)
- Looping through arrays
- Array vs Objects

---

*Congratulations! You've completed JavaScript Day 14. You now understand objects in JavaScript!*

---

**Practice creating objects and see you in the next class!** 🚀
