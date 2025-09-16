---
Created: 2025-09-16T19:43
tags:
  - Introduction-&-Basics
---
# 🚀 Dart Entry Point – `main()` Function

## 1. Full Explanation

### 🔹 The Entry Point

- Every Dart program **must have a** `**main()**` **function**.
- `main()` is the **starting point** of execution (like `int main()` in C++ or `public static void main()` in Java).
- Without it, the Dart VM doesn’t know where to begin.

### 🔹 Syntax

```Dart
void main() {
  print("Hello, Dart!");
}

```

- `void` → return type (main does not return a value).
- `main` → function name (reserved entry point).
- `()` → parentheses (optionally takes arguments).

---

### 🔹 With Arguments

Dart supports command-line arguments:

```Dart
void main(List<String> args) {
  print("Arguments: $args");
}

```

Run with:

```Bash
dart run bin/app.dart hello world
# Output: Arguments: [hello, world]

```

- `args` is a list of strings passed from CLI.
- Useful for **CLI tools** (like reading flags, file paths, etc.).

---

### 🔹 Variations of `main()`

- No args:
    
    ```Dart
    void main() { ... }
    
    ```
    
- With args:
    
    ```Dart
    void main(List<String> args) { ... }
    
    ```
    
- Async main (for `await`):
    
    ```Dart
    Future<void> main() async {
      await Future.delayed(Duration(seconds: 1));
      print("Async main finished!");
    }
    
    ```
    

---

## 2. Summary Table (Quick Reference)

|Form|Use Case|
|---|---|
|`void main()`|Basic entry point.|
|`void main(List<String>)`|Handle CLI arguments.|
|`Future<void> main()`|Use async/await inside main.|
|`Future<void> main(List<String>)`|Async + CLI arguments together.|

---

## 3. Real-World Example

Let’s build a **CLI greeting app** that uses arguments & async:

```Dart
Future<void> main(List<String> args) async {
  final name = args.isNotEmpty ? args[0] : "World";

  print("Starting app...");

  await Future.delayed(Duration(seconds: 1)); // simulate async work
  print("Hello, $name! 🎯");
}

```

Run it:

```Bash
dart run bin/hello.dart Alice
# Output:
# Starting app...
# Hello, Alice! 🎯

```

👉 Shows:

- **Arguments (**`**args**`**)**
- **Async main** (using `await`)
- **Execution starts from** `**main()**`