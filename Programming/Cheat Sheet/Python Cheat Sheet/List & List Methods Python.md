---
Created: 2025-08-21T19:29
tags:
  - Data-Structure
---
## 1. What is a List?

- A **mutable, ordered collection** of items.
- Can hold **different data types**.

```Python
my_list = [1, "apple", 3.5, True]
empty_list = []
```

✅ **Mutable** → you can change elements

✅ **Ordered** → preserves insertion order

---

## 2. Basic List Operations

```Python
nums = [10, 20, 30, 40]

print(len(nums))        # Length → 4
print(nums[0])          # Indexing → 10
print(nums[-1])         # Negative indexing → 40
print(nums[1:3])        # Slicing → [20, 30]
print(nums + [50, 60])  # Concatenation → [10,20,30,40,50,60]
print(nums * 2)         # Repetition → [10,20,30,40,10,20,30,40]
print(20 in nums)       # Membership → True
```

---

## 3. Common List Methods

|Method|Example|Description|
|---|---|---|
|`append(x)`|`lst.append(5)` → `[1,2,3,5]`|Add element at the end|
|`insert(i, x)`|`lst.insert(1, 99)`|Insert at index|
|`extend(iterable)`|`lst.extend([4,5])`|Add multiple items|
|`remove(x)`|`lst.remove(2)`|Remove first occurrence of x|
|`pop(i)`|`lst.pop()` → removes last|Remove & return element (default last)|
|`clear()`|`lst.clear()`|Remove all elements|
|`index(x)`|`lst.index(30)`|Find index of first occurrence|
|`count(x)`|`lst.count(20)`|Count occurrences of a value|
|`sort()`|`lst.sort()`|Sort list in place|
|`sort(reverse=True)`|`lst.sort(reverse=True)`|Sort descending|
|`sorted(lst)`|`sorted(lst)`|Return new sorted list|
|`reverse()`|`lst.reverse()`|Reverse list in place|
|`copy()`|`new = lst.copy()`|Shallow copy of list|

---

## 4. Adding & Removing Elements

```Python
fruits = ["apple", "banana"]

fruits.append("cherry")         # Add to end → ["apple","banana","cherry"]
fruits.insert(1, "orange")      # Insert at index → ["apple","orange","banana","cherry"]
fruits.extend(["mango", "kiwi"])# Add multiple → ["apple","orange","banana","cherry","mango","kiwi"]

fruits.remove("orange")         # Remove → ["apple","banana","cherry","mango","kiwi"]
fruits.pop()                    # Removes last → ["apple","banana","cherry","mango"]
fruits.pop(1)                   # Removes index 1 → ["apple","cherry","mango"]
```

---

## 5. Sorting & Reversing

```Python
nums = [3, 1, 4, 2]
nums.sort()              # [1, 2, 3, 4]
nums.sort(reverse=True)  # [4, 3, 2, 1]

words = ["banana", "apple", "cherry"]
sorted_words = sorted(words)  # ['apple','banana','cherry']

words.reverse()          # Reverse order in place
```

---

## 6. Copying Lists

```Python
a = [1, 2, 3]
b = a.copy()     # separate copy
c = list(a)      # another copy
```

⚠️ **Be careful:** `b = a` just creates a **reference**, not a copy!

---

## 7. Nested Lists

```Python
python
matrix = [[1,2,3],[4,5,6]]
print(matrix[0][1])  # 2
```

---

## Summary Table

|Operation/Method|Example|Description|
|---|---|---|
|Indexing & slicing|`lst[0]`, `lst[1:3]`|Access part of list|
|Append|`lst.append(x)`|Add single element|
|Insert|`lst.insert(2, x)`|Insert at position|
|Extend|`lst.extend([x,y])`|Add multiple elements|
|Remove/Pop|`lst.remove(x)`, `lst.pop()`|Remove elements|
|Sort/Reverse|`lst.sort()`, `lst.reverse()`|Sort or reverse list|
|Count/Index|`lst.count(x)`, `lst.index(x)`|Find occurrences or position|
|Clear/Copy|`lst.clear()`, `lst.copy()`|Empty or duplicate list|
|Membership|`x in lst`|Check if exists|

---

## Real-World Example: Shopping Cart

```Python
cart = []

# Add items
cart.append("Laptop")
cart.append("Phone")
cart.extend(["Headphones", "Mouse"])

# Remove an unwanted item
cart.remove("Mouse")

# Sort alphabetically
cart.sort()

print("Your cart:", cart)
print("Items count:", len(cart))
```

**Output:**

```Plain
Your cart: ['Headphones', 'Laptop', 'Phone']
Items count: 3
```

✅ Easy management of a dynamic collection of items