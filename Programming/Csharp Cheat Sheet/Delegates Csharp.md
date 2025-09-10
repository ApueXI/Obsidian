---
Created: 2025-08-07T20:10
tags:
  - Advance-Concepts
---
**Delegates** are _type-safe pointers to methods_. They allow methods to be assigned to variables and passed around.

---

## 🧱 Basic Syntax

```C#
// Step 1: Declare a delegate
public delegate void MyDelegate(string message);

// Step 2: Create a method that matches the delegate signature
public void ShowMessage(string message)
{
    Console.WriteLine(message);
}

// Step 3: Assign method to delegate and invoke
MyDelegate del = ShowMessage;
del("Hello from delegate!");
```

---

## 🎯 Why Use Delegates?

- To pass methods as parameters
- To implement **event-driven** programming
- To create **callbacks** and **plugin systems**
- To **decouple** method invocation from method definition

---

## 🔄 Multicast Delegates

A delegate can point to **multiple methods** using `+=`.

```C#
MyDelegate del = Method1;
del += Method2;
del("Test"); // Calls Method1, then Method2
```

---

## 📌 Delegate with Return Values

Return value will be from the **last** method in the invocation list.

```C#
public delegate int MathOperation(int a, int b);

int Add(int a, int b) => a + b;
int Multiply(int a, int b) => a * b;

MathOperation op = Add;
op += Multiply;

int result = op(2, 3); // result = 6 (from Multiply)
```

---

## 📋 Anonymous Methods (C# 2.0+)

```C#
MyDelegate del = delegate(string msg)
{
    Console.WriteLine("Anon: " + msg);
};
del("Test");
```

---

## 🧠 Lambda Expressions (C# 3.0+)

```C#
MyDelegate del = msg => Console.WriteLine("Lambda: " + msg);
del("Hi");
```

---

## 🧪 Delegates as Parameters

```C#
public void Execute(MyDelegate del)
{
    del("Running delegate...");
}
```

---

## 🧰 Real-World Example: Filtering List

```C#
public delegate bool Filter(int x);

List<int> FilterList(List<int> nums, Filter f)
{
    return nums.Where(n => f(n)).ToList();
}
```

Usage:

```C#
Filter isEven = x => x % 2 == 0;
var result = FilterList(new List<int> {1, 2, 3, 4}, isEven); // [2, 4]
```

---

## 🎉 Built-in Delegates

|Delegate|Parameters|Return|
|---|---|---|
|`Action<T>`|Yes|void|
|`Func<T>`|Yes|Yes|
|`Predicate<T>`|One `T`|bool|

```C#
Action<string> say = Console.WriteLine;
Func<int, int, int> add = (a, b) => a + b;
Predicate<int> isEven = x => x % 2 == 0;
```

---

## 🎈 Events Use Delegates

```C#
public delegate void Notify();
public event Notify OnComplete;
```

---

## ⚠️ Gotchas

|Problem|Fix/Tip|
|---|---|
|Mismatched method signature|Method must exactly match delegate signature|
|Exceptions in multicast|All methods still run; only last return is kept|
|Multiple delegates|Use `-=` to remove a method from delegate chain|

---

## ✅ Summary Table

|Feature|Description|
|---|---|
|Delegate Declaration|`delegate returnType Name(params)`|
|Assignment|`DelegateName d = MethodName;`|
|Invocation|`d(args);`|
|Multicast|`d += AnotherMethod;`|
|Built-in Types|`Action`, `Func`, `Predicate`|
|Anonymous|`delegate { ... }`|
|Lambda|`x => x * x`|
|Use Cases|Callbacks, events, LINQ, strategy pattern|