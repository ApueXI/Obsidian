---
Created: 2025-08-21T19:29
tags:
  - Iterators-&-Generators
---
## 1. What is a Generator Function?

- A **generator function** is defined like a normal function but uses the `yield` keyword to **produce a sequence of values lazily**, one at a time.
- When called, it returns a **generator iterator**, not the actual values immediately.
- Each `yield` pauses the function, preserving its state for the next call.

---

## 2. Basic Syntax

```Python
def my_generator():
    yield value1
    yield value2
    # ...
```

---

## 3. How to Use

```Python
gen = my_generator()

print(next(gen))  # outputs value1
print(next(gen))  # outputs value2
# Raises StopIteration when done
```

---

## 4. Example: Simple Generator

```Python
def count_up_to(n):
    count = 1
    while count <= n:
        yield count
        count += 1

counter = count_up_to(3)
for num in counter:
    print(num)
```

Output:

```Plain
1
2
3
```

---

## 5. Advantages of Generators

- **Memory efficient**: yields one item at a time, no large list needed.
- Can represent **infinite sequences** (e.g., Fibonacci numbers).
- Easy to write iterators without classes.

---

## 6. Example: Fibonacci Generator

```Python
def fibonacci(limit):
    a, b = 0, 1
    while a < limit:
        yield a
        a, b = b, a + b

for num in fibonacci(10):
    print(num)
```

Output:

```Plain
0
1
1
2
3
5
8
```

---

## Summary Table

|Feature|Description|Example|
|---|---|---|
|`yield`|Pauses function, sends a value to caller|`yield value`|
|Generator function|Function using `yield` returns generator|`def gen(): yield 1`|
|Iteration|Use `for` loop or `next()` on generator|`for x in gen(): print(x)`|
|Lazy evaluation|Values produced on demand, not all at once|Memory efficient|

---

## Real-World Example: Generating Lines from a Large File

```Python
def read_lines(file_path):
    with open(file_path) as f:
        for line in f:
            yield line.strip()

for line in read_lines("large_file.txt"):
    print(line)
```

✅ Efficiently process large files line-by-line without loading whole file into memory.