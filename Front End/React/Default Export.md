---
Created: 2025-07-12T13:30
---
## What is a Default Export?

A **default export** allows a module (like a file) to export **a single main value**, usually a React component.

```JavaScript
// MyComponent.jsx
export default function MyComponent() {
  return <h1>Hello!</h1>;
}
```

✅ You can then import it **with any name**:

```JavaScript
import MyComponent from './MyComponent';
```

  

## Default Export Syntax

### Function Component

```JavaScript
export default function MyComponent() {
  return <div>Hi</div>;
}
```

or

```JavaScript
function MyComponent() {
  return <div>Hi</div>;
}
export default MyComponent;
```

  

### Arrow Function Component

```JavaScript
const MyComponent = () => <div>Hi</div>;
export default MyComponent;
```

---

## 📥 2. Importing a Default Export

```JavaScript
import AnyName from './MyComponent';
```

✅ You can name it whatever you want

❗ Works because it's the default export

  

## Compare: Default vs Named Export

|Feature|Default Export|Named Export|
|---|---|---|
|Syntax|`export default MyComponent`|`export const MyComponent = () => {}`|
|Import syntax|`import X from 'file'`|`import { MyComponent } from 'file'`|
|Only one allowed|✅ Yes|❌ You can export many|
|Rename on import|✅ Yes|✅ But must use `as` keyword|

  

## Summary Table

|Task|Default Export Syntax|Import Syntax|
|---|---|---|
|Export component|`export default MyComponent`|`import MyComponent from ...`|
|Rename on import|`import Anything from ...`|✅ Works|
|Only one per file|✅ Yes|❌ Named can be many|

  

## Common Mistakes

|Mistake|Fix|
|---|---|
|Using curly braces for default import|❌ `import { X }` → ✅ `import X`|
|Having two default exports|❌ Only one per file allowed|
|Mixing default and named incorrectly|Know when to use `{}` or not|

  

## Combine with Named Export (Advanced)

```JavaScript
// file.js
export const helper = () => {};
export default MyComponent;
```

```JavaScript
// import both
import MyComponent, { helper } from './file';
```