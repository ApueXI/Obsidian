---
Created: 2025-11-30T14:49
tags:
  - Object-Types
---
# **Inline Object Types in TypeScript**

Inline object types allow you to **define the type of an object directly** where it’s used, without creating a separate interface or type alias.

- Useful for **small or one-off objects**.
- Keeps the code **concise** and readable.

---

## ✅ **1. Basic Syntax**

```TypeScript
function printPerson(person: { name: string; age: number }) {
  console.log(`${person.name} is ${person.age} years old`);
}

printPerson({ name: "Alice", age: 25 }); // Alice is 25 years old

```

- `{ name: string; age: number }` is an **inline object type**.
- The object passed must exactly match this shape.

---

## 🔹 **2. Optional Properties**

```TypeScript
function printPerson(person: { name: string; age?: number }) {
  console.log(`${person.name} is ${person.age ?? "unknown"} years old`);
}

printPerson({ name: "Bob" }); // Bob is unknown years old

```

- Optional properties are denoted with `?`.
- Useful for objects that may omit certain fields.

---

## 🔹 **3. Readonly Properties**

```TypeScript
function logUser(user: { readonly id: number; name: string }) {
  console.log(`User ${user.id}: ${user.name}`);
}

const user = { id: 1, name: "Neo" };
logUser(user);
// user.id = 2; ❌ Error: readonly

```

- `readonly` ensures the property **cannot be changed** after initialization.

---

## 🔹 **4. Nested Inline Objects**

```TypeScript
function printBook(book: { title: string; author: { name: string; age: number } }) {
  console.log(`${book.title} by ${book.author.name} (${book.author.age})`);
}

printBook({ title: "1984", author: { name: "Orwell", age: 46 } });

```

- Inline object types can include **nested objects** with their own types.

---

## 🔹 **5. Inline Object Type With Functions**

```TypeScript
function operate(obj: { a: number; b: number; sum: () => number }) {
  console.log(obj.sum());
}

operate({ a: 2, b: 3, sum: function() { return this.a + this.b; } }); // 5

```

- You can define **methods directly in the object type**.
- Provides **full type safety** for inline objects with functions.

---

## 🔹 **6. Inline vs Interface / Type Alias**

|Feature|Inline Object|Interface / Type Alias|
|---|---|---|
|Syntax|Direct in function or variable|Separate `interface` or `type`|
|Reusability|❌ Usually one-off|✅ Can reuse across code|
|Readability|✅ Quick for small objects|✅ Better for large/complex objects|
|Optional / readonly / nested|✅ Supported|✅ Supported|

---

## 🔹 **7. Practical Example**

```TypeScript
function sendRequest(options: { url: string; method?: "GET" | "POST"; headers?: Record<string, string> }) {
  console.log(`Sending ${options.method ?? "GET"} request to ${options.url}`);
  console.log("Headers:", options.headers ?? {});
}

sendRequest({ url: "https://api.example.com" });
sendRequest({ url: "https://api.example.com", method: "POST", headers: { "Auth": "token" } });

```

- Perfect for **config objects**, **API options**, or **temporary object structures**.

---

**Rule of Thumb**:

- Use **inline object types** for **small, one-off objects**.
- Use **interfaces or type aliases** for **reusable or complex object types**.