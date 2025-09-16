---
Created: 2025-06-11T06:58
---
```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="NavBar.css">
    <title>Nav Bar</title>
</head>

<body>

    <h1>Bro Code</h1>

    <nav class="navbar">
        <ul>
            <li><a href="NavBar.html">Home</a></li>
            <li><a href="pages/about.html">About</a></li>
            <li><a href="pages/product.html">Product</a></li>
            <li><a href="pages/contact.html">Contact</a></li>
        </ul>
    </nav>

    <main>
        <h3>This is the home page</h3>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolore nesciunt ipsum tempore laudantium sunt harum
            sapiente! Asperiores dignissimos sit, alias incidunt amet eius in, at distinctio laborum quia, totam enim.
        </p>
    </main>

</body>

</html>
```

```CSS
body{
    margin: 0px;
}
main{
    margin-left: 20px;
    margin-right: 20px;
}
h1{
    text-align: center;
}
.navbar ul{
    list-style-type: none;
    background-color: grey;
    padding: 0px;
    margin: 0px;
    overflow: hidden;
}
.navbar a{
    color: white;
    text-decoration: none;
    padding: 10px;
    display: block;
    text-align: center;
}
.navbar a:hover{
    background-color: green;
}
.navbar li{
    float: left;
}
```

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="../NavBar.css">
    <title>Nav Bar</title>
</head>

<body>

    <h1>Bro Code</h1>

    <nav class="navbar">
        <ul>
            <li><a href="../NavBar.html">Home</a></li>
            <li><a href="about.html">About</a></li>
            <li><a href="product.html">Product</a></li>
            <li><a href="contact.html">Contact</a></li>
        </ul>
    </nav>

    <main>
        <h3>This is the product page</h3>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolore nesciunt ipsum tempore laudantium sunt harum
            sapiente! Asperiores dignissimos sit, alias incidunt amet eius in, at distinctio laborum quia, totam enim.
        </p>
    </main>

</body>

</html>
```