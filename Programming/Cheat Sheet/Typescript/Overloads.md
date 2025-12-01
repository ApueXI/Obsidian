---
Created: 2025-11-30T14:47
tags:
  - Funcions
---
# **Function Overloads in TypeScript**

Function overloads allow a single function to **have multiple type signatures**.

- This is useful when a function can accept **different types or numbers of arguments**.
- TypeScript enforces type safety **based on the overload signatures**.
- Only **one implementation** exists, but multiple **signatures** describe it.

---

## ✅ **1. Basic Syntax**

```TypeScript
function combine(a: number, b: number): number;
function combine(a: string, b: string): string;
function combine(a: any, b: any): any { // implementation
  return a + b;
}

console.log(combine(1, 2));       // 3
console.log(combine("Hello, ", "World")); // "Hello, World"
// combine(1, "World"); ❌ Error: no matching overload

```

- **Overload signatures** come first.
- **Implementation signature** comes last.
- Implementation is typically `any` or union types to handle all cases.

---

## 🔹 **2. Using Overloads With Different Argument Counts**

```TypeScript
function greet(name: string): string;
function greet(name: string, age: number): string;
function greet(name: string, age?: number): string {
  if (age !== undefined) return `Hello, ${name}, age ${age}`;
  return `Hello, ${name}`;
}

console.log(greet("Alice"));       // "Hello, Alice"
console.log(greet("Bob", 25));     // "Hello, Bob, age 25"

```

- Overloads can **vary in number of parameters**.
- Implementation handles optional parameters.

---

## 🔹 **3. Overloads With Different Types**

```TypeScript
function parseInput(input: string): string[];
function parseInput(input: number): string;
function parseInput(input: string | number): string | string[] {
  if (typeof input === "string") return input.split(",");
  return input.toString();
}

console.log(parseInput("a,b,c")); // ["a","b","c"]
console.log(parseInput(123));     // "123"

```

- Overload signatures define **allowed input/output combinations**.
- Implementation uses **type guards** to handle variations.

---

## 🔹 **4. Overloads With Arrays and Rest Parameters**

```TypeScript
function sum(a: number, b: number): number;
function sum(...nums: number[]): number;
function sum(aOrNums: number | number[], b?: number): number {
  if (Array.isArray(aOrNums)) return aOrNums.reduce((acc, n) => acc + n, 0);
  return (b ?? 0) + aOrNums;
}

console.log(sum(1, 2));         // 3
console.log(sum(1, 2, 3, 4));   // 10

```

- Overloads allow **flexible function calls** with type safety.

---

## 🔹 **5. Key Rules for Overloads**

1. **Overload signatures must come first.**
2. **Implementation signature comes last** and handles all cases.
3. **Implementation can be less specific** (e.g., using `any` or union types).
4. **Return type of implementation** should be compatible with all overload signatures.

---

## 📋 **Function Overloads Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Overload signature|`function f(a: number): string;`|Multiple allowed|Describes accepted arguments & return type|
|Implementation|`function f(a: any) {}`|Single actual function|Handles all cases|
|Type safety|❌ disallowed calls|TS enforces overloads|Errors if no matching signature|
|Optional / Rest params|Supported|Can vary per overload|Handled in implementation|
|Different return types|Allowed|`string|string[]`|