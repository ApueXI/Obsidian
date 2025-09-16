---
Created: 2025-09-16T20:31
tags:
  - Dart-Core-Library-(no-external-imports)
---
# 🎯 Dart Exceptions Cheat Sheet

## 1. Full Explanation

- **Exceptions** represent **unexpected runtime errors**.
- Dart uses `**throw**` to raise an exception and `**try-catch-finally**` to handle them.
- Built-in exceptions in `dart:core` include:
    - `**FormatException**` → invalid format (e.g., parsing string to int)
    - `**UnsupportedError**` → operation not supported
    - `**RangeError**` → index or range out of bounds
    - `**StateError**` → invalid state for the operation
    - `**ArgumentError**` → invalid argument passed to a function
    - `**NoSuchMethodError**` → calling undefined method/property

---

## 2. Example: FormatException

```Dart
void main() {
  try {
    int number = int.parse("abc"); // ❌ invalid integer
  } on FormatException catch (e) {
    print("Format error: $e");
  }
}

```

✅ Catches invalid parsing.

---

## 3. Example: UnsupportedError

```Dart
void doSomething(bool supported) {
  if (!supported) throw UnsupportedError("This operation is not supported!");
}

void main() {
  try {
    doSomething(false);
  } on UnsupportedError catch (e) {
    print(e); // This operation is not supported!
  }
}

```

---

## 4. Example: RangeError

```Dart
void main() {
  var list = [1, 2, 3];
  try {
    print(list[5]); // ❌ out of range
  } on RangeError catch (e) {
    print("Range error: $e");
  }
}

```

---

## 5. Using `catch` and `finally`

```Dart
void main() {
  try {
    int.parse("abc");
  } catch (e, stackTrace) {
    print("Caught exception: $e");
    print("Stack trace: $stackTrace");
  } finally {
    print("This always runs");
  }
}

```

✅ `finally` is executed **regardless of success or exception**.

---

## 6. Custom Exceptions

```Dart
class MyException implements Exception {
  final String message;
  MyException(this.message);
  @override
  String toString() => "MyException: $message";
}

void main() {
  try {
    throw MyException("Something went wrong!");
  } catch (e) {
    print(e); // MyException: Something went wrong!
  }
}

```

---

## 7. Summary Table

|Exception|Cause / Use|
|---|---|
|`FormatException`|Invalid string format (e.g., parsing)|
|`UnsupportedError`|Operation not supported|
|`RangeError`|Index or range out of bounds|
|`StateError`|Invalid object state|
|`ArgumentError`|Invalid argument passed|
|`NoSuchMethodError`|Calling undefined method or property|
|Custom|User-defined errors using `implements Exception`|

---

## 8. Real-World Example

💡 **Parsing user input safely**

```Dart
void main() {
  String input = "123a";
  try {
    int value = int.parse(input);
    print("Parsed value: $value");
  } on FormatException {
    print("Invalid number input: $input");
  }
}

```

✅ Avoids app crash from **invalid user input**.