---
Created: 2025-08-21T19:29
tags:
  - Optional-Built-in-Tools
---
## ✅ **What is** `**subprocess**`**?**

The `subprocess` module allows you to **run external commands & programs** from Python.

✔️ Used to execute shell commands

✔️ Capture their **output**, **errors**, and **exit codes**

---

## 🏗 **1. Running a Simple Command**

```Python
import subprocess

subprocess.run(["echo", "Hello World"])
```

Output:

```Plain
Hello World
```

✔ Recommended: Pass command as a **list** (safer).

---

## 🏗 **2. Capturing Output**

```Python
result = subprocess.run(["echo", "Hi"], capture_output=True, text=True)

print(result.stdout)  # ✅ Hi\n
print(result.returncode)  # ✅ 0 (success)
```

✔ Use `capture_output=True` and `text=True` for **string output**.

---

## 🏗 **3. Running with Shell**

```Python
subprocess.run("echo Hello && echo World", shell=True)
```

⚠️ `shell=True` allows **shell features** but can be **security risk** with user input!

---

## 🏗 **4. Getting Exit Code**

```Python
result = subprocess.run(["ls", "nonexistent"], capture_output=True, text=True)
print(result.returncode)  # non-zero → error
print(result.stderr)      # error message
```

---

## ✅ **Older Way:** `**subprocess.Popen**`

For more control (streaming output, async):

```Python
proc = subprocess.Popen(["ping", "-c", "2", "example.com"],
                        stdout=subprocess.PIPE, stderr=subprocess.PIPE, text=True)

out, err = proc.communicate()
print(out)
```

---

## ✅ **Shortcut:** `**subprocess.check_output**`

If you only want the output (and raise error on failure):

```Python
out = subprocess.check_output(["echo", "Hello"], text=True)
print(out)  # Hello
```

---

## ⚠️ **Gotchas**

- Prefer passing **list of args** (`["ls", "-l"]`) over shell strings (`"ls -l"`) for safety.
- If you need **shell features** (pipes, &&), use `shell=True` but sanitize input!
- Always check `returncode` for success/failure.

---

## 📌 **Summary Table**

|Function|What it does|
|---|---|
|`subprocess.run(cmd)`|Run command, wait for completion|
|`capture_output=True`|Capture stdout & stderr|
|`text=True`|Decode output as string|
|`shell=True`|Run through shell (use carefully)|
|`returncode`|Exit status of command|
|`stdout`, `stderr`|Captured output/error|
|`check_output(cmd)`|Get only stdout, raise on error|

---

## 🌍 **Real-World Example: Cross-Platform** `**ping**`

```Python
import subprocess, sys

host = "google.com"
cmd = ["ping", "-n", "2", host] if sys.platform.startswith("win") else ["ping", "-c", "2", host]

result = subprocess.run(cmd, capture_output=True, text=True)

if result.returncode == 0:
    print("✅ Host reachable!")
    print(result.stdout)
else:
    print("❌ Host unreachable!")
    print(result.stderr)
```

Output:

```Plain
✅ Host reachable!
PING google.com ...
```

👉 **Why?**

- Works **cross-platform**, checks network connectivity programmatically.

---

✅ **TL;DR:**

- Use `subprocess.run(["cmd", "arg"], capture_output=True, text=True)` for simple cases
- Use `check_output()` for just output
- Use `Popen` for **advanced control**
- Avoid `shell=True` unless necessary