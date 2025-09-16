---
Created: 2025-06-10T12:33
---
```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="DropDownMenu.css">
    <title>Drop Down Menu</title>
</head>

<body>

    <div class="dropdown">
        <button class="button">Food</button>
        <div class="content">
            <a href="">Apple</a>
            <a href="">Orange</a>
            <a href="">Banana</a>
        </div>
    </div>

    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Harum voluptatum doloremque dolorem illo, et
        consectetur ab, aliquam ipsum impedit totam similique. Enim, consequatur quia aspernatur dicta placeat
        asperiores suscipit quis.</p>

</body>

</html>
```

```CSS
.dropdown {
    display: inline-block;
}
.button{
    background-color: grey;
    color: white;
    padding: 10px 15px;
    border: none;
    cursor: pointer;
}
.dropdown a {
    display: block;
    color: black;
    text-decoration: none;
    padding: 10px 15px;
}
.dropdown .content{
    display: none;
    position: absolute;
    background-color: hsl(0, 0%, 74%);
    min-width: 100px;
    box-shadow: 2px 2px 5px black;
}
.dropdown:hover .content {
    display: block;
}
.dropdown:hover .button {
    background-color: hsl(0, 100%, 45%);
}
.dropdown .content a:hover{
    background-color: aqua;
}
```