---
Created: 2025-12-01T11:47
tags:
  - Type-Safety-Technique
---
# 🔵 TypeScript — **Using Type Guards**

---

# ✅ 1. Full Explanation

## **What Are Type Guards?**

- Type Guards are expressions that **narrow down the type** of a variable within a conditional block.
- They let TypeScript **know the type of a variable at runtime**, enabling **safe property access, method calls, and assignments**.

---

## **Why Use Type Guards**

- Ensure **type safety** in conditional code
- Avoid runtime errors when accessing properties or methods
- Work especially well with **union types,** `**unknown**`**, or** `**any**`

---

## **Common Type Guard Techniques**

### 1. `**typeof**` **Guard**

- For **primitive types** (`string`, `number`, `boolean`, `symbol`, `bigint`, `undefined`)

```TypeScript
function printValue(value: string | number) {
  if (typeof value === "string") {
    console.log(value.toUpperCase()); // ✅ TypeScript knows it's a string
  } else {
    console.log(value.toFixed(2)); // ✅ TypeScript knows it's a number
  }
}

```

---

### 2. `**instanceof**` **Guard**

- For **class instances**

```TypeScript
class Dog { bark() { console.log("Woof"); } }
class Cat { meow() { console.log("Meow"); } }

function speak(animal: Dog | Cat) {
  if (animal instanceof Dog) {
    animal.bark(); // ✅ Safe
  } else {
    animal.meow(); // ✅ Safe
  }
}

```

---

### 3. `**in**` **Guard**

- Checks for **property existence** in objects

```TypeScript
type Fish = { swim: () => void };
type Bird = { fly: () => void };

function move(animal: Fish | Bird) {
  if ("swim" in animal) {
    animal.swim(); // ✅ Fish
  } else {
    animal.fly();  // ✅ Bird
  }
}

```

---

### 4. **Custom Type Predicates**

- Function that **returns a boolean** and narrows type

```TypeScript
interface Admin { role: "admin" }
interface User { role: "user" }

function isAdmin(account: Admin | User): account is Admin {
  return account.role === "admin";
}

const user: Admin | User = { role: "admin" };

if (isAdmin(user)) {
  console.log("Admin privileges"); // ✅ TypeScript knows it's Admin
} else {
  console.log("Regular user");
}

```

- `**account is Admin**` tells TypeScript that inside the `if` block, the type is narrowed.

---

### 5. **Exhaustive Checks with** `**never**`

- Combine type guards with **exhaustive switch statements** for full type safety

```TypeScript
type Shape = { kind: "circle"; radius: number } | { kind: "square"; size: number };

function area(shape: Shape) {
  switch (shape.kind) {
    case "circle": return Math.PI * shape.radius ** 2;
    case "square": return shape.size ** 2;
    default:
      const _exhaustiveCheck: never = shape;
      return _exhaustiveCheck;
  }
}

```

---

## **Gotchas / Pitfalls**

1. `typeof` only works for **primitive types**
2. `instanceof` only works for **classes**
3. Custom type predicates require the `**param is Type**` **syntax**
4. Use type guards for **union types,** `**unknown**`**, or type-safe APIs**

---

# ✅ 2. Summary Table

|Type Guard|Syntax|Example|Notes|
|---|---|---|---|
|`typeof`|`typeof x === "string"`|`if (typeof x === "number")`|For primitive types|
|`instanceof`|`x instanceof ClassName`|`if (obj instanceof Dog)`|For class instances|
|`in`|`'prop' in obj`|`if ("swim" in animal)`|Checks property existence|
|Custom Predicate|`function isType(x): x is Type`|`if (isAdmin(user))`|Returns boolean, narrows type|
|Exhaustive Check|`const _: never = x`|In default switch|Ensures all union members handled|

---

# ✅ 3. Real-World Examples

### **Scenario 1: Union Types**

```TypeScript
function format(input: string | number) {
  if (typeof input === "string") {
    return input.trim();
  } else {
    return input.toFixed(2);
  }
}

```

### **Scenario 2: Class Instances**

```TypeScript
class Car { drive() {} }
class Bike { pedal() {} }

function operate(vehicle: Car | Bike) {
  if (vehicle instanceof Car) vehicle.drive();
  else vehicle.pedal();
}

```

### **Scenario 3: Property Check**

```TypeScript
type Fish = { swim(): void };
type Bird = { fly(): void };

function move(animal: Fish | Bird) {
  if ("swim" in animal) animal.swim();
  else animal.fly();
}

```

### **Scenario 4: Custom Predicate**

```TypeScript
interface Admin { role: "admin" }
interface User { role: "user" }

function isAdmin(account: Admin | User): account is Admin {
  return account.role === "admin";
}

const user: Admin | User = { role: "admin" };

if (isAdmin(user)) console.log("Admin privileges");
else console.log("User privileges");

```

---

# 🔥 Bonus Tips

1. Type guards are **essential for** `**unknown**` **and union types**
2. Combine with **exhaustive switch + never** for full safety
3. Always prefer **type-safe narrowing** over `any` or unsafe casting
4. Use **custom type predicates** for **complex objects** or **external APIs**