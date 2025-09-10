---
Created: 2025-08-21T19:29
tags:
  - Concurrency-Basics
---
## ✅ **What is** `**asyncio**`**?**

`asyncio` is Python’s built-in **asynchronous I/O framework** for:

✔️ Running **concurrent** tasks (like downloads, API calls)

✔️ Efficiently handling **I/O-bound operations** without blocking

⚠️ It does **NOT** give true parallelism for CPU-bound tasks (use `multiprocessing` for that).

---

## 🏗 **Key Concepts**

- **Coroutine** → A special function defined with `async def`
- **await** → Suspends execution until awaited coroutine finishes
- **Event Loop** → Schedules and runs coroutines
- **Task** → Wrapper for a coroutine to run concurrently

---

## ✅ **Basic Example**

```Python
import asyncio

async def say_hello():
    print("Hello...")
    await asyncio.sleep(1)   # Simulate I/O
    print("World!")

asyncio.run(say_hello())
```

Output:

```Plain
Hello...
World!
```

➡ `await asyncio.sleep(1)` **does not block**, allowing other tasks to run meanwhile.

---

## 🔹 **Running Multiple Coroutines Concurrently**

```Python
async def task(name, delay):
    print(f"Task {name} started")
    await asyncio.sleep(delay)
    print(f"Task {name} finished")

async def main():
    await asyncio.gather(
        task("A", 2),
        task("B", 1),
        task("C", 3)
    )

asyncio.run(main())
```

Output (runs concurrently):

```Plain
Task A started
Task B started
Task C started
Task B finished
Task A finished
Task C finished
```

---

## ✅ **Creating & Managing Tasks**

```Python
async def my_task():
    await asyncio.sleep(1)
    print("Task done")

async def main():
    t = asyncio.create_task(my_task())  # Schedule it
    print("Waiting for task...")
    await t

asyncio.run(main())
```

---

## 🔄 **Common asyncio Functions**

|Function|What it does|
|---|---|
|`asyncio.run(coro)`|Run main coroutine|
|`asyncio.sleep(sec)`|Non-blocking sleep|
|`asyncio.gather(*coros)`|Run multiple coroutines concurrently|
|`asyncio.create_task(coro)`|Schedule a coroutine to run in background|
|`asyncio.wait(tasks)`|Wait for tasks to finish|

---

## ✅ **Async vs Sync**

```Python
# Synchronous - waits sequentially
def sync_main():
    for _ in range(3):
        time.sleep(1)
        print("Done")

# Asynchronous - runs concurrently
async def async_main():
    await asyncio.gather(
        asyncio.sleep(1),
        asyncio.sleep(1),
        asyncio.sleep(1)
    )
    print("All done in ~1s")
```

---

## ⚠️ **Gotchas**

- Can only `await` inside an `**async def**`
- Use `asyncio.run()` only **once per program entry**
- `await` is for **non-blocking I/O**, not CPU-heavy work
- Don’t mix `time.sleep()` (blocking) with asyncio → use `await asyncio.sleep()`

---

## 📌 **Summary Table**

|Concept|Description|
|---|---|
|`async def`|Defines a coroutine|
|`await`|Suspend until coroutine finishes|
|`asyncio.run()`|Run main coroutine|
|`gather()`|Run multiple coroutines concurrently|
|`create_task()`|Schedule background coroutine|

---

## 🌍 **Real-World Example: Concurrent Web Requests**

```Python
import asyncio
import aiohttp  # async HTTP client

async def fetch(url):
    async with aiohttp.ClientSession() as session:
        async with session.get(url) as response:
            print(f"{url} → {response.status}")
            return await response.text()

async def main():
    urls = [
        "https://example.com",
        "https://httpbin.org/get",
        "https://jsonplaceholder.typicode.com/todos/1"
    ]
    # Fetch all URLs concurrently
    results = await asyncio.gather(*[fetch(url) for url in urls])
    print("Fetched", len(results), "pages")

asyncio.run(main())
```

Output:

```Plain
https://example.com → 200
https://httpbin.org/get → 200
https://jsonplaceholder.typicode.com/todos/1 → 200
Fetched 3 pages
```

👉 **Why asyncio?**

- Fetches multiple URLs **concurrently** without blocking
- Much faster than sequential HTTP requests

---

✅ **TL;DR:**

- `asyncio` is for **concurrent I/O**
- `async def` defines coroutines; `await` suspends execution
- `gather()` runs multiple coroutines at once
- Use `aiohttp` for async HTTP requests