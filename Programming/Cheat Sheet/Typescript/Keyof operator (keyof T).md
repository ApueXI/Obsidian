---
Created: 2025-11-30T15:08
tags:
  - Advance-Tpes
---
# `**keyof**` **Operator in TypeScript**

The `keyof` operator allows you to **obtain a union type of all property names of an object type**.

- Useful for **type-safe property access**, **generic constraints**, and **mapped types**.

---

## ✅ **1. Basic** `**keyof**` **Usage**

```TypeScript
interface User {
  id: number;
  name: string;
  email: string;
}

type UserKeys = keyof User;
// "id" | "name" | "email"

```

- `UserKeys` is a **union of all keys** of the `User` interface.
- Helps ensure **type-safe operations on object properties**.

---

## ✅ **2. Using** `**keyof**` **With Generics**

```TypeScript
function getProp<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const user = { id: 1, name: "Alice", email: "alice@example.com" };

const userName = getProp(user, "name"); // "Alice"
// const invalid = getProp(user, "age"); ❌ Error: "age" not in User

```

- `K extends keyof T` ensures **only valid keys** can be passed.
- Return type `T[K]` gives the **type of the property**.

---

## ✅ **3. Combining** `**keyof**` **With** `**typeof**`

```TypeScript
const person = { id: 1, name: "Bob", age: 30 };

type PersonKeys = keyof typeof person;
// "id" | "name" | "age"

```

- `typeof` converts **runtime variable** to **type**, then `keyof` extracts keys.
- Useful for **dynamic objects defined at runtime**.

---

## ✅ **4. Using** `**keyof**` **in Mapped Types**

```TypeScript
type ReadonlyProps<T> = {
  readonly [K in keyof T]: T[K];
};

interface User {
  id: number;
  name: string;
}

type ReadonlyUser = ReadonlyProps<User>;
// { readonly id: number; readonly name: string; }

```

- `keyof T` allows **iterating over all properties** of `T`.
- Enables **type-safe transformations** for generic objects.

---

## ✅ **5. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Basic `keyof`|`keyof T`|`keyof User` → "id"|Union of property names|
|Generic key constraint|`K extends keyof T`|`getProp<T,K extends keyof T>`|Ensure only valid keys|
|Access property type|`T[K]`|`getProp(user, "name"): string`|Type-safe property access|
|Combine with `typeof`|`keyof typeof obj`|`keyof typeof person` → "id"|Get keys of runtime objects|
|Mapped types|`[K in keyof T]: ...`|Make all props readonly|Iterate over properties|

---

**Rule of Thumb**:

- Use `keyof` to **extract keys from types** for **type-safe property access**.
- Combine with **generics** for **flexible and safe utility functions**.
- Works well with **mapped types and type transformations**.