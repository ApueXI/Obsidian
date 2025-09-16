---
Created: 2025-06-22T13:08
---
### **Fisher-Yates Shuffle (Modern & Recommended)**

```JavaScript
function shuffle(array) {
  for (let i = array.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1)); // random index
    [array[i], array[j]] = [array[j], array[i]];   // swap elements
  }
  return array;
}

const nums = [1, 2, 3, 4, 5];
console.log(shuffle(nums)); // randomized order
```

- ✅ Random and **unbiased**.
- ✅ Works **in place** (modifies original array).

  

### **Non-mutating Shuffle (Keeps Original Array Intact)**

```JavaScript
function shuffledCopy(array) {
  return [...array].sort(() => Math.random() - 0.5);
}

const original = [1, 2, 3, 4, 5];
const result = shuffledCopy(original);

console.log(original); // stays the same
console.log(result);   // randomized
```

- ❗ This method is **not perfectly random**, but fine for **casual use**.
- Use **Fisher-Yates** for serious or large datasets.

  

### Summary Table

|   |   |   |
|---|---|---|
|Method|Code|Notes|
|Fisher-Yates (in-place)|`for (i → 0) { swap random }`|Best practice, unbiased|
|`.sort(() => Math.random())`|Simple and short|Not fully random, mutates or clone it|
|Copy then shuffle|`[...array]` then shuffle|Preserves original|

  

```JavaScript
function shuffle(array) {
    for (let index = array.length - 1; index > 0; index--) {
        const random = Math.floor(Math.random() * (index * 1));

        [array[index], array[random]] = [array[random], array[index]];
    }
    return array;
}

const cards = ["A", 2, 3, 4, 5, 6, 7, 8, 9, 10, "J", "Q", "K"];

shuffle(cards);

console.log(cards);
```