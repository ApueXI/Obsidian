---
Created: 2025-06-09T20:51
---
`height` & `width` – Control Element Size

```CSS
height: value;
width: value;
```

  

### Values You Can Use

|   |   |   |
|---|---|---|
|Value Type|Examples|Description|
|**Length**|`100px`, `50em`, `10rem`|Fixed size in pixels, ems, rems, etc.|
|**Percentage**|`50%`, `100%`|Relative to the parent element’s size|
|**Auto**|`auto`|Default — size determined by content or context|
|**Max-content**|`max-content`|Size to fit the largest content without wrapping|
|**Min-content**|`min-content`|Minimum size needed for content|
|**Fit-content**|`fit-content(200px)`|Size up to a max (like minmax)|
|**Viewport units**|`100vw`, `50vh`|Percentage of viewport width or height|

  

### Examples

```CSS
div {
  width: 300px;
  height: 150px;
}

img {
  width: 100%;    /* Fill container width */
  height: auto;   /* Maintain aspect ratio */
}

section {
  width: 80vw;    /* 80% of viewport width */
  height: 50vh;   /* 50% of viewport height */
}
```

  

`max-width` / `min-width` & `max-height` / `min-height`

|   |   |
|---|---|
|Property|Description|
|`max-width`|Maximum width the element can grow to|
|`min-width`|Minimum width the element can shrink to|
|`max-height`|Maximum height allowed|
|`min-height`|Minimum height allowed|

### examples

|   |   |
|---|---|
|Property|Description|
|`max-width`|Maximum width the element can grow to|
|`min-width`|Minimum width the element can shrink to|
|`max-height`|Maximum height allowed|
|`min-height`|Minimum height allowed|

  

`auto` vs Fixed Size

- `auto` lets the element size itself based on content or context.
- Fixed sizes (`px`, `em`) force exact dimensions.

  

## Common Use Cases

- **Responsive images:** `width: 100%; height: auto;`
- **Full viewport section:** `height: 100vh;`
- **Center box:** fixed width + auto margin (with height set or auto)

  

## Bonus: Aspect Ratio (CSS Level 4)

```CSS
.element {
  aspect-ratio: 16 / 9;
  width: 100%;
  height: auto;
}
```

Maintains width-to-height ratio automatically

  

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="HeightAndWidth.css">
    <title>Height And Width</title>
</head>

<body>

    <div class="container">

        <div class="box">
            <h2>This is number one</h2>
        </div>
        <div class="box">
            <h2>This is number two</h2>
        </div>

    </div>

</body>

</html>
```

```CSS
.box {
    border: 2px solid black;
    background-color: white;
    padding: 25px;
    box-sizing: border-box;
    height: auto;
    width: 50%;
    float: left;
    text-align: center;
    
    max-width: 50%;
    min-width: 25%;

    min-height: 50%;
}
.container {
    background-color: grey;
    height: 100vh;
}
```

Asterisk means to apply to all element

```CSS
* {
    box-sizing: border-box;
}
```

  

```JavaScript
const checkbox = document.getElementById("checkbox");
const visa = document.getElementById("visa");
const mastercard = document.getElementById("mastercard");
const paypal = document.getElementById("paypal");
const submit = document.getElementById("submit");
const sub = document.getElementById("sub");
const payment = document.getElementById("payment");

submit.onclick = function () {
  if (checkbox.checked) {
    sub.textContent = `You are subscribe`;
  } else {
    sub.textContent = `You are not subscribe`;
  }
  if (visa.checked) {
    payment.textContent = `You are have payed though visa`;
  } else if (mastercard.checked) {
    payment.textContent = `You are have payed though mastercard`;
  } else if (paypal.checked) {
    payment.textContent = `You are have payed though paypal`;
  } else {
    payment.textContent = `You are have must select a payment method`;
  }
};
```

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>CHecked Box Property</title>
    <style>
      label {
        font-size: 2em;
      }

      input {
        height: 3vh;
        width: 3vh;
      }

      button {
        font-size: 2em;
      }
    </style>
  </head>

  <body>
    <input type="checkbox" name="" id="checkbox" />
    <label for="checkbox">subscribe</label><br />

    <input type="radio" name="card" id="visa" />
    <label for="visa">visa</label><br />

    <input type="radio" name="card" id="mastercard" />
    <label for="mastercard">mastercard</label><br />

    <input type="radio" name="card" id="paypal" />
    <label for="paypal">paypal</label><br />

    <button type="submit" id="submit">submit</button>

    <p id="sub"></p>
    <p id="payment"></p>

    <script src="../CHeckedBoxProperty.js"></script>
  </body>
</html>
```