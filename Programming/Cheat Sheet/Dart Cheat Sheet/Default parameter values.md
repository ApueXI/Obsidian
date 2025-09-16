---
Created: 2025-09-16T20:00
tags:
  - Functions
---
# 🎛️ Dart Default Parameter Values Cheat Sheet

## 1. Full Explanation

- You can assign **default values** to parameters.
- If the caller omits the argument → Dart uses the default.
- Works with both **optional positional** and **named parameters**.
- Default values must be **compile-time constants** (numbers, strings, const objects, etc.).

---

### 🔹 Default with Optional Positional (`[]`)

```Dart
void greet(String name, [String suffix = "!"]) {
  print("Hello $name$suffix");
}

void main() {
  greet("Alice");       // Hello Alice!
  greet("Bob", "!!!");  // Hello Bob!!!
}

```

✅ `suffix` defaults to `"!"`.

---

### 🔹 Default with Named (`{}`)

```Dart
void greet({String name = "Guest", int age = 18}) {
  print("Hello $name, age $age");
}

void main() {
  greet();                        // Hello Guest, age 18
  greet(name: "Charlie");         // Hello Charlie, age 18
  greet(name: "Diana", age: 25);  // Hello Diana, age 25
}

```

✅ Both `name` and `age` have default values.

---

### 🔹 Mixing Required + Default

```Dart
void describe({required String name, String city = "Unknown"}) {
  print("Name: $name, City: $city");
}

void main() {
  describe(name: "Eve");                // Name: Eve, City: Unknown
  describe(name: "Frank", city: "NY");  // Name: Frank, City: NY
}

```

✅ `name` must be passed, `city` defaults if omitted.

---

### 🔹 Default with Null Safety

```Dart
void printInfo([String? name = "Anonymous"]) {
  print("Name: $name");
}

void main() {
  printInfo();           // Name: Anonymous
  printInfo("Grace");    // Name: Grace
}

```

---

## 2. Summary Table

|Parameter Type|Syntax|Example|Call|Result|
|---|---|---|---|---|
|Positional Default|`[type param=val]`|`fn([int x=5])`|`fn()`|`x=5`|
|Named Default|`{type param=val}`|`fn({int x=10})`|`fn()`|`x=10`|
|Mix Required + Default|`{required x, y=2}`|`fn(x:1)`|`y=2`||
|Null-Safe Default|`[String? name="Anon"]`|`fn()`|`name="Anon"`||

---

## 3. Real-World Example

💡 **Flutter Button with Default Styling**

```Dart
import 'package:flutter/material.dart';

Widget buildButton(String text,
    {Color color = Colors.blue, double padding = 12}) {
  return Padding(
    padding: EdgeInsets.all(padding),
    child: ElevatedButton(
      style: ElevatedButton.styleFrom(backgroundColor: color),
      onPressed: () {},
      child: Text(text),
    ),
  );
}

void main() {
  runApp(MaterialApp(
    home: Scaffold(
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            buildButton("Default"), // Blue, padding 12
            buildButton("Custom", color: Colors.red, padding: 20),
          ],
        ),
      ),
    ),
  ));
}

```

✅ `color` defaults to `blue`, `padding` defaults to `12`.