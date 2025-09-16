---
Created: 2025-09-16T20:22
tags:
  - Advance-Concepts
---
# 🎯 Dart 3 Pattern Matching Cheat Sheet

## 1. Full Explanation

- **Pattern Matching** allows you to **match and extract values** from data structures in a clean, readable way.
- Supports:
    - **Records** `(x, y)`
    - **Lists & Maps**
    - **Custom classes with** `**case**`
- Can be used inside `**switch**` **statements** or `**if-case**` **expressions**.
- Enables **destructuring directly in cases**.

---

## 2. Pattern Matching with Records

```Dart
void main() {
  (int, String) record = (1, "Alice");

  switch (record) {
    case (1, var name):
      print("ID is 1, Name is $name"); // ID is 1, Name is Alice
    case (2, var name):
      print("ID is 2, Name is $name");
    default:
      print("Unknown record");
  }
}

```

✅ You can **match specific positional values** while extracting others using `var`.

---

## 3. Pattern Matching with Named Records

```Dart
void main() {
  (int id, String name) record = (id: 2, name: "Bob");

  switch (record) {
    case (id: 1, name: var n):
      print("ID is 1, Name is $n");
    case (id: 2, name: var n):
      print("ID is 2, Name is $n"); // ID is 2, Name is Bob
    default:
      print("Unknown record");
  }
}

```

✅ Named fields make **pattern matching more readable**.

---

## 4. Pattern Matching with Lists

```Dart
void main() {
  var list = [1, 2, 3];

  switch (list) {
    case [1, var second, _]:
      print("Second element is $second"); // Second element is 2
    default:
      print("Other list");
  }
}

```

- `_` is used as a **wildcard** to ignore values.
- `var` extracts elements for use inside the case.

---

## 5. Pattern Matching with Custom Classes

```Dart
class Point {
  final int x, y;
  const Point(this.x, this.y);
}

void main() {
  const p = Point(3, 4);

  switch (p) {
    case Point(0, 0):
      print("Origin");
    case Point(var x, var y):
      print("Point at ($x, $y)"); // Point at (3, 4)
  }
}

```

✅ Works if the class has a **const constructor** and **positional fields**.

---

## 6. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Positional record|`case (1, var name):`|Match and extract|
|Named record|`case (id: 2, name: var n):`|Match named fields|
|Wildcard|`_`|Ignore value|
|List|`case [1, var x, _]:`|Match elements in list|
|Custom class|`case ClassName(var a, var b):`|Works with const constructors|
|Default|`default:`|Catch-all pattern|

---

## 7. Real-World Example

💡 **Handling API Responses with Records**

```Dart
(int status, String message) getResponse(int id) {
  return id == 0 ? (404, "User not found") : (200, "User fetched");
}

void main() {
  var response = getResponse(1);

  switch (response) {
    case (200, var msg):
      print("Success: $msg"); // Success: User fetched
    case (404, var msg):
      print("Error: $msg");
    default:
      print("Unknown status");
  }
}

```

✅ Pattern matching **simplifies multi-value handling** compared to traditional `if-else`.