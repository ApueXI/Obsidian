---
Created: 2025-08-21T19:29
tags:
  - Iterators-&-Generators
---
## 1. What is `iter()`?

- `iter()` **creates an iterator** from an iterable (like list, tuple, string, etc.).
- An **iterator** is an object that produces elements one at a time when requested.

```Python
lst = [1, 2, 3]
it = iter(lst)   # creates an iterator from list
```

---

## 2. What is `next()`?

- `next()` **retrieves the next item** from an iterator.
- Raises `StopIteration` exception when no items left.

```Python
print(next(it))  # 1
print(next(it))  # 2
print(next(it))  # 3
# next(it) now raises StopIteration
```

---

## 3. Using `next()` with Default Value

- You can pass a **default value** to avoid `StopIteration`.

```Python
print(next(it, "No more items"))  # prints "No more items" instead of raising error
```

---

## 4. Iterators vs Iterables

|Concept|Description|Example|
|---|---|---|
|Iterable|Object you can loop over (`for x in iterable`)|List, tuple, str|
|Iterator|Object that produces next item on request|`iter()` output|

`iter()` turns an **iterable** into an **iterator**.

---

## 5. Manual iteration example

```Python
fruits = ["apple", "banana", "cherry"]
it = iter(fruits)

while True:
    try:
        fruit = next(it)
        print(fruit)
    except StopIteration:
        break
```

Output:

```Plain
apple
banana
cherry
```

---

## Summary Table

|Function|Usage|Description|
|---|---|---|
|`iter(iterable)`|`it = iter([1,2,3])`|Create iterator from iterable|
|`next(iterator)`|`next(it)`|Get next item, raises StopIteration|
|`next(iterator, default)`|`next(it, None)`|Get next item or default if exhausted|

---

## Real-World Example: Reading file lines with iter and next

```Python
with open("example.txt") as f:
    file_iter = iter(f)  # file object is iterable, create iterator
    print(next(file_iter))  # Read first line
    print(next(file_iter))  # Read second line
```

✅ Useful for **manual control** of iteration, one item at a time.