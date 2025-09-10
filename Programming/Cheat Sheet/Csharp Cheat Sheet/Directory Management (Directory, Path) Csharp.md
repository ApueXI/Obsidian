---
Created: 2025-08-07T20:10
tags:
  - File-&-Directory-I/O
---
## 🔧 Namespace

```C#
using System.IO;
```

---

## 📁 `Directory` Class – Manage Folders

|Function|Purpose|
|---|---|
|`CreateDirectory(path)`|Creates a new folder (recursive)|
|`Exists(path)`|Checks if a directory exists|
|`Delete(path)`|Deletes a folder|
|`GetFiles(path)`|Lists all files in a directory|
|`GetDirectories(path)`|Lists all subdirectories|
|`Move(source, dest)`|Moves or renames a directory|

### ✅ Example: Create, Check, Delete

```C#
string folderPath = @"C:\MyFolder";

if (!Directory.Exists(folderPath))
    Directory.CreateDirectory(folderPath);

Console.WriteLine("Created: " + folderPath);

// Delete the folder
Directory.Delete(folderPath, recursive: true);
```

---

## 📁 List Files and Subdirectories

```C#
string[] files = Directory.GetFiles(@"C:\MyFolder");
string[] subDirs = Directory.GetDirectories(@"C:\MyFolder");

foreach (var file in files)
    Console.WriteLine("File: " + file);

foreach (var dir in subDirs)
    Console.WriteLine("Subdir: " + dir);
```

---

## 📁 Move/Rename Folder

```C#
Directory.Move(@"C:\OldFolder", @"C:\NewFolderName");
```

---

## 📁 `Path` Class – Manipulate Path Strings

|Method|Description|
|---|---|
|`Combine(a, b)`|Safely joins paths|
|`GetDirectoryName(path)`|Returns directory of a file|
|`GetFileName(path)`|Gets the file name from path|
|`GetExtension(path)`|Gets file extension|
|`GetFullPath(path)`|Returns absolute path|
|`ChangeExtension(path, ".new")`|Changes file extension|

### ✅ Example: Path Utilities

```C#
string fullPath = Path.Combine("C:\\Users", "Documents", "file.txt");
Console.WriteLine(fullPath);  // Output: C:\Users\Documents\file.txt

string fileName = Path.GetFileName(fullPath);         // file.txt
string dirName = Path.GetDirectoryName(fullPath);     // C:\Users\Documents
string extension = Path.GetExtension(fullPath);        // .txt
```

---

## 📋 Summary Table

|Task|Method|Notes|
|---|---|---|
|Create a folder|`Directory.CreateDirectory(path)`|Recursive creation allowed|
|Check folder existence|`Directory.Exists(path)`|Returns true/false|
|Delete a folder|`Directory.Delete(path, true)`|Use `true` for recursive|
|List files in a folder|`Directory.GetFiles(path)`|Returns array of paths|
|List subdirectories|`Directory.GetDirectories(path)`|Returns array of paths|
|Move/Rename directory|`Directory.Move(source, dest)`|Overwrites if exists|
|Join paths|`Path.Combine(...)`|Safe for cross-platform|
|Extract file info from path|`Path.GetFileName(path)` etc.|Use for parsing|

---

## 🔐 Gotchas

|Gotcha|Explanation|
|---|---|
|Invalid characters|Use `Path.GetInvalidPathChars()` to validate|
|Permissions|May throw `UnauthorizedAccessException`|
|Relative paths|Use `Path.GetFullPath()` to resolve|
|Deleting non-empty|Use `recursive: true` when deleting folders|

---

## 🧠 Real-World Use Case

```C#
string backupFolder = Path.Combine(Environment.CurrentDirectory, "Backup");

if (!Directory.Exists(backupFolder))
    Directory.CreateDirectory(backupFolder);

string sourceFile = "data.txt";
string destFile = Path.Combine(backupFolder, "data_backup.txt");

File.Copy(sourceFile, destFile, overwrite: true);
Console.WriteLine("Backup completed.");
```