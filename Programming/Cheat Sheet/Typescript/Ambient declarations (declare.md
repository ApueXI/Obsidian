---
Created: 2025-12-01T11:50
tags:
  - Extra-Advanced-Topics
---
# 🔵 TypeScript — **Ambient Declarations (**`**declare**`**)**

---

## 1. **Full Explanation**

### **What Are Ambient Declarations?**

- Ambient declarations allow you to **tell TypeScript about variables, functions, classes, or modules that exist at runtime** but are **defined elsewhere** (e.g., in plain JavaScript, browser APIs, or external libraries).
- They **do not generate JavaScript code**; they are **compile-time only**.
- The keyword `**declare**` is used for this purpose.

---

### **Why Use** `**declare**`

1. TypeScript needs **type information** to check code that uses external code.
2. Avoid **compiler errors** when using variables or functions not defined in TypeScript.
3. Enable **type-safe interaction** with global objects, JS libraries, or external scripts.

---

### **Key Points**

- `declare` is **compile-time only** → no runtime output.
- Often used in `**.d.ts**` **files** (type declaration files).
- Can be used for:
    - **Variables**
    - **Functions**
    - **Classes**
    - **Modules**
    - **Namespaces**
    - **Enums**

---

## 2. **How It Works**

### 1. **Declaring a Global Variable**

```TypeScript
declare const API_KEY: string;

console.log(API_KEY); // ✅ TypeScript knows it’s a string

```

- `API_KEY` exists at runtime (maybe injected via `<script>`), TypeScript just knows its type.

---

### 2. **Declaring a Function**

```TypeScript
declare function greet(name: string): void;

greet("Alice"); // ✅ TypeScript type-safe

```

- Function exists at runtime (in JS), TS just checks arguments.

---

### 3. **Declaring a Class**

```TypeScript
declare class Person {
  name: string;
  constructor(name: string);
  greet(): void;
}

const p = new Person("Alice");
p.greet();

```

---

### 4. **Declaring a Module**

```TypeScript
declare module "my-library" {
  export function doSomething(): void;
  export const version: string;
}

```

- Allows TypeScript to type-check **imports from JS modules** without rewriting them in TS.

---

### 5. **Declaring a Namespace**

```TypeScript
declare namespace MathUtils {
  function add(a: number, b: number): number;
}

```

- Can use **existing JS global objects** safely in TS.

---

## 3. **Gotchas / Pitfalls**

1. `**declare**` **does not provide implementation**

```TypeScript
declare const x: number;
console.log(x); // ✅ Must exist at runtime

```

- If `x` does not exist in JS at runtime, it will **throw an error**.

1. **Use in** `**.d.ts**` **files for external libraries**

- Prevents polluting compiled JS.

1. **Ambient declarations are purely type-level**

- No runtime code is generated.

---

## 4. **Summary Table**

|Feature|Syntax|Notes|
|---|---|---|
|Variable|`declare const x: number;`|Must exist at runtime|
|Function|`declare function greet(name: string): void;`|TS type-safe, no JS emitted|
|Class|`declare class Person { ... }`|Type info only|
|Module|`declare module "mod" { ... }`|Type info for external JS module|
|Namespace|`declare namespace NS { ... }`|Use with global JS objects|
|File usage|`.d.ts` files|Common practice for ambient declarations|

---

## 5. **Real-World Examples**

### **Example 1: Global Variable**

```TypeScript
// index.html <script> defines API_KEY
declare const API_KEY: string;
console.log(API_KEY); // ✅ TypeScript knows it exists

```

### **Example 2: External JS Library**

```TypeScript
// external-library.js defines doSomething
declare function doSomething(): void;

doSomething(); // ✅ TypeScript type-checked

```

### **Example 3: Module Declaration**

```TypeScript
declare module "lodash" {
  export function chunk<T>(array: T[], size?: number): T[][];
}
import { chunk } from "lodash";

chunk([1,2,3,4], 2); // ✅ TS type-safe

```

---

## 6. **Key Takeaways**

1. `declare` is **compile-time only** → type info, no runtime output.
2. Ideal for **external JS, globals, libraries, and** `**.d.ts**` **files**.
3. Combine with TypeScript **type safety** for better integration with JavaScript code.
4. Remember: **runtime presence is required** — TypeScript will not create it for you.