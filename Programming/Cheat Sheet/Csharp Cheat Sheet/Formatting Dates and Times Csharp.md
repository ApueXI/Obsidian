---
Created: 2025-08-07T20:10
tags:
  - Date-&-Time
---
## ✅ Overview

- Use `.ToString()` with **format strings** to customize how `DateTime` or `TimeSpan` is displayed.
- You can use **standard format specifiers** or **custom format strings**.

```C#
DateTime now = DateTime.Now;
Console.WriteLine(now.ToString("yyyy-MM-dd HH:mm:ss"));
```

---

## 🔤 Standard Format Strings (`ToString("X")`)

|Format|Description|Example (`8/3/2025 14:05:30`)|
|---|---|---|
|`d`|Short date|`8/3/2025`|
|`D`|Long date|`Sunday, August 3, 2025`|
|`t`|Short time|`2:05 PM`|
|`T`|Long time|`2:05:30 PM`|
|`f`|Full date + short time|`Sunday, August 3, 2025 2:05 PM`|
|`F`|Full date + long time|`Sunday, August 3, 2025 2:05:30 PM`|
|`g`|General date/time (short)|`8/3/2025 2:05 PM`|
|`G`|General date/time (long)|`8/3/2025 2:05:30 PM`|
|`M`/`m`|Month and day|`August 3`|
|`Y`/`y`|Year and month|`August 2025`|
|`O`/`o`|Round-trip format (ISO 8601)|`2025-08-03T14:05:30.0000000`|
|`R`/`r`|RFC1123 pattern (GMT)|`Sun, 03 Aug 2025 14:05:30 GMT`|
|`s`|Sortable (ISO 8601)|`2025-08-03T14:05:30`|
|`u`|Universal sortable (UTC)|`2025-08-03 14:05:30Z`|

---

## 🔧 Custom Format Strings

|Format|Meaning|Example|
|---|---|---|
|`yyyy`|4-digit year|`2025`|
|`yy`|2-digit year|`25`|
|`MMMM`|Full month name|`August`|
|`MMM`|Abbreviated month name|`Aug`|
|`MM`|Month (01–12)|`08`|
|`M`|Month (1–12)|`8`|
|`dd`|Day (01–31)|`03`|
|`d`|Day (1–31)|`3`|
|`dddd`|Full day of week|`Sunday`|
|`ddd`|Abbreviated day of week|`Sun`|
|`HH`|Hour (00–23)|`14`|
|`H`|Hour (0–23)|`14`|
|`hh`|Hour (01–12)|`02`|
|`h`|Hour (1–12)|`2`|
|`mm`|Minute (00–59)|`05`|
|`ss`|Second (00–59)|`30`|
|`tt`|AM/PM|`PM`|
|`fff`|Milliseconds (000–999)|`123`|

### Example Usage

```C#
DateTime now = DateTime.Now;
Console.WriteLine(now.ToString("dddd, MMMM dd yyyy"));   // Sunday, August 03 2025
Console.WriteLine(now.ToString("yyyy-MM-dd HH:mm:ss"));  // 2025-08-03 14:05:30
Console.WriteLine(now.ToString("hh:mm tt"));             // 02:05 PM
```

---

## 🧱 Format `TimeSpan`

```C#
TimeSpan ts = new TimeSpan(1, 2, 30); // 1 hr, 2 min, 30 sec
Console.WriteLine(ts.ToString());               // 01:02:30
Console.WriteLine(ts.ToString(@"hh\:mm\:ss"));  // 01:02:30
Console.WriteLine(ts.ToString(@"dd\.hh\:mm"));  // 00.01:02
```

> Use backslashes \ to escape colons and dots in TimeSpan formatting.

---

## 🧪 Real-World Example

```C#
DateTime meeting = new DateTime(2025, 8, 3, 9, 30, 0);
string formatted = meeting.ToString("dddd, MMM dd yyyy 'at' hh:mm tt");
Console.WriteLine(formatted); // Sunday, Aug 03 2025 at 09:30 AM
```

---

## 📋 Summary Table

|Task|Example Code|Output (Aug 3, 2025, 14:05:30)|
|---|---|---|
|Short date|`now.ToString("d")`|`8/3/2025`|
|ISO format|`now.ToString("yyyy-MM-dd")`|`2025-08-03`|
|Full date with time|`now.ToString("F")`|`Sunday, August 3, 2025 2:05:30 PM`|
|Custom with AM/PM|`now.ToString("hh:mm tt")`|`02:05 PM`|
|Milliseconds|`now.ToString("HH:mm:ss.fff")`|`14:05:30.000`|