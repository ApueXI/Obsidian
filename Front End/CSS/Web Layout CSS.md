---
Created: 2025-06-11T08:36
---
```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="WebLayout.css">
    <title>Website Layout</title>
</head>

<body>

    <header>
        <h1>Header</h1>
    </header>

    <nav class="navbar">

    </nav>

    <main>
        <aside>
            <h2>This is aside</h2>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum, voluptates ratione enim fugit debitis
                illo ex iusto necessitatibus possimus quas. Eveniet quidem eligendi vero quibusdam aperiam natus odit
                nesciunt et.</p>
        </aside>
        <section>
            <h2>This is a section</h2>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum, voluptates ratione enim fugit debitis
                illo ex iusto necessitatibus possimus quas. Eveniet quidem eligendi vero quibusdam aperiam natus odit
                nesciunt et.</p>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum, voluptates ratione enim fugit debitis
                illo ex iusto necessitatibus possimus quas. Eveniet quidem eligendi vero quibusdam aperiam natus odit
                nesciunt et.</p>
        </section>
        <article>
            <h2>This is an article</h2>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum, voluptates ratione enim fugit debitis
                illo ex iusto necessitatibus possimus quas. Eveniet quidem eligendi vero quibusdam aperiam natus odit
                nesciunt et.</p>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum, voluptates ratione enim fugit debitis
                illo ex iusto necessitatibus possimus quas. Eveniet quidem eligendi vero quibusdam aperiam natus odit
                nesciunt et.</p>
        </article>
    </main>

    <footer>
        <h2>footer</h2>
    </footer>

</body>

</html>
```

```CSS
*{
    box-sizing: border-box;
}
body {
    margin: 0;
}

header {
    background-color: lightgreen;
    text-align: center;
    padding: 25px;
}

.navbar {
    background-color: black;
    height: 50px;
}

aside {
    width: 20%;
    float: left;
    padding: 10px;
}

section {
    width: 40%;
    float: left;
    padding: 10px;

}

article {
    width: 40%;
    float: left;
    padding: 10px;
}
footer{
    display: block;
    clear: both;
    background-color: rgb(172, 172, 172);
    text-align: center;
    padding: 25px;
}
@media screen and (max-width:600px){
    aside, section, article{
        width: 100%;
    }
}
```