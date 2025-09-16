---
Created: 2025-09-16T20:14
tags:
  - Asynchronous-Programming
---
# 🎯 Dart Futures Cheat Sheet

## 1. Full Explanation

- **Future** represents a **value that will be available later**, typically as the result of an asynchronous operation.
- Useful for **I/O, HTTP requests, database queries, or timers**.
- Dart provides `**async**` **/** `**await**` syntax for easier handling of Futures.
- **States of a Future**:
    - **Uncompleted** → still running
    - **Completed with value** → success
    - **Completed with error** → failure

---

## 2. Basic Future Example

```Dart
Future<String> fetchData() {
  return Future.delayed(Duration(seconds: 2), () => "Data received");
}

void main() {
  fetchData().then((data) {
    print(data); // Data received (after 2 seconds)
  });
}

```

✅ `then()` handles the result when the Future completes successfully.

---

## 3. Using `async` / `await`

```Dart
Future<String> fetchData() async {
  await Future.delayed(Duration(seconds: 2));
  return "Data received";
}

void main() async {
  print("Fetching data...");
  var data = await fetchData();
  print(data); // Data received
}

```

✅ `await` pauses execution until the Future **completes**.

✅ Function using `await` must be marked `async`.

---

## 4. Handling Errors with Futures

```Dart
Future<int> riskyOperation() async {
  await Future.delayed(Duration(seconds: 1));
  throw Exception("Something went wrong");
}

void main() async {
  try {
    var result = await riskyOperation();
    print(result);
  } catch (e) {
    print("Caught error: $e"); // Caught error: Exception: Something went wrong
  }
}

```

✅ Use `try/catch` with `await` to handle errors.

---

## 5. Chaining Futures

```Dart
Future<int> multiplyByTwo(int x) async {
  return x * 2;
}

void main() {
  multiplyByTwo(5).then((value) => print("Result: $value")); // Result: 10
}

```

✅ Futures can be chained with `then()` for sequential asynchronous tasks.

---

## 6. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Create Future|`Future<Type> function() { ... }`|Returns a value later|
|Delay example|`Future.delayed(Duration(seconds: 2), () => value)`|Simulates async task|
|Await Future|`var result = await futureFunction();`|Must be in `async` function|
|Handle error|`try { await ... } catch (e) { ... }`|Safe error handling|
|Chain|`future.then((value) => ...)`|Sequential tasks without `await`|

---

## 7. Real-World Example

💡 **Fetching Data from API**

```Dart
Future<String> fetchUserData(String userId) async {
  await Future.delayed(Duration(seconds: 2)); // simulate network delay
  if (userId == "0") throw Exception("User not found");
  return "User data for $userId";
}

void main() async {
  try {
    var data = await fetchUserData("123");
    print(data); // User data for 123
  } catch (e) {
    print("Error: $e");
  }
}

```

✅ Demonstrates **async tasks**, **await**, and **error handling**.