---
Created: 2025-08-07T20:10
tags:
  - String-Manipulation
---
## ✅ What is String Interpolation?

String interpolation allows you to embed **variables**, **expressions**, and **formatted values** directly into strings using `$"..."`.

```C#
string name = "Alex";
Console.WriteLine($"Hello, {name}!");
// Output: Hello, Alex!
```

---

## 🧠 Basic Syntax

```C#
$"literal {expression} literal"
```

✅ Anything inside `{}` is treated as C# code (variables, method calls, calculations, etc.).

```C#
int age = 20;
Console.WriteLine($"Next year, you’ll be {age + 1} years old.");
```

---

## 🧾 Formatting Output (Dates, Numbers, Alignment)

### Numbers

```C#
double price = 1234.5;
Console.WriteLine($"Price: {price:C}"); // Currency: Price: ₱1,234.50 (locale-based)
Console.WriteLine($"Value: {price:N2}"); // Number: Value: 1,234.50
```

### Dates

```C#
DateTime today = DateTime.Now;
Console.WriteLine($"Today is {today:MMMM dd, yyyy}");  // August 01, 2025
```

### Alignment

```C#
Console.WriteLine($"|{"Item",-10}|{"Qty",5}|");
// Left-align Item, right-align Qty
```

---

## 🔄 Nesting Expressions

```C#
Console.WriteLine($"2 + 3 = {2 + 3}");  // 2 + 3 = 5
Console.WriteLine($"Upper: {"word".ToUpper()}");  // WORD
```

---

## 📦 Escaping `{` and `}`

Use double braces `{{` and `}}` to print literal `{` or `}`.

```C#
CopyEdit
Console.WriteLine($"{{This is not code}}");
// Output: {This is not code}
```

---

## 🆚 Interpolation vs Concatenation

|Approach|Example|
|---|---|
|Interpolation|`$"Name: {name}"`|
|Concatenation|`"Name: " + name`|
|`string.Format()`|`string.Format("Name: {0}", name)`|

✅ Interpolation is cleaner and safer (especially for formatting).

---

## 🧪 Real-World Example

```C#
string name = "Ella";
int score = 98;
Console.WriteLine($"Student: {name,-10} | Score: {score,3}");
```

**Output:**

```Plain
Student: Ella       | Score:  98
```

---

## 📋 Summary Table

|Feature|Syntax/Example|
|---|---|
|Basic variable|`$"Hi {name}!"`|
|Expression|`$"Sum: {2 + 3}"`|
|Format number|`$"{price:C}"`|
|Format date|`$"{date:MMMM dd}"`|
|Alignment|`$"{value,5}"` or `$"{value,-5}"`|
|Escape `{}`|`$"{{escaped}}"`|

---

## 🧠 Pro Tips

- Interpolation can span multiple lines with `@`:

```C#
Console.WriteLine($@"Hello {name},
Your balance is {balance:C}.");
```

- Great for **logging**, **templates**, **tables**, and **emails**.