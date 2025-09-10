---
Created: 2025-08-07T20:10
tags:
  - File-&-Directory-I/O
---
## 📌 Overview

C# provides multiple classes to handle file input/output:

|Class|Purpose|
|---|---|
|`File`|Quick read/write operations|
|`StreamReader`|Reading from text files|
|`StreamWriter`|Writing to text files|

All are in the `System.IO` namespace.

---

## 📖 Reading Files

### 1. **Using** `**File.ReadAllText()**` – Read entire file as one string

```C#
string content = File.ReadAllText("example.txt");
Console.WriteLine(content);
```

### 2. **Using** `**File.ReadAllLines()**` – Read lines into a string array

```C#
string[] lines = File.ReadAllLines("example.txt");
foreach (string line in lines)
    Console.WriteLine(line);
```

### 3. **Using** `**StreamReader**` **(line by line)**

```C#
using (StreamReader reader = new StreamReader("example.txt"))
{
    string line;
    while ((line = reader.ReadLine()) != null)
    {
        Console.WriteLine(line);
    }
}
```

---

## 📝 Writing Files

### 1. **Using** `**File.WriteAllText()**` – Overwrites entire file

```C#
File.WriteAllText("output.txt", "Hello, World!");
```

### 2. **Using** `**File.WriteAllLines()**` – Write an array of strings

```C#
string[] lines = { "Line 1", "Line 2" };
File.WriteAllLines("output.txt", lines);
```

### 3. **Using** `**File.AppendAllText()**` – Adds content without deleting existing

```C#
File.AppendAllText("output.txt", "New line\n");
```

### 4. **Using** `**StreamWriter**`

```C#
using (StreamWriter writer = new StreamWriter("output.txt"))
{
    writer.WriteLine("First line");
    writer.WriteLine("Second line");
}
```

### ➕ Append with StreamWriter

```C#
using (StreamWriter writer = new StreamWriter("output.txt", append: true))
{
    writer.WriteLine("This will be added at the end");
}
```

---

## 🧠 Gotchas

|Pitfall|Advice|
|---|---|
|File not found|Use `File.Exists("filename")` to check before reading|
|File locked|Ensure `StreamReader/Writer` are properly disposed (use `using`)|
|Encoding issues|Use `StreamReader(path, Encoding.UTF8)` if needed|
|File path errors|Use `Path.Combine()` for cross-platform safety|
|Large files|Prefer `StreamReader` for memory efficiency|

---

## ✅ Real-World Example

```C#
string filePath = "log.txt";

// Append log entry
using (StreamWriter writer = new StreamWriter(filePath, append: true))
{
    writer.WriteLine($"{DateTime.Now}: User logged in.");
}

// Read and display log
if (File.Exists(filePath))
{
    string[] logs = File.ReadAllLines(filePath);
    foreach (string log in logs)
        Console.WriteLine(log);
}
```

---

## 📋 Summary Table

|Operation|Method/Class|Notes|
|---|---|---|
|Read entire file|`File.ReadAllText()`|Returns a single string|
|Read lines|`File.ReadAllLines()`|Returns string array|
|Read line-by-line|`StreamReader`|Efficient for large files|
|Write (overwrite)|`File.WriteAllText()`|Overwrites entire file|
|Write lines|`File.WriteAllLines()`|Writes an array of strings|
|Append text|`File.AppendAllText()`|Adds to the end of file|
|Write with control|`StreamWriter`|More flexible, supports append|