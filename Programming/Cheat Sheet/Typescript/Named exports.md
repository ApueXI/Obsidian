---
Created: 2025-11-30T15:01
tags:
  - Modules
---
# **Named Exports in TypeScript**

Named exports allow you to **export multiple values from a module** with explicit names.

- Each export is **individually named**.
- Consumers of the module must import using the **same name** (or an alias).

---

## ✅ **1. Basic Named Export**

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

- You can export **variables, functions, classes, types, interfaces**.
- Multiple named exports can exist in a single module.

---

## ✅ **2. Importing Named Exports**

```TypeScript
// main.ts
import { PI, square, Circle } from "./utils";

console.log(PI);          // 3.14
console.log(square(5));   // 25
const c = new Circle(2);
console.log(c.radius);    // 2

```

- Must use **curly braces** `**{}**`.
- Names must **match exported names**.

---

## 🔹 **3. Renaming Named Exports**

```TypeScript
import { square as sq, PI as piValue } from "./utils";

console.log(sq(4));       // 16
console.log(piValue);     // 3.14

```

- Use `as` to **alias imports**.
- Useful to **avoid naming conflicts**.

---

## ✅ **4. Exporting All Together**

```TypeScript
const PI = 3.14;
function square(x: number) { return x * x; }
class Circle { constructor(public radius: number) {} }

export { PI, square, Circle };

```

- Alternative to **inline export**.
- Can be **organized at the bottom** of the file.

---

## ✅ **5. Re-exporting Named Exports**

```TypeScript
// index.ts
export { PI, square, Circle } from "./utils";

```

- Allows other modules to import from **one central entry point**.

```TypeScript
import { PI, Circle } from "./index";

```

- Keeps project structure **clean and maintainable**.

---

## 🔹 **6. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Inline named export|`export const x = 1`|`export function square()`|Export while declaring|
|Batch named export|`export { a, b, c }`|`export { PI, square, Circle }`|Useful for grouping exports|
|Import named export|`import { x } from './file'`|`import { PI } from './utils'`|Curly braces required|
|Rename on import|`import { x as y }`|`import { square as sq }`|Avoids conflicts|
|Re-export|`export { X } from './file'`|`export { PI, Circle } from './utils'`|Centralized module entry point|

---

**Rule of Thumb**:

- Use **named exports** when you want **multiple exports from a module**.
- Keep **names consistent** or alias them when needed.
- Combine with **re-exporting** for better modular organization.