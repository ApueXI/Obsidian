---
Created: 2025-08-21T19:29
tags:
  - Regular-Expresisons
---
## ✅ **What is the** `**re**` **Module?**

The `re` module provides **regular expression support** for:

✔️ Searching

✔️ Matching

✔️ Splitting

✔️ Substituting text

---

## 🏗 **Basic Functions**

|Function|Description|
|---|---|
|`re.match()`|Match **at the start** of a string|
|`re.search()`|Find **first occurrence** anywhere|
|`re.findall()`|Return **all matches** as a list|
|`re.finditer()`|Return **iterator of Match objects**|
|`re.split()`|Split string by regex|
|`re.sub()`|Replace matches with another string|
|`re.compile()`|Precompile regex for reuse|

---

## ✅ **Regex Metacharacters**

|Pattern|Meaning|
|---|---|
|`.`|Any character except newline|
|`^`|Start of string|
|`$`|End of string|
|`*`|0 or more|
|`+`|1 or more|
|`?`|0 or 1|
|`{n}`|Exactly n times|
|`{n,}`|At least n times|
|`{n,m}`|Between n and m times|
|`[]`|Character class|
|`|`|
|`()`|Group|
|`\d`|Digit|
|`\w`|Word char|
|`\s`|Whitespace|
|`\b`|Word boundary|
|`\\`|Escape special chars|

---

## 🔹 **Quick Examples**

```Python
python
CopyEdit
import re

text = "Email me at test@example.com or admin@site.org"

# Search for first email
match = re.search(r"\w+@\w+\.\w+", text)
print(match.group())  # test@example.com

# Find all emails
emails = re.findall(r"[\w\.-]+@[\w\.-]+", text)
print(emails)  # ['test@example.com', 'admin@site.org']

# Replace emails with placeholder
censored = re.sub(r"[\w\.-]+@[\w\.-]+", "[hidden]", text)
print(censored)

```

---

## ✅ **Using Groups**

```Python
python
CopyEdit
m = re.search(r"(\d{4})-(\d{2})-(\d{2})", "Today is 2025-07-27")
print(m.group(0))  # Full match → 2025-07-27
print(m.group(1))  # Year → 2025
print(m.group(2))  # Month → 07
print(m.group(3))  # Day → 27

```

---

## ✅ **Precompiling Regex**

If you use a regex multiple times, **compile it** for efficiency:

```Python
python
CopyEdit
pattern = re.compile(r"\d+")
print(pattern.findall("I have 2 cats and 3 dogs"))  # ['2', '3']

```

---

## ⚠️ **Gotchas**

- Always use **raw strings** `**r"..."**` for regex to avoid escaping hell.
- `match()` only checks **start** of the string; use `search()` for anywhere.
- Be careful with **greedy matching** (`.*`) → use `.*?` for non-greedy.

---

## 📌 **Summary Table**

|Function|Use Case|
|---|---|
|`re.match`|Match only at the **start**|
|`re.search`|Find **first occurrence**|
|`re.findall`|Get **all matches**|
|`re.finditer`|Get iterator of matches|
|`re.split`|Split by regex|
|`re.sub`|Replace matches|
|`re.compile`|Precompile for reuse|

---

## 🌍 **Real-World Example: Extracting Phone Numbers**

```Python
python
CopyEdit
import re

contacts = """
Call John at +1-202-555-0178 or Mary at (415) 555-2671.
Office: 212.555.1234
"""

# Regex for phone numbers
phone_pattern = r"(\+?\d{1,2}[-.\s]?)?(\(?\d{3}\)?[-.\s]?)\d{3}[-.\s]?\d{4}"

phones = re.findall(phone_pattern, contacts)
print(["".join(p) for p in phones])

```

Output:

```Plain
css
CopyEdit
['+1-202-555-0178', '(415) 555-2671', '212.555.1234']

```

👉 **Why** `**re**`**?**

- Quick pattern matching for structured text
- Useful for **email/phone extraction, log parsing, data cleaning**

---

✅ **TL;DR:**

- `match` = start only, `search` = anywhere, `findall` = all matches
- Use `()` for groups, `[]` for sets, `+`/ for repetition
- Always use raw strings `r"..."` for readability