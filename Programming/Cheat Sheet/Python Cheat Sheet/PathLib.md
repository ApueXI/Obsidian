---
Created: 2025-08-23T08:02
tags:
  - Extra
---
## **Basic Imports**

```Python
from pathlib import Path
```

---

## ✅ **Creating Paths**

```Python
p = Path("folder/subfolder/file.txt")   # Relative path
p = Path("/absolute/path/to/file.txt")  # Absolute path
p = Path.home()                         # User's home directory
p = Path.cwd()                          # Current working directory
```

---

## ✅ **Joining Paths**

```Python
p = Path("folder") / "subfolder" / "file.txt"  # Concatenation with /
```

---

## ✅ **Path Properties**

```Python
p.name         # 'file.txt'
p.stem         # 'file' (filename without extension)
p.suffix       # '.txt'
p.suffixes     # ['.tar', '.gz'] for 'file.tar.gz'
p.parent       # Path('folder/subfolder')
p.parents[0]   # Immediate parent
p.parents[1]   # Go up another level
p.anchor       # Root ('C:\\' on Windows, '/' on Unix)
```

---

## ✅ **Checking Paths**

```Python
p.exists()        # True if path exists
p.is_file()       # True if it's a file
p.is_dir()        # True if it's a directory
p.is_symlink()    # True if it's a symbolic link
```

---

## ✅ **Creating & Deleting**

```Python
p.mkdir()                     # Create a directory
p.mkdir(parents=True, exist_ok=True)  # Create all parents if needed
p.touch()                     # Create an empty file
p.unlink()                    # Delete a file
p.rmdir()                     # Remove an empty directory
```

---

## ✅ **Reading & Writing**

```Python
p.write_text("Hello World!")      # Write text to file
content = p.read_text()           # Read text from file
p.write_bytes(b"binary data")     # Write binary
data = p.read_bytes()             # Read binary
```

---

## ✅ **Directory Listing**

```Python
for item in p.iterdir():     # List all files & dirs in path
    print(item)

list(p.glob("*.txt"))        # Find all .txt files
list(p.rglob("*.py"))        # Recursive search for .py files
```

---

## ✅ **Path Resolution**

```Python
p.resolve()        # Get absolute path
p.absolute()       # Absolute path (less strict than resolve)
```

---

## ✅ **Renaming & Moving**

```Python
p.rename("newname.txt")         # Rename/move file
p.replace("newname.txt")        # Like rename, but overwrites if exists
```

---

## ✅ **Path Comparison**

```Python
p1.samefile(p2)    # Check if two paths point to the same file
```

---

## ✅ **Environment Helpers**

```Python
Path.home()    # User's home directory
Path.cwd()     # Current working directory
```

---

## ✅ **Quick Example**

```Python
from pathlib import Path

p = Path("example.txt")
if not p.exists():
    p.write_text("Hello Pathlib!")

print(f"File name: {p.name}")
print(f"Absolute path: {p.resolve()}")
```