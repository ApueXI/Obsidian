---
Created: 2025-08-21T19:29
tags:
  - Math-&-Logic
---
## ✅ **What’s the Difference?**

- **Boolean logic operators (**`**and**`**,** `**or**`**,** `**not**`**)** → work on truth values (`True`/`False`)
- **Bitwise operators (**`**&**`**,** `**|**`**,** `**^**`**,** `**~**`**,** `**<<**`**,** `**>>**`**)** → work on the **bits** of integers

---

## 🏗 **Boolean Logic Operators**

|Operator|Meaning|Example|
|---|---|---|
|`and`|True if **both** are True|`True and False → False`|
|`or`|True if **at least one** is True|`True or False → True`|
|`not`|Negates a boolean|`not True → False`|

### Truth Table

|A|B|`A and B`|`A or B`|`not A`|
|---|---|---|---|---|
|T|T|T|T|F|
|T|F|F|T|F|
|F|T|F|T|T|
|F|F|F|F|T|

---

## 🏗 **Bitwise Operators**

|Operator|Meaning|Example|
|---|---|---|
|`&`|AND → bit is 1 if both bits are 1|`5 & 3 → 1`|
|`|`|OR → bit is 1 if at least one bit is 1|
|`^`|XOR → bit is 1 if bits are different|`5 ^ 3 → 6`|
|`~`|NOT → flips all bits|`~5 → -6`|
|`<<`|Left shift → moves bits left|`5 << 1 → 10`|
|`>>`|Right shift → moves bits right|`5 >> 1 → 2`|

### Binary Breakdown Example

```Plain
  5 → 0b0101
  3 → 0b0011

5 & 3 → 0b0001 → 1
5 | 3 → 0b0111 → 7
5 ^ 3 → 0b0110 → 6
~5    → -(5+1) = -6
```

---

## 🔹 **Mixing Boolean & Bitwise**

⚠️ `and`/`or` work on **truthiness**, while `&`/`|` work on **bits**

```Python
# Boolean
print(True and False)   # False
print(True or False)    # True

# Bitwise
print(6 & 3)  # 2 (110 & 011 → 010)
print(6 | 3)  # 7 (110 | 011 → 111)
```

---

## ✅ **When to Use**

- **Boolean logic** → conditions, control flow (`if`, `while`)
- **Bitwise ops** → low-level flags, masks, cryptography, performance tricks

---

## ⚠️ **Gotchas**

❌ `and`/`or` **short-circuit** (may not evaluate the second operand)

✅ Bitwise ops **always evaluate both**

❌ `~x` is **NOT simple negation** → it’s bitwise inversion (`~5 = -6`)

---

## 🏎 **Boolean vs Bitwise vs Logical NumPy**

| Feature | Boolean (`and/or`) | Bitwise (`&/|`) | NumPy Logical |

|------------------|--------------------|-----------------|---------------|

| Works on | truth values | integer bits | arrays |

| Short-circuits? | ✅ Yes | ❌ No | ❌ No |

| Best for | control flow | masks/flags | vectorized logic |

---

## 📌 **Summary Table**

|Category|Operators|
|---|---|
|**Boolean**|`and`, `or`, `not`|
|**Bitwise**|`&`, `|
|**Use for**|Logic control (boolean) / Bit manipulation (bitwise)|

---

## 🌍 **Real-World Example: Permission Flags**

Imagine a system where **permissions** are stored as bits:

```Plain
READ  = 0b001  # 1
WRITE = 0b010  # 2
EXEC  = 0b100  # 4
```

We can **combine & check permissions** using bitwise ops:

```Python
# Combine permissions
user_perm = READ | WRITE  # 0b011 (3)

# Check if user has WRITE permission
has_write = (user_perm & WRITE) != 0
print(has_write)  # True

# Add EXEC permission
user_perm |= EXEC  # now 0b111 (7)

# Remove READ permission
user_perm &= ~READ  # now 0b110 (6)
print(bin(user_perm))  # 0b110
```

👉 **Why bitwise?**

- Efficiently **store multiple flags** in one number
- Fast checks without multiple variables

---

✅ **TL;DR:**

- **Boolean logic (**`**and/or/not**`**)** → for truthy conditions
- **Bitwise (**`**&/|/^/~**`**)** → for low-level bit manipulation (masks, flags, cryptography)