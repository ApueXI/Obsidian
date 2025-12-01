---
Created: 2025-12-01T11:15
tags:
  - Utility-Types
---
# 🔵 TypeScript Utility Type — **Awaited<T>**

**Cheat Sheet (Full Explanation • Summary Table • Real-World Example)**

---

# ✅ 1. Full Explanation

## **What is** `**Awaited<T>**`**?**

`Awaited<T>` is a built-in TypeScript utility type that **unwraps**:

- the **resolved value** of a `Promise<T>`
- nested promises (e.g. `Promise<Promise<T>>`)
- `Thenable` objects (custom objects with a `.then()` method)
- async function return types

It simulates the behavior of the `await` keyword **at the type level**.

---

## **Why does it exist?**

Before TypeScript 4.5, manually unwrapping promise types was tricky.

`Awaited<T>` was introduced to make async type inference consistent and safe.

---

## **Syntax**

```TypeScript
Awaited<T>

```

---

## **How it works**

Given a type `T`:

- If `T` is **not a Promise**, `Awaited<T> = T`
- If `T` is `Promise<U>`, then `Awaited<T> = Awaited<U>` (recursive unwrapping)
- If `T` is a **Thenable**, TypeScript infers its resolved type
- If `T` is `never`, the result stays `never`

---

## **Common Use Cases**

- Getting the resolved type of an async function
- Creating reusable async utilities
- Working with promise chains
- Ensuring correct typing for API responses or database calls

---

## **Gotchas & Pitfalls**

### ❗ 1. It unwraps **nested promises automatically**

```TypeScript
Awaited<Promise<Promise<number>>> // number

```

### ❗ 2. It understands **Thenables**, not only Promises

This means custom objects with `then()` are unwrapped.

### ❗ 3. Doesn’t change runtime behavior

It only works at the type level.

### ❗ 4. If you pass a union, it unwraps each part

```TypeScript
Awaited<Promise<string> | number> // string | number

```

---

# ✅ 2. Summary Table

|Feature|Behavior|
|---|---|
|Unwrap Promise|`Awaited<Promise<T>> → T`|
|Unwrap nested Promise|`Awaited<Promise<Promise<T>>> → T`|
|Handles Thenables|Yes|
|Works with async return types|Yes|
|Works with unions|Yes|
|No effect on non-Promises|`Awaited<number> → number`|

---

# ✅ 3. Real-World Example (Practical)

## **Scenario:**

You are building a system that fetches user data from an API.

You have an async function:

```TypeScript
async function getUser() {
  return {
    id: 1,
    name: "Alice",
    roles: ["ADMIN", "EDITOR"],
  };
}

```

### **Get the "resolved value" type of an async function**

```TypeScript
type User = Awaited<ReturnType<typeof getUser>>;

```

Now `User` becomes:

```TypeScript
type User = {
  id: number;
  name: string;
  roles: string[];
};

```

---

## **Use Case: Strongly typing API utilities**

### Example: Creating a fetch wrapper where `Awaited` helps infer response types

```TypeScript
async function fetchJSON<T>(url: string): Promise<T> {
  const res = await fetch(url);
  return res.json();
}

// Later…
type UserResponse = Awaited<ReturnType<typeof fetchJSON<User>>>;

```

Now every part of your app that uses this API is **fully typed**, including nested async calls.

---

# 🔥 Bonus Real-World Scenario (More Advanced)

## **Unwrapping complex async logic**

```TypeScript
type DeepAsync =
  Promise<
    Promise<
      Promise<{ token: string; expires: number }>
    >
  >;

```

`Awaited<DeepAsync>` becomes:

```TypeScript
{ token: string; expires: number }

```

This makes deeply nested async workflows safe and predictable.