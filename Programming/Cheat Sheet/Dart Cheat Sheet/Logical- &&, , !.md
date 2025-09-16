---
Created: 2025-09-16T19:49
tags:
  - Operators
---
# 🧩 Dart Logical Operators Cheat Sheet

## 1. Full Explanation

Logical operators combine **boolean expressions** (`true` / `false`) to make decisions in conditions.

### 🔹 AND (`&&`)

- Returns `true` if **both** sides are true.
- **Short-circuit evaluation**: If the first operand is `false`, Dart won’t check the second.

```Dart
print(true && true);   // true
print(true && false);  // false

var x = 5;
print(x > 0 && x < 10); // true

```

---

### 🔹 OR (`||`)

- Returns `true` if **at least one** side is true.
- Short-circuit: If the first operand is `true`, Dart won’t check the second.

```Dart
print(false || true);   // true
print(false || false);  // false

var y = 20;
print(y < 0 || y > 10); // true

```

---

### 🔹 NOT (`!`)

- Negates a boolean value.
- `!true` → `false`, `!false` → `true`.

```Dart
print(!true);   // false
print(!(5 > 3)); // false

```

---

### 🔹 Short-Circuit Behavior Example

```Dart
bool expensiveCheck() {
  print("expensiveCheck called");
  return true;
}

void main() {
  // Won’t call expensiveCheck, because false && anything = false
  print(false && expensiveCheck()); // false

  // Will call expensiveCheck, because need to check
  print(true && expensiveCheck()); // true (and prints message)
}

```

---

## 2. Summary Table (Quick Reference)

|Operator|Name|Example|Result|
|---|---|---|---|
|`&&`|Logical AND|`true && false`|`false`|
|`\|`|Logical OR|`false \| true`|`true`|
|`!`|Logical NOT|`!(5 > 3)`|`false`|

---

## 3. Real-World Example

A **login validation** system:

```Dart
void main() {
  String? username = "admin";
  String? password = "1234";

  if (username != null && password != null) {
    if (username == "admin" && password == "1234") {
      print("Login successful!");
    } else if (username == "admin" || password == "1234") {
      print("Partial match, check credentials again.");
    } else {
      print("Invalid login.");
    }
  } else {
    print("Username and password required.");
  }
}

```

**Possible Output:**

```Plain
Login successful!

```

---

⚡ This covers `&&`, `||`, and `!` in a realistic scenario.