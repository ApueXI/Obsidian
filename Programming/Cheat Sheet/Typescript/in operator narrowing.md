---
Created: 2025-12-01T11:16
tags:
  - Type-Narrowing
---
# 🔵 TypeScript — `**in**` **Operator Narrowing Cheat Sheet**

---

# ✅ 1. Full Explanation

## **What is** `**in**` **Operator Narrowing?**

The `in` operator is used to **check if a property exists in an object** at runtime.

TypeScript uses this to **narrow union types** based on **property presence**.

---

## **Basic Syntax**

```TypeScript
if ("propertyName" in obj) {
  // obj is narrowed to types that have propertyName
}

```

- `obj` can be a union type
- `"propertyName"` is a string literal (the property name)

---

## **Why it matters**

- Union types often have **different properties**
- You want to safely access a property **without risking runtime errors**
- `in` narrowing tells TypeScript which type you're currently working with

---

## **How Narrowing Works**

Given a union type:

```TypeScript
type Fish = { swim: () => void };
type Bird = { fly: () => void };
type Animal = Fish | Bird;

```

You can check for a property:

```TypeScript
function move(animal: Animal) {
  if ("swim" in animal) {
    // animal is narrowed to Fish
    animal.swim();
  } else {
    // animal is narrowed to Bird
    animal.fly();
  }
}

```

---

## **Gotchas / Pitfalls**

### ❗ 1. Only checks property **existence**, not type

```TypeScript
if ("swim" in animal) {
  // swim exists, but TypeScript doesn't check return type of swim
}

```

---

### ❗ 2. Works only with **object types**

Cannot use `in` on primitives like `string`, `number`, or `boolean`.

---

### ❗ 3. Works well with **discriminated unions**

Especially when objects share some properties but differ in one key property.

---

### ❗ 4. Not runtime-proof for `undefined` objects

```TypeScript
let obj: {a: number} | undefined;
if ("a" in obj) // ❌ Error: obj might be undefined

```

Use a null check first:

```TypeScript
if (obj && "a" in obj) { ... }

```

---

# ✅ 2. Summary Table

|Feature|Behavior|Example|
|---|---|---|
|`prop in obj`|Narrows union types to objects that have `prop`|`"swim" in animal`|
|Works with unions|✅|`Fish|
|Works with optional properties|✅|`{a?: number}|
|Works only on objects|✅|`{}`, classes|
|Does **not** check primitive types|❌|`number`, `string`|

---

# ✅ 3. Real-World Example (Practical)

## **Scenario: API Responses**

You have different API responses:

```TypeScript
type SuccessResponse = { data: string; status: 200 };
type ErrorResponse = { error: string; status: 400 | 500 };
type Response = SuccessResponse | ErrorResponse;

```

You want to **handle success vs error** safely.

---

### **Code using** `**in**` **narrowing**

```TypeScript
function handleApiResponse(res: Response) {
  if ("data" in res) {
    // Narrowed to SuccessResponse
    console.log("Data:", res.data);
  } else {
    // Narrowed to ErrorResponse
    console.error("Error:", res.error);
  }
}

```

### What TypeScript understands:

|Condition|Narrowed Type|
|---|---|
|`"data" in res`|SuccessResponse|
|else|ErrorResponse|

---

# 🔥 Bonus Real-World Example — Mixed Types

```TypeScript
type Cat = { meow: () => void };
type Dog = { bark: () => void };
type Pet = Cat | Dog;

function play(pet: Pet) {
  if ("meow" in pet) {
    pet.meow();  // Safe: pet is Cat
  } else {
    pet.bark();  // Safe: pet is Dog
  }
}

```