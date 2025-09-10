---
Created: 2025-08-07T20:10
tags:
  - Math-Class
---
# 🧠 C# Bitwise Operations Cheat Sheet

Bitwise operations allow you to manipulate individual bits of integers (`int`, `uint`, `long`, `byte`, etc.).

```C#
int a = 5;      // 0101
int b = 3;      // 0011
```

---

## ⚙️ Bitwise Operators

|Operator|Name|Description|Example (a = 5, b = 3)|Result|
|---|---|---|---|---|
|`&`|AND|1 if **both** bits are 1|`a & b`|1 (0001)|
|`\|`|OR|1 if **at least one** bit is 1|`a \| b`|7 (0111)|
|`^`|XOR|1 if bits are **different**|`a ^ b`|6 (0110)|
|`~`|NOT (one's complement)|Inverts all bits (unary)|`~a`|-6|
|`<<`|Left shift|Shifts bits left; adds 0s on the right|`a << 1`|10 (1010)|
|`>>`|Right shift|Shifts bits right; removes rightmost bits|`a >> 1`|2 (0010)|

### Notes:

- `a = 5` → binary: `0101`
- `b = 3` → binary: `0011`
- `~a = -6` because of how two's complement works in binary.

---

## 🔢 Bitwise Truth Tables

### AND `&`

|A|B|A & B|
|---|---|---|
|0|0|0|
|0|1|0|
|1|0|0|
|1|1|1|

### OR `|`

|A|B|A \| B|
|---|---|---|
|0|0|0|
|0|1|1|
|1|0|1|
|1|1|1|

### XOR `^`

|A|B|A ^ B|
|---|---|---|
|0|0|0|
|0|1|1|
|1|0|1|
|1|1|0|

---

## 🧰 Practical Uses

|Task|Code Example|Use Case|
|---|---|---|
|Check if bit is set|`(value & (1 << bit)) != 0`|Flags, status bits|
|Set a bit|`value|= (1 << bit)`|
|Clear a bit|`value &= ~(1 << bit)`|Disable a flag|
|Toggle a bit|`value ^= (1 << bit)`|Flip a flag|
|Masking (clear others)|`value & mask`|Isolate bits|
|Packing values|`value = (x << 4)|y`|
|Swapping variables (XOR)|`a ^= b; b ^= a; a ^= b;`|Swap without temp variable|

---

## 🧪 Real-World Example: Feature Flags

```C#
[Flags]
enum Permissions
{
    None = 0,
    Read = 1,      // 0001
    Write = 2,     // 0010
    Execute = 4    // 0100
}

Permissions userPerms = Permissions.Read | Permissions.Write;

bool canWrite = (userPerms & Permissions.Write) != 0; // true
```

---

## 📋 Summary Table

|Operation|Symbol|Example|Result (Binary)|
|---|---|---|---|
|AND|`&`|`5 & 3`|`1` (0001)|
|OR|`\|`|`5 \| 3`|`5 \| 3`|
|XOR|`^`|`5 ^ 3`|`6` (0110)|
|NOT|`~`|`~5`|`-6`|
|Left Shift|`<<`|`5 << 1`|`10` (1010)|
|Right Shift|`>>`|`5 >> 1`|`2` (0010)|