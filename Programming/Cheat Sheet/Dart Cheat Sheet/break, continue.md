---
Created: 2025-09-16T19:53
tags:
  - Control-Flow
---
# ⏹️ Dart `break` & `continue` Cheat Sheet

## 1. Full Explanation

### 🔹 `break`

- Exits the **entire loop** immediately.
- Skips remaining iterations.

```Dart
void main() {
  for (int i = 1; i <= 5; i++) {
    if (i == 3) {
      break; // stop loop entirely
    }
    print(i);
  }
}

```

**Output:**

```Plain
1
2

```

---

### 🔹 `continue`

- Skips the **current iteration** and jumps to the next one.

```Dart
void main() {
  for (int i = 1; i <= 5; i++) {
    if (i == 3) {
      continue; // skip printing 3
    }
    print(i);
  }
}

```

**Output:**

```Plain
1
2
4
5

```

---

## 2. Summary Table

|Keyword|Meaning|Effect|
|---|---|---|
|`break`|Exit loop completely|Stops loop execution|
|`continue`|Skip current iteration|Moves to next iteration|

---

## 3. Real-World Example

💡 **Searching a List**

```Dart
void main() {
  List<String> users = ["Alice", "Bob", "Charlie", "David"];

  for (var user in users) {
    if (user == "Charlie") {
      print("Found Charlie! ✅");
      break; // stop searching once found
    }
  }

  print("Filter users (skip Bob):");
  for (var user in users) {
    if (user == "Bob") continue; // skip Bob
    print(user);
  }
}

```

**Output:**

```Plain
Found Charlie! ✅
Filter users (skip Bob):
Alice
Charlie
David

```

---

⚡ In Flutter/Dart, `continue` is very handy when filtering data inside loops, and `break` is often used when searching or early exiting.