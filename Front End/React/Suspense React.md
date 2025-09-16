---
Created: 2025-07-12T08:08
---
## What is `Suspense`?

`<Suspense>` is a React component that **waits** for something (like a lazy-loaded component or data) to be ready before rendering it.

> It shows a fallback UI (like a spinner or placeholder) while loading.

  

## Basic Syntax

```JavaScript
import React, { Suspense, lazy } from 'react';

const LazyComponent = lazy(() => import('./MyComponent'));

function App() {
  return (
    <Suspense fallback={<p>Loading...</p>}>
      <LazyComponent />
    </Suspense>
  );
}
```

✅ `lazy()` tells React to load `MyComponent` **only when needed**

✅ `Suspense` shows fallback until loading is done

  

## Use Cases

|Use Case|Description|
|---|---|
|Code splitting|Load components **only when needed**|
|Route-level code loading|Load pages lazily|
|Server components (React 18+)|Combine with `use()` or streaming|
|Data fetching (advanced)|With `React Query`, `Relay`, etc.|

  

## Nested `Suspense`

You can wrap different components with different fallbacks:

```JavaScript
<Suspense fallback={<Spinner />}>
  <MainContent />
  <Suspense fallback={<SmallLoader />}>
    <Sidebar />
  </Suspense>
</Suspense>
```

✅ Useful when you want **different loading indicators** per section

  

## With React Router v6+

```JavaScript
const About = lazy(() => import('./About'));

<Routepath="/about"
  element={
    <Suspense fallback={<div>Loading About...</div>}>
      <About />
    </Suspense>
  }
/>
```

✅ Great for **route-based code splitting**

  

## Common Mistakes

|Mistake|Fix|
|---|---|
|Using `lazy()` without `Suspense`|Always wrap lazy components in `<Suspense>`|
|Putting fallback inside lazy comp|Put fallback **outside**, in `<Suspense>`|
|Fallback not visible|Happens if loading is too fast (use delay)|

  

## Summary Table

|Feature|Description|
|---|---|
|`React.lazy()`|Lazy-load a component with dynamic `import()`|
|`Suspense fallback`|Placeholder to show while loading|
|Supports nesting|Yes, multiple `Suspense` levels allowed|
|Server compatible|✅ With React 18 and server rendering|