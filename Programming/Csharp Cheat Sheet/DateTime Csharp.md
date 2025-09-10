---
Created: 2025-08-07T20:10
tags:
  - Date-&-Time
---
## ✅ What is `DateTime`?

`DateTime` is a **value type** in C# used to work with dates and times (date, time, or both).

Namespace:

```C#
using System;
```

---

## 🧱 Creating a `DateTime` Instance

```C#
DateTime now = DateTime.Now;                // Local time
DateTime utc = DateTime.UtcNow;            // UTC time
DateTime today = DateTime.Today;           // Date only, time = 00:00:00
DateTime custom = new DateTime(2025, 8, 3); // Specific date
```

You can also specify time:

```C#
DateTime dt = new DateTime(2025, 8, 3, 15, 30, 0); // 3:30 PM
```

---

## 🧾 Common Properties

|Property|Description|
|---|---|
|`dt.Year`|Gets the year|
|`dt.Month`|Gets the month (1–12)|
|`dt.Day`|Gets the day (1–31)|
|`dt.Hour`|Gets the hour (0–23)|
|`dt.Minute`|Gets the minute (0–59)|
|`dt.Second`|Gets the second (0–59)|
|`dt.DayOfWeek`|Enum (e.g., Sunday)|
|`dt.DayOfYear`|Day of the year (1–366)|
|`dt.TimeOfDay`|Gets only the time|
|`dt.Kind`|`Local`, `Utc`, or `Unspecified`|

---

## 🧮 Operations

```C#
DateTime tomorrow = DateTime.Now.AddDays(1);
DateTime nextHour = DateTime.Now.AddHours(1);
DateTime lastWeek = DateTime.Now.AddDays(-7);

// Difference
TimeSpan diff = DateTime.Now - DateTime.Today;
Console.WriteLine(diff.TotalHours); // Hours between now and today at midnight
```

---

## 🧪 Comparisons

```C#
if (date1 > date2) { /* later */ }
if (date1 == date2) { /* same */ }

bool isBefore = date1.CompareTo(date2) < 0;
```

---

## ⌛ Formatting

```C#
string formatted = DateTime.Now.ToString("yyyy-MM-dd HH:mm:ss");
Console.WriteLine(formatted); // Example: 2025-08-03 14:55:00
```

### Common Format Strings

|Format|Output example|
|---|---|
|`"d"`|8/3/2025|
|`"D"`|Sunday, August 3, 2025|
|`"t"`|2:55 PM|
|`"T"`|2:55:00 PM|
|`"g"`|8/3/2025 2:55 PM|
|`"G"`|8/3/2025 2:55:00 PM|
|`"yyyy-MM-dd"`|2025-08-03|
|`"HH:mm:ss"`|14:55:00 (24-hour)|

---

## 🌐 Parsing & TryParse

```C#
DateTime date1 = DateTime.Parse("2025-08-03");
bool success = DateTime.TryParse("03-Aug-2025", out DateTime result);
```

---

## 📋 Summary Table

|Task|Syntax Example|
|---|---|
|Current time|`DateTime.Now`|
|Add days|`dt.AddDays(1)`|
|Compare dates|`dt1 > dt2` or `dt1.CompareTo(dt2)`|
|Format as string|`dt.ToString("yyyy-MM-dd")`|
|Parse string|`DateTime.Parse("2025-08-03")`|
|Time difference|`TimeSpan t = dt1 - dt2`|
|Only date|`DateTime.Today`|

---

## 🧰 Real-World Example

```C#
DateTime birthDate = new DateTime(1995, 8, 3);
DateTime today = DateTime.Today;

int age = today.Year - birthDate.Year;
if (birthDate > today.AddYears(-age)) age--;  // Adjust if birthday hasn't occurred yet

Console.WriteLine($"You are {age} years old.");
```