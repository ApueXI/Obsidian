---
Created: 2025-09-16T20:01
tags:
  - Functions
---
# 🎯 Dart Arrow Functions Cheat Sheet

## 1. Full Explanation

- **Arrow functions** are shorthand for functions that return a single expression.
- Syntax:

```Dart
returnType functionName(params) => expression;

```

- Equivalent to a full function with `{ return ...; }`.
- Cannot contain multiple statements (only one expression).
- Great for concise code (callbacks, one-liners, Flutter widget building).

---

### 🔹 Basic Example

```Dart
int square(int x) => x * x;

void main() {
  print(square(5)); // 25
}

```

---

### 🔹 With Multiple Parameters

```Dart
int add(int a, int b) => a + b;

void main() {
  print(add(3, 4)); // 7
}

```

---

### 🔹 With `void` Functions

```Dart
void greet(String name) => print("Hello, $name!");

void main() {
  greet("Alice"); // Hello, Alice!
}

```

---

### 🔹 Inside Collections / Callbacks

```Dart
void main() {
  var numbers = [1, 2, 3];
  var doubled = numbers.map((n) => n * 2).toList();

  print(doubled); // [2, 4, 6]
}

```

---

### 🔹 Flutter Example

```Dart
ElevatedButton(
  onPressed: () => print("Button clicked"),
  child: Text("Click Me"),
)

```

✅ Cleaner than writing a block `{ print(...); }`.

---

## 2. Summary Table

|Form|Example|Equivalent Full Function|
|---|---|---|
|Return int|`int sq(int x) => x*x;`|`int sq(int x){ return x*x; }`|
|Return void|`void g(n) => print(n);`|`void g(n){ print(n); }`|
|Callback|`list.map((x)=>x*2)`|`list.map((x){ return x*2; })`|
|Flutter|`onPressed: ()=>print("hi")`|`onPressed: (){ print("hi"); }`|

---

## 3. Real-World Example

💡 **Flutter ListView with Arrow Functions**

```Dart
import 'package:flutter/material.dart';

void main() {
  final items = ["Apple", "Banana", "Cherry"];

  runApp(MaterialApp(
    home: Scaffold(
      body: ListView(
        children: items.map((item) => ListTile(title: Text(item))).toList(),
      ),
    ),
  ));
}

```

✅ `map((item) => ListTile(...))` uses an arrow function for concise widget creation.