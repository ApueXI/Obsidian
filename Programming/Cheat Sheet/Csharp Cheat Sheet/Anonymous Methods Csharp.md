---
Created: 2025-08-07T20:10
tags:
  - Advance-Concepts
---
An **anonymous method** is a method without a name, defined using the `delegate` keyword. It allows inline method definition where a delegate is expected.

Introduced in **C# 2.0**, anonymous methods came **before lambda expressions**, which are more concise.

---

## 📌 Syntax

```C#
delegate(parameterList) {
    // Method body
};
```

You assign it to a delegate variable or pass it directly as a parameter.

---

## ✅ Example

```C#
// Declare delegate
delegate void Greet(string name);

// Assign anonymous method to delegate
Greet greet = delegate(string name) {
    Console.WriteLine("Hello, " + name);
};

greet("Alice"); // Output: Hello, Alice
```

---

## 🔁 Comparison: Anonymous Method vs Lambda Expression

|Feature|Anonymous Method|Lambda Expression|
|---|---|---|
|Syntax|`delegate(params) { ... }`|`(params) => expression`|
|Supports no parameters|✅|✅|
|Can use `goto`, `break`, `continue`|✅|❌|
|Readability|Verbose|Concise|
|Closures|✅ Captures outer variables|✅ Same|

---

## 🧠 Use Cases

- **Event handlers**
- **Inline callbacks**
- When you want **more control** than lambdas (like using `break` or `goto` inside)
- Before C# 3.0 (legacy code)

---

## 🔹 With Delegates

```C#
Action<int> printSquare = delegate(int x) {
    Console.WriteLine(x * x);
};

printSquare(5); // 25
```

---

## 🔸 With Events

```C#
button.Click += delegate(object sender, EventArgs e) {
    Console.WriteLine("Button clicked!");
};
```

---

## 📋 Real-World Example: Sorting with Custom Comparison

```C#
List<string> names = new List<string> { "John", "Anna", "Bob" };

names.Sort(delegate(string x, string y) {
    return x.Length.CompareTo(y.Length);
});
```

---

## ⚠️ Gotchas

|Issue|Note|
|---|---|
|Harder to read|Compared to lambdas for short functions|
|Can't use outside method name|No reuse unless extracted|
|Less common today|Lambdas are preferred in most cases|

---

## 📋 Summary Table

|Task|Syntax Example|
|---|---|
|No parameters|`delegate { Console.WriteLine("Hi"); };`|
|With parameters|`delegate(int x) { return x + 1; };`|
|With return value|`Func<int, int> f = delegate(int x) { return x * x; };`|
|In event handler|`event += delegate(object s, EventArgs e) { ... };`|

---

## ✅ Quick Recap

- **Use** `**delegate**` **keyword** for anonymous methods.
- Can **access outer variables (closure)**.
- Still used where **lambda limitations apply**.
- Prefer **lambdas** for short, clean expressions.