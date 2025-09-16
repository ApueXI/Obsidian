---
Created: 2025-09-16T19:52
tags:
  - Control-Flow
---
# 🔄 Dart Loops Cheat Sheet

## 1. Full Explanation

Loops let you **repeat code** until a condition is met.

- `**for**` → repeat with a counter.
- `**while**` → repeat as long as a condition is true.
- `**do-while**` → like `while`, but always runs **at least once**.

---

### 🔹 `for` loop (Counter-based)

```Dart
void main() {
  for (int i = 0; i < 5; i++) {
    print("Iteration $i");
  }
}

```

✅ Runs from `i=0` to `i=4`.

---

### 🔹 `while` loop (Condition checked first)

```Dart
void main() {
  int count = 0;

  while (count < 3) {
    print("Count: $count");
    count++;
  }
}

```

✅ Runs until condition becomes false.

---

### 🔹 `do-while` loop (Runs at least once)

```Dart
void main() {
  int num = 0;

  do {
    print("Number: $num");
    num++;
  } while (num < 3);
}

```

✅ Even if condition is false, the body runs once.

---

## 2. Summary Table

|Loop Type|When to Use|Syntax|Runs at least once?|
|---|---|---|---|
|`for`|Known number of iterations|`for (init; condition; update)`|❌ No|
|`while`|Unknown iterations, condition checked first|`while (condition)`|❌ No|
|`do-while`|Must run at least once, then repeat|`do { ... } while (condition);`|✅ Yes|

---

## 3. Real-World Example

💡 **Retrying a network request simulation**

```Dart
void main() {
  int retries = 0;
  bool success = false;

  do {
    print("Attempt ${retries + 1}...");
    retries++;

    // Fake success on 3rd try
    if (retries == 3) {
      success = true;
      print("Connected ✅");
    }
  } while (!success && retries < 5);

  if (!success) {
    print("Failed after $retries attempts ❌");
  }
}

```

**Output:**

```Plain
Attempt 1...
Attempt 2...
Attempt 3...
Connected ✅

```