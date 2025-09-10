---
Created: 2025-08-07T20:10
tags:
  - Advance-Concepts
---
**Lambda expressions** are anonymous functions used to create delegates or expression tree types. They simplify writing inline functions in a concise, readable way.

---

## 📌 Syntax

```C#
(parameters) => expression

// or with a block body
(parameters) => {
    // statements
    return result;
}
```

---

## ✅ Examples

```C#
x => x * x             // Single parameter
(x, y) => x + y        // Multiple parameters
() => Console.WriteLine("Hi") // No parameters
```

---

## 🧠 Where You Use Lambdas

|Usage|Example|
|---|---|
|Delegate|`Func<int, int> square = x => x * x;`|
|LINQ|`list.Where(x => x > 5);`|
|Event handlers|`button.Click += (s, e) => { ... };`|
|Anonymous methods|Replacing `delegate` with lambda|
|Threading/async|`Task.Run(() => DoSomething());`|

---

## 🔹 With Delegates

```C#
public delegate int Operation(int a, int b);

Operation add = (a, b) => a + b;
Console.WriteLine(add(2, 3)); // 5
```

---

## 🔸 With `Func`, `Action`, `Predicate`

|Type|Purpose|Example|
|---|---|---|
|`Func<T>`|Returns a value|`Func<int, int> square = x => x * x;`|
|`Action<T>`|Returns void|`Action<string> print = s => Console.WriteLine(s);`|
|`Predicate<T>`|Returns bool|`Predicate<int> isEven = x => x % 2 == 0;`|

---

## 🌈 Lambda with LINQ

```C#
var evenNumbers = list.Where(x => x % 2 == 0);
var squares = list.Select(x => x * x);
```

---

## 🚀 Advanced Example with Block Body

```C#
Func<int, int, int> add = (x, y) =>
{
    int sum = x + y;
    return sum;
};
```

---

## 🔐 Closures

Lambdas can capture and use outer scope variables:

```C#
int factor = 5;
Func<int, int> multiply = x => x * factor;
Console.WriteLine(multiply(2)); // 10
```

---

## ⚠️ Gotchas

|**Issue**|**Explanation**|
|---|---|
|Capturing loop variable|Use local copy inside loop|
|Can't use ref/out|Not allowed in lambda parameters|
|Debugging is harder|Use clear names or extract to named method|
|Lambdas can't contain goto, break, or continue (in most cases)|Control flow keywords are generally restricted; use regular loops or methods instead|
|Limited to expressions (for expression-bodied lambdas)|Only one expression allowed; use statement-bodied lambdas for complex logic|
|No implicit conversion to delegate type (in some contexts)|May need explicit casting to match delegate signature|
|Cannot have attributes or modifiers|Lambdas can't have access modifiers, attributes, or unsafe modifiers|
|Can capture more memory than expected|Captured variables are kept alive as closures; be mindful of memory use|
|Exceptions in lambdas may be swallowed (in async)|Use `try/catch` inside lambdas, especially for async/await scenarios|

---

## 📋 Summary Table

|Feature|Example|
|---|---|
|No params|`() => Console.WriteLine("Hi")`|
|One param|`x => x + 1`|
|Multiple params|`(x, y) => x + y`|
|With block body|`x => { var y = x*2; return y; }`|
|Delegate use|`Func<int, int> f = x => x * x;`|
|LINQ use|`list.Where(x => x > 10)`|