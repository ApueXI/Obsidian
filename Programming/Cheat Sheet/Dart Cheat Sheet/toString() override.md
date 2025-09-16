---
Created: 2025-09-16T20:06
tags:
  - Classes-&-Objects
---
# 🎯 Dart `toString()` Override Cheat Sheet

## 1. Full Explanation

- Every Dart object inherits a `**toString()**` **method** from the `Object` class.
- Default `toString()` → prints something like `Instance of 'ClassName'`.
- Overriding `toString()` → provides a **custom string representation** of the object.
- Useful for:
    - Debugging (`print(object)`)
    - Logging
    - Displaying objects in Flutter widgets

---

## 2. Basic Example

```Dart
class Person {
  String name;
  int age;

  Person(this.name, this.age);

  @override
  String toString() {
    return "Person(name: $name, age: $age)";
  }
}

void main() {
  var alice = Person("Alice", 25);
  print(alice); // Person(name: Alice, age: 25)
}

```

✅ `print(alice)` automatically calls `toString()`.

---

## 3. Using Short Arrow Syntax

```Dart
class Point {
  int x, y;

  Point(this.x, this.y);

  @override
  String toString() => "Point(x: $x, y: $y)";
}

void main() {
  var p = Point(10, 20);
  print(p); // Point(x: 10, y: 20)
}

```

✅ Arrow syntax is concise for single-expression overrides.

---

## 4. Real-World Example

💡 **Bank Account with** `**toString()**`

```Dart
class BankAccount {
  String owner;
  double balance;

  BankAccount(this.owner, this.balance);

  @override
  String toString() => "BankAccount(owner: $owner, balance: \$${balance})";
}

void main() {
  var account = BankAccount("Alice", 1500);
  print(account); // BankAccount(owner: Alice, balance: $1500)
}

```

✅ Makes logging and debugging **much clearer**.

---

## 5. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Override `toString()`|`@override String toString() { return "..."; }`|Full function body|
|Arrow syntax|`@override String toString() => "...";`|Concise, single-expression|
|Default|`print(object)`|`Instance of 'ClassName'`|
|Custom|Provides human-readable object info|Helpful for debugging/logging|