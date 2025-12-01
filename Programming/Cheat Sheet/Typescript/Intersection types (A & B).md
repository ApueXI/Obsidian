---
Created: 2025-11-30T14:42
tags:
  - Type-System
---
# **Intersection Types (**`**A & B**`**)**

An **intersection type** combines **multiple types into one**, meaning the resulting value **must satisfy** _**all**_ **of the types at once**.

Think of it as:

> A & B = A AND B together

Unlike **unions**, which mean “either one,”

**intersections** mean “both at the same time.”

---

# ✅ Basic Example

```TypeScript
type A = { name: string };
type B = { age: number };

type Person = A & B;

```

Now `Person` must have **both**:

- `name: string`
- `age: number`

```TypeScript
const p: Person = {
  name: "Luis",
  age: 21
};

```

Missing any property = ❌ error.

---

# 🎯 Why Intersection Types Matter

### ✔ Combine types into richer structures

Useful when composing features or models.

### ✔ Enforce complete objects

Guarantees no missing properties.

### ✔ Great for mixing interfaces / traits

Especially common in frameworks and libraries.

---

# 🆚 Union vs. Intersection (Quick Comparison)

|Concept|Meaning|Example|Allows|
|---|---|---|---|
|**Union (**`**A \| B**`**)**|One OR the other|`number \| string`|any type in the union|
|**Intersection (**`**A & B**`**)**|Must be BOTH|`{a} & {b}`|all properties combined|

---

# 🧩 More Examples

## **1. Combining object types**

```TypeScript
type WithID = { id: number };
type WithTimestamps = { createdAt: number; updatedAt: number };

type Entity = WithID & WithTimestamps;

const item: Entity = {
  id: 1,
  createdAt: Date.now(),
  updatedAt: Date.now()
};

```

---

## **2. Using intersections with interfaces**

```TypeScript
interface Fly {
  fly(): void;
}

interface Swim {
  swim(): void;
}

type Duck = Fly & Swim;

const donald: Duck = {
  fly() { console.log("flying"); },
  swim() { console.log("swimming"); }
};

```

---

## **3. Enforcing strict parameter types**

```TypeScript
function handle(data: { name: string } & { email: string }) {
  console.log(data);
}

handle({ name: "Ana", email: "ana@test.com" }); // OK
handle({ name: "Ana" }); // ❌ email missing

```

---

# ⚠️ Gotchas

### ❗ Intersections combine **requirements**, not values

If two types conflict, the result may be impossible.

Example:

```TypeScript
type A = { value: string };
type B = { value: number };

type C = A & B; // ❌ impossible type

```

`value` cannot be both `string` AND `number`.

---

### ❗ Very different from unions

Beginners often confuse:

- `A | B` = one or the other
- `A & B` = both combined

---

# 🚀 Real-World Example (API Response + Metadata)

API returns data with metadata added:

```TypeScript
type Data = { userId: number; username: string };
type Meta = { requestId: string; status: number };

type ApiResponse = Data & Meta;

function logResponse(res: ApiResponse) {
  console.log(
    res.userId,
    res.username,
    res.requestId,
    res.status
  );
}

logResponse({
  userId: 1,
  username: "neo",
  requestId: "req-123",
  status: 200
});

```

Everything must exist — making it perfect for strongly typed APIs.