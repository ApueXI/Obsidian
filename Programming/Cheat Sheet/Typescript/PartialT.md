---
Created: 2025-11-30T15:10
tags:
  - Utility-Types
---
# `**Partial<T>**` **in TypeScript**

The `Partial<T>` utility type **makes all properties of a type optional**.

- Useful for **update operations, optional configurations, or partial objects**.
- It is a **mapped type** under the hood: `[P in keyof T]?: T[P]`.

---

## ✅ **1. Basic Example**

```TypeScript
interface User {
  id: number;
  name: string;
  email: string;
}

type PartialUser = Partial<User>;

const user1: PartialUser = {};
const user2: PartialUser = { id: 1 };
const user3: PartialUser = { name: "Alice", email: "alice@example.com" };

```

- Every property of `User` becomes optional in `PartialUser`.
- Useful when you **don’t want to provide all fields**.

---

## ✅ **2. With Functions (Update Pattern)**

```TypeScript
function updateUser(id: number, updates: Partial<User>) {
  // Imagine updating the user in a database
  console.log(`Updating user ${id}`, updates);
}

updateUser(1, { name: "Bob" });  // ✅ Only name updated
updateUser(2, {});                // ✅ No fields updated

```

- `Partial<T>` allows **passing only the properties you want to change**.

---

## ✅ **3. Nested Partial Types**

```TypeScript
interface Profile {
  username: string;
  settings: {
    theme: string;
    notifications: boolean;
  };
}

type PartialProfile = Partial<Profile>;

const profile: PartialProfile = {
  settings: {
    theme: "dark"
  }  // notifications is optional now
};

```

- **Top-level properties** become optional, but **nested objects are still fully typed**.
- For deep partials, you may need **custom deep partial utility types**.

---

## ✅ **4. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Make all properties optional|`Partial<T>`|`Partial<User>`|Allows any or none of the properties|
|Function arguments|`Partial<T>`|`updateUser(id, updates)`|Useful for update patterns|
|Nested objects|`Partial<T>`|Only top-level optional|Deep partial requires custom type|
|Under the hood|`[P in keyof T]?: T[P]`|Mapped type|Shows how TypeScript implements it|

---

**Rule of Thumb**:

- Use `**Partial<T>**` when **not all properties are required**.
- Great for **update functions, optional config objects, and flexible API inputs**.
- Remember **nested objects remain fully typed** unless using a deep partial approach.