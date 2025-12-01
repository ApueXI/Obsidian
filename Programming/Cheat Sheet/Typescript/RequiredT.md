---
Created: 2025-11-30T15:12
tags:
  - Utility-Types
---
# `**Required<T>**` **in TypeScript**

The `Required<T>` utility type **makes all properties of a type required**.

- Useful for **ensuring full objects are provided**.
- Opposite of `Partial<T>`.
- Internally, it is a **mapped type**: `[P in keyof T]-?: T[P]`.

---

## ✅ **1. Basic Example**

```TypeScript
interface User {
  id?: number;
  name?: string;
  email?: string;
}

type FullUser = Required<User>;

const user: FullUser = {
  id: 1,
  name: "Alice",
  email: "alice@example.com"
};

// ❌ Missing any property → Compile-time error
// const invalidUser: FullUser = { id: 1 }; // Error

```

- All properties are **now mandatory** in `FullUser`.
- Prevents **partially defined objects**.

---

## ✅ **2. With Functions**

```TypeScript
function createUser(user: Required<User>) {
  console.log(user.id, user.name, user.email);
}

// ✅ All fields required
createUser({ id: 1, name: "Bob", email: "bob@example.com" });

// ❌ Missing fields → Error
// createUser({ id: 1, name: "Bob" });

```

- Ensures **function receives complete objects**.

---

## ✅ **3. Nested Objects**

```TypeScript
interface Profile {
  username?: string;
  settings?: {
    theme?: string;
    notifications?: boolean;
  };
}

type FullProfile = Required<Profile>;

const profile: FullProfile = {
  username: "alice",
  settings: { theme: "dark", notifications: true }
};

// ❌ Missing top-level or nested properties → Error

```

- **Top-level properties** become required.
- Nested objects are **not deeply affected**; deep required needs a custom type.

---

## ✅ **4. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Make all properties required|`Required<T>`|`Required<User>`|All optional fields become mandatory|
|Function arguments|`Required<T>`|`createUser(user)`|Ensures full object is passed|
|Nested objects|`Required<T>`|Only top-level required|Deep required requires custom type|
|Under the hood|`[P in keyof T]-?: T[P]`|Mapped type|Shows how TypeScript implements it|

---

**Rule of Thumb**:

- Use `**Required<T>**` when you want to **enforce full objects**.
- Useful in **object creation, validation, and API calls**.
- Combine with other utility types for **custom type transformations**.