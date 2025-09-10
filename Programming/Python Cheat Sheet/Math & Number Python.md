---
Created: 2025-08-21T19:29
tags:
  - Built-in-Function
---
## 1. `abs()`

- Returns the **absolute value** of a number (removes the sign).

### Syntax:

```Python
abs(x)
```

### Example:

```Python
abs(-7)     # 7
abs(3.5)    # 3.5
```

---

## 2. `round()`

- Rounds a floating-point number to a specified number of decimal places (default is 0).

### Syntax:

```Python
round(number, ndigits=0)
```

- `ndigits` is optional — if omitted, rounds to nearest integer.

### Example:

```Python
round(3.14159, 2)  # 3.14
round(5.678)       # 6
```

---

## 3. `pow()`

- Returns the **value of a number raised to the power of another** (`x**y`).
- Optional 3rd argument for modulus: `pow(x, y, mod)` computes `(x**y) % mod` efficiently.

### Syntax:

```Python
pow(x, y, mod=None)
```

### Examples:

```Python
pow(2, 3)       # 8 (2^3)
pow(2, 3, 5)    # 3 ((2^3) % 5)
```

---

## 4. `divmod()`

- Returns a tuple `(quotient, remainder)` when dividing two numbers.

### Syntax:

```Python
divmod(a, b)
```

### Example:

```Python
divmod(17, 5)   # (3, 2) because 17 = 5*3 + 2
```

---

## 5. `max()`

- Returns the **maximum value** from an iterable or multiple arguments.

### Syntax:

```Python
max(iterable, *[, key, default])
max(arg1, arg2, *args[, key])
```

### Examples:

```Python
max([1, 5, 3])     # 5
max(1, 5, 3)       # 5
```

---

## 6. `min()`

- Returns the **minimum value** from an iterable or multiple arguments.

### Syntax:

```Python
min(iterable, *[, key, default])
min(arg1, arg2, *args[, key])
```

### Examples:

```Python
min([1, 5, 3])     # 1
min(1, 5, 3)       # 1
```

---

## 7. `sum()`

- Returns the **sum of all items** in an iterable.
- Optional `start` argument to add to the sum (default 0).

### Syntax:

```Python
sum(iterable, start=0)
```

### Examples:

```Python
sum([1, 2, 3])      # 6
sum([1, 2, 3], 10)  # 16 (10 + 6)
```

---

## Summary Table

|Function|Purpose|Syntax|Example|
|---|---|---|---|
|`abs()`|Absolute value|`abs(x)`|`abs(-7) -> 7`|
|`round()`|Round to given decimals|`round(num, ndigits=0)`|`round(3.14159, 2) -> 3.14`|
|`pow()`|Power (exponentiation)|`pow(x, y, mod=None)`|`pow(2, 3) -> 8`|
|`divmod()`|Quotient and remainder tuple|`divmod(a, b)`|`divmod(17, 5) -> (3, 2)`|
|`max()`|Maximum value|`max(iterable or args)`|`max([1,5,3]) -> 5`|
|`min()`|Minimum value|`min(iterable or args)`|`min([1,5,3]) -> 1`|
|`sum()`|Sum of iterable|`sum(iterable, start=0)`|`sum([1,2,3]) -> 6`|

---

## Real-World Example: Grade Statistics

```Python
grades = [85, 90, 78, 92, 88]

print("Highest grade:", max(grades))        # 92
print("Lowest grade:", min(grades))         # 78
print("Average grade:", round(sum(grades)/len(grades), 2))  # 86.6

# Difference between highest and lowest
diff = abs(max(grades) - min(grades))
print("Range of grades:", diff)              # 14

# Using divmod to split total points by tests
total_points = sum(grades)
tests = len(grades)
quotient, remainder = divmod(total_points, tests)
print(f"Each test average: {quotient} with remainder {remainder}")
```