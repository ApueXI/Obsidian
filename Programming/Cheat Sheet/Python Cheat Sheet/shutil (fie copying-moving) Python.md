---
Created: 2025-08-21T19:29
tags:
  - Optional-Built-in-Tools
---
## ✅ **What is** `**shutil**`**?**

The `shutil` module provides **high-level file operations** such as copying, moving, deleting files and directories.

✔️ Easier than using low-level `os` functions for file operations.

---

## 🏗 **1. Copy Files**

- **Copy file content and permissions**:

```Python
import shutil

shutil.copy("source.txt", "destination.txt")
```

- **Copy file content only (no metadata):**

```Python
shutil.copyfile("source.txt", "destination.txt")
```

- **Copy file plus metadata (permissions, timestamps):**

```Python
shutil.copy2("source.txt", "destination.txt")
```

---

## 🏗 **2. Copy Directories**

- Copy entire directory tree:

```Python
shutil.copytree("src_folder", "dest_folder")
```

⚠️ `dest_folder` must **not exist**.

---

## 🏗 **3. Move or Rename Files/Directories**

```Python
shutil.move("old_path.txt", "new_path.txt")
```

Works for both files and directories.

---

## 🏗 **4. Delete Files or Directories**

- Delete a file:

```Python
import os
os.remove("file.txt")
```

- Delete a directory tree:

```Python
shutil.rmtree("folder_to_delete")
```

---

## ✅ **Common Use Cases**

|Operation|Function|Notes|
|---|---|---|
|Copy file (content + permissions)|`shutil.copy()`|Destination can be a directory|
|Copy file (content only)|`shutil.copyfile()`|Destination must be file path|
|Copy file + metadata|`shutil.copy2()`|Includes timestamps, permissions|
|Copy folder tree|`shutil.copytree()`|Destination folder must NOT exist|
|Move/Rename file or folder|`shutil.move()`|Moves or renames files/folders|
|Delete directory tree|`shutil.rmtree()`|Be careful: permanent deletion|

---

## ⚠️ **Gotchas**

- `copytree()` **fails if destination exists**. Use `dirs_exist_ok=True` in Python 3.8+ to allow overwriting:

```Python
shutil.copytree("src", "dst", dirs_exist_ok=True)
```

- Always **handle exceptions** like `FileNotFoundError`, `PermissionError` for robust code.
- `rmtree()` **deletes recursively and permanently** — use with care!

---

## 🌍 **Real-World Example: Backup Folder**

```Python
import shutil
import os
import datetime

src_folder = "my_project"
backup_folder = f"backup_{datetime.datetime.now().strftime('%Y%m%d_%H%M%S')}"

try:
    shutil.copytree(src_folder, backup_folder)
    print(f"Backup successful: {backup_folder}")
except FileExistsError:
    print("Backup folder already exists!")
except Exception as e:
    print("Error during backup:", e)
```

---

## 📌 **Summary Table**

|Function|Description|
|---|---|
|`shutil.copy(src, dst)`|Copy file content + permissions|
|`shutil.copyfile(src, dst)`|Copy file content only|
|`shutil.copy2(src, dst)`|Copy file + metadata|
|`shutil.copytree(src, dst)`|Copy entire directory tree|
|`shutil.move(src, dst)`|Move or rename file or folder|
|`shutil.rmtree(path)`|Recursively delete directory|

---

✅ **TL;DR:**

- Use `copy()` to copy files (with permissions)
- Use `copytree()` to copy folders recursively
- Use `move()` to move or rename files/folders
- Use `rmtree()` to delete directories fully (careful!)