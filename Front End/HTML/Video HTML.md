---
Created: 2025-06-06T11:11
---
## HTML Video Cheat Sheet

The `<video>` element is used to **embed video files** directly into a webpage.

  

## **Basic Video Syntax**

```HTML
<video src="movie.mp4" controls></video>
```

|   |   |
|---|---|
|Attribute|Description|
|`src`|Path to the video file|
|`controls`|Adds playback controls (play, pause, volume)|

  

## **Recommended: Use** `**<source>**` **Elements**

```HTML
<video controls>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.webm" type="video/webm">
  Your browser does not support the video tag.
</video>
```

- Allows for **multiple formats** for better browser support.
- Text inside `<video>` is shown if the browser doesn’t support video.

  

## **Common Video Formats**

|   |   |   |
|---|---|---|
|Format|Type|Description|
|`.mp4`|`video/mp4`|Most widely supported format|
|`.webm`|`video/webm`|Efficient for modern browsers|
|`.ogg` / `.ogv`|`video/ogg`|Open format, less common now|

  

## **Important Video Attributes**

|   |   |   |
|---|---|---|
|Attribute|Description|Example|
|`controls`|Shows built-in video player|`controls`|
|`autoplay`|Plays video automatically|`autoplay` _(usually muted)_|
|`loop`|Restarts video after finishing|`loop`|
|`muted`|Starts video with sound off|`muted`|
|`poster`|Image shown before playback|`poster="preview.jpg"`|
|`preload`|Load strategy|`preload="auto"`|

  

## **Autoplay + Loop + Muted Example**

```HTML
<video src="clip.mp4" autoplay loop muted controls></video>
```

> Most browsers block autoplay unless the video is muted.

  

## **Poster Image Example**

```HTML
<video src="trailer.mp4" controls poster="thumbnail.jpg"></video>
```

- Displays an image **before** the video is played.

  

## **Preload Attribute Values**

|   |   |
|---|---|
|Value|Description|
|`auto`|Load video when page loads|
|`metadata`|Only load metadata (duration, etc.)|
|`none`|Don’t preload anything|

```HTML
<video src="video.mp4" controls preload="metadata"></video>
```

  

## **Fallback Message Example**

```HTML
<video controls>
  <source src="video.mp4" type="video/mp4">
  Your browser does not support HTML5 video.
</video>
```

  

## **Styling the Video (CSS Example)**

```CSS
video {
  max-width: 100%;
  height: auto;
  border-radius: 10px;
}
```

- Makes the video responsive and stylish.

  

## Summary Table

|   |   |
|---|---|
|Element / Attribute|Description|
|`<video>`|Embeds a video player|
|`src`|Video file path|
|`<source>`|Multiple formats|
|`controls`|Enables built-in controls|
|`autoplay`|Auto-plays video|
|`loop`|Restarts video after finishing|
|`muted`|Starts muted (required for autoplay)|
|`poster`|Thumbnail before playback|
|`preload`|Loading behavior|

  

## Full Example:

```HTML
<video controls autoplay loop muted preload="auto" poster="cover.jpg">
  <source src="promo.mp4" type="video/mp4">
  <source src="promo.webm" type="video/webm">
  Your browser does not support the video tag.
</video>
```

  

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width= , initial-scale=1.0">
    <title>Video</title>
</head>
<body>
    <a href="twitter.com">
        <Video controls autoplay muted loop src="Video/ssstwitter.com_1746171043172.mp4"></Video>
    </a>
</body>
</html>
```