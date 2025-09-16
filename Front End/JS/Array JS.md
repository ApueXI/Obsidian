---
Created: 2025-06-19T08:48
---
### What is an Array?

An **array** is a single variable that holds a **list of values** (elements).

```JavaScript
let fruits = ["apple", "banana", "cherry"];
```

  

## **Creating Arrays**

```JavaScript
let empty = []; // Empty array
let numbers = [1, 2, 3, 4]; // Number array
let mixed = [1, "hi", true]; // Mixed types
```

  

## **Accessing Elements**

```JavaScript
let colors = ["red", "green", "blue"];
console.log(colors[0]); // Output: "red"
console.log(colors[2]); // Output: "blue"
```

> ⚠ Index starts at 0, not 1.

  

## **Looping Through Arrays**

```JavaScript
let nums = [10, 20, 30];

for (let i = 0; i < nums.length; i++) {
  console.log(nums[i]);
}
```

  

## **Common Array Methods**

|   |   |   |
|---|---|---|
|Method|Description|Example|
|`push()`|Add to end|`arr.push("new")`|
|`pop()`|Remove from end|`arr.pop()`|
|`unshift()`|Add to beginning|`arr.unshift("first")`|
|`shift()`|Remove from beginning|`arr.shift()`|
|`length`|Count elements|`arr.length`|
|`includes()`|Check if value exists|`arr.includes("apple")`|
|`indexOf()`|Find position|`arr.indexOf("banana")`|
|`join()`|Combine to string|`arr.join(", ")`|
|`slice()`|Copy part of array|`arr.slice(1, 3)`|
|`splice()`|Add/remove elements at a position|`arr.splice(1, 2, "x", "y")`|
|`reverse()`|Reverse order|`arr.reverse()`|
|`sort()`|Sort alphabetically|`arr.sort()`|

  

## **Array Example**

```JavaScript
let arr = ["a", "b", "c"];
arr.push("d");        // ["a", "b", "c", "d"]
arr.shift();          // ["b", "c", "d"]
console.log(arr[1]);  // Output: "c"
```

  

## `**for...of**` **Loop (easy array loop)**

```JavaScript
let animals = ["cat", "dog", "bird"];
for (let animal of animals) {
  console.log(animal);
}
```

  

## **Array of Objects**

```JavaScript
let people = [
  { name: "Alice", age: 20 },
  { name: "Bob", age: 25 }
];

console.log(people[1].name); // Output: "Bob"
```

  

## **Check if Variable is Array**

```JavaScript
Array.isArray([1, 2, 3]); // ✅ true
Array.isArray("hello");   // ❌ false
```

  

```JavaScript
let fruits = ["apple", "orange", "banana"];

fruits.push("coconut");

fruits.pop();

fruits.unshift("mango");

fruits.shift();

let numoffruits = fruits.length;

let index = fruits.indexOf("apple");

for (let index = fruits.length - 1; index >= 0; index--) {
    console.log(fruits[index]);
}
for (let fruit in fruits) {
    console.log(fruit);
}
fruits = fruits.sort().reverse();
for (let fruit of fruits) {
    console.log(fruit);
}

console.log(numoffruits);
console.log(index);
```