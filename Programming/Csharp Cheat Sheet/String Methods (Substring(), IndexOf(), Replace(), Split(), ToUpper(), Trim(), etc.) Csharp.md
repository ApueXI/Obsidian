---
Created: 2025-08-07T20:10
tags:
  - String-Manipulation
---
✅ All methods are part of the `System.String` class (immutable).

📌 Strings in C# are **0-indexed** and **immutable** (operations return a new string).

---

## 🔠 `Substring(int startIndex[, int length])`

Extracts a portion of the string.

```C#
string text = "Hello World";
string sub = text.Substring(6);      // "World"
string sub2 = text.Substring(0, 5);  // "Hello"
```

⚠️ _Throws `ArgumentOutOfRangeException` if index/length is invalid._

---

## 🔍 `IndexOf(string value)`

Returns the **first index** of a substring, or `-1` if not found.

```C#
string msg = "banana";
int index = msg.IndexOf("na");   // 2
```

---

## 🔄 `Replace(oldValue, newValue)`

Replaces **all occurrences** of a substring.

```C#
string text = "cat bat rat";
string replaced = text.Replace("at", "og");  // "cog bog rog"
```

---

## 🔪 `Split(params char[] separator)`

Splits a string into an array.

```C#
string csv = "apple,banana,carrot";
string[] items = csv.Split(',');  // ["apple", "banana", "carrot"]
```

➡️ You can also split using strings:

```C#
str.Split(new string[] { ", " }, StringSplitOptions.None);
```

---

## 🔼 `ToUpper()` / 🔽 `ToLower()`

Converts to uppercase or lowercase.

```C#
"Hello".ToUpper();  // "HELLO"
"Hello".ToLower();  // "hello"
```

---

## ✂️ `Trim()`, `TrimStart()`, `TrimEnd()`

Removes whitespace (or specified characters) from start/end.

```C#
"  hello  ".Trim();       // "hello"
"!!cool!!".Trim('!');     // "cool"
```

---

## 🔒 `Equals(string)`, `==`

Compares two strings.

```C#
string a = "test";
string b = "test";
bool isEqual = a == b;             // true
bool isSame = a.Equals("Test");    // false (case-sensitive)
```

Use `.Equals(..., StringComparison.OrdinalIgnoreCase)` for **case-insensitive** comparison.

---

## 🔄 `StartsWith()`, `EndsWith()`

```C#
"Notebook".StartsWith("Note");  // true
"Report.doc".EndsWith(".doc");  // true
```

---

## 🎯 `Contains(string)`

Checks if substring exists.

```C#
"chatbot".Contains("bot");  // true
```

---

## 📏 `Length`

Gets number of characters in a string.

```C#
string name = "John";
int len = name.Length;  // 4
```

---

## 📎 Interpolation & Formatting

```C#
string name = "Alex";
int age = 21;

// Interpolation
string message = $"Name: {name}, Age: {age}";

// Formatting
string formatted = string.Format("Name: {0}, Age: {1}", name, age);
```

---

# 🧾 Summary Table

|Method|Example|Purpose|
|---|---|---|
|`Substring()`|`"abc".Substring(1)`|Extract part of string|
|`IndexOf()`|`"hello".IndexOf("l")`|Find index|
|`Replace()`|`"a-b-c".Replace("-", "+")`|Replace text|
|`Split()`|`"a,b,c".Split(',')`|Split into array|
|`ToUpper()`|`"hello".ToUpper()`|All uppercase|
|`ToLower()`|`"HELLO".ToLower()`|All lowercase|
|`Trim()`|`" test ".Trim()`|Remove spaces|
|`Contains()`|`"test123".Contains("123")`|Check substring|
|`StartsWith()`|`"code".StartsWith("co")`|Check prefix|
|`EndsWith()`|`"image.jpg".EndsWith(".jpg")`|Check suffix|
|`Length`|`"abc".Length`|Count of characters|

---

## 🧪 Real-World Example

```C#
string input = "  Email: user@example.com  ";
if (input.Trim().ToLower().Contains("@"))
{
    Console.WriteLine("Valid Email Format");
}
```