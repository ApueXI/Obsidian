---
Created: 2025-11-30T15:00
tags:
  - Modules
---
# **Modules in TypeScript**

Modules allow you to **split code into reusable files** and **control scope**.

- Each file is a module if it **exports** or **imports** something.
- TypeScript uses **ES Module syntax** (`export` / `import`).

---

## ✅ **1. Exporting**

### **Named Exports**

```TypeScript
// utils.ts
export const PI = 3.14;

export function square(x: number): number {
  return x * x;
}

export class Circle {
  constructor(public radius: number) {}
}

```

- You can export **variables, functions, classes, interfaces, types**.
- Named exports must be imported **with the same name** (or aliased).

---

### **Default Export**

```TypeScript
// logger.ts
export default class Logger {
  log(message: string) {
    console.log("LOG:", message);
  }
}

```

- Default exports allow **one primary export per module**.
- Imported without curly braces.

---

## ✅ **2. Importing**

### **Import Named Exports**

```TypeScript
// main.ts
import { PI, square, Circle } from "./utils";

console.log(PI);           // 3.14
console.log(square(5));    // 25
const c = new Circle(2);
console.log(c.radius);     // 2

```

- Use curly braces `{}` for **named imports**.
- Can **rename** using `as`:

```TypeScript
import { square as sq } from "./utils";
console.log(sq(4)); // 16

```

---

### **Import Default Export**

```TypeScript
// main.ts
import Logger from "./logger";

const logger = new Logger();
logger.log("Hello!"); // LOG: Hello!

```

- Default export **does not use curly braces**.
- Name can be **anything** during import.

---

### **Import All as Namespace**

```TypeScript
import * as Utils from "./utils";

console.log(Utils.PI);          // 3.14
console.log(Utils.square(3));  // 9
const c = new Utils.Circle(5);

```

- Imports **all exports as a namespace object**.
- Useful for grouping utilities.

---

## ✅ **3. Re-exporting**

```TypeScript
// shapes.ts
export { Circle } from "./utils";
export { default as Logger } from "./logger";

```

- Allows **creating a single entry point** for multiple modules.
- Other files can import from **one consolidated module**.

---

## ✅ **4. Practical Use Case**

```TypeScript
// math.ts
export function add(a: number, b: number) { return a + b; }
export function sub(a: number, b: number) { return a - b; }

// index.ts
export * from "./math";

// app.ts
import { add, sub } from "./index";
console.log(add(2,3)); // 5
console.log(sub(5,2)); // 3

```

- Makes **module organization scalable**.

---

## 🔹 **5. Summary Table**

|Concept|Syntax|Example|Notes|
|---|---|---|---|
|Named export|`export const x = 1;`|`export function square()`|Must import with same name|
|Default export|`export default class Logger {}`|`import Logger from './logger'`|One per module, name flexible|
|Import named|`import { x } from './file'`|`import { PI, Circle } from './utils'`|Curly braces required|
|Import default|`import Name from './file'`|`import Logger from './logger'`|Curly braces **not used**|
|Import all as namespace|`import * as NS from './file'`|`NS.PI`|Groups all exports under object|
|Re-export|`export { X } from './file'`|`export * from './math'`|Consolidates modules|

---

**Rule of Thumb**:

- Use **named exports** for multiple values from a module.
- Use **default export** for the main class/function.
- Use **namespace imports or re-exports** for modular organization.