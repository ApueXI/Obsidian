---
Created: 2025-11-30T15:08
tags:
  - Advance-Tpes
---
# **Optional & Required Modifiers in TypeScript**

TypeScript provides **utility types** to **modify object types** by making properties optional, required, or read-only.

- These are **mapped type helpers** that work with generics.
- Very useful for **flexible and type-safe APIs**.

---

## ✅ **1.** `**Partial<T>**` **— Makes All Properties Optional**

```TypeScript
interface User {
  id: number;
  name: string;
  email: string;
}

type PartialUser = Partial<User>;

const user1: PartialUser = {};
const user2: PartialUser = { id: 1 };

```

- All properties of `User` become **optional**.
- Useful for **update operations** or **partial objects**.

---

## ✅ **2.** `**Required<T>**` **— Makes All Properties Required**

```TypeScript
interface User {
  id?: number;
  name?: string;
  email?: string;
}

type RequiredUser = Required<User>;

const user: RequiredUser = { id: 1, name: "Alice", email: "alice@example.com" };
// ❌ Missing any property → Type error

```

- Ensures **all properties must be present**.
- Useful when **ensuring full data objects**.

---

## ✅ **3.** `**Readonly<T>**` **— Makes All Properties Read-Only**

```TypeScript
interface User {
  id: number;
  name: string;
}

type ReadonlyUser = Readonly<User>;

const user: ReadonlyUser = { id: 1, name: "Alice" };
// user.id = 2; ❌ Error: Cannot assign to 'id' because it is a read-only property

```

- Prevents **modification of properties** after initialization.
- Useful for **immutable objects**.

---

## ✅ **4. Combining Utility Types**

```TypeScript
interface User {
  id: number;
  name: string;
  email: string;
}

type PartialReadonlyUser = Readonly<Partial<User>>;

const user: PartialReadonlyUser = { id: 1 };
// user.id = 2; ❌ Cannot modify

```

- You can **compose multiple utility types** to customize type behavior.

---

## ✅ **5. Summary Table**

|Utility Type|Syntax|Effect|Example|
|---|---|---|---|
|`Partial<T>`|`Partial<User>`|All properties optional|`{}` or `{ id: 1 }`|
|`Required<T>`|`Required<User>`|All properties required|`{ id:1, name:'Alice', email:'a@b.com' }`|
|`Readonly<T>`|`Readonly<User>`|All properties read-only|Cannot assign to any property|
|Combination|`Readonly<Partial<T>>`|Optional + immutable|`{ id?: 1 }`, cannot modify|

---

**Rule of Thumb**:

- Use `**Partial<T>**` for **partial updates** or optional data.
- Use `**Required<T>**` to **enforce full object presence**.
- Use `**Readonly<T>**` to **prevent object mutation**.
- Combine utility types for **custom type transformations**.