---
Created: 2025-09-16T19:52
tags:
  - Control-Flow
---
# 🎯 Dart `switch`, `case`, `default` Cheat Sheet

## 1. Full Explanation

- ✅ `**switch**` is used when you want to compare a value against **multiple constant options**.
- ✅ Each `**case**` must end with a `break` (or `return`, `continue`, `throw`) unless you want _fall-through_ using `continue case`.
- ✅ `**default**` runs if no cases match.

⚡ Dart `switch` works with:

- `int`, `String`, `enum`, and compile-time constants.

---

### 🔹 Basic Example

```Dart
void main() {
  int day = 3;

  switch (day) {
    case 1:
      print("Monday");
      break;
    case 2:
      print("Tuesday");
      break;
    case 3:
      print("Wednesday");
      break;
    default:
      print("Invalid day");
  }
}

```

**Output:**

```Plain
Wednesday

```

---

### 🔹 Without `break` → Compile Error

```Dart
// ❌ Dart requires case to end with break/return/throw
switch (x) {
  case 1:
    print("One");
  // Error if missing break or similar
}

```

---

### 🔹 Using `continue case` (Fall-through)

```Dart
void main() {
  var grade = "B";

  switch (grade) {
    case "A":
      print("Excellent!");
      break;
    case "B":
    case "C":
      print("Good job!");
      break;
    case "D":
      print("Needs improvement.");
      break;
    default:
      print("Invalid grade");
  }
}

```

✅ Here, `"B"` and `"C"` share the same logic.

---

## 2. Summary Table

|Keyword|Purpose|Example|
|---|---|---|
|`switch`|Start multi-branch structure|`switch(x) { ... }`|
|`case`|Match against a constant|`case 1:`|
|`break`|Exit the switch after match|`break;`|
|`continue case`|Jump to another case|`continue case "C";`|
|`default`|Runs if no case matches|`default: print("Invalid");`|

---

## 3. Real-World Example

💡 **Command Handler**

```Dart
void main() {
  String command = "login";

  switch (command) {
    case "login":
      print("Logging in...");
      break;
    case "logout":
      print("Logging out...");
      break;
    case "signup":
      print("Creating new account...");
      break;
    default:
      print("Unknown command");
  }
}

```

**Output:**

```Plain
Logging in...
```