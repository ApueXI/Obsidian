---
Created: 2025-09-16T19:44
tags:
  - Basic-Syntax
---
# 🌀 Dart `dynamic` vs `Object` vs `var` Cheat Sheet

## 1. Full Explanation

### 🔹 `var`

- **Not a type** → it means _“infer the type from the value at compile-time.”_
- Once inferred, the variable has a **fixed type** and can’t change later.

```Dart
var x = 10;      // inferred as int
x = 20;          // ✅ allowed
// x = "hello";  // ❌ error: String not assignable to int

```

So `var` ≈ “auto type inference” (like `auto` in C++ or `var` in C#).

---

### 🔹 `Object`

- **Base class of all Dart types** (like `Object` in Java or C#).
- You can assign _any value_ to an `Object` variable.
- But you must **cast** or use type checks before calling type-specific methods.

```Dart
Object y = "Hello";
print(y);               // ✅ works, toString() is in Object
// print(y.length);     // ❌ error: Object has no length
print((y as String).length); // ✅ type cast

```

Good for when you want **flexibility but still some safety**.

---

### 🔹 `dynamic`

- **Disables static type checking**.
- Any operation is allowed → errors only show at runtime.
- Similar to Python variables or `var` in JavaScript.

```Dart
dynamic z = "Hello";
print(z.length);   // ✅ works (runtime check)
z = 123;
print(z + 10);     // ✅ runtime math
z.foo();           // ❌ compiles fine, crashes at runtime

```

Good for cases where type is truly unknown until runtime (e.g., JSON decoding).

---

### 🔹 Key Differences

|Feature|`var`|`Object`|`dynamic`|
|---|---|---|---|
|Meaning|Type inference at compile time|Base class of all types|Disables static type checking|
|Type fixed?|✅ Yes (inferred once)|✅ Yes (always Object)|❌ No, can change anytime|
|Method access|Only valid for inferred type|Only Object methods unless cast|Any method allowed (checked at runtime)|
|Safety|Compile-time safe|Compile-time safe, needs casting|Runtime-only safety|
|Example use|Normal variables|Store multiple types in one var|JSON, dynamic APIs, scripting|

---

## 2. Summary Table (Quick Reference)

|Keyword|Static Check?|Runtime Flexibility|When to Use|
|---|---|---|---|
|`var`|✅ Yes|❌ No|Regular variables with inferred type|
|`Object`|✅ Yes|⚠️ Needs cast|Store any type but still use safely|
|`dynamic`|❌ No|✅ Yes|Unstructured data (JSON, dynamic APIs)|

---

## 3. Real-World Example

Imagine parsing **JSON data** from an API:

```Dart
import 'dart:convert';

void main() {
  String jsonStr = '{"name": "Alice", "age": 25}';
  dynamic data = jsonDecode(jsonStr);  // returns dynamic

  // dynamic → no compile-time safety
  print("Name: ${data['name']}");
  print("Age: ${data['age']}");

  // Object → safer but needs cast
  Object obj = data['age'];
  print("Age as int: ${(obj as int) + 5}");

  // var → type inferred once
  var name = data['name'];  // inferred as String
  print("Uppercase: ${name.toUpperCase()}");
}

```

👉 Shows when each is useful:

- `dynamic` for JSON (runtime structure).
- `Object` when storing different types safely.
- `var` for normal inferred variables.