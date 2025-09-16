---
Created: 2025-06-20T09:17
---
### What is `.filter()`?

- `.filter()` is an **array method** that creates a **new array** containing **only the elements that pass a test** (the callback returns `true`).
- It’s used for **filtering out unwanted elements**.

  

### Syntax

```JavaScript
const newArray = array.filter(function(element, index, array) {
    return condition; // true to keep, false to remove
});
```

- `element` — Current element (required)
- `index` — Index of the element (optional)
- `array` — The original array (optional)

  

### Basic Example

```JavaScript
const numbers = [1, 2, 3, 4, 5];

const evens = numbers.filter(num => num % 2 === 0);

console.log(evens); // [2, 4]
```

  

### Real-World Example

```JavaScript
const users = [
  { name: 'Alice', isAdmin: true },
  { name: 'Bob', isAdmin: false },
  { name: 'Carol', isAdmin: true }
];

const admins = users.filter(user => user.isAdmin);

console.log(admins);
// [
//   { name: 'Alice', isAdmin: true },
//   { name: 'Carol', isAdmin: true }
// ]
```

  

### Key Differences from `map` and `forEach`

|   |   |   |   |
|---|---|---|---|
|Feature|`forEach`|`map`|`filter`|
|Returns new array?|❌ No|✅ Yes|✅ Yes|
|Purpose|Side effects|Transform|Filter|
|Return value use|Ignored|Used|Used for condition|

  

### Summary

- `.filter()` returns a **new array**.
- Keeps only elements where the callback returns `true`.
- Original array is **not changed**.
- Useful for **searching, removing, or selecting items** from an array.

  

```JavaScript
let numbers = [1, 2, 3, 4, 5, 6, 7];
let evenNums = numbers.filter(isEven);

function isEven(params) {
    return params % 2 === 0;
}

console.log(evenNums);
```

  

```JavaScript
const ages = [19, 15, 19, 18, 60, 14];
const adult = ages.filter(isAdult);

function isAdult(params) {
    return params >= 18;
}

console.log(adult);
```

  

```JavaScript
const words = ["apple", "orange", "banana", "kiwi", "pomegranate", "coconut"];
const shortwords = words.filter(wordLength);

function wordLength(params) {
    return params.length <= 6;
}

console.log(shortwords);
```