---
Created: 2025-09-16T20:19
tags:
  - Advance-Concepts
---
# 🎯 Dart Type Bounds Cheat Sheet

## 1. Full Explanation

- **Type bounds** restrict what types can be used for a generic parameter.
- Syntax: `<T extends SomeClass>` → T must be **SomeClass or a subclass**.
- Ensures **type safety** while still being generic.
- Useful for **methods or classes that require specific functionality**.

---

## 2. Basic Example

```Dart
class Animal {
  void speak() => print("Animal speaks");
}

class Dog extends Animal {
  @override
  void speak() => print("Dog barks");
}

class Cage<T extends Animal> {
  T occupant;
  Cage(this.occupant);

  void makeNoise() => occupant.speak();
}

void main() {
  var dogCage = Cage(Dog());
  dogCage.makeNoise(); // Dog barks

  // var stringCage = Cage("Not an animal"); // ❌ Compile-time error
}

```

✅ `Cage` only accepts types that **extend Animal**, preventing invalid types.

---

## 3. Multiple Type Bounds (Dart 2.13+ with `with`)

```Dart
mixin Swimmer {
  void swim() => print("Swimming");
}

class Fish extends Animal with Swimmer {}

class Aquarium<T extends Animal> {
  T creature;
  Aquarium(this.creature);

  void action() {
    creature.speak();
    if (creature is Swimmer) (creature as Swimmer).swim();
  }
}

void main() {
  var goldfish = Aquarium(Fish());
  goldfish.action();
  // Output:
  // Animal speaks
  // Swimming
}

```

✅ Type bounds combined with **mixins/interfaces** restrict T while enabling extra functionality.

---

## 4. Generic Method with Type Bound

```Dart
T getFirstAnimal<T extends Animal>(List<T> animals) {
  return animals[0];
}

void main() {
  var dogList = [Dog(), Dog()];
  var firstDog = getFirstAnimal(dogList);
  firstDog.speak(); // Dog barks
}

```

✅ Ensures the generic method **only works with subclasses of Animal**.

---

## 5. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Type bound|`<T extends Class>`|T must be Class or subclass|
|Multiple bounds|`<T extends ClassA & ClassB>`|Dart uses `with` for mixins|
|Generic class|`class Cage<T extends Animal>`|Restricts allowed types|
|Generic method|`T getFirst<T extends Animal>(List<T> list)`|Restricts method parameter type|

---

## 6. Real-World Example

💡 **Repository Only for Models**

```Dart
class Model {
  int id = 0;
}

class User extends Model {
  String name;
  User(this.name);
}

class Repository<T extends Model> {
  List<T> items = [];
  void add(T item) => items.add(item);
  T get(int index) => items[index];
}

void main() {
  var userRepo = Repository<User>();
  userRepo.add(User("Alice"));
  print(userRepo.get(0).name); // Alice

  // var stringRepo = Repository<String>(); // ❌ Compile-time error
}

```

✅ Type bounds ensure **repositories only store model objects**, preventing runtime errors.