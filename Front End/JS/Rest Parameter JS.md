---
Created: 2025-06-19T13:00
---
### What is it?

The **rest parameter** `...` allows a function to **collect multiple arguments into a single array**.

  

## **Basic Syntax**

```JavaScript
function myFunc(...args) {
  console.log(args);
}

myFunc(1, 2, 3); // Output: [1, 2, 3]
```

✅ `**args**` **becomes an array** of all arguments passed.

  

## **Collect Remaining Arguments**

```JavaScript
function greet(first, ...rest) {
  console.log("First:", first);
  console.log("Rest:", rest);
}

greet("Alice", "Bob", "Carol");

// Output:
// First: Alice
// Rest: ["Bob", "Carol"]
```

  

## **Using in Loops**

```JavaScript
function sumAll(...nums) {
  let total = 0;
  for (let num of nums) {
    total += num;
  }
  return total;
}

console.log(sumAll(1, 2, 3, 4)); // Output: 10
```

  

## **With Destructuring**

```JavaScript
const [first, ...others] = [10, 20, 30, 40];
console.log(first);  // 10
console.log(others); // [20, 30, 40]
```

  

## Rules for Rest Parameters

- Only **one rest parameter** is allowed.
- It **must be the last** parameter.

```JavaScript
// ❌ Invalid
// function wrong(...a, b) {}
```

  

## **Rest vs Spread**

|   |   |   |
|---|---|---|
|Feature|Rest Parameter|Spread Operator|
|Collects items|Yes (into an array)|No (spreads them out)|
|Used in|Function parameters|Function calls, arrays, objects|
|Example|`function(...args)`|`myFunc(...arr)`|

  

## Real-World Example

```JavaScript
function multiply(multiplier, ...numbers) {
  return numbers.map(n => n * multiplier);
}

console.log(multiply(2, 1, 2, 3)); // Output: [2, 4, 6]
```

  

```JavaScript
function combineString(...params) {
    return params.join(" ")
}

const fullname = combineString('Mr.', 'Bro' , 'Code', 'V')

console.log(fullname);
```