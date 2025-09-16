---
Created: 2025-06-22T12:26
---
### Lexicographic(alphabet + numbers + symbols) order

  

### **Basic** `**.sort()**` **for Strings**

```JavaScript
const names = ["Charlie", "Alice", "Bob"];
names.sort();
console.log(names); // ["Alice", "Bob", "Charlie"]
```

- **Default sort** is **alphabetical (lexical)**.
- It converts elements to **strings** and sorts **by Unicode**.

  

### **Sort Numbers (ascending)**

```JavaScript
const numbers = [10, 1, 21, 2];
numbers.sort((a, b) => a - b);
console.log(numbers); // [1, 2, 10, 21]
```

- Default sort fails on numbers — use a **compare function**.

  

### **Sort Numbers (descending)**

```JavaScript
numbers.sort((a, b) => b - a);
console.log(numbers); // [21, 10, 2, 1]
```

  

### **Sort Array of Objects by Property**

### Ascending:

```JavaScript
const users = [
  { name: "Alice", age: 25 },
  { name: "Bob", age: 20 }
];

users.sort((a, b) => a.age - b.age);
// Result: Bob (20), then Alice (25)
```

### Descending:

```JavaScript
users.sort((a, b) => b.age - a.age);
```

  

### **Sort by String Property (Alphabetically)**

```JavaScript
users.sort((a, b) => a.name.localeCompare(b.name));
// "Alice" before "Bob"
```

- Use `localeCompare()` for **string sorting** that handles Unicode properly.

  

### **Sort by Multiple Conditions**

```JavaScript
users.sort((a, b) => {
  return a.age - b.age || a.name.localeCompare(b.name);
});
```

- First sort by `age`. If equal, sort by `name`.

  

### **Don't Mutate Original Array**

```JavaScript
const sorted = [...users].sort((a, b) => a.age - b.age);
```

- Use spread (`[...]`) to **copy the array** before sorting.

  

### **Reverse Order**

```JavaScript
names.reverse(); // Reverses array in-place
```

  

### Summary Table

|   |   |   |
|---|---|---|
|Task|Code Example|Notes|
|String sort|`arr.sort()`|Lexical order|
|Number sort (asc)|`arr.sort((a, b) => a - b)`|Ascending|
|Number sort (desc)|`arr.sort((a, b) => b - a)`|Descending|
|Object sort by number|`arr.sort((a, b) => a.age - b.age)`|Common in arrays of objects|
|Object sort by string|`a.name.localeCompare(b.name)`|Safer for string comparison|
|Multi-condition sort|`a.age - b.age||
|Avoid mutation|`[...arr].sort(...)`|Makes a copy|
|Reverse order|`arr.reverse()`|In-place reversal|

  

```JavaScript
const people = [
    { name: "Zamuelle", age: 19, gpa: 3.8 },
    { name: "Laren Jay Acob", age: 16, gpa: 3.0 },
    { name: "Patrick John Goco", age: 18, gpa: 3.6 },
    { name: "Andy SArne", age: 17, gpa: 3.2 },
];

people.sort((a, b) => a.gpa - b.gpa);

console.log(people);
```

  

```JavaScript
const people = [
    { name: "Zamuelle", age: 19, gpa: 3.8 },
    { name: "Laren Jay Acob", age: 16, gpa: 3.0 },
    { name: "Patrick John Goco", age: 18, gpa: 3.6 },
    { name: "Andy SArne", age: 17, gpa: 3.2 },
];

people.sort((a, b) => a.name.localeCompare(b.name));

console.log(people);
```