---
Created: 2025-09-16T19:44
tags:
  - Basic-Syntax
---
# 📝 Dart Variables & Constants Cheat Sheet (`var`, `final`, `const`)

## 1. Full Explanation

### 🔹 `var`

- Declares a **mutable variable** (can be reassigned).
- Type is **inferred** at compile time, but you cannot change the type later.

```Dart
var name = "Alice";   // inferred as String
name = "Bob";         // ✅ allowed
// name = 123;        // ❌ error: type mismatch

```

---

### 🔹 `final`

- Declares a **single-assignment variable**.
- Value is **set once** at runtime → cannot be reassigned.
- Useful for values that are known only at runtime but shouldn’t change later.

```Dart
final currentTime = DateTime.now();
print(currentTime);   // ✅ works
// currentTime = DateTime.now(); // ❌ cannot reassign

```

---

### 🔹 `const`

- Declares a **compile-time constant**.
- Value must be **known at compile time**.
- Faster & more memory efficient since Dart **canonicalizes const objects** (reuses them).

```Dart
const pi = 3.14159;
const list = [1, 2, 3];
// list.add(4); // ❌ error: const collection is immutable

```

---

### 🔹 Key Differences

|Keyword|When Value is Fixed|Can Reassign?|Example Use Case|
|---|---|---|---|
|`var`|Mutable, type inferred|✅ Yes|Regular variables that can change|
|`final`|Fixed at runtime|❌ No|Runtime constants (e.g., DateTime.now)|
|`const`|Fixed at compile-time|❌ No|Compile-time constants (e.g., pi)|

---

### 🔹 Gotchas

1. `final` vs `const`:
    
    ```Dart
    final now = DateTime.now(); // ✅ runtime allowed
    const now = DateTime.now(); // ❌ error: not compile-time constant
    
    ```
    
2. **Const objects are canonicalized**:
    
    ```Dart
    const a = [1, 2];
    const b = [1, 2];
    print(identical(a, b)); // true (same object)
    
    ```
    
3. **Use** `**late**` **with** `**final**` for delayed initialization:
    
    ```Dart
    late final token;
    token = "abc123"; // ✅ assign once later
    
    ```
    

---

## 2. Summary Table (Quick Reference)

|Keyword|Compile-time?|Runtime?|Reassign?|Common Use|
|---|---|---|---|---|
|`var`|❌ No|✅ Yes|✅ Yes|Normal mutable variable|
|`final`|❌ No|✅ Yes|❌ No|Values fixed at runtime|
|`const`|✅ Yes|❌ No|❌ No|Values fixed at compile time|

---

## 3. Real-World Example

```Dart
void main() {
  // var → mutable
  var user = "Alice";
  user = "Bob"; // ✅ allowed
  print("User: $user");

  // final → runtime fixed
  final timestamp = DateTime.now();
  print("Timestamp: $timestamp");

  // const → compile-time fixed
  const apiVersion = "v1.0";
  print("API Version: $apiVersion");

  // const objects are canonicalized
  const list1 = [1, 2];
  const list2 = [1, 2];
  print(identical(list1, list2)); // true
}

```

**Output example:**

```Plain
User: Bob
Timestamp: 2025-09-16 18:05:32.123456
API Version: v1.0
true

```

👉 This shows:

- `var` is mutable.
- `final` locks after first assignment at runtime.
- `const` is compile-time and canonicalized.