---
Created: 2025-08-21T19:29
tags:
  - Data-Structure
---
## 1. What is a String?

- A **sequence of characters** enclosed in **single** `**'**`, **double** `**"**`, or **triple quotes** `**'''**` **/** `**"""**`.

```Python
s1 = 'Hello'
s2 = "World"
s3 = """Multi-line
string"""
```

- Strings are **immutable** → cannot be changed in place.

---

## 2. Basic String Operations

```Python
s = "Python"
print(len(s))          # Length → 6
print(s[0])            # Indexing → 'P'
print(s[-1])           # Negative indexing → 'n'
print(s[0:3])          # Slicing → 'Pyt'
print(s + " Rocks")    # Concatenation → 'Python Rocks'
print(s * 3)           # Repetition → 'PythonPythonPython'
print("Py" in s)       # Membership → True
```

---

## 3. Common String Methods

|Method|Example|Description|
|---|---|---|
|`lower()`|`"HELLO".lower()` → `hello`|Converts to lowercase|
|`upper()`|`"hi".upper()` → `HI`|Converts to uppercase|
|`title()`|`"hello world".title()` → `Hello World`|Capitalizes each word|
|`capitalize()`|`"python".capitalize()` → `Python`|Capitalizes first letter|
|`strip()`|`" hi ".strip()` → `hi`|Removes whitespace (or chars)|
|`lstrip()` / `rstrip()`|`" hi ".lstrip()` → `hi`|Removes left/right spaces|
|`replace(a, b)`|`"hi".replace("h","H")` → `Hi`|Replace substring|
|`split()`|`"a,b,c".split(",")` → `['a','b','c']`|Split into list|
|`join()`|`",".join(['a','b'])` → `a,b`|Join list into string|
|`find()` / `index()`|`"hello".find("e")` → `1`|Find first occurrence|
|`count()`|`"banana".count("a")` → `3`|Count occurrences|
|`startswith()`|`"hello".startswith("he")` → `True`|Check prefix|
|`endswith()`|`"hello".endswith("lo")` → `True`|Check suffix|
|`isalnum()`|`"abc123".isalnum()` → `True`|Check letters+digits only|
|`isalpha()`|`"abc".isalpha()` → `True`|Check letters only|
|`isdigit()`|`"123".isdigit()` → `True`|Check digits only|
|`isspace()`|`" ".isspace()` → `True`|Check only whitespace|
|`zfill(n)`|`"42".zfill(5)` → `00042`|Pad with zeros|
|`center(n)`|`"hi".center(6)` → `' hi '`|Center with padding|

---

## 4. String Formatting

### f-strings (Recommended)

```Python
name = "Alice"
age = 30
print(f"My name is {name} and I’m {age} years old.")
```

---

### `format()` method

```Python
print("My name is {} and I’m {} years old.".format("Alice", 30))
print("{0} is {1}".format("Python", "fun"))
```

---

### Old `%` formatting

```Python
print("My name is %s and I’m %d years old." % ("Alice", 30))
```

---

## 5. Multi-line Strings

```Python
multi = """This
is
multi-line"""
```

---

## Summary Table

|Feature|Example|Description|
|---|---|---|
|Indexing & slicing|`s[0]`, `s[-1]`, `s[2:5]`|Access parts of a string|
|Concatenation|`"Hi" + "There"` → `HiThere`|Combine strings|
|Repetition|`"Hi"*3` → `HiHiHi`|Repeat string|
|Membership|`"Py" in "Python"` → `True`|Check if substring exists|
|Case methods|`"hi".upper()` → `HI`|Change case|
|Strip/Replace|`" x ".strip()`, `.replace()`|Trim or replace text|
|Split/Join|`"a,b".split(",")`, `",".join()`|Split & join strings|
|Find/Count|`"text".find("t")`, `.count("t")`|Search substring|
|is-checks|`isalpha()`, `isdigit()`, etc.|String content checks|
|Formatting|`f"Hello {name}"`|Insert variables dynamically|

---

## Real-World Example: Simple Text Cleaner

```Python
def clean_text(text):
    text = text.strip()              # Remove extra spaces
    text = text.replace("\n", " ")   # Replace newlines
    text = " ".join(text.split())    # Remove extra internal spaces
    return text

raw = "   Hello   \n   world!   \nThis   is   Python.  "
print(clean_text(raw))
```

**Output:**

```Plain
Hello world! This is Python.
```

✅ Useful for cleaning messy user input