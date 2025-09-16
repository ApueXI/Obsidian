---
Created: 2025-06-20T11:40
---
### **Basic Function Expression**

```JavaScript
const greet = function(name) {
  return `Hello, ${name}!`;
};
```

- **Explanation:** A function assigned to a variable. It’s anonymous unless named explicitly.
- Can be called like `greet("Alice")`.

  

### **Named Function Expression**

```JavaScript
const factorial = function fact(n) {
  return n <= 1 ? 1 : n * fact(n - 1);
};
```

- **Explanation:** Function has a name (`fact`) inside the expression. Useful for recursion or debugging.
- Can be called via the variable `factorial(5)` but not `fact(5)` outside.

  

### **Immediately Invoked Function Expression (IIFE)**

```JavaScript
(function() {
  console.log("This runs immediately!");
})();
```

- **Explanation:** A function expression that runs right after it’s defined.
- Useful for creating private scopes.

  

### **Arrow Function Expression**

```JavaScript
const add = (a, b) => a + b;
```

- **Explanation:** Shorter syntax for writing functions.
- Implicit `return` if no braces `{}`.
- `this` behaves lexically (inherits from surrounding context).

  

### **Arrow Function with Block Body**

```JavaScript
const multiply = (a, b) => {
  const result = a * b;
  return result;
};
```

- **Explanation:** When you need multiple statements, use `{}` and `return`.

  

### **Function Expression with Default Parameters**

```JavaScript
const greet = function(name = "Guest") {
  return `Hello, ${name}!`;
};
```

- **Explanation:** Assigns default values if arguments are not passed.

  

### **Function Expression as Callback**

```JavaScript
setTimeout(function() {
  console.log("Executed after 1 second");
}, 1000);
```

- **Explanation:** Anonymous function passed as an argument, common in async operations.

  

### Summary Table

|   |   |   |
|---|---|---|
|Syntax|Description|Notes|
|`const f = function() {}`|Basic function expression|Anonymous or named|
|`(function(){})();`|IIFE|Runs immediately|
|`const f = () => {}`|Arrow function|Short syntax, lexical `this`|
|`const f = (a=1) => a * 2;`|Arrow with default params|Implicit return possible|
|`setTimeout(function(){}, 1000);`|Callback with function expression|Common async usage|

  

```JavaScript
const number = [1, 2, 3, 4, 5, 6];

const squares = number.map(function (params) {
    return Math.pow(params, 2);
});

const even = number.filter(function (params) {
    return params % 2 === 0;
});

const odd = number.filter(function (params) {
    return params % 2 !== 0;
});

const total = number.reduce(function (params, elem) {
    return params + elem;
});

console.log(squares);
console.log(even);
console.log(odd);
console.log(total);
```