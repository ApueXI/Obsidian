---
Created: 2025-07-11T20:37
tags:
  - Hooks
---
> [!important] useState() = Re-renders the component when the state value changes.
> 
>   
> useRef() = "use Reference" Does not cause re-renders when its value changes. When you want a component to "remember" some information, but you don't want that information to trigger new renders.
> 
> 1. Accessing/Interacting with DOM elements
> 2. Handling Focus, Animations, and Transitions
> 3. Managing Timers and Intervals

  

```JavaScript
import React, { useEffect, useRef } from "react";

function MyComponent(params) {
  const inpputRef1 = useRef(null);
  const inpputRef2 = useRef(null);
  const inpputRef3 = useRef(null);

  useEffect(() => {
    console.log(`COMPONENT RENDERED`);
  });

  function handleClick1() {
    inpputRef1.current.focus();
    inpputRef1.current.style.backgroundColor = "yellow";
    inpputRef2.current.style.backgroundColor = "";
    inpputRef3.current.style.backgroundColor = "";
  }

  function handleClick2() {
    inpputRef2.current.focus();
    inpputRef1.current.style.backgroundColor = "";
    inpputRef2.current.style.backgroundColor = "yellow";
    inpputRef3.current.style.backgroundColor = "";
  }
  function handleClick3() {
    inpputRef3.current.focus();
    inpputRef1.current.style.backgroundColor = "";
    inpputRef2.current.style.backgroundColor = "";
    inpputRef3.current.style.backgroundColor = "yellow";
  }

  return (
    <div>
      <button onClick={handleClick1}>Click Me</button>
      <input ref={inpputRef1} />
      <br />
      <br />

      <button onClick={handleClick2}>Click Me</button>
      <input ref={inpputRef2} />
      <br />
      <br />

      <button onClick={handleClick3}>Click Me</button>
      <input ref={inpputRef3} />
      <br />
      <br />
    </div>
  );
}

export default MyComponent;
```