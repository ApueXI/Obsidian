---
Created: 2025-06-18T08:49
---
### **What is** `**===**`**?**

- Checks **both value AND type** equality.
- No type coercion happens.
- Safer and recommended over `==` (loose equality).

  

### **Syntax**

```JavaScript
value1 === value2
```

Returns `true` only if **both values and types match exactly**.

### **Examples**

```JavaScript
5 === 5          // true (same number and type)
5 === '5'        // false (number vs string)
true === true    // true
true === 1       // false
null === null    // true
undefined === undefined // true
```

  

### **Why prefer** `**===**` **over** `**==**`**?**

- `==` does type coercion, which can cause unexpected results:

```JavaScript
5 == '5'         // true (because string '5' coerced to number)
0 == false       // true
null == undefined // true
```

- `===` avoids those pitfalls:

```JavaScript
5 === '5'        // false
0 === false      // false
null === undefined // false
```

  

### **Strict inequality**

```JavaScript
value1 !== value2
```

Returns `true` if values or types **do NOT match**.

  

```JavaScript
let PI = '3.14';

if (PI === 3.14) {
    console.log(`This is not an int PI`);
}
else{
    console.log(`This is a int PI`);
}
```