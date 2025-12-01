---
Created: 2025-11-30T15:09
tags:
  - Advance-Tpes
---
# `**Record<Keys, Type>**` **in TypeScript**

The `Record` utility type lets you **create an object type with specified keys and value types**.

- Syntax: `Record<Keys, Type>`
- `Keys` → union of string or number literals
- `Type` → type of all values

---

## ✅ **1. Basic** `**Record**` **Example**

```TypeScript
type Roles = "admin" | "user" | "guest";

const rolePermissions: Record<Roles, string> = {
  admin: "all-access",
  user: "limited-access",
  guest: "read-only"
};

// rolePermissions["admin"] → "all-access"

```

- Creates an object type with **keys** `**"admin" | "user" | "guest"**`.
- Ensures **all keys are present** and **all values have type** `**string**`.

---

## ✅ **2. Using** `**Record**` **With Numbers**

```TypeScript
type PageScores = Record<number, number>;

const scores: PageScores = {
  1: 100,
  2: 95,
  3: 80
};

```

- `Keys` can also be `number`.
- Useful for **index-like objects**.

---

## ✅ **3. With Complex Types**

```TypeScript
interface User {
  id: number;
  name: string;
}

type UserMap = Record<string, User>;

const users: UserMap = {
  alice: { id: 1, name: "Alice" },
  bob: { id: 2, name: "Bob" }
};

```

- Values can be **complex objects**.
- Ensures **all values follow the** `**User**` **type**.

---

## ✅ **4. Dynamic Key Unions**

```TypeScript
type Events = "click" | "hover" | "scroll";
type EventHandlers = Record<Events, () => void>;

const handlers: EventHandlers = {
  click: () => console.log("click"),
  hover: () => console.log("hover"),
  scroll: () => console.log("scroll")
};

```

- `Record` ensures **every key in the union is included**.
- Useful for **typed maps of handlers or configurations**.

---

## ✅ **5. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Basic Record|`Record<Keys, Type>`|`Record<"a"|"b", string>`|
|Number keys|`Record<number, Type>`|`Record<number, number>`|Keys can be numeric|
|Complex values|`Record<string, User>`|Object values must match type|Type-safe object map|
|Dynamic union keys|`Record<Events, () => void>`|Every key must exist|Useful for handlers, configs|

---

**Rule of Thumb**:

- Use `**Record<Keys, Type>**` to create **object maps with predefined keys and value types**.
- Ensures **all keys are present** and values are **type-safe**.
- Works well with **event handlers, configuration objects, or ID maps**.