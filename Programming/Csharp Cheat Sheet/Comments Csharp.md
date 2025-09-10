---
Created: 2025-08-07T20:20
tags:
  - Basics-&-Syntax
---
## 🔹 1. **Single-Line Comments**

### 🔸 Syntax:

```C#
// This is a single-line comment
int x = 5; // Comment after code
```

- Use `//` before the comment.
- Common for short explanations, reminders, or disabling code lines temporarily.

---

## 🔹 2. **Multi-Line (Block) Comments**

### 🔸 Syntax:

```C#
/*
 This is a multi-line comment.
 It can span multiple lines.
*/
int y = 10;
```

- Starts with `/*` and ends with `/`.
- Useful for longer notes or temporarily disabling blocks of code.

---

## 🔹 3. **XML Documentation Comments**

Used to generate **documentation** for classes, methods, properties, etc.

### 🔸 Syntax:

```C#
/// <summary>
/// Adds two numbers.
/// </summary>
/// <param name="a">First number</param>
/// <param name="b">Second number</param>
/// <returns>The sum of a and b</returns>
public int Add(int a, int b)
{
    return a + b;
}
```

- Must start with `///`.
- Recognized by IntelliSense and tools like **DocFX**, **Sandcastle**, or **Visual Studio’s XML doc generator**.

---

## 📋 XML Comment Tags

|Tag|Purpose|
|---|---|
|`<summary>`|Brief explanation of what the code does|
|`<param>`|Describes method parameters|
|`<returns>`|Describes return value|
|`<remarks>`|Additional info|
|`<example>`|Usage example|
|`<exception>`|Describes exceptions the method might throw|

---

## 🧠 Gotchas

|Issue|Explanation|
|---|---|
|Nested block comments not allowed|You can’t do `/* ... /* ... */ ... */`|
|Don’t over-comment obvious code|Keep it concise and helpful|
|Keep comments updated|Outdated comments confuse readers|
|Don't comment out code and leave forever|Clean up dead code|

---

## 📋 Summary Table

|Comment Type|Syntax|Use Case|
|---|---|---|
|Single-line|`// comment`|Brief notes, disabling one line|
|Multi-line block|`/* ... */`|Longer explanations or blocks|
|XML doc comment|`/// <summary>...</summary>`|Auto-doc generation & IntelliSense|

---

## 🌍 Real-World Example

```C#
using System;

class Calculator
{
    /// <summary>
    /// Multiplies two numbers.
    /// </summary>
    /// <param name="x">First number</param>
    /// <param name="y">Second number</param>
    /// <returns>The product of x and y</returns>
    public static int Multiply(int x, int y)
    {
        return x * y;
    }

    static void Main()
    {
        // Define two integers
        int a = 5;
        int b = 10;

        // Multiply the numbers and print the result
        int result = Multiply(a, b);
        Console.WriteLine(result); // Output: 50
    }
}
```