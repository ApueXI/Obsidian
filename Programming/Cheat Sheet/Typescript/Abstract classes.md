---
Created: 2025-11-30T14:57
tags:
  - Classes
---
# **Abstract Classes in TypeScript**

Abstract classes are **base classes** that **cannot be instantiated directly**.

- They define **shared properties and methods** for subclasses.
- Can include **abstract methods** that must be implemented in subclasses.

---

## ✅ **1. Basic Syntax**

```TypeScript
abstract class Animal {
  constructor(public name: string) {}

  move(distance: number) {
    console.log(`${this.name} moved ${distance} meters`);
  }

  abstract makeSound(): void; // abstract method
}

// const a = new Animal("Generic"); ❌ Error: Cannot create an instance of an abstract class

```

- `abstract` before class → cannot create instances directly.
- `abstract` before method → must be **implemented in subclass**.

---

## 🔹 **2. Implementing Subclasses**

```TypeScript
class Dog extends Animal {
  makeSound(): void {
    console.log("Woof! Woof!");
  }
}

const dog = new Dog("Rex");
dog.move(10);      // Rex moved 10 meters
dog.makeSound();   // Woof! Woof!

```

- Subclass **must implement all abstract methods**.
- Subclasses inherit concrete methods like `move()`.

---

## 🔹 **3. Abstract Properties**

```TypeScript
abstract class Vehicle {
  abstract wheels: number; // abstract property

  describe() {
    console.log(`This vehicle has ${this.wheels} wheels`);
  }
}

class Car extends Vehicle {
  wheels = 4;
}

const car = new Car();
car.describe(); // This vehicle has 4 wheels

```

- Abstract properties are **declared without values** in the abstract class.
- Subclasses **must assign a value**.

---

## 🔹 **4. Combining Abstract & Concrete Methods**

```TypeScript
abstract class Shape {
  constructor(public name: string) {}

  abstract area(): number;        // must implement in subclass

  describe() {                    // concrete method
    console.log(`Shape: ${this.name}`);
  }
}

class Circle extends Shape {
  constructor(public radius: number) {
    super("Circle");
  }

  area(): number {
    return Math.PI * this.radius ** 2;
  }
}

const circle = new Circle(5);
circle.describe(); // Shape: Circle
console.log(circle.area()); // 78.53981633974483

```

- Concrete methods in abstract classes can **provide default behavior**.
- Abstract methods **force subclasses to implement specific functionality**.

---

## 🔹 **5. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Abstract class|`abstract class ClassName`|`abstract class Animal`|Cannot instantiate directly|
|Abstract method|`abstract methodName(): type;`|`abstract makeSound(): void`|Must implement in subclass|
|Abstract property|`abstract propName: type;`|`abstract wheels: number`|Subclass must assign value|
|Concrete method|`methodName() { ... }`|`describe()`|Can be used directly in subclass|
|Subclass implementation|`class Sub extends AbstractClass`|`class Dog extends Animal`|Must implement all abstract members|

---

**Rule of Thumb**:

- Use **abstract classes** to define a **common blueprint** for related classes.
- Use **abstract methods/properties** to **enforce implementation** in subclasses.
- Use **concrete methods** for **shared behavior**.