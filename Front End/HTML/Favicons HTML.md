---
Created: 2025-06-06T11:27
---
## HTML Favicons Cheat Sheet

A **favicon** (short for “favorite icon”) is the **small icon** shown in the browser tab, bookmarks, and browser history. It helps with **branding** and **user recognition**.

  

## **Basic Favicon Syntax**

```HTML
<link rel="icon" href="favicon.ico" type="image/x-icon">
```

- Should be placed **inside** `**<head>**`
- `href` points to the icon file
- `type` defines the file MIME type

  

## **Common Favicon File Formats**

|   |   |   |
|---|---|---|
|Format|MIME Type|Notes|
|`.ico`|`image/x-icon`|Most widely supported|
|`.png`|`image/png`|Higher quality, modern browsers|
|`.svg`|`image/svg+xml`|Scalable, sharp on all screens|
|`.gif`|`image/gif`|Rare, may be animated|
|`.jpg`|`image/jpeg`|Not recommended (no transparency)|

  

## **Modern Example With Multiple Sizes**

```HTML
<link rel="icon" href="favicon-32.png" sizes="32x32" type="image/png">
<link rel="icon" href="favicon-16.png" sizes="16x16" type="image/png">
```

- Use multiple sizes for best appearance on all devices.

  

## **High-Resolution (Retina) Favicon**

```HTML
<link rel="icon" href="favicon.svg" type="image/svg+xml">
```

- **SVG format** ensures crisp rendering on all screen sizes and zoom levels.

  

## **Apple Touch Icon (iOS Home Screen)**

```HTML
<link rel="apple-touch-icon" href="apple-touch-icon.png">
```

- Used when users **add your site to their iPhone home screen**.

  

## **Favicon for Web App (PWA / Android)**

```HTML
<link rel="manifest" href="site.webmanifest">
```

- Used for progressive web apps. The manifest file includes app icons, colors, and metadata.

  

## **Favicon Generator Tools**

You can use online generators to automatically create and link all required favicon files:

- ==[https://realfavicongenerator.net](https://realfavicongenerator.net/)==
- ==[https://favicon.io](https://favicon.io/)==

  

## **Complete Example With Fallbacks**

```HTML
<head>
  <link rel="icon" href="/favicon.ico" type="image/x-icon">
  <link rel="icon" href="/favicon-32x32.png" sizes="32x32" type="image/png">
  <link rel="icon" href="/favicon-16x16.png" sizes="16x16" type="image/png">
  <link rel="apple-touch-icon" href="/apple-touch-icon.png">
  <link rel="manifest" href="/site.webmanifest">
</head>
```

  

## Summary Table

|   |   |
|---|---|
|Tag/Attribute|Purpose|
|`<link rel="icon">`|Main favicon|
|`href`|Path to favicon file|
|`type`|MIME type (`image/png`, `image/x-icon`, etc.)|
|`sizes`|Favicon dimensions (`32x32`, etc.)|
|`rel="apple-touch-icon"`|iOS Home Screen icon|
|`rel="manifest"`|Web app metadata|

  

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="icon" type="image/jpg" href="images/huashiJW_banner.jpg" >
    <title>Favisons</title>
</head>
<body>
    
</body>
</html>
```