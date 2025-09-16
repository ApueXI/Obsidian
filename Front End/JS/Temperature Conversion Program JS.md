---
Created: 2025-06-19T08:21
---
```JavaScript
const textbox = document.getElementById("textbox");
const toFahrenheit = document.getElementById("toFahrenheit");
const toCelsius = document.getElementById("toCelsius");
const result = document.getElementById("result");
let temp;

function convert() {
  if (toFahrenheit.checked) {
    temp = Number(textbox.value);
    temp = (temp * 9) / 5 + 32;
    result.textContent = `${temp.toFixed(2)}Fahrenheit`;
  } else if (toCelsius.checked) {
    temp = Number(textbox.value);
    temp = (temp - 32) * (5 / 9);
    result.textContent = `${temp.toFixed(2)}Celsius`;
  } else {
    result.textContent = `Select a unit`;
  }
}
```