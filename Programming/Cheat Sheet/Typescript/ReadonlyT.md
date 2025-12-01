---
Created: 2025-11-30T15:12
tags:
  - Utility-Types
---
# `**Readonly<T>**` **in TypeScript**

The `Readonly<T>` utility type **makes all properties of a type immutable**.

- Prevents reassignment of properties after initialization.
- Useful for **immutable data structures** or **preventing accidental modifications**.
- Internally, it is a **mapped type**: `[P in keyof T]: Readonly<T[P]>`.

---

## ✅ **1. Basic Example**

```TypeScript
interface User {
  id: number;
  name: string;
}

type ReadonlyUser = Readonly<User>;

const user: ReadonlyUser = { id: 1, name: "Alice" };

// ❌ Cannot modify properties
// user.id = 2;
// user.name = "Bob";

```

- All properties in `ReadonlyUser` are **read-only**.
- Compile-time error if you try to assign a new value.

---

## ✅ **2. Using Readonly with Arrays**

```TypeScript
const numbers: ReadonlyArray<number> = [1, 2, 3];

// ❌ Cannot modify array
// numbers.push(4);
// numbers[0] = 10;

```

- `ReadonlyArray<T>` is a **specialized read-only array type**.
- Provides **immutability guarantees** for arrays.

---

## ✅ **3. Nested Objects**

```TypeScript
interface Profile {
  username: string;
  settings: {
    theme: string;
    notifications: boolean;
  };
}

type ReadonlyProfile = Readonly<Profile>;

const profile: ReadonlyProfile = {
  username: "alice",
  settings: { theme: "dark", notifications: true }
};

// ❌ profile.settings.theme = "light"; // Allowed?

```

- **Top-level properties** are read-only.
- Nested objects are **not deeply readonly**.
- For deep immutability, a **custom DeepReadonly** type is needed.

---

## ✅ **4. Combining Utility Types**

```TypeScript
type PartialReadonlyUser = Readonly<Partial<User>>;

const user: PartialReadonlyUser = { id: 1 };
// ❌ Cannot modify id

```

- Can combine with **Partial<T>**, **Required<T>**, etc., to customize type behavior.

---

## ✅ **5. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Make all properties read-only|`Readonly<T>`|`Readonly<User>`|Prevents property reassignment|
|Readonly array|`ReadonlyArray<T>`|`ReadonlyArray<number>`|Immutable arrays|
|Nested objects|`Readonly<T>`|Top-level readonly only|Deep readonly requires custom type|
|Combine with other utilities|`Readonly<Partial<T>>`|Optional + immutable|Flexible type transformations|
|Under the hood|`[P in keyof T]: T[P]`|Mapped type|Shows TypeScript implementation|

---

**Rule of Thumb**:

- Use `**Readonly<T>**` to **prevent modification** of objects or arrays.
- Works best for **immutable data structures, configs, and constants**.
- For nested immutability, consider a **deep readonly utility type**.