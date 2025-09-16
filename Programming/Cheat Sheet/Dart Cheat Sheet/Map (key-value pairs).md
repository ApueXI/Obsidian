---
Created: 2025-09-16T19:56
tags:
  - Collections
---
# 🗂️ Dart Map Cheat Sheet

## 1. Full Explanation

- A **Map** is a collection of **key–value pairs**.
- Keys are **unique**, values can be duplicated.
- Keys can be any object type, but most often `String` or `int`.

---

### 🔹 Creating Maps

```Dart
void main() {
  // Literal
  var scores = {"Alice": 90, "Bob": 80};

  // Explicit type
  Map<String, int> grades = {"Charlie": 85, "Diana": 95};

  // Empty map
  var empty = <String, String>{};

  print(scores); // {Alice: 90, Bob: 80}
}

```

---

### 🔹 Accessing & Updating

```Dart
void main() {
  var scores = {"Alice": 90, "Bob": 80};

  print(scores["Alice"]); // 90

  scores["Alice"] = 95; // update value
  scores["Eve"] = 70;   // add new entry

  print(scores); // {Alice: 95, Bob: 80, Eve: 70}
}

```

---

### 🔹 Removing

```Dart
void main() {
  var scores = {"Alice": 90, "Bob": 80};

  scores.remove("Bob");
  print(scores); // {Alice: 90}
}

```

---

### 🔹 Iterating

```Dart
void main() {
  var scores = {"Alice": 90, "Bob": 80};

  for (var key in scores.keys) {
    print("Key: $key");
  }

  for (var value in scores.values) {
    print("Value: $value");
  }

  for (var entry in scores.entries) {
    print("${entry.key} → ${entry.value}");
  }
}

```

---

### 🔹 Common Methods

```Dart
void main() {
  var scores = {"Alice": 90, "Bob": 80};

  print(scores.containsKey("Alice"));   // true
  print(scores.containsValue(80));      // true
  print(scores.length);                 // 2
  scores.clear();                       // {}
}

```

---

## 2. Summary Table

|Operation|Example|Result|
|---|---|---|
|Create|`{"A":1, "B":2}`|`{A:1, B:2}`|
|Access|`map["A"]`|`1`|
|Update|`map["A"]=10`|`{A:10}`|
|Add|`map["C"]=3`|`{A:1,B:2,C:3}`|
|Remove|`map.remove("A")`|`{B:2}`|
|Keys|`map.keys`|`(A,B,C)`|
|Values|`map.values`|`(1,2,3)`|
|Entries|`map.entries`|iterable of pairs|
|Contains Key|`map.containsKey("A")`|`true/false`|
|Contains Value|`map.containsValue(2)`|`true/false`|
|Clear|`map.clear()`|`{}`|

---

## 3. Real-World Example

💡 **Flutter Dropdown with Map**

```Dart
import 'package:flutter/material.dart';

void main() {
  final items = {
    "1": "Apple",
    "2": "Banana",
    "3": "Cherry",
  };

  runApp(MaterialApp(
    home: Scaffold(
      body: Center(
        child: DropdownButton<String>(
          items: [
            for (var entry in items.entries)
              DropdownMenuItem(value: entry.key, child: Text(entry.value))
          ],
          onChanged: (value) => print("Selected: $value"),
        ),
      ),
    ),
  ));
}

```

✅ Uses a `Map` to map IDs → display names.