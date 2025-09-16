---
Created: 2025-06-13T12:05
---
### **Convert to String**

|   |   |   |
|---|---|---|
|Method|Example|Result|
|`String()`|`String(123)`|`"123"`|
|`.toString()`|`(123).toString()`|`"123"`|

```JavaScript
let num = 100;
console.log(String(num));        // "100"
console.log((true).toString());  // "true"
```

  

### **Convert to Number**

|   |   |   |
|---|---|---|
|Method|Example|Result|
|`Number()`|`Number("123")`|`123`|
|`parseInt()`|`parseInt("123px")`|`123`|
|`parseFloat()`|`parseFloat("123.45px")`|`123.45`|

```JavaScript
console.log(Number("42"));       // 42
console.log(parseInt("5.99"));   // 5
console.log(parseFloat("5.99")); // 5.99
```

  

### **Convert to Boolean**

|   |   |
|---|---|
|Value|Boolean result|
|`""`, `0`, `null`, `undefined`, `NaN`, `false`|`false`|
|All others|`true`|

```JavaScript
console.log(Boolean("hello"));  // true
console.log(Boolean(0));        // false
console.log(Boolean([]));       // true (empty array is truthy)
```

  

### **Automatic Type Coercion (Beware!)**

```JavaScript
"5" + 1      // "51" (string + number = string)
"5" - 1      // 4    (converted to number)
true + 1     // 2    (true → 1)
false + "1"  // "false1"
```

  

### **Check Type with** `**typeof**`

```JavaScript
let x = "123";
console.log(typeof x); // "string"
x = Number(x);
console.log(typeof x); // "number"
```

  

### Tips

- Use `===` instead of `==` to avoid unexpected coercion.
- Wrap user input (from `prompt()`) with `Number()` or `parseInt()` if you're doing math.

  

```JavaScript
let age = Number(window.prompt(`How old are you: `))

age += 1;

console.log(age, typeof age)

let x = 'Pizza';
let y = 'Pizza';
let z = 'Pizza';

x = Number(x)
y = String(y)
z = Boolean(z)

console.log(x, typeof x)
console.log(y, typeof y)
console.log(z, typeof z)
```