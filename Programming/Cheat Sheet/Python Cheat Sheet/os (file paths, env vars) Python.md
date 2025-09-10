---
Created: 2025-08-21T19:29
tags:
  - Optional-Built-in-Tools
---
## ✅ **What is** `**os**`**?**

The `os` module gives you **operating system-level functions**, including:

✔️ **Working with file paths**

✔️ **Accessing environment variables**

---

## 🏗 **1. File Path Operations**

### ✅ **Join Paths Safely**

```Python
import os

path = os.path.join("folder", "subfolder", "file.txt")
print(path)
# Windows → folder\subfolder\file.txt
# Linux/macOS → folder/subfolder/file.txt
```

✔ **Always use** `**os.path.join()**` **instead of hardcoding** `**/**` **or** `**\**`**!**

---

### ✅ **Absolute & Relative Paths**

```Python
print(os.path.abspath("file.txt"))  # Get full absolute path
print(os.path.dirname("/path/to/file.txt"))  # → /path/to
print(os.path.basename("/path/to/file.txt")) # → file.txt
print(os.path.splitext("file.txt"))  # ('file', '.txt')
```

---

### ✅ **Check Paths**

```Python
os.path.exists("file.txt")      # True if exists
os.path.isfile("file.txt")      # True if file
os.path.isdir("folder")         # True if folder
```

---

## 🏗 **2. Environment Variables**

### ✅ **Read Environment Variables**

```Python
import os

print(os.environ.get("HOME"))     # Linux/macOS home dir
print(os.environ.get("USER", "unknown"))  # With default
```

---

### ✅ **Set Environment Variables**

```Python
os.environ["MY_VAR"] = "123"
print(os.environ["MY_VAR"])  # 123
```

---

### ✅ **Remove Environment Variable**

```Python
os.environ.pop("MY_VAR", None)  # Avoid KeyError if missing
```

---

## ✅ **Cross-Platform Path Constants**

|Constant|Meaning|
|---|---|
|`os.sep`|Path separator (`/` or `\`)|
|`os.linesep`|Line separator (`\n` or `\r\n`)|
|`os.pathsep`|Separator for PATH lists (`:` or `;`)|

---

## ⚠️ **Gotchas**

- **Always use** `**os.path.join()**` for portability (Windows vs Linux).
- Changing `os.environ` **only affects the current process**, not the system-wide environment.
- `os.environ` keys are **case-sensitive** on Linux, but **not** on Windows.

---

## 📌 **Summary Table**

|Operation|Function|
|---|---|
|Join paths safely|`os.path.join()`|
|Get absolute path|`os.path.abspath()`|
|Get dir or filename|`os.path.dirname()`, `os.path.basename()`|
|Split filename & extension|`os.path.splitext()`|
|Check existence/file/dir|`os.path.exists()/isfile()/isdir()`|
|Get env var|`os.environ.get("VAR")`|
|Set env var|`os.environ["VAR"] = "value"`|
|Remove env var|`os.environ.pop("VAR", None)`|

---

## 🌍 **Real-World Example: Configurable App Path**

```Python
import os

# Get config dir from ENV, fallback to default
config_dir = os.environ.get("APP_CONFIG", os.path.join(os.getcwd(), "config"))

# Ensure folder exists
if not os.path.exists(config_dir):
    os.makedirs(config_dir)

config_file = os.path.join(config_dir, "settings.json")

print("Config file will be:", config_file)
```

Running:

```Shell
export APP_CONFIG=/tmp/myapp   # Linux/macOS
# set APP_CONFIG=C:\temp\myapp # Windows
python app.py
```

Output:

```Plain
Config file will be: /tmp/myapp/settings.json
```

👉 **Why?**

- Lets you **override paths via environment variables** while staying cross-platform.

---

✅ **TL;DR:**

- `os.path.join()` → safe cross-platform paths
- `os.environ.get()` → read environment variables
- `os.environ["VAR"] = "x"` → set them
- `os.path.exists()` → check before use