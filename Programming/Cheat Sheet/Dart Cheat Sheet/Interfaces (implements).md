---
Created: 2025-09-16T20:08
tags:
  - OOP
---
# 🎯 Dart Interfaces & `implements` Cheat Sheet

## 1. Full Explanation

- **Interfaces** define a **contract** of methods a class must implement.
- In Dart, **every class is also an interface**.
- Use `**implements**` to make a class **adhere to an interface**.
- When a class implements an interface:
    - It **must implement all methods and getters/setters** declared in the interface.
- Different from `extends`:
    - `extends` inherits **implementation** from parent class.
    - `implements` inherits **only the contract**, no implementation is inherited.

---

## 2. Basic Interface Example

```Dart
abstract class Animal {
  void eat();
  void sleep();
}

class Dog implements Animal {
  @override
  void eat() {
    print("Dog is eating");
  }

  @override
  void sleep() {
    print("Dog is sleeping");
  }
}

void main() {
  var dog = Dog();
  dog.eat();   // Dog is eating
  dog.sleep(); // Dog is sleeping
}

```

✅ `Dog` must implement **all methods** of `Animal`.

---

## 3. Implementing Multiple Interfaces

```Dart
abstract class Flyable {
  void fly();
}

abstract class Swimmable {
  void swim();
}

class Duck implements Flyable, Swimmable {
  @override
  void fly() {
    print("Duck is flying");
  }

  @override
  void swim() {
    print("Duck is swimming");
  }
}

void main() {
  var duck = Duck();
  duck.fly();  // Duck is flying
  duck.swim(); // Duck is swimming
}

```

✅ Dart allows **multiple interfaces**, unlike single inheritance.

---

## 4. Interface from Concrete Class

```Dart
class Vehicle {
  void start() {
    print("Vehicle started");
  }
}

// Create interface from concrete class
class Car implements Vehicle {
  @override
  void start() {
    print("Car started");
  }
}

void main() {
  var car = Car();
  car.start(); // Car started
}

```

✅ Any class can act as an **interface**, even if it has implementations.

---

## 5. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Implement interface|`class Child implements Interface {}`|Must implement all members|
|Multiple interfaces|`class Child implements A, B {}`|Supports multiple contracts|
|Difference from extends|`extends` inherits code, `implements` only contract|`implements` ignores parent implementation|
|Interface from class|Any class can act as interface|Forces method implementation|

---

## 6. Real-World Example

💡 **Payment Gateway Example**

```Dart
abstract class Payment {
  void pay(double amount);
}

abstract class Refundable {
  void refund(double amount);
}

class CreditCardPayment implements Payment, Refundable {
  @override
  void pay(double amount) {
    print("Paid \$${amount} with credit card");
  }

  @override
  void refund(double amount) {
    print("Refunded \$${amount} to credit card");
  }
}

void main() {
  var payment = CreditCardPayment();
  payment.pay(100);    // Paid $100 with credit card
  payment.refund(50);  // Refunded $50 to credit card
}

```

✅ `CreditCardPayment` implements **multiple interfaces**, ensuring it provides all required methods.