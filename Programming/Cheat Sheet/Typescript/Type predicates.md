---
Created: 2025-12-01T11:18
tags:
  - Type-Narrowing
---
# 🔵 TypeScript — **Type Predicates / Custom Type Guards Cheat Sheet**

---

# ✅ 1. Full Explanation

## **What are Type Predicates?**

A **type predicate** is a special TypeScript syntax that allows a **function to tell the compiler**:

> “If this function returns true, then the value is of this specific type.”

This enables **custom, reusable narrowing logic** beyond `typeof`, `instanceof`, or `in`.

---

## **Basic Syntax**

```TypeScript
function isType(value: unknown): value is Type {
  // return true if value is Type
}

```

- `value is Type` → type predicate
- `unknown` or union type is usually the input
- Returns `boolean` at runtime

---

## **Why Use Type Predicates**

- For **complex types** or **union types**
- For **nested object structures**
- To **reuse narrowing logic** across multiple places
- Works anywhere TypeScript expects **type narrowing**

---

## **How it Works**

Given a union type:

```TypeScript
type Fish = { swim: () => void };
type Bird = { fly: () => void };
type Animal = Fish | Bird;

```

We can create a custom type guard:

```TypeScript
function isFish(animal: Animal): animal is Fish {
  return (animal as Fish).swim !== undefined;
}

```

Now TypeScript understands:

```TypeScript
function move(animal: Animal) {
  if (isFish(animal)) {
    animal.swim(); // Safe
  } else {
    animal.fly();  // Safe
  }
}

```

---

## **Gotchas / Pitfalls**

1. Type predicate functions must **return boolean**
2. They **must not mutate** the input type
3. The **predicate narrows only inside the conditional block**
4. Overly complex logic can confuse TypeScript; keep it simple and clear

---

# ✅ 2. Summary Table

|Feature|Purpose|Example|
|---|---|---|
|Custom type guard|Narrows union types|`function isFish(animal: Animal): animal is Fish`|
|Return type must be `value is Type`|Signals TypeScript|`value is Fish`|
|Used with `if`|Safe to access narrowed type|`if (isFish(a)) { a.swim() }`|
|Works with unions|✅|`Fish|
|Reusable|✅|Can call multiple times|

---

# ✅ 3. Real-World Example (Practical)

## **Scenario:**

You have a mixed list of animals:

```TypeScript
type Cat = { meow: () => void; name: string };
type Dog = { bark: () => void; name: string };
type Pet = Cat | Dog;

```

### **Step 1: Define type guard functions**

```TypeScript
function isCat(pet: Pet): pet is Cat {
  return (pet as Cat).meow !== undefined;
}

function isDog(pet: Pet): pet is Dog {
  return (pet as Dog).bark !== undefined;
}

```

---

### **Step 2: Use type guards for safe narrowing**

```TypeScript
function playWithPet(pet: Pet) {
  if (isCat(pet)) {
    pet.meow(); // Safe
  } else if (isDog(pet)) {
    pet.bark(); // Safe
  }
}

```

- TypeScript knows exactly which type you’re working with inside each branch.

---

# 🔥 Bonus Real-World Example — API Responses

```TypeScript
type Success = { status: 200; data: string };
type Failure = { status: 400 | 500; error: string };
type Response = Success | Failure;

function isSuccess(res: Response): res is Success {
  return res.status === 200;
}

function handleResponse(res: Response) {
  if (isSuccess(res)) {
    console.log("Data:", res.data); // Safe
  } else {
    console.error("Error:", res.error); // Safe
  }
}

```

- Makes complex response handling **type-safe**
- Can be reused in multiple functions