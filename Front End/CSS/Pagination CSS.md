---
Created: 2025-06-10T11:48
---
pagination = method by which a document is separated into pages, and numbers given

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="Pagination.css">
    <title>Paginition</title>
</head>

<body>

    <h1>This is page number 1</h1>
    <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Cupiditate ad odio fuga accusantium sit saepe animi,
        ducimus perferendis reprehenderit nostrum soluta sint earum provident qui laborum eum, quisquam vero accusamus.
    </p>
    <div class="pagination">
        <a href="Pagination.html">&lt</a>
        <a href="Pagination.html" class="active">1</a>
        <a href="pages/page2.html">2</a>
        <a href="pages/page3.html">3</a>
        <a href="pages/page4.html">4</a>
        <a href="pages/page5.html">5</a>
        <a href="pages/page2.html">&gt</a>
    </div>

</body>

</html>
```

```CSS
.pagination {
    text-align: center;
}

.pagination a {
    color: black;
    text-decoration: none;
    padding: 8px 15px;
    display: inline-block;
}

.pagination a.active {
    background-color: rgb(21, 250, 21);
    border-radius: 10px;
    font-weight: bold;
}

.pagination a:hover:not(.active) {
    background-color: grey;
    border-radius: 10px;
}
```

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="../Pagination.css">
    <title>Paginition</title>
</head>

<body>

    <h1>This is page number 2</h1>
    <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Cupiditate ad odio fuga accusantium sit saepe animi,
        ducimus perferendis reprehenderit nostrum soluta sint earum provident qui laborum eum, quisquam vero accusamus.
    </p>
    <div class="pagination">
        <a href="../Pagination.html">&lt</a>
        <a href="../Pagination.html">1</a>
        <a href="page2.html" class="active">2</a>
        <a href="page3.html">3</a>
        <a href="page4.html">4</a>
        <a href="page5.html">5</a>
        <a href="page3.html">&gt</a>
    </div>

</body>

</html>
```