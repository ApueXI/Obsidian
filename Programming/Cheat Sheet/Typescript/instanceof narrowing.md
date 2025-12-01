---
Created: 2025-12-01T11:16
tags:
  - Type-Narrowing
---
# 🔵 TypeScript — `**instanceof**` **Narrowing Cheat Sheet**

---

# ✅ 1. Full Explanation

## **What is** `**instanceof**` **Narrowing?**

`instanceof` narrowing is a TypeScript technique that allows the compiler to **narrow a variable's type** based on a runtime `instanceof` check.

It is used to check whether a value was created from a **class** or **constructor function**.

---

## **Basic Syntax**

```TypeScript
if (value instanceof ClassName) {
  // value is now typed as ClassName
}

```

---

## **When to Use** `**instanceof**`

Use `instanceof` when you want to narrow based on:

- **Classes**
- **Built-in constructors**
    
    e.g. `Date`, `Error`, `RegExp`, `Array`, etc.
    
- **Custom classes / objects created with** `**new**`

---

## **How TypeScript Narrows Types**

If TypeScript knows a value is:

```TypeScript
string | Date

```

Then:

```TypeScript
if (value instanceof Date) {
  // Here: value is Date
} else {
  // Here: value is string
}

```

It removes all types from the union that are not instances of the class.

---

## **What** `**instanceof**` **Can Check**

|Type|Works with `instanceof`?|Example|
|---|---|---|
|Classes|✅ Yes|`x instanceof MyClass`|
|Built-in objects|✅ Yes|`x instanceof Date`|
|Functions|❌ No|Not meaningful|
|Interfaces|❌ No|Interfaces don’t exist at runtime|
|Type aliases|❌ No|Not runtime values|
|Literal types|❌ No|Not objects|

---

## **Gotchas / Pitfalls**

### ❗ 1. Cannot use with interfaces

Interfaces don’t exist at runtime.

```TypeScript
interface Cat {}
value instanceof Cat // ❌ invalid

```

---

### ❗ 2. Only works on **objects**, not primitives

```TypeScript
"hello" instanceof String  // false
5 instanceof Number        // false

```

---

### ❗ 3. Must reference a real constructor

```TypeScript
value instanceof undefined // ❌ invalid

```

---

### ❗ 4. Works best with classes using `new`

If something wasn’t created with `new`, `instanceof` fails.

---

### ❗ 5. Cross-realm issues (rare)

Values created in different JS contexts (iframes) may break `instanceof`.

---

# ✅ 2. Summary Table

|Check|Narrows To|Good For|Bad For|
|---|---|---|---|
|`value instanceof Class`|The specific class type|Classes, built-ins|Interfaces, primitives|
|`value instanceof Date`|`Date`|Date parsing, validation|Strings with date text|
|`value instanceof Error`|`Error`|Error handling|Error-like objects|
|`value instanceof Array`|Any[]|Arrays|Typed arrays, objects|

---

# ✅ 3. Real-World Example (Practical)

## **Scenario:**

You’re building an API handler that may return:

- a `string` (error message)
- a `Date` object
- a custom `User` instance

You need to process each differently.

---

### **Step 1: Define a class**

```TypeScript
class User {
  constructor(public id: number, public name: string) {}
}

```

---

### **Step 2: Create a function that receives mixed types**

```TypeScript
type ResponseType = string | Date | User;

```

---

### **Step 3: Narrow types using** `**instanceof**`

```TypeScript
function handleResponse(res: ResponseType) {
  if (res instanceof User) {
    return `User: ${res.name} (ID: ${res.id})`;
  }

  if (res instanceof Date) {
    return `Date: ${res.toISOString()}`;
  }

  // Only one type left: string
  return `Error: ${res.toUpperCase()}`;
}

```

### What TypeScript understands:

|Condition|Narrowed Type|
|---|---|
|`res instanceof User`|User|
|`res instanceof Date`|Date|
|else|string|

---

# 🔥 Bonus Real-World Example — Error handling

```TypeScript
function logError(err: unknown) {
  if (err instanceof Error) {
    console.error("Error:", err.message);
  } else {
    console.error("Unknown error:", err);
  }
}

```

Here:

- `instanceof Error` → narrows to `Error`
- else → narrows to everything else