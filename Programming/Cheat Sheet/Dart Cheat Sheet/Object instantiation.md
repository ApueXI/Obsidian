---
Created: 2025-09-16T20:05
tags:
  - Classes-&-Objects
---
# 🎯 Dart Object Instantiation Cheat Sheet

## 1. Full Explanation

- **Object instantiation** = creating an instance of a class.
- Use the **constructor** of the class with the `new` keyword (optional in Dart 2+) or call it directly.
- Syntax:

```Dart
ClassName objectName = ClassName(constructorArgs);

```

- Objects can be stored in variables and used to access **fields, methods, getters, setters**.

---

## 2. Basic Instantiation

```Dart
class Person {
  String name;
  int age;

  Person(this.name, this.age);

  void introduce() {
    print("Hi, I'm $name, $age years old.");
  }
}

void main() {
  var alice = Person("Alice", 25); // Instantiate object
  alice.introduce(); // Hi, I'm Alice, 25 years old.
}

```

✅ No need for `new` in modern Dart: `var obj = ClassName(...)`

---

## 3. Using Named Constructors

```Dart
class Point {
  int x, y;

  Point(this.x, this.y);

  Point.origin() : x = 0, y = 0;
}

void main() {
  var p1 = Point(10, 20);   // Default constructor
  var p2 = Point.origin();   // Named constructor

  print("p1: (${p1.x}, ${p1.y})"); // (10, 20)
  print("p2: (${p2.x}, ${p2.y})"); // (0, 0)
}

```

---

## 4. Using Factory Constructors

```Dart
class Logger {
  final String name;
  static final Map<String, Logger> _cache = {};

  Logger._internal(this.name);

  factory Logger(String name) {
    if (_cache.containsKey(name)) {
      return _cache[name]!;
    } else {
      final logger = Logger._internal(name);
      _cache[name] = logger;
      return logger;
    }
  }
}

void main() {
  var log1 = Logger("Main");
  var log2 = Logger("Main");

  print(log1 == log2); // true, same cached instance
}

```

✅ Factory constructors control instantiation logic and can return existing objects.

---

## 5. Summary Table

|Constructor Type|Example Instantiation|Notes|
|---|---|---|
|Default|`var obj = ClassName(args);`|Normal object creation|
|Named|`var obj = ClassName.named(args);`|Multiple ways to create objects|
|Factory|`var obj = ClassName.factory(args);`|Custom logic, caching, subclass|

---

## 6. Real-World Example

💡 **Bank Account Instantiation**

```Dart
class BankAccount {
  String owner;
  double balance;

  BankAccount(this.owner, this.balance);
}

void main() {
  var aliceAccount = BankAccount("Alice", 1000);
  var bobAccount = BankAccount("Bob", 500);

  print("${aliceAccount.owner}: \$${aliceAccount.balance}"); // Alice: $1000
  print("${bobAccount.owner}: \$${bobAccount.balance}");     // Bob: $500
}

```

✅ Demonstrates creating multiple **instances with independent state**.