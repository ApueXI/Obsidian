---
Created: 2025-08-07T20:10
tags:
  - Advance-Concepts
---
These are **built-in generic delegates** in C#. Instead of declaring custom delegates, you can use these to simplify your code.

---

## 📌 `Func<>` — Returns a Value

### ✅ Syntax

```C#
Func<param1, param2, ..., returnType> name = (params) => expression;
```

- Must **return** a value.
- Last type in angle brackets is the **return type**.

### 🔹 Examples

```C#
Func<int> getNumber = () => 42;
Func<int, int> square = x => x * x;
Func<int, int, int> add = (x, y) => x + y;
```

---

## 📌 `Action<>` — Returns **void**

### ✅ Syntax

```C#
Action<param1, param2, ...> name = (params) => 
{ 
// code 
};
```

- Returns **no value (void)**.
- Used when **only side effects** are needed.

### 🔹 Examples

```C#
Action greet = () => Console.WriteLine("Hello");
Action<string> say = name => Console.WriteLine($"Hi, {name}");
Action<int, int> logSum = (x, y) => Console.WriteLine(x + y);
```

---

## 🔁 `Predicate<T>` — Special Case

- Shortcut for `Func<T, bool>`

```C#
Predicate<int> isEven = x => x % 2 == 0;
```

---

## ✅ Real-World Use Cases

|Scenario|Delegate to Use|Example|
|---|---|---|
|Return a number|`Func<int>`|`Func<int> random = () => rand.Next(1, 100);`|
|Process two numbers|`Func<int, int, int>`|`(a, b) => a * b`|
|Logging a message|`Action<string>`|`(msg) => Console.WriteLine(msg)`|
|Loop with condition|`Predicate<int>`|`list.Find(isEven)`|

---

## 🧪 With LINQ

```C#
List<int> numbers = new List<int> { 1, 2, 3, 4 };

Func<int, bool> isEven = x => x % 2 == 0;
var evenNumbers = numbers.Where(isEven);  // Uses Func<int, bool>

Action<int> print = x => Console.WriteLine(x);
numbers.ForEach(print);                   // Uses Action<int>
```

---

## 📋 Summary Table

|Delegate Type|Parameters|Returns|Example|
|---|---|---|---|
|`Func<int>`|None|int|`() => 42`|
|`Func<int, int>`|int|int|`x => x * x`|
|`Func<int, int, int>`|int, int|int|`(x, y) => x + y`|
|`Action`|None|void|`() => Console.WriteLine("Hi")`|
|`Action<string>`|string|void|`name => Console.WriteLine(name)`|
|`Predicate<T>`|T|bool|`x => x > 0`|

---

## ⚠️ Gotchas

|Caveat|Explanation|
|---|---|
|`Func<>` must always return a value|Otherwise you'll get a compiler error|
|`Action<>` **never returns** value|Even `return;` is optional|
|Max 16 parameters|`Func<>` and `Action<>` support up to 16 args|
|Easy to confuse with custom delegates|Especially for beginners|