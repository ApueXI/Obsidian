---
Created: 2025-07-11T10:07
tags:
  - Hooks
---
### What is `useLayoutEffect()`?

`useLayoutEffect()` is just like `useEffect()`, but it runs **synchronously after DOM mutations** and **before the browser paints** the screen.

> Use it when you need to measure layout or make immediate visual updates before the user sees anything.

  

## Basic Syntax

```JavaScript
useLayoutEffect(() => {
  // This runs after DOM update but before paint

  return () => {
    // Optional cleanup before the next effect
  };
}, [dependencies]);
```

  

## Timing vs `useEffect()`

|Hook|Timing|
|---|---|
|`useEffect()`|After paint (asynchronous, non-blocking)|
|`useLayoutEffect()`|Before paint (synchronous, blocks paint)|

✅ `useLayoutEffect()` runs **immediately after DOM updates**, before the browser draws the screen

⚠️ Can block UI rendering — **use only when necessary**

  

## When to Use `useLayoutEffect()`

Use `useLayoutEffect()` for:

- Measuring layout (`getBoundingClientRect`)
- Fixing scroll positions
- Avoiding flickering on layout updates
- Synchronizing animations or CSS transitions

  

### Example: Measure DOM Element

```JavaScript
function Box() {
  const boxRef = useRef();

  useLayoutEffect(() => {
    const { height } = boxRef.current.getBoundingClientRect();
    console.log("Box height before paint:", height);
  }, []);

  return <div ref={boxRef}>Measure me</div>;
}
```

✅ Ensures you measure layout **before paint**

  

## Don’t Overuse

Overusing `useLayoutEffect()` can:

- Block browser paint
- Cause janky UI
- Hurt performance

🧠 Prefer `useEffect()` unless you have a **layout-critical reason**

  

## Combined with `useRef()`

`useLayoutEffect()` is usually paired with `useRef()` for DOM measurements or direct manipulation.

  

## Summary Table

|Feature|`useEffect`|`useLayoutEffect`|
|---|---|---|
|Runs|After paint (async)|Before paint (sync)|
|Blocks rendering?|❌ No|✅ Yes|
|Use for|Data fetching, side effects|Layout measuring, DOM edits|

  

## When to Use

✅ Yes:

- Read layout before it’s shown
- Prevent flickering
- Scroll/animation sync

❌ Avoid:

- Heavy logic
- API calls or non-visual effects