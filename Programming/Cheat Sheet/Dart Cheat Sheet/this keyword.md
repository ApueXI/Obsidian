---
Created: 2025-09-16T20:05
tags:
  - Classes-&-Objects
---
# 🎯 Dart `this` Keyword Cheat Sheet

## 1. Full Explanation

- `**this**` refers to the **current instance of a class**.
- Common uses:
    1. **Distinguish between field and parameter names**
    2. **Call other constructors** (redirecting constructors)
    3. **Pass current instance** to other methods or objects

---

## 2. Basic Example

```Dart
class Person {
  String name;
  int age;

  Person(String name, int age) {
    this.name = name; // refers to instance field
    this.age = age;
  }

  void introduce() {
    print("Hi, I'm $name and I'm $age years old");
  }
}

void main() {
  var p = Person("Alice", 25);
  p.introduce(); // Hi, I'm Alice and I'm 25 years old
}

```

✅ `this.name` distinguishes **field** from **parameter**.

---

## 3. Using `this` in Constructors (Redirecting Constructors)

```Dart
class Point {
  int x, y;

  Point(this.x, this.y);

  // Named constructor redirecting to default constructor
  Point.origin() : this(0, 0);
}

void main() {
  var p = Point.origin();
  print("x=${p.x}, y=${p.y}"); // x=0, y=0
}

```

✅ `this(...)` calls another constructor of the same class.

---

## 4. Using `this` to Pass Current Instance

```Dart
class Printer {
  void printPerson(Person p) {
    print("${p.name}, ${p.age}");
  }
}

class Person {
  String name;
  int age;
  Person(this.name, this.age);

  void sendToPrinter(Printer printer) {
    printer.printPerson(this); // pass current instance
  }
}

void main() {
  var printer = Printer();
  var alice = Person("Alice", 25);
  alice.sendToPrinter(printer); // Alice, 25
}

```

✅ Useful to give **current object** to other methods.

---

## 5. `this` With Methods & Fields

```Dart
class Counter {
  int value = 0;

  void increment() {
    this.value++; // explicit reference, can omit
  }

  void show() {
    print(this.value); // explicit reference
  }
}

void main() {
  var c = Counter();
  c.increment();
  c.show(); // 1
}

```

✅ Optional in most cases, but **required when parameter name conflicts with field name**.

---

## 6. Summary Table

|Use Case|Example|Notes|
|---|---|---|
|Access field|`this.name = name`|Distinguish field from parameter|
|Call constructor|`Point.origin() : this(0,0);`|Redirecting constructor|
|Pass instance|`printer.printPerson(this);`|Send current object|
|Optional usage|`this.value++`|Can be omitted if no ambiguity|

---

## 7. Real-World Example

💡 **Flutter Widget Example**

```Dart
class MyButton {
  String label;

  MyButton(this.label);

  void onPressed() {
    print("Button ${this.label} clicked!");
  }
}

void main() {
  var btn = MyButton("Submit");
  btn.onPressed(); // Button Submit clicked!
}

```

✅ Demonstrates `this` referencing the **current instance** in a method.