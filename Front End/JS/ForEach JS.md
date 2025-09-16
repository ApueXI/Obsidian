---
Created: 2025-06-19T20:31
---
### What is `forEach`?

- `forEach` is an **array method** that executes a provided callback function once for **each element** in the array.
- It’s used to **iterate over arrays** in a clean, functional style.

  

### Syntax

```JavaScript
array.forEach(function(element, index, array) {
    // Your code here
});
```

- `element` — Current array element being processed (required).
- `index` — Index of the current element (optional).
- `array` — The original array (optional).

  

### Basic Example

```JavaScript
const fruits = ['apple', 'banana', 'cherry'];

fruits.forEach(function(fruit) {
    console.log(fruit);
});

// Output:
// apple
// banana
// cherry
```

  

### Using Arrow Function Syntax

```JavaScript
fruits.forEach(fruit => console.log(fruit));
```

  

### With Index

```JavaScript
fruits.forEach((fruit, index) => {
    console.log(`${index}: ${fruit}`);
});

// Output:
// 0: apple
// 1: banana
// 2: cherry
```

  

### Important Notes

- `forEach` **does not return a new array** (unlike `map`).
- It **always returns** `**undefined**`.
- You **cannot break or return early** from a `forEach` loop. Use a `for` loop or `some`/`every` if you need that.
- Good for **side effects** like logging or updating outside variables.

  

### Example: Using `forEach` with Callback

```JavaScript
function logFruit(fruit) {
    console.log('I like ' + fruit);
}

fruits.forEach(logFruit);
```

  

```JavaScript
let numbers = [1, 2, 3, 4, 5];

numbers.forEach(double);
numbers.forEach(display);

function double(elements, index, array) {
    array[index] = elements * 2;
}

function triple(elements, index, array) {
    array[index] = elements * 3;
}

function display(elements) {
    console.log(elements);
}
```

  

```JavaScript
let fruits = ["apple", "orange", "banana", "coConut"];

function display(elements) {
    console.log(elements);
}
function upperCase(elements, index, array) {
    array[index] = elements.toUpperCase();
}
function lowerCase(elements, index, array) {
    array[index] = elements.toLowerCase();
}

function capitalize(elements, index, array) {
    array[index] =
        elements.charAt(0).toUpperCase() + elements.slice(1).toLowerCase();
}

fruits.forEach(capitalize);
fruits.forEach(display);
```

```JavaScript
let nums = [2, 4, 6, 2, 10, 2];
nums.forEach((val, idx, arr) => {
    console.log(`Is ${val} equal to the first element?`, val === arr[0]);
});
```