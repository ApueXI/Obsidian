---
Created: 2025-08-21T19:29
tags:
  - Math-&-Logic
---
## ✅ **What is the** `**random**` **Module?**

The `random` module generates **pseudo-random numbers** for:

✔️ Numbers (ints, floats)

✔️ Choosing random items

✔️ Shuffling sequences

✔️ Simulating randomness

> ⚠️ It’s not cryptographically secure → For security, use secrets instead.

---

## 🏗 **Basic Usage**

```Python
import random

print(random.random())      # Random float 0.0 ≤ x < 1.0
print(random.randint(1, 10))# Random int [1,10]
print(random.choice(["A","B","C"]))  # Random element
```

---

## 🔹 **Key Functions**

### 1️⃣ **Random Floats**

```Python
random.random()        # 0.0 ≤ x < 1.0
random.uniform(5, 10)  # Random float in [5,10]
```

---

### 2️⃣ **Random Integers**

```Python
random.randint(1, 6)   # Inclusive [1,6]
random.randrange(0, 10, 2)  # Even numbers: 0,2,4,6,8
```

---

### 3️⃣ **Sequences**

```Python
items = ["apple", "banana", "cherry"]

random.choice(items)      # Pick 1 item
random.sample(items, 2)   # Pick 2 unique items
random.choices(items, k=5)# Pick 5 items (with replacement)
```

---

### 4️⃣ **Shuffling**

```Python
deck = [1,2,3,4,5]
random.shuffle(deck)
print(deck)  # Deck is shuffled in-place
```

---

### 5️⃣ **State Control**

```Python
random.seed(42)   # Makes results reproducible
print(random.random())
```

---

### 6️⃣ **Random Distributions**

```Python
random.gauss(mu=0, sigma=1)   # Gaussian/Normal distribution
random.expovariate(1/5)       # Exponential distribution
random.triangular(1, 10, 3)   # Triangular distribution
```

---

## ⚠️ **Gotchas**

❌ **Not for security** → use `secrets`

❌ `random.seed()` affects **all random calls**

✅ For isolated reproducibility, use `random.Random(seed)`

---

## 🏎 **random vs secrets vs numpy.random**

|Feature|random|secrets|numpy.random|
|---|---|---|---|
|Security|❌ Weak|✅ Strong|❌ Weak|
|Arrays support|❌ No|❌ No|✅ Yes|
|Speed for large|Normal|Normal|✅ Fast|
|Best for|Simulations, games|Passwords, tokens|Data science|

---

## 📌 **Summary Table**

|Category|Functions|
|---|---|
|**Floats**|`random()`, `uniform(a,b)`|
|**Integers**|`randint(a,b)`, `randrange(start,stop,step)`|
|**Sequences**|`choice(seq)`, `sample(seq,k)`, `choices(seq,k)`|
|**Shuffling**|`shuffle(seq)`|
|**Distributions**|`gauss(mu,sigma)`, `expovariate(lmbd)`, `triangular(low,high,mode)`|
|**Seed**|`seed(x)`|

---

## 🌍 **Real-World Example: Simple Dice Roller & Loot Drop**

```Python
import random

def roll_dice(sides=6):
    return random.randint(1, sides)

def loot_drop():
    items = ["Gold", "Potion", "Sword", "Nothing"]
    return random.choices(items, weights=[50, 30, 15, 5], k=1)[0]

# Roll 5 dice
print([roll_dice() for _ in range(5)])

# Simulate 3 loot drops
print([loot_drop() for _ in range(3)])
```

👉 **Why** `**random**`**?**

- `randint()` makes dice rolls easy
- `choices()` with **weights** simulates realistic loot probabilities

---

✅ **TL;DR:**

- `random` = **simple pseudo-random numbers**
- Great for **games, simulations, testing**
- Not for **cryptographic security**