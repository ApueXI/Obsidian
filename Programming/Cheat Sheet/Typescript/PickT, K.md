---
Created: 2025-11-30T15:12
tags:
  - Utility-Types
---
# `**Pick<T, K>**` **in TypeScript**

The `Pick<T, K>` utility type **selects a subset of properties from an existing type**.

- `T` → original type
- `K` → union of keys from `T` to include
- Useful for **creating smaller types from larger ones** without repeating definitions.

---

## ✅ **1. Basic Example**

```TypeScript
interface User {
  id: number;
  name: string;
  email: string;
}

type UserPreview = Pick<User, "id" | "name">;

const preview: UserPreview = { id: 1, name: "Alice" };
// ❌ preview.email = "alice@example.com"; // Error: email not included

```

- `UserPreview` only includes `**id**` **and** `**name**`.
- Useful for **API responses, forms, or restricted views**.

---

## ✅ **2. With Functions**

```TypeScript
function showUserPreview(user: Pick<User, "id" | "name">) {
  console.log(user.id, user.name);
}

const user: User = { id: 1, name: "Alice", email: "alice@example.com" };
showUserPreview(user); // ✅ Only id and name used

```

- Can **pass a full object** but only **subset of keys is typed**.

---

## ✅ **3. Dynamic Key Subsets with Generics**

```TypeScript
function selectKeys<T, K extends keyof T>(obj: T, keys: K[]): Pick<T, K> {
  const result = {} as Pick<T, K>;
  keys.forEach(key => {
    result[key] = obj[key];
  });
  return result;
}

const user: User = { id: 1, name: "Alice", email: "alice@example.com" };
const preview = selectKeys(user, ["id", "email"]); // { id: 1, email: "alice@example.com" }

```

- Generic version lets you **pick keys dynamically while remaining type-safe**.

---

## ✅ **4. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Pick specific properties|`Pick<T, K>`|`Pick<User, "id"|"name">`|
|Function arguments|`Pick<T, K>`|`showUserPreview(user)`|Only selected keys are used|
|Generic pick|`Pick<T, K extends keyof T>`|`selectKeys(obj, keys)`|Dynamic selection of keys|
|Use case|API response, forms|`UserPreview`|Avoid exposing unnecessary data|
|Under the hood|Mapped type|`[P in K]: T[P]`|TypeScript implementation detail|

---

**Rule of Thumb**:

- Use `**Pick<T, K>**` to **create a type with only the properties you need**.
- Ideal for **partial views, restricted APIs, or lightweight objects**.
- Works well with **generics for dynamic key selection**.