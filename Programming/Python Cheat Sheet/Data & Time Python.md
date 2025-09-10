---
Created: 2025-08-21T19:29
tags:
  - Date-&-Time-(Basics)
---
## 1. Importing the `datetime` Module

```Python
import datetime
from datetime import datetime, date, time, timedelta
```

---

## 2. Getting Current Date & Time

```Python
from datetime import datetime

now = datetime.now()
print(now)            # 2025-07-26 12:34:56.789123

today = datetime.today()
print(today.date())   # 2025-07-26
```

- `datetime.now()` → current **date & time**
- `datetime.today()` → same as `now()` but no timezone support

---

## 3. Creating Specific Dates & Times

```Python
from datetime import datetime, date, time

# Specific date
d = date(2025, 7, 26)
print(d)  # 2025-07-26

# Specific datetime
dt = datetime(2025, 7, 26, 14, 30)
print(dt)  # 2025-07-26 14:30:00
```

---

## 4. Formatting Dates (strftime)

```Python
now = datetime.now()

print(now.strftime("%Y-%m-%d"))  # 2025-07-26
print(now.strftime("%A, %B %d, %Y"))  # Saturday, July 26, 2025
print(now.strftime("%I:%M %p"))  # 12:45 PM
```

✅ **Common Format Codes:**

|Code|Meaning|Example|
|---|---|---|
|`%Y`|Year (4 digits)|2025|
|`%m`|Month (01-12)|07|
|`%d`|Day (01-31)|26|
|`%H`|Hour (00-23)|14|
|`%I`|Hour (01-12)|02|
|`%M`|Minute|30|
|`%S`|Seconds|45|
|`%A`|Weekday name|Saturday|
|`%B`|Month name|July|
|`%p`|AM/PM|PM|

---

## 5. Parsing Strings → Datetime (strptime)

```Python
from datetime import datetime

dt = datetime.strptime("2025-07-26 14:30", "%Y-%m-%d %H:%M")
print(dt)  # 2025-07-26 14:30:00
```

---

## 6. Date Arithmetic with `timedelta`

```Python
from datetime import datetime, timedelta

today = datetime.now()
tomorrow = today + timedelta(days=1)
yesterday = today - timedelta(days=1)

print("Tomorrow:", tomorrow)
print("Yesterday:", yesterday)

# Adding hours/minutes
in_two_hours = today + timedelta(hours=2)
print("In 2 hours:", in_two_hours)
```

---

## 7. Getting Components

```Python
now = datetime.now()

print(now.year)    # 2025
print(now.month)   # 7
print(now.day)     # 26
print(now.hour)    # 14
print(now.minute)  # 30
print(now.second)  # 45
```

---

## 8. Working with `date` & `time` Separately

```Python
from datetime import date, time

d = date.today()
print(d)  # 2025-07-26

t = time(14, 30, 15)
print(t)  # 14:30:15
```

---

## Summary Table

|Function/Method|Purpose|Example|
|---|---|---|
|`datetime.now()`|Get current date & time|`2025-07-26 14:30:00`|
|`datetime()`|Create a specific datetime|`datetime(2025,7,26,14,30)`|
|`strftime()`|Format datetime → string|`%Y-%m-%d` → `2025-07-26`|
|`strptime()`|Parse string → datetime|`"2025-07-26"`|
|`timedelta(days=1)`|Add/subtract time durations|`now + timedelta(days=1)`|
|`date.today()`|Get today’s date|`2025-07-26`|
|`datetime.year`|Get components (year, month, etc.)|`now.year` → `2025`|

---

## Real-World Examples

### ✅ Countdown to a Deadline

```Python
from datetime import datetime

deadline = datetime(2025, 12, 31, 23, 59)
now = datetime.now()
remaining = deadline - now

print(f"Days left until New Year: {remaining.days}")
```

---

### ✅ Logging with Timestamps

```Python
from datetime import datetime

def log_message(msg):
    timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    print(f"[{timestamp}] {msg}")

log_message("Server started")
```

---

### ✅ Scheduling Future Events

```Python
from datetime import datetime, timedelta

now = datetime.now()
next_meeting = now + timedelta(weeks=2)
print("Next meeting:", next_meeting.strftime("%A, %B %d at %I:%M %p"))
```