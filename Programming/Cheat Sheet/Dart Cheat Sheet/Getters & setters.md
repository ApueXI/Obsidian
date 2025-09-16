---
Created: 2025-09-16T20:04
tags:
  - Classes-&-Objects
---
# 🎯 Dart Getters & Setters Cheat Sheet

## 1. Full Explanation

- **Getters** → Special methods to **read a property**.
- **Setters** → Special methods to **modify a property**.
- Useful for:
    - Controlling access to private fields
    - Adding validation or computed properties
    - Maintaining **encapsulation**
- Syntax:

```Dart
returnType get propertyName => valueOrExpression;
set propertyName(type value) => doSomething;

```

---

## 2. Basic Example

```Dart
class Rectangle {
  double _width = 0;
  double _height = 0;

  // Getter
  double get area => _width * _height;

  // Setter
  set width(double w) {
    if (w > 0) _width = w;
  }

  set height(double h) {
    if (h > 0) _height = h;
  }
}

void main() {
  var rect = Rectangle();
  rect.width = 5;
  rect.height = 10;
  print(rect.area); // 50
}

```

✅ `_width` and `_height` are private; `area` is **computed**, and setters validate values.

---

## 3. Shorter Syntax for Simple Getters

```Dart
class Circle {
  double radius;

  Circle(this.radius);

  double get area => 3.14 * radius * radius;
}

void main() {
  var c = Circle(5);
  print(c.area); // 78.5
}

```

---

## 4. Setter With Validation

```Dart
class Person {
  String _name = "";

  set name(String value) {
    if (value.isNotEmpty) {
      _name = value;
    } else {
      print("Name cannot be empty");
    }
  }

  String get name => _name;
}

void main() {
  var p = Person();
  p.name = "Alice";   // valid
  p.name = "";        // Name cannot be empty
  print(p.name);      // Alice
}

```

---

## 5. Summary Table

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Getter|`get property => value`|`double get area => w*h;`|Read-only computed property|
|Setter|`set property(value) => ...`|`set width(double w){...}`|Add validation or modify private fields|
|Private Field|`_field`|`_balance`|Encapsulate state|
|Read-Only Property|Only getter|`get area`|No setter, cannot modify|
|Write-Only Property|Only setter|`set password`|Cannot read directly|

---

## 6. Real-World Example

💡 **Bank Account With Encapsulation**

```Dart
class BankAccount {
  String owner;
  double _balance = 0;

  BankAccount(this.owner, this._balance);

  // Getter
  double get balance => _balance;

  // Setter with validation
  set deposit(double amount) {
    if (amount > 0) _balance += amount;
  }

  set withdraw(double amount) {
    if (amount <= _balance) _balance -= amount;
    else print("Insufficient funds");
  }
}

void main() {
  var account = BankAccount("Alice", 1000);
  account.deposit = 500;
  account.withdraw = 200;
  account.withdraw = 2000; // Insufficient funds
  print(account.balance);   // 1300
}

```

✅ Shows **private fields**, **getter**, **setter with validation**, and controlled access.