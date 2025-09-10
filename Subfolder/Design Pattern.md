## Design Patterns

## 🧠 1. Categories of Design Patterns

Design patterns in software engineering are generally grouped into three categories:

|Category|Purpose|
|---|---|
|Creational|Object creation mechanisms|
|Structural|Class/object composition|
|Behavioral|Communication between objects|

---

## 🧩 2. Common Patterns in Each Category

### ✅ **Creational Patterns**

|Pattern|Purpose|
|---|---|
|**Singleton**|One instance only (e.g., config manager)|
|**Factory Method**|Let subclasses decide what object to create|
|**Abstract Factory**|Create families of related objects|
|**Builder**|Step-by-step construction of complex objects|
|**Prototype**|Clone existing objects|

### 🏗️ **Structural Patterns**

|Pattern|Purpose|
|---|---|
|**Adapter**|Bridge incompatible interfaces|
|**Bridge**|Separate abstraction from implementation|
|**Composite**|Treat group of objects like a single one|
|**Decorator**|Add responsibilities at runtime|
|**Facade**|Simplify interface to a subsystem|
|**Flyweight**|Reduce memory via shared objects|
|**Proxy**|Control access to objects (e.g., lazy load, security)|

### 🔁 **Behavioral Patterns**

|Pattern|Purpose|
|---|---|
|**Chain of Responsibility**|Pass request along a chain|
|**Command**|Encapsulate requests as objects|
|**Interpreter**|Define grammar and interpret sentences|
|**Iterator**|Traverse a container|
|**Mediator**|Reduce chaos by centralizing communication|
|**Memento**|Capture and restore object state|
|**Observer**|Notify dependents on change|
|**State**|Change behavior based on state|
|**Strategy**|Swap algorithms at runtime|
|**Template Method**|Define skeleton of algorithm|
|**Visitor**|Add operations without changing objects|

  

## 🧾 3. Summary Table (Quick Reference)

|Category|Patterns|
|---|---|
|Creational|Singleton, Factory, Abstract Factory, Builder, Prototype|
|Structural|Adapter, Bridge, Composite, Decorator, Facade, Flyweight, Proxy|
|Behavioral|Chain of Responsibility, Command, Interpreter, Iterator, Mediator, Memento, Observer, State, Strategy, Template Method, Visitor|

---

## 🌍 4. Real-World Example (E-Commerce Site)

**Scenario:** You’re building an online store.

- Use **Factory** to create different types of `PaymentProcessor` (PayPal, Stripe).
- Use **Singleton** for a `ShoppingCartManager`.
- Use **Decorator** to add "gift wrap" or "express shipping" options dynamically.
- Use **Observer** to notify users of order status updates.
- Use **Strategy** for different discount algorithms.
- Use **Facade** to provide a simple interface to complex shipping APIs.

---

## ⚠️ 5. Gotchas & Tips

|Tip or Caution|Explanation|
|---|---|
|Don’t overuse patterns|Only use them when they solve real problems|
|Understand before you apply|Learn the intent, not just the structure|
|Combine patterns smartly|E.g., Builder + Factory is common|
|Favor composition over inheritance|Many patterns aim to follow this principle|
|Know your language’s features|Some patterns are less useful in dynamic or functional languages|
