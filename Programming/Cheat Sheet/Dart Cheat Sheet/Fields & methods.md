---
Created: 2025-09-16T20:04
tags:
  - Classes-&-Objects
---
# 🎯 Dart Fields & Methods Cheat Sheet

## 1. Full Explanation

- **Fields** → Variables declared inside a class. They hold **state** for objects.
- **Methods** → Functions declared inside a class. They define **behavior**.
- Fields can be:
    - **Instance fields** → each object has its own copy
    - **Static fields** → shared across all instances (`static`)
- Methods can be:
    - **Instance methods** → operate on individual objects
    - **Static methods** → belong to the class, not instances

---

## 2. Instance Fields

```Dart
class Person {
  String name;
  int age;

  Person(this.name, this.age);
}

void main() {
  var alice = Person("Alice", 25);
  var bob = Person("Bob", 30);

  print(alice.name); // Alice
  print(bob.age);    // 30
}

```

✅ Each object has its **own copy** of `name` and `age`.

---

## 3. Instance Methods

```Dart
class Car {
  String brand;
  int speed;

  Car(this.brand, this.speed);

  void drive() {
    print("$brand is driving at $speed km/h");
  }

  void accelerate(int increment) {
    speed += increment;
    print("$brand accelerated to $speed km/h");
  }
}

void main() {
  var car = Car("Toyota", 100);
  car.drive();           // Toyota is driving at 100 km/h
  car.accelerate(20);    // Toyota accelerated to 120 km/h
}

```

---

## 4. Static Fields & Methods

- **Static fields** → shared across all instances
- **Static methods** → can be called on the class itself

```Dart
class Counter {
  static int totalCount = 0;

  Counter() {
    totalCount++;
  }

  static void showTotal() {
    print("Total objects created: $totalCount");
  }
}

void main() {
  Counter(); Counter(); Counter();
  Counter.showTotal(); // Total objects created: 3
}

```

---

## 5. Private Fields & Methods

- Prefix with `_` to make **private to the library**.

```Dart
class BankAccount {
  String owner;
  double _balance; // private

  BankAccount(this.owner, this._balance);

  void deposit(double amount) {
    _balance += amount;
  }

  double get balance => _balance; // getter to access private field
}

void main() {
  var acc = BankAccount("Alice", 1000);
  acc.deposit(200);
  print(acc.balance); // 1200
}

```

---

## 6. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Instance field|`String name;`|Each object has its own value|
|Instance method|`void drive() {}`|Operates on instance|
|Static field|`static int total;`|Shared by class|
|Static method|`static void showTotal() {}`|Called on class|
|Private|`_balance`|Accessible only within library|
|Getter|`double get balance => _balance;`|Access private fields safely|
|Setter|`set balance(double val) => _balance = val;`|Modify private fields safely|

---

## 7. Real-World Example

💡 **Dart Class for a Simple Bank Account**

```Dart
class BankAccount {
  String owner;
  double _balance;

  BankAccount(this.owner, this._balance);

  void deposit(double amount) {
    _balance += amount;
    print("$owner deposited \$${amount}. Balance: \$$_balance");
  }

  void withdraw(double amount) {
    if (amount <= _balance) {
      _balance -= amount;
      print("$owner withdrew \$${amount}. Balance: \$$_balance");
    } else {
      print("Insufficient funds for $owner");
    }
  }

  double get balance => _balance;
}

void main() {
  var account = BankAccount("Alice", 1000);
  account.deposit(500);
  account.withdraw(200);
  print("Current Balance: ${account.balance}");
}

```

✅ Demonstrates **instance fields, methods, private field, and getter**.