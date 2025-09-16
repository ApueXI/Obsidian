---
Created: 2025-07-12T13:32
---
## What is a Named Export?

A **named export** lets you export **multiple values** (like components or functions) from a single file, **by name**.

```JavaScript
export const Header = () => <h1>Header</h1>;
export const Footer = () => <footer>Footer</footer>;
```

You must then **import them by the same name**:

```JavaScript
import { Header, Footer } from './Layout';
```

  

## Named Export Syntax

### Component Declaration

```JavaScript
export function Header() {
  return <h1>Header</h1>;
}
```

### Arrow Function

```JavaScript
export const Footer = () => <footer>Footer</footer>;
```

✅ Multiple exports per file

❌ Must import with **exact names** (unless aliased)

  

## Importing Named Exports

```JavaScript
import { Header, Footer } from './Layout';
```

✅ Must match exported names exactly

  

### Rename on Import (Alias)

```JavaScript
import { Header as PageHeader } from './Layout';
```

✅ Useful to avoid naming conflicts

  

## Export All at Once (List Syntax)

```JavaScript
const Header = () => <h1>Header</h1>;
const Footer = () => <footer>Footer</footer>;

export { Header, Footer };
```

✅ Clean if all exports are declared first

  

## Common Mistakes

|Mistake|Fix|
|---|---|
|Forgetting `{}` when importing|❌ `import Header` → ✅ `import { Header }`|
|Importing a non-exported name|Must match exported identifiers|
|Mixing default + named without clarity|Know what you're importing|

  

## Default vs Named Export Comparison

|Feature|Named Export|Default Export|
|---|---|---|
|How many per file?|✅ Many|❌ Only one|
|Import syntax|`import { X }`|`import X`|
|Rename allowed?|✅ `as NewName`|✅ Rename freely|
|Tree-shaking friendly|✅ Yes|⚠️ Less optimal sometimes|

  

## When to Use Which?

|Use Default Export When...|Use Named Export When...|
|---|---|
|File exports a **single component**|File exports **multiple components or utils**|
|You want flexible import names|You want strict, consistent naming|

## Bonus: Combine Both

```JavaScript
export const Helper = () => {};
export default function MainComponent() {
  return <div>Main</div>;
}
```

```JavaScript
import MainComponent, { Helper } from './file';
```