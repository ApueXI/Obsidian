---
Created: 2025-09-16T20:24
tags:
  - Memory-&-Performance
---
# 🎯 Dart Variables: `final` vs `const` vs `var` Cheat Sheet

## 1. Full Explanation

|Keyword|Meaning|When to Use|Key Notes|
|---|---|---|---|
|`var`|Declares a variable **with inferred type**|Use when value can **change**|Mutable by default|
|`final`|Declares a **runtime constant**|Use for **immutable references** assigned **once at runtime**|Object fields can still be mutable|
|`const`|Declares a **compile-time constant**|Use for **immutable values known at compile-time**|Object fields and collections are fully immutable; canonicalized|

---

## 2. Examples

### `**var**` – mutable variable

```Dart
void main() {
  var name = "Alice"; // inferred as String
  name = "Bob";       // ✅ Can reassign
  print(name);        // Bob
}

```

---

### `**final**` – runtime constant

```Dart
void main() {
  final currentTime = DateTime.now(); // value known at runtime
  // currentTime = DateTime.now(); // ❌ Cannot reassign
  print(currentTime);

  final list = [1, 2, 3];
  list.add(4); // ✅ Can mutate contents
  print(list); // [1, 2, 3, 4]
}

```

---

### `**const**` – compile-time constant

```Dart
void main() {
  const pi = 3.1415; // compile-time known
  // pi = 3.14; // ❌ Cannot reassign

  const numbers = [1, 2, 3];
  // numbers[0] = 99; // ❌ Cannot mutate
  print(numbers);
}

```

✅ `const` objects are **fully immutable** and **canonicalized** in memory.

---

## 3. Choosing the Right Keyword

|Scenario|Recommended|
|---|---|
|Value can change|`var`|
|Value known only at runtime but shouldn’t change|`final`|
|Value known at compile-time and fully immutable|`const`|
|Immutable configuration objects (e.g., colors, constants)|`const`|
|Immutable object reference but mutable contents|`final`|

---

## 4. Real-World Flutter Example

```Dart
class AppColors {
  static const primary = Color(0xFF0000FF); // compile-time constant
}

void main() {
  final date = DateTime.now(); // runtime constant
  var userName = "Alice";      // mutable

  userName = "Bob";             // ✅
  print("$userName, $date, ${AppColors.primary}");
}

```

✅ **Use** `**const**` **for immutable config**, `final` for runtime values, `var` for mutable data.