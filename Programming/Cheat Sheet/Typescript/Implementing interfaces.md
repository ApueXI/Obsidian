---
Created: 2025-11-30T15:00
tags:
  - Classes
---
# **Implementing Interfaces in TypeScript Classes**

Classes in TypeScript can **implement interfaces** to **enforce a specific structure**.

- Ensures that the class contains **all properties and methods** defined in the interface.
- Helps with **type safety** and **consistent API design**.

---

## ✅ **1. Basic Syntax**

```TypeScript
interface Animal {
  name: string;
  makeSound(): void;
}

class Dog implements Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  makeSound(): void {
    console.log("Woof! Woof!");
  }
}

const dog = new Dog("Rex");
console.log(dog.name); // Rex
dog.makeSound();       // Woof! Woof!

```

- `class Dog implements Animal` → Dog **must define all properties and methods** of `Animal`.
- TypeScript ensures **compile-time safety**.

---

## 🔹 **2. Multiple Interfaces**

A class can implement **multiple interfaces**:

```TypeScript
interface Flyable {
  fly(): void;
}

interface Swimmable {
  swim(): void;
}

class Duck implements Flyable, Swimmable {
  fly(): void {
    console.log("Duck is flying");
  }

  swim(): void {
    console.log("Duck is swimming");
  }
}

const duck = new Duck();
duck.fly();  // Duck is flying
duck.swim(); // Duck is swimming

```

- Each interface’s members **must be implemented** in the class.

---

## 🔹 **3. Interfaces With Optional Properties**

```TypeScript
interface Person {
  name: string;
  age?: number; // optional
}

class Employee implements Person {
  constructor(public name: string, public age?: number) {}
}

const emp = new Employee("Alice");
console.log(emp.name); // Alice
console.log(emp.age);  // undefined

```

- Optional properties (`?`) are **not required**, giving flexibility.

---

## 🔹 **4. Readonly Properties in Interfaces**

```TypeScript
interface Vehicle {
  readonly wheels: number;
  drive(): void;
}

class Car implements Vehicle {
  readonly wheels = 4;

  drive(): void {
    console.log("Driving...");
  }
}

const car = new Car();
car.drive();
// car.wheels = 6; ❌ Error: readonly

```

- Classes **must respect readonly constraints** defined in interfaces.

---

## 🔹 **5. Practical Use Case**

```TypeScript
interface Logger {
  log(message: string): void;
  error(message: string): void;
}

class ConsoleLogger implements Logger {
  log(message: string) {
    console.log("LOG:", message);
  }

  error(message: string) {
    console.error("ERROR:", message);
  }
}

const logger: Logger = new ConsoleLogger();
logger.log("Hello!");   // LOG: Hello!
logger.error("Oops!");  // ERROR: Oops!

```

- Using **interfaces with classes** ensures **consistent APIs**.

---

## 🔹 **6. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Implement interface|`class ClassName implements InterfaceName`|`class Dog implements Animal`|Must implement all interface members|
|Multiple interfaces|`implements InterfaceA, InterfaceB`|`class Duck implements Flyable, Swimmable`|Each interface must be fully implemented|
|Optional properties|`prop?: type`|`age?: number`|Implementation is optional|
|Readonly|`readonly prop: type`|`readonly wheels = 4`|Cannot reassign in class|
|Practical use|`interface Logger` → `class ConsoleLogger`|Ensures consistent API|Useful for dependency injection|

---

**Rule of Thumb**:

- Use **interfaces with classes** to **enforce structure** and **type safety**.
- Combine with **optional and readonly properties** to make classes flexible yet safe.
- Multiple interfaces allow **composition of capabilities** without multiple inheritance.