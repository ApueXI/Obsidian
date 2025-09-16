---
Created: 2025-09-16T20:26
tags:
  - Null-Safety-Deep-Dive
---
# 🎯 Dart Null Assertion (`!`) Cheat Sheet

## 1. Full Explanation

- The **null assertion operator** `**!**` tells Dart:
    
    > “I guarantee this value is not null here.”
    
- Converts a **nullable type** `**T?**` to a **non-nullable type** `**T**`.
- Use **only when you are certain** the value is **non-null at runtime**.
- ⚠ **Misuse can cause runtime exceptions (**`**LateInitializationError**` **or** `**NullPointerException**`**)**.

---

## 2. Basic Example

```Dart
void main() {
  String? name = "Alice";
  print(name!.length); // 5 → asserts non-null
}

```

✅ `name!` converts `String?` → `String`.

---

## 3. Runtime Error Example

```Dart
void main() {
  String? name;
  print(name!.length); // ❌ Runtime error: Null check operator used on null
}

```

⚠ Only use `!` if you are **sure the variable is initialized**.

---

## 4. Common Use Cases

### **1. Accessing Nullable Parameter**

```Dart
void greet(String? name) {
  print("Hello, ${name!}"); // safe only if name is not null
}

void main() {
  greet("Bob");  // Hello, Bob
  // greet(null); // ❌ Runtime error
}

```

---

### **2. Late Variables**

```Dart
late String name;

void main() {
  name = "Alice";
  print(name!.length); // 5 → safe after initialization
}

```

✅ Often used when **late initialization** guarantees a value before first use.

---

### **3. Working with Collections**

```Dart
void main() {
  List<String?>? list = ["Alice", "Bob", null];

  print(list![0]!.length); // 5 → asserts list and element are non-null
}

```

- `list!` → list itself is non-null
- `list[0]!` → element is non-null

---

## 5. Summary Table

|Operator|Syntax|Notes|
|---|---|---|
|Null assertion|`variable!`|Converts `T?` → `T`|
|Use case|`String? name; print(name!.length);`|Only when sure it’s non-null|
|Risk|`LateInitializationError` or `NullPointerException`|If variable is actually null|
|Alternative|`variable?.length ?? 0`|Safe null-aware access|

---

## 6. Real-World Example

💡 **Flutter TextField Value**

```Dart
String? input;

void main() {
  input = "Hello";

  // Access value safely using null assertion
  print(input!.toUpperCase()); // HELLO
}

```

✅ Null assertion is **useful when you know input is initialized**, e.g., after form validation.