---
Created: 2025-06-20T15:31
---
### **Global Context**

```JavaScript
console.log(this); // In browsers: refers to `window`
```

- **Outside any function**, `this` refers to the **global object** (e.g., `window` in browsers, `global` in Node.js).

  

### **Inside a Regular Function**

```JavaScript
function show() {
  console.log(this);
}
show(); // In non-strict mode: `window` (global object)
// In strict mode: `undefined`
```

- **In functions**, `this` defaults to the global object (or `undefined` in strict mode).

  

### **Inside an Object Method**

```JavaScript
const user = {
  name: "Alice",
  greet() {
    console.log(this.name);
  }
};

user.greet(); // "Alice"
```

- `this` refers to the **object that called the method**.

  

### **Arrow Functions**

```JavaScript
const user = {
  name: "Bob",
  greet: () => {
    console.log(this.name);
  }
};

user.greet(); // `undefined` (or error)
```

- **Arrow functions don’t have their own** `**this**` — they inherit it from their outer (lexical) context.

  

### **Inside setTimeout / Callbacks**

```JavaScript
const obj = {
  value: 10,
  show() {
    setTimeout(function () {
      console.log(this.value); // undefined or global value
    }, 1000);
  }
};
obj.show();
```

- Regular function loses `this`.

**Fix it with arrow function:**

```JavaScript
setTimeout(() => {
  console.log(this.value); // Correctly logs 10
}, 1000);
```

  

### **Constructor Functions**

```JavaScript
function Person(name) {
  this.name = name;
}
const p = new Person("Charlie");
console.log(p.name); // "Charlie"
```

- When using `new`, `this` refers to the **newly created object**.

  

### `**call**`**,** `**apply**`**, and** `**bind**`

```JavaScript
function greet() {
  console.log(this.name);
}
const person = { name: "Dana" };

greet.call(person);  // "Dana"
greet.apply(person); // "Dana"
const bound = greet.bind(person);
bound();             // "Dana"
```

- These **manually set** `**this**`:
    - `call`: pass args one by one
    - `apply`: pass args as array
    - `bind`: returns a new function with `this` bound

  

### Summary Table

|   |   |
|---|---|
|Where `this` is used|What it refers to|
|Global scope|Global object (`window`, `global`)|
|Regular function|Global object or `undefined` (strict mode)|
|Object method|The object calling the method|
|Arrow function|Inherits `this` from outer scope|
|Constructor (`new`)|New instance object|
|`call(obj)` / `apply(obj)`|Object you passed in|
|`bind(obj)`|Object permanently bound as `this`|

  

```JavaScript
const person = {
    name: "Acob",
    food: "Fries",
    sayHello: function () {
        console.log(`Hello ${this.name}`);
    },
    sayEat: function () {
        console.log(`Im eating ${this.food}`);
    },
};

person.sayHello();
person.sayEat();
console.log(this);
```