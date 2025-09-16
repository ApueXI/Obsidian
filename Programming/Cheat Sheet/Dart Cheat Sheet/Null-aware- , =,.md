---
Created: 2025-09-16T19:50
tags:
  - Operators
---
# 🧩 Dart Null-Aware Operators Cheat Sheet

## 1. Full Explanation

Null-aware operators help handle `null` values **safely** without throwing runtime errors.

---

### 🔹 `??` → Default Value

- Returns the left-hand side if it’s **not null**, otherwise returns the right-hand side.

```Dart
var name = null;
print(name ?? "Guest"); // "Guest"

```

✅ Great for fallback values.

---

### 🔹 `??=` → Assign If Null

- Assigns the value **only if the variable is null**.

```Dart
int? score;
score ??= 100; // score becomes 100
score ??= 200; // no change, still 100
print(score);  // 100

```

✅ Useful for lazy initialization.

---

### 🔹 `?.` → Safe Access

- Calls a property/method **only if the variable is not null**.
- If the variable is null, returns `null` instead of throwing an error.

```Dart
String? text;
print(text?.length); // null (no crash)

text = "Dart";
print(text?.length); // 4

```

✅ Prevents null pointer exceptions.

---

### 🔹 Combined Usage Example

```Dart
class User {
  String? name;
  User(this.name);
}

void main() {
  User? user = null;

  // Safe access
  print(user?.name ?? "Anonymous"); // "Anonymous"

  user = User("Alice");
  print(user?.name ?? "Anonymous"); // "Alice"

  // Assign default if null
  String? nickname;
  nickname ??= "No Nick";
  print(nickname); // "No Nick"
}

```

---

## 2. Summary Table (Quick Reference)

|Operator|Meaning|Example|Result|
|---|---|---|---|
|`??`|Default value if null|`x ?? 10`|`10` if `x` is null|
|`??=`|Assign if null|`x ??= 5`|`x = 5` if `x` was null|
|`?.`|Safe property/method access|`user?.name`|`null` if `user` is null|

---

## 3. Real-World Example

A **settings loader** with null-aware operators:

```Dart
void main() {
  Map<String, String?> settings = {
    "theme": null,
    "language": "en",
  };

  // Use ?? for defaults
  var theme = settings["theme"] ?? "light";
  var language = settings["language"] ?? "en";

  // Assign default if null
  settings["theme"] ??= "dark";

  print("Theme: $theme");
  print("Language: $language");
  print("Updated settings: $settings");

  // Safe access with ?.
  String? username;
  print("Username length: ${username?.length}");
}

```

**Output Example:**

```Plain
Theme: light
Language: en
Updated settings: {theme: dark, language: en}
Username length: null

```

---

⚡ This shows `??`, `??=`, and `?.` working together in a practical config scenario.