---
Created: 2025-08-21T19:29
tags:
  - Built-in-Function
---
## 1. `open()`

- Opens a **file** and returns a **file object**.
- Used for **reading, writing, or appending**.

### Syntax:

```Python
open(filename, mode='r', encoding=None)
```

### Common modes:

- `'r'` → read (default)
- `'w'` → write (overwrites file)
- `'a'` → append
- `'b'` → binary mode (`'rb'`, `'wb'`)
- `'+'` → read & write

### Example:

```Python
with open("data.txt", "w") as f:
    f.write("Hello World")
```

---

## 2. `hash()`

- Returns the **hash value** of an object (only works for hashable types like str, int, tuple).
- Useful for dict keys, sets, and hashing algorithms.

### Syntax:

```Python
hash(obj)
```

### Example:

```Python
print(hash("hello"))    # e.g., 123456789
print(hash(42))         # e.g., 42
```

---

## 3. `format()`

- Formats a value according to a **format specification**.
- Similar to f-strings but as a function.

### Syntax:

```Python
format(value, format_spec)
```

### Example:

```Python
print(format(1234.5678, ".2f"))   # '1234.57'
print(format(255, "x"))           # 'ff' (hex)
```

---

## 4. `chr()`

- Converts a **Unicode code point** (int) into its **character**.

### Syntax:

```Python
chr(code_point)
```

### Example:

```Python
print(chr(65))   # 'A'
print(chr(128512))  # '😀'
```

---

## 5. `ord()`

- Converts a **character** into its **Unicode code point (int)**.

### Syntax:

```Python
ord(character)
```

### Example:

```Python
print(ord('A'))   # 65
print(ord('😀'))  # 128512
```

---

## 6. `bin()`

- Converts an integer into its **binary string** (prefix `'0b'`).

### Syntax:

```Python
bin(x)
```

### Example:

```Python
print(bin(10))    # '0b1010'
```

---

## 7. `oct()`

- Converts an integer into its **octal string** (prefix `'0o'`).

### Syntax:

```Python
oct(x)
```

### Example:

```Python
print(oct(10))    # '0o12'
```

---

## 8. `hex()`

- Converts an integer into its **hexadecimal string** (prefix `'0x'`).

### Syntax:

```Python
hex(x)
```

### Example:

```Python
print(hex(255))   # '0xff'
```

---

## Summary Table

|Function|Purpose|Example|
|---|---|---|
|`open()`|Open a file for read/write|`open("file.txt", "r")`|
|`hash()`|Get hash value of an object|`hash("abc")` → e.g. 12345|
|`format()`|Format value with specifier|`format(3.14, ".1f") → '3.1'|
|`chr()`|Unicode code → character|`chr(65)` → 'A'|
|`ord()`|Character → Unicode code|`ord('A')` → 65|
|`bin()`|Convert int → binary string|`bin(5)` → '0b101'|
|`oct()`|Convert int → octal string|`oct(8)` → '0o10'|
|`hex()`|Convert int → hex string|`hex(255)` → '0xff'|

---

## Real-World Example: File + Encoding + Number Conversions

```Python
# Save character codes to file
text = "ABC😀"

with open("chars.txt", "w", encoding="utf-8") as f:
    for ch in text:
        f.write(f"{ch} -> code {ord(ch)}\n")

# Read file back
with open("chars.txt", "r", encoding="utf-8") as f:
    print(f.read())

# Number formatting
num = 255
print("Binary:", bin(num))      # 0b11111111
print("Octal:", oct(num))       # 0o377
print("Hex:", hex(num))         # 0xff

# Hash for quick integrity check
print("Hash of text:", hash(text))
```