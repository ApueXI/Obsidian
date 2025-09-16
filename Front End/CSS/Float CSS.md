---
Created: 2025-06-09T11:40
---
## `float` – Floating Elements

```CSS
float: left | right | none | inline-start | inline-end;
```

  

## Float Values

|   |   |
|---|---|
|Value|Description|
|`left`|Floats the element to the **left** of its container.|
|`right`|Floats the element to the **right** of its container.|
|`none`|Removes float; element follows normal flow.|
|`inline-start`|Floats according to the **text direction** (LTR or RTL).|
|`inline-end`|Floats to the opposite side of `inline-start`.|

  

```HTML
<style>
    img {
        float: left;
        margin-right: 10px;
    }
</style>
<p><img src="pic.jpg">This text will wrap around the image.</p>
```

  

## Common Issue: Collapsed Parent Height

When all child elements are floated, the parent may collapse (height = 0). Fix it by **clearing the float**.

  

## `clear` – Stop Floating Behavior

```CSS
clear: left | right | both | none;
```

|   |   |
|---|---|
|Value|Description|
|`left`|Prevents the element from sitting next to left-floated elements.|
|`right`|Prevents the element from sitting next to right-floated elements.|
|`both`|Prevents the element from sitting next to any floated elements.|
|`none`|No clearing; default.|

  

## Example: Clearfix (modern solution)

```HTML
<div class="clearfix">
  <div style="float: left;">Box 1</div>
  <div style="float: right;">Box 2</div>
</div>

<style>
    .clearfix::after {
        content: "";
        display: table;
        clear: both;
    }
</style>
```

  

## Float vs Flex/Grid (Modern Advice)

|   |   |   |
|---|---|---|
|Feature|Float|Flexbox/Grid|
|Layout use|Legacy layout tool|Recommended modern layout systems|
|Text wrapping|Yes|Yes (flex/grid with tricks)|
|Responsive design|Harder|Easier|
|Centering|Hard|Easy|

  

## Bonus: Float Reset on Forms

Sometimes form elements float unexpectedly—always remember:

```CSS
input, button {
  float: none;
}
```

  

  

  

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="Float.css">
    <title>Float</title>
</head>

<body>

    <img id="img" src="images/huashiJW_banner.jpg" alt="">

    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Recusandae a et itaque veniam veritatis ea aperiam eius
        nulla iste placeat cum, quibusdam accusantium repellendus cumque dicta maiores. Sunt, quidem beatae?
    </p>
    
    <p>Dolorum, cum quidem perspiciatis reiciendis non facere neque! Nemo velit fugiat laudantium nobis illum veniam,
        vitae rerum, voluptatem facere voluptate, accusamus distinctio culpa error ab sit numquam. Repellat,
        necessitatibus rem?
    </p>

    <img id="img2" src="images/huashiJW_banner.jpg" alt="">

    <p>Quis earum enim aliquid odio reprehenderit, quo quia iure, ratione, incidunt quaerat minus facilis alias
        eligendi! Debitis, ad deleniti quae fuga, tenetur temporibus quisquam officia natus nam incidunt, provident
        magnam.
    </p>

    <p>Quis earum enim aliquid odio reprehenderit, quo quia iure, ratione, incidunt quaerat minus facilis alias
        eligendi! Debitis, ad deleniti quae fuga, tenetur temporibus quisquam officia natus nam incidunt, provident
        magnam.
    </p>

</body>

</html>
```

```CSS
\#img{
    height: 150px;
    float: left;
    margin-left: 3vh;
}
\#img2{
    height: 150px;
    float: right;
    margin-left: 3vh;
}
body{
    border: 2px solid black;
    display: flow-root;
}
```