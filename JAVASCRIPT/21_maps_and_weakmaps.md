# JavaScript Day 21: Maps and WeakMaps

## Introduction

A Map is a collection of key-value pairs where keys can be any data type. Unlike objects, Map keys can be numbers, objects, or any other type, not just strings.

**Think of a Map as a dictionary where you can look up values using any type of key.**

---

## Part 1: What is a Map?

### Map Definition

A Map is an object that stores collections of key-value pairs, similar to a dictionary in other programming languages.

### Map Characteristics

| Feature | Description |
|---------|-------------|
| Key Types | Keys can be any type (strings, numbers, objects) |
| Insertion Order | Remembers original insertion order |
| Size Property | Easy to get number of items with `size` |
| Performance | Optimized for frequent additions/removals |
| Iterable | Can use for...of loops and forEach |

### Visual: Map Structure

```
Map:
┌─────────┬─────────┐
│  Key    │  Value  │
├─────────┼─────────┤
│ "apple" │   500   │
│ "banana"│   300   │
│ "orange"│   200   │
└─────────┴─────────┘
```

---

## Part 2: Creating a Map

### Method 1: Empty Map, Add with set()

```javascript
// Create empty Map
const fruits = new Map();

// Add values
fruits.set("apples", 500);
fruits.set("bananas", 300);
fruits.set("oranges", 200);

console.log(fruits);
```

### Method 2: Pass Array to Constructor

```javascript
// Create Map from array
const fruits = new Map([
    ["apples", 500],
    ["bananas", 300],
    ["oranges", 200]
]);

console.log(fruits);
```

**Output:**
```
Map(3) {"apples" => 500, "bananas" => 300, "oranges" => 200}
```

---

## Part 3: Map Methods

### The set() Method

Add or update key-value pairs:

```javascript
const fruits = new Map();

// Add new entries
fruits.set("apples", 500);
fruits.set("bananas", 300);

// Update existing entry
fruits.set("apples", 600);

console.log(fruits.get("apples"));  // Output: 600
```

### The get() Method

Get the value of a key:

```javascript
const fruits = new Map([
    ["apples", 500],
    ["bananas", 300]
]);

console.log(fruits.get("apples"));   // Output: 500
console.log(fruits.get("bananas"));  // Output: 300
console.log(fruits.get("oranges"));  // Output: undefined
```

### The has() Method

Check if a key exists:

```javascript
const fruits = new Map([
    ["apples", 500],
    ["bananas", 300]
]);

console.log(fruits.has("apples"));   // Output: true
console.log(fruits.has("oranges"));  // Output: false
```

### The delete() Method

Remove a key-value pair:

```javascript
const fruits = new Map([
    ["apples", 500],
    ["bananas", 300],
    ["oranges", 200]
]);

fruits.delete("bananas");

console.log(fruits.has("bananas"));  // Output: false
console.log(fruits.size);            // Output: 2
```

### The clear() Method

Remove all entries:

```javascript
const fruits = new Map([
    ["apples", 500],
    ["bananas", 300]
]);

console.log(fruits.size);  // Output: 2

fruits.clear();

console.log(fruits.size);  // Output: 0
```

### The size Property

Get number of entries:

```javascript
const fruits = new Map([
    ["apples", 500],
    ["bananas", 300],
    ["oranges", 200]
]);

console.log(fruits.size);  // Output: 3
```

---

## Part 4: Map Methods Summary

### Complete Methods Table

| Method | Description | Returns |
|--------|-------------|---------|
| `set(key, value)` | Add/update entry | The Map |
| `get(key)` | Get value for key | Value or undefined |
| `has(key)` | Check if key exists | true/false |
| `delete(key)` | Remove entry | true/false |
| `clear()` | Remove all entries | undefined |
| `size` | Number of entries | Number |

---

## Part 5: Iterating Through Maps

### Method 1: for...of with entries()

```javascript
const fruits = new Map([
    ["apples", 500],
    ["bananas", 300],
    ["oranges", 200]
]);

for (const [key, value] of fruits.entries()) {
    console.log(key + " = " + value);
}
```

**Output:**
```
apples = 500
bananas = 300
oranges = 200
```

### Method 2: forEach()

```javascript
const fruits = new Map([
    ["apples", 500],
    ["bananas", 300]
]);

fruits.forEach(function(value, key) {
    console.log(key + " = " + value);
});
```

**Output:**
```
apples = 500
bananas = 300
```

### Method 3: keys()

```javascript
const fruits = new Map([
    ["apples", 500],
    ["bananas", 300]
]);

for (const key of fruits.keys()) {
    console.log(key);
}
```

**Output:**
```
apples
bananas
```

### Method 4: values()

```javascript
const fruits = new Map([
    ["apples", 500],
    ["bananas", 300]
]);

for (const value of fruits.values()) {
    console.log(value);
}
```

**Output:**
```
500
300
```

---

## Part 6: Objects as Keys

### Using Objects as Keys

One of Map's most powerful features is using objects as keys:

```javascript
// Create objects
const apples = {name: "Apples"};
const bananas = {name: "Bananas"};
const oranges = {name: "Oranges"};

// Create Map
const fruits = new Map();

// Use objects as keys
fruits.set(apples, 500);
fruits.set(bananas, 300);
fruits.set(oranges, 200);

console.log(fruits.get(apples));   // Output: 500
console.log(fruits.get(bananas));  // Output: 300
```

### Important: Key is Object, Not String

```javascript
const apples = {name: "Apples"};
const fruits = new Map();

fruits.set(apples, 500);

// Wrong ❌ - using string
console.log(fruits.get("apples"));  // Output: undefined

// Correct ✅ - using object
console.log(fruits.get(apples));    // Output: 500
```

### Visual: Objects as Keys

```
Object References as Keys:
┌──────────────┬─────────┐
│     Key      │  Value  │
├──────────────┼─────────┤
│ {name:"A"}   │   500   │ ← Object reference
│ {name:"B"}   │   300   │ ← Object reference
└──────────────┴─────────┘
```

---

## Part 7: Map vs Object

### Comparison Table

| Feature | Object | Map |
|---------|--------|-----|
| Key types | Strings/Symbols only | Any type |
| Key order | Not guaranteed | Insertion order |
| Size | Manual count | `size` property |
| Iteration | Not directly iterable | Directly iterable |
| Performance | Good for static data | Better for frequent changes |
| Default keys | Has prototype keys | No default keys |

### When to Use Map

✅ Use Map when:
- Keys are not strings
- Keys are unknown until runtime
- All keys are same type, all values are same type
- Need to iterate in insertion order
- Need frequent additions/deletions

### When to Use Object

✅ Use Object when:
- Keys are strings or symbols
- Working with JSON data
- Need to use object methods
- Simple key-value storage

---

## Part 8: Practical Map Examples

### Example 1: Count Occurrences

```javascript
const words = ["apple", "banana", "apple", "orange", "banana", "apple"];

const count = new Map();

for (const word of words) {
    if (count.has(word)) {
        count.set(word, count.get(word) + 1);
    } else {
        count.set(word, 1);
    }
}

console.log(count);
```

**Output:**
```
Map(3) {"apple" => 3, "banana" => 2, "orange" => 1}
```

### Example 2: Cache Function Results

```javascript
const cache = new Map();

function expensiveOperation(n) {
    // Check cache first
    if (cache.has(n)) {
        console.log("From cache");
        return cache.get(n);
    }
    
    // Calculate result
    console.log("Calculating...");
    const result = n * n;
    
    // Store in cache
    cache.set(n, result);
    return result;
}

console.log(expensiveOperation(5));  // Calculating... 25
console.log(expensiveOperation(5));  // From cache 25
```

### Example 3: Sum Map Values

```javascript
const fruits = new Map([
    ["apples", 500],
    ["bananas", 300],
    ["oranges", 200]
]);

let total = 0;
for (const value of fruits.values()) {
    total += value;
}

console.log("Total:", total);  // Output: Total: 1000
```

### Example 4: User Roles

```javascript
const userRoles = new Map();

const user1 = {id: 1, name: "John"};
const user2 = {id: 2, name: "Jane"};
const user3 = {id: 3, name: "Bob"};

userRoles.set(user1, "admin");
userRoles.set(user2, "editor");
userRoles.set(user3, "viewer");

console.log(userRoles.get(user1));  // Output: admin
console.log(userRoles.get(user2));  // Output: editor
```

---

## Part 9: Map Type Checking

### typeof Returns "object"

```javascript
const fruits = new Map();

console.log(typeof fruits);  // Output: object
```

### instanceof Returns true

```javascript
const fruits = new Map();

console.log(fruits instanceof Map);  // Output: true
```

---

## Part 10: WeakMap Introduction

### What is a WeakMap?

A WeakMap is similar to a Map, but:
- Keys must be objects (not primitives)
- Holds weak references (allows garbage collection)
- Not iterable (no loops)
- No size property
- Limited methods

### Creating a WeakMap

```javascript
// Create WeakMap
let myMap = new WeakMap();

// Create object
let myObj = {fname: "John", lname: "Doe"};

// Set value
myMap.set(myObj, "player");

// Get value
console.log(myMap.get(myObj));  // Output: player
```

---

## Part 11: WeakMap Methods

### WeakMap Methods

| Method | Description |
|--------|-------------|
| `set(key, value)` | Add/update entry |
| `get(key)` | Get value for key |
| `has(key)` | Check if key exists |
| `delete(key)` | Remove entry |

### Example: Basic Operations

```javascript
let myMap = new WeakMap();

let myObj = {fname: "John", lname: "Doe"};

// Set value
myMap.set(myObj, "secret data");

// Check if exists
console.log(myMap.has(myObj));  // Output: true

// Get value
console.log(myMap.get(myObj));  // Output: secret data

// Delete
myMap.delete(myObj);
console.log(myMap.has(myObj));  // Output: false
```

---

## Part 12: WeakMap Garbage Collection

### Weak References

WeakMap holds weak references. If an object has no other references, it gets garbage collected:

```javascript
let myMap = new WeakMap();

let myObj = {fname: "John", lname: "Doe"};

// Add to WeakMap
myMap.set(myObj, "secret");

// Remove reference
myObj = null;

// Now the object in myMap will be garbage collected
```

### Visual: Garbage Collection

```
Step 1: Object created
myObj → {fname: "John"}
         ↑
      myMap (weak reference)

Step 2: Remove strong reference
myObj = null
         
      myMap (weak reference only)

Step 3: Garbage collection
Object is removed from memory
Entry removed from myMap
```

---

## Part 13: WeakMap Use Cases

### Example 1: Track Visit Counts

```javascript
// Create WeakMap to store visit counts
const visitsCount = new WeakMap();

// Create visitor objects
const John = {name: "John", age: 40};
const Paul = {name: "Paul", age: 41};
const Ringo = {name: "Ringo", age: 42};

// Function to track visitors
function track(visitor) {
    let count = visitsCount.get(visitor) || 0;
    count++;
    visitsCount.set(visitor, count);
    console.log(`${visitor.name} has visited ${count} time(s)`);
}

track(Paul);   // Paul has visited 1 time(s)
track(Ringo);  // Ringo has visited 1 time(s)
track(Paul);   // Paul has visited 2 time(s)
track(Paul);   // Paul has visited 3 time(s)
```

### Example 2: Private Data Storage

```javascript
// Create WeakMap for private data
const privateData = new WeakMap();

class User {
    constructor(name, secret) {
        this.name = name;
        // Store secret in WeakMap
        privateData.set(this, {secret: secret});
    }
    
    getSecret() {
        return privateData.get(this).secret;
    }
}

const user1 = new User("John", "my-password-123");

console.log(user1.name);         // Output: John
console.log(user1.getSecret());  // Output: my-password-123
console.log(user1.secret);       // Output: undefined (private!)
```

### Example 3: DOM Node Metadata

```javascript
const nodeData = new WeakMap();

function attachData(element, data) {
    nodeData.set(element, data);
}

function getData(element) {
    return nodeData.get(element);
}

// Usage
const button = document.getElementById("myButton");
attachData(button, {clicks: 0, lastClicked: null});

// When button is removed from DOM, data is automatically cleaned up
```

---

## Part 14: WeakMap Limitations

### Keys Must Be Objects

```javascript
let myMap = new WeakMap();

// This works ✅
let obj = {name: "John"};
myMap.set(obj, "value");

// These fail ❌
myMap.set("string", "value");  // Error!
myMap.set(123, "value");       // Error!
myMap.set(true, "value");      // Error!
```

### Not Iterable

```javascript
let myMap = new WeakMap();
let obj1 = {name: "John"};
let obj2 = {name: "Jane"};

myMap.set(obj1, "value1");
myMap.set(obj2, "value2");

// Cannot iterate ❌
for (const [key, value] of myMap) {  // Error!
    console.log(key, value);
}

// Cannot use forEach ❌
myMap.forEach((value, key) => {  // Error!
    console.log(key, value);
});
```

### No size Property

```javascript
let myMap = new WeakMap();
let obj = {name: "John"};

myMap.set(obj, "value");

console.log(myMap.size);  // Output: undefined (no size property)
```

### No keys(), values(), entries()

```javascript
let myMap = new WeakMap();

// These don't exist ❌
myMap.keys();     // Error!
myMap.values();   // Error!
myMap.entries();  // Error!
```

---

## Part 15: Map vs WeakMap

### Comparison Table

| Feature | Map | WeakMap |
|---------|-----|---------|
| Key types | Any type | Objects only |
| References | Strong | Weak |
| Garbage collection | No | Yes |
| Iterable | Yes | No |
| size property | Yes | No |
| Methods | Many | Limited (set, get, has, delete) |
| Use case | General key-value storage | Private data, metadata |

### When to Use Map

✅ Use Map when:
- Need any type of keys
- Need to iterate through entries
- Need size property
- Want to keep all entries in memory

### When to Use WeakMap

✅ Use WeakMap when:
- Keys are objects only
- Want automatic garbage collection
- Storing private/metadata about objects
- Memory management is important

---

## Part 16: Map.groupBy() (ES2024)

### Grouping Array Elements

```javascript
// Create array
const fruits = [
    {name: "apples", quantity: 300},
    {name: "bananas", quantity: 500},
    {name: "oranges", quantity: 200},
    {name: "kiwi", quantity: 150}
];

// Callback function to group
function myCallback({quantity}) {
    return quantity > 200 ? "ok" : "low";
}

// Group by quantity
const result = Map.groupBy(fruits, myCallback);

console.log(result);
```

**Output:**
```
Map(2) {
  "ok" => [{name: "apples", quantity: 300}, {name: "bananas", quantity: 500}],
  "low" => [{name: "oranges", quantity: 200}, {name: "kiwi", quantity: 150}]
}
```

---

## Part 17: Common Mistakes

### Mistake 1: Using String Instead of Object Key

```javascript
const obj = {name: "Apple"};
const map = new Map();

map.set(obj, 500);

// Wrong ❌
console.log(map.get("obj"));  // undefined

// Correct ✅
console.log(map.get(obj));    // 500
```

### Mistake 2: Expecting WeakMap to be Iterable

```javascript
let myMap = new WeakMap();
let obj = {name: "John"};
myMap.set(obj, "value");

// Wrong ❌
for (const [key, value] of myMap) {  // Error!
    console.log(key, value);
}

// WeakMaps cannot be iterated
```

### Mistake 3: Using Primitives in WeakMap

```javascript
let myMap = new WeakMap();

// Wrong ❌
myMap.set("key", "value");  // Error!

// Correct ✅
let obj = {key: "key"};
myMap.set(obj, "value");
```

### Mistake 4: Forgetting Map is Iterable

```javascript
const map = new Map([
    ["a", 1],
    ["b", 2]
]);

// Don't do this ❌
const keys = [];
map.forEach((value, key) => {
    keys.push(key);
});

// Better ✅
const keys = [...map.keys()];
```

---

## Part 18: Converting Between Map and Object

### Object to Map

```javascript
const obj = {
    name: "John",
    age: 30,
    city: "New York"
};

// Convert to Map
const map = new Map(Object.entries(obj));

console.log(map);
```

**Output:**
```
Map(3) {"name" => "John", "age" => 30, "city" => "New York"}
```

### Map to Object

```javascript
const map = new Map([
    ["name", "John"],
    ["age", 30],
    ["city", "New York"]
]);

// Convert to Object
const obj = Object.fromEntries(map);

console.log(obj);
```

**Output:**
```
{name: "John", age: 30, city: "New York"}
```

---

## Part 19: Key Takeaways

### ✅ Remember These Points

1. **Map** stores key-value pairs with any key type
2. **Keys can be objects**, numbers, or any type
3. **Insertion order** is preserved
4. **size property** gives number of entries
5. **Maps are iterable** with for...of, forEach
6. **set()** adds/updates, **get()** retrieves values
7. **WeakMap** only accepts object keys
8. **WeakMap** allows garbage collection
9. **WeakMap** is not iterable
10. Use Map for general storage, WeakMap for private data

### Map Quick Reference

```javascript
// Create Map
const map = new Map([
    ["key1", "value1"],
    ["key2", "value2"]
]);

// Add/update
map.set("key3", "value3");

// Get value
map.get("key1");  // "value1"

// Check existence
map.has("key1");  // true

// Delete
map.delete("key1");

// Get size
map.size;  // 2

// Clear all
map.clear();

// Iterate
for (const [key, value] of map) {
    console.log(key, value);
}

// Use object as key
const obj = {id: 1};
map.set(obj, "value");
map.get(obj);  // "value"
```

### WeakMap Quick Reference

```javascript
// Create WeakMap
const weakMap = new WeakMap();

// Create object key
let obj = {name: "John"};

// Set value
weakMap.set(obj, "secret");

// Get value
weakMap.get(obj);  // "secret"

// Check existence
weakMap.has(obj);  // true

// Delete
weakMap.delete(obj);

// Note: Cannot iterate, no size property
// Keys must be objects
```

---

## What's Next?

In the next lesson, we'll learn about:

### Coming Up: JavaScript Day 22

- Advanced array methods (map, filter, reduce)
- Chaining array methods
- Array transformation techniques
- Practical data manipulation
- Performance considerations

---

*Congratulations! You've completed JavaScript Day 21. You now understand Maps and WeakMaps in JavaScript!*

---

**Practice with Maps and see you in the next class!** 🚀
