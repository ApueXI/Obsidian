---
Created: 2025-09-16T20:07
tags:
  - OOP
---
# 🎯 Dart Inheritance Cheat Sheet

## 1. Full Explanation

- **Inheritance** allows a class (**subclass/child**) to acquire **fields and methods** of another class (**superclass/parent**).
- Use the keyword `**extends**` to define a subclass.
- Subclasses can:
    - **Reuse** parent class functionality
    - **Override** parent methods
    - **Add** new fields and methods

---

## 2. Basic Example

```Dart
class Animal {
  void eat() {
    print("Animal is eating");
  }
}

class Dog extends Animal {
  void bark() {
    print("Dog is barking");
  }
}

void main() {
  var dog = Dog();
  dog.eat();  // Inherited from Animal
  dog.bark(); // Defined in Dog
}

```

✅ `Dog` inherits `eat()` from `Animal`.

---

## 3. Overriding Methods

```Dart
class Animal {
  void speak() {
    print("Animal makes a sound");
  }
}

class Cat extends Animal {
  @override
  void speak() {
    print("Cat meows");
  }
}

void main() {
  var cat = Cat();
  cat.speak(); // Cat meows
}

```

✅ Use `@override` annotation to indicate you’re overriding a method.

---

## 4. Calling Superclass Methods

```Dart
class Animal {
  void move() {
    print("Animal moves");
  }
}

class Bird extends Animal {
  @override
  void move() {
    super.move(); // call parent method
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

✅ `super` allows access to parent class methods.

---

## 5. Inheritance with Constructors

```Dart
class Person {
  String name;
  Person(this.name);
}

class Employee extends Person {
  int id;
  Employee(String name, this.id) : super(name); // call parent constructor
}

void main() {
  var emp = Employee("Alice", 101);
  print("${emp.name}, ID: ${emp.id}"); // Alice, ID: 101
}

```

✅ Use `super(...)` to pass arguments to the parent constructor.

---

## 6. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Extend a class|`class Child extends Parent {}`|Child inherits fields/methods|
|Override method|`@override void method() {}`|Customize parent behavior|
|Call parent method|`super.method()`|Access original method|
|Parent constructor|`Child(...) : super(args)`|Must call parent constructor if required|

---

## 7. Real-World Example

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
    super.start();
    print("Car engine is running");
  }

  void honk() {
    print("Car horn: Beep beep!");
  }
}

void main() {
  var myCar = Car();
  myCar.start();
  myCar.honk();
  // Output:
  // Vehicle started
  // Car engine is running
  // Car horn: Beep beep!
}

```

✅ Demonstrates **reuse, override, and new functionality**.