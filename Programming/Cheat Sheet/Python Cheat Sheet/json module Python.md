---
Created: 2025-08-21T19:29
tags:
  - Data-Serialization
---
## ✅ **What is the** `**json**` **Module?**

The `json` module helps you **encode and decode JSON data**, which is a lightweight data interchange format commonly used for APIs, config files, and data storage.

✔️ Supports:

- Converting Python objects to JSON strings (serialization)
- Parsing JSON strings into Python objects (deserialization)

---

## 🏗 **Basic Usage**

```Python
python
CopyEdit
import json

# Python dict to JSON string
data = {"name": "Alice", "age": 30}
json_str = json.dumps(data)
print(json_str)  # '{"name": "Alice", "age": 30}'

# JSON string back to Python dict
parsed = json.loads(json_str)
print(parsed["name"])  # Alice

```

---

## 🔹 **Key Functions**

|Function|Description|
|---|---|
|`json.dumps(obj)`|Convert Python object to JSON string|
|`json.dump(obj, file)`|Write JSON string directly to a file|
|`json.loads(str)`|Parse JSON string into Python object|
|`json.load(file)`|Parse JSON content from a file into Python object|

---

## ✅ **Advanced Options**

### `json.dumps()` options

- `indent` → pretty print JSON
- `separators` → control comma and colon spacing
- `sort_keys` → sort keys alphabetically

```Python
python
CopyEdit
pretty = json.dumps(data, indent=4, sort_keys=True)
print(pretty)

```

### Custom encoding/decoding

- Use `default` parameter to serialize custom objects
- Use `object_hook` parameter to deserialize into custom objects

---

## ⚠️ **Gotchas**

❌ JSON supports only **basic types** (dict, list, str, int, float, bool, None)

✅ Custom objects must be converted manually (e.g., via `default` function)

❌ JSON keys **must be strings**

---

## 🏎 **json vs pickle vs yaml**

|Feature|json|pickle|yaml|
|---|---|---|---|
|Human-readable|✅ Yes|❌ No|✅ Yes|
|Cross-language|✅ Yes|❌ No|✅ Yes|
|Supports custom types|❌ Limited (need extra work)|✅ Yes|✅ Yes|
|Security|Safer (text-based)|Unsafe (code execution)|Safer|

---

## 📌 **Summary Table**

|Function|Usage|
|---|---|
|`json.dumps()`|Python → JSON string|
|`json.dump()`|Python → JSON file|
|`json.loads()`|JSON string → Python|
|`json.load()`|JSON file → Python|

---

## 🌍 **Real-World Example: Config File Read/Write**

```Python
python
CopyEdit
import json

config = {
    "username": "user123",
    "theme": "dark",
    "volume": 75
}

# Write config to file
with open("config.json", "w") as f:
    json.dump(config, f, indent=4)

# Read config from file
with open("config.json", "r") as f:
    loaded_config = json.load(f)

print(loaded_config["theme"])  # dark

```

👉 **Why** `**json**`**?**

- Easy interchange of config/settings
- Human-readable & editable
- Compatible with many languages & tools

---

✅ **TL;DR:**

- `json` handles **serialization/deserialization** of JSON data
- Use `dump`/`load` for files, `dumps`/`loads` for strings
- Supports basic Python types only