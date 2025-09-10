---
Created: 2025-08-07T20:10
tags:
  - Attributes
---
## ✅ 1. Concept Overview

**Attributes** in C# are metadata added to code elements (classes, methods, properties, etc.). They influence behavior at **compile time**, **runtime**, or just serve as **documentation**.

### Syntax:

```C#
[AttributeName(optionalParams)]
public class MyClass { ... }
```

### Applied to:

- Classes
- Methods
- Properties
- Fields
- Assemblies
- Enums

---

## 🧩 2. Common Built-in Attributes

|Attribute|Purpose|
|---|---|
|`[Obsolete]`|Marks code as outdated/deprecated|
|`[Serializable]`|Marks a class to support binary serialization|
|`[NonSerialized]`|Excludes a field from serialization|
|`[Flags]`|Allows bitwise combination of enum values|
|`[DllImport]`|Enables interop with unmanaged code|
|`[Conditional]`|Method executes only if a conditional symbol is defined|
|`[CallerMemberName]`|Used in logging/invocation tracking|
|`[AttributeUsage]`|Restricts how a custom attribute can be used|

---

## 🛠️ 3. Attribute Details & Usage

### 🔹 `[Obsolete]`

Marks elements that should no longer be used. Compiler gives a warning or error.

```C#
[Obsolete("Use NewMethod instead")]
public void OldMethod() {}

[Obsolete("Do not use", true)]  // will cause compile error
public void Deprecated() {}
```

---

### 🔹 `[Serializable]` and `[NonSerialized]`

Used with **binary formatters** (legacy) or custom serialization logic.

```C#
[Serializable]
public class Person {
    public string Name;

    [NonSerialized]
    public int TempId; // This field will be skipped during serialization
}
```

> Note: For JSON/XML serialization, attributes like [JsonIgnore], [XmlElement] from external libraries are often used instead.

---

### 🔹 `[Flags]`

Used for **bitwise enums**, often in configuration or permission systems.

```C#
[Flags]
public enum FileAccess {
    Read = 1,
    Write = 2,
    Execute = 4
}

FileAccess access = FileAccess.Read | FileAccess.Write;
bool canWrite = access.HasFlag(FileAccess.Write);  // true
```

---

### 🔹 `[DllImport]`

Used for calling **native/unmanaged functions** (P/Invoke).

```C#
[DllImport("user32.dll")]
public static extern int MessageBox(IntPtr hWnd, string text, string caption, uint type);
```

---

### 🔹 `[Conditional("DEBUG")]`

Used to include methods **only in certain builds**.

```C#
[Conditional("DEBUG")]
void LogDebug(string message) {
    Console.WriteLine("DEBUG: " + message);
}
```

---

### 🔹 `[CallerMemberName]`

Used in logging and data-binding to get the name of the **calling method**.

```C#
public void Log(string message, [CallerMemberName] string caller = null) {
    Console.WriteLine($"[{caller}]: {message}");
}
```

---

## 📋 4. Summary Table

|Attribute|Applies To|Purpose / Effect|
|---|---|---|
|`[Obsolete]`|Class, Method, etc.|Warn or error for deprecated elements|
|`[Serializable]`|Class|Marks type for serialization|
|`[NonSerialized]`|Field|Excludes field from serialization|
|`[Flags]`|Enum|Enables bitwise enum operations|
|`[DllImport]`|Method|Enables interop with native libraries|
|`[Conditional]`|Method|Includes method only in specific builds|
|`[CallerMemberName]`|Method parameter|Captures caller name at runtime|

---

## 💡 5. Real-World Example

```C#
using System;
using System.Runtime.CompilerServices;
using System.Runtime.InteropServices;

[Serializable]
public class User {
    public string Username;

    [NonSerialized]
    public string SessionToken;
}

[Flags]
public enum Permissions {
    None = 0,
    Read = 1,
    Write = 2,
    Execute = 4
}

public class Logger {
    [Conditional("DEBUG")]
    public static void Log(string message, [CallerMemberName] string caller = "") {
        Console.WriteLine($"[{caller}] {message}");
    }

    [Obsolete("Use Log() instead")]
    public static void OldLog(string msg) => Console.WriteLine(msg);
}

public class NativeMethods {
    [DllImport("user32.dll")]
    public static extern int MessageBox(IntPtr hWnd, string text, string caption, uint type);
}
```

---

## ⚠️ Gotchas & Best Practices

|Tip|Explanation|
|---|---|
|Use `[Obsolete(..., true)]` sparingly|Compile-time errors should be used only when migration is critical.|
|Avoid `[Serializable]` on large/complex types|Prefer custom serialization (e.g., JSON.NET).|
|Don’t overuse `[Conditional]`|May cause missing method calls in release builds.|
|Cache reflection results if inspecting attributes dynamically|Improves performance.|