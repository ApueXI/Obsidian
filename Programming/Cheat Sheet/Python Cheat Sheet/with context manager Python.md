---
Created: 2025-08-21T19:29
tags:
  - File-I/O
---
## 1. What is a Context Manager?

- A **context manager** automatically **sets up and tears down resources**.
- The `with` statement ensures **proper cleanup** (even if an error occurs).
- Commonly used for **file handling**, **database connections**, **locks**, etc.

✅ **Main benefit: No need to manually call** `**close()**`

---

## 2. Syntax

```Python
with context_manager as var:
    # code using var
# resource is automatically released here
```

---

## 3. Using `with` for File Handling

### ✅ Without `with` (NOT recommended)

```Python
f = open("file.txt", "r")
data = f.read()
f.close()  # must be called manually
```

### ✅ With `with` (BEST practice)

```Python
with open("file.txt", "r") as f:
    data = f.read()
# file automatically closed here
```

---

## 4. Multiple Context Managers

You can open **multiple files at once**:

```Python
with open("input.txt", "r") as src, open("output.txt", "w") as dst:
    dst.write(src.read())
```

---

## 5. Why Use `with`?

✅ Auto-closes the file

✅ Even if an exception occurs, the file still closes

✅ Cleaner and safer

---

## 6. Context Manager with `time` Example

```Python
from time import perf_counter

class Timer:
    def __enter__(self):
        self.start = perf_counter()
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        self.end = perf_counter()
        print(f"Elapsed: {self.end - self.start:.4f} sec")

# Usage
with Timer():
    sum(range(10_000_000))  # heavy task
```

---

## 7. Custom Context Manager

You can create your own using a **class** with `__enter__()` and `__exit__()`:

```Python
class MyContext:
    def __enter__(self):
        print("Entering context")
        return "resource"

    def __exit__(self, exc_type, exc_val, exc_tb):
        print("Exiting context")

with MyContext() as res:
    print("Inside:", res)
```

---

## 8. Alternative: `contextlib`

For simple cases, use `contextlib.contextmanager` decorator:

```Python
from contextlib import contextmanager

@contextmanager
def my_context():
    print("Setup")
    yield "resource"
    print("Teardown")

with my_context() as res:
    print("Using", res)
```

---

## Summary Table

|Feature|What it does|Example|
|---|---|---|
|`with open()`|Opens & auto-closes files|`with open("x.txt") as f:`|
|Multiple managers|Open multiple resources|`with open(a) as f1, open(b) as f2:`|
|Custom context|Use `__enter__` & `__exit__`|`class MyContext: ...`|
|`contextlib` helper|Easier custom managers|`@contextmanager`|

---

## Real-World Examples

---

### ✅ Reading & Writing Safely

```Python
with open("data.txt", "r") as f:
    content = f.read()

with open("log.txt", "a") as log:
    log.write("File was read successfully\n")
```

---

### ✅ Copying a File

```Python
with open("source.txt", "r") as src, open("backup.txt", "w") as dst:
    dst.write(src.read())
```

---

### ✅ Benchmarking Code Execution

```Python
from time import perf_counter

class Timer:
    def __enter__(self):
        self.start = perf_counter()
        return self
    def __exit__(self, *args):
        print(f"Execution time: {perf_counter() - self.start:.3f}s")

with Timer():
    sum(range(10_000_000))
```

---

### ✅ Temporary Database Connection

```Python
class DBConnection:
    def __enter__(self):
        print("Connecting to DB")
        return self
    def __exit__(self, exc_type, exc_val, exc_tb):
        print("Closing DB")

with DBConnection() as db:
    print("Querying data...")
```

---

## TL;DR

- `with` ensures **automatic cleanup** → **always use it for files**.
- Works with any object that defines `__enter__` & `__exit__`.
- Can be nested or combined in one line.