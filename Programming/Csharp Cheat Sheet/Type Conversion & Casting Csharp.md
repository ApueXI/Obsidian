---
Created: 2025-08-07T20:20
tags:
  - Basics-&-Syntax
---
## 🔹 1. **Implicit Conversion (Safe, Automatic)**

- Automatically done by the compiler.
- Happens when there is **no risk of data loss**.
- Between compatible types (e.g., `int` to `double`).

```C#
int x = 100;
double y = x;  // Implicit conversion: int → double
```

✅ Safe because `double` can hold all `int` values.

---

## 🔹 2. **Explicit Conversion (Casting, Risky)**

- You must **manually cast** using parentheses.
- Required when there's **potential data loss**.

```C#
double a = 9.8;
int b = (int)a;  // Explicit cast: double → int
Console.WriteLine(b);  // Output: 9 (truncated)
```

⚠️ Precision is **lost**.

---

## 🔹 3. **Using** `**Convert**` **Class (Safe Utility)**

- Converts between many types using **methods**.

```C#
string input = "123";
int num = Convert.ToInt32(input);
```

✔️ Handles **nulls** and **format exceptions** better than direct casts.

---

## 🔹 4. **Using** `**Parse()**` **and** `**TryParse()**`

### 🔸 `Parse()` (Risky if input is invalid)

```C#
int value = int.Parse("100");
```

### 🔸 `TryParse()` (Safe)

```C#
string text = "100";
int number;
bool success = int.TryParse(text, out number);
```

✅ Prevents crashes by returning a **boolean**.

---

## 🔹 5. **Boxing & Unboxing**

Used to convert between **value types** and **object types**.

```C#
int x = 42;
object obj = x;       // Boxing
int y = (int)obj;     // Unboxing
```

📦 Boxing puts a value type in an object wrapper.

---

## 🧠 Gotchas

|Issue|Explanation|
|---|---|
|Casting invalid string → crash|`"abc"` to `int.Parse()` → runtime error|
|Precision loss in float → int|`(int)5.99` = `5`, not `6`|
|Use TryParse for user input|Always safer than `Parse()`|
|Casting between unrelated types|Invalid and causes exceptions|
|Overflow|Casting large `long` to `int` may overflow silently|

---

## 📋 Summary Table

|Conversion Type|Method|Risk|Use When|
|---|---|---|---|
|Implicit|`int → double`|Low|No data loss|
|Explicit (cast)|`(int)doubleVar`|Medium|Data loss possible|
|`Convert` class|`Convert.ToInt32()`|Low/Medium|Works with nulls, strings|
|`Parse()`|`int.Parse("123")`|High|Fast but fails on bad input|
|`TryParse()`|`int.TryParse()`|None|Safest way to parse user input|
|Boxing/Unboxing|`object ↔ int`|Low|Needed when working with `object`|

---

## 🌍 Real-World Example

```C#
using System;

class Program
{
    static void Main()
    {
        string input = "85.5";
        double grade;

        if (double.TryParse(input, out grade))
        {
            int roundedGrade = (int)grade;  // explicit cast
            Console.WriteLine($"Original: {grade}, Rounded: {roundedGrade}");
        }
        else
        {
            Console.WriteLine("Invalid input.");
        }
    }
}
```

**Output:**

```Plain
Original: 85.5, Rounded: 85
```