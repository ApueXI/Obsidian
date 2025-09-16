---
Created: 2025-09-16T20:17
tags:
  - Asynchronous-Programming
---
# 🎯 Dart Async Error Handling Cheat Sheet

## 1. Full Explanation

- `**try-catch**` **works with async/await** just like synchronous code.
- Place the `await` calls **inside the** `**try**` **block**.
- Use `**catch**` to handle the error, optionally with `**stackTrace**`.
- Use `**finally**` to execute code regardless of whether an error occurred.

---

## 2. Basic Example

```Dart
Future<String> fetchData(bool fail) async {
  await Future.delayed(Duration(seconds: 1));
  if (fail) throw Exception("Failed to fetch data");
  return "Data received";
}

void main() async {
  try {
    var data = await fetchData(true);
    print(data);
  } catch (e) {
    print("Caught error: $e"); // Caught error: Exception: Failed to fetch data
  } finally {
    print("Fetch attempt finished");
  }
}

```

✅ The `finally` block runs **regardless of success or failure**.

---

## 3. Using `catch` with Stack Trace

```Dart
Future<void> riskyOperation() async {
  await Future.delayed(Duration(seconds: 1));
  throw FormatException("Invalid format");
}

void main() async {
  try {
    await riskyOperation();
  } catch (e, stackTrace) {
    print("Error: $e");
    print("Stack trace: $stackTrace");
  }
}

```

✅ Useful for **debugging and logging** asynchronous errors.

---

## 4. Handling Specific Exceptions

```Dart
Future<int> parseNumber(String value) async {
  await Future.delayed(Duration(seconds: 1));
  return int.parse(value); // may throw FormatException
}

void main() async {
  try {
    await parseNumber("abc");
  } on FormatException catch (e) {
    print("Format error: $e"); // Format error: FormatException: Invalid radix-10 number
  } catch (e) {
    print("Other error: $e");
  }
}

```

✅ `on ExceptionType` allows **catching specific exception types**.

---

## 5. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Try async|`try { await future(); }`|Wrap awaited code|
|Catch error|`catch (e)`|Handles exception|
|Catch with stack trace|`catch (e, stackTrace)`|For debugging|
|Specific exception|`on ExceptionType catch (e)`|Handle only specific errors|
|Finally|`finally { ... }`|Always executes|

---

## 6. Real-World Example

💡 **Fetching User Data with Error Handling**

```Dart
Future<String> fetchUser(String id) async {
  await Future.delayed(Duration(seconds: 1));
  if (id == "0") throw Exception("User not found");
  return "User data for $id";
}

void main() async {
  try {
    var user = await fetchUser("0");
    print(user);
  } catch (e) {
    print("Error: $e"); // Error: Exception: User not found
  } finally {
    print("Fetch attempt finished");
  }
}

```

✅ Demonstrates **handling errors gracefully** in async code.