---
Created: 2025-08-07T20:10
tags:
  - Exception-Handling
---
## ✅ What is `throw`?

- Used to **manually raise (throw) an exception** during program execution.
- Forces an error condition, which can be caught by surrounding `try-catch` blocks or propagate up the call stack.

---

## 🧠 Syntax

```C#
throw new ExceptionType("Error message");
```

Example:

```C#
throw new ArgumentException("Invalid argument");
```

You can throw any exception that derives from `System.Exception`.

---

## 🧾 Usage Examples

### 1. Throwing a new exception:

```C#
if (age < 0)
{
    throw new ArgumentOutOfRangeException(nameof(age), "Age cannot be negative.");
}
```

### 2. Re-throwing caught exception:

Inside a `catch` block, to preserve stack trace:

```C#
catch (Exception)
{
    // Log or do something
    throw;  // Re-throw the same exception
}
```

**Important:** Use just `throw;` (without argument) to preserve the original stack trace.

---

## ⚠️ Common Mistakes

|Mistake|Explanation|
|---|---|
|`throw ex;` in catch|Resets stack trace — avoid doing this|
|Throwing non-exception|Only objects derived from `Exception` can be thrown|
|Throwing without message|Makes debugging harder; always provide a message|

---

## 🧪 Example with Validation

```C#
public void SetScore(int score)
{
    if (score < 0 || score > 100)
    {
        throw new ArgumentOutOfRangeException(nameof(score), "Score must be between 0 and 100.");
    }
    // Set the score
}
```

---

## 📋 Summary Table

|Use Case|Syntax|Notes|
|---|---|---|
|Throw new exception|`throw new ExceptionType("msg")`|Create & throw a new exception|
|Re-throw caught exc.|`throw;`|Preserve original stack trace|
|Throw in validation|`if(...) throw ...;`|Enforce method parameter rules|

---

## 🧠 Pro Tips

- Create custom exceptions by extending `Exception`.
- Use `throw` to fail fast — catch issues early and clearly.
- Combine with `try-catch` for robust error handling.