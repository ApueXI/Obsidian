---
Created: 2025-09-16T20:20
tags:
  - Advance-Concepts
---
# 🎯 Dart Const Constructors Cheat Sheet

## 1. Full Explanation

- **Const constructors** allow you to create objects that are **immutable and canonicalized** at **compile-time**.
- Benefits:
    - Reduces memory usage (same object instance reused)
    - Ensures **immutability**
- Rules for const constructors:
    1. All instance variables must be `final`.
    2. The constructor must be marked with `const`.
    3. Any fields initialized in the constructor must be **compile-time constants**.

---

## 2. Basic Example

```Dart
class Point {
  final int x;
  final int y;

  const Point(this.x, this.y); // const constructor
}

void main() {
  const p1 = Point(1, 2);
  const p2 = Point(1, 2);

  print(identical(p1, p2)); // true → same instance
}

```

✅ `identical()` shows that **const objects with same values share the same memory**.

---

## 3. Nested Const Objects

```Dart
class Circle {
  final Point center;
  final double radius;

  const Circle(this.center, this.radius);
}

void main() {
  const c1 = Circle(Point(0, 0), 5);
  const c2 = Circle(Point(0, 0), 5);

  print(identical(c1, c2)); // true
}

```

✅ Const constructors work recursively if **all fields are final and const**.

---

## 4. Using Const with Collections

```Dart
void main() {
  const numbers = [1, 2, 3]; // immutable list
  // numbers.add(4); // ❌ Compile-time error

  const points = [Point(0, 0), Point(1, 1)]; // list of const objects
  print(points);
}

```

✅ Const collections are **immutable and evaluated at compile-time**.

---

## 5. Const vs Regular Constructor

|Feature|Const Constructor|Regular Constructor|
|---|---|---|
|Object immutability|Yes|Optional|
|Compile-time creation|Yes|No|
|Memory reuse|Yes (canonicalization)|No|
|Instance variables|Must be final|Can be mutable|

---

## 6. Real-World Example

💡 **Color Class**

```Dart
class Color {
  final int red;
  final int green;
  final int blue;

  const Color(this.red, this.green, this.blue);
}

void main() {
  const red = Color(255, 0, 0);
  const redAgain = Color(255, 0, 0);

  print(identical(red, redAgain)); // true → same instance
}

```

✅ Useful for **immutable configuration objects**, like colors, points, or constants in UI.