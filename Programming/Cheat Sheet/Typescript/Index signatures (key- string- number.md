---
Created: 2025-11-30T14:50
tags:
  - Object-Types
---
# **Index Signatures in TypeScript**

Index signatures allow objects to have **dynamic property names** while still **enforcing type constraints** on their values.

- Useful when you don’t know all property names in advance.
- You can specify the **key type** and the **value type**.

---

## ✅ **1. Basic Syntax**

```TypeScript
interface Scores {
  [key: string]: number;
}

const playerScores: Scores = {
  Alice: 10,
  Bob: 15
};

console.log(playerScores.Alice); // 10
console.log(playerScores["Bob"]); // 15

```

- `[key: string]: number` → **any string key** must have a **number value**.

---

## 🔹 **2. Index Signatures with Optional Properties**

You can combine index signatures with known properties:

```TypeScript
interface Scores {
  total: number;       // known property
  [key: string]: number; // any additional string keys
}

const gameScores: Scores = {
  total: 100,
  Alice: 10,
  Bob: 15
};

```

- The **known property** must also satisfy the type of the index signature.
- Here, `total` is a `number`, matching `[key: string]: number`.

---

## 🔹 **3. Number Index Signature**

You can also use **numbers as keys**:

```TypeScript
interface WeekTemperatures {
  [day: number]: number;
}

const temps: WeekTemperatures = {
  1: 23,
  2: 25,
  3: 22
};

console.log(temps[1]); // 23

```

- Keys are treated as numbers.
- Useful for **arrays or maps with numeric keys**.

---

## 🔹 **4. Index Signature with Union Values**

```TypeScript
interface Config {
  [key: string]: string | number;
}

const settings: Config = {
  theme: "dark",
  fontSize: 14
};

```

- Values can be **union types** to allow flexibility.

---

## 🔹 **5. Readonly Index Signatures**

```TypeScript
interface ReadonlyScores {
  readonly [key: string]: number;
}

const scores: ReadonlyScores = { Alice: 10 };
// scores.Alice = 15; ❌ Error

```

- Prevents modification of dynamic properties.

---

## 🔹 **6. Practical Example**

```TypeScript
function sumValues(obj: { [key: string]: number }): number {
  return Object.values(obj).reduce((acc, val) => acc + val, 0);
}

const scores = { Alice: 10, Bob: 15, Carol: 20 };
console.log(sumValues(scores)); // 45

```

- Index signatures are great for **generic key-value objects** with unknown keys at design time.

---

## 📋 **Index Signatures Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|String index|`[key: string]: number`|`interface Scores { [key: string]: number }`|Dynamic string keys|
|Number index|`[key: number]: string`|`interface Days { [key: number]: string }`|Dynamic numeric keys|
|Optional known properties|`[key: string]: number; total: number`|Mix of fixed + dynamic|Known props must match index type|
|Union values|`[key: string]: string|number`|Flexible values|
|Readonly index|`readonly [key: string]: number`|Immutable dynamic properties|Cannot reassign values|

---

**Rule of Thumb**:

- Use **index signatures** when the object has **dynamic keys** whose names are not known in advance.
- Combine with **readonly**, **optional**, or **union types** for flexibility and safety.