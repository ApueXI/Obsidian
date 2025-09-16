---
Created: 2025-07-11T10:07
tags:
  - Hooks
---
### What is `useRef()`?

The `useRef()` hook:

- **Creates a reference object** with a `.current` property
- **Persists** across renders
- Does **not trigger re-renders** when `.current` changes

  

## Basic Syntax

```JavaScript
import { useRef } from 'react';

const myRef = useRef(initialValue);
```

  

## Referencing a DOM Element

```JavaScript
function App() {
  const inputRef = useRef();

  function handleClick() {
    inputRef.current.focus(); // Access the actual DOM element
  }

  return (
    <><input ref={inputRef} />
      <button onClick={handleClick}>Focus Input</button>
    </>
  );
}
```

✅ Use `ref={myRef}` to connect the ref to a DOM element

✅ Use `myRef.current` to access it

  

## Persisting Mutable Values Without Re-Renders

```JavaScript
function Timer() {
  const count = useRef(0);

  useEffect(() => {
    const id = setInterval(() => {
      count.current++;
      console.log("Count:", count.current);
    }, 1000);

    return () => clearInterval(id);
  }, []);

  return <p>Check console for count</p>;
}
```

✅ `useRef()` is great for:

- Interval IDs
- Scroll positions
- Caching values
- Tracking previous props or state

  

## Tracking Previous State

```JavaScript
function NameTracker({ name }) {
  const prevName = useRef();

  useEffect(() => {
    prevName.current = name;
  }, [name]);

  return <p>Previous name: {prevName.current}</p>;
}
```

✅ `useRef()` keeps its value between renders

  

## Don’t Confuse with `useState`

|Feature|`useRef`|`useState`|
|---|---|---|
|Persists value|✅ Yes|✅ Yes|
|Triggers re-render|❌ No|✅ Yes|
|Use with DOM|✅ Yes|❌ No|

  

## Summary Table

|Use Case|Example|
|---|---|
|DOM access|`inputRef.current.focus()`|
|Persist across renders|`ref.current = ...`|
|Store timers/intervals|`useRef(null)`|
|Previous state tracking|Store `useRef(oldState)` in `useEffect`|