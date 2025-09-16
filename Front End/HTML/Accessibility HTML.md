---
Created: 2025-06-11T18:11
---
## Web Accessibility (A11y) Cheat Sheet

Making your site usable by everyone, including people with disabilities.

  

### **Images**

- Always use descriptive `alt` text:

```HTML
<img src="cat.jpg" alt="A fluffy gray cat sitting on a windowsill">
```

- If the image is purely decorative, use empty alt:

```HTML
<img src="decorative-border.png" alt="">
```

  

### **Form Elements**

- Link labels with inputs using `for` and `id`:

```HTML
<label for="email">Email:</label>
<input type="email" id="email" name="email" required>
```

- Use fieldsets and legends to group related fields:

```HTML
<fieldset>
  <legend>Choose your favorite fruits</legend>
  <input type="checkbox" id="apple" name="fruits" value="apple">
  <label for="apple">Apple</label>
  <input type="checkbox" id="banana" name="fruits" value="banana">
  <label for="banana">Banana</label>
</fieldset>
```

  

### **Keyboard Navigation**

- Ensure all interactive elements (links, buttons, form controls) are reachable by **Tab** key.
- Use `tabindex="0"` for custom focusable elements.
- Use visible focus styles (outline or box-shadow):

```CSS
a:focus, button:focus {
  outline: 3px solid \#00f;
}
```

  

### **ARIA (Accessible Rich Internet Applications)**

- Add ARIA roles and attributes for complex widgets:

```HTML
<nav role="navigation" aria-label="Primary">
  ...
</nav>

<button aria-expanded="false" aria-controls="menu">Menu</button>
<div id="menu" hidden>
  ...
</div>
```

- Use ARIA only when native HTML can’t do the job.

  

### **Semantic HTML**

- Use correct tags (`<header>`, `<nav>`, `<main>`, `<footer>`, `<article>`, etc.) for better screen reader support.

  

### **Color & Contrast**

- Ensure sufficient contrast (use tools like WebAIM Contrast Checker).
- Don’t rely on color alone to convey information (e.g., add icons or text).

  

### **Accessible Multimedia**

- Provide captions for videos.
- Provide transcripts for audio.
- Use `<track>` element inside `<video>`:

```HTML
<video controls>
  <source src="movie.mp4" type="video/mp4">
  <track kind="captions" src="captions_en.vtt" srclang="en" label="English">
</video>
```

  

### Summary Table

|   |   |
|---|---|
|Area|Tips|
|Images|Use meaningful alt text|
|Forms|Label every input properly|
|Keyboard|Ensure focus and tab navigation|
|ARIA|Use roles & states only when necessary|
|HTML|Use semantic elements|
|Color|Ensure high contrast and avoid color-only cues|
|Multimedia|Provide captions & transcripts|