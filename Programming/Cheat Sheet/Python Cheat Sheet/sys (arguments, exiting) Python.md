---
Created: 2025-08-21T19:29
tags:
  - Optional-Built-in-Tools
---
## ✅ **What is** `**sys**`**?**

The `sys` module provides **system-specific parameters and functions**, including:

✔️ **Command-line arguments**

✔️ **Exiting the program**

✔️ Access to interpreter info

We’ll focus on **arguments** and **exiting**.

---

## 🏗 **1.** `**sys.argv**` **→ Command-Line Arguments**

- `sys.argv` is a **list of strings** representing command-line arguments.
- `sys.argv[0]` is the **script name**.
- `sys.argv[1:]` are the **extra arguments**.

```Python
import sys

print("Script name:", sys.argv[0])
print("Arguments:", sys.argv[1:])
```

Running:

```Shell
python myscript.py hello world
```

Output:

```Plain
Script name: myscript.py
Arguments: ['hello', 'world']
```

---

## 🏗 **2.** `**sys.exit([status])**` **→ Exit Program**

- `sys.exit(0)` → normal exit
- `sys.exit(1)` → error exit (non-zero = failure)
- `sys.exit("message")` → prints message then exits with status `1`

```Python
import sys

if len(sys.argv) < 2:
    print("Missing argument!")
    sys.exit(1)  # Exit with error

print("Running normally...")
sys.exit(0)  # Normal exit
```

---

## ✅ **Exit Codes**

|Code|Meaning|
|---|---|
|`0`|Success|
|`1`|Generic error|
|other|Custom exit reason|

---

## ⚠️ **Gotchas**

- `sys.exit()` **raises** `**SystemExit**`, so you can catch it.
- If you don’t catch it, it terminates the program.

```Python
try:
    sys.exit("Something went wrong!")
except SystemExit as e:
    print("Caught exit:", e)
```

---

## 📌 **Summary Table**

|Function|Description|
|---|---|
|`sys.argv`|List of command-line arguments|
|`sys.argv[0]`|Script name|
|`sys.argv[1:]`|Extra args|
|`sys.exit(code)`|Exit program with status code|

---

## 🌍 **Real-World Example: CLI Script**

```Python
import sys

def main():
    if len(sys.argv) != 3:
        print(f"Usage: python {sys.argv[0]} <name> <age>")
        sys.exit(1)

    name = sys.argv[1]
    age = sys.argv[2]
    print(f"Hello {name}, you are {age} years old!")

    if int(age) < 18:
        sys.exit("You must be 18+ to continue.")

    print("Welcome to the system!")

if __name__ == "__main__":
    main()
```

Running:

```Shell
python app.py Alice 17
```

Output:

```Plain
Hello Alice, you are 17 years old!
You must be 18+ to continue.
```

---

✅ **TL;DR:**

- `sys.argv` → list of command-line args
- `sys.exit()` → exit program with optional status or message
- Non-zero exit code = **error**