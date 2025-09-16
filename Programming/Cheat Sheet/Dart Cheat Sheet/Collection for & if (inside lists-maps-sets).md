---
Created: 2025-09-16T19:54
tags:
  - Control-Flow
---
# 🧩 Dart Collection `for` & `if` Cheat Sheet

## 1. Full Explanation

Dart allows **control flow inside collection literals** (`List`, `Set`, `Map`).

- ✅ **Collection** `**for**` → insert elements from a loop directly into a collection.
- ✅ **Collection** `**if**` → conditionally include elements.

This feature makes **list comprehensions** possible (like Python).

---

### 🔹 Collection `for`

```Dart
void main() {
  var numbers = [1, 2, 3];
  var doubled = [
    for (var n in numbers) n * 2
  ];

  print(doubled); // [2, 4, 6]
}

```

✅ Iterates over `numbers` and inserts transformed values into a new list.

---

### 🔹 Collection `if`

```Dart
void main() {
  bool addMore = true;

  var items = [
    "Apple",
    "Banana",
    if (addMore) "Cherry", // conditionally add
  ];

  print(items); // [Apple, Banana, Cherry]
}

```

✅ Cherry is included only if condition is true.

---

### 🔹 Combined `for` + `if`

```Dart
void main() {
  var numbers = [1, 2, 3, 4, 5];

  var evens = [
    for (var n in numbers)
      if (n % 2 == 0) n
  ];

  print(evens); // [2, 4]
}

```

✅ Filters inside the comprehension.

---

### 🔹 Works with Sets & Maps Too

```Dart
void main() {
  // Set
  var squares = {
    for (var n in [1, 2, 3]) n * n
  };
  print(squares); // {1, 4, 9}

  // Map
  var users = ["Alice", "Bob"];
  var userMap = {
    for (var u in users) u: u.length
  };
  print(userMap); // {Alice: 5, Bob: 3}
}

```

---

## 2. Summary Table

|Feature|Usage|Example|Result|
|---|---|---|---|
|Collection `for`|Add loop-generated items|`[for (var x in list) x*2]`|`[2,4,6]`|
|Collection `if`|Add item conditionally|`[1,2, if(flag) 3]`|`[1,2,3]`|
|Combined|Filter & transform in one|`[for (x in list) if (x>5) x]`|`[6,7,...]`|

---

## 3. Real-World Example

💡 **Flutter Widget List with Conditions**

```Dart
import 'package:flutter/material.dart';

void main() {
  bool showExtras = true;
  List<String> items = ["Home", "Profile", "Settings"];

  runApp(MaterialApp(
    home: Scaffold(
      body: Column(
        children: [
          for (var item in items) Text(item),
          if (showExtras) Text("Extras Section"),
        ],
      ),
    ),
  ));
}

```

✅ Flutter UIs often use collection `for` + `if` when dynamically building widget lists.

---

⚡ This is one of the most **Flutter-friendly Dart features** since UI trees often depend on loops and conditions.