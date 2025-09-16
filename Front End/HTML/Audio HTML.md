---
Created: 2025-06-06T10:52
---
## HTML Audio Cheat Sheet

The `<audio>` element allows you to **embed sound files** (music, sound effects, podcasts) into a webpage.

  

## **Basic Audio Syntax**

```HTML
<audio src="audio.mp3" controls></audio>
```

|   |   |
|---|---|
|Attribute|Description|
|`src`|Path to audio file|
|`controls`|Displays playback controls (play, pause, volume)|

  

## **Recommended: Using** `**<source>**` **Elements**

```HTML
<audio controls>
  <source src="audio.mp3" type="audio/mpeg">
  <source src="audio.ogg" type="audio/ogg">
  Your browser does not support the audio element.
</audio>
```

- Ensures better **browser compatibility** by providing multiple formats.
- The text inside `<audio>` is shown if audio is not supported.

  

## **Common Audio File Formats**

|   |   |   |
|---|---|---|
|Format|Type|Description|
|`.mp3`|`audio/mpeg`|Most widely supported|
|`.ogg`|`audio/ogg`|Open format, good quality|
|`.wav`|`audio/wav`|Uncompressed, large files|

  

## **Important** `**<audio>**` **Attributes**

|   |   |
|---|---|
|Attribute|Description|
|`controls`|Shows audio player UI|
|`autoplay`|Starts playing automatically _(often blocked)_|
|`loop`|Repeats the audio once it ends|
|`muted`|Starts the audio muted|
|`preload`|Hints to browser when to load the audio|
|`src`|Audio file source (can be inline or in `<source>`)|

  

## **Autoplay + Loop Example**

```HTML
<audio src="song.mp3" autoplay loop muted controls></audio>
```

> Note: Most browsers block autoplay unless the audio is muted or user interacts with the page.

  

## **Preload Attribute Options**

```HTML
<audio preload="auto"></audio>
```

|   |   |
|---|---|
|Value|Description|
|`auto`|Load full file if possible|
|`metadata`|Load only metadata (duration, etc.)|
|`none`|Don’t preload anything until play is requested|

  

## **Fallback Text Example**

```HTML
<audio controls>
  <source src="track.ogg" type="audio/ogg">
  <source src="track.mp3" type="audio/mpeg">
  Your browser does not support HTML audio.
</audio>
```

  

## **Styling Audio (CSS Example)**

```CSS
audio {
  width: 100%;
  outline: none;
}
```

- Audio players can be styled to fit layout needs.

  

## Summary Table

|   |   |
|---|---|
|Element / Attribute|Purpose|
|`<audio>`|Embeds an audio player|
|`src`|Audio file path|
|`<source>`|Used for multiple file formats|
|`controls`|Shows playback buttons|
|`autoplay`|Starts playback automatically|
|`loop`|Repeats when finished|
|`muted`|Mutes audio on load|
|`preload`|Loading behavior hint|

  

## Example: Full Use Case

```HTML
<audio controls preload="metadata" loop>
  <source src="background-music.mp3" type="audio/mpeg">
  <source src="background-music.ogg" type="audio/ogg">
  Your browser does not support the audio element.
</audio>
```

  

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Audio</title>
</head>

<body>
    <audio controls autoplay muted loop src="songs/AKASAKIBunny GirlLyric Video.mp3">
    </audio>
    <audio controls autoplay muted loop>
        <source src="songs/AKASAKIBunny GirlLyric Video.wav" type="audio/wav">
    </audio>
</body>

</html>
```