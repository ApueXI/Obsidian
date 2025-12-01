---
Created: 2025-12-01T11:19
tags:
  - Compiler-Config
---
# 🔵 TypeScript — **Compiler Strict Mode Cheat Sheet**

---

# ✅ 1. Full Explanation

## **What is** `**strict**` **mode?**

`strict` mode is a **compiler option in TypeScript** that **enables a set of type-checking rules** to make your code safer and more predictable.

- When enabled, TypeScript will **catch more errors at compile time**.
- It essentially **turns on multiple strict type-checking flags** at once.

---

## **How to Enable**

In `tsconfig.json`:

```JSON
{
  "compilerOptions": {
    "strict": true}
}

```

This is equivalent to enabling the following **individual flags**:

|Flag|Behavior|
|---|---|
|`strictNullChecks`|Prevents `null` and `undefined` from being assigned to other types by default|
|`noImplicitAny`|Requires explicit type annotation if TS cannot infer `any`|
|`strictFunctionTypes`|Checks function type compatibility more rigorously|
|`strictBindCallApply`|Ensures `.bind()`, `.call()`, `.apply()` are used safely|
|`strictPropertyInitialization`|Ensures class properties are properly initialized in constructor|
|`noImplicitThis`|Requires explicit type for `this` in functions|
|`alwaysStrict`|Parses files in `strict mode` (JavaScript `use strict`)|
|`noUnusedLocals`|Reports unused local variables|
|`noUnusedParameters`|Reports unused function parameters|
|`noImplicitReturns`|Reports functions that do not return a value on all code paths|
|`noFallthroughCasesInSwitch`|Reports missing `break` statements in `switch` cases|

> Note: Some flags can also be enabled individually, but strict: true turns them all on.

---

## **Why It Matters**

- **Catches bugs early** at compile time
- Makes code **more maintainable**
- Forces **clear typing** and **better design practices**
- Highly recommended for **large projects**

---

## **Gotchas / Pitfalls**

1. Enabling `strict` may **break existing code** if there are implicit `any`s or uninitialized properties.
2. Some third-party libraries may not have strict typings — you may need to use `@types/...`.
3. You can override individual strict flags if needed:

```JSON
{
  "strict": true,
  "noImplicitAny": false}

```

1. `strictNullChecks` is usually the most impactful; it changes how `null` and `undefined` behave.

---

# ✅ 2. Summary Table

|Flag|Effect|Default with `strict: true`|
|---|---|---|
|`strictNullChecks`|`null`/`undefined` safety|ON|
|`noImplicitAny`|Must type all `any`|ON|
|`strictFunctionTypes`|Function type safety|ON|
|`strictBindCallApply`|Safe `.bind/.call/.apply`|ON|
|`strictPropertyInitialization`|Class property initialization|ON|
|`noImplicitThis`|Explicit `this` typing|ON|
|`alwaysStrict`|JS `use strict`|ON|
|`noUnusedLocals`|Report unused locals|ON|
|`noUnusedParameters`|Report unused parameters|ON|
|`noImplicitReturns`|Ensure all code paths return|ON|
|`noFallthroughCasesInSwitch`|Report switch fallthrough|ON|

---

# ✅ 3. Real-World Example (Practical)

### **Scenario:**

You have a class and a function without proper types:

```TypeScript
class User {
  name;
  age;
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}

function greet(user) {
  console.log("Hello " + user.name);
}

```

### **With** `**strict: true**`, TypeScript reports errors:

1. Class properties `name` and `age` are **not initialized** → `strictPropertyInitialization`
2. Function parameter `user` has **implicit** `**any**` → `noImplicitAny`

---

### **Fixing for strict mode:**

```TypeScript
class User {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

function greet(user: User) {
  console.log("Hello " + user.name);
}

```

✅ Now it compiles safely under strict mode.

---

# 🔥 Bonus — Real-World Impact

1. **Null safety**:

```TypeScript
let username: string;
// username.toUpperCase(); // Error: username might be undefined
username = "Alice";
console.log(username.toUpperCase()); // OK

```

1. **Function type safety**:

```TypeScript
type Fn = (x: number) => void;
let f: Fn = (y: string) => {}; // Error with strictFunctionTypes

```

- `strict` mode ensures **better type guarantees** for your app.