---
Created: 2025-09-16T20:15
tags:
  - Asynchronous-Programming
---
# 🎯 Dart `async` & `await` Cheat Sheet

## 1. Full Explanation

- `**async**`
    - Marks a function as **asynchronous**.
    - Allows the use of `**await**` inside the function.
    - Returns a **Future** automatically.
- `**await**`
    - Pauses execution of the **async function** until the awaited **Future completes**.
    - Makes asynchronous code easier to read than chaining `.then()`.

---

## 2. Basic Example

```Dart
Future<String> fetchData() async {
  await Future.delayed(Duration(seconds: 2)); // simulate async task
  return "Data received";
}

void main() async {
  print("Fetching data...");
  var data = await fetchData();
  print(data); // Data received
}

```

✅ Execution waits at `await fetchData()` until the Future completes.

---

## 3. Error Handling with `async` / `await`

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

✅ Use `try/catch` inside **async functions** for safe error handling.

---

## 4. Multiple `await`s Sequentially

```Dart
Future<String> step1() async => "Step 1 done";
Future<String> step2() async => "Step 2 done";

void main() async {
  var result1 = await step1();
  print(result1); // Step 1 done
  var result2 = await step2();
  print(result2); // Step 2 done
}

```

✅ Sequential execution — each `await` waits for the previous Future to complete.

---

## 5. Multiple `await`s Concurrently

```Dart
Future<String> step1() async => "Step 1 done";
Future<String> step2() async => "Step 2 done";

void main() async {
  var futures = [step1(), step2()];
  var results = await Future.wait(futures);
  print(results); // [Step 1 done, Step 2 done]
}

```

✅ `Future.wait()` runs multiple Futures **concurrently**.

---

## 6. Summary Table

|Keyword|Usage|Notes|
|---|---|---|
|async|`Future<Type> function() async { ... }`|Marks function as asynchronous|
|await|`var result = await futureFunction();`|Waits for Future to complete|
|Error handling|`try { await ... } catch (e) { ... }`|Catch exceptions safely|
|Sequential execution|`await step1(); await step2();`|Waits step by step|
|Concurrent execution|`await Future.wait([f1, f2])`|Run multiple Futures at the same time|

---

## 7. Real-World Example

💡 **Fetching API Data Sequentially**

```Dart
Future<String> fetchUser(String id) async {
  await Future.delayed(Duration(seconds: 1));
  return "User $id data";
}

Future<String> fetchOrders(String id) async {
  await Future.delayed(Duration(seconds: 1));
  return "Orders for user $id";
}

void main() async {
  var user = await fetchUser("123");
  print(user); // User 123 data

  var orders = await fetchOrders("123");
  print(orders); // Orders for user 123
}

```

✅ Makes **asynchronous tasks readable** and **maintains logical order**.