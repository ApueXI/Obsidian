---
Created: 2025-08-07T20:10
tags:
  - Advance-Concepts
---
Events are a way for a class to **notify** other classes or objects when something happens. Events are based on **delegates** but add encapsulation to limit who can raise the event.

---

## 🧱 Basic Structure

### 1. Declare a delegate type (optional; often use built-in types)

```C#
public delegate void NotifyEventHandler(string message);
```

### 2. Declare an event based on the delegate

```C#
public event NotifyEventHandler OnNotify;
```

Or use built-in delegate type:

```C#
public event EventHandler OnNotify;
public event EventHandler<MyEventArgs> OnNotifyWithArgs;
```

---

## 🔧 Event Publisher Example

```C#
public class Publisher
{
    // Declare event using EventHandler delegate
    public event EventHandler<string> OnChange;

    public void RaiseEvent(string message)
    {
        OnChange?.Invoke(this, message);  // Raise event safely
    }
}
```

---

## 🔗 Event Subscriber Example

```C#
public class Subscriber
{
    public void Subscribe(Publisher pub)
    {
        pub.OnChange += HandleEvent;
    }

    private void HandleEvent(object sender, string message)
    {
        Console.WriteLine("Event received: " + message);
    }
}
```

---

## 🧩 Raising Events

- Raise using `?.Invoke` to avoid null exceptions
- Pass `sender` (usually `this`) and event arguments

---

## 📋 EventHandler and EventArgs

- `EventHandler` is a delegate with `(object sender, EventArgs e)`
- You can subclass `EventArgs` to send custom data:

```C#
public class MyEventArgs : EventArgs
{
    public int Value { get; }
    public MyEventArgs(int value) => Value = value;
}

public event EventHandler<MyEventArgs> OnValueChanged;
```

Raise with:

```C#
OnValueChanged?.Invoke(this, new MyEventArgs(42));
```

---

## 🔄 Unsubscribe Events

```C#
pub.OnChange -= HandleEvent;
```

---

## 🧰 Real-World Example: Button Click

```C#
class Button
{
    public event EventHandler Clicked;

    public void Click()
    {
        Clicked?.Invoke(this, EventArgs.Empty);
    }
}

class Program
{
    static void Main()
    {
        var button = new Button();
        button.Clicked += (s, e) => Console.WriteLine("Button clicked!");
        button.Click();
    }
}
```

---

## ⚠️ Common Pitfalls

|Problem|Solution|
|---|---|
|Forgetting to unsubscribe|Use `-=` to avoid memory leaks|
|Null event invocation|Use `?.Invoke` syntax safely|
|Event handler exceptions|Catch inside handler or use safe patterns|

---

## 📋 Summary Table

|Task|Syntax/Code Example|
|---|---|
|Declare event|`public event EventHandler OnNotify;`|
|Subscribe|`publisher.OnNotify += HandlerMethod;`|
|Unsubscribe|`publisher.OnNotify -= HandlerMethod;`|
|Raise event|`OnNotify?.Invoke(this, EventArgs.Empty);`|
|Custom EventArgs|Subclass `EventArgs` and pass data|