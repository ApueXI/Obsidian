---
Created: 2025-08-21T19:29
tags:
  - Control-Flow
---
# 🐍 Python `match` / `case` Cheat Sheet (Structural Pattern Matching)

## 🔹 1. Concept

- Introduced in **Python 3.10**.
- `match` / `case` is similar to `switch` statements in other languages but **much more powerful**.
- It’s used for **structural pattern matching** → allows matching not only values but also **patterns, types, and structures**.

---

## 🔹 2. Syntax

```Python
match subject:
    case pattern1:
        # code block
    case pattern2 if condition:
        # code block with guard
    case _:
        # default/fallback case
```

- `subject`: the value you want to match against.
- `pattern`: what you’re checking for (literal, type, sequence, dict, class, etc.).
- `_`: wildcard, matches anything (like `default` in `switch`).
- `if condition`: optional guard for extra filtering.

---

## 🔹 3. Usage Scenarios

- Replacing multiple `if-elif-else` blocks.
- Matching **data structures** (lists, dicts, tuples).
- Handling **different types** of input elegantly.
- Parsing **nested objects**.

---

## 🔹 4. Pattern Types & Examples

|**Pattern Type**|**Example**|**Explanation**|
|---|---|---|
|**Literal Match**|`case 1:`|Matches exact value `1`.|
|**Multiple Options (OR)**|`case 1|2|
|**Wildcard (**`**_**`**)**|`case _:`|Matches anything (default).|
|**Variable Capture**|`case x:`|Captures value into variable `x`.|
|**Guard Condition**|`case x if x > 10:`|Matches if value > 10.|
|**Sequence Matching**|`case [a, b]:`|Matches list with exactly 2 elements.|
|**Rest Elements**|`case [a, *rest]:`|Matches list starting with `a` and captures the rest.|
|**Dict Matching**|`case {"name": n, "age": a}:`|Matches dict with keys `"name"` and `"age"`.|
|**Class Matching**|`case Point(x, y):`|Matches object `Point` and unpacks attributes.|
|**Nested Matching**|`case {"user": {"id": uid, "name": uname}}:`|Matches nested dicts.|

---

## 🔹 5. Real-World Example

### Example: Handling API Responses

```Python
def handle_response(response):
    match response:
        case {"status": 200, "data": data}:
            print("✅ Success:", data)
        case {"status": 404}:
            print("❌ Not Found")
        case {"status": 500, "error": err}:
            print("⚠️ Server Error:", err)
        case _:
            print("Unknown response")

# Example usage
handle_response({"status": 200, "data": {"id": 1, "name": "Alice"}})
handle_response({"status": 404})
handle_response({"status": 500, "error": "DB down"})
```

### Output:

```Plain
✅ Success: {'id': 1, 'name': 'Alice'}
❌ Not Found
⚠️ Server Error: DB down
```

---

## 🔹 6. Gotchas / Things to Remember

- Requires **Python 3.10+**.
- Patterns are **checked top to bottom** (first match wins).
- Avoid capturing variables with `_` unless intentional (use `_` as wildcard).
- Good for **structured data** → not just numbers.