---
Created: 2025-08-07T20:10
tags:
  - Methods-(Functions)
---
## ✅ Concept

- A **method** is a block of code that performs a task.
- **Declaration** defines the method’s name, return type, parameters, and body.
- **Calling (invoking)** runs the method and optionally receives a return value.

---

## 🧠 Syntax

### Method Declaration

```C#
[access_modifier] return_type MethodName([parameter_list])
{
    // Method body (code to execute)
}
```

- `access_modifier`: `public`, `private`, `protected`, `internal` (optional; default is `private`).
- `return_type`: Data type returned (`void` if no return value).
- `MethodName`: Identifier for the method.
- `parameter_list`: Comma-separated parameters with type and name (optional).
- Curly braces `{}` contain the method code.

---

### Method Calling

```C#
MethodName(argument_list);
```

- Pass arguments matching the parameters.
- If method returns a value, you can assign or use it.

---

## 🔄 Examples

### 1. Void method (no return)

```C#
public void Greet(string name)
{
    Console.WriteLine($"Hello, {name}!");
}

// Calling
Greet("Alice");
```

---

### 2. Method with return value

```C#
public int Add(int a, int b)
{
    return a + b;
}

// Calling
int sum = Add(5, 3);
Console.WriteLine(sum);  // Output: 8
```

---

### 3. Method with multiple parameters

```C#
public double CalculateArea(double width, double height)
{
    return width * height;
}

// Calling
double area = CalculateArea(5.5, 3.2);
Console.WriteLine(area);  // Output: 17.6
```

---

## ⚠️ Common Gotchas

|Gotcha|Explanation|
|---|---|
|Parameter mismatch|Argument types/count must match parameter list.|
|Return type missing|If method returns a value, must include `return`.|
|Overloading rules|Method names can be same with different parameters.|
|Void methods cannot return a value|`return;` only allowed (no expression).|

---

## 📋 Quick Reference Table

|Part|Example|Notes|
|---|---|---|
|Access modifier|`public`, `private`|Controls visibility|
|Return type|`void`, `int`, `string`|`void` means no return|
|Method name|`CalculateArea`|Must follow naming rules|
|Parameter list|`(int a, int b)`|Optional, can be empty|
|Return statement|`return a + b;`|Required if non-void|
|Calling syntax|`CalculateArea(3, 4);`|Use arguments matching parameters|

---

## 🧠 Extra Tips

- **Optional parameters** with default values:
    
    ```C#
    public void Log(string message, int level = 1)
    {
        Console.WriteLine($"Level {level}: {message}");
    }
    
    Log("Warning");        // level defaults to 1
    Log("Error", 3);       // level is 3
    ```
    
- **Named arguments** for clarity:
    
    ```C#
    CalculateArea(width: 5, height: 10);
    ```
    
- **Method overloading** (same name, different parameters):
    
    ```C#
    public void Print(int number) { ... }
    public void Print(string text) { ... }
    ```