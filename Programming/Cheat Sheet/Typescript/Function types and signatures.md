---
Created: 2025-11-30T14:47
tags:
  - Funcions
---
# **Function Types and Signatures in TypeScript**

A **function type** describes **the types of parameters and the return type** for a function.

- It ensures that any function assigned to a variable or passed as a parameter **matches the expected signature**.
- Makes APIs safer and more readable.

---

## ✅ **1. Basic Function Type**

```TypeScript
let add: (a: number, b: number) => number;

add = (x, y) => x + y; // ✅ matches the signature
// add = (x, y) => x + y + ""; // ❌ Error: return type must be number

```

- `(a: number, b: number) => number` is the **function signature**:
    - Parameters: `a: number, b: number`
    - Return type: `number`

---

## 🔹 **2. Function Type with Optional Parameters**

```TypeScript
let greet: (name?: string) => void;

greet = (n) => console.log(`Hello, ${n || "Guest"}`);

greet();        // OK
greet("Alice"); // OK

```

- Optional parameters are allowed in the signature using `?`.

---

## 🔹 **3. Function Type with Default Parameters**

Default parameters are not part of the type but are allowed in the implementation:

```TypeScript
let greet: (name?: string) => void;

greet = (name = "Guest") => console.log(`Hello, ${name}`);

```

- TypeScript sees `name` as optional (`string | undefined`) in the type signature.

---

## 🔹 **4. Function Type with Rest Parameters**

```TypeScript
let sum: (...nums: number[]) => number;

sum = (...numbers) => numbers.reduce((acc, n) => acc + n, 0);

sum(1, 2, 3); // 6

```

- The `...nums: number[]` rest parameter is part of the signature.

---

## 🔹 **5. Function Type Aliases**

You can **give a function type a name** for reuse:

```TypeScript
type BinaryOp = (x: number, y: number) => number;

const add: BinaryOp = (a, b) => a + b;
const multiply: BinaryOp = (a, b) => a * b;

```

- Makes large codebases **more readable and consistent**.

---

## 🔹 **6. Functions as Parameters**

```TypeScript
function operate(a: number, b: number, op: (x: number, y: number) => number) {
  return op(a, b);
}

const result = operate(5, 3, (x, y) => x * y); // 15

```

- `op` must match the **signature** `(x: number, y: number) => number`.

---

## 🔹 **7. Functions Returning Functions**

```TypeScript
type Mapper = (x: number) => number;

function createMultiplier(factor: number): Mapper {
  return (x) => x * factor;
}

const double = createMultiplier(2);
console.log(double(5)); // 10

```

- You can **type functions that return other functions**.

---

## 📋 **Function Types Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Basic function type|`(a: number, b: number) => number`|`let add: (a,b)=>number`|Describes parameters & return type|
|Optional param|`(name?: string) => void`|Optional in signature|Must match implementation|
|Default param|`(name?: string) => void`|Allowed in implementation|Default does not affect type|
|Rest params|`(...nums: number[]) => number`|`sum(...nums)`|Collects multiple arguments|
|Type alias for function|`type Fn = (x:number)=>number`|Reusable signature|Cleaner code|
|Function as param|`(a:number,b:number, op:(x:number,y:number)=>number)`|Safe callbacks|Enforces correct usage|
|Function returning function|`(): (x:number)=>number`|Higher-order functions|Typing nested functions|