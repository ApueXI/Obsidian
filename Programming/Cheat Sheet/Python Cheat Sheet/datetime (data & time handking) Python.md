---
Created: 2025-08-21T19:29
tags:
  - Date-&-Time-(Basics)
---
## 1. Importing

```Python
import datetime
from datetime import datetime, date, time, timedelta
```

---

## 2. Getting Current Date & Time

```Python
from datetime import datetime

now = datetime.now()
print(now)             # 2025-07-26 14:45:30.123456

today = date.today()
print(today)           # 2025-07-26
```

✅ `datetime.now()` → current **date & time**

✅ `date.today()` → just **date**

---

## 3. Creating Specific Dates & Times

```Python
from datetime import datetime, date, time

# Specific date
d = date(2025, 7, 26)
print(d)   # 2025-07-26

# Specific datetime
dt = datetime(2025, 7, 26, 14, 30, 15)
print(dt)  # 2025-07-26 14:30:15

# Specific time
t = time(14, 30, 15)
print(t)   # 14:30:15
```

---

## 4. Formatting Dates → Strings (`strftime`)

```Python
now = datetime.now()

print(now.strftime("%Y-%m-%d"))        # 2025-07-26
print(now.strftime("%A, %B %d, %Y"))   # Saturday, July 26, 2025
print(now.strftime("%I:%M %p"))        # 02:45 PM
```

✅ **Common Format Codes:**

|Code|Meaning|Example|
|---|---|---|
|`%Y`|Year (4 digits)|2025|
|`%m`|Month (01-12)|07|
|`%d`|Day (01-31)|26|
|`%H`|Hour (00-23)|14|
|`%I`|Hour (01-12)|02|
|`%M`|Minute|45|
|`%S`|Seconds|30|
|`%A`|Weekday name|Saturday|
|`%B`|Month name|July|
|`%p`|AM/PM|PM|

---

## 5. Parsing Strings → Datetime (`strptime`)

```Python
from datetime import datetime

dt = datetime.strptime("2025-07-26 14:30", "%Y-%m-%d %H:%M")
print(dt)  # 2025-07-26 14:30:00
```

---

## 6. Date Arithmetic (`timedelta`)

```Python
from datetime import datetime, timedelta

now = datetime.now()
tomorrow = now + timedelta(days=1)
yesterday = now - timedelta(days=1)

print("Tomorrow:", tomorrow)
print("Yesterday:", yesterday)

# Adding hours/minutes
in_two_hours = now + timedelta(hours=2)
print("In 2 hours:", in_two_hours)
```

---

## 7. Extracting Components

```Python
now = datetime.now()

print(now.year)    # 2025
print(now.month)   # 7
print(now.day)     # 26
print(now.hour)    # 14
print(now.minute)  # 45
print(now.second)  # 30
print(now.weekday())  # 5 (Monday=0, Sunday=6)
```

---

## 8. Converting Between Timestamp & Datetime

```Python
import time
from datetime import datetime

# Timestamp → datetime
ts = time.time()
dt = datetime.fromtimestamp(ts)
print(dt)  # 2025-07-26 14:50:12

# Datetime → timestamp
now = datetime.now()
print(now.timestamp())  # e.g., 1753524612.123456
```

---

## 9. Timezones (`timezone`, `zoneinfo`)

```Python
from datetime import datetime, timezone, timedelta

# UTC
utc_now = datetime.now(timezone.utc)
print("UTC time:", utc_now)

# Custom timezone (UTC+8)
ph_time = utc_now.astimezone(timezone(timedelta(hours=8)))
print("Philippines:", ph_time)
```

✅ For more advanced zones: `from zoneinfo import ZoneInfo`

---

## Summary Table

|Function/Method|Purpose|Example|
|---|---|---|
|`datetime.now()`|Get current date & time|`2025-07-26 14:45:30`|
|`date.today()`|Get today’s date|`2025-07-26`|
|`datetime()`|Create a specific datetime|`datetime(2025,7,26,14,30)`|
|`strftime()`|Format datetime → string|`%Y-%m-%d`|
|`strptime()`|Parse string → datetime|`"2025-07-26 14:30"`|
|`timedelta()`|Add/subtract time durations|`+ timedelta(days=1)`|
|`fromtimestamp()`|Convert timestamp → datetime|`datetime.fromtimestamp(1234567890)`|
|`timestamp()`|Convert datetime → timestamp|`dt.timestamp()`|
|`timezone()` / `ZoneInfo()`|Handle timezones|`astimezone(ZoneInfo("Asia/Manila"))`|

---

## Real-World Examples

---

### ✅ Countdown to a Deadline

```Python
from datetime import datetime

deadline = datetime(2025, 12, 31, 23, 59)
now = datetime.now()
remaining = deadline - now

print(f"Days left until New Year: {remaining.days}")
```

---

### ✅ Log with Formatted Timestamp

```Python
from datetime import datetime

def log(msg):
    print(f"[{datetime.now().strftime('%Y-%m-%d %H:%M:%S')}] {msg}")

log("Server started")
```

---

### ✅ Schedule Future Events

```Python
from datetime import datetime, timedelta

meeting = datetime.now() + timedelta(weeks=2)
print("Next meeting:", meeting.strftime("%A, %B %d at %I:%M %p"))
```

---

### ✅ Convert Between Timezones

```Python
from datetime import datetime, timezone, timedelta

utc_time = datetime.now(timezone.utc)
manila_time = utc_time.astimezone(timezone(timedelta(hours=8)))
print("UTC:", utc_time)
print("Manila:", manila_time)
```

---

## `datetime` vs `time` Module

|`time` Module|`datetime` Module|
|---|---|
|Works mostly with **timestamps (float seconds)**|Works with full **datetime objects**|
|Good for **sleep, performance timing**|Good for **date math, formatting, parsing**|
|Less human-readable|More structured & readable|