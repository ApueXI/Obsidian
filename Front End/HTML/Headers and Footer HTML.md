---
Created: 2025-06-07T08:14
---
## HTML Semantic Elements Cheat Sheet

**Semantic elements** clearly describe their meaning **both to the browser and the developer** — improving readability, accessibility, and SEO.

  

## **Main Semantic Tags & Their Roles**

|   |   |
|---|---|
|Tag|Description|
|`<header>`|Intro or navigational section of a page or section|
|`<nav>`|Major navigation links|
|`<main>`|Central, unique content of the page|
|`<section>`|Thematic grouping of content|
|`<article>`|Self-contained content (e.g., blog post, news)|
|`<aside>`|Secondary info (e.g., sidebar, ad, note)|
|`<footer>`|Closing content for a page or section|
|`<figure>`|A media container with a caption|
|`<figcaption>`|Caption for the `<figure>`|
|`<time>`|Represents a time or date|
|`<mark>`|Highlights or marks text|
|`<address>`|Contact information|

  

## **Basic Structure Using Semantics**

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Semantic Page</title>
  </head>
  <body>
    <header>
      <h1>My Blog</h1>
      <nav>
        <a href="/">Home</a>
        <a href="/about">About</a>
      </nav>
    </header>

    <main>
      <article>
        <h2>Post Title</h2>
        <p>Written on <time datetime="2025-06-11">June 11, 2025</time></p>
        <p>This is the content of the article.</p>
      </article>

      <aside>
        <h3>About the Author</h3>
        <p>Jane Doe is a web developer...</p>
      </aside>
    </main>

    <footer>
      <p>&copy; 2025 My Blog</p>
      <address>Contact: blog@example.com</address>
    </footer>
  </body>
</html>
```

  

## **When to Use What?**

|   |   |
|---|---|
|Use Case|Semantic Tag|
|Top of page or section|`<header>`|
|Bottom of page or section|`<footer>`|
|Navigation menu|`<nav>`|
|Unique content per page|`<main>`|
|Thematic group (e.g., news feed)|`<section>`|
|Standalone article (e.g., blog post)|`<article>`|
|Sidebar or note|`<aside>`|
|Image with caption|`<figure>` + `<figcaption>`|
|Highlighted search result|`<mark>`|
|Publication or event date|`<time>`|
|Contact details|`<address>`|

  

## **Why Use Semantic HTML?**

✅ Improves SEO

✅ Boosts accessibility (screen readers)

✅ Makes your code cleaner and more readable

✅ Helps search engines and developers understand your structure better

  

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Headers and Footer</title>
</head>

<body>
    <header>
        <h1>Welcome to OneDee</h1>
        <a href="">Contact</a>
        <a href="">About</a>
        <a href="">Product</a>
        <hr>
    </header>

    <main>
        <h4>Check out this cool moves</h4>
        <img src="images/huashiJW_banner.jpg" alt="" style="height: 400px;">
        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Blanditiis, facilis! Quas, delectus
            repellat rem pariatur minus, possimus et dolor eos dolore vitae qui fuga ipsam ratione itaque porro corrupti
            ad!
        </p>
    </main>

    <footer>
        <hr>
        Author: Bro Code <br>
        &copy; copyright reserved <br>
        <a href="mailto:@gmail.com">Email</a>
    </footer>
</body>

</html>
```