---
Created: 2025-09-16T20:08
tags:
  - OOP
---
# 🎯 Dart Abstract Classes & Methods Cheat Sheet

## 1. Full Explanation

- **Abstract classes**: Classes that **cannot be instantiated directly**.
- Serve as **blueprints** for subclasses.
- Can contain:
    - **Fields**
    - **Concrete methods** (with implementation)
    - **Abstract methods** (without implementation)
- **Abstract methods** must be **overridden** in concrete subclasses.

---

## 2. Basic Abstract Class Example

```Dart
abstract class Animal {
  void eat(); // abstract method

  void sleep() {
    print("Animal is sleeping"); // concrete method
  }
}

class Dog extends Animal {
  @override
  void eat() {
    print("Dog is eating");
  }
}

void main() {
  // var a = Animal(); // ❌ Cannot instantiate abstract class
  var dog = Dog();
  dog.eat();   // Dog is eating
  dog.sleep(); // Animal is sleeping
}

```

✅ Abstract class enforces **mandatory method implementation** in subclasses.

---

## 3. Multiple Abstract Methods

```Dart
abstract class Shape {
  double area(); // abstract
  double perimeter(); // abstract
}

class Circle extends Shape {
  double radius;
  Circle(this.radius);

  @override
  double area() => 3.14 * radius * radius;

  @override
  double perimeter() => 2 * 3.14 * radius;
}

void main() {
  var c = Circle(5);
  print("Area: ${c.area()}, Perimeter: ${c.perimeter()}");
}

```

✅ Each subclass **must implement all abstract methods**.

---

## 4. Concrete Methods in Abstract Class

```Dart
abstract class Vehicle {
  void start(); // abstract

  void stop() {
    print("Vehicle stopped"); // concrete
  }
}

class Car extends Vehicle {
  @override
  void start() {
    print("Car started");
  }
}

void main() {
  var car = Car();
  car.start(); // Car started
  car.stop();  // Vehicle stopped
}

```

✅ Abstract classes can provide **default behavior** while forcing certain methods to be implemented.

---

## 5. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Abstract class|`abstract class ClassName {}`|Cannot instantiate directly|
|Abstract method|`void method();`|No implementation, must override|
|Concrete method|`void method() { ... }`|Optional for subclasses|
|Subclass override|`@override void method() { ... }`|Required for abstract methods|

---

## 6. Real-World Example

💡 **Payment System Example**

```Dart
abstract class Payment {
  void pay(double amount); // abstract

  void receipt(double amount) {
    print("Paid \$${amount}");
  }
}

class CreditCardPayment extends Payment {
  @override
  void pay(double amount) {
    print("Paying \$${amount} with credit card");
  }
}

class PayPalPayment extends Payment {
  @override
  void pay(double amount) {
    print("Paying \$${amount} via PayPal");
  }
}

void main() {
  var payment1 = CreditCardPayment();
  payment1.pay(100);      // Paying $100 with credit card
  payment1.receipt(100);  // Paid $100

  var payment2 = PayPalPayment();
  payment2.pay(200);      // Paying $200 via PayPal
  payment2.receipt(200);  // Paid $200
}

```

✅ Abstract classes provide a **common interface** while allowing multiple implementations.