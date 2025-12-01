---
Created: 2025-11-30T14:46
tags:
  - Funcions
---
# **Optional Parameters in TypeScript**

Optional parameters are parameters that **may or may not be passed** to a function.

- Declared with a **question mark** `**?**` after the parameter name.
- TypeScript treats them as **possibly** `**undefined**`.

---

## ✅ **1. Basic Syntax**

```TypeScript
function greet(name?: string) {
  console.log(`Hello, ${name || "Guest"}`);
}

greet();          // "Hello, Guest"
greet("Alice");   // "Hello, Alice"

```

- `name?: string` → optional parameter
- If not provided, TypeScript automatically considers it `undefined`.

---

## 🔹 **2. Optional Parameters Are Always Last**

Optional parameters **must come after required parameters**:

```TypeScript
function greet(greeting: string, name?: string) {
  console.log(`${greeting}, ${name || "Guest"}`);
}

// Correct
greet("Hi");           // "Hi, Guest"
greet("Hi", "Alice");  // "Hi, Alice"

// ❌ Wrong
function greet(name?: string, greeting: string) {} // Error

```

---

## 🔹 **3. TypeScript Infers** `**undefined**`

```TypeScript
function multiply(a: number, b?: number) {
  if (b === undefined) {
    return a * a;
  }
  return a * b;
}

multiply(5);    // 25
multiply(5, 2); // 10

```

- TypeScript treats `b` as `number | undefined`.
- You need to handle the `undefined` case if necessary.

---

## 🔹 **4. Optional Parameters vs Default Parameters**

Optional parameters can have **default values**, which are **used if the parameter is missing**:

```TypeScript
function greet(name: string = "Guest") {
  console.log(`Hello, ${name}`);
}

greet();        // "Hello, Guest"
greet("Alice"); // "Hello, Alice"

```

- With default values, TypeScript **does not consider the parameter** `**undefined**` inside the function.

---

## 🔹 **5. Multiple Optional Parameters**

You can have multiple optional parameters, but **all optional ones must follow required ones**:

```TypeScript
function buildUrl(protocol: string, domain?: string, path?: string) {
  return `${protocol}://${domain || "example.com"}/${path || ""}`;
}

buildUrl("https");               // "https://example.com/"
buildUrl("https", "mydomain");   // "https://mydomain/"
buildUrl("https", "mydomain", "home"); // "https://mydomain/home"

```

---

## 📋 **Optional Parameters Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Optional param|`b?: number`|`function f(a: number, b?: number)`|Must be last|
|Default value|`b: number = 5`|`function f(a: number, b: number = 5)`|Optional behavior with default|
|TypeScript type|`number|undefined`|`b?: number`|
|Multiple optional|`f(a: number, b?: number, c?: string)`|All optional params after required|Order matters|