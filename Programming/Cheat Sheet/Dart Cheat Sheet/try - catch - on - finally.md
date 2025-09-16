---
Created: 2025-09-16T20:11
tags:
  - Error-Handling
---
# 🎯 Dart `try / catch / on / finally` Cheat Sheet

## 1. Full Explanation

- `**try**` → Wraps code that might throw an exception.
- `**catch**` → Handles the exception; provides access to the exception object.
- `**on**` → Handles **specific exception types**.
- `**finally**` → Optional block that **always runs**, whether an exception occurs or not.

---

## 2. Syntax

```Dart
try {
  // risky code
} on SpecificException catch (e) {
  // handle a specific exception
} catch (e, stackTrace) {
  // handle any exception
} finally {
  // code that always runs
}

```

- `e` → Exception object
- `stackTrace` → Stack trace for debugging

---

## 3. Basic Example

```Dart
void main() {
  try {
    int result = 12 ~/ 0; // integer division by zero
    print(result);
  } catch (e) {
    print("Caught exception: $e");
  } finally {
    print("This always runs");
  }
}

```

✅ Output:

```Plain
Caught exception: IntegerDivisionByZeroException
This always runs

```

---

## 4. Using `on` for Specific Exception

```Dart
void main() {
  try {
    int.parse("abc"); // throws FormatException
  } on FormatException catch (e) {
    print("FormatException caught: $e");
  } catch (e) {
    print("Other exception caught: $e");
  } finally {
    print("Finished exception handling");
  }
}

```

✅ `on` handles **specific exceptions**, `catch` handles **all others**.

---

## 5. Accessing Stack Trace

```Dart
void main() {
  try {
    int.parse("xyz");
  } catch (e, stackTrace) {
    print("Error: $e");
    print("StackTrace: $stackTrace");
  }
}

```

✅ Useful for **debugging**, especially in larger applications.

---

## 6. Summary Table

|Keyword|Usage|Notes|
|---|---|---|
|try|`try { ... }`|Wrap code that might fail|
|catch|`catch (e)`|Catch any exception|
|on|`on ExceptionType catch (e)`|Catch specific exception types|
|finally|`finally { ... }`|Always executed, even if exception occurs|
|catch with stack trace|`catch (e, stackTrace)`|Debugging purposes|

---

## 7. Real-World Example

💡 **File Reading Example**

```Dart
void readFile(String path) {
  try {
    // pretend to read a file
    if (path != "file.txt") throw FileSystemException("File not found");
    print("File read successfully");
  } on FileSystemException catch (e) {
    print("Error: ${e.message}");
  } catch (e) {
    print("Unknown error: $e");
  } finally {
    print("File read attempt finished");
  }
}

void main() {
  readFile("wrongfile.txt");
}

```

✅ Demonstrates **specific exception handling**, fallback handling, and guaranteed cleanup.