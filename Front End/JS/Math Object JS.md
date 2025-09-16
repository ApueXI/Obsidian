---
Created: 2025-06-15T09:32
---
### **Common Methods**

|   |   |   |   |
|---|---|---|---|
|Method|Description|Example|Result|
|`Math.round(x)`|Rounds to nearest integer|`Math.round(4.6)`|`5`|
|`Math.floor(x)`|Rounds **down**|`Math.floor(4.9)`|`4`|
|`Math.ceil(x)`|Rounds **up**|`Math.ceil(4.1)`|`5`|
|`Math.trunc(x)`|Removes decimal part|`Math.trunc(4.9)`|`4`|
|`Math.abs(x)`|Absolute value|`Math.abs(-5)`|`5`|
|`Math.sqrt(x)`|Square root|`Math.sqrt(9)`|`3`|
|`Math.pow(x, y)`|Power (x raised to y)|`Math.pow(2, 3)`|`8`|
|`Math.max(a, b, ...)`|Max value|`Math.max(1, 5, 2)`|`5`|
|`Math.min(a, b, ...)`|Min value|`Math.min(1, 5, 2)`|`1`|
|`Math.random()`|Random float from `0` to `<1`|`Math.random()`|`0.53` (e.g.)|
|`Math.round(Math.random() * n)`|Random int `0` to `n`|`Math.round(Math.random() * 10)`|0–10|

  

### **Trigonometry**

```JavaScript
Math.sin(x);   // x in radians
Math.cos(x);
Math.tan(x);
Math.asin(x);
Math.acos(x);
Math.atan(x);
```

  

### **Useful Constants**

|   |   |
|---|---|
|Constant|Value|
|`Math.PI`|3.141592653589793|
|`Math.E`|2.718281828459045|
|`Math.SQRT2`|1.414213562...|
|`Math.LN2`|0.693... (ln 2)|

  

### **Random Integer Generator Example**

```JavaScript
// Random integer from 1 to 10
let rand = Math.floor(Math.random() * 10) + 1;
```

  

### Tips

- Always use `Math.floor()` with `Math.random()` to avoid going over the limit.
- Trig functions require radians, not degrees (convert with `deg * (Math.PI / 180)`).

  

```JavaScript
console.log(Math.E)
console.log(Math.PI)

let x = 3.21;
let a = 3.21;
let b = 3.21;
let c = 3.21
let d = 3.21
let e = 3.21
let y = 2;
let z;
let max = Math.max(x, y, a)
let min = Math.min(x, y, a)

z = Math.round(x)
b = Math.ceil(b)
a = Math.floor(a)
c = Math.trunc(c)
d = Math.pow(d, 2)
e = Math.log(e)

console.log(z)
console.log(a)
console.log(b)
console.log(c)
console.log(d)
console.log(e)
console.log(max)
console.log(min)
```