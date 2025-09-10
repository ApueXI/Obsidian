---
Created: 2025-08-21T19:29
tags:
  - Math-&-Logic
---
## ✅ **What is the** `**math**` **Module?**

The `**math**` **module** provides **mathematical functions & constants** for floating-point operations.

✔️ Includes:

- Basic math functions (`ceil`, `floor`, `sqrt`, etc.)
- Trigonometry (`sin`, `cos`, `tan`, radians/degrees)
- Exponent & logarithmic functions (`exp`, `log`, `log10`)
- Special functions (`factorial`, `gcd`, `comb`, `perm`)
- Mathematical constants (`pi`, `e`, `tau`, `inf`, `nan`)

---

## 🏗 **Basic Usage**

```Python
import math

print(math.sqrt(16))    # 4.0
print(math.ceil(4.3))   # 5
print(math.floor(4.9))  # 4
print(math.pi)          # 3.141592653589793
```

---

## 🔹 **Key Categories**

### 1️⃣ **Constants**

```Python
math.pi     # 3.141592653589793
math.e      # 2.718281828459045
math.tau    # 6.283185307179586 (2π)
math.inf    # Infinity
math.nan    # Not a number
```

---

### 2️⃣ **Rounding & Absolute**

```Python
math.ceil(3.2)   # 4
math.floor(3.8)  # 3
math.trunc(3.9)  # 3 (just drops decimal)
math.fabs(-5.3)  # 5.3 (float abs)
```

---

### 3️⃣ **Exponential & Logarithms**

```Python
math.exp(2)        # e²
math.pow(2, 3)     # 8.0
math.log(8, 2)     # 3.0 (log base 2)
math.log10(1000)   # 3.0
math.log2(32)      # 5.0
```

---

### 4️⃣ **Roots & Hypotenuse**

```Python
math.sqrt(25)      # 5.0
math.hypot(3, 4)   # 5.0 (Pythagoras)
```

---

### 5️⃣ **Trigonometry**

```Python
math.radians(180)  # π
math.degrees(math.pi) # 180.0

math.sin(math.pi/2)  # 1.0
math.cos(0)          # 1.0
math.tan(math.pi/4)  # 1.0

math.asin(1)         # π/2
math.acos(0)         # π/2
math.atan(1)         # π/4
```

---

### 6️⃣ **Combinatorics & Number Theory**

```Python
math.factorial(5)  # 120
math.gcd(12, 18)   # 6
math.lcm(4, 6)     # 12 (Python 3.9+)
math.comb(5, 2)    # 10 (n choose k)
math.perm(5, 2)    # 20 (n permute k)
```

---

## ⚠️ **Gotchas**

❌ `math.pow()` always returns **float**

✅ Use `**` operator if you want to preserve int when possible

❌ `math` works only with **numbers (no lists)**

✅ For element-wise math → use **NumPy**

❌ Angles are in **radians** by default

✅ Convert degrees ↔ radians with `math.radians()` & `math.degrees()`

---

## 🏎 **math vs cmath vs numpy**

|Feature|math|cmath (complex math)|numpy|
|---|---|---|---|
|Works on|real numbers|complex numbers|arrays|
|Element-wise?|❌ No|❌ No|✅ Yes|
|Speed for arrays|❌ Normal|❌ Normal|✅ Optimized|

---

## 📌 **Summary Table**

|Category|Functions|
|---|---|
|**Constants**|`pi`, `e`, `tau`, `inf`, `nan`|
|**Rounding**|`ceil`, `floor`, `trunc`, `fabs`|
|**Exponents**|`exp`, `pow`, `log`, `log2`, `log10`|
|**Roots**|`sqrt`, `hypot`|
|**Trig**|`sin`, `cos`, `tan`, `asin`, `acos`, `atan`, `radians`, `degrees`|
|**Combinatorics**|`factorial`, `gcd`, `lcm`, `comb`, `perm`|

---

## 🌍 **Real-World Example: Projectile Motion Calculator**

```Python
import math

def projectile_range(speed, angle_deg, gravity=9.81):
    # Convert angle to radians
    angle_rad = math.radians(angle_deg)
    # Formula: (v² * sin(2θ)) / g
    return (speed ** 2 * math.sin(2 * angle_rad)) / gravity

# Example: speed=50 m/s, angle=45°
print(f"Range: {projectile_range(50, 45):.2f} m")
```

👉 **Why** `**math**`**?**

- `sin()` & `radians()` simplify trigonometric calculations
- Clean & reliable for physics/engineering computations

---

✅ **TL;DR:**

- `math` is for **basic real-number math**
- Angles → **radians**
- For **arrays or advanced math**, use **NumPy**