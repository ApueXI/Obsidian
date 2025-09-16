---
Created: 2025-07-11T10:10
tags:
  - Hooks
---
> [!important]
> 
> ```JavaScript
> useEffect() = React Hook that tells React DO SOME CODE WHEN (pick one):
>               This component re-renders
>               This component mounts
>               The state of a value
> 
> useEffect(function, [dependencies])
> 
> 1. useEffect(() => {})                   Runs after every re-render
> 2. useEffect(() => {}, [])               Runs only on mount
> 3. useEffect(() => {}, [value])          Runs on mount + when value changes
> 
> USES
> #1 Event Listeners
> #2 DOM manipulation
> #3 Subscriptions (real-time updates)
> #4 Fetching Data from an API
> #5 Clean up when a component unmounts
> ```

```JavaScript
import React, { useState, useEffect } from "react";

function MyComponent() {
  const [count, setCOunt] = useState(0);
  const [color, setColor] = useState("green");

  //   add an
  useEffect(() => {
    document.title = `Count ${count} ${color}`;
  }, [count]);

  function countAdd() {
    setCOunt((prevCount) => prevCount + 1);
  }

  function countSubtract() {
    setCOunt((prevCount) => prevCount - 1);
  }

  function colorChange() {
    setColor((color) => (color === "green" ? "red" : "green"));
  }

  return (
    <>
      <p style={{color: color}}>Count {count}</p>
      <button onClick={countAdd}>Add</button>
      <button onClick={countSubtract}>Subtract</button>
      <button onClick={colorChange}>Change Color</button>
    </>
  );
}

export default MyComponent;
```

  

```JavaScript
import React, { useState, useEffect } from "react";

function MyComponent() {
  const [width, setWidth] = useState(window.innerWidth);
  const [height, setHeight] = useState(window.innerHeight);

  function winResize() {
    setWidth(window.innerWidth);
    setHeight(window.innerHeight);
  }

  useEffect(() => {
    window.addEventListener("resize", winResize);
    console.log(`Reisezed Window`);

    return () => {
      window.removeEventListener("resize", winResize);
      console.log(`Event Listener Removed`);
    };
  }, []);

  useEffect(() => {
    document.title = `Size: ${width} x ${height}`;
  }, [width, height]);

  return (
    <>
      <p>Window Width: {width}px</p>
      <p>Window Height: {height}px</p>
    </>
  );
}

export default MyComponent;
```