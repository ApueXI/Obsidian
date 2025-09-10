---
Created: 2025-08-21T19:29
tags:
  - File-I/O
---
## 1. Opening a File

```Python
f = open("file.txt", "r")  # open for reading
f.close()                  # always close!
```

✅ **Better way (auto-closes):**

```Python
with open("file.txt", "r") as f:
    content = f.read()
```

---

## 2. File Modes

|Mode|Meaning|
|---|---|
|`"r"`|**Read** (default) – file must exist|
|`"w"`|**Write** (overwrites existing file or creates new)|
|`"a"`|**Append** (adds to the end of file)|
|`"x"`|**Create new file** (fails if exists)|
|`"r+"`|Read & write|
|`"w+"`|Write & read (overwrites)|
|`"a+"`|Append & read|

For **text mode (default)** vs **binary mode** → add `"b"` (`"rb"`, `"wb"`).

---

## 3. Reading from a File

```Python
with open("file.txt", "r") as f:
    data = f.read()        # Read entire file as string
    # OR:
    # data = f.readline()  # Read one line
    # data = f.readlines() # Read all lines into a list
```

✅ Example:

```Python
with open("file.txt", "r") as f:
    for line in f:
        print(line.strip())  # iterate line by line
```

---

## 4. Writing to a File

```Python
with open("file.txt", "w") as f:
    f.write("Hello, World!\n")
    f.write("Another line.\n")
```

- `"w"` **overwrites** the file
- `"a"` **appends** instead

---

## 5. Appending to a File

```Python
with open("file.txt", "a") as f:
    f.write("This will be added at the end.\n")
```

---

## 6. Checking File Position

```Python
with open("file.txt", "r") as f:
    print(f.tell())     # current position
    f.seek(0)           # move to beginning
```

---

## 7. Best Practice → Use `with`

- **Automatically closes** the file, even on errors.
- Prevents resource leaks.

```Python
with open("data.txt", "r") as f:
    content = f.read()
```

---

## Summary Table

|Method|Purpose|Example|
|---|---|---|
|`open(file,mode)`|Open a file in a given mode|`open("file.txt","r")`|
|`read()`|Read entire file as string|`f.read()`|
|`readline()`|Read one line|`f.readline()`|
|`readlines()`|Read all lines into list|`f.readlines()`|
|`write()`|Write text to file|`f.write("Hello")`|
|`seek()`|Move file pointer|`f.seek(0)`|
|`tell()`|Get current pointer position|`f.tell()`|
|`with open()`|Best practice for auto-close|`with open(...) as f:`|

---

## Real-World Examples

---

### ✅ Reading a Config File

```Python
with open("config.txt", "r") as f:
    for line in f:
        key, value = line.strip().split("=")
        print(f"{key} -> {value}")
```

---

### ✅ Saving Logs

```Python
log_msg = "Server started\n"
with open("server.log", "a") as f:
    f.write(log_msg)
```

---

### ✅ Copying a Text File

```Python
with open("source.txt", "r") as src, open("backup.txt", "w") as dst:
    dst.write(src.read())
```

---

### ✅ Reading a File into a List

```Python
with open("names.txt", "r") as f:
    names = [line.strip() for line in f]

print(names)
```

---

## Key Points

- Always use `**with open()**` to avoid forgetting `close()`.
- Choose mode carefully: `"r"` for read, `"w"` for overwrite, `"a"` for append.
- Use `read()` for the whole file, `readline()` for one line, `readlines()` for all lines as list.