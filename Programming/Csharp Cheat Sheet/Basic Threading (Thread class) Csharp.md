---
Created: 2025-08-07T20:10
tags:
  - Threading-&-Task
---
## ✅ What is Threading?

Threading allows your program to **run multiple operations concurrently** — improving responsiveness (like UI apps) or parallelizing heavy work.

- `Thread` class is part of `**System.Threading**`.
- Used to create and manage threads manually.

---

## 🔧 Syntax: Creating and Starting a Thread

```C#
using System;
using System.Threading;

void MyMethod()
{
    Console.WriteLine("Running in a separate thread!");
}

Thread t = new Thread(MyMethod); // ThreadStart delegate
t.Start();
```

---

## 📌 Using Lambda / Anonymous Methods

```C#
Thread t = new Thread(() =>
{
    Console.WriteLine("Hello from thread!");
});
t.Start();
```

---

## 💤 Sleep (Pause Thread)

```C#
Thread.Sleep(1000); // Sleep for 1000 ms = 1 second
```

---

## 🔃 Thread.Join() – Wait for Completion

```C#
Thread t = new Thread(() => Console.WriteLine("Thread running"));
t.Start();
t.Join(); // Main thread waits for t to finish
Console.WriteLine("Thread completed");
```

---

## 🔐 Shared Data + Race Conditions

When multiple threads access shared data:

```C#
int counter = 0;

void Increment()
{
    for (int i = 0; i < 1000; i++) counter++;
}

Thread t1 = new Thread(Increment);
Thread t2 = new Thread(Increment);
t1.Start(); t2.Start();
t1.Join(); t2.Join();

Console.WriteLine(counter); // NOT always 2000 due to race condition!
```

---

## 🔒 Locking to Avoid Race Conditions

```C#
object locker = new object();
int counter = 0;

void SafeIncrement()
{
    for (int i = 0; i < 1000; i++)
    {
        lock (locker)
        {
            counter++;
        }
    }
}
```

---

## 📋 Threading Summary Table

|Feature|Usage Example|
|---|---|
|Create Thread|`new Thread(MyMethod)`|
|Start Thread|`t.Start()`|
|Sleep|`Thread.Sleep(ms)`|
|Wait for Thread|`t.Join()`|
|Race Condition|Happens with shared data|
|Lock|`lock(obj) { ... }` to make critical section|

---

## 🔥 Real-World Example

### Download and Process Simultaneously

```C#
void Download()
{
    Console.WriteLine("Downloading...");
    Thread.Sleep(2000);
    Console.WriteLine("Download complete");
}

void Process()
{
    Console.WriteLine("Processing...");
    Thread.Sleep(1000);
    Console.WriteLine("Process complete");
}

Thread t1 = new Thread(Download);
Thread t2 = new Thread(Process);

t1.Start();
t2.Start();

t1.Join();
t2.Join();
Console.WriteLine("All tasks done");
```

---

## ⚠️ Gotchas

|Issue|Fix|
|---|---|
|UI updates from thread|Must marshal back to main/UI thread|
|Accessing shared data|Use `lock`, `Monitor`, or other sync primitives|
|Threads stay running|Make sure `t.Join()` is used or threads terminate|

---

## ✅ Best Practices

- For simple tasks, prefer `Task` or `async/await` (modern threading).
- Use `Thread` when you need **low-level control**.
- Always **handle exceptions** inside threads.