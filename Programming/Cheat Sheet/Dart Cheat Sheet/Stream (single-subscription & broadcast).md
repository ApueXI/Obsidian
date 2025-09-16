---
Created: 2025-09-16T20:17
tags:
  - Asynchronous-Programming
---
# 🎯 Dart Streams Cheat Sheet

## 1. Full Explanation

- **Stream** = sequence of asynchronous events (data, errors, done) over time.
- Useful for:
    - User input events
    - WebSocket or HTTP event streams
    - Sensor data, timers
- **Types of Streams**:
    1. **Single-subscription Stream**
        - Only **one listener** allowed.
        - Events are delivered **in order**.
    2. **Broadcast Stream**
        - **Multiple listeners** allowed.
        - Useful for events that need to be observed by many subscribers.

---

## 2. Single-Subscription Stream

```Dart
void main() {
  Stream<int> singleStream = Stream.fromIterable([1, 2, 3]);

  singleStream.listen(
    (event) => print("Received: $event"),
    onDone: () => print("Done"),
  );
}

```

✅ Output:

```Plain
Received: 1
Received: 2
Received: 3
Done

```

- Only **one listener** is allowed.
- Throws an error if you add a second listener.

---

## 3. Broadcast Stream

```Dart
void main() {
  Stream<int> broadcastStream = Stream.fromIterable([10, 20, 30]).asBroadcastStream();

  broadcastStream.listen((event) => print("Listener 1: $event"));
  broadcastStream.listen((event) => print("Listener 2: $event"));
}

```

✅ Output:

```Plain
Listener 1: 10
Listener 2: 10
Listener 1: 20
Listener 2: 20
Listener 1: 30
Listener 2: 30

```

- Multiple listeners **receive the same events**.
- Ideal for **UI events or notifications**.

---

## 4. Adding Error & Done Handlers

```Dart
void main() {
  Stream<int> stream = Stream.fromIterable([1, 2, 0, 3]).asyncMap((value) async {
    if (value == 0) throw Exception("Zero not allowed");
    return value;
  });

  stream.listen(
    (data) => print("Data: $data"),
    onError: (err) => print("Error: $err"),
    onDone: () => print("Stream finished"),
  );
}

```

✅ Output:

```Plain
Data: 1
Data: 2
Error: Exception: Zero not allowed
Data: 3
Stream finished

```

- `onError` handles asynchronous errors gracefully.

---

## 5. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Single-subscription|`Stream.fromIterable([...])`|Only one listener|
|Broadcast|`stream.asBroadcastStream()`|Multiple listeners allowed|
|Listen to events|`stream.listen((data) {}, onError: (e){}, onDone: (){})`|Handles events, errors, completion|
|Async map|`stream.asyncMap((data) => Future)`|Transform asynchronously|

---

## 6. Real-World Example

💡 **Timer Event Stream**

```Dart
import 'dart:async';

void main() {
  Stream<int> timerStream = Stream.periodic(Duration(seconds: 1), (count) => count).take(5);

  timerStream.listen(
    (event) => print("Tick: $event"),
    onDone: () => print("Timer finished"),
  );
}

```

✅ Output:

```Plain
Tick: 0
Tick: 1
Tick: 2
Tick: 3
Tick: 4
Timer finished

```

- Generates **repeated asynchronous events** (like a timer).