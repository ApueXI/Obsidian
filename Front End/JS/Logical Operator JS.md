---
Created: 2025-06-18T08:33
---
### `**&&**` **– AND Operator**

Returns `true` only if **both** sides are `true`.

```JavaScript
true && true    // true
true && false   // false

let age = 20;
if (age > 18 && age < 30) {
  console.log("Young adult");
}
```

  

### `**||**` **– OR Operator**

Returns `true` if **at least one** side is `true`.

```JavaScript
false || true   // true
false || false  // false

let isAdmin = false;
let isEditor = true;

if (isAdmin || isEditor) {
  console.log("Access granted");
}
```

  

### `**!**` **– NOT Operator**

Flips the value: `true` → `false`, `false` → `true`

```JavaScript
!true     // false
!false    // true

let isLoggedIn = false;

if (!isLoggedIn) {
  console.log("Please log in");
}
```

  

### Truthy vs Falsy (for `&&` and `||`)

- `&&` returns the **first falsy** value, or the **last** if all are truthy.
- `||` returns the **first truthy** value.

```JavaScript
console.log(0 && "hello");      // 0 (falsy)
console.log("hi" && "bye");     // "bye"

console.log(null || "default"); // "default"
console.log("user" || "guest"); // "user"
```

  

### Real-World Shortcut Use

```JavaScript
let username = userInput || "Guest";  // Default value

isLoggedIn && showDashboard();        // Only run if true
```

  

```JavaScript
const isSunny = false;
let temp = 41;

if (!isSunny || (temp <= 30 && temp >= 12)) {
  console.log(`It is humid outside`);
}
```