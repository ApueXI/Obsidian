---
Created: 2025-11-30T14:48
tags:
  - Funcions
---
# **Callbacks in TypeScript**

A **callback** is a function passed as an argument to another function.

- It allows code to be **executed later**, often after an operation finishes.
- TypeScript enforces **type safety** for callbacks.

---

## ✅ **1. Basic Callback Example**

```TypeScript
function greet(name: string, callback: (msg: string) => void) {
  const message = `Hello, ${name}`;
  callback(message);
}

greet("Alice", (msg) => {
  console.log(msg); // "Hello, Alice"
});

```

- `callback: (msg: string) => void` is the **callback type**.
- TypeScript ensures the function you pass matches the expected parameters and return type.

---

## 🔹 **2. Callback With Return Value**

```TypeScript
function transform(num: number, callback: (x: number) => number): number {
  return callback(num);
}

const result = transform(5, (n) => n * 2);
console.log(result); // 10

```

- Callback can **return a value**, which can be used by the outer function.
- TypeScript checks the return type as well.

---

## 🔹 **3. Optional Callback Parameter**

```TypeScript
function logMessage(msg: string, callback?: (msg: string) => void) {
  console.log(msg);
  callback?.(msg);
}

logMessage("Test");              // Works without callback
logMessage("Hello", (m) => console.log("Callback:", m));

```

- Optional callbacks can be handled safely using `?`.

---

## 🔹 **4. Callback With Multiple Parameters**

```TypeScript
function operate(a: number, b: number, callback: (x: number, y: number) => number) {
  return callback(a, b);
}

const sum = operate(3, 4, (x, y) => x + y);
console.log(sum); // 7

```

- Callback can accept **multiple arguments**, fully typed.

---

## 🔹 **5. Callback Type Alias**

```TypeScript
type StringCallback = (msg: string) => void;

function greet(name: string, cb: StringCallback) {
  cb(`Hi, ${name}`);
}

greet("Bob", console.log);

```

- Makes code cleaner and **reusable**.

---

## 🔹 **6. Asynchronous Callback Example**

```TypeScript
function fetchData(callback: (data: string) => void) {
  setTimeout(() => {
    callback("Fetched data!");
  }, 1000);
}

fetchData((data) => {
  console.log(data); // "Fetched data!" after 1 second
});

```

- Callbacks are often used for **async operations** like `setTimeout`, network requests, or events.

---

## 📋 **Callbacks Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Basic callback|`(param: type) => returnType`|`callback: (msg: string) => void`|Passed as function argument|
|Optional callback|`callback?: (msg: string) => void`|`callback?.(msg)`|Safe optional calls|
|Multiple parameters|`(x:number, y:number)=>number`|`operate(a,b,callback)`|Fully typed arguments|
|Return value|`(x:number)=>number`|`return callback(num)`|Can pass results back|
|Type alias|`type Fn = (msg:string)=>void`|Reusable type for multiple callbacks|Cleaner code|