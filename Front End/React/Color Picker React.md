---
Created: 2025-07-10T12:11
---
```JavaScript
import React, { useState } from "react";

function ColorPicker() {
  const [color, setColor] = useState("\#FFFFFF");

  function changeColor(params) {
    setColor(params.target.value);
  }

  return (
    <>
      <div className="color-picker-container">
        <h1>Color Picker</h1>
        <div className="color-display" style={{ backgroundColor: color }}>
          <p>Selected Color {color}</p>
        </div>
        <label htmlFor="">Select a color</label>
        <input
          type="color"
          name=""
          id=""
          value={color}
          onChange={changeColor}
        />
      </div>
    </>
  );
}
export default ColorPicker;
```

```CSS
body {
  font-family: sans-serif, Arial, Helvetica, sans-serif;
}
.color-picker-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
h1 {
  margin: 50px;
  font-size: 3rem;
}
.color-display {
  width: 300px;
  height: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: bold;
  border: 5px solid hsl(0, 0%, 80%);
  border-radius: 15px;
  margin-bottom: 25px;
  transition: 0.25sec ease;
}
.color-display p {
  color: hsl(0, 0%, 20%);
  font-size: 2rem;
  text-align: center;
}
label {
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 10px;
}
input[type="color"] {
  width: 75px;
  height: 50px;
  padding: 5px;
  border-radius: 15px;
  border: 3px solid hsl(0, 0%, 80%);
}
```