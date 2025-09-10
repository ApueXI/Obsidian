---
Created: 2025-08-21T19:29
tags:
  - Data-Structure
---
## 1. What is a Tuple?

- A **tuple** is an **immutable, ordered collection** of items.
- Can hold **different data types**.
- Defined with **parentheses** `**()**` or **just commas**.

```Python
t1 = (1, 2, 3)
t2 = ("apple", 3.5, True)
t3 = 1, 2, 3  # same as (1, 2, 3)
empty_tuple = ()
```

✅ **Ordered** → preserves insertion order

✅ **Immutable** → cannot change elements after creation

---

## 2. Tuple Basics

```Python
t = (10, 20, 30, 40)

print(len(t))        # Length → 4
print(t[0])          # Indexing → 10
print(t[-1])         # Negative indexing → 40
print(t[1:3])        # Slicing → (20, 30)
print(t + (50, 60))  # Concatenation → (10,20,30,40,50,60)
print(t * 2)         # Repetition → (10,20,30,40,10,20,30,40)
print(20 in t)       # Membership → True
```

---

## 3. Tuple with One Element

Be careful! A single-element tuple needs a **comma**, otherwise it’s just a value.

```Python
t1 = (5)     # NOT a tuple → just an int
t2 = (5,)    # ✅ single-element tuple
```

---

## 4. Tuple Methods

Tuples have **only 2 built-in methods**:

|Method|Example|Description|
|---|---|---|
|`count(x)`|`(1,2,1).count(1)` → `2`|Counts occurrences of x|
|`index(x)`|`(1,2,3).index(2)` → `1`|Finds first occurrence|

---

## 5. Tuple Packing & Unpacking

```Python
# Packing
person = ("Alice", 30, "Engineer")

# Unpacking
name, age, job = person
print(name, age, job)  # Alice 30 Engineer
```

---

## 6. Nested Tuples

```Python
nested = (1, (2, 3), (4, 5))
print(nested[1][1])  # 3
```

---

## 7. Why Use Tuples?

✅ **Immutable** → safe to use as dictionary keys or set elements

✅ **Faster than lists** (lighter in memory)

✅ Represent **fixed collections** of data

---

## Summary Table

|Feature/Method|Example|Description|
|---|---|---|
|Indexing/Slicing|`t[0]`, `t[1:3]`|Access part of tuple|
|Concatenation|`t + (4,5)`|Combine tuples|
|Repetition|`t * 2`|Repeat tuple|
|Membership|`x in t`|Check existence|
|`count(x)`|`(1,2,1).count(1)` → 2|Count occurrences|
|`index(x)`|`(1,2,3).index(2)` → 1|Find position|
|Packing/Unpacking|`a,b = (1,2)`|Assign elements|

---

## Real-World Example: Returning Multiple Values

Tuples are often used to return **multiple values** from a function.

```Python
def min_max_avg(numbers):
    return min(numbers), max(numbers), sum(numbers)/len(numbers)

result = min_max_avg([10, 20, 30, 40])
low, high, avg = result

print("Min:", low)
print("Max:", high)
print("Avg:", avg)
```

**Output:**

```Plain
Min: 10
Max: 40
Avg: 25.0
```

✅ Easy way to return multiple results at once