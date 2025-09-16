---
Created: 2025-06-23T15:15
---
### **What Are ES6 Modules?**

- ES6 modules let you **split code into multiple files**.
- Use `export` to expose values/functions/classes.
- Use `import` to bring them into another file.

  

### **Named Exports**

### ✅ `math.js`

```JavaScript
export const PI = 3.14;

export function add(a, b) {
  return a + b;
}
```

### ✅ `main.js`

```JavaScript
import { PI, add } from './math.js';

console.log(PI);         // 3.14
console.log(add(2, 3));  // 5
```

- Use `{}` to import specific names.
- Export multiple things.

  

### **Exporting in One Block**

```JavaScript
const PI = 3.14;
function subtract(a, b) {
  return a - b;
}

export { PI, subtract };
```

  

### **Renaming Imports or Exports**

```JavaScript
// math.js
export { subtract as minus };

// main.js
import { minus } from './math.js';
```

- Useful to avoid naming conflicts.

  

### **Default Export**

### ✅ `greet.js`

```JavaScript
export default function greet(name) {
  return `Hello, ${name}`;
}
```

### ✅ `main.js`

```JavaScript
import greet from './greet.js';

console.log(greet("Alice")); // "Hello, Alice"
```

- `default` = one value per file.
- Can use **any name** when importing a default export.

  

### **Mixing Default and Named Exports**

### ✅ `tools.js`

```JavaScript
export default function greet() {
  return "Hello!";
}

export const version = "1.0";
```

### ✅ `main.js`

```JavaScript
import greet, { version } from './tools.js';
```

  

### **Import Everything as an Object**

```JavaScript
import * as math from './math.js';

console.log(math.add(2, 3));
console.log(math.PI);
```

  

### **Important Notes**

- Modules **only work in modules-aware environments**:
    - In HTML: use `<script type="module">`
    - In Node.js: use `.mjs` or `"type": "module"` in `package.json`

  

  

```JavaScript
import { pi, circumference, area, volume } from "./ES6Modules_Util.js";

console.log(pi);
console.log(circumference(10).toFixed(2));
console.log(area(10).toFixed(2));
console.log(volume(10).toFixed(2));
```

```JavaScript
export const pi = 3.14159;

export function circumference(radius) {
    return 2 * pi * radius;
}

export function area(radius) {
    return pi * radius * radius;
}

export function volume(radius) {
    return 4 * pi * radius * radius;
}
```