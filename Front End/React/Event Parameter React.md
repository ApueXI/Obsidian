---
Created: 2025-07-09T20:25
---
### What Is the `event` Parameter?

React wraps browser events into a **SyntheticEvent** object to provide consistent behavior across browsers.

When an event occurs (like a button click), React passes the event object to your handler automatically

  

### Accessing the Event Object

```JavaScript
function handleClick(event) {
  console.log(event); // SyntheticEvent
  console.log(event.target); // The clicked DOM element
}

<button onClick={handleClick}>Click Me</button>
```

✅ The `event` is automatically passed by React.

  

### Preventing Default Behavior

```JavaScript
function handleLinkClick(e) {
  e.preventDefault();
  alert("Default link behavior prevented");
}

<a href="https://example.com" onClick={handleLinkClick}>Don't go</a>
```

✅ Use `.preventDefault()` to stop the browser's default behavior.

  

### Accessing Event Values (e.g. `onChange`)

```JavaScript
function handleInputChange(event) {
  console.log(event.target.value);
}

<input type="text" onChange={handleInputChange} />
```

✅ Use `event.target.value` to get the input's current value.

  

### With Extra Parameters

You **must** use an arrow function to include custom arguments:

```JavaScript
function handleClick(id, event) {
  console.log("ID:", id);
  console.log("Event Target:", event.target);
}

<button onClick={(e) => handleClick(42, e)}>Click</button>
```

  

### Common Event Properties

|Property|Description|
|---|---|
|`event.target`|The element that triggered the event|
|`event.currentTarget`|The element the handler is bound to|
|`event.preventDefault()`|Stops default browser behavior|
|`event.stopPropagation()`|Stops bubbling to parent elements|
|`event.type`|The type of event (`click`, `change`, etc.)|
|`event.nativeEvent`|Access raw browser event (not synthetic)|

  

### SyntheticEvent vs NativeEvent

```JavaScript
function handleClick(e) {
  console.log(e); // SyntheticEvent
  console.log(e.nativeEvent); // Real browser event
}
```

✅ Use `.nativeEvent` only when you need low-level browser info.

  

### Summary

|Use Case|Example|
|---|---|
|Access click event|`onClick={(e) => console.log(e.target)}`|
|Prevent default link behavior|`e.preventDefault()`|
|Read input value|`e.target.value`|
|Pass extra arguments with event|`onClick={(e) => handler(arg, e)}`|