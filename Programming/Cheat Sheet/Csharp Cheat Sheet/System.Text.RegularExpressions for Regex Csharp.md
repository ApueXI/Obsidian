---
Created: 2025-08-07T20:10
tags:
  - Optional
---
## ✅ 1. Concept Overview

**Regular Expressions (Regex)** are patterns used to match, search, or replace strings.

C# uses the `System.Text.RegularExpressions` namespace, with core classes:

- `Regex`: Represents the pattern and provides methods
- `Match`, `MatchCollection`: Hold match results
- `Group`, `GroupCollection`: Represent submatches (capturing groups)

```C#
using System.Text.RegularExpressions;
```

---

## 🔧 2. Common Use Cases

- Validate email, phone, password, etc.
- Extract data from strings (e.g., HTML, logs)
- Find/replace values in text
- Split strings by custom rules

---

## 🧪 3. Key Classes and Methods

### 🔹 Create a Regex:

```C#
Regex regex = new Regex(@"\d+");
```

Or use static methods:

```C#
Regex.IsMatch(input, pattern);
Regex.Match(input, pattern);
Regex.Matches(input, pattern);
Regex.Replace(input, pattern, replacement);
Regex.Split(input, pattern);
```

---

## 🧾 4. Summary Table of Methods

|Method|Purpose|Returns|
|---|---|---|
|`IsMatch`|Checks if input matches regex|`bool`|
|`Match`|Returns first match|`Match` object|
|`Matches`|Returns all matches|`MatchCollection`|
|`Replace`|Replaces matched patterns|Modified string|
|`Split`|Splits string by pattern|`string[]`|

---

## 📐 5. Summary Table of Regex Patterns

|Pattern|Meaning|
|---|---|
|`.`|Any character except newline|
|`\d`|Digit (0–9)|
|`\D`|Non-digit|
|`\w`|Word character (A-Z, a-z, 0–9, _)|
|`\W`|Non-word character|
|`\s`|Whitespace|
|`\S`|Non-whitespace|
|`^`|Start of string|
|`$`|End of string|
|`*`|0 or more|
|`+`|1 or more|
|`?`|0 or 1|
|`{n}`|Exactly n|
|`{n,}`|n or more|
|`{n,m}`|Between n and m|
|`(abc)`|Capturing group|
|`(?:abc)`|Non-capturing group|
|`\|`|OR|
|`[abc]`|Match a, b, or c|
|`[^abc]`|Not a, b, or c|
|`(?<name>...)`|Named capturing group|

---

## 💡 6. Real-World Examples

### ✅ Check if a string is an email:

```C#
string pattern = @"^[\w.-]+@[\w.-]+\.\w+$";
bool valid = Regex.IsMatch("user@example.com", pattern);
```

---

### ✅ Extract numbers from text:

```C#
string text = "Item ID: 12345, Qty: 67";
MatchCollection matches = Regex.Matches(text, @"\d+");

foreach (Match match in matches)
    Console.WriteLine(match.Value);  // 12345, 67
```

---

### ✅ Replace dates in format `dd/mm/yyyy` with `yyyy-mm-dd`:

```C#
string input = "Date: 06/08/2025";
string pattern = @"(?<d>\d{2})/(?<m>\d{2})/(?<y>\d{4})";
string output = Regex.Replace(input, pattern, "${y}-${m}-${d}");

Console.WriteLine(output);  // Date: 2025-08-06
```

---

### ✅ Split by commas but ignore commas inside quotes:

```C#
string csv = "apple,\"orange,juice\",banana";
string[] parts = Regex.Split(csv, @",(?=(?:[^""]*""[^""]*"")*[^""]*$)");

foreach (var item in parts)
    Console.WriteLine(item);
// apple
// "orange,juice"
// banana
```

---

## 🧠 7. Tips & Gotchas

|Tip|Why|
|---|---|
|Always use `@` before pattern strings|To avoid escaping backslashes like `\\d`|
|Prefer `RegexOptions.Compiled` for performance in loops|Compiles the pattern into IL|
|Use named groups for clarity|Easier to access by name than index|
|Test patterns with regex101.com|Great for visualizing regex behavior|
|Be careful with greedy quantifiers|Use `*?` or `+?` for non-greedy versions|

---

## 🧪 8. Compiling Regex

```C#
Regex regex = new Regex(@"\d+", RegexOptions.Compiled);
```

- Speeds up execution in long-running or repeated code
- Use only if pattern is reused many times