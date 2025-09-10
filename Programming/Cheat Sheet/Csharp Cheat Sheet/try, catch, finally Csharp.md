---
Created: 2025-08-07T20:10
tags:
  - Exception-Handling
---
## ✅ What Are They?

Used to **handle exceptions** (runtime errors) gracefully, preventing the program from crashing and allowing error recovery or cleanup.

---

## 🧠 Basic Syntax

```C#
try
{
    // Code that may throw an exception
}
catch (ExceptionType ex)
{
    // Code to handle the exception
}
finally
{
    // Code that always runs (cleanup)
}
```

---

## 🧾 Components Explained

### ✅ `try` block

Contains code that **might throw** an exception.

### ✅ `catch` block

Handles the error. You can:

- Catch specific exceptions (recommended)
- Use a general `catch` block

### ✅ `finally` block _(optional)_

Runs **regardless of an exception** — good for closing files, releasing resources, etc.

---

## 🧪 Example

```C#
try
{
    int[] nums = { 1, 2 };
    Console.WriteLine(nums[5]); // Will throw
}
catch (IndexOutOfRangeException ex)
{
    Console.WriteLine("Index error: " + ex.Message);
}
finally
{
    Console.WriteLine("This always runs.");
}
```

**Output:**

```Plain
Index error: Index was outside the bounds of the array.
This always runs.
```

---

## 🔀 Multiple `catch` Blocks

```C#
try
{
    int.Parse("abc"); // FormatException
}
catch (FormatException ex)
{
    Console.WriteLine("Invalid number format.");
}
catch (Exception ex)
{
    Console.WriteLine("General error: " + ex.Message);
}
```

✔️ Catch more specific exceptions **before** general ones.

---

## 🛠️ Common Exception Types

|Exception|Description|
|---|---|
|`DivideByZeroException`|Dividing by zero|
|`FormatException`|Invalid format (e.g., parsing)|
|`IndexOutOfRangeException`|Array index out of bounds|
|`NullReferenceException`|Accessing a null object|
|`FileNotFoundException`|File does not exist|
|`IOException`|Input/output error|
|`ArgumentException`|Invalid method argument|

---

## 📦 Using Exception Object

```C#
catch (Exception ex)
{
    Console.WriteLine($"Error: {ex.Message}");
    Console.WriteLine($"Stack Trace: {ex.StackTrace}");
}
```

---

## ⚙️ Best Practices

- 🧠 Catch only exceptions you can **handle or log**.
- ✅ Use specific exception types first.
- ❌ Don’t silently swallow exceptions (`catch {}`).
- ✅ Always clean up in `finally`, or use `using` blocks for `IDisposable`.

---

## 📋 Summary Table

|Keyword|Purpose|
|---|---|
|`try`|Run code that might throw|
|`catch`|Handle a specific or general error|
|`finally`|Always run code (cleanup, close, etc)|

---

## 🧠 Real-World Use Case

```C#
StreamReader reader = null;
try
{
    reader = new StreamReader("file.txt");
    Console.WriteLine(reader.ReadToEnd());
}
catch (FileNotFoundException)
{
    Console.WriteLine("File not found.");
}
finally
{
    if (reader != null)
        reader.Close(); // Clean up
}
```