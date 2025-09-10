---
Created: 2025-08-21T19:29
tags:
  - Advance-Topics
---
## ✅ **What are Context Managers?**

Context managers help you **manage resources safely and cleanly**, by automatically setting up and tearing down resources using the `with` statement.

Common examples: file handling, locks, database connections.

---

## 🏗 **Key Concepts**

- `**with**` **statement** ensures resources are properly **acquired and released**.
- Classes that implement `**__enter__()**` and `**__exit__()**` methods define context managers.

---

## 🔹 **How it works**

```Python
with open("file.txt", "w") as f:
    f.write("Hello world!")
```

Behind the scenes, this is equivalent to:

```Python
f = open("file.txt", "w")
try:
    f.write("Hello world!")
finally:
    f.close()
```

---

## 🏗 **Implementing a Context Manager Class**

```Python
class MyContext:
    def __enter__(self):
        print("Entering context")
        # Setup code here
        return self

    def __exit__(self, exc_type, exc_value, traceback):
        print("Exiting context")
        # Cleanup code here
        # Return True to suppress exceptions, else False
        return False

with MyContext() as ctx:
    print("Inside context")
```

Output:

```Plain
Entering context
Inside context
Exiting context
```

---

## 🔹 `**__enter__**` **and** `**__exit__**` **parameters**

- `__enter__(self)`
    - Called at start of `with` block.
    - Return value assigned to `as` variable.
- `__exit__(self, exc_type, exc_value, traceback)`
    - Called at block exit (even if exception raised).
    - Arguments describe any exception (`None` if none).
    - Return `True` to **suppress** exception, else it propagates.

---

## ✅ **Using** `**contextlib**` **for simpler context managers**

```Python
from contextlib import contextmanager

@contextmanager
def my_context():
    print("Enter")
    yield
    print("Exit")

with my_context():
    print("Inside")
```

Output:

```Plain
Enter
Inside
Exit
```

---

## ⚠️ **Gotchas**

- Always implement **both** `__enter__` and `__exit__` in classes used with `with`.
- Be careful about **exception suppression** — returning `True` from `__exit__` stops exceptions from propagating.
- Use `contextlib` for **simpler, cleaner** context managers.

---

## 📌 **Summary Table**

|Method|Purpose|
|---|---|
|`__enter__()`|Setup resource, return object to use|
|`__exit__()`|Cleanup resource, handle exceptions|
|`with`|Context manager usage syntax|

---

## 🌍 **Real-World Example: File Context Manager**

```Python
class FileOpener:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode

    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_value, traceback):
        self.file.close()

with FileOpener("test.txt", "w") as f:
    f.write("Hello from context manager!")
```

This safely opens and closes the file automatically.

---

✅ **TL;DR:**

- Context managers manage setup/cleanup automatically using `with`.
- Implement `__enter__` and `__exit__` to create one.
- Use `contextlib` for easier creation.