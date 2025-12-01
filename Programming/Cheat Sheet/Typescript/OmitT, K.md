---
Created: 2025-12-01T11:12
tags:
  - Utility-Types
---
# `**Omit<T, K>**` **in TypeScript**

`Omit<T, K>` creates a new type by **removing** one or more properties (`K`) from an existing type (`T`).

- It is the **opposite of** `**Pick**`.
- Very useful when you want **almost the same type**, but without certain keys.

Internally, it's defined as:

```TypeScript
type Omit<T, K extends keyof any> = Pick<T, Exclude<keyof T, K>>;

```

---

## ✅ **1. Basic Example**

```TypeScript
interface User {
  id: number;
  name: string;
  email: string;
  password: string;
}

type PublicUser = Omit<User, "password">;

const user: PublicUser = {
  id: 1,
  name: "Alice",
  email: "alice@example.com"
};

// ❌ user.password = "abc"; // Error: removed from the type

```

- `PublicUser` contains **everything except** `**password**`.
- Useful when returning safe objects from APIs.

---

## ✅ **2. Removing Multiple Keys**

```TypeScript
type UserForForm = Omit<User, "id" | "password">;

```

`UserForForm` now has:

- `name`
- `email`

---

## ✅ **3. With Functions**

```TypeScript
function createUser(data: Omit<User, "id">) {
  const newUser: User = {
    id: Date.now(),
    ...data,
  };
  return newUser;
}

createUser({ name: "Bob", email: "b@b.com", password: "123" }); // OK

```

- Useful for **create** operations where the database generates the ID.

---

## ✅ **4. Combining Omit with Intersection**

You can combine `Omit` with `&` to replace fields:

```TypeScript
type UserWithoutEmail = Omit<User, "email"> & {
  email: string | null;
};

```

---

## ✅ **5. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Remove keys from a type|`Omit<T, K>`|`Omit<User, "password">`|Opposite of `Pick`|
|Remove multiple keys|`Omit<T, "a"|"b">`|`Omit<User, "id"|
|Function arguments|`Omit<T, K>`|`createUser(data)`|Useful for CREATE/UPDATE ops|
|Replace properties|`Omit<T, K> & {}`|Custom overrides|Advanced transformations|
|Under the hood|`Pick` + `Exclude`|`[P in Exclude<keyof T, K>]`|TypeScript implementation|

---

**Rule of Thumb**:

- Use `**Omit<T, K>**` when you want **almost the same type**, but without certain fields.
- Perfect for **public API responses**, **DTOs**, **form inputs**, and **creating safer types**.