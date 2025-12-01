---
Created: 2025-12-01T11:46
tags:
  - Type-Safety-Technique
---
# 🔵 TypeScript — **Using** `**unknown**` **Properly**

---

# ✅ 1. Full Explanation

## **What is** `**unknown**`**?**

- `unknown` is a TypeScript type that represents **any value**, but unlike `any`, **you cannot perform operations on it without type checking**.
- It is the **type-safe counterpart of** `**any**`.

```TypeScript
let value: unknown;
value = 42;         // ✅ allowed
value = "hello";    // ✅ allowed

```

- You **cannot directly access properties, call it as a function, or assign it to other types** without type narrowing.

---

## **Why Use** `**unknown**` **Instead of** `**any**`

1. Forces **type checking before usage** → safer than `any`
2. Prevents **silent runtime errors**
3. Encourages **type guards, assertions, and proper validation**
4. Makes code **self-documenting**, indicating that type is unknown at compile-time

---

## **Key Rules**

- You **cannot** do this with `unknown`:

```TypeScript
let value: unknown;
console.log(value.toUpperCase()); // ❌ Error: Object is of type 'unknown'
let num: number = value;          // ❌ Error: Type 'unknown' is not assignable

```

- You **must** check or assert the type first.

---

## **How to Use** `**unknown**` **Properly**

### 1. **Type Narrowing**

```TypeScript
function process(value: unknown) {
  if (typeof value === "string") {
    console.log(value.toUpperCase()); // ✅ Safe
  } else if (typeof value === "number") {
    console.log(value * 2); // ✅ Safe
  } else {
    console.log("Unknown type");
  }
}

```

### 2. **Type Assertions (When Sure)**

```TypeScript
let value: unknown = "hello";
console.log((value as string).toUpperCase()); // ✅ Works

```

- Use sparingly; prefer narrowing first.

### 3. **Assigning to Another** `**unknown**`

```TypeScript
let val: unknown = 123;
let another: unknown = val; // ✅ Allowed

```

### 4. **Using Generics for Type-Safe Wrapping**

```TypeScript
function wrap<T>(value: T): { value: T } {
  return { value };
}

const wrapped = wrap<unknown>(42); // ✅ Works safely

```

### 5. **Function Parameters**

```TypeScript
function logValue(value: unknown) {
  if (typeof value === "string") {
    console.log("String length:", value.length);
  } else if (typeof value === "number") {
    console.log("Number squared:", value * value);
  } else {
    console.log("Value is unknown");
  }
}

```

---

## **Gotchas / Pitfalls**

1. Using `unknown` like `any` **defeats the purpose** → always narrow or assert types
2. Cannot assign `unknown` to other types **without narrowing**
3. Good practice to **combine** `**unknown**` **with type guards or** `**typeof**` **checks**
4. Often used in **function arguments, API responses, and dynamic data**

---

# ✅ 2. Summary Table

|Technique|Example|Notes|
|---|---|---|
|Direct assignment|`let value: unknown = 42;`|✅ Allowed|
|Type narrowing|`if (typeof value === "string") { ... }`|✅ Safe usage|
|Type assertion|`(value as string).toUpperCase()`|Use sparingly|
|Assign to unknown|`let another: unknown = value;`|✅ Allowed|
|Generic wrapping|`wrap<unknown>(value)`|Keeps type safe|

---

# ✅ 3. Real-World Examples

### **Scenario 1: API Response**

```TypeScript
function handleApiResponse(response: unknown) {
  if (typeof response === "object" && response !== null) {
    console.log("Received object with keys:", Object.keys(response));
  } else {
    console.log("Unexpected response type");
  }
}

```

### **Scenario 2: Dynamic User Input**

```TypeScript
function processInput(input: unknown) {
  if (typeof input === "string") {
    console.log("String input length:", input.length);
  } else if (typeof input === "number") {
    console.log("Number squared:", input * input);
  } else {
    console.log("Invalid input type");
  }
}

```

### **Scenario 3: Safe Type Assertion**

```TypeScript
const value: unknown = "hello world";
const str: string = value as string; // ✅ OK if you're certain

```

---

# 🔥 Bonus Tips

1. Prefer **type narrowing over assertions** whenever possible
2. Use `unknown` for **external input, JSON parsing, or library results**
3. Combining `unknown` with `**strict**` **mode** maximizes safety