---
Created: 2025-06-20T11:40
---
### **Basic Arrow Function**

```JavaScript
const add = (a, b) => a + b;
```

- **Explanation:** Concise syntax for function expressions.
- Implicitly returns the result of `a + b` (no need for `return` keyword).

  

### **Arrow Function with Single Parameter**

```JavaScript
const square = x => x * x;
```

- **Explanation:** If there’s only one parameter, parentheses around the parameter list are optional.

  

### **Arrow Function with No Parameters**

```JavaScript
const greet = () => "Hello!";
```

- **Explanation:** Use empty parentheses if no parameters are needed.

  

### **Arrow Function with Block Body**

```JavaScript
const multiply = (a, b) => {
  const result = a * b;
  return result; // Must use explicit return here
};
```

- **Explanation:** When using `{}`, you must use `return` explicitly.

  

### **Returning Object Literal**

```JavaScript
const getUser = () => ({ name: "Alice", age: 25 });
```

- **Explanation:** Wrap the object in parentheses `()` to return an object literal implicitly.

  

### **Arrow Functions and** `**this**`

```JavaScript
const obj = {
  value: 42,
  getValue: function() {
    setTimeout(() => {
      console.log(this.value);
    }, 1000);
  }
};

obj.getValue(); // logs 42
```

- **Explanation:** Arrow functions don’t have their own `this`. They use the `this` from their surrounding scope, which is useful in callbacks.

  

### **No** `**arguments**` **Object**

```JavaScript
const fn = () => {
  console.log(arguments); // ReferenceError: arguments is not defined
};
```

- **Explanation:** Arrow functions do not have their own `arguments` object.

  

### Summary Table

|   |   |   |
|---|---|---|
|Syntax|Description|Notes|
|`(a, b) => a + b`|Concise body, implicit return|Single expression|
|`x => x * x`|Single parameter without parentheses|Parentheses optional for one param|
|`() => "Hello"`|No parameters|Empty parentheses needed|
|`(a, b) => { return a * b; }`|Block body, explicit return|Use braces `{}` and `return`|
|`() => ({ name: "Alice" })`|Returning object literal implicitly|Wrap object in parentheses|

  

```JavaScript
const hello = (name) => {
    return `Hello ${name}\n${name} is old`    
};

console.log(hello(`Bro Code`));
```

  

```JavaScript
const number = [1, 2, 3, 4, 5, 6];

const squares = number.map((element) => Math.pow(element, 2));
const cube = number.map((element) => Math.pow(element, 3));
const even = number.filter((param) => param % 2 === 0);
const total = number.reduce((param, next) => param + next);

console.log(squares);
console.log(cube);
console.log(even);
console.log(total);
```