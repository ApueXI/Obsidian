---
Created: 2025-06-18T13:19
---
### What is Scope?

**Scope** determines **where** variables are accessible in your code.

  

## **Types of Scope**

  

### **Global Scope**

- Declared **outside** any function or block.
- Accessible **anywhere** in the script.

```JavaScript
let globalVar = "I'm global";

function showVar() {
  console.log(globalVar); // ✅ Accessible
}

showVar();
```

  

### **Function Scope**

- Declared **inside a function**.
- **Only accessible within** that function.

```JavaScript
function test() {
  let localVar = "I'm local";
  console.log(localVar); // ✅ OK
}

test();
console.log(localVar); // ❌ Error: not defined
```

  

### **Block Scope (**`**let**` **&** `**const**`**)**

- Declared inside `**{}**` like `if`, `for`, etc.
- Only accessible **inside that block**.

```JavaScript
if (true) {
  let blockVar = "Inside block";
  console.log(blockVar); // ✅ OK
}

console.log(blockVar); // ❌ Error: not defined
```

  

## **Loop Scope Example**

```JavaScript
for (let i = 0; i < 3; i++) {
  console.log(i); // ✅ OK
}
console.log(i); // ❌ Error with let (but works with var)
```

  

## `var` vs `let` vs `const` Scope

|   |   |   |
|---|---|---|
|Feature|`var`|`let` / `const`|
|Scope type|Function scoped|Block scoped|
|Redeclarable|✅ Yes|❌ No (in same scope)|
|Hoisted|✅ Yes (but undefined)|✅ Yes (in temporal dead zone)|
|Preferred|❌ No (legacy)|✅ Yes (modern JS)|

  

### **Example: Scope Differences**

```JavaScript
function example() {
  if (true) {
    var a = 10;
    let b = 20;
    const c = 30;
  }
  console.log(a); // ✅ OK (function scoped)
  console.log(b); // ❌ Error
  console.log(c); // ❌ Error
}
example();
```

  

### **Best Practices**

- Use `let` or `const` (not `var`)
- Prefer `const` unless reassignment is needed
- Limit variable scope to where it’s needed (for clean code)

  

```JavaScript
let x = 3;

function func1() {
  let x = 2;
  console.log(x);
}
function func2() {
  let x = 5;
  console.log(x);
}
function func3() {
  console.log(x);
}

func1();
func2();
func3();
```