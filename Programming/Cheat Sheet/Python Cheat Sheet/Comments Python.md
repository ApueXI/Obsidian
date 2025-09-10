---
Created: 2025-08-21T19:29
tags:
  - Basic-Syntax
---
## ✅ Summary Table

|Comment Type|Syntax Example|When to Use|
|---|---|---|
|**Single-line**|`# This is a comment`|Quick explanations|
|**Inline**|`x = 10 # Store user age`|Small notes after code|
|**Multi-line**|`''' Multiple lines '''`|Longer notes or temporary disable code|
|**Docstring**|`"""Describe function"""`|Document functions, classes, or modules|

---

## ✅ Real-World Example

You’re creating a **bank withdrawal system**:

```Python
# Bank balance in dollars
balance = 1000

# Amount user wants to withdraw
withdraw_amount = 200

# Check if enough balance is available
if withdraw_amount <= balance:
    balance -= withdraw_amount  # Deduct amount
    print("Withdrawal successful!")
else:
    print("Insufficient funds!")  # Not enough balance

"""
This simple program:
1. Checks account balance
2. Deducts withdrawal amount if possible
3. Shows appropriate message
"""
```

✅ **Why comments help here?**

They make it clear **what each step does**, which is useful for future developers or even yourself later.

  

|Topic|Description|Syntax / Example|Notes|
|---|---|---|---|
|Single-line Comment|Used to add short explanations or notes.|`# This is a single-line comment`|Anything after `#` on the line is ignored.|
|Multi-line Comment|Used for longer explanations or temporarily disabling code.|`''' This is a multi-line comment '''` or `""" This is a multi-line comment """`|These are actually multi-line strings often used as comments. Python doesn't have a true multi-line comment.|

---

### Real-World Examples:

**1. Single-line comment example:**

```Python
# Calculate the sum of two numbers
a = 5
b = 3
total = a + b  # sum stored in total variable
print(total)
```

_Use:_ Explain small blocks or lines of code for clarity.

---

**2. Multi-line comment example:**

```Python
'''
This function calculates
the factorial of a number
using recursion.
'''
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n-1)
```

_Use:_ Provide detailed explanations or temporarily disable chunks of code.