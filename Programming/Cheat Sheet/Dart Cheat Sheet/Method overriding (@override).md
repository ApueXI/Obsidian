---
Created: 2025-09-16T20:09
tags:
  - OOP
---
# 🎯 Dart Method Overriding Cheat Sheet

## 1. Full Explanation

- **Method overriding** = redefining a method in a **subclass** that exists in the **parent class**.
- Use `**@override**` **annotation** to indicate intentional overriding.
- Can call **parent method** using `super.methodName()`.
- Important for **polymorphism**, allowing subclasses to behave differently while sharing the same interface.

---

## 2. Basic Example

```Dart
class Animal {
  void speak() {
    print("Animal makes a sound");
  }
}

class Dog extends Animal {
  @override
  void speak() {
    print("Dog barks");
  }
}

void main() {
  var dog = Dog();
  dog.speak(); // Dog barks
}

```

✅ `Dog` overrides `speak()` to provide **custom behavior**.

---

## 3. Calling Superclass Method

```Dart
class Animal {
  void move() {
    print("Animal moves");
  }
}

class Bird extends Animal {
  @override
  void move() {
    super.move(); // call parent implementation
    print("Bird flies");
  }
}

void main() {
  var bird = Bird();
  bird.move();
  // Output:
  // Animal moves
  // Bird flies
}

```

✅ `super` lets you **reuse parent logic** and add extra behavior.

---

## 4. Polymorphic Example

```Dart
class Shape {
  void draw() {
    print("Drawing a shape");
  }
}

class Circle extends Shape {
  @override
  void draw() {
    print("Drawing a circle");
  }
}

void main() {
  Shape shape = Circle(); // polymorphism
  shape.draw();           // Drawing a circle
}

```

✅ Overridden methods support **runtime polymorphism**.

---

## 5. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Override method|`@override void method() { ... }`|Must match signature|
|Call parent method|`super.method()`|Optional, reuses parent logic|
|Polymorphism|`Parent obj = Child();`|Overridden method runs from **child**|
|Required annotation|`@override`|Not strictly required, but improves readability & safety|

---

## 6. Real-World Example

💡 **Vehicle Example**

```Dart
class Vehicle {
  void start() {
    print("Vehicle started");
  }
}

class Car extends Vehicle {
  @override
  void start() {
    super.start(); // call parent
    print("Car engine is running");
  }
}

void main() {
  var car = Car();
  car.start();
  // Output:
  // Vehicle started
  // Car engine is running
}

```

✅ Demonstrates **method overriding** + **calling parent method**.