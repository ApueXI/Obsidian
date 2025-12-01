---
Created: 2025-12-01T11:13
tags:
  - Utility-Types
---
# `**ReturnType<T>**` **in TypeScript**

`ReturnType<T>` extracts the **return type** of a function type.

- `T` must be a function type.
- The result is **whatever that function returns**.
- Very useful for avoiding duplicate type declarations when multiple parts of your code depend on the same function output.

Internally:

```TypeScript
type ReturnType<T extends (...args: any) => any> =
    T extends (...args: any) => infer R ? R : any;

```

(`infer R` captures the return type.)

---

## ✅ **1. Basic Example**

```TypeScript
function getUser() {
  return { id: 1, name: "Alice" };
}

type User = ReturnType<typeof getUser>;

const u: User = { id: 1, name: "Alice" }; // Works

```

- `ReturnType<typeof getUser>` becomes `{ id: number; name: string; }`
- You avoid writing the shape twice.

---

## ✅ **2. With Arrow Functions**

```TypeScript
const sum = (a: number, b: number) => a + b;

type SumResult = ReturnType<typeof sum>;
// number

```

---

## ✅ **3. With Async Functions (Important)**

```TypeScript
async function fetchData() {
  return { ok: true, value: 123 };
}

type FetchResult = ReturnType<typeof fetchData>;
// Promise<{ ok: boolean; value: number }>

```

If you want the **resolved value**, use `Awaited<T>`:

```TypeScript
type Resolved = Awaited<ReturnType<typeof fetchData>>;
// { ok: boolean; value: number }

```

---

## ✅ **4. With Function Type Aliases**

```TypeScript
type Creator = () => { created: boolean };

type CreatedObj = ReturnType<Creator>;
// { created: boolean }

```

---

## ✅ **5. With Overloaded Functions**

`ReturnType` gets the **last overload signature**.

```TypeScript
function fn(x: number): number;
function fn(x: string): string;
function fn(x: any) { return x; }

type RT = ReturnType<typeof fn>;
// string | number

```

---

## ✅ **6. Real-World Example: Redux Action Creators**

```TypeScript
function createLoginAction(username: string) {
  return { type: "LOGIN", payload: username };
}

type LoginAction = ReturnType<typeof createLoginAction>;

```

Ensures:

- Actions always match the actual creator output.
- Changes in function automatically update the type.

---

## ✅ **7. Summary Table**

|Feature|Description|Example|
|---|---|---|
|Extract function return type|Uses `infer`|`ReturnType<typeof fn>`|
|Works with any function|Normal, arrow, async|`ReturnType<typeof sum>`|
|Async returns Promise|Use `Awaited` to unwrap|`Awaited<ReturnType<typeof fetch>>`|
|Avoids duplicate types|One source of truth|Redux actions, services|
|Overloads|Uses last overload|`string \| number`|

---

**Rule of Thumb**

Use `**ReturnType<T>**` whenever multiple parts of your app depend on the **output shape of a function** — it gives you **one source of truth**, avoids duplication, and ensures automatic type updates.