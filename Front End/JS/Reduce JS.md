---
Created: 2025-06-20T10:27
---
### What is `.reduce()`?

- `.reduce()` is an **array method** that reduces the array to **a single value** by applying a **callback function** on each element **from left to right**.
- Useful for summing, multiplying, or accumulating data.

  

### Syntax

```JavaScript
const result = array.reduce(function(accumulator, currentValue, index, array) {
    return newAccumulator;
}, initialValue);
```

- `accumulator` — Result carried over from the previous iteration.
- `currentValue` — Current array item.
- `initialValue` — Starting value of the accumulator.

  

### Basic Example: Sum of Numbers

```JavaScript
const numbers = [1, 2, 3, 4];

const total = numbers.reduce((sum, num) => sum + num, 0);

console.log(total); // 10
```

  

### Example: Find Max

```JavaScript
const numbers = [4, 10, 7, 2];

const max = numbers.reduce((a, b) => (a > b ? a : b));

console.log(max); // 10
```

  

### Example: Group by Property

```JavaScript
const pets = [
  { type: 'dog', name: 'Fido' },
  { type: 'cat', name: 'Whiskers' },
  { type: 'dog', name: 'Rex' }
];

const grouped = pets.reduce((acc, pet) => {
    if (!acc[pet.type]) acc[pet.type] = [];
    acc[pet.type].push(pet.name);
    return acc;
}, {});

console.log(grouped);
// { dog: ['Fido', 'Rex'], cat: ['Whiskers'] }
```

  

### Key Points

- `.reduce()` is **powerful** but can be confusing at first.
- Great for:
    - Summing numbers
    - Flattening arrays
    - Grouping data
    - Counting items
- Does **not modify** the original array.
- Needs an **initial value** for safety.

  

### Summary Table

|   |   |   |
|---|---|---|
|Method|Returns|Best For|
|`forEach`|Nothing|Side effects (e.g. logging)|
|`map`|Array|Transforming values|
|`filter`|Array|Selecting elements|
|`reduce`|Any|Combining into one value|

  

```JavaScript
const prices = [5, 10, 15, 20, 25, 30];

const total = prices.reduce(sum);

function sum(accumuulator, element) {
    return accumuulator + element;
}

console.log(total.toFixed(2));
```

  

```JavaScript
const grades = [75, 50, 90, 80, 65, 95];

const maxValue = grades.reduce(getMax);

function getMax(params, next) {
    return Math.max(params, next);
}

console.log(maxValue);
```