---
Created: 2025-11-30T14:54
tags:
  - Classes
---
# **Access Modifiers in TypeScript**

Access modifiers control the **visibility and accessibility of class members** (properties and methods).

TypeScript supports three main modifiers: `**public**`, `**private**`, and `**protected**`.

---

## ✅ **1.** `**public**`

- Default access modifier.
- Class members marked `public` are **accessible anywhere**: inside the class, subclasses, and outside.

```TypeScript
class Person {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }
}

const alice = new Person("Alice");
console.log(alice.name); // ✅ "Alice"

```

- If no modifier is specified, **members are public by default**.

---

## ✅ **2.** `**private**`

- Members are **only accessible inside the class**.
- Cannot be accessed by subclasses or outside the class.

```TypeScript
class BankAccount {
  private balance: number;

  constructor(balance: number) {
    this.balance = balance;
  }

  deposit(amount: number) {
    this.balance += amount;
  }

  getBalance(): number {
    return this.balance;
  }
}

const acc = new BankAccount(1000);
// console.log(acc.balance); ❌ Error: private
console.log(acc.getBalance()); // ✅ 1000

```

- Use `private` to **encapsulate internal state** and protect it from external modification.

---

## ✅ **3.** `**protected**`

- Members are **accessible inside the class and subclasses**, but **not outside**.

```TypeScript
class Animal {
  protected name: string;

  constructor(name: string) {
    this.name = name;
  }
}

class Dog extends Animal {
  bark() {
    console.log(`Woof! I'm ${this.name}`);
  }
}

const dog = new Dog("Rex");
dog.bark();         // ✅ "Woof! I'm Rex"
// console.log(dog.name); ❌ Error: protected

```

- Useful for **inheritance scenarios**, where subclasses need access but external code shouldn’t modify it.

---

## 🔹 **4. Summary Table**

|Modifier|Accessible in Class|Subclass|Outside|Notes|
|---|---|---|---|---|
|`public`|✅ Yes|✅ Yes|✅ Yes|Default if no modifier|
|`private`|✅ Yes|❌ No|❌ No|Encapsulates internal state|
|`protected`|✅ Yes|✅ Yes|❌ No|Allows subclass access, hides from outside|

---

## 🔹 **5. Quick Example Combining Modifiers**

```TypeScript
class Example {
  public a: number;
  private b: number;
  protected c: number;

  constructor(a: number, b: number, c: number) {
    this.a = a;
    this.b = b;
    this.c = c;
  }

  showB() {
    console.log(this.b); // ✅ Access private inside class
  }
}

class SubExample extends Example {
  showC() {
    console.log(this.c); // ✅ Access protected in subclass
  }
}

const obj = new SubExample(1, 2, 3);
console.log(obj.a); // ✅ public
// console.log(obj.b); ❌ private
// console.log(obj.c); ❌ protected

```

---

**Rule of Thumb**:

- `**public**` → default, open access.
- `**private**` → encapsulate data, hide from everyone.
- `**protected**` → hide from outside but allow subclasses.