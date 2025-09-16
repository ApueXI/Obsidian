---
Created: 2025-06-19T09:42
---
### What is it?

The **spread operator (**`**...**`**)** allows you to:

- **Expand** elements of an array or object
- **Copy** or **combine** arrays/objects
- Pass multiple arguments easily

  

## **Spread in Arrays**

### ✅ Copying an array

```JavaScript
let nums = [1, 2, 3];
let copy = [...nums];
console.log(copy); // [1, 2, 3]
```

### ✅ Merging arrays

```JavaScript
let a = [1, 2];
let b = [3, 4];
let combined = [...a, ...b];
console.log(combined); // [1, 2, 3, 4]
```

### ✅ Adding elements during merge

```JavaScript
let newArray = [0, ...a, 5];
console.log(newArray); // [0, 1, 2, 5]
```

  

## **Spread in Objects (ES2018+)**

### ✅ Copying an object

```JavaScript
let user = { name: "Alice", age: 25 };
let clone = { ...user };
console.log(clone); // { name: "Alice", age: 25 }
```

### ✅ Merging objects

```JavaScript
let a = { x: 1 };
let b = { y: 2 };
let merged = { ...a, ...b };
console.log(merged); // { x: 1, y: 2 }
```

> 📌 If keys conflict, last one wins:

```JavaScript
let obj = { x: 1, x: 2 }; // x will be 2
```

  

## **Spread in Function Arguments**

```JavaScript
function sum(a, b, c) {
  return a + b + c;
}

let nums = [1, 2, 3];
console.log(sum(...nums)); // 6
```

  

## Not to Confuse With: **Rest Parameter**

```JavaScript
function showAll(...args) {
  console.log(args);
}

showAll(1, 2, 3); // [1, 2, 3]
```

- **Spread**: Expands arrays/objects
- **Rest**: Collects multiple args into one array

  

## Summary Table

|   |   |   |
|---|---|---|
|Use Case|Syntax Example|Result|
|Copy array|`[...arr]`|New independent copy|
|Merge arrays|`[...arr1, ...arr2]`|Combined array|
|Copy object|`{...obj}`|New object|
|Merge objects|`{...obj1, ...obj2}`|Combined object|
|Function args|`func(...arr)`|Individual arguments passed|

  

```JavaScript
let fruits = ["apple", "orange", "banana"];
let vegetables = ["carrot", "celery", "potatoes"];

let foods = [...fruits, ...vegetables, "egg", "milk"];

console.log(foods);
```