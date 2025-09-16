---
Created: 2025-09-16T19:50
tags:
  - Operators
---
# 🏗️ Dart Cascade Operator Cheat Sheet

## 1. Full Explanation

The **cascade operator (**`**..**`**)** allows you to perform **multiple operations on the same object** without repeating its name.

- `..` → Executes operations on a **non-null object**.
- `?..` → Executes operations only if the object is **not null** (null-safe cascade).

---

### 🔹 `..` Example (Chained Operations)

```Dart
class User {
  String name = "";
  int age = 0;

  void greet() => print("Hello, my name is $name and I'm $age.");
}

void main() {
  var user = User()
    ..name = "Alice"
    ..age = 25
    ..greet();
}

```

✅ No need to repeat `user` multiple times.

---

### 🔹 `?..` Example (Null-Safe Cascade)

```Dart
User? user = null;

user
  ?..name = "Bob"
  ..age = 30
  ..greet(); // ❌ Nothing happens, no crash

```

✅ Avoids `NullPointerException` when object might be null.

---

## 2. Summary Table

|Operator|Meaning|Example|Result|
|---|---|---|---|
|`..`|Perform multiple actions on the same object|`user..name="Alice"..greet()`|Works normally|
|`?..`|Perform multiple actions if not null|`user?..name="Bob"..greet()`|Skips if `user` is null|

---

## 3. Real-World Example

**Building a** `**TextEditingController**` **in Flutter:**

```Dart
import 'package:flutter/material.dart';

void main() {
  final controller = TextEditingController()
    ..text = "Hello World"
    ..addListener(() {
      print("Text changed: ${controller.text}");
    });

  runApp(MaterialApp(
    home: Scaffold(
      body: TextField(controller: controller),
    ),
  ));
}

```

✅ Instead of:

```Dart
final controller = TextEditingController();
controller.text = "Hello World";
controller.addListener(() { ... });

```

You can chain everything with `..`.

---

### Combined `?..` Example

```Dart
User? user;

// Safe cascade - won’t crash if null
user
  ?..name = "Charlie"
  ..age = 40
  ..greet();

```

---

👉 In Flutter, cascades are heavily used for **controllers, animations, widget builders, and services**.