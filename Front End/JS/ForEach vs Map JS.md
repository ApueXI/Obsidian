---
Created: 2025-06-20T09:09
---
### `forEach()`

**Purpose**:

Used to **iterate** over an array and perform **side effects** (e.g., logging, DOM updates).

**Returns**:

`undefined`

**Use Case**:

When you want to **do something** with each item (but not create a new array).

```JavaScript
const nums = [1, 2, 3];
nums.forEach(num => {
  console.log(num * 2);  // just logs
});
```

  

### `map()`

**Purpose**:

Used to **transform** each item in an array and return a **new array** with the results.

**Returns**:

A **new array** of the same length.

**Use Case**:

When you want to **create a new array** from existing one.

```JavaScript
const nums = [1, 2, 3];
const doubled = nums.map(num => num * 2);  // [2, 4, 6]
```

  

### Summary Table

|   |   |   |
|---|---|---|
|Feature|`forEach()`|`map()`|
|Return value|`undefined`|New transformed array|
|Mutates original|No|No|
|Chainable|No|Yes|
|Main purpose|Side effects|Data transformation|