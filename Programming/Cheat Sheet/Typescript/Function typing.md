---
Created: 2025-11-30T14:45
tags:
  - Funcions
---
# **Function Typing in TypeScript**

In TypeScript, you can **explicitly define types for function parameters and return values**.

This ensures functions are used safely and improves code readability.

---

## ✅ **1. Basic Syntax**

```TypeScript
function add(a: number, b: number): number {
  return a + b;
}

```

- `a: number, b: number` → parameter types
- `: number` → return type
- TypeScript will throw an error if the return type doesn’t match.

---

## 🔹 **2. Functions Without Return Value**

Use `void` when a function does **not return anything**:

```TypeScript
function logMessage(msg: string): void {
  console.log(msg);
}

```

---

## 🔹 **3. Optional Parameters**

Use `?` to make parameters optional:

```TypeScript
function greet(name?: string): void {
  console.log(`Hello, ${name || "Guest"}`);
}

greet();          // OK
greet("Alice");   // OK

```

---

## 🔹 **4. Default Parameters**

```TypeScript
function greet(name: string = "Guest"): void {
  console.log(`Hello, ${name}`);
}

```

- Default values also **implicitly type the parameter**.

---

## 🔹 **5. Rest Parameters**

```TypeScript
function sum(...numbers: number[]): number {
  return numbers.reduce((acc, curr) => acc + curr, 0);
}

sum(1, 2, 3, 4); // 10

```

- `...numbers: number[]` → array of numbers of any length

---

## 🔹 **6. Function Type Expressions**

You can define the **type of a function** separately:

```TypeScript
let multiply: (x: number, y: number) => number;

multiply = (a, b) => a * b;

```

- `(x: number, y: number) => number` describes **parameters and return type**.
- Ensures any assigned function matches the type.

---

## 🔹 **7. Functions with Union Types**

```TypeScript
function format(input: string | number): string {
  if (typeof input === "number") {
    return input.toFixed(2);
  }
  return input.toUpperCase();
}

```

- Type narrowing is used inside the function to safely handle multiple input types.

---

## 🔹 **8. Function Type Aliases**

```TypeScript
type BinaryOp = (a: number, b: number) => number;

const add: BinaryOp = (x, y) => x + y;
const multiply: BinaryOp = (x, y) => x * y;

```

- Makes function typing **reusable and readable**.

---

## 🔹 **9. Optional & Default Function Parameters in Types**

```TypeScript
type Greet = (name?: string) => void;

const sayHello: Greet = (name = "Guest") => console.log(`Hello, ${name}`);

```

---

## 📋 **Function Typing Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Parameter types|`(a: number, b: number)`|`function add(a: number, b: number)`|Required types for inputs|
|Return type|`: number`|`function add(...) : number`|Enforces return value type|
|Optional param|`name?: string`|`greet(name?: string)`|Can be undefined|
|Default param|`name: string = "Guest"`|`greet(name = "Guest")`|Default value also types param|
|Rest params|`...nums: number[]`|`sum(...nums: number[])`|Accepts multiple arguments|
|Function type|`(x: number, y: number) => number`|`let multiply: (x,y)=>number`|Describes entire function|
|Type alias for function|`type Fn = (a:number)=>void`|Reusable function type|Cleaner code|