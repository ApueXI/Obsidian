---
Created: 2025-08-07T20:10
tags:
  - Control-Flow
---
## 🔹 1. **Basic Syntax**

```C#
while (condition)
{
    // Code to repeat
}
```

### 🔸 Example:

```C#
int i = 0;
while (i < 5)
{
    Console.WriteLine(i);
    i++;
}
```

**Output:**

```Plain
0
1
2
3
4
```

---

## 🔹 2. **Key Characteristics**

|Feature|Description|
|---|---|
|Entry-controlled|Condition is checked **before** each loop|
|May not run|If the condition is initially false|
|Requires manual update|You must increment/decrement inside|

---

## 🔹 3. **Infinite Loop (intentional or bug)**

```C#
while (true)
{
    Console.WriteLine("This runs forever!");
    // Use break or return to exit
}
```

---

## 🔹 4. **Using** `**break**` **and** `**continue**`

### 🔸 Exit Early:

```C#
while (true)
{
    string input = Console.ReadLine();
    if (input == "exit") break;
    Console.WriteLine("You typed: " + input);
}
```

### 🔸 Skip Iteration:

```C#
int i = 0;
while (i < 5)
{
    i++;
    if (i == 3) continue;
    Console.WriteLine(i);
}
```

**Output:** `1 2 4 5`

---

## 🧠 Gotchas

|Issue|Explanation|
|---|---|
|Forgetting to update|Causes infinite loops|
|Bad condition logic|Loop might never run or run forever|
|Missing braces `{}`|Only the next line is considered part of the loop|
|Using assignment `=` instead of comparison `==`|Common logic bug|

---

## 📋 Summary Table

|Element|Example|Description|
|---|---|---|
|Condition|`i < 5`|Checked before each loop|
|Break|`break;`|Exits loop immediately|
|Continue|`continue;`|Skips rest of current iteration|
|Infinite|`while (true)`|Useful for repeated input until stop|

---

## 🌍 Real-World Example: Password Prompt

```C#
string password = "";
while (password != "secret")
{
    Console.Write("Enter password: ");
    password = Console.ReadLine();
}
Console.WriteLine("Access granted.");
```

---

## 🔄 Bonus: `while` for Validation

```C#
int age;
bool valid = false;

while (!valid)
{
    Console.Write("Enter your age: ");
    if (int.TryParse(Console.ReadLine(), out age) && age > 0)
    {
        valid = true;
    }
    else
    {
        Console.WriteLine("Invalid input. Try again.");
    }
}
Console.WriteLine($"You entered: {age}");
```