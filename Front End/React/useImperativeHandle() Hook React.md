---
Created: 2025-07-10T08:44
tags:
  - Hooks
---
### What is `useImperativeHandle()`?

`useImperativeHandle()` lets you **customize the instance value** that is exposed when a **ref** is attached to a child component using `forwardRef()`.

> Use it when a parent needs to call functions or access properties inside a child.

  

## Basic Setup with `forwardRef`

```JavaScript
import { forwardRef, useImperativeHandle, useRef } from 'react';
```

✅ Must be used inside a component wrapped with `forwardRef`.

  

## Full Example

### 🔸 Child Component (`CustomInput.jsx`)

```JavaScript
import { useImperativeHandle, forwardRef, useRef } from 'react';

const CustomInput = forwardRef((props, ref) => {
  const inputRef = useRef();

  useImperativeHandle(ref, () => ({
    focus: () => {
      inputRef.current.focus();
    },
    clear: () => {
      inputRef.current.value = '';
    }
  }));

  return <input ref={inputRef} />;
});

export default CustomInput;
```

### 🔸 Parent Component

```JavaScript
import { useRef } from 'react';
import CustomInput from './CustomInput';

function App() {
  const inputRef = useRef();

  return (
    <><CustomInput ref={inputRef} />
      <button onClick={() => inputRef.current.focus()}>Focus</button>
      <button onClick={() => inputRef.current.clear()}>Clear</button>
    </>
  );
}
```

✅ Now the parent can call `focus()` and `clear()` methods on the child.

  

## Why Use It?

- To **expose specific functions** (e.g., `focus`, `reset`, `scrollTo`) from child to parent
- To **hide internal details** from the parent (encapsulation)

  

## When Not to Use

❌ Don’t use it to share state — use props or context instead

❌ Avoid exposing too many internals — it breaks component abstraction

  

## Summary Table

|Term|Description|
|---|---|
|`forwardRef()`|Wraps the child to accept a ref from the parent|
|`useImperativeHandle()`|Customizes the values/functions exposed|
|`ref.current`|Holds the exposed instance on the parent side|

  

### Typical Use Cases

✅ Triggering animations

✅ Manually controlling input fields

✅ Calling focus, clear, scroll, reset, etc.

  

### Bonus Tip

You can combine `useImperativeHandle()` with `**useRef**` **+** `**useLayoutEffect**` for layout-based actions like animations or scroll.