---
Created: 2025-08-07T20:10
tags:
  - Methods-(Functions)
---
## ✅ Concept

A **return type** in a method defines the **type of value** that the method gives back to its caller. It appears **before the method name** in the declaration.

---

## 🧠 Basic Syntax

```C#
return_type MethodName(parameters)
{
    // ...
    return value;
}
```

Example:

```C#
int Square(int number)
{
    return number * number;
}
```

---

## 📋 Common Return Types

|Return Type|Description|Example Value|
|---|---|---|
|`void`|No return value|_(no `return value`)_|
|`int`, `double`, `bool`, etc.|Return a basic value type|`return 42;`|
|`string`, `object`|Return reference types|`return "Hello";`|
|Class types|Return an instance of a class|`return new Car();`|
|`Tuple`|Return multiple values in one|`return (1, "OK");`|
|`Task`|Async method with no result (`void`-like)|`return Task.CompletedTask;`|
|`Task<T>`|Async method that returns value|`return Task.FromResult(42);`|
|`ref` / `ref readonly`|Return a **reference** to a variable (advanced)|`ref int GetRef() {...}`|

---

## ✅ `void` Return Type

```C#
void Greet(string name)
{
    Console.WriteLine($"Hello, {name}");
}
```

✔️ No return statement is needed (unless it's just `return;` to exit early).

---

## ✅ Returning Value Types

```C#
bool IsEven(int number)
{
    return number % 2 == 0;
}
```

✔️ You **must** return a value matching the declared type.

---

## ✅ Returning Reference Types

```C#
string GetGreeting()
{
    return "Welcome!";
}
```

---

## ✅ Returning a Class or Object

```C#
Person CreatePerson(string name, int age)
{
    return new Person { Name = name, Age = age };
}
```

---

## ✅ Returning Tuples

```C#
(string name, int age) GetUser()
{
    return ("Alice", 25);
}
```

✔️ Access like: `var (name, age) = GetUser();`

---

## ✅ Async Return Types (`Task`, `Task<T>`)

```C#
async Task DelayMessage()
{
    await Task.Delay(1000);
    Console.WriteLine("Done!");
}

async Task<int> GetDataAsync()
{
    await Task.Delay(500);
    return 42;
}
```

---

## ✅ Returning `ref` Values (Advanced)

```C#
ref int FindRef(int[] array, int value)
{
    for (int i = 0; i < array.Length; i++)
        if (array[i] == value)
            return ref array[i];
    throw new Exception("Not found");
}
```

✔️ Must be used with `ref` on both declaration and call:

```C#
ref int item = ref FindRef(arr, 10);
item = 99;  // Modifies the original array
```

---

## 🧱 Gotchas

|Gotcha|Explanation|
|---|---|
|❌ Return type mismatch|Return value must exactly match the method’s return type.|
|❌ Missing return|All code paths in non-void methods must return a value.|
|🧠 `return` ends method|Any code after a `return` is **unreachable**.|
|⚠️ Don't confuse `void` with `Task`|`void` is for sync; `Task` is async equivalent.|

---

## 📌 Quick Reference Summary

|Type|Use When...|Return Example|
|---|---|---|
|`void`|You don’t need to return anything|`return;` or none|
|`int`, etc.|Returning a single value|`return 5;`|
|`string`, `object`|Returning a reference type|`return "text";`|
|`ClassName`|Returning an object instance|`return new User();`|
|`(T1, T2)`|Returning multiple values|`return ("OK", 200);`|
|`Task`|Async method without result|`return Task.Delay(500);`|
|`Task<T>`|Async method with result|`return Task.FromResult(1);`|
|`ref T`|Return reference to variable (advanced)|`ref int val = ref Get();`|