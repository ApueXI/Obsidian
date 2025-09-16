---
Created: 2025-09-16T20:25
tags:
  - Null-Safety-Deep-Dive
---
# 🎯 Dart Nullable Types Cheat Sheet

## 1. Full Explanation

- **Nullable types** are declared by adding `?` after the type: `String?`, `int?`, etc.
- A variable of type `T?` can hold **either a value of type** `**T**` **or** `**null**`.
- Dart’s **sound null safety** ensures:
    - Non-nullable variables (`String`) **cannot be null**
    - Nullable variables (`String?`) **may contain null**
- Helps **catch null errors at compile-time**.

---

## 2. Declaring Nullable Variables

```Dart
void main() {
  String? name;      // nullable
  name = null;       // ✅ allowed
  name = "Alice";    // ✅ allowed
  print(name);
}

```

✅ `String?` can safely hold null or a string.

---

## 3. Accessing Nullable Variables

### **1. Null Check**

```Dart
void main() {
  String? name = "Alice";

  if (name != null) {
    print(name.length); // safe access
  }
}

```

---

### **2. Null-Aware Operator (**`**?.**`**)**

```Dart
void main() {
  String? name;
  print(name?.length); // prints null instead of throwing error
}

```

✅ `?.` prevents null dereference.

---

### **3. Default Value (**`**??**`**)**

```Dart
void main() {
  String? name;
  print(name ?? "Unknown"); // Unknown
}

```

✅ `??` provides a **fallback value** if null.

---

### **4. Null Assertion (**`**!**`**)**

```Dart
void main() {
  String? name = "Alice";
  print(name!.length); // 5 → asserts value is not null
}

```

⚠ Use `!` **only if you are sure the value is not null**, otherwise runtime error occurs.

---

## 4. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Nullable type|`String? name`|Can be null or value|
|Null-aware access|`name?.length`|Returns null if variable is null|
|Default fallback|`name ?? "default"`|Use value if null|
|Null assertion|`name!`|Force non-null (runtime error if null)|
|Safe check|`if (name != null)`|Access safely|

---

## 5. Real-World Example

```Dart
void main() {
  String? userInput;

  // Using null-aware operator
  print(userInput?.toUpperCase()); // null

  // Using default fallback
  print(userInput ?? "No input");  // No input

  // Assign value
  userInput = "hello";

  print(userInput!.length);         // 5
}

```

✅ Nullable types make Dart **safer and more predictable**, especially in Flutter forms, API responses, and user input.