---
Created: 2025-09-16T19:53
tags:
  - Control-Flow
---
# 🔁 Dart `for-in` Loop Cheat Sheet

## 1. Full Explanation

- The `**for-in**` **loop** is used to iterate directly over **collections** like lists, sets, or maps.
- It eliminates the need for an index counter.
- Works well with **iterables** (anything that implements `Iterable`).

---

### 🔹 Basic Example with List

```Dart
void main() {
  List<String> fruits = ["Apple", "Banana", "Cherry"];

  for (var fruit in fruits) {
    print(fruit);
  }
}

```

**Output:**

```Plain
Apple
Banana
Cherry

```

---

### 🔹 Example with Set

```Dart
void main() {
  Set<int> numbers = {1, 2, 3};

  for (var n in numbers) {
    print(n);
  }
}

```

---

### 🔹 Iterating Map (Keys & Values)

```Dart
void main() {
  Map<String, int> scores = {
    "Alice": 90,
    "Bob": 80,
    "Charlie": 85
  };

  // Keys only
  for (var key in scores.keys) {
    print("Key: $key");
  }

  // Values only
  for (var value in scores.values) {
    print("Value: $value");
  }

  // Both key and value
  for (var entry in scores.entries) {
    print("${entry.key}: ${entry.value}");
  }
}

```

---

## 2. Summary Table

|Loop Type|Best Use|Example|
|---|---|---|
|`for`|When index is needed|`for (int i=0; i<list.length; i++) ...`|
|`for-in`|When iterating collections directly|`for (var item in list) ...`|
|`forEach`|Functional style iteration|`list.forEach((item) => print(item));`|

---

## 3. Real-World Example

💡 **Flutter Widget List**

```Dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(
    home: Scaffold(
      body: Column(
        children: [
          for (var color in ["Red", "Green", "Blue"])
            Text("Color: $color"),
        ],
      ),
    ),
  ));
}

```

✅ Using `for-in` directly in Flutter widget tree (thanks to collection-for).

---

⚡ In practice, you’ll use `for-in` often for lists/maps in Flutter when building UI from collections.