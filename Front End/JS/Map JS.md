---
Created: 2025-06-19T21:20
---
### What is `.map()`?

- `.map()` is an **array method** that creates a **new array** by applying a **callback function** to **each element** of the original array.
- It’s used for **transforming** data.

  

### Syntax

```JavaScript
const newArray = array.map(function(element, index, array) {
    // return transformed element
});
```

- `element` — Current element (required)
- `index` — Index of the element (optional)
- `array` — The original array (optional)

  

### Basic Example

```JavaScript
const numbers = [1, 2, 3];

const doubled = numbers.map(num => num * 2);

console.log(doubled); // [2, 4, 6]
```

  

### Using with Functions

```JavaScript
function square(n) {
    return n * n;
}

const result = numbers.map(square);

console.log(result); // [1, 4, 9]
```

---

### Key Differences from `forEach`

|   |   |   |
|---|---|---|
|Feature|`forEach`|`map`|
|Returns value?|❌ `undefined`|✅ New transformed array|
|Use case|Side effects|Transforming data|
|Chainable?|❌ Not chainable|✅ Chainable|

  

### Real-World Example

```JavaScript
const users = [
  { name: 'Alice', age: 25 },
  { name: 'Bob', age: 30 }
];

const names = users.map(user => user.name);
console.log(names); // ['Alice', 'Bob']
```

  

### Summary

- `.map()` **returns a new array** with modified values.
- Original array is **not modified**.
- Great for **data transformation**.

  

```JavaScript
const number = [1, 2, 3, 4, 5];

const squares = number.map(square);
const cubes = number.map(cube);

function square(params) {
    return Math.pow(params, 2);
}

function cube(params) {
    return Math.pow(params, 3);
}

console.log(number);
console.log(squares);
console.log(cubes);
```

  

```JavaScript
const students = ["acob", "andy", "goco", "zam"];
const upperstudents = students.map(upperCase);

function upperCase(params) {
    return params.toUpperCase();
}

console.log(students);
console.log(upperstudents);
```

  

```JavaScript
const dates = ["2024-10-1", "2021-3-25", "2016-4-17"];
const formattedDates = dates.map(formatDate);

function formatDate(params) {
    const parts = params.split("-");
    return `${parts[1]}/${parts[2]}/${parts[0]}`;
}

console.log(formattedDates);
```