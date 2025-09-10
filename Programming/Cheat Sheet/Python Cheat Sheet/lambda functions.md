---
Created: 2025-08-21T19:29
tags:
  - Functional-Programming-Features
---
## ✅ **What is a Lambda Function?**

A **lambda function** is a small, anonymous function defined with the `lambda` keyword.

✔️ **Key traits:**

- **Anonymous** (no formal name unless assigned)
- **Single expression only** (no multiple statements)
- **Can return a value implicitly**

---

## 🏗 **Basic Syntax**

```Python
lambda arguments: expression
```

Equivalent to:

```Python
def func(arguments):
    return expression
```

---

## 🔹 **Examples**

```Python
add = lambda x, y: x + y
print(add(2, 3))  # 5

square = lambda n: n ** 2
print(square(4))  # 16

no_args = lambda: "Hello"
print(no_args())  # Hello
```

---

## 🧰 **When to Use Lambda Functions**

- **Quick, throwaway functions**
- As **arguments to higher-order functions** like `map`, `filter`, `sorted`
- To **inline small computations**

---

## ✅ **Common Uses**

🔹 **With** `**map()**`

```Python
nums = [1, 2, 3]
print(list(map(lambda x: x * 2, nums)))  # [2, 4, 6]
```

🔹 **With** `**filter()**`

```Python
nums = [1, 2, 3, 4]
print(list(filter(lambda x: x % 2 == 0, nums)))  # [2, 4]
```

🔹 **With** `**sorted()**`

```Python
words = ["apple", "banana", "kiwi"]
print(sorted(words, key=lambda w: len(w)))  # ['kiwi', 'apple', 'banana']
```

---

## ⚠️ **Gotchas**

❌ **Only one expression**

- Cannot have multiple statements or assignments.
    
    ✅ Use a `def` function if logic is complex.
    

❌ **Harder to debug**

- No proper name in stack traces.

---

## 🏎 **Lambda vs. def**

|Feature|lambda|def|
|---|---|---|
|Anonymous?|✅ Yes|❌ No|
|Multiple lines?|❌ No|✅ Yes|
|Readability|✅ Good for short|✅ Better for complex|
|Best use case|Inline short funcs|Full reusable funcs|

---

## 📌 **Summary Table**

|Concept|Quick Notes|
|---|---|
|**Definition**|Small anonymous function|
|**Syntax**|`lambda args: expression`|
|**Returns**|Implicitly returns the expression|
|**Best for**|Quick one-liners, map/filter/sorted|
|**Limitations**|Single expression only|

---

## 🌍 **Real-World Example: Sorting JSON-like Data**

Imagine you have a list of dictionaries and want to sort by a specific key:

```Python
users = [
    {"name": "Alice", "age": 30},
    {"name": "Bob", "age": 25},
    {"name": "Charlie", "age": 35}
]

# Sort by age using a lambda
sorted_users = sorted(users, key=lambda u: u["age"])

print(sorted_users)
# [{'name': 'Bob', 'age': 25},
#  {'name': 'Alice', 'age': 30},
#  {'name': 'Charlie', 'age': 35}]
```

👉 **Why lambda?**

- Quick, inline way to define a sorting rule without writing a full `def get_age(user): return user["age"]`.

---

✅ **TL;DR:**

Use **lambda functions** for short, throwaway functions. For anything more complex → **use** `**def**`.