---
Created: 2025-08-21T19:29
tags:
  - Itertool
---
## ✅ **What is** `**itertools**`**?**

`itertools` is a **standard library** module for efficient looping with iterators.

✔️ Useful for:

- Combining sequences
- Infinite iterators
- Generating permutations & combinations

We’ll focus on:

- `chain()` → flatten/concatenate iterables
- `cycle()` → infinite looping
- `permutations()` → all possible orderings
- `combinations()` → unique selections

---

## 🏗 **1.** `**itertools.chain()**`

✔️ **Flattens multiple iterables into one sequence**

```Python
from itertools import chain

a = [1, 2, 3]
b = ['x', 'y']
print(list(chain(a, b)))  # [1, 2, 3, 'x', 'y']
```

➡ **Use case**: Flatten lists without creating nested loops.

---

## 🏗 **2.** `**itertools.cycle()**`

✔️ **Repeats elements of an iterable indefinitely**

```Python
from itertools import cycle

count = 0
for item in cycle("AB"):
    print(item, end=" ")   # A B A B A B ...
    count += 1
    if count > 5: break
```

➡ **Use case**: Round-robin scheduling, repeating patterns.

---

## 🏗 **3.** `**itertools.permutations()**`

✔️ **All possible orderings of elements**

```Python
from itertools import permutations

print(list(permutations([1, 2, 3], 2)))
# [(1,2), (1,3), (2,1), (2,3), (3,1), (3,2)]
```

➡ **Order matters** → `(1,2)` ≠ `(2,1)`

---

## 🏗 **4.** `**itertools.combinations()**`

✔️ **All unique selections (no order)**

```Python
from itertools import combinations

print(list(combinations([1, 2, 3], 2)))
# [(1,2), (1,3), (2,3)]
```

➡ **Order doesn’t matter** → `(1,2)` == `(2,1)`

---

## ✅ **Comparison: permutations vs combinations**

|Feature|permutations|combinations|
|---|---|---|
|Order matters?|✅ Yes|❌ No|
|Output size|`n!/(n-r)!`|`n!/(r!(n-r)!)`|

---

## ✅ **When to Use**

- `**chain**` → merge multiple iterables
- `**cycle**` → infinite round-robin
- `**permutations**` → all possible arrangements
- `**combinations**` → unique selections

---

## ⚠️ **Gotchas**

❌ `cycle` never stops → must **break manually**

❌ `permutations` & `combinations` **generate tuples**, not lists

✅ For large inputs, they **generate lazily** (don’t store in memory)

---

## 🏎 **itertools vs manual loops**

|Feature|itertools|Manual|
|---|---|---|
|Memory efficient|✅ Yes|❌ No|
|Lazy evaluation|✅ Yes|❌ No|
|Readability|✅ Clean|❌ More code|

---

## 📌 **Summary Table**

|Function|Purpose|
|---|---|
|`chain(a, b, c)`|Concatenate multiple iterables|
|`cycle(iter)`|Repeat elements indefinitely|
|`permutations(iter, r)`|All possible orderings|
|`combinations(iter, r)`|Unique selections without order|

---

## 🌍 **Real-World Example: Outfit Generator**

Imagine you’re building a **fashion app** to generate outfit combos.

```Python
from itertools import chain, cycle, permutations, combinations

# Clothing items
tops = ["T-shirt", "Shirt"]
bottoms = ["Jeans", "Shorts"]
shoes = ["Sneakers", "Sandals"]

# Merge all categories for a catalog view
catalog = list(chain(tops, bottoms, shoes))
print("Catalog:", catalog)

# Suggest repeating color patterns (limited)
colors = cycle(["Red", "Blue", "Green"])
print("Next colors:", [next(colors) for _ in range(6)])

# Generate all outfit permutations (tops+bottoms)
print("Possible outfits:", list(permutations(["T-shirt", "Jeans", "Sneakers"], 2)))

# Generate unique 2-item combos for packing light
print("Packing combos:", list(combinations(["T-shirt", "Shirt", "Jeans"], 2)))
```

👉 **Why** `**itertools**`**?**

- `chain()` quickly flattens product categories
- `cycle()` rotates colors infinitely
- `permutations()` shows all possible outfit orders
- `combinations()` suggests minimal unique sets for packing

---

✅ **TL;DR:**

- `chain` → merge
- `cycle` → infinite repeat
- `permutations` → all orderings
- `combinations` → unique selections