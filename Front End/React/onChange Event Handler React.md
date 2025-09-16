---
Created: 2025-07-10T09:59
---
### What is `onChange`?

The `onChange` handler in React is used to **listen for user input** and **update component state** in real-time.

It works on form elements like:

- `<input>`
- `<textarea>`
- `<select>`
- `<checkbox>`

  

## Text Input Example

```JavaScript
function App() {
  const [text, setText] = useState("");

  const handleChange = (event) => {
    setText(event.target.value);
  };

  return (
    <input type="text" value={text} onChange={handleChange} />
  );
}
```

🧠 `event.target.value` gives you the current input text

✅ Controlled component pattern

  

## Inline Arrow Function

```JavaScript
<input onChange={(e) => setText(e.target.value)} />
```

✅ Great for simple use cases

⚠️ Avoid if the function gets complex or reused

  

## Checkbox Example

```JavaScript
function App() {
  const [isChecked, setIsChecked] = useState(false);

  return (
    <label>
      <inputtype="checkbox"
        checked={isChecked}
        onChange={(e) => setIsChecked(e.target.checked)}
      />
      Accept Terms
    </label>
  );
}
```

🧠 Use `e.target.checked` for checkboxes

  

## Select Dropdown Example

```JavaScript
function App() {
  const [fruit, setFruit] = useState("apple");

  return (
    <select value={fruit} onChange={(e) => setFruit(e.target.value)}>
      <option value="apple">🍎 Apple</option>
      <option value="banana">🍌 Banana</option>
      <option value="orange">🍊 Orange</option>
    </select>
  );
}
```

  

## Reading the Event Object

```JavaScript
const handleChange = (event) => {
  console.log("Input Name:", event.target.name);
  console.log("Input Value:", event.target.value);
};
```

✅ You can access any DOM attribute (e.g., `name`, `value`, `type`, `checked`, etc.)

  

## Summary Table

|Element Type|Value Used Inside Handler|
|---|---|
|Text Input|`event.target.value`|
|Textarea|`event.target.value`|
|Checkbox|`event.target.checked`|
|Radio Button|`event.target.value`|
|Select|`event.target.value`|

  

## Common Mistakes

|Mistake|Fix|
|---|---|
|Forgetting `value={state}`|Always bind value to state for controlled inputs|
|Using `defaultValue` + `onChange`|Use either controlled or uncontrolled, not both|
|Using `event` after async call|Wrap in `e.persist()` or copy `e.target.value`|

  

```JavaScript
import React, { useState } from "react";

function MyComponent() {
  const [name, setName] = useState("Guest");
  const [num, setNum] = useState(1);
  const [comment, setComment] = useState("");
  const [payment, setPayment] = useState("");
  const [shipping, setShippng] = useState("Delivery");

  function nameChange(param) {
    setName(param.target.value);
  }

  function numChange(params) {
    setNum(params.target.value);
  }

  function commentChange(params) {
    console.log(`the change`);

    setComment(params.target.value);
  }

  function paymentChange(params) {
    setPayment(params.target.value);
  }

  function shippingChange(params) {
    setShippng(params.target.value);
  }

  return (
    <>
      <div>
        <input value={name} onChange={nameChange} type="text" name="" id="" />
        <p>Name: {name}</p>
        <br />

        <input value={num} onChange={numChange} type="number" name="" id="" />
        <p>Quantity: {num}</p>
        <br />

        <textarea
          value={comment}
          placeholder="Enter delivery Instructions"
          onChange={commentChange}
        ></textarea>
        <p>Comment: {comment}</p>
        <br />

        <select onChange={paymentChange} value={payment} name="" id="">
          <option value="">Select an Option</option>
          <option value="Visa">Visa</option>
          <option value="Mastercard">Mastercard</option>
          <option value="Giftcard">Giftcard</option>
        </select>
        <p>Payment: {payment}</p>
        <br />

        <label htmlFor="">
          <input
            value="Pick Up"
            checked={shipping === "Pick Up"}
            onChange={shippingChange}
            type="radio"
            name="shipping"
          />
          Pick Up
        </label>
        <br />
        <label htmlFor="">
          <input
            value="Delivery"
            checked={shipping === "Delivery"}
            onChange={shippingChange}
            type="radio"
            name="shipping"
          />
          Delivery
        </label>
        <p>Shipping: {shipping}</p>
      </div>
    </>
  );
}
export default MyComponent;
```