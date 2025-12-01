---
Created: 2025-11-30T14:56
tags:
  - Classes
---
# **Inheritance in TypeScript**

Inheritance allows a **class (subclass) to extend another class (superclass)**, inheriting its **properties and methods**.

- Promotes **code reuse** and **polymorphism**.

---

## ✅ **1. Basic Syntax**

```TypeScript
class Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  move(distance: number) {
    console.log(`${this.name} moved ${distance} meters`);
  }
}

class Dog extends Animal {
  bark() {
    console.log("Woof! Woof!");
  }
}

const dog = new Dog("Rex");
dog.bark();        // Woof! Woof!
dog.move(10);      // Rex moved 10 meters

```

- `class Dog extends Animal` → Dog inherits **name property** and **move method**.
- `Dog` can also define **additional methods** (`bark`).

---

## 🔹 **2. Using** `**super**`

- `super` is used to **call the superclass constructor or methods**.

```TypeScript
class Cat extends Animal {
  constructor(name: string, public color: string) {
    super(name); // call Animal constructor
  }

  describe() {
    console.log(`${this.name} is ${this.color}`);
  }
}

const cat = new Cat("Whiskers", "white");
cat.describe();  // Whiskers is white
cat.move(5);     // Whiskers moved 5 meters

```

- Must call `super()` in the constructor of a subclass **before using** `**this**`.

---

## 🔹 **3. Overriding Methods**

- Subclasses can **override superclass methods**.

```TypeScript
class Bird extends Animal {
  move(distance: number) {
    console.log(`${this.name} flies ${distance} meters`);
  }
}

const bird = new Bird("Parrot");
bird.move(20); // Parrot flies 20 meters

```

- TypeScript ensures **type safety** while overriding.

---

## 🔹 **4. Inheritance with Access Modifiers**

```TypeScript
class Vehicle {
  protected speed: number = 0;

  protected accelerate(amount: number) {
    this.speed += amount;
  }
}

class Car extends Vehicle {
  drive() {
    this.accelerate(50); // ✅ protected accessible in subclass
    console.log(`Speed: ${this.speed}`);
  }
}

const car = new Car();
car.drive();
// car.speed ❌ Error: protected
// car.accelerate(10) ❌ Error: protected

```

- `protected` members are accessible in **subclasses**, not outside.

---

## 🔹 **5. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Subclass|`class Sub extends Super`|`class Dog extends Animal`|Inherits properties & methods|
|`super` constructor|`super(args)`|`super(name)`|Must call before `this`|
|`super` method|`super.method()`|Call overridden method|Access parent implementation|
|Method overriding|Define same method in subclass|`move()` in Bird|TS ensures type safety|
|Protected access|`protected prop` or `protected method()`|Accessible in subclass|Not accessible outside|

---

**Rule of Thumb**:

- Use **extends** to create a subclass that **reuses and extends functionality**.
- Use **super** to call **parent constructor or methods**.
- Combine