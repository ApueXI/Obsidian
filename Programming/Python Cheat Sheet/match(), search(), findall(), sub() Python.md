---
Created: 2025-08-21T19:29
tags:
  - Regular-Expresisons
---
## ✅ **Quick Overview**

|Function|What it does|
|---|---|
|`match()`|Match **only at the start** of the string|
|`search()`|Find **first match anywhere** in the string|
|`findall()`|Return **all matches** as a list|
|`sub()`|Replace all matches with another string|

---

## 🏗 **1.** `**re.match()**` **→ Only Start of String**

```Python
import re

print(re.match(r"\d+", "123abc").group())  # ✅ 123
print(re.match(r"\d+", "abc123"))         # ❌ None (not at start)
```

➡ **Only works if the pattern is at the beginning of the string.**

---

## 🏗 **2.** `**re.search()**` **→ First Match Anywhere**

```Python
m = re.search(r"\d+", "abc123xyz456")
print(m.group())  # ✅ 123 (first match)
```

➡ **Finds the first occurrence** anywhere in the string.

---

## 🏗 **3.** `**re.findall()**` **→ All Matches**

```Python
print(re.findall(r"\d+", "abc123xyz456"))
# ['123', '456']
```

➡ Returns a **list** of all matches.

---

## 🏗 **4.** `**re.sub()**` **→ Replace Matches**

```Python
text = "My phone is 123-456-7890"
censored = re.sub(r"\d", "*", text)
print(censored)  # My phone is ***-***-****
```

➡ Replace all matches with a replacement string.

---

## ✅ **Using Groups**

With `match()` / `search()`, you can get **groups**:

```Python
m = re.search(r"(\d{3})-(\d{3})-(\d{4})", "Call 123-456-7890")
print(m.group(0))  # Full match → 123-456-7890
print(m.group(1))  # First group → 123
print(m.group(2))  # Second group → 456
print(m.group(3))  # Third group → 7890
```

---

## ⚠️ **Gotchas**

- **Always use raw strings** `r"..."` to avoid double escaping.
- `match()` only matches at **start**, use `search()` for anywhere.
- `findall()` returns **strings** (or tuples if groups).
- `sub()` replaces **all occurrences**, not just the first.

---

## 📌 **Summary Table**

|Function|Use Case|
|---|---|
|`match()`|Match **start** of string|
|`search()`|Find **first occurrence**|
|`findall()`|Find **all occurrences**|
|`sub()`|Replace matches|

---

## 🌍 **Real-World Example: Censoring Emails**

```Python
import re

text = """
Contact john.doe@example.com and admin@mysite.org for details.
"""

# Regex for emails
email_pattern = r"[\w\.-]+@[\w\.-]+\.\w+"

# 1️⃣ Find first email
m = re.search(email_pattern, text)
print("First email:", m.group())

# 2️⃣ Find all emails
emails = re.findall(email_pattern, text)
print("All emails:", emails)

# 3️⃣ Replace emails with [hidden]
censored = re.sub(email_pattern, "[hidden]", text)
print("Censored text:", censored)
```

Output:

```Plain
First email: john.doe@example.com
All emails: ['john.doe@example.com', 'admin@mysite.org']
Censored text:
Contact [hidden] and [hidden] for details.
```

---

✅ **TL;DR:**

- `match()` → only beginning
- `search()` → first match anywhere
- `findall()` → all matches as a list
- `sub()` → replace matches