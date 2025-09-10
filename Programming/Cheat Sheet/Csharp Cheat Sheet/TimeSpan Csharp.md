---
Created: 2025-08-07T20:10
tags:
  - Date-&-Time
---
## ✅ What is `TimeSpan`?

`TimeSpan` represents a **duration** (interval of time), not a specific date or clock time.

Used for measuring time differences or defining time intervals (e.g., 2 hours, 15 minutes).

---

## 🧱 Creating a `TimeSpan`

```C#
TimeSpan span1 = new TimeSpan(1, 30, 0);       // 1 hour, 30 minutes
TimeSpan span2 = TimeSpan.FromHours(2.5);      // 2 hours, 30 minutes
TimeSpan span3 = TimeSpan.FromMinutes(90);     // 1.5 hours
TimeSpan span4 = TimeSpan.FromDays(1);         // 1 day
TimeSpan span5 = TimeSpan.FromMilliseconds(500); // Half a second
```

---

## 🧾 Common Properties

|Property|Description|
|---|---|
|`span.Days`|Number of whole days|
|`span.Hours`|Remaining hours (not total)|
|`span.Minutes`|Remaining minutes|
|`span.Seconds`|Remaining seconds|
|`span.Milliseconds`|Remaining milliseconds|
|`span.TotalDays`|Duration as fractional days|
|`span.TotalHours`|Duration as fractional hours|
|`span.TotalMinutes`|Duration as fractional minutes|
|`span.TotalSeconds`|Duration as fractional seconds|

Example:

```C#
TimeSpan ts = new TimeSpan(1, 2, 30); // 1 hour, 2 min, 30 sec
Console.WriteLine(ts.TotalMinutes);  // 62.5
```

---

## 🔁 Operations

### Arithmetic:

```C#
TimeSpan ts1 = TimeSpan.FromHours(1);
TimeSpan ts2 = TimeSpan.FromMinutes(30);

TimeSpan sum = ts1 + ts2;      // 1.5 hours
TimeSpan diff = ts1 - ts2;     // 30 minutes
TimeSpan doubled = ts1 * 2;    // 2 hours (C# 8+)
TimeSpan halved = ts1 / 2;     // 30 minutes
```

### Negation & Comparison:

```C#
TimeSpan neg = -ts1;
bool isLonger = ts1 > ts2;
```

---

## ⌛ Getting Duration Between Dates

```C#
DateTime start = new DateTime(2025, 8, 3, 10, 0, 0);
DateTime end = new DateTime(2025, 8, 3, 12, 15, 0);

TimeSpan duration = end - start;   // 2:15:00
Console.WriteLine(duration.TotalMinutes); // 135
```

---

## 🖨️ Formatting `TimeSpan`

```C#
TimeSpan ts = new TimeSpan(2, 5, 30); // 2 hours, 5 min, 30 sec

Console.WriteLine(ts.ToString());         // "02:05:30"
Console.WriteLine(ts.ToString(@"hh\:mm")); // "02:05"
Console.WriteLine(ts.ToString(@"dd\.hh\:mm\:ss")); // "00.02:05:30"
```

---

## 📋 Summary Table

|Task|Example|
|---|---|
|Create 2-hour span|`TimeSpan.FromHours(2)`|
|Add spans|`ts1 + ts2`|
|Subtract spans|`ts1 - ts2`|
|Compare spans|`ts1 > ts2`|
|Total hours|`ts.TotalHours`|
|Time between dates|`end - start`|
|Format (HH:mm:ss)|`ts.ToString(@"hh\:mm\:ss")`|

---

## 🧰 Real-World Example

```C#
DateTime start = DateTime.Now;
DateTime end = start.AddMinutes(90); // Simulated end time

TimeSpan duration = end - start;

Console.WriteLine($"Elapsed: {duration.TotalMinutes} minutes");
Console.WriteLine($"Formatted: {duration.ToString(@"hh\:mm")}");
```