---
Created: 2025-12-01T11:51
tags:
  - Extra-Advanced-Topics
---
# 🔵 TypeScript — **Ambient Modules**

---

## 1. **Full Explanation**

### **What Are Ambient Modules?**

- Ambient modules are a way to tell TypeScript about the **existence and types of modules** that are **imported from JavaScript or external libraries** but **do not have TypeScript type definitions**.
- They are **compile-time only** and use the `declare module "module-name"` syntax.
- Useful when integrating **plain JS libraries** into a TypeScript project.

---

### **Why Use Ambient Modules**

1. Provides **type safety** when importing JavaScript modules.
2. Allows **IntelliSense in editors** for JS libraries.
3. Avoids **compiler errors** like:
    
    ```Plain
    Cannot find module 'some-js-lib' or its corresponding type declarations.
    
    ```
    

---

### **Key Points**

- Declared in `**.d.ts**` **files** or at the top of a TS file.
- Supports:
    - **Functions**
    - **Variables**
    - **Classes**
    - **Interfaces**
    - **Type aliases**

---

## 2. **How It Works**

### 1. **Basic Ambient Module**

```TypeScript
// my-lib.d.ts
declare module "my-lib" {
  export function greet(name: string): void;
  export const version: string;
}

```

```TypeScript
import { greet, version } from "my-lib";

greet("Alice");       // ✅ TS knows types
console.log(version); // ✅ TS knows types

```

---

### 2. **Module with Default Export**

```TypeScript
declare module "awesome-lib" {
  export default function awesomeFn(input: string): number;
}

```

```TypeScript
import awesomeFn from "awesome-lib";

console.log(awesomeFn("hello")); // ✅ TS type-safe

```

---

### 3. **Module Exporting Types**

```TypeScript
declare module "user-lib" {
  export interface User { name: string; age: number; }
  export type ID = string | number;
}

```

```TypeScript
import { User, ID } from "user-lib";

const user: User = { name: "Alice", age: 30 };
const userId: ID = "abc123";

```

---

### 4. **Module with Classes**

```TypeScript
declare module "person-lib" {
  export class Person {
    name: string;
    constructor(name: string);
    greet(): void;
  }
}

```

```TypeScript
import { Person } from "person-lib";

const p = new Person("Bob");
p.greet();

```

---

## 3. **Gotchas / Pitfalls**

1. **Ambient module declarations are compile-time only** → no runtime JS is generated.
2. Must ensure **the actual module exists** at runtime.
3. Use `.d.ts` files for **cleaner project structure**, especially for multiple ambient modules.
4. Cannot mix **ambient module with actual implementation** in the same file.

---

## 4. **Summary Table**

|Feature|Syntax|Notes|
|---|---|---|
|Basic Module|`declare module "module-name" { ... }`|Type info only|
|Default Export|`export default function ...`|Use with `import x from "..."`|
|Named Exports|`export const/ function / class / interface`|Type-safe imports|
|Interface / Type|Inside module|Provides TS type info for JS|
|Classes|Inside module|TS knows shape of JS class|

---

## 5. **Real-World Examples**

### **Example 1: Basic Function Module**

```TypeScript
// math-lib.d.ts
declare module "math-lib" {
  export function add(a: number, b: number): number;
}

```

```TypeScript
import { add } from "math-lib";
console.log(add(2, 3)); // ✅ Type-checked

```

### **Example 2: Default Export Module**

```TypeScript
declare module "logger" {
  export default function log(msg: string): void;
}

```

```TypeScript
import log from "logger";
log("Hello"); // ✅ Type-checked

```

### **Example 3: Module Exporting Types**

```TypeScript
declare module "user-lib" {
  export interface User { name: string; age: number; }
  export type ID = string | number;
}

```

```TypeScript
import { User, ID } from "user-lib";

const u: User = { name: "Alice", age: 25 };
const id: ID = "abc123";

```

---

## 6. **Key Takeaways**

1. Ambient modules **declare external JS modules** to TypeScript.
2. Always use `**.d.ts**` **files** for organization and clarity.
3. TypeScript only provides **type safety**, no runtime code.
4. Essential for **JS library integration** and **avoiding TS compiler errors**.