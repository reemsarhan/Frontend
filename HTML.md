# HTML Interview Questions

###  What is HTML? 
HTML (HyperText Markup Language) is the standard language used to create and design web pages. It defines the structure of a webpage using elements such as headings, paragraphs, links, images, and forms.

###  What are HTML tags and attributes? 
- **Tags:** HTML tags are the building blocks of an HTML page, enclosed in angle brackets (`< >`). Example: `<p>`, `<a>`, `<div>`.
- **Attributes:** Attributes provide additional information about an element and are always defined in the opening tag. Example: `<a href="https://example.com">Click here</a>`.

###  What is the difference between HTML and XHTML? 
- **HTML** is more flexible and does not require strict syntax.
- **XHTML** (Extensible HTML) follows stricter rules, such as properly nesting elements and always closing tags.

###  What is the difference between `<div>` and `<span>`? 
- `<div>` is a block-level element used to group larger sections of HTML.
- `<span>` is an inline element used to style or manipulate specific portions of text inside a block.

###  What is semantic HTML?
Semantic HTML uses meaningful tags that describe their purpose, such as `<header>`, `<article>`, `<section>`, and `<footer>`, improving accessibility and SEO.


###  What is the difference between inline, block, and inline-block elements?
- **Block elements:** Take up the full width available (e.g., `<div>`, `<p>`, `<h1>`).
- **Inline elements:** Take up only as much width as needed (e.g., `<span>`, `<a>`, `<strong>`).
- **Inline-block elements:** Behave like inline elements but allow height and width adjustments.

###  What is the difference between id and class attributes? 
- **id** is unique and can be applied to a single element (`id="header"`).
- **class** can be used on multiple elements (`class="button"`).

###  What are the different types of lists in HTML?   
- **Ordered List (`<ol>`):** Numbered items.
- **Unordered List (`<ul>`):** Bulleted items.
- **Definition List (`<dl>`):** A set of terms (`<dt>`) and definitions (`<dd>`).

###  What is the difference between absolute, relative, and fixed paths in HTML? 
- **Absolute Path:** Specifies the full URL (`https://example.com/images/logo.png`).
- **Relative Path:** Refers to a location relative to the current document (`./images/logo.png`).
- **Fixed Path:** Typically starts from the root directory (`/images/logo.png`).

###  What is the alt attribute in an `<img>` tag? 
The `alt` attribute provides alternative text for an image if it fails to load, improving accessibility.


###  What is the difference between `<iframe>` and `<frame>`?  
- `<iframe>`: Embeds another webpage within the current page.
- `<frame>`: Used in `<frameset>`, which is deprecated in HTML5.

###  What is the use of the `<meta>` tag?  
The `<meta>` tag provides metadata about the HTML document, such as:
```html
<meta charset="UTF-8">
<meta name="description" content="HTML Interview Questions">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

###  What is the difference between `<b>` and `<strong>`?  
- `<b>` makes text bold without adding importance.  
- `<strong>` makes text bold and indicates importance, improving accessibility.

###  What are data- attributes in HTML?
Custom attributes used to store extra information on elements.
```html
<div data-user-id="1234">John Doe</div>
```

### How can you make an HTML page responsive?
#### Use the <meta name="viewport" content="width=device-width, initial-scale=1.0"> tag.
#### Use CSS media queries.
#### Use flexible layouts with percentages instead of fixed units.

### What is the difference between <script> and <noscript>?
#### <script>: Embeds JavaScript.
#### <noscript>: Displays alternative content if JavaScript is disabled.

### What is the difference between defer and async in <script>?
#### async: Loads and executes JavaScript as soon as possible without blocking HTML parsing.
#### defer: Loads the script in the background and executes it after HTML parsing.

### What is the purpose of the download attribute in <a> tags?
The download attribute allows users to download a file instead of navigating to the link.

```
<a href="file.pdf" download="myfile.pdf">Download PDF</a>
```

### How do you embed audio and video in HTML5?
 ```
<audio controls>
  <source src="audio.mp3" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>

```
```
<video controls width="400">
  <source src="video.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
```
### What is the difference between <section> and <article>?
<section>: Represents a general section of a page.
<article>: Represents self-contained content that can stand alone.

  
### HTML5 Features 
#### New semantic elements (<header>, <footer>, <section>, <article>).
#### Native support for audio and video.
#### Form enhancements (<input type="email">, <input type="date">).
#### Geolocation API.
#### Web Storage API (localStorage, sessionStorage).
