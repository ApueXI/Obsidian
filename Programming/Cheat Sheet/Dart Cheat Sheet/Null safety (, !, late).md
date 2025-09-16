---
Created: 2025-09-16T19:45
tags:
  - Basic-Syntax
---
# 🧩 Dart Null Safety Cheat Sheet

## 1. Full Explanation

### 🔹 What is Null Safety?

- Dart ensures **variables cannot contain** `**null**` **unless explicitly allowed**.
- This prevents **runtime null reference errors** ("null pointer exceptions").
- You must explicitly opt-in with `?` if a variable can be `null`.

---

### 🔹 Nullable Types (`?`)

- Add `?` to make a type nullable.
- Without `?`, it’s **non-nullable** by default.

```Dart
int x = 5;       // non-nullable int
int? y;          // nullable int, defaults to null
y = null;        // ✅ allowed

```

⚠️ Using a nullable variable without checking → error:

```Dart
print(y + 1); // ❌ error: y might be null

```

✅ Safe way: null-check or null-aware operators (`??`, `?.`):

```Dart
print((y ?? 0) + 1); // ✅ safe

```

---

### 🔹 Null Assertion (`!`)

- Tells Dart: “I’m sure this value is not null.”
- Throws runtime error if the value **is actually null**.

```Dart
int? age;
print(age! + 1); // ❌ runtime error: Null check operator used on a null value

```

✅ Safe usage when logically guaranteed non-null:

```Dart
int? maybeAge = 18;
print(maybeAge! + 1); // ✅ 19

```

---

### 🔹 `late` Keyword

- Defers initialization of a **non-nullable** variable.
- Tells Dart: “I’ll assign this later before using it.”
- Used when you **can’t initialize immediately** (e.g., dependency injection, heavy computation).

```Dart
late String username;
username = "Alice";   // must be assigned before use
print(username);      // ✅ Alice

```

⚠️ Using before assignment → runtime error:

```Dart
late int score;
print(score); // ❌ LateInitializationError

```

---

### 🔹 Combining with `final` and `const`

```Dart
final String? name = null;   // nullable final
const String greeting = "Hi"; // compile-time constant
late final String token;     // assigned once, later

```

---

### 🔹 Null-Aware Operators (quick overview)

- `??` → default value
- `?.` → safe method/property access
- `??=` → assign only if null

```Dart
int? a;
print(a ?? 10);   // 10
a ??= 5;          // a becomes 5
print(a?.isEven); // true

```

---

## 2. Summary Table (Quick Reference)

|Symbol/Keyword|Meaning|Example|Behavior|
|---|---|---|---|
|`?`|Nullable type|`int? x;`|Can hold `int` or `null`|
|`!`|Null assertion|`x!`|Forces non-null, runtime error if null|
|`late`|Deferred initialization|`late String name;`|Must assign before use|
|`??`|Default if null|`x ?? 0`|Returns `x` if not null, else `0`|
|`?.`|Safe access|`x?.length`|Calls only if `x` not null|
|`??=`|Assign if null|`x ??= 10`|Assigns only when `x` is null|

---

## 3. Real-World Example

A **user profile loader** with null safety:

```Dart
class User {
  final String name;
  final int? age;         // nullable
  late final String token; // will be assigned later

  User(this.name, {this.age});

  void authenticate(String authToken) {
    token = authToken; // assign once
  }
}

void main() {
  var user = User("Alice", age: null);

  // Safe null check with ??
  print("Age: ${user.age ?? 'Unknown'}");

  // Authenticate later with 'late'
  user.authenticate("secureToken123");
  print("Token: ${user.token}");

  // Dangerous null assertion example
  int? score;
  // print(score!); // ❌ would throw LateInitializationError
}

```

**Output Example:**

```Plain
Age: Unknown
Token: secureToken123

```

---

⚡ This shows `?` for optional age, `late` for deferred token, and `??` for safe default.