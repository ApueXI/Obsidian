---
Created: 2025-11-30T14:46
tags:
  - Funcions
---
# **Default Parameters in TypeScript**

Default parameters allow you to **provide a fallback value** if a function parameter is **not passed**.

- Declared using `=` after the parameter name.
- Makes parameters **optional implicitly**, without using `?`.

---

## ✅ **1. Basic Syntax**

```TypeScript
function greet(name: string = "Guest") {
  console.log(`Hello, ${name}`);
}

greet();        // "Hello, Guest"
greet("Alice"); // "Hello, Alice"

```

- `name: string = "Guest"` → default value `"Guest"`
- If no argument is passed, TypeScript uses the default value.

---

## 🔹 **2. Multiple Parameters with Defaults**

```TypeScript
function buildUrl(protocol: string = "https", domain: string = "example.com", path: string = "") {
  return `${protocol}://${domain}/${path}`;
}

console.log(buildUrl());                        // "https://example.com/"
console.log(buildUrl("http", "mydomain"));     // "http://mydomain/"
console.log(buildUrl("http", "mydomain", "home")); // "http://mydomain/home"

```

- Default values are applied **only when the argument is missing**.

---

## 🔹 **3. Difference Between Optional and Default Parameters**

|Feature|Optional Parameter|Default Parameter|
|---|---|---|
|Syntax|`b?: number`|`b: number = 1`|
|Type inside function|`number|undefined`|
|Must handle undefined?|Yes|No|
|Can assign default?|Usually handled manually|Default value assigned automatically|

### Example

```TypeScript
function squareOptional(x: number, y?: number) {
  return x * (y ?? x);  // handle undefined
}

function squareDefault(x: number, y: number = x) {
  return x * y;          // safe, no undefined
}

```

---

## 🔹 **4. Expressions as Default Values**

Default values can be **expressions**:

```TypeScript
function randomPoint(max: number = 100) {
  return { x: Math.random() * max, y: Math.random() * max };
}

console.log(randomPoint());

```

- Default values are evaluated **at call time**, not at compile time.

---

## 🔹 **5. Default Parameters with Destructuring**

```TypeScript
function createUser({ name = "Guest", age = 18 } = {}) {
  console.log(name, age);
}

createUser();                     // Guest 18
createUser({ name: "Alice" });    // Alice 18

```

- You can provide defaults for **individual object properties**.

---

## 📋 **Default Parameters Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Basic default|`b: number = 1`|`function f(b: number = 1)`|Automatically used if param missing|
|Optional vs Default|`b?: number` vs `b: number = 1`|`?: undefined` vs default value|Default is safer inside function|
|Expression as default|`b: number = Math.random()`|Can calculate at runtime|Evaluated at call time|
|Object destructuring|`{name = "Guest", age = 18} = {}`|Default per property|Flexible API design|