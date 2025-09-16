---
Created: 2025-07-10T20:15
---
## Updating Arrays in React State

  

> [!important] always use return in something like map, filder, etc

  

### 🧠 Why?

React requires **immutable state updates** — never modify the array directly (e.g., `push()`, `splice()`, etc.)

Instead, create a **new array** with the update and pass it to `setState`.

  

## Add Item to Array

```JavaScript
const [items, setItems] = useState([]);

// Add new item
setItems(prev => [...prev, newItem]);
```

✅ Adds an item at the end

✅ Keeps the original array untouched

  

## Remove Item (by Index)

```JavaScript
setItems(prev => prev.filter((_, index) => index !== iToRemove));
```

✅ Returns a new array **excluding** the unwanted item

  

## Remove Item (by ID)

```JavaScript
setItems(prev => prev.filter(item => item.id !== idToRemove));
```

✅ Assumes items look like `{ id, name }`

  

## Update Item in Array

```JavaScript
setItems(prev =>
  prev.map(item =>
    item.id === idToUpdate
      ? { ...item, name: 'Updated Name' }
      : item
  )
);
```

✅ Use `map()` to create a new array

✅ Replace only the matching item with a new object

  

## Replace Entire Array

```JavaScript
setItems(newArray); // if newArray is a fresh array
```

  

## Insert at Specific Index

```JavaScript
setItems(prev => [
  ...prev.slice(0, index),
  newItem,
  ...prev.slice(index)
]);
```

✅ Inserts without mutating the original array

  

## Summary Table

|Task|Code Snippet|
|---|---|
|Add item|`setX(prev => [...prev, item])`|
|Remove by index|`setX(prev => prev.filter((_, i) => i !== index))`|
|Remove by ID|`setX(prev => prev.filter(item => item.id !== id))`|
|Update item|`setX(prev => prev.map(item => item.id === id ? updated : item))`|
|Insert at index|`setX(prev => [...prev.slice(0, i), item, ...prev.slice(i)])`|

  

## Never Do This

```JavaScript
items.push(newItem);      // ❌ mutates the array
setItems(items);          // ❌ React won’t detect a change
```

✅ Always return a **new array reference** from `setItems()`

  

```JavaScript
  return (
    <>
      <div>
        <h2>List of Food</h2>
        <ul>
          {foods.map((food, index) => {
            return <li key={food}>{food}</li>;
          })}
        </ul>
      </div>
    </>
  );
}
```

```JavaScript
  return (
    <>
      <div>
        <h2>List of Food</h2>
        <ul>
          {foods.map((food, index) => {
            return (
              <>
                <li key={food}>{food}</li>
              </>
            );
          })}
        </ul>
      </div>
    </>
  );
	}
```

  

```JavaScript
import { element } from "prop-types";
import React, { useState } from "react";

function MyComponent() {
  const [foods, setFoods] = useState(["Apple", "Orange", "Banana"]);

  function addFood() {
    const newFood = document.getElementById("foodInput").value;
    document.getElementById("foodInput").value = "";

    setFoods((prevFoods) => [...prevFoods, newFood]);
  }

  function removeFood(index) {
    setFoods(
      // Use an underscore to tell other peeps that the vvraible will not be used
      foods.filter((_, i) => {
        return i !== index;
      })
    );
  }

  return (
    <>
      <div>
        <h2>List of Food</h2>
        <ul>
          {foods.map((food, index) => {
            return (
              <li key={index} onClick={() => removeFood(index)} style={{cursor: "pointer"}}>
                {food}
              </li>
            );
          })}
        </ul>
        <input type="text" id="foodInput" placeholder="Enter Food Name" />
        <button onClick={addFood}>Add Food</button>
      </div>
    </>
  );
}

export default MyComponent;
```