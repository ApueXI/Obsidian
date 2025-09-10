---
Created: 2025-08-21T19:29
tags:
  - Data-Structure
---
## 1. What is a Dictionary?

- A **mutable, unordered collection** of **key-value pairs**.
- Keys must be **unique** and **immutable** (e.g., strings, numbers, tuples).
- Values can be **any type**.

```Python
person = {
    "name": "Alice",
    "age": 30,
    "city": "New York"
}
empty_dict = {}        # empty dictionary
another = dict(name="Bob", age=25)
```

✅ Fast **lookup** by key

✅ **Mutable** → can add, modify, or delete

---

## 2. Accessing Dictionary Items

```Python
print(person["name"])         # Alice
print(person.get("age"))      # 30
print(person.get("country", "Unknown"))  # Default if key missing
```

✅ `.get()` is safer than `[]` → avoids `KeyError`

---

## 3. Adding & Updating

```Python
person["job"] = "Engineer"   # Add new key-value
person["age"] = 31           # Update existing value
```

---

## 4. Removing Items

```Python
del person["city"]      # Remove key
person.pop("job")       # Remove and return value
person.popitem()        # Remove last inserted item (Python 3.7+)
person.clear()          # Empty dictionary
```

---

## 5. Dictionary Methods

|Method|Example|Description|
|---|---|---|
|`keys()`|`person.keys()` → `dict_keys([...])`|Get all keys|
|`values()`|`person.values()` → `dict_values([...])`|Get all values|
|`items()`|`person.items()` → `dict_items([...])`|Get key-value pairs|
|`get(key, default)`|`person.get("age", 0)` → `31`|Safe lookup|
|`pop(key)`|`person.pop("age")`|Remove & return value|
|`popitem()`|`person.popitem()`|Remove last added pair|
|`update(other_dict)`|`person.update({"city": "LA"})`|Merge dictionaries|
|`setdefault(k, v)`|`person.setdefault("country","USA")`|Add if missing|
|`copy()`|`new = person.copy()`|Shallow copy|

---

## 6. Looping Through Dictionaries

```Python
for key in person:
    print(key, person[key])

for key, value in person.items():
    print(f"{key} → {value}")

for value in person.values():
    print(value)
```

---

## 7. Dictionary Comprehension

```Python
nums = [1, 2, 3]
squares = {n: n**2 for n in nums}
print(squares)  # {1: 1, 2: 4, 3: 9}
```

✅ Quick way to build dictionaries

---

## 8. Merging Dictionaries

```Python
a = {"x": 1, "y": 2}
b = {"y": 3, "z": 4}

merged = a | b   # Python 3.9+ → {'x':1, 'y':3, 'z':4}
a.update(b)      # Updates in place
```

---

## Summary Table

|Operation/Method|Example|Description|
|---|---|---|
|Access value|`d["key"]`, `d.get("key")`|Get value|
|Add/Update|`d["key"]=val`|Add or modify|
|Remove key|`del d["key"]`, `d.pop("key")`|Remove item|
|Get keys/values/items|`d.keys()`, `d.values()`, `d.items()`|View contents|
|Pop item|`d.popitem()`|Remove last pair|
|Merge dicts|`d1.update(d2)` / `d1|d2` (3.9+)|
|Set default|`d.setdefault("k", default)`|Add if missing|
|Clear dict|`d.clear()`|Empty dict|
|Copy dict|`d.copy()`|Shallow copy|

---

## Real-World Example: Student Grades

```Python
grades = {
    "Alice": 85,
    "Bob": 92,
    "Charlie": 78
}

# Add/update a grade
grades["Diana"] = 90
grades["Alice"] = 88

# Remove a student
grades.pop("Charlie")

# Calculate average
avg = sum(grades.values()) / len(grades)

# Print all
for student, score in grades.items():
    print(f"{student}: {score}")

print("Average score:", avg)
```

**Output:**

```Plain
Alice: 88
Bob: 92
Diana: 90
Average score: 90.0
```

✅ Great for **fast lookups** & **structured data**