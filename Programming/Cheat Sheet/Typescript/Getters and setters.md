---
Created: 2025-11-30T14:59
tags:
  - Classes
---
# **Getters and Setters in TypeScript**

Getters and setters provide **controlled access to class properties**.

- **Getters (**`**get**`**)**: retrieve a property value.
- **Setters (**`**set**`**)**: assign a property value with optional **validation or transformation**.
- Allow you to **encapsulate internal state** while keeping a clean interface.

---

## ✅ **1. Basic Getter**

```TypeScript
class Person {
  constructor(private _name: string) {}

  get name(): string {
    return this._name;
  }
}

const alice = new Person("Alice");
console.log(alice.name); // Alice
// alice.name = "Bob"; ❌ Error: no setter

```

- `_name` is **private**.
- `get name()` allows **read access** while keeping the underlying property private.

---

## ✅ **2. Basic Setter**

```TypeScript
class Person {
  private _age: number = 0;

  get age(): number {
    return this._age;
  }

  set age(value: number) {
    if (value < 0) {
      throw new Error("Age cannot be negative");
    }
    this._age = value;
  }
}

const p = new Person();
p.age = 25;          // ✅ Works
console.log(p.age);   // 25
// p.age = -5;        // ❌ Error: Age cannot be negative

```

- Setter **validates the value** before assignment.
- Encapsulates internal logic safely.

---

## 🔹 **3. Using Getters and Setters With Computed Values**

```TypeScript
class Rectangle {
  constructor(private _width: number, private _height: number) {}

  get area(): number {
    return this._width * this._height;
  }

  set width(value: number) {
    if (value <= 0) throw new Error("Width must be positive");
    this._width = value;
  }

  set height(value: number) {
    if (value <= 0) throw new Error("Height must be positive");
    this._height = value;
  }
}

const rect = new Rectangle(5, 10);
console.log(rect.area); // 50
rect.width = 6;
console.log(rect.area); // 60

```

- `area` is **computed dynamically** using the current width and height.
- No setter needed if the value is **read-only**.

---

## 🔹 **4. Readonly Property With Getter**

```TypeScript
class Circle {
  constructor(private _radius: number) {}

  get radius(): number {
    return this._radius;
  }

  get diameter(): number {
    return this._radius * 2;
  }
}

const c = new Circle(5);
console.log(c.radius);   // 5
console.log(c.diameter); // 10

```

- `diameter` is **derived from radius** and cannot be set directly.
- Useful for **calculated values**.

---

## 🔹 **5. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Getter|`get propName()`|`get name(): string { return this._name }`|Read-only access to private property|
|Setter|`set propName(value)`|`set age(value: number) { ... }`|Encapsulates validation or transformation|
|Computed value|`get computedProp()`|`get area(): number`|No setter needed if read-only|
|Readonly via getter|Only `get`|`get diameter()`|Prevents external assignment|

---

**Rule of Thumb**:

- Use **getters** to **read private or computed properties**.
- Use **setters** to **validate or transform values** before assignment.
- Keep **internal properties private** to enforce encapsulation.