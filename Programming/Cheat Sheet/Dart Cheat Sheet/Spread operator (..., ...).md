---
Created: 2025-09-16T19:56
tags:
  - Collections
---
# 🌐 Dart Spread Operator Cheat Sheet

## 1. Full Explanation

The **spread operator** (`...`) is used to **insert all elements from one collection into another**.

- `...` → adds all elements (throws error if the collection is `null`).
- `...?` → adds all elements **only if the collection is not null** (safe for nullable collections).

---

### 🔹 Basic Usage

```Dart
void main() {
  var list1 = [1, 2, 3];
  var list2 = [0, ...list1, 4, 5];
  print(list2); // [0, 1, 2, 3, 4, 5]
}

```

---

### 🔹 Null-Safe Spread (`...?`)

```Dart
void main() {
  List<int>? maybeNull;

  var list = [0, ...?maybeNull, 1];
  print(list); // [0, 1]
}

```

✅ Without `...?`, this would throw an error if `maybeNull` is `null`.

---

### 🔹 Works with Sets

```Dart
void main() {
  var set1 = {1, 2, 3};
  var set2 = {...set1, 4, 5};
  print(set2); // {1, 2, 3, 4, 5}
}

```

---

### 🔹 Works with Maps

```Dart
void main() {
  var map1 = {"a": 1, "b": 2};
  var map2 = {"c": 3, ...map1};
  print(map2); // {c: 3, a: 1, b: 2}
}

```

---

## 2. Summary Table

|Operator|Meaning|Example|Result|
|---|---|---|---|
|`...`|Spread elements|`[0, ...[1,2,3]]`|`[0,1,2,3]`|
|`...?`|Null-safe spread|`[0, ...?null]`|`[0]`|
|`...` (Set)|Spread in Set|`{...{1,2},3}`|`{1,2,3}`|
|`...` (Map)|Spread in Map|`{"c":3, ...{"a":1}}`|`{c:3,a:1}`|

---

## 3. Real-World Example

💡 **Merging multiple Flutter widget lists**

```Dart
import 'package:flutter/material.dart';

void main() {
  final buttons = [
    ElevatedButton(onPressed: () {}, child: Text("Yes")),
    ElevatedButton(onPressed: () {}, child: Text("No")),
  ];

  runApp(MaterialApp(
    home: Scaffold(
      body: Column(
        children: [
          Text("Do you agree?"),
          ...buttons, // Spread widgets into Column
        ],
      ),
    ),
  ));
}

```

✅ `...buttons` inserts multiple widgets inside the `Column`.

✅ Avoids manually writing each widget.