---
Created: 2025-08-21T19:29
tags:
  - Data-Serialization
---
## ✅ **What is the** `**pickle**` **Module?**

`pickle` is a Python module used for **serializing and deserializing Python objects** — converting objects to a byte stream and back.

- Supports almost **any Python object** (functions, classes, instances, etc.)
- Commonly used for saving program state, caching, or IPC (inter-process communication).

---

## 🏗 **Basic Usage**

```Python
python
CopyEdit
import pickle

# Python object
data = {"name": "Alice", "age": 30}

# Serialize to bytes
pickled_data = pickle.dumps(data)

# Deserialize back to Python object
original_data = pickle.loads(pickled_data)
print(original_data["name"])  # Alice

```

---

## 🔹 **Working with Files**

```Python
python
CopyEdit
# Write to file
with open("data.pkl", "wb") as f:
    pickle.dump(data, f)

# Read from file
with open("data.pkl", "rb") as f:
    loaded_data = pickle.load(f)

print(loaded_data)

```

---

## ✅ **Key Functions**

|Function|Description|
|---|---|
|`pickle.dumps(obj)`|Serialize object to bytes|
|`pickle.loads(bytes_obj)`|Deserialize bytes to object|
|`pickle.dump(obj, file)`|Serialize and write to file|
|`pickle.load(file)`|Read from file and deserialize|

---

## ⚠️ **Security Warning**

- **Never unpickle data from untrusted sources!**
- Pickle can execute arbitrary code during loading, which is a **major security risk**.

---

## 🏎 **pickle vs json**

|Feature|pickle|json|
|---|---|---|
|Supports all Python objects?|✅ Yes|❌ No (basic types only)|
|Human-readable?|❌ No|✅ Yes|
|Cross-language?|❌ No|✅ Yes|
|Security|Unsafe (code exec)|Safer (text)|

---

## 📌 **Summary Table**

|Function|Usage|
|---|---|
|`pickle.dumps()`|Serialize to bytes|
|`pickle.loads()`|Deserialize from bytes|
|`pickle.dump()`|Serialize to file|
|`pickle.load()`|Deserialize from file|

---

## 🌍 **Real-World Example: Saving & Loading ML Model**

```Python
python
CopyEdit
import pickle
from sklearn.linear_model import LogisticRegression

# Train a simple model
model = LogisticRegression()
# ... model training code here ...

# Save model to disk
with open("model.pkl", "wb") as f:
    pickle.dump(model, f)

# Later, load the model
with open("model.pkl", "rb") as f:
    loaded_model = pickle.load(f)

# Use loaded model to predict
# predictions = loaded_model.predict(X_test)

```

👉 **Why** `**pickle**`**?**

- Save complex Python objects (like models) easily
- No need to manually convert to JSON or other formats

---

✅ **TL;DR:**

- `pickle` serializes **any Python object** to bytes
- Use for caching, saving state, or model persistence
- **Avoid loading pickle data from untrusted sources** due to security risks