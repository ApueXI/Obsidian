---
Created: 2025-11-30T14:42
tags:
  - Type-System
---
# **Union Types in TypeScript**

A **union type** lets a variable hold **multiple possible types**.

This makes your code flexible while still being type-safe.

The syntax:

```Plain
typeA | typeB | typeC

```

Means the value can be **any one** of those types.

Example:

```TypeScript
let value: number | string;

```

`value` can be either a number **or** a string.

---

# ✅ Why Union Types Matter

### ✔ They allow flexibility

Different kinds of data can be handled.

### ✔ They enforce safety

You must check which type you're actually working with before using it.

### ✔ They pair well with narrowing

(type checks inside `if`, `typeof`, etc.)

---

# ✅ Basic Example

```TypeScript
let id: number | string;

id = 42;       // OK
id = "user01"; // OK
id = true;     // ❌ Error

```

---

# 🧩 Using Narrowing With Unions

Before performing operations that only work for certain types, TypeScript forces you to check.

```TypeScript
function printId(id: number | string) {
  if (typeof id === "string") {
    console.log(id.toUpperCase()); // string methods OK
  } else {
    console.log(id.toFixed(2));    // number methods OK
  }
}

```

This makes union types safe instead of ambiguous.

---

# 🚀 Real-World Example: ID That Can Be a Number or String

```TypeScript
type UserID = number | string;

function getUser(id: UserID) {
  console.log("Fetching user:", id);
}

getUser(123);       // OK
getUser("admin01"); // OK

```

---

# 🔄 Union Types with Arrays

```TypeScript
let data: (number | string)[] = [1, "two", 3];

```

---

# 🔥 Union Types with Literal Types

Very common in config options:

```TypeScript
type Direction = "left" | "right" | "up" | "down";

```

This restricts a variable to allowed values only.

---

# ⚠️ Gotchas

### ❗ Methods must be type-safe

You cannot do:

```TypeScript
id.toUpperCase();  // ❌ Error if id might be a number

```

TypeScript forces you to **narrow**:

```TypeScript
if (typeof id === "string") {
  id.toUpperCase();  // OK
}

```

---

# 📌 Summary Table

|Feature|Meaning|Example|
|---|---|---|
|Union Type|Variable can be multiple types|`number|
|Narrowing|Checking type before use|`typeof id === "string"`|
|Flexible?|Yes|Accepts multiple input types|
|Safe?|Yes|Must narrow before unsafe operations|