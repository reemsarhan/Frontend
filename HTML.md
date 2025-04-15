# HTML Interview Questions

###  What is HTML?
**Answer:**  
HTML (HyperText Markup Language) is the standard language used to create and design web pages. It defines the structure of a webpage using elements such as headings, paragraphs, links, images, and forms.

###  What are HTML tags and attributes?
**Answer:**  
- **Tags:** HTML tags are the building blocks of an HTML page, enclosed in angle brackets (`< >`). Example: `<p>`, `<a>`, `<div>`.
- **Attributes:** Attributes provide additional information about an element and are always defined in the opening tag. Example: `<a href="https://example.com">Click here</a>`.

###  What is the difference between HTML and XHTML?
**Answer:**  
- **HTML** is more flexible and does not require strict syntax.
- **XHTML** (Extensible HTML) follows stricter rules, such as properly nesting elements and always closing tags.

###  What is the difference between `<div>` and `<span>`?
**Answer:**  
- `<div>` is a block-level element used to group larger sections of HTML.
- `<span>` is an inline element used to style or manipulate specific portions of text inside a block.

###  What is semantic HTML?
Semantic HTML uses meaningful tags that describe their purpose, such as `<header>`, `<article>`, `<section>`, and `<footer>`, improving accessibility and SEO.


###  What is the difference between inline, block, and inline-block elements?
**Answer:**  
- **Block elements:** Take up the full width available (e.g., `<div>`, `<p>`, `<h1>`).
- **Inline elements:** Take up only as much width as needed (e.g., `<span>`, `<a>`, `<strong>`).
- **Inline-block elements:** Behave like inline elements but allow height and width adjustments.

### 7. What is the difference between id and class attributes?
**Answer:**  
- **id** is unique and can be applied to a single element (`id="header"`).
- **class** can be used on multiple elements (`class="button"`).

### 8. What are the different types of lists in HTML?
**Answer:**  
- **Ordered List (`<ol>`):** Numbered items.
- **Unordered List (`<ul>`):** Bulleted items.
- **Definition List (`<dl>`):** A set of terms (`<dt>`) and definitions (`<dd>`).

### 9. What is the difference between absolute, relative, and fixed paths in HTML?
**Answer:**  
- **Absolute Path:** Specifies the full URL (`https://example.com/images/logo.png`).
- **Relative Path:** Refers to a location relative to the current document (`./images/logo.png`).
- **Fixed Path:** Typically starts from the root directory (`/images/logo.png`).

### 10. What is the alt attribute in an `<img>` tag?
**Answer:**  
The `alt` attribute provides alternative text for an image if it fails to load, improving accessibility.

---

## Advanced HTML Questions

### 11. What is the difference between `<iframe>` and `<frame>`?
**Answer:**  
- `<iframe>`: Embeds another webpage within the current page.
- `<frame>`: Used in `<frameset>`, which is deprecated in HTML5.

### 12. What is the use of the `<meta>` tag?
**Answer:**  
The `<meta>` tag provides metadata about the HTML document, such as:
```html
<meta charset="UTF-8">
<meta name="description" content="HTML Interview Questions">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
