---
Created: 2025-06-06T10:49
---
## HTML Images Cheat Sheet

Images in HTML are added using the `<img>` tag. It is a **self-closing** tag that **does not need a closing** `**</img>**`.

  

## **Basic Image Syntax**

```HTML
<img src="image.jpg" alt="Description of image">
```

|   |   |
|---|---|
|Attribute|Purpose|
|`src`|Source (URL or file path) of the image|
|`alt`|Alternative text for accessibility and when image can't load|

  

## **Common Attributes**

|   |   |   |
|---|---|---|
|Attribute|Description|Example|
|`src`|Path to the image file|`src="images/photo.jpg"`|
|`alt`|Text shown if image fails or for screen readers|`alt="Mountain landscape"`|
|`width`|Width of image (in px or %)|`width="300"` or `width="50%"`|
|`height`|Height of image|`height="200"`|
|`title`|Tooltip shown on hover|`title="This is a beach"`|
|`loading`|Lazy load control|`loading="lazy"` or `"eager"`|

  

## **Image Formats**

|   |   |   |
|---|---|---|
|Format|Best For|Example|
|`.jpg` / `.jpeg`|Photos, good compression|`img.jpg`|
|`.png`|Transparency|`logo.png`|
|`.gif`|Simple animations|`animation.gif`|
|`.webp`|Modern, fast, small size|`image.webp`|
|`.svg`|Scalable vector (logos/icons)|`icon.svg`|

  

## **Responsive Images (HTML5)**

### `srcset` and `sizes` for responsive loading:

```HTML
<img
  src="small.jpg"
  srcset="medium.jpg 768w, large.jpg 1200w"
  sizes="(max-width: 768px) 100vw, 50vw"
  alt="Responsive image">
```

- `**srcset**`: List of images with width hints
- `**sizes**`: What image width should be used under different screen sizes

  

## **Clickable Image**

```HTML
<a href="https://example.com">
  <img src="logo.png" alt="Company Logo">
</a>
```

  

## **Image Inside a Figure with Caption**

```HTML
<figure>
  <img src="sunset.jpg" alt="Sunset view">
  <figcaption>Beautiful sunset at the beach</figcaption>
</figure>
```

- `figcaption` provides a visible caption.

  

## **Image Styling Tips (CSS)**

```CSS
img {
  max-width: 100%;
  height: auto;
  border-radius: 10px;
}
```

- Makes image **responsive** and keeps aspect ratio.

  

## **Lazy Loading (Performance Boost)**

```HTML
<img src="large.jpg" loading="lazy" alt="Big image">
```

- Delays image load until it's visible in the viewport.

  

## **Broken Image Example (for** `**alt**` **fallback)**

```HTML
<img src="notfound.jpg" alt="Image failed to load">
```

- If the image is missing, the **alt text** will show.

  

## Summary Table

|   |   |
|---|---|
|Tag / Attribute|Description|
|`<img>`|Embeds an image|
|`src`|Image file path|
|`alt`|Fallback text / accessibility|
|`title`|Tooltip text|
|`width` / `height`|Controls size|
|`loading`|Lazy-load image|
|`srcset` / `sizes`|Responsive images|
|`<figure>` / `<figcaption>`|Image with caption|

  

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Images</title>
</head>

<body>
    <a href="https://monkeytype.com/" target="_blank">
        <img src="images/huashiJW_banner.jpg" alt="huashiJW_banner" height="500px" width="700px">
    </a>
</body>

</html>
```