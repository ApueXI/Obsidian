---
Created: 2025-08-21T19:29
tags:
  - Built-in-Function
---
## 1. `any()`

- Returns **True** if **any element** of the iterable is truthy.
- Returns **False** if all are falsy or iterable is empty.

### Syntax:

```Python
any(iterable)
```

### Behavior:

- Stops **early** (short-circuits) when it finds the first truthy value.
- Truthy values: non-zero numbers, non-empty strings/lists/etc.

### Examples:

```Python
print(any([0, False, "", None]))    # False (all falsy)
print(any([0, False, 5]))           # True (5 is truthy)
print(any([]))                      # False (empty is falsy)
```

---

## 2. `all()`

- Returns **True** if **all elements** of the iterable are truthy.
- Returns **True** if iterable is empty (vacuous truth).

### Syntax:

```Python
all(iterable)
```

### Behavior:

- Stops **early** (short-circuits) when it finds the first falsy value.
- Falsy values: `0`, `False`, `None`, `""`, `[]`, `{}`, etc.

### Examples:

```Python
print(all([True, 1, "hi"]))         # True (all truthy)
print(all([True, 0, "hi"]))         # False (0 is falsy)
print(all([]))                      # True (empty is vacuously true)
```

---

## Truthy & Falsy Reminder

- **Falsy:** `0`, `0.0`, `False`, `None`, `""` (empty string), `[]` (empty list), `{}` (empty dict), `set()`
- **Truthy:** everything else

---

## Summary Table

|Function|Returns True If…|Empty Iterable|Example|
|---|---|---|---|
|`any()`|At least **one** element is truthy|`False`|`any([0,5]) -> True`|
|`all()`|**All** elements are truthy|`True`|`all([1,2,3]) -> True`|

---

## Real-World Examples

### ✅ Checking login permissions

```Python
permissions = [False, False, True]
print(any(permissions))
# True → user has at least one permission
```

### ✅ Validating required fields

```Python
fields = ["Name", "Email", ""]
print(all(fields))
# False → not all fields filled in
```

### ✅ Quick status checks

```Python
servers_online = [True, True, True]
print("All servers up?", all(servers_online))  # True

alerts = [False, False, True]
print("Any alerts?", any(alerts))  # True
```

---

## Key Points

- `**any()**` → like **OR** (if any True → True).
- `**all()**` → like **AND** (if any False → False).
- Both **short-circuit** for efficiency.