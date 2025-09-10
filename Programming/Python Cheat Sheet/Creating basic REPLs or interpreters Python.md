---
Created: 2025-08-21T19:29
tags:
  - Extra
---
## ✅ **What is a REPL?**

REPL = **Read-Eval-Print Loop**

✔ Reads user input

✔ Evaluates it

✔ Prints the result

✔ Loops until exit

You can build **mini interactive shells** or **interpreters** in Python.

---

## 🏗 **1. Simplest REPL**

```Python
while True:
    cmd = input(">>> ")  # Read
    if cmd.strip() in {"exit", "quit"}:
        break
    print(eval(cmd))  # Eval & Print
```

Run:

```Plain
>>> 1 + 2
3
>>> len("hello")
5
>>> quit
```

⚠ **Danger!** `eval()` can execute arbitrary code → insecure for untrusted input.

---

## 🏗 **2. Safer Command REPL**

```Python
def run_command(cmd):
    if cmd == "hello":
        return "Hi there!"
    elif cmd == "help":
        return "Available commands: hello, help, exit"
    else:
        return "Unknown command"

while True:
    cmd = input("> ").strip()
    if cmd in {"exit", "quit"}:
        print("Goodbye!")
        break
    print(run_command(cmd))
```

Run:

```Plain
> hello
Hi there!
> help
Available commands: hello, help, exit
> exit
Goodbye!
```

---

## 🏗 **3. Using** `**code**` **Module for an Interactive Console**

```Python
import code

# Launch a Python interpreter with custom context
vars = {"message": "Hello REPL!"}
code.interact(local=vars)
```

Run:

```Plain
Python 3.x console
>>> print(message)
Hello REPL!
>>> 2 + 3
5
```

---

## ✅ **Enhancing REPL**

- **History & editing** → use `readline` module (on Linux/macOS)
- **Autocomplete** → use `cmd` module for structured commands
- **Custom prompt** → modify prompt strings

---

## ✅ **Using** `**cmd**` **Module for Structured CLI**

`cmd` helps build **interactive CLI shells** easily.

```Python
import cmd

class MyShell(cmd.Cmd):
    prompt = "myshell> "

    def do_hello(self, arg):
        """Say hello"""
        print("Hello,", arg or "world!")

    def do_exit(self, arg):
        """Exit shell"""
        print("Bye!")
        return True  # Returning True exits loop

MyShell().cmdloop()
```

Run:

```Plain
myshell> hello Alice
Hello, Alice
myshell> hello
Hello, world!
myshell> exit
Bye!
```

---

## ⚠️ **Gotchas**

- `eval()` is powerful but **not safe** → only use in trusted environments.
- For complex REPLs, use `cmd` module instead of manual loops.
- Long-running REPLs may need **signal handling** (e.g., Ctrl+C).

---

## 📌 **Summary Table**

|Approach|When to use|
|---|---|
|`eval()` loop|Quick & dirty REPL for trusted code|
|Manual parser|Safer custom commands|
|`code.interact()`|Drop into Python console|
|`cmd` module|Structured CLI shell with built-in help|

---

## 🌍 **Real-World Example: Mini Calculator REPL**

```Python
def calc(expr):
    try:
        return eval(expr, {"__builtins__": {}}, {})
    except Exception as e:
        return f"Error: {e}"

print("Simple Calculator REPL (type 'exit' to quit)")
while True:
    expr = input("calc> ")
    if expr.strip() in {"exit", "quit"}:
        break
    print(calc(expr))
```

Run:

```Plain
calc> 2 + 3 * 4
14
calc> (10/2) + 5
10.0
calc> quit
```

👉 **Why?**

- Shows **REPL concept** (read → eval → print → loop).
- Uses **restricted eval** for slightly safer execution.

---

✅ **TL;DR:**

- Basic REPL = `while True → input() → eval() → print()`
- Use `cmd` for **structured interactive shells**
- `code.interact()` drops into a real Python console