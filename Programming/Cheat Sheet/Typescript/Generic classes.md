---
Created: 2025-11-30T15:05
tags:
  - Generics
---
# **Generic Classes in TypeScript**

Generic classes allow you to **create classes that work with multiple types** while maintaining **type safety**.

- Useful for **reusable data structures** or **type-safe containers**.
- Denoted with **angle brackets** `**<T>**` for type parameters.

---

## ✅ **1. Basic Generic Class**

```TypeScript
class Box<T> {
  constructor(public value: T) {}

  getValue(): T {
    return this.value;
  }
}

const numberBox = new Box<number>(123);
const stringBox = new Box<string>("Hello");

console.log(numberBox.getValue()); // 123
console.log(stringBox.getValue()); // Hello

```

- `<T>` is a **type parameter**.
- Ensures **value and methods are type-safe**.

---

## ✅ **2. Multiple Type Parameters**

```TypeScript
class Pair<K, V> {
  constructor(public key: K, public value: V) {}

  display(): void {
    console.log(`${this.key}: ${this.value}`);
  }
}

const pair = new Pair<string, number>("Age", 25);
pair.display(); // Age: 25

```

- Classes can have **multiple generic type parameters**.
- Types are specified at **instantiation**.

---

## ✅ **3. Generic Constraints in Classes**

```TypeScript
interface Lengthwise {
  length: number;
}

class Collection<T extends Lengthwise> {
  constructor(private items: T[]) {}

  longest(): T {
    return this.items.reduce((a, b) => (a.length > b.length ? a : b));
  }
}

const strings = new Collection(["short", "longest", "medium"]);
console.log(strings.longest()); // longest

```

- `T extends Lengthwise` → restricts `T` to types with a `.length` property.
- Ensures **type safety while keeping flexibility**.

---

## ✅ **4. Generic Class With Methods**

```TypeScript
class Stack<T> {
  private items: T[] = [];

  push(item: T): void {
    this.items.push(item);
  }

  pop(): T | undefined {
    return this.items.pop();
  }

  peek(): T | undefined {
    return this.items[this.items.length - 1];
  }
}

const stack = new Stack<number>();
stack.push(10);
stack.push(20);
console.log(stack.pop()); // 20
console.log(stack.peek()); // 10

```

- Generic classes are ideal for **data structures** like **stack, queue, or linked list**.

---

## ✅ **5. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Basic generic class|`class Box<T>`|`new Box<number>(123)`|Type-safe class for any type|
|Multiple type parameters|`class Pair<K,V>`|`new Pair<string,number>("Age",25)`|Types specified at instantiation|
|Generic constraints|`T extends Interface`|`class Collection<T extends Lengthwise>`|Restrict acceptable types|
|Generic methods|`push(item: T): void`|Stack example|Works with internal type-safe operations|
|Type inference|`const x = new Box("Hi")`|TS infers `T = string`|No need to explicitly specify type|

---

**Rule of Thumb**:

- Use **generic classes** to **create reusable, type-safe structures**.
- Use **constraints** to restrict acceptable types when needed.
- Generic classes are particularly useful for **data structures, repositories, or API wrappers**.