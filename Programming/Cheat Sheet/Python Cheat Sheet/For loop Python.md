---
Created: 2025-08-21T19:29
tags:
  - Control-Flow
---
### Basic Syntax

```Python
for variable in iterable:
    # code block to execute
```

- `variable`: Temporary name for each element in the `iterable`.
- `iterable`: Any sequence or collection (like list, tuple, string, dict, set, range).

---

### Iterating Over a List

```Python
fruits = ['apple', 'banana', 'cherry']
for fruit in fruits:
    print(fruit)
```

---

### Iterating Over a String

```Python
for char in "hello":
    print(char)
```

---

### Iterating Over a Tuple

```Python
t = (1, 2, 3)
for num in t:
    print(num)
```

---

### Iterating Over a Dictionary

- Iterate over keys:

```Python
d = {'a': 1, 'b': 2}
for key in d:
    print(key)
```

- Iterate over keys and values:

```Python
for key, value in d.items():
    print(key, value)
```

---

### Using `range()` in For Loops

```Python
for i in range(5):  # 0 to 4
    print(i)
```

- `range(start, stop, step)`

```Python
for i in range(2, 10, 2):  # 2,4,6,8
    print(i)
```

---

### Loop Control Statements

- `break`: Exit the loop immediately

```Python
for i in range(10):
    if i == 5:
        break
    print(i)
```

- `continue`: Skip the rest of the current iteration and go to next

```Python
for i in range(5):
    if i == 3:
        continue
    print(i)
```

- `else` block on loops: runs if loop is **not** terminated by `break`

```Python
for i in range(3):
    print(i)
else:
    print("Loop finished without break")
```

---

### Looping with `enumerate()` — getting index and value

```Python
fruits = ['apple', 'banana', 'cherry']
for index, fruit in enumerate(fruits):
    print(index, fruit)
```

---

### Looping with `zip()` — iterate over multiple iterables in parallel

```Python
names = ['Alice', 'Bob']
ages = [25, 30]
for name, age in zip(names, ages):
    print(name, age)
```

---

### List Comprehensions (compact for-loop for creating lists)

```Python
squares = [x**2 for x in range(5)]
print(squares)  # [0, 1, 4, 9, 16]
```

---

### Nested For Loops

```Python
for i in range(3):
    for j in range(2):
        print(i, j)
```

---

### Looping over a file line by line

```Python
with open('file.txt') as f:
    for line in f:
        print(line.strip())
```

---

### Tips & Tricks

- Use `list()` or `tuple()` to convert an iterable if needed.
- Use `sorted()` to loop over a sorted iterable.
- Use `reversed()` to loop in reverse.
- You can unpack tuples in the loop:
    
    ```Python
    pairs = [(1, 2), (3, 4)]
    for x, y in pairs:
        print(x, y)
    ```
    

  

### Summary Table

|Concept|Syntax / Usage|Description|
|---|---|---|
|Basic loop|`for x in iterable:`|Iterate over elements in any iterable|
|Iterate over list|`for item in list:`|Loop through list elements|
|Iterate over string|`for char in "text":`|Loop through characters in a string|
|Iterate over dict|`for key in dict:` or `for k,v in dict.items():`|Loop through keys or keys & values in dict|
|Use `range()`|`for i in range(start, stop, step):`|Loop over sequence of numbers|
|Break loop|`break`|Exit loop immediately|
|Skip iteration|`continue`|Skip current iteration|
|Loop with else|`for... else:`|Runs if loop wasn’t exited by `break`|
|Enumerate for index|`for i, val in enumerate(iterable):`|Loop with index and value|
|Zip multiple iterables|`for a, b in zip(list1, list2):`|Loop over multiple lists in parallel|
|Nested loops|`for i in ...: for j in ...:`|Loops inside loops|
|List comprehension|`[expr for x in iterable]`|Create list with a for loop in one line|

---

  

### Real-World Example: Processing Orders

Imagine you have a list of orders, each a dictionary with a product and quantity. You want to print a summary and calculate total items ordered.

```Python
orders = [
    {'product': 'T-shirt', 'quantity': 3},
    {'product': 'Jeans', 'quantity': 2},
    {'product': 'Hat', 'quantity': 1},
]

total_items = 0
for order in orders:
    print(f"Ordered {order['quantity']} units of {order['product']}")
    total_items += order['quantity']

print(f"Total items ordered: {total_items}")
```

**Output:**

```Plain
Ordered 3 units of T-shirt
Ordered 2 units of Jeans
Ordered 1 units of Hat
Total items ordered: 6
```