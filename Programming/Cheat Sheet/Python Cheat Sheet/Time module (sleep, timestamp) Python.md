---
Created: 2025-08-21T19:29
tags:
  - Date-&-Time-(Basics)
---
## 1. Importing

```Python
import time
```

---

## 2. `time.time()` → Get Current Timestamp

- Returns the **current time in seconds** since the **Unix Epoch (Jan 1, 1970)**.

```Python
import time

timestamp = time.time()
print(timestamp)
# e.g. 1753523456.123456  (seconds with decimals)
```

You can convert it to a readable format later.

---

## 3. `time.sleep(seconds)` → Pause Execution

- **Delays program execution** for a given number of seconds.

```Python
print("Start")
time.sleep(2)    # wait 2 seconds
print("End after delay")
```

✅ You can use **fractions** (e.g., `0.5` for half a second).

---

## 4. `time.ctime([secs])` → Human-readable Time

- Converts a timestamp into a **readable string**.

```Python
print(time.ctime())           # Current time → 'Sat Jul 26 14:35:00 2025'
print(time.ctime(0))          # Epoch → 'Thu Jan  1 00:00:00 1970'
```

---

## 5. `time.localtime([secs])` & `time.gmtime([secs])`

- Converts a timestamp into a **struct_time** (like a named tuple).

```Python
t = time.localtime()
print(t.tm_year, t.tm_mon, t.tm_mday)
# 2025 7 26

utc_t = time.gmtime()  # UTC time
```

---

## 6. `time.strftime(format, struct_time)`

- Formats a `struct_time` → string

```Python
print(time.strftime("%Y-%m-%d %H:%M:%S", time.localtime()))
# '2025-07-26 14:35:00'
```

✅ Format codes same as `datetime.strftime()`

---

## 7. `time.perf_counter()` → High-Resolution Timer

- Measures **elapsed time** for performance benchmarking.

```Python
start = time.perf_counter()
time.sleep(1.5)
end = time.perf_counter()
print("Elapsed:", end - start)  # ~1.5 seconds
```

---

## Summary Table

|Function|Purpose|Example|
|---|---|---|
|`time.time()`|Get current timestamp (seconds)|`1753523456.12`|
|`time.sleep(sec)`|Pause execution|`time.sleep(2)`|
|`time.ctime()`|Convert timestamp → readable string|`'Sat Jul 26 14:35:00 2025'`|
|`time.localtime()`|Convert timestamp → `struct_time`|`tm_year=2025, tm_mon=7, ...`|
|`time.strftime()`|Format time into custom string|`%Y-%m-%d %H:%M:%S`|
|`time.perf_counter()`|High-resolution elapsed time|Benchmarking|

---

## Real-World Examples

---

### ✅ Countdown Timer

```Python
import time

for i in range(5, 0, -1):
    print(i)
    time.sleep(1)
print("Time’s up!")
```

---

### ✅ Measure Execution Time

```Python
import time

start = time.perf_counter()
# some heavy computation
time.sleep(2.3)
end = time.perf_counter()

print(f"Execution took {end - start:.2f} seconds")
```

---

### ✅ Show Human-Readable Timestamp

```Python
import time

timestamp = time.time()
print("Raw timestamp:", timestamp)
print("Readable:", time.ctime(timestamp))
```

---

### ✅ Log Current Time Every 2 Seconds

```Python
import time

for _ in range(3):
    print(time.strftime("%Y-%m-%d %H:%M:%S", time.localtime()))
    time.sleep(2)
```

---

## Key Points

- `time.sleep()` → delay execution.
- `time.time()` → Unix timestamp in seconds.
- `time.ctime()` → quick human-readable format.
- `time.strftime()` → custom formatting.
- `time.perf_counter()` → accurate elapsed time measurement.