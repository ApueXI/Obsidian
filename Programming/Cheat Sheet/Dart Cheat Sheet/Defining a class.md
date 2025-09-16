---
Created: 2025-09-16T20:02
tags:
  - Classes-&-Objects
---
# 🎯 Dart Class Definition Cheat Sheet

## 1. Full Explanation

- A **class** in Dart is a blueprint for creating **objects** (instances).
- Classes can contain:
    - **Fields** (variables/properties)
    - **Methods** (functions inside class)
    - **Constructors** (special methods to create objects)
- Dart supports **single inheritance**, **interfaces (via** `**implements**`**)**, and **mixins (**`**with**`**)**.

---

## 2. Basic Class Example

```Dart
class Person {
  // Fields
  String name;
  int age;

  // Constructor
  Person(this.name, this.age);

  // Method
  void introduce() {
    print("Hi, I'm $name and I'm $age years old.");
  }
}

void main() {
  var p = Person("Alice", 25);
  p.introduce(); // Hi, I'm Alice and I'm 25 years old.
}

```

---

## 3. Fields and Methods

```Dart
class Car {
  String brand;
  int year;

  Car(this.brand, this.year);

  void drive() {
    print("The $brand is driving!");
  }
}

```

---

## 4. Named Constructor

```Dart
class Point {
  int x, y;

  Point(this.x, this.y);

  // Named constructor
  Point.origin() : x = 0, y = 0;
}

void main() {
  var p1 = Point(10, 20);
  var p2 = Point.origin();

  print("p1: (${p1.x}, ${p1.y})"); // (10, 20)
  print("p2: (${p2.x}, ${p2.y})"); // (0, 0)
}

```

---

## 5. Using `this`

```Dart
class Animal {
  String name;

  Animal(this.name);

  void speak() {
    print("$name makes a sound!");
  }
}

```

---

## 6. Flutter Example

```Dart
class TodoItem {
  String title;
  bool isDone;

  TodoItem(this.title, {this.isDone = false});

  void toggle() {
    isDone = !isDone;
  }
}

void main() {
  var todo = TodoItem("Learn Dart");
  print(todo.isDone); // false
  todo.toggle();
  print(todo.isDone); // true
}

```

---

## 7. Summary Table

|Feature|Example|Notes|
|---|---|---|
|Class definition|`class Person { ... }`|Blueprint|
|Constructor|`Person(this.name, this.age);`|Auto-assigns fields|
|Named constructor|`Point.origin()`|Custom constructors|
|Method|`void drive(){}`|Functions inside class|
|`this` keyword|`this.name`|Refers to current object|

---

## 8. Real-World Example

💡 **Dart Class for a Bank Account**

```Dart
class BankAccount {
  String owner;
  double balance;

  BankAccount(this.owner, this.balance);

  void deposit(double amount) {
    balance += amount;
    print("$owner deposited $amount. Balance: $balance");
  }

  void withdraw(double amount) {
    if (amount <= balance) {
      balance -= amount;
      print("$owner withdrew $amount. Balance: $balance");
    } else {
      print("Insufficient funds for $owner");
    }
  }
}

void main() {
  var account = BankAccount("Alice", 1000.0);
  account.deposit(200);
  account.withdraw(500);
  account.withdraw(800);
}

```

✅ Demonstrates fields, methods, and state changes.