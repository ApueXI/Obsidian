---
Created: 2025-09-16T20:17
tags:
  - Asynchronous-Programming
---
# 🎯 Dart `await for` Cheat Sheet

## 1. Full Explanation

- `**await for**` is used to **iterate over a Stream** inside an `async` function.
- Each event is **processed sequentially** as it arrives.
- Simpler and more readable than using `.listen()`, especially with **async/await**.
- Works with **single-subscription streams** and **broadcast streams**.

---

## 2. Basic Example

```Dart
Stream<int> numberStream() async* {
  for (int i = 1; i <= 5; i++) {
    await Future.delayed(Duration(seconds: 1));
    yield i; // emit value
  }
}

void main() async {
  await for (var number in numberStream()) {
    print("Received: $number");
  }
  print("Stream consumed!");
}

```

✅ Output (one per second):

```Plain
Received: 1
Received: 2
Received: 3
Received: 4
Received: 5
Stream consumed!

```

- `await for` waits for each value **before continuing**.
- Makes async stream consumption **sequential and readable**.

---

## 3. Error Handling with `await for`

```Dart
Stream<int> riskyStream() async* {
  yield 1;
  yield 2;
  throw Exception("Oops!");
}

void main() async {
  try {
    await for (var value in riskyStream()) {
      print("Value: $value");
    }
  } catch (e) {
    print("Caught error: $e");
  } finally {
    print("Finished consuming stream");
  }
}

```

✅ Output:

```Plain
Value: 1
Value: 2
Caught error: Exception: Oops!
Finished consuming stream

```

- Errors in the stream are **caught by try/catch**.
- `finally` executes after the stream finishes or errors.

---

## 4. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Iterate stream|`await for (var value in stream) { ... }`|Consumes each event sequentially|
|Error handling|Wrap `await for` in `try-catch`|Catch stream errors|
|Async stream source|`async*` + `yield`|Generates stream values asynchronously|
|Broadcast streams|`await for` works|Multiple listeners allowed|

---

## 5. Real-World Example

💡 **Simulated Chat Messages Stream**

```Dart
Stream<String> chatMessages() async* {
  var messages = ["Hello!", "How are you?", "See you later"];
  for (var msg in messages) {
    await Future.delayed(Duration(seconds: 1));
    yield msg;
  }
}

void main() async {
  await for (var message in chatMessages()) {
    print("New message: $message");
  }
  print("No more messages.");
}

```

✅ Output:

```Plain
New message: Hello!
New message: How are you?
New message: See you later
No more messages.

```

- Demonstrates **sequential asynchronous stream consumption**.