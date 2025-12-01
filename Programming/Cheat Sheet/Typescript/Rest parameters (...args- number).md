---
Created: 2025-11-30T14:47
tags:
  - Funcions
---
# **Rest Parameters in TypeScript**

Rest parameters allow a function to **accept an arbitrary number of arguments** as an **array**.

- Declared using `...` before the parameter name.
- Must always be the **last parameter** in the function.

---

## ✅ **1. Basic Syntax**

```TypeScript
function sum(...numbers: number[]): number {
  return numbers.reduce((acc, curr) => acc + curr, 0);
}

console.log(sum(1, 2, 3));    // 6
console.log(sum(4, 5, 6, 7)); // 22

```

- `...numbers: number[]` → all remaining arguments are collected into an array.

---

## 🔹 **2. Rest Parameters With Other Parameters**

```TypeScript
function greet(greeting: string, ...names: string[]) {
  console.log(`${greeting} ${names.join(", ")}`);
}

greet("Hello");                 // "Hello "
greet("Hello", "Alice", "Bob"); // "Hello Alice, Bob"

```

- Only the **last parameter** can be a rest parameter.
- All preceding parameters are **regular, fixed parameters**.

---

## 🔹 **3. TypeScript Type Checking**

- TypeScript enforces the type of rest parameters:

```TypeScript
function multiply(...nums: number[]) {
  return nums.reduce((acc, val) => acc * val, 1);
}

multiply(2, 3, 4);       // OK
multiply(2, "3", 4);     // ❌ Error: "3" is not a number

```

---

## 🔹 **4. Combining Rest Parameters With Optional / Default Parameters**

```TypeScript
function buildName(first: string, last: string = "Doe", ...titles: string[]) {
  return `${first} ${last} ${titles.join(" ")}`;
}

console.log(buildName("John"));                     // "John Doe "
console.log(buildName("John", "Smith", "PhD"));    // "John Smith PhD"

```

- Default parameters can be used **before** the rest parameter.
- Rest parameter **collects all remaining arguments**.

---

## 🔹 **5. Real-World Example**

```TypeScript
function logMessages(level: "info" | "warn" | "error", ...messages: string[]) {
  messages.forEach(msg => console.log(`[${level}] ${msg}`));
}

logMessages("info", "Server started", "Listening on port 3000");
// [info] Server started
// [info] Listening on port 3000

```

- Perfect for **logging functions**, **event handlers**, or **utility functions** that need variable arguments.

---

## 📋 **Rest Parameters Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Basic rest param|`...args: number[]`|`function sum(...numbers: number[])`|Collects multiple arguments into an array|
|Must be last|`function f(a: number, ...rest: number[])`|OK|Only last param can use `...`|
|Type checked|`...nums: number[]`|`multiply(2, 3, 4)`|TS ensures type safety|
|Combined with defaults|`function f(a: number = 1, ...rest: number[])`|Optional defaults allowed|Default applies before rest|
|Practical use|Logging, calculations, event handlers|See `logMessages` example|Flexible API design|