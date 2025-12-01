---
Created: 2025-12-01T11:46
tags:
  - Type-Safety-Technique
---
# 🔵 TypeScript — **Branding Types (Type-Safe IDs)**

---

# ✅ 1. Full Explanation

## **What Are Branding Types?**

- Branding (or “opaque”) types are a **TypeScript technique to create nominal types**.
- They let you **differentiate types with the same underlying primitive** (e.g., `string` or `number`) without runtime overhead.
- Useful for **type-safe IDs**, avoiding mix-ups between different IDs like `UserId` vs `OrderId`.

---

## **Why Use Branding Types**

- Prevents accidentally **mixing IDs of different entities**
- Enforces **compile-time safety** without runtime cost
- Useful in large applications where multiple IDs have the **same primitive type**

---

## **How It Works**

- TypeScript is structurally typed, so `string` and `string` are the same.
- Branding adds a **unique phantom type** to differentiate them.

```TypeScript
type UserId = string & { readonly __brand: "UserId" };
type OrderId = string & { readonly __brand: "OrderId" };

```

- The `__brand` property **does not exist at runtime**.
- It ensures **compile-time differentiation**.

---

## **Creating and Using Brand Types**

### 1. **Casting Primitive to Branded Type**

```TypeScript
function createUserId(id: string): UserId {
  return id as UserId;
}

function createOrderId(id: string): OrderId {
  return id as OrderId;
}

const userId: UserId = createUserId("user-123");
const orderId: OrderId = createOrderId("order-456");

```

### 2. **Prevent Mixing IDs**

```TypeScript
function getUserData(userId: UserId) {
  console.log("Fetching data for", userId);
}

getUserData(userId);   // ✅ OK
getUserData(orderId);  // ❌ Error: Type 'OrderId' is not assignable to 'UserId'

```

- This prevents **accidental misuse of IDs** at compile time.

---

### 3. **Generic Branded Type**

```TypeScript
type Brand<T, B> = T & { readonly __brand: B };

type UserId2 = Brand<string, "UserId">;
type OrderId2 = Brand<string, "OrderId">;

const uId: UserId2 = "user-789" as UserId2;
const oId: OrderId2 = "order-789" as OrderId2;

```

- `Brand<T, B>` is reusable for **any primitive type**.

---

## **Gotchas / Pitfalls**

1. **Branding is compile-time only**; runtime value is still the primitive
2. Cannot **directly assign one branded type to another**, even if underlying primitive matches
3. When parsing IDs from external sources (e.g., API JSON), **cast carefully**

---

# ✅ 2. Summary Table

|Concept|Example|Notes|
|---|---|---|
|Branded Type|`type UserId = string & { readonly __brand: "UserId" }`|Adds compile-time phantom type|
|Creating ID|`const uid: UserId = "123" as UserId;`|Cast primitive to branded type|
|Generic Branding|`type Brand<T, B> = T & { readonly __brand: B }`|Reusable for any type|
|Usage Safety|`function getUserData(uid: UserId)`|Cannot pass `OrderId` accidentally|
|Runtime Behavior|Still `string` at runtime|No overhead, purely type-level|

---

# ✅ 3. Real-World Example (Practical)

### **Scenario 1: Type-Safe IDs**

```TypeScript
type UserId = string & { readonly __brand: "UserId" };
type OrderId = string & { readonly __brand: "OrderId" };

function createUserId(id: string): UserId { return id as UserId; }
function createOrderId(id: string): OrderId { return id as OrderId; }

const userId = createUserId("user-101");
const orderId = createOrderId("order-101");

// Safe usage
function getUserOrders(uid: UserId) { console.log(uid); }

getUserOrders(userId);   // ✅ OK
getUserOrders(orderId);  // ❌ Compile-time error

```

### **Scenario 2: Generic Brand Helper**

```TypeScript
type Brand<T, B> = T & { readonly __brand: B };

type ProductId = Brand<string, "ProductId">;
type CategoryId = Brand<string, "CategoryId">;

const pid: ProductId = "prod-202" as ProductId;
const cid: CategoryId = "cat-202" as CategoryId;

function getProduct(id: ProductId) { console.log(id); }

getProduct(pid);  // ✅ OK
getProduct(cid);  // ❌ Error

```

---

# 🔥 Bonus Tips

1. Combine with **opaque types** for better type safety across domains
2. Use **generic** `**Brand<T, B>**` for reusable, consistent patterns
3. Works especially well in **large applications with multiple ID types**
4. No runtime overhead — only affects **compile-time safety**