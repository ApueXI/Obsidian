---
Created: 2025-09-16T20:03
tags:
  - Classes-&-Objects
---
# 🎯 Dart Constructors Cheat Sheet

## 1. Full Explanation

A **constructor** is a special method that runs when you create an object.

Dart has several kinds of constructors:

1. **Default (Generative) Constructor** → Initializes fields when object is created.
2. **Named Constructor** → Provides multiple ways to create objects.
3. **Factory Constructor** → Returns an existing instance or custom object creation logic.

---

## 2. Default Constructor

The simplest form — initializes fields.

```Dart
class Person {
  String name;
  int age;

  // Default constructor
  Person(this.name, this.age);
}

void main() {
  var p = Person("Alice", 25);
  print("${p.name}, ${p.age}"); // Alice, 25
}

```

➡️ `this.name` and `this.age` assign directly to fields.

---

## 3. Named Constructors

Custom constructors with different names.

```Dart
class Point {
  int x, y;

  Point(this.x, this.y);

  // Named constructor
  Point.origin() : x = 0, y = 0;

  Point.unit() : x = 1, y = 1;
}

void main() {
  var p1 = Point(5, 10);
  var p2 = Point.origin();
  var p3 = Point.unit();

  print("p1: (${p1.x}, ${p1.y})"); // (5, 10)
  print("p2: (${p2.x}, ${p2.y})"); // (0, 0)
  print("p3: (${p3.x}, ${p3.y})"); // (1, 1)
}

```

➡️ Useful for multiple initialization strategies.

---

## 4. Factory Constructors

Used when:

- Returning an existing cached instance (singleton pattern).
- Returning a **subclass** instance.
- Running custom logic before returning an object.

```Dart
class Logger {
  final String name;
  static final Map<String, Logger> _cache = {};

  // Private generative constructor
  Logger._internal(this.name);

  // Factory constructor
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
  var l1 = Logger("Main");
  var l2 = Logger("Main");

  print(l1 == l2); // true (same cached instance)
}

```

➡️ Factory constructors don’t always create a new object.

---

## 5. Summary Table

|Type|Syntax|Example|Notes|
|---|---|---|---|
|Default|`Class(this.field)`|`Person("A", 20)`|Simple, auto-assigns fields|
|Named|`Class.named()`|`Point.origin()`|Multiple creation styles|
|Factory|`factory Class(...)`|`Logger("Main")`|Custom logic, return cached or new instance|

---

## 6. Real-World Example

💡 **Shape Factory with Named & Factory Constructors**

```Dart
abstract class Shape {
  double area();
}

class Circle implements Shape {
  double radius;
  Circle(this.radius);

  @override
  double area() => 3.14 * radius * radius;
}

class Square implements Shape {
  double side;
  Square(this.side);

  @override
  double area() => side * side;
}

class ShapeFactory {
  factory ShapeFactory(String type, double size) {
    if (type == "circle") return Circle(size);
    if (type == "square") return Square(size);
    throw Exception("Unknown shape: $type");
  }
}

void main() {
  Shape c = ShapeFactory("circle", 5);
  Shape s = ShapeFactory("square", 4);

  print("Circle area: ${c.area()}"); // 78.5
  print("Square area: ${s.area()}"); // 16
}

```

✅ Uses **factory** to decide which subclass to return.