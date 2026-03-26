# JavaScript Day 20: Sets and WeakSets

## Introduction

A Set is a collection of unique values. Each value can only appear once in a Set. Sets are useful when you need to store unique items without duplicates.

**Think of a Set as a bag that automatically removes duplicates.**

---

## Part 1: What is a Set?

### Set Definition

A Set is a collection where each value must be unique. If you try to add the same value twice, it will only be stored once.

### Key Characteristics

| Feature | Description |
|---------|-------------|
| Unique values | No duplicates allowed |
| Any type | Can store primitives or objects |
| Ordered | Maintains insertion order |
| Iterable | Can loop through values |

### Visual: Set vs Array

```
Array (allows duplicates):
["a", "b", "c", "a", "b"]
  ↓    ↓    ↓    ↓    ↓
All values stored

Set (unique only):
["a", "b", "c", "a", "b"]
  ↓    ↓    ↓    ✗    ✗
Only unique values: {"a", "b", "c"}
```

---

## Part 2: Creating a Set

### Method 1: From Array

```javascript
// Create Set from array
const letters = new Set(["a", "b", "c"]);

console.log(letters);  // Output: Set(3) {"a", "b", "c"}
```

### Method 2: Empty Set, Add Later

```javascript
// Create empty Set
const letters = new Set();

// Add values
letters.add("a");
letters.add("b");
letters.add("c");

console.log(letters);  // Output: Set(3) {"a", "b", "c"}
```

### Method 3: Add Variables

```javascript
// Create Set
const letters = new Set();

// Create variables
const a = "a";
const b = "b";
const c = "c";

// Add variables
letters.add(a);
letters.add(b);
letters.add(c);

console.log(letters);  // Output: Set(3) {"a", "b", "c"}
```

---

## Part 3: The add() Method

### Adding Values

```javascript
const letters = new Set();

letters.add("a");
letters.add("b");
letters.add("c");

console.log(letters);  // Output: Set(3) {"a", "b", "c"}
```

### Duplicates are Ignored

```javascript
const letters = new Set();

letters.add("a");
letters.add("b");
letters.add("c");
letters.add("c");  // Duplicate - ignored
letters.add("c");  // Duplicate - ignored
letters.add("c");  // Duplicate - ignored

console.log(letters);  // Output: Set(3) {"a", "b", "c"}
console.log(letters.size);  // Output: 3 (not 6!)
```

### Visual: Adding Duplicates

```
Adding to Set:
add("a") → Set: {"a"}
add("b") → Set: {"a", "b"}
add("c") → Set: {"a", "b", "c"}
add("c") → Set: {"a", "b", "c"}  ← No change!
add("c") → Set: {"a", "b", "c"}  ← No change!
```

---

## Part 4: Set Properties and Methods

### The size Property

```javascript
const letters = new Set(["a", "b", "c"]);

console.log(letters.size);  // Output: 3
```

### Common Set Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `add(value)` | Add a value | The Set |
| `delete(value)` | Remove a value | true/false |
| `has(value)` | Check if value exists | true/false |
| `clear()` | Remove all values | undefined |
| `size` | Number of values | Number |

---

## Part 5: The has() Method

### Check if Value Exists

```javascript
const letters = new Set(["a", "b", "c"]);

console.log(letters.has("a"));  // Output: true
console.log(letters.has("d"));  // Output: false
```

### Example: Checking Membership

```javascript
const fruits = new Set(["Apple", "Banana", "Orange"]);

if (fruits.has("Banana")) {
    console.log("We have bananas!");
} else {
    console.log("No bananas.");
}
```

**Output:**
```
We have bananas!
```

---

## Part 6: The delete() Method

### Remove a Value

```javascript
const letters = new Set(["a", "b", "c"]);

letters.delete("b");

console.log(letters);  // Output: Set(2) {"a", "c"}
```

### Returns true/false

```javascript
const letters = new Set(["a", "b", "c"]);

console.log(letters.delete("b"));  // Output: true (existed)
console.log(letters.delete("z"));  // Output: false (didn't exist)
```

---

## Part 7: The clear() Method

### Remove All Values

```javascript
const letters = new Set(["a", "b", "c"]);

console.log(letters.size);  // Output: 3

letters.clear();

console.log(letters.size);  // Output: 0
console.log(letters);       // Output: Set(0) {}
```

---

## Part 8: Iterating Through Sets

### Method 1: for...of Loop

```javascript
const letters = new Set(["a", "b", "c"]);

let text = "";
for (const x of letters) {
    text += x + " ";
}

console.log(text);  // Output: a b c
```

### Method 2: forEach()

```javascript
const letters = new Set(["a", "b", "c"]);

let text = "";
letters.forEach(function(value) {
    text += value + " ";
});

console.log(text);  // Output: a b c
```

### Method 3: values()

```javascript
const letters = new Set(["a", "b", "c"]);

const myIterator = letters.values();

let text = "";
for (const entry of myIterator) {
    text += entry + " ";
}

console.log(text);  // Output: a b c
```

---

## Part 9: Set Iterator Methods

### values() Method

Returns an iterator with all values:

```javascript
const letters = new Set(["a", "b", "c"]);

// Get iterator
const myIterator = letters.values();

// Loop through
for (const value of myIterator) {
    console.log(value);
}
```

**Output:**
```
a
b
c
```

### keys() Method

Sets don't have keys, but `keys()` returns the same as `values()` for compatibility with Maps:

```javascript
const letters = new Set(["a", "b", "c"]);

// keys() returns same as values()
for (const key of letters.keys()) {
    console.log(key);
}
```

**Output:**
```
a
b
c
```

### entries() Method

Returns `[value, value]` pairs (for Map compatibility):

```javascript
const letters = new Set(["a", "b", "c"]);

for (const entry of letters.entries()) {
    console.log(entry);
}
```

**Output:**
```
["a", "a"]
["b", "b"]
["c", "c"]
```

---

## Part 10: Practical Set Examples

### Example 1: Remove Duplicates from Array

```javascript
const numbers = [1, 2, 3, 2, 4, 3, 5, 1];

// Convert to Set (removes duplicates)
const uniqueNumbers = new Set(numbers);

// Convert back to array
const uniqueArray = [...uniqueNumbers];

console.log(uniqueArray);  // Output: [1, 2, 3, 4, 5]
```

### Example 2: Check Unique Values

```javascript
const emails = ["john@example.com", "jane@example.com", "john@example.com"];

const uniqueEmails = new Set(emails);

if (uniqueEmails.size === emails.length) {
    console.log("All emails are unique");
} else {
    console.log("Duplicate emails found");
}
```

**Output:**
```
Duplicate emails found
```

### Example 3: Track Unique Visitors

```javascript
const visitors = new Set();

// Add visitors
visitors.add("John");
visitors.add("Jane");
visitors.add("Bob");
visitors.add("John");  // Duplicate - ignored

console.log(`Total unique visitors: ${visitors.size}`);
```

**Output:**
```
Total unique visitors: 3
```

### Example 4: Set Operations (Union)

```javascript
const setA = new Set([1, 2, 3]);
const setB = new Set([3, 4, 5]);

// Union (combine both sets)
const union = new Set([...setA, ...setB]);

console.log(union);  // Output: Set(5) {1, 2, 3, 4, 5}
```

### Example 5: Set Operations (Intersection)

```javascript
const setA = new Set([1, 2, 3, 4]);
const setB = new Set([3, 4, 5, 6]);

// Intersection (common values)
const intersection = new Set(
    [...setA].filter(x => setB.has(x))
);

console.log(intersection);  // Output: Set(2) {3, 4}
```

---

## Part 11: Set vs Array

### Comparison Table

| Feature | Array | Set |
|---------|-------|-----|
| Duplicates | Allowed | Not allowed |
| Order | Indexed (0, 1, 2...) | Insertion order |
| Access | `arr[0]` | No index access |
| Check existence | `includes()` (slow) | `has()` (fast) |
| Add element | `push()` | `add()` |
| Remove element | `splice()` | `delete()` |

### When to Use Set

✅ Use Set when:
- You need unique values only
- You need fast existence checks
- You don't need index access

### When to Use Array

✅ Use Array when:
- Duplicates are allowed
- You need index access
- You need array methods (map, filter, etc.)

---

## Part 12: Set Type Checking

### typeof Returns "object"

```javascript
const letters = new Set(["a", "b", "c"]);

console.log(typeof letters);  // Output: object
```

### instanceof Returns true

```javascript
const letters = new Set(["a", "b", "c"]);

console.log(letters instanceof Set);  // Output: true
```

---

## Part 13: WeakSet Introduction

### What is a WeakSet?

A WeakSet is similar to a Set, but:
- Can only store objects (not primitives)
- Holds weak references (allows garbage collection)
- Not iterable (no loops)
- Limited methods

### Creating a WeakSet

```javascript
// Create WeakSet
let mySet = new WeakSet();

// Create object
let myObj = {fname: "John", lname: "Doe"};

// Add object
mySet.add(myObj);

// Check if exists
console.log(mySet.has(myObj));  // Output: true
```

---

## Part 14: WeakSet Methods

### WeakSet Methods

| Method | Description |
|--------|-------------|
| `add(object)` | Add an object |
| `delete(object)` | Remove an object |
| `has(object)` | Check if object exists |

### Example: Add and Delete

```javascript
let mySet = new WeakSet();

let myObj = {fname: "John", lname: "Doe"};

// Add object
mySet.add(myObj);
console.log(mySet.has(myObj));  // Output: true

// Delete object
mySet.delete(myObj);
console.log(mySet.has(myObj));  // Output: false
```

---

## Part 15: WeakSet Garbage Collection

### Weak References

WeakSet holds weak references. If an object has no other references, it gets garbage collected:

```javascript
let mySet = new WeakSet();

let myObj = {fname: "John", lname: "Doe"};

// Add to WeakSet
mySet.add(myObj);

// Remove reference
myObj = null;

// Now the object in mySet will be garbage collected
```

### Visual: Garbage Collection

```
Step 1: Object created
myObj → {fname: "John"}
         ↑
      mySet (weak reference)

Step 2: Remove strong reference
myObj = null
         
      mySet (weak reference only)

Step 3: Garbage collection
Object is removed from memory
mySet is now empty
```

---

## Part 16: WeakSet Use Cases

### Example: Track Visitors

```javascript
// Create WeakSet to track persons
const persons = new WeakSet();

// Visitor objects
const John = {name: "John", age: 40};
const Paul = {name: "Paul", age: 41};
const Ringo = {name: "Ringo", age: 42};

// Track visits
function track(visitor) {
    if (persons.has(visitor)) {
        console.log(visitor.name + " is visiting again.");
    } else {
        persons.add(visitor);
        console.log(visitor.name + " is visiting for the first time.");
    }
}

track(Paul);   // First time
track(Ringo);  // First time
track(Paul);   // Visiting again
```

**Output:**
```
Paul is visiting for the first time.
Ringo is visiting for the first time.
Paul is visiting again.
```

---

## Part 17: WeakSet Limitations

### Cannot Store Primitives

```javascript
let mySet = new WeakSet();

// This works ✅
let obj = {name: "John"};
mySet.add(obj);

// This fails ❌
mySet.add("string");  // Error!
mySet.add(123);       // Error!
mySet.add(true);      // Error!
```

### Not Iterable

```javascript
let mySet = new WeakSet();
let obj1 = {name: "John"};
let obj2 = {name: "Jane"};

mySet.add(obj1);
mySet.add(obj2);

// Cannot iterate ❌
for (const item of mySet) {  // Error!
    console.log(item);
}

// Cannot use forEach ❌
mySet.forEach(item => {  // Error!
    console.log(item);
});
```

### No size Property

```javascript
let mySet = new WeakSet();
let obj = {name: "John"};

mySet.add(obj);

console.log(mySet.size);  // Output: undefined (no size property)
```

---

## Part 18: Set vs WeakSet

### Comparison Table

| Feature | Set | WeakSet |
|---------|-----|---------|
| Value types | Any type | Objects only |
| References | Strong | Weak |
| Garbage collection | No | Yes |
| Iterable | Yes | No |
| size property | Yes | No |
| Methods | Many | Limited (add, delete, has) |

### When to Use Set

✅ Use Set when:
- You need to store any type of value
- You need to iterate through values
- You need the size property
- You want to keep values in memory

### When to Use WeakSet

✅ Use WeakSet when:
- You only need to store objects
- You want automatic garbage collection
- You're tracking objects temporarily
- Memory management is important

---

## Part 19: Common Mistakes

### Mistake 1: Expecting Index Access

```javascript
const letters = new Set(["a", "b", "c"]);

// Wrong ❌
console.log(letters[0]);  // Output: undefined

// Correct ✅
const arr = [...letters];
console.log(arr[0]);  // Output: a
```

### Mistake 2: Modifying During Iteration

```javascript
const numbers = new Set([1, 2, 3, 4, 5]);

// Be careful when modifying during iteration
for (const num of numbers) {
    if (num > 3) {
        numbers.delete(num);  // This works but be cautious
    }
}
```

### Mistake 3: Adding Primitives to WeakSet

```javascript
let mySet = new WeakSet();

// Wrong ❌
mySet.add("string");  // Error!

// Correct ✅
let obj = {value: "string"};
mySet.add(obj);
```

### Mistake 4: Expecting WeakSet to be Iterable

```javascript
let mySet = new WeakSet();
let obj = {name: "John"};
mySet.add(obj);

// Wrong ❌
for (const item of mySet) {  // Error!
    console.log(item);
}

// WeakSets cannot be iterated
```

---

## Part 20: Key Takeaways

### ✅ Remember These Points

1. **Set** stores unique values only
2. **Duplicates** are automatically removed
3. **add()** adds values, **delete()** removes values
4. **has()** checks if value exists (fast)
5. **size** property gives number of values
6. **Sets are iterable** with for...of, forEach
7. **WeakSet** only stores objects
8. **WeakSet** allows garbage collection
9. **WeakSet** is not iterable
10. Use Set for unique values, WeakSet for temporary object tracking

### Set Quick Reference

```javascript
// Create Set
const mySet = new Set([1, 2, 3]);

// Add values
mySet.add(4);

// Check existence
mySet.has(2);  // true

// Delete value
mySet.delete(2);

// Get size
mySet.size;  // 3

// Clear all
mySet.clear();

// Iterate
for (const value of mySet) {
    console.log(value);
}

// Remove duplicates from array
const unique = [...new Set([1, 2, 2, 3])];  // [1, 2, 3]
```

### WeakSet Quick Reference

```javascript
// Create WeakSet
const myWeakSet = new WeakSet();

// Create object
let obj = {name: "John"};

// Add object
myWeakSet.add(obj);

// Check existence
myWeakSet.has(obj);  // true

// Delete object
myWeakSet.delete(obj);

// Note: Cannot iterate, no size property
```

---

## What's Next?

In the next lesson, we'll learn about:

### Coming Up: JavaScript Day 21

- Maps and WeakMaps
- Key-value pairs
- Map methods and properties
- Map vs Object
- Practical Map applications

---

*Congratulations! You've completed JavaScript Day 20. You now understand Sets and WeakSets in JavaScript!*

---

**Practice with Sets and see you in the next class!** 🚀
