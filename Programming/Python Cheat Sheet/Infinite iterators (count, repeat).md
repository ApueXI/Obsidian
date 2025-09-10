---
Created: 2025-08-21T19:29
tags:
  - Itertool
---
## ✅ **What are Infinite Iterators?**

In `itertools`, **infinite iterators** keep generating values endlessly until you **manually stop** them.

✔️ Common infinite iterators:

- `count()` → endless counting numbers
- `repeat()` → endlessly repeat a value
- `cycle()` → endlessly loop through an iterable

We’ll focus on `**count**` and `**repeat**` here (you already saw `cycle` earlier).

---

## 🏗 **1.** `**itertools.count()**`

✔️ **Infinite arithmetic progression**

```Python
python
CopyEdit
from itertools import count

for n in count(start=5, step=2):
    print(n, end=" ")
    if n > 15: break
# 5 7 9 11 13 15 17

```

➡ **Use case:** Generating sequential IDs, infinite loops with a counter.

---

## 🏗 **2.** `**itertools.repeat()**`

✔️ **Repeat a single value indefinitely (or a fixed number of times)**

```Python
python
CopyEdit
from itertools import repeat

for item in repeat("Hello", 3):
    print(item)
# Hello
# Hello
# Hello

```

➡ **Use case:** Pre-filling values, initializing structures.

---

## ✅ **When to Use**

- `**count()**` → Infinite counting sequences, IDs, timestamps
- `**repeat()**` → Repeat same value, default arguments, placeholders

---

## ⚠️ **Gotchas**

❌ Both are **infinite** by default → must **limit manually**

✅ Use `itertools.islice()` to take only a finite slice

```Python
python
CopyEdit
from itertools import islice

# Take only first 5 from an infinite count
print(list(islice(count(10), 5)))
# [10, 11, 12, 13, 14]

```

---

## 🏎 **Infinite Iterators vs range()**

|Feature|count|repeat|range|
|---|---|---|---|
|Infinite?|✅ Yes|✅ Yes|❌ No|
|Generates seq?|✅ Yes|❌ No|✅ Yes|
|Memory safe?|✅ Yes|✅ Yes|✅ Yes|

---

## 📌 **Summary Table**

|Function|Purpose|
|---|---|
|`count(start, step)`|Infinite sequence of numbers|
|`repeat(value, times=None)`|Repeat value forever (or `times` times)|
|`islice(iter, n)`|Take only `n` elements from an infinite iterator|

---

## 🌍 **Real-World Example: Invoice Number Generator**

Imagine you need an **auto-incrementing invoice number** and **default placeholder text**.

```Python
python
CopyEdit
from itertools import count, repeat, islice

# Infinite invoice numbers starting at 1000
invoice_numbers = count(1000)

# Placeholder message repeated 3 times
placeholders = list(repeat("TBD", 3))
print("Default placeholders:", placeholders)

# Simulate generating first 5 invoices
for inv_id in islice(invoice_numbers, 5):
    print(f"Invoice #{inv_id}")

```

Output:

```Plain
less
CopyEdit
Default placeholders: ['TBD', 'TBD', 'TBD']
Invoice #1000
Invoice #1001
Invoice #1002
Invoice #1003
Invoice #1004

```

👉 **Why infinite iterators?**

- `count()` gives endless unique invoice numbers without extra code
- `repeat()` avoids manual loops for placeholder creation

---

✅ **TL;DR:**

- `count()` → endless counting sequence
- `repeat()` → endlessly repeat a value
- **Limit them with** `**islice()**`