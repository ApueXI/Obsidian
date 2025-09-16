---
Created: 2025-06-22T09:54
---
### **What Is an Array of Objects?**

A **collection of multiple objects**, stored inside a single array.

```JavaScript
const users = [
  { id: 1, name: "Alice", age: 25 },
  { id: 2, name: "Bob", age: 30 },
  { id: 3, name: "Charlie", age: 22 }
];
```

  

### **Accessing an Object in the Array**

```JavaScript
console.log(users[0].name);  // "Alice"
console.log(users[1]["age"]); // 30
```

- Use **array index** + **object property**.

  

### **Looping Through the Array**

### `for...of`

```JavaScript
for (const user of users) {
  console.log(user.name);
}
```

### `.forEach()`

```JavaScript
users.forEach(user => {
  console.log(user.name);
});
```

  

### **Filtering the Array**

```JavaScript
const adults = users.filter(user => user.age >= 25);
console.log(adults); // Only Alice and Bob
```

- Returns a **new array** with matching items.

  

### **Finding a Single Object**

```JavaScript
const bob = users.find(user => user.name === "Bob");
console.log(bob); // { id: 2, name: "Bob", age: 30 }
```

- `.find()` returns the **first match**, or `undefined`.

  

### **Transforming Each Object**

```JavaScript
const names = users.map(user => user.name);
console.log(names); // ["Alice", "Bob", "Charlie"]
```

- `.map()` creates a **new array** from values.

  

### **Sorting the Array**

```JavaScript
const sortedByAge = [...users].sort((a, b) => a.age - b.age);
console.log(sortedByAge);
```

- Sorts in ascending order by age.
- Use `[...]` to **avoid mutating** the original array.

  

### **Modifying Objects in the Array**

```JavaScript
users[0].age = 26;
```

- You can directly change object properties by index.

  

### **Adding and Removing Objects**

```JavaScript
users.push({ id: 4, name: "Dana", age: 28 }); // Add to end
users.splice(1, 1); // Remove 1 item at index 1 (Bob)
```

  

### **Destructuring Inside a Loop**

```JavaScript
for (const { name, age } of users) {
  console.log(`${name} is ${age} years old.`);
}
```

  

### Summary Table

|   |   |   |
|---|---|---|
|Action|Code Example|Result|
|Access one object|`arr[0].prop`|Access property of first item|
|Loop all|`for (let obj of arr)`|Each object|
|Filter|`arr.filter(obj => ...)`|Subset array|
|Find|`arr.find(obj => ...)`|First match|
|Map|`arr.map(obj => obj.prop)`|Extracted values|
|Sort|`arr.sort((a, b) => ...)`|Ordered array|
|Modify|`arr[i].key = val`|Updates item|
|Add/Remove|`arr.push(obj)`, `arr.splice(i, 1)`|Adds/removes objects|

  

```JavaScript
const fruit = [
    { name: "apple", color: "red", calories: "95" },
    { name: "banana", color: "yellow", calories: "120" },
    { name: "coconut", color: "nrown", calories: "75" },
    { name: "kiwi", color: "green", calories: "40" },
    { name: "pineapple", color: "yellow", calories: "65" },
];

fruit.forEach((param, index) =>
    console.log(
        `Number  : ${index + 1}\nName:     ${param.name}\nColor:    ${
            param.color
        }\nCalories: ${param.calories}`
    )
);

console.log(``);

for (const fruits of fruit) {
    console.log(
        `Name:     ${fruits.name}\nColor:    ${fruits.color}\nCalories: ${fruits.calories}`
    );
}

console.log(``);

fruit.forEach((param, index, array) =>
    console.log(
        `Param: ${param.name}\nIndex: ${index}\nArray: ${array[0].name}`
    )
);
```

  

```JavaScript
const fruits = [
    { name: "apple", color: "red", calories: "95" },
    { name: "banana", color: "yellow", calories: "120" },
    { name: "coconut", color: "nrown", calories: "75" },
    { name: "kiwi", color: "green", calories: "40" },
    { name: "pineapple", color: "yellow", calories: "65" },
];

fruits.push({ name: "grapes", color: "purple", calories: 22 });
fruits.pop();
fruits.splice(1, 2);

console.log(fruits);
```

  

```JavaScript
const fruits = [
    { name: "apple", color: "red", calories: "95" },
    { name: "banana", color: "yellow", calories: "120" },
    { name: "coconut", color: "nrown", calories: "75" },
    { name: "kiwi", color: "green", calories: "40" },
    { name: "pineapple", color: "yellow", calories: "65" },
];

const fruitnames = fruits.map((fruits) => fruits.name);
const fruitcolor = fruits.map((fruits) => fruits.color);
const fruitcalories = fruits.map((fruits) => fruits.calories);

console.log(fruitnames);
console.log(fruitcolor);
console.log(fruitcalories);
```

  

```JavaScript
const fruits = [
    { name: "apple", color: "red", calories: "95" },
    { name: "banana", color: "yellow", calories: "120" },
    { name: "coconut", color: "nrown", calories: "75" },
    { name: "kiwi", color: "green", calories: "40" },
    { name: "pineapple", color: "yellow", calories: "65" },
];

const yellow = fruits.filter((param) => param.color == "yellow");
const lowcal = fruits.filter((param) => param.calories <= 50);

for (const colorss of yellow) {
    console.log(colorss);
}

lowcal.forEach((param) => console.log(param));
```

```JavaScript
const fruits = [
    { name: "apple", color: "red", calories: 95 },
    { name: "banana", color: "yellow", calories: 120 },
    { name: "coconut", color: "nrown", calories: 75 },
    { name: "kiwi", color: "green", calories: 40 },
    { name: "pineapple", color: "yellow", calories: 65 },
    { name: "grape", color: "purple", calories: 25 },
];

const maxcal = fruits.reduce((max, compare) =>
    max.calories > compare.calories ? max : compare
);

const mincal = fruits.reduce((max, compare) =>
    max.calories < compare.calories ? max : compare
);

fruits.forEach((param) =>
    console.log(`Name:     ${param.name}\nCalories: ${param.calories}`)
);

console.log(``);

console.log(
    `Name:     ${maxcal.name}\nColorL:   ${maxcal.color}\nCalories: ${maxcal.calories}`
);

console.log(``);

console.log(
    `Name:     ${mincal.name}\nColorL:   ${mincal.color}\nCalories: ${mincal.calories}`
);
```