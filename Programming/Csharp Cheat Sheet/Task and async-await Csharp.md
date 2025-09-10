---
Created: 2025-08-07T20:10
tags:
  - Threading-&-Task
---
## ✅ What is async/await?

- `async` enables **asynchronous methods**.
- `await` pauses execution until a `Task` completes — without blocking the thread.
- Used for I/O-bound and CPU-bound operations.

---

## 🧱 Syntax Overview

```C#
async Task MyAsyncMethod()
{
    await Task.Delay(1000); // Non-blocking wait
    Console.WriteLine("Done!");
}
```

Call it like this:

```C#
await MyAsyncMethod(); // only inside another async method
```

> If you're in Main(), use:
> 
> `Task.Run(() => MyAsyncMethod()).Wait();` (Console apps pre-C# 7.1)

---

## 🔧 Return Types

|Return Type|Usage|
|---|---|
|`Task`|Method does work, no result|
|`Task<T>`|Returns a value asynchronously|
|`void`|Avoid unless for event handlers|

```C#
async Task<int> GetNumberAsync()
{
    await Task.Delay(100);
    return 42;
}
```

---

## 🔄 Example: Async File Reading

```C#
using System.IO;

async Task ReadFileAsync()
{
    string content = await File.ReadAllTextAsync("file.txt");
    Console.WriteLine(content);
}
```

---

## ⚙️ Simulating Work with Task.Run()

```C#
async Task DoHeavyWork()
{
    int result = await Task.Run(() =>
    {
        Thread.Sleep(2000); // Simulate work
        return 42;
    });
    Console.WriteLine(result);
}
```

---

## 🧠 Real-World Scenario: API Call

```C#
async Task<string> GetDataAsync()
{
    using (HttpClient client = new HttpClient())
    {
        string result = await client.GetStringAsync("https://api.example.com/data");
        return result;
    }
}
```

---

## 🧯 Error Handling with try-catch

```C#
async Task HandleErrorAsync()
{
    try
    {
        await Task.Delay(-1); // invalid delay
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Error: {ex.Message}");
    }
}
```

---

## 📋 Summary Table

|Feature|Example|Notes|
|---|---|---|
|`async`|`async Task Foo()`|Marks method as async|
|`await`|`await Task.Delay(1000)`|Non-blocking wait|
|`Task`|`Task MyTask()`|Async method with no return|
|`Task<T>`|`Task<int> GetNum()`|Async method with return|
|`Task.Run()`|`await Task.Run(() => ...)`|Run CPU-bound work|
|Exception Handling|`try { await ... } catch { ... }`|Catch async errors|

---

## ⚠️ Gotchas & Tips

|Gotcha|Fix|
|---|---|
|Cannot `await` in non-async method|Make method `async`|
|Forgetting `await` on a `Task`|The method won’t wait — can cause bugs|
|Blocking with `.Wait()` or `.Result`|Avoid in UI apps (deadlocks!)|
|Async void|Only for event handlers — cannot `await` them|

---

## 📘 Console App Tip (Main method)

Starting C# 7.1, you can make `Main` async:

```C#
static async Task Main(string[] args)
{
    await MyAsyncMethod();
}
```