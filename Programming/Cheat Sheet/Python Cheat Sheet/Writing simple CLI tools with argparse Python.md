---
Created: 2025-08-21T19:29
tags:
  - Extra
---
## ✅ **What is** `**argparse**`**?**

`argparse` is the **standard library** for building **command-line interfaces (CLI)** in Python.

✔ Handles **command-line arguments**

✔ Generates **help messages** automatically

✔ Supports **flags, options, and positional args**

---

## 🏗 **1. Basic CLI Tool**

```Python
import argparse

parser = argparse.ArgumentParser(description="Simple CLI Example")
parser.add_argument("name", help="Your name")  # positional arg
args = parser.parse_args()

print(f"Hello, {args.name}!")
```

Run it:

```Shell
python app.py Alice
```

Output:

```Plain
Hello, Alice!
```

---

## 🏗 **2. Optional Arguments (Flags)**

```Python
parser.add_argument("--age", type=int, help="Your age")
args = parser.parse_args()

if args.age:
    print(f"You are {args.age} years old.")
```

Run:

```Shell
python app.py Alice --age 30
```

Output:

```Plain
Hello, Alice!
You are 30 years old.
```

---

## 🏗 **3. Boolean Flags**

```Python
parser.add_argument("--verbose", action="store_true", help="Enable verbose mode")
args = parser.parse_args()

if args.verbose:
    print("Verbose mode is ON")
```

Run:

```Shell
python app.py Alice --verbose
```

---

## 🏗 **4. Default Values**

```Python
parser.add_argument("--city", default="Unknown", help="Your city")
args = parser.parse_args()
print(f"City: {args.city}")
```

Run:

```Shell
python app.py Alice
# City: Unknown
```

---

## ✅ **Key** `**add_argument()**` **Options**

|Option|What it does|
|---|---|
|`help="text"`|Help message|
|`type=int`|Convert to int/float/etc.|
|`default=val`|Default value if missing|
|`choices=[...]`|Restrict allowed values|
|`required=True`|Make optional arg mandatory|
|`action="store_true"`|Boolean flag|

---

## ✅ **Auto-Generated Help**

Every `argparse` CLI gets **help for free**:

```Shell
python app.py --help
```

Output:

```Plain
usage: app.py [-h] [--age AGE] name

Simple CLI Example

positional arguments:
  name        Your name

optional arguments:
  -h, --help  show this help message and exit
  --age AGE   Your age
```

---

## ⚠️ **Gotchas**

- Positional args are **required by default**.
- Optional args must start with `-` or .
- `argparse` **exits the program** with an error if invalid args are passed.

---

## 📌 **Summary Table**

|Feature|Example|
|---|---|
|Positional arg|`parser.add_argument("name")`|
|Optional arg|`parser.add_argument("--age")`|
|Boolean flag|`parser.add_argument("--verbose", action="store_true")`|
|Default value|`parser.add_argument("--city", default="NY")`|
|Choices limit|`parser.add_argument("--mode", choices=["dev","prod"])`|
|Auto-help|`python app.py --help`|

---

## 🌍 **Real-World Example: Simple File Copier**

```Python
import argparse, shutil

parser = argparse.ArgumentParser(description="Copy a file")
parser.add_argument("src", help="Source file")
parser.add_argument("dst", help="Destination file")
parser.add_argument("--backup", action="store_true", help="Keep a backup")

args = parser.parse_args()

if args.backup:
    shutil.copy2(args.src, args.src + ".bak")
    print("Backup created:", args.src + ".bak")

shutil.copy2(args.src, args.dst)
print(f"Copied {args.src} → {args.dst}")
```

Run:

```Shell
python copy.py file.txt copy.txt --backup
```

Output:

```Plain
Backup created: file.txt.bak
Copied file.txt → copy.txt
```

---

✅ **TL;DR:**

- `argparse` makes building **CLI tools easy**
- Positional args = required
- `-flags` = optional args
- `action="store_true"` for boolean flags
- Auto `-help` generation