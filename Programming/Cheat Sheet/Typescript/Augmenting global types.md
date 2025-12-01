---
Created: 2025-12-01T11:52
tags:
  - Extra-Advanced-Topics
---
# 🔵 TypeScript — **Augmenting Global Types**

---

## 1. **Full Explanation**

### **What Is Global Type Augmentation?**

- Global type augmentation is a way to **add or extend types of global objects** (like `Window`, `Document`, `Array`, etc.) in TypeScript.
- Useful for **custom properties, third-party libraries, or environment-specific globals**.
- Uses **declaration merging** with `**interface**` **augmentation** and `**declare global**`.

---

### **Why Use It**

1. Add **custom properties to global objects** safely.
2. Extend **built-in types** like `Array`, `Window`, or `Event`.
3. Provide **type safety** when interacting with JS code or libraries that modify globals.

---

### **Key Points**

- Must be in a **module context** (wrap in `export {}`) to avoid polluting global scope unintentionally.
- Use `declare global { ... }` to indicate **augmenting global scope**.
- Supports **interfaces, types, and modules**.

---

## 2. **How It Works**

### 1. **Augmenting** `**Window**`

```TypeScript
export {}; // ensures this file is a module

declare global {
  interface Window {
    API_KEY: string;
    myCustomFunction(): void;
  }
}

// Usage
window.API_KEY = "abc123";
window.myCustomFunction = () => console.log("Hello");
window.myCustomFunction(); // ✅ "Hello"

```

---

### 2. **Extending Built-in Types**

```TypeScript
export {};

declare global {
  interface Array<T> {
    first(): T | undefined;
  }
}

// Implementation
Array.prototype.first = function () {
  return this[0];
};

// Usage
const nums = [1, 2, 3];
console.log(nums.first()); // ✅ 1

```

---

### 3. **Adding Properties to** `**Document**`

```TypeScript
export {};

declare global {
  interface Document {
    myCustomData: string;
  }
}

document.myCustomData = "test";
console.log(document.myCustomData); // ✅ "test"

```

---

### 4. **Global Variable Declaration**

```TypeScript
export {};

declare global {
  var globalVar: number;
}

globalVar = 42;
console.log(globalVar); // ✅ 42

```

---

## 3. **Gotchas / Pitfalls**

1. Must **wrap in** `**export {}**` to make the file a module, otherwise `declare global` may fail.
2. **Augmentation affects all files** in the project → be careful to avoid conflicts.
3. Cannot **remove existing global properties**, only extend them.
4. For **third-party library augmentation**, check **library’s type definitions** first.

---

## 4. **Summary Table**

|Feature|Syntax|Notes|
|---|---|---|
|Global object|`declare global { interface Window { ... } }`|Extends runtime global objects|
|Built-in type|`interface Array<T> { ... }` inside `declare global`|Adds new methods/properties|
|Global variable|`declare global { var x: type; }`|Accessible in all files|
|Module wrapper|`export {};`|Required to make file a module context|
|Limitation|Cannot remove properties|Only extend existing types|

---

## 5. **Real-World Examples**

### **Example 1: Extending** `**Window**`

```TypeScript
export {};

declare global {
  interface Window {
    APP_VERSION: string;
  }
}

window.APP_VERSION = "1.0.0";
console.log(window.APP_VERSION); // ✅ "1.0.0"

```

### **Example 2: Extending** `**Array**`

```TypeScript
export {};

declare global {
  interface Array<T> {
    last(): T | undefined;
  }
}

Array.prototype.last = function () { return this[this.length - 1]; };

console.log([1, 2, 3].last()); // ✅ 3

```

### **Example 3: Global Variable**

```TypeScript
export {};

declare global {
  var ENV: "development" | "production";
}

ENV = "development";
console.log(ENV); // ✅ "development"

```

---

## 6. **Key Takeaways**

1. Use `declare global` to **augment global types** safely.
2. Useful for **custom properties, polyfills, or JS interop**.
3. Must ensure the file is a **module** with `export {}`.
4. All augmentations are **compile-time only** — runtime objects must exist.