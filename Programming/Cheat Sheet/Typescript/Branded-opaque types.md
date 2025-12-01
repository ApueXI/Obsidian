---
Created: 2025-12-01T11:53
tags:
  - Extra-Advanced-Topics
---
# 🔵 TypeScript — **Branded / Opaque Types**

---

## 1. **Full Explanation**

### **What Are Branded (Opaque) Types?**

- Branded or opaque types are a **technique to create nominal types in TypeScript**, which normally uses **structural typing**.
- They allow you to **distinguish between types that are structurally identical** but represent **different concepts**.
- Achieved by **adding a unique “brand” property** that is never used at runtime.

---

### **Why Use Branded Types**

1. Prevent **mixing incompatible types** (e.g., `UserId` vs `ProductId`).
2. Maintain **type safety** in large applications.
3. Document **intent of a type** clearly.

---

### **Key Points**

- Uses **intersection types** (`& { __brand: "BrandName" }`).
- The `__brand` property is **never accessed at runtime**.
- The underlying type can be **string, number, etc.**.
- TypeScript enforces **type distinction** despite structural similarity.

---

## 2. **How It Works**

### 1. **Simple Branded Type**

```TypeScript
type UserId = string & { __brand: "UserId" };
type ProductId = string & { __brand: "ProductId" };

// Function that accepts UserId only
function getUser(id: UserId) {
  console.log("Fetching user with ID:", id);
}

const userId = "123" as UserId; // ✅ Cast to brand
const productId = "456" as ProductId;

// getUser(productId); // ❌ Error: ProductId not assignable to UserId
getUser(userId); // ✅ Works

```

---

### 2. **Creating Branded Type Factory**

```TypeScript
function createUserId(id: string): UserId {
  return id as UserId;
}

const myUserId = createUserId("abc123");
getUser(myUserId); // ✅ Works

```

- Ensures **values are only branded via a controlled function**.

---

### 3. **Branded Numbers**

```TypeScript
type Meter = number & { __brand: "Meter" };
type Second = number & { __brand: "Second" };

const distance = 100 as Meter;
const time = 9 as Second;

// function accepting only Meter
function printDistance(d: Meter) { console.log(d); }

printDistance(distance); // ✅ Works
// printDistance(time); // ❌ Error

```

---

### 4. **Real-World Use Case: IDs**

```TypeScript
type UserId = string & { __brand: "UserId" };
type OrderId = string & { __brand: "OrderId" };

function fetchUser(id: UserId) { /* ... */ }
function fetchOrder(id: OrderId) { /* ... */ }

const uid = "u123" as UserId;
const oid = "o456" as OrderId;

fetchUser(uid); // ✅ Works
// fetchUser(oid); // ❌ Error: OrderId not assignable to UserId

```

---

## 3. **Gotchas / Pitfalls**

1. **Brand exists only at compile-time** → no runtime overhead.
2. Must **cast values** to the branded type or use a factory function.
3. Can only **intersect with existing types** (string, number, etc.).
4. Overuse can lead to **complex type definitions**, so use judiciously.

---

## 4. **Summary Table**

|Feature|Syntax|Notes|
|---|---|---|
|Branded type|`type Brand = BaseType & { __brand: "BrandName" }`|Distinguishes nominal types|
|Casting|`value as Brand`|Needed to assign a value to a branded type|
|Factory function|`function create(): Brand { return val as Brand }`|Ensures controlled branding|
|Examples|`UserId`, `ProductId`, `Meter`, `Second`|Prevent accidental mixing|
|Runtime|None|Branding exists **only at compile-time**|

---

## 5. **Real-World Examples**

### **Example 1: User vs Product IDs**

```TypeScript
type UserId = string & { __brand: "UserId" };
type ProductId = string & { __brand: "ProductId" };

function fetchUser(id: UserId) {}
function fetchProduct(id: ProductId) {}

const uid = "u123" as UserId;
const pid = "p456" as ProductId;

fetchUser(uid); // ✅ Works
// fetchUser(pid); // ❌ Error

```

### **Example 2: Distance & Time Units**

```TypeScript
type Meter = number & { __brand: "Meter" };
type Second = number & { __brand: "Second" };

const d = 100 as Meter;
const t = 10 as Second;

function speed(distance: Meter, time: Second) { return distance / time; }
console.log(speed(d, t)); // ✅ Works
// speed(t, d); // ❌ Error

```

### **Example 3: Factory Function for Safer Branding**

```TypeScript
function makeUserId(id: string): UserId {
  return id as UserId;
}

const uid = makeUserId("u789");
fetchUser(uid); // ✅ Works

```

---

## 6. **Key Takeaways**

1. Branded types **enforce nominal typing** in TypeScript.
2. Use for **IDs, units, or any conceptually distinct types**.
3. Safe at compile-time, **no runtime overhead**.
4. Combine with **factory functions** for **type-safe construction**.
5. Improves **code safety, readability, and maintainability**.