---
Created: 2025-08-25T20:00
tags:
  - Object-Oriented-Programming-(OOP)
---
## 1. Full Explanation

### 🔹 What is an Interface?

- An **interface** is a **100% abstract type** in Java (Java 8+ allows default and static methods).
- Declared using the keyword: `interface`
- Contains:
    - **Abstract methods** (no body)
    - **Default methods** (with body)
    - **Static methods** (with body)
    - **Constants** (`public static final` by default)
- Cannot have **instance fields** (except `static final`).
- A class **implements an interface** to provide method definitions.

---

### 🔹 Syntax

```Java
interface Vehicle {
    void start();   // abstract method
    void stop();    // abstract method
}

```

- A class **implements** the interface:

```Java
class Car implements Vehicle {
    @Override
    public void start() {
        System.out.println("Car starts");
    }

    @Override
    public void stop() {
        System.out.println("Car stops");
    }
}

```

---

### 🔹 Multiple Interfaces

- A class can **implement multiple interfaces**, unlike classes (single inheritance only).

```Java
interface Electric {
    void charge();
}

class ElectricCar implements Vehicle, Electric {
    @Override
    public void start() {
        System.out.println("Electric car starts silently");
    }

    @Override
    public void stop() {
        System.out.println("Electric car stops");
    }

    @Override
    public void charge() {
        System.out.println("Charging electric car");
    }
}

```

---

### 🔹 Default and Static Methods (Java 8+)

```Java
interface Vehicle {
    void start();

    default void honk() { // default method
        System.out.println("Vehicle honks");
    }

    static void info() { // static method
        System.out.println("All vehicles info");
    }
}

class Car implements Vehicle {
    @Override
    public void start() {
        System.out.println("Car starts");
    }
}

```

- Call default method via object: `new Car().honk()`
- Call static method via interface: `Vehicle.info()`

---

### 🔹 Key Points

1. **Interface = full abstraction** (no instance fields, mostly abstract methods).
2. **A class implements an interface** to provide method bodies.
3. **Multiple interfaces** can be implemented by one class → **multiple inheritance of type**.
4. **Polymorphism:** interface reference can hold implementing class object.

```Java
Vehicle v = new Car();
v.start(); // Car starts
v.honk();  // Vehicle honks

```

---

### 🔹 Gotchas / Notes

- Methods in interfaces are **public abstract by default**.
- Fields in interfaces are **public static final by default**.
- Supports **loose coupling** in programs.
- Default and static methods **cannot override** each other.

---

## 2. 📊 Summary Table

|Concept|Syntax / Example|Notes|
|---|---|---|
|Interface|`interface Name {}`|100% abstraction (Java 8+ allows default/static methods)|
|Implement interface|`class ClassName implements Interface1, Interface2`|Provide method bodies|
|Default method|`default void method(){}`|Called via object|
|Static method|`static void method(){}`|Called via interface|
|Fields|`int x = 10;`|public static final by default|

---

### 🔹 Real-World Example

**Payment Systems**

```Java
interface Payment {
    void pay(double amount);
}

interface Refundable {
    void refund(double amount);
}

class CreditCard implements Payment, Refundable {
    @Override
    public void pay(double amount) {
        System.out.println("Paid " + amount + " using credit card");
    }

    @Override
    public void refund(double amount) {
        System.out.println("Refunded " + amount + " to credit card");
    }

    public static void main(String[] args) {
        Payment p = new CreditCard();
        p.pay(100); // Paid 100 using credit card

        Refundable r = new CreditCard();
        r.refund(50); // Refunded 50 to credit card
    }
}

```

- Demonstrates **implementing multiple interfaces** and **interface polymorphism**.