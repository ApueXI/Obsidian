---
Created: 2025-09-16T20:00
tags:
  - Functions
---
# 🏷️ Dart Named Parameters Cheat Sheet

## 1. Full Explanation

- Named parameters are wrapped in **curly braces** `**{ }**`.
- Callers must **specify parameter names** → makes code clearer.
- They can be:
    - **Required** → marked with `required`.
    - **Optional** → can be omitted, may have default values.
- Order doesn’t matter when calling (unlike positional parameters).

---

### 🔹 Basic Named Parameters

```Dart
void greet({String? name, int? age}) {
  print("Hello $name, age: $age");
}

void main() {
  greet(name: "Alice", age: 25); // Hello Alice, age: 25
  greet(age: 30, name: "Bob");   // Hello Bob, age: 30
  greet();                       // Hello null, age: null
}

```

---

### 🔹 Required Named Parameters

```Dart
void greet({required String name, required int age}) {
  print("Hello $name, you are $age years old");
}

void main() {
  greet(name: "Charlie", age: 20);
  // greet(); ❌ ERROR: Missing required arguments
}

```

✅ Safer because compiler enforces them.

---

### 🔹 With Default Values

```Dart
void greet({String name = "Guest", int age = 18}) {
  print("Hello $name, age: $age");
}

void main() {
  greet();                         // Hello Guest, age: 18
  greet(name: "Diana");            // Hello Diana, age: 18
  greet(name: "Eve", age: 30);     // Hello Eve, age: 30
}

```

---

### 🔹 Mixing Required + Default

```Dart
void describe({required String name, String city = "Unknown"}) {
  print("Name: $name, City: $city");
}

void main() {
  describe(name: "Frank");              // Name: Frank, City: Unknown
  describe(name: "Grace", city: "NY");  // Name: Grace, City: NY
}

```

---

### 🔹 Functions with Both Positional & Named

```Dart
void orderPizza(String type, {bool extraCheese = false, int size = 12}) {
  print("Order: $type, Size: $size, Extra Cheese: $extraCheese");
}

void main() {
  orderPizza("Pepperoni"); // Order: Pepperoni, Size: 12, Extra Cheese: false
  orderPizza("Hawaiian", size: 16, extraCheese: true);
}

```

---

## 2. Summary Table

|Syntax|Example|Call|Result|
|---|---|---|---|
|Optional Named|`fn({String? name})`|`fn(name:"A")`|Works, `name=A`|
|Required Named|`fn({required int x})`|`fn(x:10)`|Must pass `x`|
|Default Value|`fn({int x=5})`|`fn()`|`x=5`|
|Mix Positional+Named|`fn(a,{b=1})`|`fn(10,b:2)`|`a=10,b=2`|

---

## 3. Real-World Example

💡 **Flutter ElevatedButton with Named Parameters**

```Dart
import 'package:flutter/material.dart';

void showAlert(BuildContext context,
    {required String title, String message = "No details"}) {
  showDialog(
    context: context,
    builder: (context) => AlertDialog(
      title: Text(title),
      content: Text(message),
      actions: [
        TextButton(onPressed: () => Navigator.pop(context), child: Text("OK")),
      ],
    ),
  );
}

void main() {
  runApp(MaterialApp(
    home: Scaffold(
      body: Center(
        child: Builder(
          builder: (context) => ElevatedButton(
            onPressed: () => showAlert(
              context,
              title: "Welcome",
              message: "This uses named parameters!",
            ),
            child: Text("Show Alert"),
          ),
        ),
      ),
    ),
  ));
}

```

✅ `title` is **required**,

✅ `message` has a **default value**.