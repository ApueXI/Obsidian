---
Created: 2025-08-07T20:10
tags:
  - OOP
---
## ✅ What Are Generics?

Generics allow you to **define classes, methods, interfaces, and delegates with a placeholder for data types**.

### Why Use Generics?

✔ Type-safe (no casting)

✔ Reusable

✔ Better performance (avoids boxing/unboxing)

✔ Cleaner code

---

## 🧱 Generic Class

```C#
public class Box<T>
{
    public T Value;

    public void SetValue(T val)
    {
        Value = val;
    }

    public T GetValue()
    {
        return Value;
    }
}
```

### Usage

```C#
Box<int> intBox = new Box<int>();
intBox.SetValue(100);

Box<string> strBox = new Box<string>();
strBox.SetValue("Hello");
```

---

## 🔧 Generic Method

```C#
public T GetFirst<T>(T[] array)
{
    return array[0];
}
```

```C#
int first = GetFirst<int>(new int[] { 1, 2, 3 });
```

---

## ⚙️ Generic Interface

```C#
public interface IRepository<T>
{
    void Add(T item);
    T Get(int id);
}
```

---

## 🎛 Constraints on Generics

|Constraint|Meaning|
|---|---|
|`where T : class`|Only reference types|
|`where T : struct`|Only value types|
|`where T : new()`|Must have public parameterless constructor|
|`where T : BaseClass`|Must inherit from BaseClass|
|`where T : Interface`|Must implement Interface|

```C#
public class Factory<T> where T : new()
{
    public T Create()
    {
        return new T(); // must have default constructor
    }
}
```

---

## 📦 Built-in Generic Types

|Generic Type|Description|
|---|---|
|`List<T>`|Resizable array|
|`Dictionary<K,V>`|Key-value store|
|`HashSet<T>`|Unique unordered collection|
|`Queue<T>`|FIFO collection|
|`Stack<T>`|LIFO collection|
|`Nullable<T>`|Nullable value type|
|`Func<T>` / `Action<T>`|Generic delegates|

---

## ✨ Real-World Example

```C#
public class DataStore<T>
{
    private List<T> _items = new List<T>();

    public void Add(T item) => _items.Add(item);

    public T GetByIndex(int index) => _items[index];
}
```

```C#
var store = new DataStore<string>();
store.Add("Apple");
Console.WriteLine(store.GetByIndex(0)); // Apple
```

---

## 🧪 Generic Delegates

```C#
Func<int, int, int> add = (a, b) => a + b;
Action<string> print = msg => Console.WriteLine(msg);
```

---

## 📋 Summary Table

|Feature|Syntax Example|Purpose|
|---|---|---|
|Generic Class|`class Box<T>`|Reusable class|
|Generic Method|`T GetFirst<T>()`|Reusable logic|
|Generic Interface|`interface IRepository<T>`|Abstraction over type|
|Generic Delegate|`Func<T1,T2>` / `Action<T>`|Strongly typed methods|
|Constraint: `class`|`where T : class`|Only reference types|
|Constraint: `struct`|`where T : struct`|Only value types|
|Constraint: `new()`|`where T : new()`|Must have default constructor|

---

## ⚠️ Gotchas

|Issue|Solution|
|---|---|
|Cannot use operators like `+` on `T`|Use constraints or dynamic|
|Can't create `T[]` directly|Use `new T[n]` only inside methods or with tricks|
|Runtime type info may be erased|Use `typeof(T)` for reflection|