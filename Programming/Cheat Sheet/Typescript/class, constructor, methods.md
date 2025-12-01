---
Created: 2025-11-30T14:53
tags:
  - Classes
---
# **Classes in TypeScript**

TypeScript classes are **blueprints for creating objects**, supporting **properties, constructors, and methods**.

- They are **syntactic sugar over JavaScript prototypes**, but with **type safety**.

---

## ✅ **1. Basic Class Syntax**

```TypeScript
class Person {
  name: string; // property
  age: number;

  constructor(name: string, age: number) { // constructor
    this.name = name;
    this.age = age;
  }

  greet(): void { // method
    console.log(`Hello, my name is ${this.name}`);
  }
}

const alice = new Person("Alice", 25);
alice.greet(); // "Hello, my name is Alice"

```

- `class Person { ... }` defines the class.
- `constructor` initializes **new instances**.
- Methods are **functions inside the class**.

---

## 🔹 **2. Readonly and Optional Properties**

```TypeScript
class Car {
  readonly make: string;
  model?: string;

  constructor(make: string, model?: string) {
    this.make = make;
    this.model = model;
  }

  printInfo(): void {
    console.log(`${this.make} ${this.model ?? ""}`);
  }
}

const car = new Car("Toyota");
car.printInfo(); // "Toyota"

```

- `readonly` → cannot be changed after initialization.
- Optional properties (`?`) can be omitted.

---

## 🔹 **3. Access Modifiers**

TypeScript supports **public, private, and protected** modifiers:

```TypeScript
class BankAccount {
  private balance: number; // accessible only inside class
  protected accountNumber: string; // accessible in class & subclasses
  public owner: string; // default, accessible anywhere

  constructor(owner: string, balance: number, accountNumber: string) {
    this.owner = owner;
    this.balance = balance;
    this.accountNumber = accountNumber;
  }

  deposit(amount: number): void {
    this.balance += amount;
  }

  getBalance(): number {
    return this.balance;
  }
}

const acc = new BankAccount("Alice", 1000, "12345");
acc.deposit(500);
console.log(acc.getBalance()); // 1500
// acc.balance ❌ Error: private
// acc.accountNumber ❌ Error: protected

```

- `private` → only inside the class
- `protected` → inside class & subclasses
- `public` → default, accessible anywhere

---

## 🔹 **4. Parameter Properties**

You can declare properties **directly in the constructor parameters**:

```TypeScript
class Employee {
  constructor(public name: string, private salary: number) {}

  getSalary(): number {
    return this.salary;
  }
}

const emp = new Employee("Bob", 5000);
console.log(emp.name); // Bob
// console.log(emp.salary); ❌ Error: private

```

- Saves lines by **combining property declaration and assignment**.

---

## 🔹 **5. Inheritance (Extends)**

```TypeScript
class Animal {
  constructor(public name: string) {}
  move(distance: number) {
    console.log(`${this.name} moved ${distance}m`);
  }
}

class Dog extends Animal {
  bark() {
    console.log("Woof!");
  }
}

const dog = new Dog("Rex");
dog.bark();        // "Woof!"
dog.move(10);      // "Rex moved 10m"

```

- `extends` allows **class inheritance**.
- Subclasses inherit **properties and methods** from the parent class.

---

## 🔹 **6. Static Members**

```TypeScript
class Counter {
  static count = 0;

  static increment() {
    Counter.count++;
  }
}

Counter.increment();
console.log(Counter.count); // 1

```

- `static` members belong to the **class itself**, not instances.

---

## 📋 **Classes Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Class|`class ClassName {}`|`class Person {}`|Blueprint for objects|
|Constructor|`constructor(params) {}`|Initializes instances|Required for initialization|
|Property|`name: string;`|`this.name = name;`|Can use modifiers|
|Method|`methodName(): void {}`|`greet() {}`|Functions inside class|
|Access modifiers|`public`, `private`, `protected`|Controls accessibility|`public` default|
|Parameter properties|`constructor(public x: number)`|Declares & assigns|Saves lines|
|Inheritance|`class Sub extends Parent {}`|Inherits props & methods|Supports polymorphism|
|Static|`static count = 0`|Belongs to class|Not accessible via instance|

---

**Rule of Thumb**:

- Use **classes** to structure objects with **shared behavior**.
- Use **access modifiers** to protect data.
- Use **parameter properties** for concise code.
- Use **static members** for class-level data or utilities.