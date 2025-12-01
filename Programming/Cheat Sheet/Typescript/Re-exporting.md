---
Created: 2025-11-30T15:02
tags:
  - Modules
---
# **Re-exporting in TypeScript**

Re-exporting allows a module to **export members from another module** without importing them first.

- Useful for creating **centralized entry points**.
- Helps **organize multiple modules** for easier imports.

---

## ✅ **1. Basic Re-export**

```TypeScript
// utils.ts
export const PI = 3.14;
export function square(x: number) { return x * x; }

// index.ts
export { PI, square } from "./utils";

```

```TypeScript
// main.ts
import { PI, square } from "./index";

console.log(PI);      // 3.14
console.log(square(5));// 25

```

- `index.ts` re-exports **PI** and **square** from `utils.ts`.
- Consumers **import from index.ts**, not individual modules.

---

## ✅ **2. Re-export Default Export**

```TypeScript
// logger.ts
export default class Logger {
  log(message: string) { console.log("LOG:", message); }
}

// index.ts
export { default as Logger } from "./logger";

```

```TypeScript
// main.ts
import { Logger } from "./index";

const logger = new Logger();
logger.log("Hello!"); // LOG: Hello!

```

- Default exports can be **renamed** during re-export.

---

## ✅ **3. Re-export Everything**

```TypeScript
// utils.ts
export const PI = 3.14;
export function square(x: number) { return x * x; }

// index.ts
export * from "./utils";

```

```TypeScript
// main.ts
import { PI, square } from "./index";

```

- `export * from './utils'` re-exports **all named exports**.
- Cannot directly re-export **default export** with syntax.

---

## ✅ **4. Combining Multiple Re-exports**

```TypeScript
// math.ts
export const add = (a: number, b: number) => a + b;
export const sub = (a: number, b: number) => a - b;

// string.ts
export const greet = (name: string) => `Hello, ${name}`;

// index.ts
export * from "./math";
export * from "./string";

```

```TypeScript
// app.ts
import { add, sub, greet } from "./index";

console.log(add(2,3)); // 5
console.log(greet("Alice")); // Hello, Alice

```

- Allows **one import source** for multiple modules.

---

## 🔹 **5. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Re-export named|`export { X } from './file'`|`export { PI, square } from './utils'`|Only specified members|
|Re-export default|`export { default as Name } from './file'`|`export { default as Logger } from './logger'`|Can rename default export|
|Re-export all|`export * from './file'`|`export * from './utils'`|Re-exports all named exports|
|Combine multiple|`export * from './file1'; export * from './file2';`|`index.ts` example|Single entry point for consumers|

---

**Rule of Thumb**:

- Use **re-exporting** to **create centralized module entry points**.
- Use `export *` for **all named exports**, and `export { default as X }` for **default exports**.
- Keeps your project **organized and easier to maintain**.