---
Created: 2025-09-16T19:57
tags:
  - Functions
---
# 🏗️ Dart Functions Cheat Sheet

## 1. Full Explanation

Functions in Dart are defined with the syntax:

```Plain
returnType functionName(parameters) {
  // body
}

```

- `returnType` → The type of value returned (`int`, `String`, `void`, etc.).
- `functionName` → Identifier (camelCase by convention).
- `parameters` → Input values (can be required, optional, named, default).
- Dart also supports **arrow functions** (`=>`) for single expressions.

---

### 🔹 Basic Function

```Dart
int add(int a, int b) {
  return a + b;
}

void main() {
  print(add(3, 4)); // 7
}

```

---

### 🔹 Function Without Return (`void`)

```Dart
void greet(String name) {
  print("Hello, $name!");
}

```

---

### 🔹 Arrow Function (Expression Body)

```Dart
int square(int x) => x * x;

void main() {
  print(square(5)); // 25
}

```

---

### 🔹 Optional Positional Parameters

```Dart
void printInfo(String name, [int? age]) {
  print("Name: $name, Age: ${age ?? "unknown"}");
}

void main() {
  printInfo("Alice");         // Name: Alice, Age: unknown
  printInfo("Bob", 30);       // Name: Bob, Age: 30
}

```

---

### 🔹 Named Parameters

```Dart
void greet({required String name, int age = 18}) {
  print("Hello $name, age $age");
}

void main() {
  greet(name: "Charlie");          // Hello Charlie, age 18
  greet(name: "Diana", age: 25);   // Hello Diana, age 25
}

```

---

### 🔹 Anonymous Functions

```Dart
void main() {
  var list = [1, 2, 3];

  list.forEach((n) {
    print(n * 2);
  });
}

```

---

### 🔹 Functions as First-Class Citizens

Functions can be stored in variables and passed around.

```Dart
int multiply(int a, int b) => a * b;

void main() {
  var operation = multiply;
  print(operation(3, 4)); // 12
}

```

---

## 2. Summary Table

|Function Type|Syntax|Example|
|---|---|---|
|Basic|`returnType name(params) {}`|`int add(int a, int b){}`|
|Void|`void name(params) {}`|`void greet(String n){}`|
|Arrow|`type name(params) => expr;`|`int sq(int x)=>x*x;`|
|Optional Positional|`type name(type p, [type? opt])`|`printInfo("A",[20])`|
|Named|`type name({type p, type p2})`|`greet(name:"A", age:20)`|
|Anonymous|`(params) { body }`|`(n){print(n);}`|
|Stored in var|`var f = fn;`|`f(3,4);`|

---

## 3. Real-World Example

💡 **Flutter Button Callback with Function**

```Dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(
    home: Scaffold(
      body: Center(
        child: ElevatedButton(
          onPressed: () => greet("Flutter"),
          child: Text("Click Me"),
        ),
      ),
    ),
  ));
}

void greet(String name) {
  print("Hello, $name!");
}

```

✅ Here, `greet` is a normal Dart function, passed as a callback to the button.