---
Created: 2025-08-07T20:10
tags:
  - Optional
---
## ✅ 1. Concept Overview

The `System.Diagnostics` namespace provides tools for:

- Logging messages (`Trace`, `Debug`)
- Inspecting stack traces
- Measuring time (`Stopwatch`)
- Attaching debuggers
- Event logging (Windows Event Log)

Use this for:

- In-app diagnostics
- Debug-time messages
- Performance measurement
- Structured logs for analysis

```C#
using System.Diagnostics;
```

---

## 🧾 2. Summary Table

|Feature|Class / Method|Description|
|---|---|---|
|Basic logging|`Debug.WriteLine()` / `Trace.WriteLine()`|Log messages (conditional based on build)|
|Assertions|`Debug.Assert(condition)`|Logs when a condition fails (only in DEBUG)|
|Timing|`Stopwatch`|Measures elapsed time|
|Stack trace|`StackTrace` / `StackFrame`|Captures the current call stack|
|Attach debugger|`Debugger.Launch()`|Attaches a debugger at runtime|
|Break in code|`Debugger.Break()`|Breakpoint in code|
|Event logging|`EventLog`|Writes to Windows Event Log (Windows only)|

---

## 🧰 3. Debug vs Trace

|Type|Available When|Output Location|
|---|---|---|
|`Debug`|Only in **DEBUG** builds|Output window (IDE), listeners|
|`Trace`|In **both DEBUG & RELEASE** builds|Output window or file (with listeners)|

You can also configure **Trace Listeners** to direct logs to files, console, or event log.

---

## 🧪 4. Key Usage Examples

### 🔹 Log with Debug (IDE only)

```C#
Debug.WriteLine("Debug: App started.");
```

### 🔹 Log with Trace (Production-safe)

```C#
Trace.WriteLine("Trace: User login attempt.");
```

### 🔹 Debug Assertion

```C#
Debug.Assert(user != null, "User must not be null.");
```

### 🔹 Measure Execution Time

```C#
Stopwatch sw = Stopwatch.StartNew();

// code to time
Thread.Sleep(500);

sw.Stop();
Console.WriteLine($"Elapsed: {sw.ElapsedMilliseconds} ms");
```

### 🔹 View Stack Trace

```C#
StackTrace st = new StackTrace();
Console.WriteLine(st.ToString());
```

### 🔹 Force Debugger to Attach

```C#
if (!Debugger.IsAttached) {
    Debugger.Launch();
}
Debugger.Break();  // Triggers a manual breakpoint
```

---

## 💡 5. Real-World Logging Setup

### 🔸 Configure a File Trace Listener (writes logs to file)

```C#
TextWriterTraceListener logFile = new TextWriterTraceListener("app.log");
Trace.Listeners.Add(logFile);
Trace.AutoFlush = true;

Trace.WriteLine("App started.");
```

---

### 🔸 Use in a Custom Logger Class

```C#
public static class Logger {
    public static void Log(string message) {
        Trace.WriteLine($"[{DateTime.Now}] {message}");
    }
}
```

---

## ⚠️ 6. Gotchas & Tips

|Tip|Why|
|---|---|
|Use `Trace` for release-safe diagnostics|Unlike `Debug`, `Trace` works in production builds|
|Use `Stopwatch` over `DateTime` for performance timing|More accurate|
|Remember `Debug.WriteLine()` does not appear in Release builds|It's conditionally compiled|
|Set `Trace.AutoFlush = true`|Ensures logs are immediately written to file|
|Always remove `Debugger.Break()` from production code|It's for dev debugging only|

---

## 🧬 7. When to Use Which

|Use Case|Recommended API|
|---|---|
|Quick dev logs|`Debug.WriteLine()`|
|Long-term app diagnostics|`Trace.WriteLine()` + `TextWriterTraceListener`|
|Performance testing|`Stopwatch`|
|Unexpected nulls/crashes|`Debug.Assert()`|
|Runtime error inspection|`StackTrace`, `Debugger.Break()`|