---
Created: 2025-08-21T19:29
tags:
  - Concurrency-Basics
---
## ✅ **What is** `**threading**`**?**

The `threading` module allows **concurrent execution** of code within the same process.

✔️ Useful for **I/O-bound tasks** (network, file, waiting).

✔️ Runs multiple threads **within one process**.

⚠️ **Not truly parallel for CPU-heavy tasks** because of the **Global Interpreter Lock (GIL)**.

---

## 🏗 **Basic Thread Usage**

```Python
import threading

def worker():
    print("Worker thread running")

# Create thread
t = threading.Thread(target=worker)
t.start()    # Starts the thread
t.join()     # Wait for it to finish
```

---

## ✅ **Thread Lifecycle**

1. **Create**: `Thread(target=func, args=(...))`
2. **Start**: `thread.start()`
3. **Run concurrently**
4. **Join**: `thread.join()` waits for completion

---

## 🔹 **Common Threading Features**

|Feature|Example|
|---|---|
|**Thread name**|`thread.name`|
|**Check alive**|`thread.is_alive()`|
|**Daemon thread**|`thread.daemon = True` (kills when main exits)|
|**Active threads**|`threading.active_count()`|

---

## ✅ **Example with Arguments**

```Python
def greet(name):
    print(f"Hello {name} from {threading.current_thread().name}")

t = threading.Thread(target=greet, args=("Alice",))
t.start()
t.join()
```

---

## 🔄 **Synchronization with Lock**

Threads may **conflict** when accessing shared data → use `Lock`.

```Python
lock = threading.Lock()
counter = 0

def increment():
    global counter
    for _ in range(100000):
        with lock:      # ensures safe access
            counter += 1

threads = [threading.Thread(target=increment) for _ in range(5)]
for t in threads: t.start()
for t in threads: t.join()

print("Final counter:", counter)
```

Without lock → race conditions! ✅ **Always lock shared mutable state.**

---

## 🔹 **Other Sync Primitives**

- `threading.RLock()` → Reentrant lock
- `threading.Semaphore()` → Limits access to a resource
- `threading.Event()` → Thread signaling
- `threading.Condition()` → Complex wait/notify patterns
- `threading.Barrier()` → Wait until N threads reach a point

---

## ✅ **Daemon Threads**

Daemon threads **automatically stop when the main thread exits**.

```Python
def background_task():
    while True:
        print("Running in background...")

t = threading.Thread(target=background_task, daemon=True)
t.start()
```

---

## ⚠️ **Gotchas**

- **CPU-bound tasks?** → Use `multiprocessing`, not `threading` (GIL limits parallelism).
- Always use `join()` if you want to wait for threads to finish.
- Be careful with shared mutable data → use locks.

---

## 📌 **Summary Table**

|Concept|Usage|
|---|---|
|`Thread(target, args)`|Create a thread|
|`start()`|Start thread|
|`join()`|Wait for thread|
|`daemon=True`|Stops with main thread|
|`Lock()`|Prevent race conditions|
|`Event()`|Signal between threads|

---

## 🌍 **Real-World Example: Download Multiple URLs Concurrently**

```Python
import threading
import time

def download(url):
    print(f"Starting download: {url}")
    time.sleep(2)  # Simulate network delay
    print(f"Finished download: {url}")

urls = ["url1", "url2", "url3"]

threads = []
for u in urls:
    t = threading.Thread(target=download, args=(u,))
    threads.append(t)
    t.start()

# Wait for all downloads
for t in threads:
    t.join()

print("All downloads complete!")
```

Output:

```Plain
Starting download: url1
Starting download: url2
Starting download: url3
Finished download: url1
Finished download: url2
Finished download: url3
All downloads complete!
```

👉 **Why threading?**

- **Concurrent I/O** → downloads run simultaneously, reducing total time.

---

✅ **TL;DR:**

- Use `threading` for **I/O-bound tasks**.
- Use `Lock` for **safe shared state**.
- For CPU-heavy tasks, use `**multiprocessing**`.