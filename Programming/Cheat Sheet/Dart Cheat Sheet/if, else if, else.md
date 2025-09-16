---
Created: 2025-09-16T19:51
tags:
  - Control-Flow
---
# 🔀 Dart `if`, `else if`, `else` Cheat Sheet

## 1. Full Explanation

Dart uses **standard conditional statements** to control the program flow.

- ✅ `**if**` → executes a block if the condition is true.
- ✅ `**else if**` → provides additional conditions if the first is false.
- ✅ `**else**` → executes if none of the conditions are true.

⚡ Conditions must be **boolean expressions** (`true` / `false`).

---

### 🔹 Basic `if`

```Dart
int score = 80;

if (score >= 50) {
  print("You passed!");
}

```

---

### 🔹 `if...else`

```Dart
int score = 40;

if (score >= 50) {
  print("You passed!");
} else {
  print("You failed!");
}

```

---

### 🔹 `if...else if...else`

```Dart
int score = 85;

if (score >= 90) {
  print("Grade: A");
} else if (score >= 75) {
  print("Grade: B");
} else if (score >= 60) {
  print("Grade: C");
} else {
  print("Grade: F");
}

```

---

## 2. Summary Table

|Structure|Usage|Example|
|---|---|---|
|`if`|Run only when condition is true|`if (x > 0) print("Positive");`|
|`if...else`|Choose between two options|`if (x % 2 == 0) print("Even"); else print("Odd");`|
|`if...else if...else`|Check multiple conditions|`if (score > 90) ... else if (score > 80) ... else ...`|

---

## 3. Real-World Example

💡 **Login Check Simulation**

```Dart
void main() {
  String username = "admin";
  String password = "1234";

  if (username == "admin" && password == "1234") {
    print("Login successful ✅");
  } else if (username == "admin") {
    print("Wrong password ❌");
  } else {
    print("User not found 🚫");
  }
}

```

**Output Examples:**

- If correct → `Login successful ✅`
- If wrong password → `Wrong password ❌`
- If wrong user → `User not found 🚫`