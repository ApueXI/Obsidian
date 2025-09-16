---
Created: 2025-09-16T20:28
tags:
  - Dart-Core-Library-(no-external-imports)
---
# 🎯 Dart `dart:core` (DateTime & Duration) Cheat Sheet

## 1. Full Explanation

- `**dart:core**` is **automatically imported** in every Dart program.
- Provides **core functionality**: numbers, strings, collections, dates, exceptions, etc.
- Two key classes for time handling:
    1. **DateTime** → represents a **point in time**
    2. **Duration** → represents a **time span / difference**

---

## 2. DateTime

### **Creating DateTime Objects**

```Dart
void main() {
  var now = DateTime.now();               // current date and time
  var specific = DateTime(2025, 9, 16);   // year, month, day
  var withTime = DateTime(2025, 9, 16, 18, 30); // year, month, day, hour, min
  var fromMillis = DateTime.fromMillisecondsSinceEpoch(1000000000);

  print(now);
  print(specific);
  print(withTime);
  print(fromMillis);
}

```

---

### **DateTime Properties**

|Property|Description|
|---|---|
|`.year`|Year component|
|`.month`|Month (1–12)|
|`.day`|Day of the month|
|`.hour`|Hour (0–23)|
|`.minute`|Minute (0–59)|
|`.second`|Second (0–59)|
|`.millisecond`|Millisecond (0–999)|
|`.weekday`|Day of the week (1 = Monday)|

---

### **DateTime Methods**

```Dart
void main() {
  var now = DateTime.now();

  var tomorrow = now.add(Duration(days: 1));        // add time
  var yesterday = now.subtract(Duration(days: 1));  // subtract time

  print(now.isBefore(tomorrow));  // true
  print(now.isAfter(yesterday));  // true
  print(now.difference(yesterday)); // Duration object
}

```

---

## 3. Duration

- Represents a **time span**, useful for adding/subtracting from DateTime or timers.

### **Creating Duration**

```Dart
void main() {
  var dur1 = Duration(days: 2, hours: 3, minutes: 30);
  var dur2 = Duration(seconds: 90);

  print(dur1); // 2:03:30.000000
  print(dur2); // 0:01:30.000000
}

```

### **Using Duration with DateTime**

```Dart
void main() {
  var now = DateTime.now();
  var future = now.add(Duration(days: 7)); // 7 days later
  var past = now.subtract(Duration(hours: 5)); // 5 hours ago

  print(future);
  print(past);
}

```

### **Duration Properties**

|Property|Description|
|---|---|
|`.inDays`|Total number of days|
|`.inHours`|Total hours|
|`.inMinutes`|Total minutes|
|`.inSeconds`|Total seconds|
|`.inMilliseconds`|Total milliseconds|
|`.inMicroseconds`|Total microseconds|

---

## 4. Summary Table

|Class|Purpose|Key Methods / Properties|
|---|---|---|
|`DateTime`|Represents a point in time|`.now()`, `.add()`, `.subtract()`, `.difference()`, `.year`, `.month`, `.day`|
|`Duration`|Represents a time span|`.inDays`, `.inHours`, `.inMinutes`, `.inSeconds`, `.inMilliseconds`, `.inMicroseconds`|

---

## 5. Real-World Example

💡 **Countdown Timer**

```Dart
void main() {
  var now = DateTime.now();
  var event = DateTime(2025, 12, 31);
  var remaining = event.difference(now);

  print("Days until event: ${remaining.inDays}");
  print("Hours until event: ${remaining.inHours}");
}

```

✅ Easily calculate **time differences** or schedule events.