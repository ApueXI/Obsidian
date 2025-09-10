---
Created: 2025-08-21T19:29
tags:
  - Data-Structure
---
## 1. What is a Set?

- A **set** is an **unordered, mutable collection** of **unique elements**.
- Defined with **curly braces** `**{}**` or the `set()` function.

```Python
s1 = {1, 2, 3, 4}
s2 = set([3, 4, 5, 6])
empty_set = set()   # {} would create a dict, not a set
```

✅ **No duplicates** → `{1, 2, 2, 3}` → `{1, 2, 3}`

✅ **Unordered** → no indexing or slicing

✅ **Mutable** but only immutable objects can be inside

---

## 2. Basic Set Operations

```Python
s = {1, 2, 3}
print(len(s))         # Length → 3
print(2 in s)         # Membership → True
s.add(4)              # Add element → {1,2,3,4}
s.remove(2)           # Remove element → {1,3,4}
s.discard(5)          # Remove safely (no error if missing)
s.pop()               # Remove random element
s.clear()             # Empty the set
```

---

## 3. Mathematical Set Operations

Let’s use two sets:

```Python
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}
```

|Operation|Example|Result|
|---|---|---|
|**Union**|`a|b`or`a.union(b)`|
|**Intersection**|`a & b` or `a.intersection(b)`|`{3,4}`|
|**Difference**|`a - b` or `a.difference(b)`|`{1,2}`|
|**Symmetric Difference**|`a ^ b` or `a.symmetric_difference(b)`|`{1,2,5,6}`|
|**Subset check**|`a <= b` or `a.issubset(b)`|True/False|
|**Superset check**|`a >= b` or `a.issuperset(b)`|True/False|
|**Disjoint check**|`a.isdisjoint(b)`|True if no common elements|

---

## 4. Frozen Set

- **Immutable set** that cannot be changed after creation.

```Python
fs = frozenset([1, 2, 3])
# fs.add(4)  ❌ Error (immutable)
```

✅ Can be used as a **dictionary key** or inside another set

---

## 5. Creating Sets from Other Data

```Python
nums = [1, 2, 2, 3, 3, 4]
unique_nums = set(nums)  # Removes duplicates → {1,2,3,4}
```

---

## 6. Set Comprehension

```Python
squares = {x**2 for x in range(5)}
print(squares)  # {0, 1, 4, 9, 16}
```

---

## Summary Table

|Operation/Method|Example|Result/Description|
|---|---|---|
|Add element|`s.add(x)`|Adds x to set|
|Remove element|`s.remove(x)`|Removes x, error if not found|
|Discard element|`s.discard(x)`|Removes x safely|
|Pop element|`s.pop()`|Removes random element|
|Clear all|`s.clear()`|Empty set|
|Union|`a|b`or`a.union(b)`|
|Intersection|`a & b` or `a.intersection(b)`|Common elements|
|Difference|`a - b`|Elements in a but not b|
|Symmetric Difference|`a ^ b`|Elements in a or b but not both|
|Subset/Superset|`a <= b`, `a >= b`|Relationship check|
|Disjoint|`a.isdisjoint(b)`|No common elements?|
|Frozen set|`frozenset(iterable)`|Immutable set|

---

## Real-World Example: Finding Unique & Common Users

```Python
site_a_users = {"alice", "bob", "charlie"}
site_b_users = {"bob", "david", "emma"}

all_users = site_a_users | site_b_users      # Union → all users
common_users = site_a_users & site_b_users   # Intersection → {'bob'}
exclusive_to_a = site_a_users - site_b_users # Difference → {'alice','charlie'}
exclusive_to_b = site_b_users - site_a_users # Difference → {'david','emma'}

print("All:", all_users)
print("Common:", common_users)
print("Only A:", exclusive_to_a)
print("Only B:", exclusive_to_b)
```

**Output:**

```Plain
All: {'alice', 'bob', 'charlie', 'david', 'emma'}
Common: {'bob'}
Only A: {'alice', 'charlie'}
Only B: {'david', 'emma'}
```

✅ Useful for membership management, filtering, and removing duplicates

---