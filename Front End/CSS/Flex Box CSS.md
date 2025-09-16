---
Created: 2025-06-12T12:27
---
### **Enable Flexbox**

```CSS
.container {
  display: flex; /* or inline-flex */
}
```

  

### **Main Axis & Cross Axis**

- **Main axis:** Default is horizontal (left to right).
- **Cross axis:** Perpendicular to main axis (vertical).

  

### **Container Properties**

|   |   |   |
|---|---|---|
|Property|Values|Description|
|`flex-direction`|`row` (default), `row-reverse`, `column`, `column-reverse`|Direction of flex items|
|`flex-wrap`|`nowrap` (default), `wrap`, `wrap-reverse`|Allow items to wrap to next line|
|`justify-content`|`flex-start` (default), `flex-end`, `center`, `space-between`, `space-around`, `space-evenly`|Align items along main axis|
|`align-items`|`stretch` (default), `flex-start`, `flex-end`, `center`, `baseline`|Align items along cross axis|
|`align-content`|`stretch` (default), `flex-start`, `flex-end`, `center`, `space-between`, `space-around`|Align wrapped lines (multi-line)|

  

### **Item Properties**

|   |   |   |
|---|---|---|
|Property|Values|Description|
|`order`|Number (default 0)|Controls item order|
|`flex-grow`|Number (default 0)|How much item grows relative to others|
|`flex-shrink`|Number (default 1)|How much item shrinks if needed|
|`flex-basis`|Length or `auto` (default)|Initial size before growing/shrinking|
|`flex`|Shorthand for grow, shrink, basis (e.g., `flex: 1 0 auto;`)|Set grow, shrink, and basis together|
|`align-self`|`auto` (default), `flex-start`, `flex-end`, `center`, `baseline`, `stretch`|Override container’s align-items per item|

  

### **Example: Basic Flexbox Layout**

```CSS
.container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

.item {
  flex: 1; /* all items grow equally */
  margin: 5px;
}
```

  

### **Common Use Cases**

|   |   |
|---|---|
|Layout|Example Property Values|
|Center items horizontally|`justify-content: center;`|
|Center items vertically|`align-items: center;`|
|Space items evenly|`justify-content: space-evenly;`|
|Wrap items on smaller screens|`flex-wrap: wrap;`|
|Reverse order|`flex-direction: row-reverse;`|

  

### **Tips**

- Use `flex: 1` on items to distribute remaining space evenly.
- `align-self` lets you customize alignment for a single flex item.
- `flex-wrap: wrap` is essential for responsive multi-line flex layouts.

  

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="FlexBox.css">
    <title>Flex Box</title>
</head>
<body>
    
    <div class="container">
        <div class="box" id="box1">1</div>
        <div class="box" id="box2">2</div>
        <div class="box" id="box3">3</div>
        <div class="box" id="box4">4</div>
        <div class="box" id="box1">5</div>
        <div class="box" id="box2">6</div>
        <div class="box" id="box3">7</div>
        <div class="box" id="box4">8</div>
    </div>

</body>
</html>
```

```CSS
.box{
    width: 150px;
    height: 150px;
    font-size: 8em;
    text-align: center;
    border-radius: 15px;
}
.container{
    display: flex;
    border: 10px solid black;
    height: 90vh;
    column-gap: 1em;
    row-gap: 1em;
}
\#box1{
    background-color: red;
    align-self: start;
}
\#box2{
    background-color: yellow;
    order: 1;
}
\#box3{
    background-color: green;
    order: -1;
}
\#box4{
    background-color: blue;
}
```