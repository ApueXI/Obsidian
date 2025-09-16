---
Created: 2025-07-10T20:54
---
## Updating an Array of Objects in React State

> 🧠 Always return a new array
> 
> ❌ Never mutate original array or object

  

### Example State

```JavaScript
const [todos, setTodos] = useState([
  { id: 1, text: "Learn React", done: false },
  { id: 2, text: "Build App", done: true },
]);
```

  

## Update a Property in One Object

Update `done` to `true` for item with `id === 1`:

```JavaScript
setTodos(prev =>
  prev.map(todo =>
    todo.id === 1
      ? { ...todo, done: true }  // 🔁 new object
      : todo
  )
);
```

✅ Creates a **new array**

✅ Only updates the matching object

✅ Leaves others unchanged

  

## Add a New Object

```JavaScript
setTodos(prev => [
  ...prev,
  { id: 3, text: "Deploy App", done: false },
]);
```

✅ Use spread to add new object at the end

  

## Remove an Object (by ID)

```JavaScript
setTodos(prev => prev.filter(todo => todo.id !== 2));
```

✅ Filters out the object with `id === 2`

  

## Toggle a Boolean Property

```JavaScript
setTodos(prev =>
  prev.map(todo =>
    todo.id === 1
      ? { ...todo, done: !todo.done }
      : todo
  )
);
```

✅ Toggling a value without mutating original

  

## Replace an Object Entirely

```JavaScript
const updated = { id: 1, text: "Learn React deeply", done: true };

setTodos(prev =>
  prev.map(todo =>
    todo.id === updated.id ? updated : todo
  )
);
```

✅ Replace entire object (not just a field)

  

## Summary Table

|Task|Code Example|
|---|---|
|Update field by ID|`map()`, then `...todo`, update only if ID matches|
|Add object|`[...prev, newObject]`|
|Remove object by ID|`filter(todo => todo.id !== id)`|
|Toggle boolean field|`todo.done: !todo.done` in a mapped update|
|Replace whole object|`map()` and return full new object if IDs match|

  

## Common Mistakes

|Mistake|Why It's Wrong|
|---|---|
|`todos[0].done = true`|❌ Mutates state directly|
|`setTodos(todos)` after mutation|❌ Same reference, no re-render|
|`push()`, `splice()`|❌ Changes original array|

✅ Always use **immutable updates**

  

```JavaScript
import React, { useState } from "react";

function MyComponent() {
  const [cars, setCars] = useState([]);
  const [carYear, setCarYear] = useState(new Date().getFullYear());
  const [carMake, setCarMake] = useState("");
  const [carModel, setCarModel] = useState("");

  function carAdd() {
    const newCar = { year: carYear, make: carMake, model: carModel };
    setCars((prevCars) => [...prevCars, newCar]);

    setCarYear(new Date().getFullYear());
    setCarMake("");
    setCarModel("");
  }

  function carRemove(index) {
    // Use an underscore to tell other peeps that the vvraible will not be used
    setCars((prevCars) => prevCars.filter((_, i) => i !== index));
  }

  function changeYear(params) {
    setCarYear(params.target.value);
  }

  function changeMake(params) {
    setCarMake(params.target.value);
  }

  function changeModel(params) {
    setCarModel(params.target.value);
  }

  return (
    <>
      <div>
        <h2>List of Car Objects</h2>
        <ul>
          {cars.map((car, index) => {
            return (
              <li
                key={index}
                onClick={() => carRemove(index)}
                style={{ cursor: "pointer" }}
              >
                {car.year} {car.make} {car.model}
              </li>
            );
          })}
        </ul>
        <input type="number" value={carYear} onChange={changeYear} />
        <br />
        <input
          type="text"
          value={carMake}
          onChange={changeMake}
          placeholder="Enter Car Make"
        />
        <br />
        <input
          type="text"
          value={carModel}
          onChange={changeModel}
          placeholder="Enter Car Model"
        />
        <br />
        <button onClick={carAdd}>Add Car</button>
      </div>
    </>
  );
}

export default MyComponent;
```