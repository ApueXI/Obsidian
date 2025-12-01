---
Created: 2025-11-30T15:08
tags:
  - Advance-Tpes
---
# **Indexed Access Types in TypeScript**

Indexed access types allow you to **retrieve the type of a property of an object type**.

- Often used with `keyof` for **type-safe property access**.
- Syntax: `T[K]` → type of property `K` in type `T`.

---

## ✅ **1. Basic Indexed Access Type**

```TypeScript
interface User {
  id: number;
  name: string;
  email: string;
}

type UserIdType = User["id"];     // number
type UserNameType = User["name"]; // string

```

- `T[K]` extracts the **type of the property K**.
- Useful for **reusing property types** in other types or functions.

---

## ✅ **2. Indexed Access With** `**keyof**`

```TypeScript
type UserKeys = keyof User; // "id" | "name" | "email"
type UserValue = User[UserKeys];
// number | string

```

- Combines `keyof` + indexed access for **union of all property types**.

---

## ✅ **3. Using Indexed Access in Generics**

```TypeScript
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const user: User = { id: 1, name: "Alice", email: "alice@example.com" };

const userName = getProperty(user, "name"); // string
const userId = getProperty(user, "id");     // number

```

- `T[K]` ensures **return type matches the property type**.
- Generic + `keyof` + `T[K]` = **fully type-safe property access**.

---

## ✅ **4. Nested Indexed Access**

```TypeScript
interface Company {
  name: string;
  owner: {
    id: number;
    name: string;
  };
}

type OwnerType = Company["owner"]; // { id: number; name: string; }
type OwnerIdType = Company["owner"]["id"]; // number

```

- Can **access nested property types** easily.

---

## ✅ **5. With Mapped Types**

```TypeScript
type OptionalProps<T> = {
  [K in keyof T]?: T[K];
};

type OptionalUser = OptionalProps<User>;
// { id?: number; name?: string; email?: string; }

```

- Indexed access types let **mapped types refer to original property types**.

---

## 🔹 **6. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Single property type|`T[K]`|`User["id"]` → number|Extract type of a property|
|All property types|`T[keyof T]`|`User[keyof User]` → number|Union of all property types|
|Generic usage|`T[K]` with `K extends keyof T`|`getProperty<T,K>(obj,key)`|Type-safe property access|
|Nested properties|`T[K1][K2]`|`Company["owner"]["id"]` → number|Access nested types|
|Mapped types|`[K in keyof T]: T[K]`|OptionalProps<T>|Iterate while preserving types|

---

**Rule of Thumb**:

- Use `T[K]` to **get the type of a property** from an object or interface.
- Works perfectly with `**keyof**`, **mapped types**, and **generics** for **flexible, type-safe code**.
- Ideal for **utility functions that depend on property types**.