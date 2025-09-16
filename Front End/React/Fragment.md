---
Created: 2025-07-11T09:03
---
## What is a Fragment?

React **Fragments** let you **group multiple elements** without introducing an extra `<div>` or wrapper into the DOM.

```JavaScript
return (
  <React.Fragment>
    <h1>Hello</h1>
    <p>World</p>
  </React.Fragment>
);
```

✅ No unnecessary DOM nodes

✅ Cleaner output

✅ Better styling and layout control

  

## Short Syntax

```JavaScript
return (
  <><h1>Hello</h1>
    <p>World</p>
  </>
);
```

✅ This is exactly the same as `<React.Fragment>`

❗ But you **can’t add props** to the short syntax

  

## Why Use Fragments?

|Use Case|Why Fragments Help|
|---|---|
|Return multiple elements|Without needing a parent `<div>`|
|Cleaner HTML|Avoids layout bugs from extra wrappers|
|Inside Lists/Maps|Wrap each item in a Fragment|
|Group elements in a component|No side effects on layout/CSS|

  

## Example in a List

```JavaScript
const users = [
  { id: 1, name: 'Nein' },
  { id: 2, name: 'Nika' }
];

return (
  <ul>
    {users.map(user => (
      <React.Fragment key={user.id}>
        <li>{user.name}</li>
        <li>---</li>
      </React.Fragment>
    ))}
  </ul>
);
```

✅ No `<div>` wrappers

✅ `key` can be applied to each `Fragment` (only in long form)

  

## Fragment vs `<div>`

|Feature|`<div>`|`<React.Fragment>`|
|---|---|---|
|Adds DOM element|✅ Yes|❌ No|
|Affects layout/styling|✅ Sometimes|❌ Never|
|Needed for rendering|✅ Yes (in old React)|✅ Now cleaner with Fragments|

  

## Summary Table

|Syntax|Description|
|---|---|
|`<React.Fragment>...</React.Fragment>`|Full version (can take props like `key`)|
|`<>...</>`|Short version (cleaner, no props)|
|`key` on fragment?|✅ Only in full version|