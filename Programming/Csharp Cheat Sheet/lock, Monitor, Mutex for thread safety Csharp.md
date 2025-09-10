---
Created: 2025-08-07T20:10
tags:
  - Threading-&-Task
---
## ✅ 1. Concept Overview

In multithreaded applications, **thread safety** ensures that shared resources (e.g., a variable or object) are accessed by only one thread at a time. This prevents race conditions, data corruption, and unpredictable behavior.

C# provides several synchronization primitives:

- `lock` (simplest)
- `Monitor` (more control than `lock`)
- `Mutex` (can be used across processes)

---

## 🔒 `lock` Keyword

### 🔹 What it is:

A simplified syntax for `Monitor.Enter/Exit`. It prevents multiple threads from entering a **critical section** at the same time.

### 🔹 Syntax:

```C#
lock (someObject) {
    // Critical section
}
```

### 🔹 Rules:

- `someObject` should be **private** and **not mutable**.
- Avoid locking on `this`, `typeof`, or public objects.

### 🔹 Pros:

- Easy to use and clean syntax.
- Auto-handles `Monitor.Enter` and `Exit` (even on exception).

---

## ⚙️ `Monitor` Class

### 🔹 What it is:

A lower-level synchronization primitive. It gives more control (e.g., try locking with timeout or checking ownership).

### 🔹 Common Methods:

```C#
Monitor.Enter(obj);
try {
    // Critical section
}
finally {
    Monitor.Exit(obj);
}
```

With timeout:

```C#
if (Monitor.TryEnter(obj, TimeSpan.FromSeconds(2))) {
    try {
        // Critical section
    }
    finally {
        Monitor.Exit(obj);
    }
}
```

### 🔹 Pros:

- Supports timeout and conditional waiting.
- More control for advanced use cases.

---

## 🧱 `Mutex`

### 🔹 What it is:

A kernel-based locking primitive that can work **across processes** (unlike `lock` or `Monitor` which are in-process only).

### 🔹 Syntax:

```C#
Mutex mutex = new Mutex();
mutex.WaitOne(); // Enter
try {
    // Critical section
}
finally {
    mutex.ReleaseMutex(); // Exit
}
```

Named (cross-process):

```C#
Mutex mutex = new Mutex(false, "Global\\MyNamedMutex");
```

### 🔹 Pros:

- Works across **multiple processes**.
- Good for system-wide resource protection.

### 🔹 Cons:

- Slower (involves OS-level context switches).
- Higher overhead than `lock` or `Monitor`.

---

## 🧾 2. Summary Table

|Feature|`lock`|`Monitor`|`Mutex`|
|---|---|---|---|
|Scope|In-process only|In-process only|Cross-process capable|
|Simplicity|Very simple|Moderate complexity|More complex|
|Timeout|❌ Not supported|✅ `TryEnter(timeout)`|✅ `WaitOne(timeout)`|
|Performance|✅ Fastest|✅ Fast|❌ Slower|
|Exception Safety|✅ Automatic|❌ Must use `try-finally`|❌ Must use `try-finally`|
|Use Case|Most scenarios|Need timeout or control|Shared resources across apps|

---

## 💡 3. Real-World Example

Imagine you’re writing a logging class used by multiple threads:

### With `lock`:

```C#
private static readonly object _logLock = new object();

public void WriteLog(string message) {
    lock (_logLock) {
        File.AppendAllText("log.txt", message + Environment.NewLine);
    }
}
```

### With `Monitor` (with timeout):

```C#
private static readonly object _logLock = new object();

public void WriteLog(string message) {
    if (Monitor.TryEnter(_logLock, TimeSpan.FromSeconds(1))) {
        try {
            File.AppendAllText("log.txt", message + Environment.NewLine);
        } finally {
            Monitor.Exit(_logLock);
        }
    } else {
        Console.WriteLine("Could not acquire lock.");
    }
}
```

### With `Mutex` (named):

```C#
private static readonly Mutex _mutex = new Mutex(false, "Global\\LogFileMutex");

public void WriteLog(string message) {
    _mutex.WaitOne();
    try {
        File.AppendAllText("log.txt", message + Environment.NewLine);
    } finally {
        _mutex.ReleaseMutex();
    }
}
```

---

## 🧠 Gotchas & Best Practices

- Never lock on public or `this` — risk of **deadlocks** or interference from other code.
- Always use `try-finally` with `Monitor` and `Mutex`.
- Prefer `lock` unless you need timeout or inter-process coordination.
- Use `Mutex` only when sharing between **processes**, otherwise it's overkill.