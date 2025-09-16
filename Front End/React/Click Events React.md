---
Created: 2025-07-09T19:59
---
### What Are Click Events?

React uses a **synthetic event system** to handle DOM events like `onClick`, which is consistent across browsers and performs well.

  

### Basic Click Event

```JavaScript
function MyButton() {
  function handleClick() {
    alert('Button was clicked!');
  }

  return <button onClick={handleClick}>Click me</button>;
}
```

- ✅ `onClick` is the event handler
- ✅ Event name is camelCase in React (`onClick`, not `onclick`)

  

### Click Event with Inline Function

```JavaScript
<button onClick={() => console.log('Clicked!')}>Click</button>
```

- ⚠️ Use inline functions cautiously—can hurt performance if overused

  

### Accessing the Event Object

```JavaScript
function MyComponent() {
  const handleClick = (event) => {
    console.log(event); // SyntheticEvent
  };

  return <button onClick={handleClick}>Click</button>;
}
```

- 🧠 React uses **SyntheticEvent** for cross-browser compatibility

  

### Passing Arguments to Click Handlers

```JavaScript
function MyButton({ message }) {
  const handleClick = (msg) => {
    alert(msg);
  };

  return <button onClick={() => handleClick(message)}>Click</button>;
}
```

  

### Click Handler with Parameters

```JavaScript
function handleGreet(name) {
  alert(`Hello, ${name}`);
}

<button onClick={() => handleGreet("Nein")}>Greet</button>
```

✅ Use arrow function to pass arguments

  

### Accessing the Event Object

```JavaScript
function handleClick(event) {
  console.log("Target:", event.target);
}

<button onClick={handleClick}>Inspect</button>
```

> React wraps native events in a SyntheticEvent

  

### Prevent Default Behavior

```JavaScript
function LinkButton() {
  function handleClick(e) {
    e.preventDefault();
    console.log('Link clicked but not followed');
  }

  return (
    <a href="https://example.com" onClick={handleClick}>
      Click me
    </a>
  );
}
```

  

### Event Delegation / Bubbling Example

```JavaScript
function Parent() {
  const handleClick = () => {
    alert('Parent clicked');
  };

  return (
    <div onClick={handleClick}>
      <button>Child button</button>
    </div>
  );
}
```

- ✔️ Event bubbles up from button to `div`

  

### Updating State on Click

```JavaScript
const [count, setCount] = useState(0);

<button onClick={() => setCount(count + 1)}>Clicked {count} times</button>
```

✅ Common pattern in counter UIs

  

### Stopping Propagation

```JavaScript
function ChildButton() {
  const handleClick = (e) => {
    e.stopPropagation();
    alert('Child button clicked');
  };

  return <button onClick={handleClick}>Click</button>;
}
```

  

### Toggle State with Click

```JavaScript
import { useState } from 'react';

function ToggleButton() {
  const [on, setOn] = useState(false);

  return (
    <button onClick={() => setOn(!on)}>
      {on ? 'ON' : 'OFF'}
    </button>
  );
}
```

  

### Click Events in Child Components

```JavaScript
function Button({ onClick }) {
  return <button onClick={onClick}>Child Button</button>;
}

function Parent() {
  const handleClick = () => alert("Parent clicked!");
  return <Button onClick={handleClick} />;
}
```

✅ Pass functions as props for modular click handling

  

### Prevent Default (e.g. `<a>` tags)

```JavaScript
function handleLinkClick(e) {
  e.preventDefault();
  alert("Link clicked without navigating");
}

<a href="https://example.com" onClick={handleLinkClick}>Click me</a>
```

✅ Stops the default browser behavior

  

### Summary Table

|Use Case|Pattern Example|
|---|---|
|Basic click handler|`onClick={handleClick}`|
|With arguments|`onClick={() => handleClick(arg)}`|
|Access event object|`onClick={(e) => console.log(e.target)}`|
|State update on click|`onClick={() => setState(val + 1)}`|
|Prevent default behavior|`e.preventDefault()`|

  

### Bonus: Double Click

```JavaScript
<button onDoubleClick={() => alert("Double click!")}>Double Click Me</button>
```

  

```JavaScript
function Button() {
  const handleClick = () => {
    console.log("OUCH");
  };

  const handleClick2 = (name) => {
    console.log(`${name} Stop Clicking me`);
  };

  //  use an Function Expression/arrow function to avoid calling the function right away
  return <button onClick={() => handleClick2("Bro Code")}>Click Me ⭐</button>;
}
export default Button;
```

```JavaScript
function Button() {
  let count = 0;

  const handleClick = (name) => {
    if (count < 3) {
      count++;
      console.log(`${name} Clicked Me ${count}`);
    } else {
      console.log(`${name} Stopped Clicking me`);
    }
  };

  //  use an arrow function to avoid calling the function right away. if you have parameters
  return <button onClick={() => handleClick("Bro Code")}>Click Me ⭐</button>;
}
export default Button;
```

  

  

```JavaScript
function Button() {
  const handleClick = (e) => {
    e.target.textContent = "OUCh";
  };

  //  use an arrow function to avoid calling the function right away, if you have parameters
  return <button onClick={(e) => handleClick(e)}>Click Me ⭐</button>;
}
export default Button;
```

  

```JavaScript
function ProfilePic() {
  const imgURL = "./src/assets/Stelle.png";

  const handleClick = (e) => {
    e.target.style.display = "none";
  };

  return <img onClick={(e) => handleClick(e)} src={imgURL}></img>;
}
export default ProfilePic;
```