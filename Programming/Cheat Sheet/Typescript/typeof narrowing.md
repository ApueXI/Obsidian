---
Created: 2025-12-01T11:15
tags:
  - Type-Narrowing
---
# 🔵 TypeScript — `**typeof**` **Narrowing Cheat Sheet**

---

# ✅ 1. Full Explanation

## **What is** `**typeof**` **Narrowing?**

`typeof` narrowing is a TypeScript technique where the compiler **reduces** (narrows) the possible type of a variable based on a runtime `typeof` check.

This allows TypeScript to understand:

- **What type the variable actually is**
- **What operations you can safely perform**
- **Which branches of code are reachable**

---

## **Why it matters**

JavaScript is dynamically typed — values can change type at runtime.

TypeScript enforces static safety by **narrowing** union types inside conditional branches.

---

## **Basic Syntax**

```TypeScript
if (typeof value === "string") {
  // value is a string here
}

```

Supported `typeof` type checks:

|`typeof x === ...`|Meaning|
|---|---|
|`"string"`|String values|
|`"number"`|Numbers, including `NaN`|
|`"boolean"`|true / false|
|`"bigint"`|BigInt values|
|`"symbol"`|Symbol values|
|`"undefined"`|undefined|
|`"object"`|object or null|
|`"function"`|functions|

---

## **How Narrowing Works**

If you start with:

```TypeScript
let input: string | number;

```

Then:

```TypeScript
if (typeof input === "string") {
   // input: string
} else {
   // input: number
}

```

TypeScript removes the impossible types inside each branch.

---

## **Gotchas / Pitfalls**

### ❗ 1. `"object"` includes `null`

```TypeScript
typeof null === "object" // true

```

Be careful when narrowing `object`.

---

### ❗ 2. Cannot detect arrays

```TypeScript
typeof [] === "object"

```

Use `Array.isArray()` instead — this also performs narrowing.

---

### ❗ 3. Cannot detect classes

Classes are `"object"` at runtime.

---

### ❗ 4. Custom types or interfaces cannot use `typeof`

`typeof` works on **runtime values**, not type names.

---

### ❗ 5. Narrowing is flow-sensitive

TypeScript remembers narrowing **within the block**, not outside.

---

# ✅ 2. Summary Table

|Check|Narrows To|Notes|
|---|---|---|
|`typeof x === "string"`|`string`|Safe string operations|
|`typeof x === "number"`|`number`|Includes `NaN`|
|`typeof x === "boolean"`|`boolean`|True/false|
|`typeof x === "bigint"`|`bigint`|For large integers|
|`typeof x === "symbol"`|`symbol`|Rare, but supported|
|`typeof x === "undefined"`|`undefined`|Useful for optional params|
|`typeof x === "function"`|`Function`|Callable values|
|`typeof x === "object"`|`object|null`|

---

# ✅ 3. Real-World Example (Practical & Useful)

## **Scenario:**

You’re building a function that accepts **multiple kinds of request payloads**.

It may come as:

- a raw string
- an object
- a number (ID reference)

You want different behavior depending on the actual type.

---

## **Code Example With** `**typeof**` **Narrowing**

```TypeScript
type Payload = string | number | { data: string };

function handleRequest(input: Payload) {
  if (typeof input === "string") {
    return input.toUpperCase();         // safe: input is string
  }

  if (typeof input === "number") {
    return `Fetching record #${input}`; // safe: input is number
  }

  // Remaining type: { data: string }
  return `Object payload: ${input.data}`;
}

```

### What TypeScript knows:

|Condition|Narrowed Type|
|---|---|
|`typeof input === "string"`|string|
|`typeof input === "number"`|number|
|else|`{ data: string }`|

---

# 🔥 Bonus Real-World Example — Handling API responses

```TypeScript
function parseResponse(res: unknown) {
  if (typeof res === "string") {
    return JSON.parse(res);
  }

  if (typeof res === "object" && res !== null) {
    return res; // already an object
  }

  return { error: "Invalid response type" };
}

```

Here, TypeScript narrows:

- `"string"` → string
- `"object" && res !== null` → object
- else → all other types

This pattern is heavily used in backend/frontend data parsing.