---
Created: 2025-08-07T20:10
tags:
  - String-Manipulation
---
## ✅ What is `StringBuilder`?

`StringBuilder` is a **mutable** string class from `System.Text`. Unlike `string`, it allows modifications **without creating a new object** every time, making it much more efficient for large or repeated string operations.

> Namespace: System.Text

---

## 🧠 Syntax

### ✅ Declaration

```C#
using System.Text;

StringBuilder sb = new StringBuilder();
```

### ✅ With Initial Value

```C#
StringBuilder sb = new StringBuilder("Hello");
```

### ✅ With Capacity

```C#
StringBuilder sb = new StringBuilder(100); // reserve 100 characters
```

---

## 🔧 Common Methods

|Method|Description|Example|
|---|---|---|
|`.Append(str)`|Adds to the end|`sb.Append("World")`|
|`.AppendLine(str)`|Adds with newline|`sb.AppendLine("Line1")`|
|`.Insert(index, str)`|Inserts at index|`sb.Insert(5, "Hello")`|
|`.Remove(start, length)`|Removes part of the string|`sb.Remove(3, 2)`|
|`.Replace(old, new)`|Replaces text|`sb.Replace("Hi", "Hello")`|
|`.Clear()`|Removes all contents|`sb.Clear()`|
|`.ToString()`|Converts to standard string|`string s = sb.ToString()`|
|`.Length`|Gets or sets number of characters|`int len = sb.Length`|
|`.Capacity` / `.MaxCapacity`|Gets current/max capacity|`sb.Capacity`|

---

## 🧪 Example

```C#
using System;
using System.Text;

class Program {
    static void Main() {
        StringBuilder sb = new StringBuilder("Hello");
        sb.Append(" World");
        sb.AppendLine("!");
        sb.Insert(0, "Greeting: ");
        sb.Replace("World", "C#");

        Console.WriteLine(sb.ToString());
    }
}
```

**Output:**

```Plain
Greeting: Hello C#!
```

---

## 🆚 String vs StringBuilder

|Feature|`string`|`StringBuilder`|
|---|---|---|
|Mutability|❌ Immutable|✅ Mutable|
|Performance|❌ Slower in loops|✅ Faster with many operations|
|Syntax Simplicity|✅ Easier for simple tasks|⚠️ More verbose|

🔺 **Use** `**string**` for short, static, or simple manipulations.

🔺 **Use** `**StringBuilder**` for loops, logging, templating, or large strings.

---

## 🧠 Real-World Use Case: Efficient String Concatenation

```C#
StringBuilder log = new StringBuilder();
for (int i = 1; i <= 1000; i++)
{
    log.Append($"Log Entry {i}\n");
}
Console.WriteLine(log.ToString());
```

✅ Way more efficient than:

```C#
string log = "";
for (...) { log += "..." } // ❌ Performance hit
```

---

## 📋 Summary Table

|Method|Purpose|
|---|---|
|`.Append(str)`|Add string to end|
|`.AppendLine()`|Add string + newline|
|`.Insert(i, str)`|Insert string at index|
|`.Remove(i, len)`|Remove substring|
|`.Replace(old, new)`|Replace substring|
|`.Clear()`|Remove all contents|
|`.ToString()`|Convert to regular string|