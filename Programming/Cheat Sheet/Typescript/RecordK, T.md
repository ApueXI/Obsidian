---
Created: 2025-12-01T11:12
tags:
  - Utility-Types
---
# `**Record<K, T>**` **in TypeScript**

`Record<K, T>` creates a type where:

- `K` = **keys**
- `T` = **value type for all keys**

It is used to define **objects with a fixed set of keys** and **uniform value types**.

Think of it as:

> “An object whose keys are K and whose values are T.”

Internally:

```TypeScript
type Record<K extends keyof any, T> = {
  [P in K]: T;
};

```

---

## ✅ **1. Basic Example**

```TypeScript
type Scores = Record<string, number>;

const scores: Scores = {
  alice: 95,
  bob: 87,
};

```

Here:

- Keys = any `string`
- Values = `number`

---

## ✅ **2. Record with Specific Keys (Most Common)**

```TypeScript
type UserRoles = "admin" | "editor" | "viewer";

type Permissions = Record<UserRoles, boolean>;

const perms: Permissions = {
  admin: true,
  editor: false,
  viewer: true,
};

```

- All keys are required.
- You **cannot** add keys outside the union.

---

## ✅ **3. Record for Config Objects**

```TypeScript
type Theme = "light" | "dark";

const themeSettings: Record<Theme, { background: string; color: string }> = {
  light: { background: "\#fff", color: "#000" },
  dark: { background: "#000", color: "\#fff" }
};

```

- Each theme must have the same value structure.
- Helps maintain consistent config objects.

---

## ✅ **4. Record with Numbers as Keys**

```TypeScript
type Indexes = 1 | 2 | 3;

const items: Record<Indexes, string> = {
  1: "one",
  2: "two",
  3: "three"
};

```

Works for numeric unions as well.

---

## ✅ **5. Record vs. Index Signatures**

### **Record<K, T>**

- Keys are **specific and required**
- Can't have extra keys

```TypeScript
type UserInfo = Record<"name" | "email", string>;

```

### **Index Signature**

- Allows many arbitrary keys

```TypeScript
type StringMap = {
  [key: string]: string;
};

```

---

## ✅ **6. Real-World Example: Routing Table**

```TypeScript
type Route = "/home" | "/login" | "/profile";

type RouteHandlers = Record<Route, () => void>;

const handlers: RouteHandlers = {
  "/home": () => console.log("home"),
  "/login": () => console.log("login"),
  "/profile": () => console.log("profile")
};

```

- Guarantees that **every route has a handler**.
- Prevents missing or extra keys.

---

## ✅ **7. Summary Table**

|Feature|Description|Example|
|---|---|---|
|Uniform value type|All properties have the same type|`Record<string, number>`|
|Specific key union|Keys are limited & required|`Record<"a"|
|Works with objects|Values can be complex|`Record<Role, { access: boolean }>`|
|Prevents missing keys|Ensures all keys are present|Routing tables, config maps|
|Under the hood|Mapped type|`[P in K]: T`|

---

**Rule of Thumb**:

Use `**Record<K, T>**` when you want a **fully typed object** where every key has a **consistent value type** and **all keys are required**.