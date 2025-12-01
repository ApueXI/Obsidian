---
Created: 2025-12-01T11:18
tags:
  - Type-Narrowing
---
# 🔵 TypeScript — **Control-Flow-Based Narrowing Cheat Sheet**

---

# ✅ 1. Full Explanation

## **What is Control-Flow-Based Narrowing?**

Control-flow-based narrowing is TypeScript’s ability to **refine the type of a variable** depending on **how the program executes**, based on:

- `if` / `else` statements
- `switch` statements
- `throw` / `return` / `break`
- Loops and type guards

It **analyzes the flow of code** to determine what type a variable **must** be at a certain point.

---

## **Why it matters**

- Helps TypeScript **infer the correct type automatically** without manual casting
- Reduces runtime errors
- Works across complex logic, unlike simple `typeof` or `instanceof` checks

---

## **Basic Concept**

```TypeScript
function example(value: string | number) {
  if (typeof value === "string") {
    // TypeScript knows: value is string
    console.log(value.toUpperCase());
  } else {
    // TypeScript knows: value is number
    console.log(value.toFixed(2));
  }
}

```

- Type narrowing is **not limited to one check**; TS tracks the type through the flow.

---

## **Key Control Flow Patterns**

### 1. `if / else` narrowing

```TypeScript
if (x !== undefined) {
  // x is definitely defined
}

```

### 2. `return` / `throw` / `break` / `continue`

```TypeScript
function doSomething(x?: number) {
  if (!x) return; // after this line, TS knows x is defined
  console.log(x.toFixed(2));
}

```

### 3. `switch` statement

```TypeScript
type Animal = "dog" | "cat";

function speak(a: Animal) {
  switch (a) {
    case "dog":
      // a is "dog"
      break;
    case "cat":
      // a is "cat"
      break;
  }
}

```

### 4. `const` assertion in loops / destructuring

```TypeScript
const arr: (string | number)[] = [1, "a"];
for (const item of arr) {
  if (typeof item === "string") {
    // item is string here
  } else {
    // item is number here
  }
}

```

---

## **Gotchas / Pitfalls**

1. **Variables with** `**any**` **type** are not narrowed
2. **Union types with overlapping properties** may require `in` or custom type guards
3. Narrowing **does not mutate the type of the original variable** outside the block if reassigned
4. Complex nested conditions can confuse TypeScript unless explicit checks are made

---

# ✅ 2. Summary Table

|Pattern|How It Narrows|Example|
|---|---|---|
|`if / else`|Narrows type within the block|`if (typeof x === "string")`|
|`return` / `throw`|Narrows type after exit|`if (!x) return;` → x is defined afterward|
|`switch`|Narrows based on matched case|`switch(a) { case "dog": ... }`|
|Loops (`for` / `while`)|Narrows type inside iteration|`for (const item of arr) { if (typeof item === "number") ... }`|
|`in` operator|Narrows based on property presence|`'swim' in animal`|
|`instanceof`|Narrows based on constructor|`x instanceof Date`|

---

# ✅ 3. Real-World Example (Practical)

## **Scenario:**

You’re processing API responses that could be different shapes:

```TypeScript
type Success = { data: string; status: 200 };
type Error = { error: string; status: 400 | 500 };
type Response = Success | Error;

function handleResponse(res: Response | null) {
  if (!res) {
    throw new Error("No response");
  }

  switch (res.status) {
    case 200:
      // TypeScript knows: res is Success
      console.log("Data:", res.data);
      break;
    case 400:
    case 500:
      // TypeScript knows: res is Error
      console.error("Error:", res.error);
      break;
  }
}

```

**Control-flow-based narrowing** ensures:

- After `if (!res) throw`, `res` is non-null
- Within each `switch` case, `res` has the correct type (`Success` or `Error`)

---

# 🔥 Bonus Real-World Scenario — Loops with Union Types

```TypeScript
type Pet = { meow?: () => void; bark?: () => void };
const pets: Pet[] = [{ meow: () => console.log("meow") }, { bark: () => console.log("bark") }];

for (const pet of pets) {
  if (pet.meow) {
    pet.meow(); // pet is narrowed to Cat-like
  } else {
    pet.bark(); // pet is narrowed to Dog-like
  }
}

```

- TypeScript **tracks the narrowed type inside the loop** automatically.