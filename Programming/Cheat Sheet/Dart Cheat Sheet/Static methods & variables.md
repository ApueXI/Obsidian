---
Created: 2025-09-16T20:10
tags:
  - OOP
---
# 🎯 Dart Static Methods & Variables Cheat Sheet

## 1. Full Explanation

- **Static members** belong to the **class itself**, not to any instance.
- **Static variables** → shared across all instances of the class.
- **Static methods** → can be called without creating an object.
- Cannot access **instance variables or methods** directly inside static members.
- Syntax: `static` keyword

---

## 2. Static Variables

```Dart
class Counter {
  static int count = 0; // shared across all instances

  Counter() {
    count++;
  }
}

void main() {
  Counter(); Counter(); Counter();
  print(Counter.count); // 3
}

```

✅ `count` is **shared across all objects**, updated every time a new instance is created.

---

## 3. Static Methods

```Dart
class MathHelper {
  static double square(double x) {
    return x * x;
  }
}

void main() {
  print(MathHelper.square(5)); // 25
}

```

✅ No need to instantiate `MathHelper`.

---

## 4. Static with Instance Members

```Dart
class Person {
  String name;
  static int population = 0;

  Person(this.name) {
    population++;
  }

  void greet() {
    print("Hello, I'm $name");
  }

  static void showPopulation() {
    print("Population: $population");
  }
}

void main() {
  var p1 = Person("Alice");
  var p2 = Person("Bob");

  p1.greet(); // Hello, I'm Alice
  Person.showPopulation(); // Population: 2
}

```

✅ Static method **cannot access** `**name**` **directly**; must use instance.

---

## 5. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Static variable|`static int count;`|Shared across all instances|
|Static method|`static void method() {}`|Can be called on class directly|
|Accessing instance|Not allowed directly|Use instance reference if needed|
|Accessing static|`ClassName.member` or inside class directly|Both variables & methods|

---

## 6. Real-World Example

💡 **Logger Example**

```Dart
class Logger {
  static int logCount = 0;

  static void log(String message) {
    logCount++;
    print("LOG[$logCount]: $message");
  }
}

void main() {
  Logger.log("App started");   // LOG[1]: App started
  Logger.log("User logged in"); // LOG[2]: User logged in
  print("Total logs: ${Logger.logCount}"); // 2
}

```

✅ `Logger` demonstrates **shared state** and **utility method**.