---
Created: 2025-12-01T11:51
tags:
  - Extra-Advanced-Topics
---
### **What Are** `**.d.ts**` **Files?**

- `.d.ts` files are **TypeScript declaration files** that describe the **types of JavaScript code** without providing implementations.
- They are used to **type-check JS libraries or code** while keeping the JS runtime code untouched.
- These files are **purely for the TypeScript compiler**.

---

### **Why Use** `**.d.ts**` **Files**

1. Provide **type safety** when using **JavaScript libraries**.
2. Enable **IntelliSense in editors** like VS Code.
3. Allow **TypeScript code to interact with JS code safely**.
4. Avoid modifying **original JavaScript** when adding type definitions.

---

### **Key Points**

- `.d.ts` files contain **ambient declarations** (`declare`) for variables, functions, classes, modules, and namespaces.
- No actual **implementation code** should exist inside `.d.ts` files.
- Commonly used for:
    - Global variables and functions
    - Modules (`declare module`)
    - Interfaces and type aliases
    - Class types

---

## 2. **How to Write** `**.d.ts**` **Files**

### 1. **Global Variable / Function**

```TypeScript
// globals.d.ts
declare const API_KEY: string;
declare function greet(name: string): void;

```

- TypeScript compiler knows these exist **without runtime code**.

---

### 2. **Module Declaration**

```TypeScript
// my-library.d.ts
declare module "my-library" {
  export function doSomething(): void;
  export const version: string;
}

```

- Use this when importing a JS library without type definitions.

```TypeScript
import { doSomething, version } from "my-library";
doSomething();
console.log(version);

```

---

### 3. **Interface & Type Declaration**

```TypeScript
// types.d.ts
interface User {
  name: string;
  age: number;
}

type ID = string | number;

```

- Provides **type information** for objects or aliases in JS code.

---

### 4. **Class Declaration**

```TypeScript
// person.d.ts
declare class Person {
  name: string;
  constructor(name: string);
  greet(): void;
}

```

- TS knows about the **class structure** even if the implementation exists in JS.

---

### 5. **Namespace Declaration**

```TypeScript
// utils.d.ts
declare namespace Utils {
  function add(a: number, b: number): number;
  function subtract(a: number, b: number): number;
}

```

- Use when you have **global JS objects**.

---

## 3. **Gotchas / Pitfalls**

1. `.d.ts` files are **compile-time only** — no runtime code generated.
2. Must ensure **runtime object exists**, otherwise JS will throw errors.
3. Use `**declare**` **keyword** everywhere inside `.d.ts`.
4. Avoid implementing logic; `.d.ts` files **only describe types**.
5. `.d.ts` files **cannot contain** `**import**`**/**`**export**` **statements** in global context unless it’s a module declaration.

---

## 4. **Summary Table**

|Feature|Syntax in `.d.ts`|Notes|
|---|---|---|
|Global Variable|`declare const API_KEY: string;`|Must exist at runtime|
|Function|`declare function greet(name: string): void;`|Only type info|
|Class|`declare class Person { ... }`|Only structure, no implementation|
|Module|`declare module "mod" { ... }`|For external JS libraries|
|Namespace|`declare namespace NS { ... }`|Use with global JS objects|
|Interface / Type|`interface User { ... }` / `type ID = ...`|Describes object or alias shape|

---

## 5. **Real-World Example**

### **Example 1: Typing a JS Library**

```TypeScript
// math-lib.d.ts
declare module "math-lib" {
  export function add(a: number, b: number): number;
  export function multiply(a: number, b: number): number;
}

```

```TypeScript
import { add, multiply } from "math-lib";

console.log(add(2, 3));      // ✅ TypeScript knows types
console.log(multiply(4, 5)); // ✅ TypeScript knows types

```

### **Example 2: Global Variables**

```TypeScript
// globals.d.ts
declare const API_URL: string;
declare function log(message: string): void;

```

```TypeScript
console.log(API_URL); // ✅ TS knows it's a string
log("Hello World");   // ✅ TS knows it takes a string

```

### **Example 3: Class Declaration**

```TypeScript
// person.d.ts
declare class Person {
  name: string;
  constructor(name: string);
  greet(): void;
}

const p = new Person("Alice");
p.greet();

```

---

## 6. **Key Takeaways**

1. `.d.ts` files are **purely type information**, no runtime code.
2. Use `declare` to tell TypeScript about **existing JS code or libraries**.
3. Essential for **third-party JS integration** and **type safety**.
4. Combine with **ambient declarations** and **module/type declarations** for robust TS support.