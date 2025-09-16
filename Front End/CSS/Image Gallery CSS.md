---
Created: 2025-06-11T20:25
---
```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="ImgGallery.css">
    <title>Image Gallery</title>
</head>

<body>

    <div class="gallery">
        <a href="images/huashiJW_banner.jpg" target="_blank">
            <img src="images/huashiJW_banner.jpg" alt="Huashi">
            <div class="description">Huashi</div>
        </a>
    </div>
    <div class="gallery">
        <a href="images/Senti_crayonblue.png" target="_blank">
            <img src="images/Senti_crayonblue.png" alt="Senti">
            <div class="description">Senti</div>
        </a>
    </div>
    <div class="gallery">
        <a href="images/Stelle.png" target="_blank">
            <img src="images/Stelle.png" alt="Stelle">
            <div class="description">Stelle</div>
        </a>
    </div>

</body>

</html>
```

```CSS
.gallery{
    display: inline-block; 
    border: 1px solid darkgrey;
    margin: 5px;
    width: 150px;
}
.gallery .description{
    padding: 10px;
    text-align: center;
}
.gallery:hover{
    border: 1px solid rgb(0, 0, 0);
}
.gallery img{
    width: 100%;
    height: auto;
}
```