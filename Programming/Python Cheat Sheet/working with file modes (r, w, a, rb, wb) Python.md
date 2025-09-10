---
Created: 2025-08-21T19:29
tags:
  - File-I/O
---
## 1. File Modes Overview

|Mode|Meaning|
|---|---|
|`"r"`|**Read** (default) – file must exist|
|`"w"`|**Write** – overwrites file or creates new|
|`"a"`|**Append** – adds to end of file, creates if missing|
|`"x"`|**Exclusive creation** – fails if file exists|
|`"r+"`|**Read + Write** (file must exist)|
|`"w+"`|**Write + Read** (overwrites existing)|
|`"a+"`|**Append + Read**|
|`"b"`|Binary mode (combine with others, e.g., `"rb"`, `"wb"`)|

---

## 2. Basic Modes

### **Reading (**`**r**`**)**

```Python
with open("file.txt", "r") as f:
    print(f.read())  # reads entire file
```

- **Fails if file doesn’t exist**

---

### **Writing (**`**w**`**)**

```Python
with open("file.txt", "w") as f:
    f.write("Overwrites existing content!\n")
```

- Creates file if missing
- **Overwrites** if it exists

---

### **Appending (**`**a**`**)**

```Python
with open("file.txt", "a") as f:
    f.write("This is added at the end.\n")
```

- **Adds new content** at the end
- Creates file if missing

---

### **Read & Write (**`**r+**`**)**

```Python
with open("file.txt", "r+") as f:
    data = f.read()
    f.write("\nNew content")
```

- File **must exist**
- Can **read + write**, but does **not truncate**

---

### **Write & Read (**`**w+**`**)**

```Python
with open("file.txt", "w+") as f:
    f.write("New data")
    f.seek(0)           # move to start
    print(f.read())
```

- **Overwrites** file first
- Then allows reading

---

### **Append & Read (**`**a+**`**)**

```Python
with open("file.txt", "a+") as f:
    f.write("\nAnother line")
    f.seek(0)
    print(f.read())  # can read but always writes at the end
```

---

## 3. Binary Modes

- Add `"b"` for **binary data** (e.g., images, PDFs).

```Python
# Reading binary
with open("image.png", "rb") as f:
    img_data = f.read()

# Writing binary
with open("copy.png", "wb") as f:
    f.write(img_data)
```

✅ Useful for **images, videos, pickled objects, PDFs**

---

## 4. Exclusive Creation (`x`)

```Python
python
CopyEdit
with open("newfile.txt", "x") as f:
    f.write("Created new file")
```

- Fails if file already exists

---

## Summary Table

|Mode|Read|Write|Creates File?|Overwrites?|Appends?|
|---|---|---|---|---|---|
|`r`|✅|❌|❌ (must exist)|❌|❌|
|`w`|❌|✅|✅|✅|❌|
|`a`|❌|✅|✅|❌|✅|
|`r+`|✅|✅|❌ (must exist)|❌|❌|
|`w+`|✅|✅|✅|✅|❌|
|`a+`|✅|✅|✅|❌|✅|
|`x`|❌|✅|✅ (fails if exists)|❌|❌|
|`b`|Works with binary (combine)|`rb`, `wb`, etc.||||

---

## Real-World Examples

---

### ✅ Copying a Text File

```Python
with open("source.txt", "r") as src, open("copy.txt", "w") as dst:
    dst.write(src.read())
```

---

### ✅ Appending Logs

```Python
with open("log.txt", "a") as log:
    log.write("New log entry\n")
```

---

### ✅ Reading & Writing at Same Time

```Python
with open("data.txt", "r+") as f:
    content = f.read()
    f.seek(0)
    f.write("UPDATED\n" + content)
```

---

### ✅ Copying a Binary File (e.g., image)

```Python
with open("photo.jpg", "rb") as src, open("backup.jpg", "wb") as dst:
    dst.write(src.read())
```

---

### ✅ Safe File Creation

```Python
try:
    with open("newfile.txt", "x") as f:
        f.write("This file is new!")
except FileExistsError:
    print("File already exists!")
```

---

## Key Points

- Use `**with open()**` → auto-closes files safely.
- Use `"r"` when reading only, `"w"` when overwriting, `"a"` when appending.
- Add `"b"` for **binary files** like images.
- Use `"x"` to create new file safely.