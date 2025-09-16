---
Created: 2025-09-16T19:45
tags:
  - Basic-Syntax
---
# 🧩 Dart Type Inference Cheat Sheet

## 1. Full Explanation

### 🔹 What is Type Inference?

- Dart is a **statically typed language**, but it can **infer types** automatically from the initializer.
- When you use `var`, `final`, or `const` **without explicitly specifying a type**, Dart infers it at **compile-time**.

```Dart
var x = 10;       // inferred as int
final y = "Hi";   // inferred as String
const pi = 3.14;  // inferred as double

```

---

### 🔹 How it Works

- The **initializer expression** determines the type.
- Once inferred, the type **cannot change**.

```Dart
var value = 42;   // inferred as int
// value = "hello"; // ❌ error: String not assignable to int

```

---

### 🔹 With `dynamic` vs `Object`

- If you **don’t provide an initializer**, `var` defaults to **dynamic**.
- If you explicitly want a flexible type → use `dynamic` or `Object`.

```Dart
var anything;     // inferred as dynamic
anything = 123;
anything = "Hello"; // ✅ allowed (runtime check)

```

```Dart
Object obj = 42;     // ✅ can store anything
obj = "Text";        // ✅ but requires casting for type-specific methods

```

---

### 🔹 Type Inference with `final` and `const`

- `final` → runtime value, inferred type.
- `const` → compile-time value, inferred type.

```Dart
final today = DateTime.now(); // inferred as DateTime
const maxScore = 100;         // inferred as int

```

---

### 🔹 Function Inference

- Functions also infer return type and parameter types (if omitted).

```Dart
// Return type inferred as int
add(a, b) {
  return a + b;
}

```

⚠️ But: Without explicit types, parameters default to **dynamic**, which is dangerous.

```Dart
print(add(2, 3));       // ✅ works
print(add("a", "b"));   // ✅ runtime concatenation, not type-safe!

```

✅ Best practice: **Always specify function parameter & return types** for clarity.

---

### 🔹 Collection Literals

Type inference works inside **lists, sets, and maps**:

```Dart
var numbers = [1, 2, 3];          // inferred as List<int>
var names = {"Alice", "Bob"};     // inferred as Set<String>
var scores = {"Alice": 95};       // inferred as Map<String, int>

```

---

## 2. Summary Table (Quick Reference)

|Keyword|Inference Rule|Example|
|---|---|---|
|`var`|Infers type from initializer|`var x = 10; // int`|
|`var`|No initializer → `dynamic`|`var y; // dynamic`|
|`final`|Infers type from runtime value|`final name = "Dart"; // String`|
|`const`|Infers type from compile-time constant|`const pi = 3.14; // double`|
|Function|Infers return type from body, params → dynamic if untyped|`add(a, b)` → params dynamic|

---

## 3. Real-World Example

Let’s build a **score tracking app** using inference:

```Dart
void main() {
  var user = "Alice";           // String
  final today = DateTime.now(); // DateTime
  const pi = 3.14;              // double

  var scores = {"math": 95, "science": 90}; // Map<String, int>

  print("User: $user");
  print("Date: $today");
  print("Pi: $pi");
  print("Scores: $scores");

  // Function with inferred return type
  var average = (int a, int b) => (a + b) / 2;
  print("Average score: ${average(95, 90)}");
}

```

**Output Example:**

```Plain
User: Alice
Date: 2025-09-16 18:45:00.123456
Pi: 3.14
Scores: {math: 95, science: 90}
Average score: 92.5

```

👉 Shows inference in variables, constants, maps, and functions.