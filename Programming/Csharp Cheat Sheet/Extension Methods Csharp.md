---
Created: 2025-08-07T20:10
tags:
  - Advance-Concepts
---
## ✅ What is an Extension Method?

An **extension method** allows you to **"add" methods to existing types** (like `string`, `int`, or even your own classes) **without modifying their source code**.

It’s a **static method** defined in a **static class**, using the `this` keyword in the first parameter to specify which type it extends.

---

## 🧱 Syntax

```C#
public static class ExtensionClass
{
    public static returnType MethodName(this Type typeName, ...)
    {
        // logic
    }
}
```

### 🧪 Example

```C#
public static class StringExtensions
{
    public static bool IsCapitalized(this string str)
    {
        return !string.IsNullOrEmpty(str) && char.IsUpper(str[0]);
    }
}
```

### ✅ Usage

```C#
string name = "Nein";
bool result = name.IsCapitalized(); // true
```

---

## 🧠 Key Concepts

|Feature|Detail|
|---|---|
|Defined in|Static class|
|Method|Static, with `this` modifier on first parameter|
|Invoked like|Instance method: `obj.ExtensionMethod()`|
|Extends|Can extend any **non-sealed** class or interface|
|Use cases|Add methods to system types or third-party types without access|

---

## 📌 Real-World Examples

### 🔹 Example 1: String Extension

```C#
public static bool IsNullOrWhiteSpace(this string str)
    => string.IsNullOrWhiteSpace(str);
```

### 🔹 Example 2: Int Extension

```C#
public static bool IsEven(this int value)
    => value % 2 == 0;
```

### 🔹 Example 3: Custom Object Extension

```C#
public class Person { public string Name; }

public static class PersonExtensions
{
    public static void Greet(this Person person)
        => Console.WriteLine($"Hello, {person.Name}!");
}
```

---

## ⚠️ Gotchas

|Issue|Details|
|---|---|
|Must be in a **static class**|Or compiler will throw an error|
|First param must use `this`|This tells the compiler you're extending the type|
|Can't override instance methods|Extension methods can't replace existing instance methods|
|IntelliSense priority|Instance methods take precedence over extension methods|
|Must import namespace|You must `using` the namespace where the extension is defined|

---

## 📋 Summary Table

|Part|Syntax / Example|
|---|---|
|Declare class|`public static class MyExtensions { ... }`|
|Declare method|`public static bool IsEven(this int x) => x % 2 == 0;`|
|Usage|`5.IsEven();`|
|Works with|`string`, `int`, custom classes, interfaces, etc.|
|Can't be|Used on sealed types like `System.String` **internally**|
|Namespace needed|`using MyExtensionsNamespace;`|

---

## 🧪 Extension Methods with LINQ

LINQ uses extension methods extensively:

```C#
var evenNumbers = list.Where(x => x % 2 == 0).ToList();
```

- `Where()`, `Select()`, `ToList()`, etc. are all **extension methods** on `IEnumerable<T>`.

---

## 🔚 Conclusion

Extension methods:

- Make code **cleaner** and **more readable**
- Allow you to "add" features to existing types
- Power **LINQ**, **fluent APIs**, and **reusable utilities**