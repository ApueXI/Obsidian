---
Created: 2025-09-16T20:20
tags:
  - Advance-Concepts
---
# 🎯 Dart Operator Overloading Cheat Sheet

## 1. Full Explanation

- **Operator overloading** allows you to **define custom behavior** for operators like `+`, , `[]`, `==`, etc.
- Only certain operators can be overloaded in Dart.
- Syntax: `operator <symbol>(parameters) { ... }`
- Common use cases:
    - Mathematical objects (Point, Vector, Complex)
    - Collections with custom indexing
    - Domain-specific classes

---

## 2. Overloading `+` Operator

```Dart
class Point {
  final int x;
  final int y;

  Point(this.x, this.y);

  Point operator +(Point other) {
    return Point(x + other.x, y + other.y);
  }

  @override
  String toString() => "Point($x, $y)";
}

void main() {
  var p1 = Point(2, 3);
  var p2 = Point(4, 5);

  var p3 = p1 + p2;
  print(p3); // Point(6, 8)
}

```

✅ The `+` operator is now **customized for Point addition**.

---

## 3. Overloading `[]` Operator

```Dart
class MyList {
  final List<int> _data = [10, 20, 30];

  int operator [](int index) => _data[index];

  void operator []=(int index, int value) {
    _data[index] = value;
  }
}

void main() {
  var list = MyList();
  print(list[1]); // 20
  list[1] = 99;
  print(list[1]); // 99
}

```

✅ The `[]` and `[]=` operators allow **custom indexing**.

---

## 4. Overloading Comparison Operators

```Dart
class Box {
  final int size;
  Box(this.size);

  bool operator >(Box other) => size > other.size;
}

void main() {
  var b1 = Box(5);
  var b2 = Box(10);

  print(b2 > b1); // true
}

```

✅ Operators like `>`, `<`, `>=`, `<=` can also be customized.

---

## 5. Summary Table

|Operator|Syntax|Notes|
|---|---|---|
|Arithmetic|`operator +`, `operator -`, `operator *`, `operator /`|Customize math operations|
|Indexing|`operator []`, `operator []=`|Custom getter/setter for index|
|Comparison|`operator >`, `<`, `>=`, `<=`|Define custom comparisons|
|Equality|`operator ==`|Override equality|
|Unary|`operator -`, `operator ~`|Unary negation or bitwise complement|

---

## 6. Real-World Example

💡 **Vector Addition and Scaling**

```Dart
class Vector {
  final double x, y;

  Vector(this.x, this.y);

  Vector operator +(Vector other) => Vector(x + other.x, y + other.y);
  Vector operator *(double scalar) => Vector(x * scalar, y * scalar);

  @override
  String toString() => "Vector($x, $y)";
}

void main() {
  var v1 = Vector(1, 2);
  var v2 = Vector(3, 4);

  print(v1 + v2); // Vector(4, 6)
  print(v1 * 2);  // Vector(2, 4)
}

```

✅ Makes mathematical objects **more intuitive to work with** using operators.