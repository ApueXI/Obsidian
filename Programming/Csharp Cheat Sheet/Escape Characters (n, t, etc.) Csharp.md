---
Created: 2025-08-07T20:10
tags:
  - String-Manipulation
---
Escape characters are **special sequences** starting with a backslash `\` used in string literals to represent characters that are hard or impossible to type directly.

---

## 🔑 Most Common Escape Characters

|Escape Code|Description|Example|Output Example|
|---|---|---|---|
|`\n`|New line|`"Line1\nLine2"`|Line1Line2|
|`\t`|Horizontal tab|`"A\tB"`|A  B|
|`\\`|Backslash|`"C:\\Files"`|C:\Files|
|`\"`|Double quote|`"She said, \"Hello!\""`|She said, "Hello!"|
|`\'`|Single quote|`'\'A\''`|'A'|
|`\r`|Carriage return|`"Hello\rWorld"`|World (overwrites `Hello`)|
|`\b`|Backspace (removes previous char)|`"abc\b"`|ab|
|`\f`|Form feed (page break - rarely used)|`"Text\fNext"`|Output may vary|
|`\0`|Null character (char value 0)|`"end\0"`|Often not visible|

---

## 🧠 Example

```C#
Console.WriteLine("Hello\tWorld\nLine2");
```

**Output:**

```Plain
Hello   World
Line2
```

---

## 🧱 Verbatim Strings (disable escape parsing)

Prefix with `@` to **disable escape sequences** (except `""` for quotes):

```C#
string path = @"C:\Users\Public";   // no need for double backslashes
```

But newlines, tabs, etc., won't work:

```C#
string raw = @"Line1\nLine2"; // Literal \n, not new line
```

---

## ✍️ Escape in Single and Double Quotes

|Use case|String literal|Output|
|---|---|---|
|Quote inside string|`"She said, \"Hi\""`|She said, "Hi"|
|Path in Windows|`"C:\\Windows\\System"`|C:\Windows\System|

---

## 📋 Summary Table

|Character|Purpose|Read As|
|---|---|---|
|`\n`|Newline|Line break|
|`\t`|Tab|Horizontal tab|
|`\\`|Backslash|`\`|
|`\"`|Double quote|`"`|
|`\'`|Single quote|`'`|
|`\r`|Carriage return|CR (overwrites)|
|`\b`|Backspace|Delete 1 char back|
|`\0`|Null char|ASCII 0|
|`\f`|Form feed|Page break|

---

## 🧪 Real-World Example

```C#
string report = "Name\tScore\nJohn\t95\nJane\t99";
Console.WriteLine(report);
```

**Output:**

```Plain
Name    Score
John    95
Jane    99
```