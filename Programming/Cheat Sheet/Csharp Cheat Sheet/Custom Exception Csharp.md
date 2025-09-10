---
Created: 2025-08-07T20:44
tags:
  - Exception-Handling
---
## ✅ Why create custom exceptions?

- To provide **meaningful error types** specific to your application/domain.
- Easier to **catch and handle** distinct error conditions.
- Improves code readability and debugging.

---

## 🧠 How to Create a Custom Exception Class

- Derive from `System.Exception` (or a more specific subclass like `ApplicationException`).
- Implement standard constructors to support serialization and messages.

```C#
using System;

public class MyCustomException : Exception
{
    public MyCustomException() { }

    public MyCustomException(string message) : base(message) { }

    public MyCustomException(string message, Exception inner) : base(message, inner) { }

    // Optional: support for serialization
    protected MyCustomException(System.Runtime.Serialization.SerializationInfo info,
                              System.Runtime.Serialization.StreamingContext context)
        : base(info, context) { }
}
```

---

## 🧪 Throwing Your Custom Exception

```C#
if (balance < 0)
{
    throw new MyCustomException("Balance cannot be negative!");
}
```

---

## 🔄 Catching Your Custom Exception

```C#
try
{
    // Code that may throw MyCustomException
}
catch (MyCustomException ex)
{
    Console.WriteLine("Custom error: " + ex.Message);
}
```

---

## 📋 Summary Table

|Step|Code Example|
|---|---|
|Define custom exception|`class MyException : Exception { ... }`|
|Throw exception|`throw new MyException("Error!");`|
|Catch exception|`catch (MyException ex) { ... }`|

---

## 🧠 Best Practices

- Name exception classes with **“Exception”** suffix.
- Include **meaningful messages**.
- Consider adding **custom properties** to hold extra info if needed.
- Support serialization if your app requires it (e.g., remoting).

---

## 🧰 Real-World Example: Validation Exception

```C#
public class ValidationException : Exception
{
    public string PropertyName { get; }

    public ValidationException(string propertyName, string message)
        : base(message)
    {
        PropertyName = propertyName;
    }
}

// Usage
if (string.IsNullOrEmpty(name))
{
    throw new ValidationException("Name", "Name cannot be empty.");
}
```