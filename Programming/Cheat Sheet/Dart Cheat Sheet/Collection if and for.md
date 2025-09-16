---
Created: 2025-09-16T19:56
tags:
  - Collections
---
# 🛠️ Dart Collection `if` & `for` Cheat Sheet

## 1. Full Explanation

Dart allows **control flow** (`if` / `for`) **inside collection literals** (`[]`, `{}`, `{}` for maps).

- Makes collections **dynamic & concise**.
- Works with **List, Set, Map**.
- Commonly used in **Flutter widget trees**.

---

### 🔹 Collection `if`

Use `if` inside a collection to include elements conditionally.

```Dart
void main() {
  bool addExtra = true;

  var numbers = [1, 2, if (addExtra) 3];
  print(numbers); // [1, 2, 3]
}

```

✅ Only adds `3` if condition is true.

---

### 🔹 Collection `for`

Use `for` to generate elements in a collection.

```Dart
void main() {
  var base = [1, 2, 3];
  var doubled = [for (var n in base) n * 2];

  print(doubled); // [2, 4, 6]
}

```

✅ Transforms elements on the fly.

---

### 🔹 Combining `if` and `for`

```Dart
void main() {
  var numbers = [1, 2, 3, 4, 5];
  var evens = [for (var n in numbers) if (n.isEven) n];

  print(evens); // [2, 4]
}

```

✅ Powerful way to filter & map collections in one line.

---

### 🔹 Works with Sets

```Dart
void main() {
  var names = {"Alice", "Bob"};
  var moreNames = {"Charlie", if (true) ...names};

  print(moreNames); // {Charlie, Alice, Bob}
}

```

---

### 🔹 Works with Maps

```Dart
void main() {
  var includeExtra = true;

  var scores = {
    "Alice": 90,
    "Bob": 80,
    if (includeExtra) "Charlie": 70,
    for (var i in [1, 2]) "User$i": i * 10
  };

  print(scores);
  // {Alice: 90, Bob: 80, Charlie: 70, User1: 10, User2: 20}
}

```

---

## 2. Summary Table

|Feature|Example|Result|
|---|---|---|
|`if` in list|`[1, 2, if (true) 3]`|`[1, 2, 3]`|
|`if` in map|`{"A":1, if (flag) "B":2}`|`{"A":1,"B":2}`|
|`for` in list|`[for (var i in [1,2]) i*2]`|`[2,4]`|
|`for` with `if`|`[for (var i in [1,2,3]) if(i>1) i]`|`[2,3]`|

---

## 3. Real-World Example

💡 **Flutter Navigation Drawer Menu**

```Dart
import 'package:flutter/material.dart';

void main() {
  final menuItems = ["Home", "Profile", "Settings"];
  final isAdmin = true;

  runApp(MaterialApp(
    home: Scaffold(
      drawer: Drawer(
        child: ListView(
          children: [
            for (var item in menuItems)
              ListTile(title: Text(item)),
            if (isAdmin) ListTile(title: Text("Admin Panel")),
          ],
        ),
      ),
      body: Center(child: Text("Collection if & for Example")),
    ),
  ));
}

```

✅ `for` generates a list of tiles.

✅ `if` conditionally adds **Admin Panel** if user is admin.