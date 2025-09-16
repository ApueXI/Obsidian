---
Created: 2025-09-16T19:55
tags:
  - Collections
---
# 📋 Dart Lists Cheat Sheet

## 1. Full Explanation

A **List** in Dart is an **ordered collection** (like arrays in other languages).

- Index-based (`list[0]` → first element).
- Supports **growable (dynamic size)** or **fixed-length**.

---

### 🔹 Growable List (default)

- Can add or remove elements.
- Created with `[]` or `List()`.

```Dart
void main() {
  var fruits = ["Apple", "Banana"]; // growable by default
  fruits.add("Cherry");
  print(fruits); // [Apple, Banana, Cherry]

  fruits.remove("Banana");
  print(fruits); // [Apple, Cherry]
}

```

✅ Most common in Flutter/Dart apps.

---

### 🔹 Fixed-Length List

- Created with `List.filled(length, value)` or `List(length, growable: false)`.
- Length **cannot change** (no `add`/`remove`).
- Values can still be reassigned.

```Dart
void main() {
  var numbers = List.filled(3, 0); // length = 3, all zeros
  print(numbers); // [0, 0, 0]

  numbers[1] = 42; // update allowed
  print(numbers); // [0, 42, 0]

  // numbers.add(99); ❌ Error: cannot change length
}

```

---

### 🔹 Empty List Examples

```Dart
var growable = <int>[]; // growable, empty
var fixed = List<int>.filled(5, -1); // fixed, filled with -1

```

---

## 2. Summary Table

|Type|Syntax|Size|Add/Remove|Modify Elements|
|---|---|---|---|---|
|Growable|`var list = [1,2,3];`|Dynamic|✅ Yes|✅ Yes|
|Fixed-length|`List.filled(3, 0)`|Fixed|❌ No|✅ Yes|

---

## 3. Real-World Example

💡 **Flutter Dropdown Menu with Fixed & Growable Lists**

```Dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(
    home: Scaffold(
      body: Center(
        child: DropdownButton<String>(
          items: [
            for (var fruit in ["Apple", "Banana", "Cherry"])
              DropdownMenuItem(value: fruit, child: Text(fruit))
          ],
          onChanged: (value) => print("Selected: $value"),
        ),
      ),
    ),
  ));
}

```

✅ Growable lists let you dynamically add/remove items.

✅ Fixed-length lists are useful for **placeholders**, preallocated storage, or fixed-size game grids.