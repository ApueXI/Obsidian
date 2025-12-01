---
Created: 2025-12-01T11:53
tags:
  - Extra-Advanced-Topics
---
# 🔵 TypeScript — **Typing Complex Callback Chains**

---

## 1. **Full Explanation**

### **What It Means**

- Complex callback chains involve **functions that accept other functions as parameters**, where the **callbacks themselves may accept callbacks**.
- Proper typing ensures **type safety, autocomplete, and maintainability** across multiple layers of asynchronous or sequential operations.
- Can combine **interfaces, generics, union types, and function types**.

---

### **Why Use It**

1. Avoid `**any**` **hell** in nested callbacks.
2. Ensure **consistent parameter and return types**.
3. Make code easier to **refactor and read**.
4. Support **asynchronous flows** or **event chains** safely.

---

### **Key Points**

- Use **function types** `(args) => returnType` to describe callbacks.
- Use **optional parameters** `param?: type` for flexibility.
- Use **generics** to allow reusable callback types.
- For nested callbacks, **type each layer** explicitly.
- Prefer **interfaces for named callback shapes** for clarity.

---

## 2. **How It Works**

### 1. **Simple Callback Typing**

```TypeScript
interface Callback {
  (error: Error | null, result?: string): void;
}

function fetchData(cb: Callback) {
  cb(null, "Data loaded");
}

fetchData((err, data) => {
  if (err) console.error(err);
  else console.log(data); // ✅ Type-checked
});

```

---

### 2. **Nested Callback Typing**

```TypeScript
interface InnerCallback {
  (err: Error | null, value?: number): void;
}

interface OuterCallback {
  (err: Error | null, next?: InnerCallback): void;
}

function doSomething(cb: OuterCallback) {
  cb(null, (err, value) => {
    if (err) console.error(err);
    else console.log("Value:", value);
  });
}

doSomething((err, inner) => {
  if (inner) inner(null, 42); // ✅ Type-safe nested call
});

```

---

### 3. **Using Generics for Reusable Callbacks**

```TypeScript
interface Callback<T> {
  (err: Error | null, result?: T): void;
}

function fetchNumber(cb: Callback<number>) {
  cb(null, 123);
}

fetchNumber((err, value) => {
  console.log(value); // ✅ 123
});

```

- Generics allow **different callback types** without redefining interfaces.

---

### 4. **Chaining Callbacks with Promises for Safety**

- Sometimes complex chains are easier to type with **promises**:

```TypeScript
type AsyncFn<T> = (cb: (err: Error | null, result?: T) => void) => void;

const fetchData: AsyncFn<string> = (cb) => cb(null, "Hello");

fetchData((err, result) => {
  if (err) throw err;
  console.log(result); // ✅ "Hello"
});

```

- Ensures **type safety** across asynchronous layers.

---

### 5. **Optional Callback Parameters**

```TypeScript
interface Callback {
  (err?: Error): void;
}

function maybeCallback(cb?: Callback) {
  if (cb) cb();
}

maybeCallback(); // ✅ OK
maybeCallback(err => console.log(err?.message)); // ✅ OK

```

- Useful for **optional callbacks** in libraries.

---

## 3. **Gotchas / Pitfalls**

1. **Implicit** `**any**`: Always type callback parameters explicitly.
2. **Callback hell**: Too many nested callbacks reduce readability → consider **promises or async/await**.
3. **Optional parameters**: Place them at the end of the signature.
4. **Generics**: Make reusable callback interfaces instead of repeating types.

---

## 4. **Summary Table**

|Feature|Syntax|Notes|
|---|---|---|
|Simple callback|`(err: Error|null, result?: T) => void`|
|Nested callback|`(err: Error|null, next?: Callback) => void`|
|Generic callback|`interface Callback<T> { (err: Error|null, result?: T): void }`|
|Optional callback|`cb?: Callback`|Safe to skip passing callback|
|Promises alternative|`type AsyncFn<T> = (cb: Callback<T>) => void`|Simplifies chaining|

---

## 5. **Real-World Examples**

### **Example 1: Simple Nested Callback**

```TypeScript
interface InnerCallback {
  (err: Error | null, value?: number): void;
}

interface OuterCallback {
  (err: Error | null, next?: InnerCallback): void;
}

function processData(cb: OuterCallback) {
  cb(null, (err, val) => console.log("Value:", val));
}

processData((err, inner) => {
  if (inner) inner(null, 42); // ✅ 42
});

```

### **Example 2: Generic Callback**

```TypeScript
interface Callback<T> {
  (err: Error | null, data?: T): void;
}

function fetchString(cb: Callback<string>) {
  cb(null, "Hello TypeScript");
}

fetchString((err, data) => console.log(data)); // ✅ "Hello TypeScript"

```

### **Example 3: Optional Callback**

```TypeScript
interface Callback {
  (err?: Error): void;
}

function doTask(cb?: Callback) {
  if (cb) cb();
}

doTask(); // ✅ OK
doTask(err => console.log(err)); // ✅ OK

```

---

## 6. **Key Takeaways**

1. Explicitly type **all callback parameters** for safety.
2. Use **interfaces or type aliases** for complex callbacks.
3. Use **generics** for reusable callback types.
4. Consider **promises or async/await** to reduce deeply nested callbacks.
5. Optional callbacks can be declared with `cb?: Callback`.