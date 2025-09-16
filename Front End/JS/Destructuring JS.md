---
Created: 2025-06-21T13:41
---
### **What Is Destructuring?**

Destructuring allows you to **unpack values** from arrays or objects into **individual variables**.

  

### **Object Destructuring**

```JavaScript
const person = { name: "Alice", age: 25 };

const { name, age } = person;
console.log(name); // "Alice"
console.log(age);  // 25
```

- Unpacks properties based on **matching key names**.

  

### **Renaming During Destructuring**

```JavaScript
const user = { id: 1, username: "bob" };

const { username: userName } = user;
console.log(userName); // "bob"
```

- `username` is renamed to `userName`.

  

### **Default Values**

```JavaScript
const { role = "guest" } = user;
console.log(role); // "guest" (if not present)
```

- Assigns fallback values if property is missing.

  

### **Array Destructuring**

```JavaScript
const colors = ["red", "green", "blue"];

const [first, second] = colors;
console.log(first);  // "red"
console.log(second); // "green"
```

- Uses **index position** instead of keys.

  

### **Skipping Elements**

```JavaScript
const [ , , third] = colors;
console.log(third); // "blue"
```

- Skip values by leaving empty commas.

  

### **Swapping Variables**

```JavaScript
let a = 1, b = 2;
[a, b] = [b, a];
console.log(a, b); // 2, 1
```

- Clean swap using array destructuring.

  

### **Nested Object Destructuring**

```JavaScript
const user = {
  name: "Charlie",
  address: {
    city: "Manila",
    zip: 1000
  }
};

const {
  address: { city, zip }
} = user;

console.log(city); // "Manila"
```

  

### **Function Parameter Destructuring**

```JavaScript
function greet({ name, age }) {
  return `Hello, ${name}. You are ${age}.`;
}

greet({ name: "Dana", age: 30 }); // "Hello, Dana. You are 30."
```

- Unpacks object **directly in function arguments**.

  

### **Rest with Destructuring**

```JavaScript
const { a, b, ...rest } = { a: 1, b: 2, c: 3, d: 4 };
console.log(rest); // { c: 3, d: 4 }

const [x, ...others] = [10, 20, 30];
console.log(others); // [20, 30]
```

- Collects remaining values with `...`.

  

### Summary Table

|   |   |   |
|---|---|---|
|Type|Syntax Example|Notes|
|Object|`{ name } = person`|Match by key name|
|Array|`[a, b] = arr`|Match by index|
|Rename|`{ x: myX }`|`x` becomes `myX`|
|Defaults|`{ z = 10 }`|Use if property is `undefined`|
|Nested|`{ a: { b } }`|Access deep properties|
|Swap|`[a, b] = [b, a]`|Swap values|
|Function args|`function({ x })`|Destructure in parameters|
|Rest|`{ ...rest }`, `[...others]`|Get leftover props/elements|

  

```JavaScript
const names = ["kiana", "mei", "bronya"];

[names[0], names[2]] = [names[2], names[0]];

names.forEach((param) => console.log(param));
```

  

```JavaScript
const names = ["kiana", "mei", "bronya", "seele"];

const [firstname, secondname, ...extraname] = names;

names.forEach((param) => console.log(param));
console.log(``);
console.log(firstname);
console.log(secondname);
console.log(extraname);
```

  

```JavaScript
const person1 = {
  fname: "Laren Jay",
  lname: "Acob",
  age: 19,
  isStudent: true,
};
const person2 = {
  fname: "Andy",
  lname: "Sarne",
  age: 30,
  isStudent: false,
};

function displayPerson({ fname, lname, age, isStudent }) {
  console.log(
    `First Name: ${fname}\nLast Name:  ${lname}\nAge:        ${age}\nJob:        ${isStudent}`
  );
}

displayPerson(person1);
displayPerson(person2);
```

  

```JavaScript
const person1 = {
  fname: "Laren Jay",
  lname: "Acob",
  age: 19,
  isStudent: true,
};
const person2 = {
  firstname: "Andy",
  lastname: "Sarne",
  ages: 30,
};

const { fname, lname, age, isStudent } = person1;
const { lastname, firstname, isStudents = false, ages } = person2;

console.log(fname);
console.log(lname);
console.log(age);
console.log(isStudent);
console.log(``);
console.log(firstname);
console.log(lastname);
console.log(ages);
console.log(isStudents);
```