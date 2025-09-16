---
Created: 2025-09-16T20:19
tags:
  - Advance-Concepts
---
# 🎯 Dart `late` Cheat Sheet

## 1. Full Explanation

- `**late**` tells Dart that a variable will be **initialized later**, but **non-nullable**.
- Helps **avoid null values** while deferring initialization.
- Can be used with:
    - **Instance variables**
    - **Top-level variables**
    - **Local variables**
- Dart **throws an error if you access a late variable before it’s initialized**.

---

## 2. Basic Example

```Dart
late String description;

void main() {
  description = "This is a late variable";
  print(description); // This is a late variable
}

```

✅ Variable is **non-nullable** but initialized later.

---

## 3. Late with Computed Values

```Dart
class Circle {
  final double radius;
  late double area = 3.14 * radius * radius; // computed when accessed

  Circle(this.radius);
}

void main() {
  var circle = Circle(5);
  print(circle.area); // 78.5
}

```

✅ The `area` is **computed lazily** when first accessed.

---

## 4. Late with Final Variables

```Dart
class Config {
  late final String apiUrl;

  void setup(String url) {
    apiUrl = url;
  }
}

void main() {
  var config = Config();
  config.setup("https://example.com");
  print(config.apiUrl); // https://example.com
}

```

✅ `late final` allows **one-time assignment deferred**.

---

## 5. Late Initialization Error

```Dart
late String name;

void main() {
  // print(name); // ❌ Error: LateInitializationError
  name = "Alice";
  print(name); // Alice
}

```

✅ Accessing **before assignment** causes `**LateInitializationError**`.

---

## 6. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Late variable|`late Type varName;`|Deferred initialization|
|Late with final|`late final Type varName;`|One-time assignment|
|Computed lazy|`late Type varName = expression;`|Value computed on first access|
|Error if uninitialized|Access before assignment|Throws `LateInitializationError`|

---

## 7. Real-World Example

💡 **Database Connection**

```Dart
class Database {
  late final String connectionString;

  void connect(String conn) {
    connectionString = conn;
    print("Connected to $connectionString");
  }
}

void main() {
  var db = Database();
  db.connect("Server=127.0.0.1;Database=myDB");
  print(db.connectionString); // Server=127.0.0.1;Database=myDB
}

```

✅ Useful for **objects that can’t be initialized immediately**, like database connections or API clients.