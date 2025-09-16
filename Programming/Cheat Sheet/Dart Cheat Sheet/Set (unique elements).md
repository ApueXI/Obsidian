---
Created: 2025-09-16T19:55
tags:
  - Collections
---
# 🟢 Dart Set Cheat Sheet

## 1. Full Explanation

- A **Set** is an **unordered collection** of **unique elements**.
- No duplicates allowed.
- Useful for membership checks, unions, intersections.

---

### 🔹 Creating a Set

```Dart
void main() {
  var numbers = {1, 2, 3}; // literal
  var emptySet = <String>{}; // empty set with type
  Set<int> ids = {}; // inferred as Set<int>

  print(numbers); // {1, 2, 3}
}

```

❌ `{}` without a type defaults to **Map**, so use `<Type>{}` for empty sets.

---

### 🔹 Adding & Removing

```Dart
void main() {
  var fruits = <String>{};

  fruits.add("Apple");
  fruits.add("Banana");
  fruits.add("Apple"); // duplicate ignored

  print(fruits); // {Apple, Banana}

  fruits.remove("Banana");
  print(fruits); // {Apple}
}

```

---

### 🔹 Common Operations

```Dart
void main() {
  var a = {1, 2, 3};
  var b = {3, 4, 5};

  print(a.contains(2));       // true
  print(a.union(b));          // {1,2,3,4,5}
  print(a.intersection(b));   // {3}
  print(a.difference(b));     // {1,2}
}

```

---

## 2. Summary Table

|Operation|Example|Result|
|---|---|---|
|Create|`var s = {1,2,3};`|`{1,2,3}`|
|Empty Set|`var s = <int>{};`|`{}`|
|Add|`s.add(4)`|`{1,2,3,4}`|
|Remove|`s.remove(2)`|`{1,3}`|
|Contains|`s.contains(1)`|`true`|
|Union|`a.union(b)`|combine both|
|Intersection|`a.intersection(b)`|common elements|
|Difference|`a.difference(b)`|only in `a`|

---

## 3. Real-World Example

💡 **Unique Tags in Flutter**

```Dart
import 'package:flutter/material.dart';

void main() {
  final tags = {"Flutter", "Dart", "Mobile", "Dart"}; // duplicate ignored

  runApp(MaterialApp(
    home: Scaffold(
      body: Wrap(
        spacing: 8,
        children: [
          for (var tag in tags)
            Chip(label: Text(tag)),
        ],
      ),
    ),
  ));
}

```

✅ Ensures no duplicate tags are shown in the UI.