---
Created: 2025-08-07T20:10
tags:
  - Methods-(Functions)
---
## ✅ Concept

**Parameters** let you pass data into methods. They act as **variables defined in the method signature**. You can pass values when calling the method — and in some cases, even get values back out.

---

## 🧠 Basic Syntax

### Method with Parameters

```C#
public void Greet(string name, int age)
{
    Console.WriteLine($"Hello {name}, you are {age} years old.");
}
```

### Calling the Method

```C#
Greet("Alice", 30);
```

---

## 🔢 Parameter Types (Detailed)

|Type|Keyword|Description|
|---|---|---|
|Value|_(none)_|Default; copies the argument (primitive types).|
|Reference|`ref`|Passes **reference** to variable; must be initialized before calling.|
|Output|`out`|Returns **data from method** via parameter; must be assigned in method.|
|Params array|`params`|Accepts a **variable number** of arguments as an array.|
|Optional|`=`|Parameters with **default values** (can be skipped during method call).|
|Named|_(none)_|Specify parameters **by name** during method call for clarity/flexibility.|

---

## 🧪 Examples of Special Parameter Types

### 1. `ref` (read and write to caller's variable)

```C#
void Double(ref int x)
{
    x *= 2;
}

int num = 5;
Double(ref num);
Console.WriteLine(num); // Output: 10
```

---

### 2. `out` (method gives value back)

```C#
bool TryParseInt(string input, out int result)
{
    return int.TryParse(input, out result);
}

int number;
if (TryParseInt("123", out number))
    Console.WriteLine(number); // Output: 123
```

---

### 3. `params` (variable number of arguments)

```C#
void Sum(params int[] numbers)
{
    int total = 0;
    foreach (var n in numbers) total += n;
    Console.WriteLine($"Sum: {total}");
}

Sum(1, 2, 3, 4); // Output: Sum: 10
```

---

### 4. Optional Parameters

```C#
void Print(string message = "Hello", int times = 1)
{
    for (int i = 0; i < times; i++)
        Console.WriteLine(message);
}

Print();           // Uses default values
Print("Hi", 3);    // Overrides both
```

---

### 5. Named Parameters

```C#
Print(times: 2, message: "C# is fun");
```

✔️ You can **reorder arguments** when using named parameters.

---

## 📋 Quick Reference Table

|Modifier|Can be skipped?|Must initialize before call?|Must assign inside method?|
|---|---|---|---|
|Regular|❌|✅|❌|
|`ref`|❌|✅|❌|
|`out`|❌|❌|✅|
|`params`|✅|✅|❌|
|Optional|✅|✅ (default exists)|❌|

---

## ⚠️ Gotchas

|Gotcha|Explanation|
|---|---|
|❌ `ref` and `out` must be used both in method **and** call.|When using `ref` or `out`, you must specify them in both the method signature **and** at the call site, or you'll get a compile-time error.|
|🧠 `params` must be the **last** parameter.|The `params` keyword allows variable-length arguments, but it must always appear as the **last** parameter in the method signature. Otherwise, you'll get a compiler error.|
|❓ Ambiguity with optional + overloads is possible.|Using optional parameters alongside method overloading can confuse the compiler, leading to ambiguous calls that result in compilation errors.|
|💥 `ref` and `out` can't be used with `async`/`await` methods.|`ref` and `out` require synchronous, immediate assignment. Since `async` methods execute asynchronously, they can't use `ref` or `out` due to undefined timing of the value assignment.|