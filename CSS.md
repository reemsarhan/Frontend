# CSS
### What is the difference between relative, absolute, fixed, and sticky positioning in CSS?
Position Type	Description
relative	Positioned relative to its normal position.
absolute	Positioned relative to the nearest positioned ancestor.
fixed	Positioned relative to the viewport (doesn't move on scroll).
sticky	Behaves like relative until a certain scroll position, then becomes fixed.

### What is the difference between em, rem, px, %, and vh/vw in CSS?
Unit	Description
px	Fixed pixel size.
em	Relative to the font size of its parent.
rem	Relative to the root (html) font size.
%	Relative to its parent's size.
vh	Percentage of the viewport height.
vw	Percentage of the viewport width.

| Feature     | Box Model                          | Flexbox                                              |
|-------------|------------------------------------|------------------------------------------------------|
| Purpose     | Handles spacing within an element  | Handles layout of multiple elements in a container   |
| Focus       | Margin, border, padding, content   | Alignment, direction, spacing between items          |
| Use Case    | Spacing for a single element       | Arranging multiple items inside a container          |
| CSS Example | `margin`, `padding`, `border`      | `display: flex`, `justify-content`, `align-items`    |


### Box Model
```
+---------------------------+
|        margin             |
|  +---------------------+  |
|  |      border         |  |
|  |  +---------------+  |  |
|  |  |   padding     |  |  |
|  |  |  +---------+  |  |  |
|  |  |  | content |  |  |  |
|  |  |  +---------+  |  |  |
|  |  +---------------+  |  |
|  +---------------------+  |
+---------------------------+
```

### What is Flexbox and how does it work?
Flexbox is a layout model that allows items to align efficiently inside a container.
It is used for one-dimensional layouts (either row or column).
```
.flex-container {
    display: flex;
    justify-content: space-between; /* Distributes items evenly */
    align-items: center; /* Aligns items vertically */
}
```
Main Flexbox Properties:
Property	Description
display: flex;	Enables Flexbox.
flex-direction	Defines direction (row or column).
justify-content	Aligns items horizontally.
align-items	Aligns items vertically.

### What is CSS Grid and how is it different from Flexbox?
CSS Grid is a two-dimensional layout system that allows precise control over both rows and columns.
Flexbox, on the other hand, works in one direction (either row or column).
```
.grid-container {
    display: grid;
    grid-template-columns: repeat(3, 1fr); /* 3 equal columns */
    gap: 10px;
}
```
Feature	Flexbox	CSS Grid
Layout	One-dimensional	Two-dimensional
Best for	Simple layouts	Complex layouts
Example	Navbar, buttons	Full-page layout

### CSS selectors 
1. Universal Selector (*)
📌 Selects all elements on a page.
```
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```
2. Element (Type) Selector
📌 Targets all elements of a specific type (e.g., p, h1, div).
```
p {
    color: blue;
}
```
🔹 Styles all <p> elements with blue text.
3. Class Selector (.)
📌 Targets elements with a specific class.
```
.text-red {
    color: red;
}
<p class="text-red">This text is red.</p>
```
4. ID Selector (#)
📌 Selects a single unique element by ID.
```
#main-title {
    font-size: 24px;
}

<h1 id="main-title">Hello World</h1>
```
⚠ IDs should be unique on a page.
5. Grouping Selector (A, B, C)
📌 Applies styles to multiple selectors at once.
```
h1, h2, h3 {
    font-family: Arial, sans-serif;
}
```
6. Descendant Selector (A B)
📌 Selects elements inside another element.
```
div p {
    color: green;
}
```
🔹 Styles <p> elements inside <div>, but not standalone <p>.
7. Child Selector (A > B)
📌 Selects direct children only.
```
div > p {
    color: purple;
}
```
🔹 Only selects <p> that are direct children of <div>.
8. Adjacent Sibling Selector (A + B)
📌 Selects the next immediate sibling.
```
h1 + p {
    color: orange;
}
```
🔹 Only styles the first <p> after <h1>.
9. General Sibling Selector (A ~ B)
📌 Selects all siblings after a specific element.
```
h1 ~ p {
    color: pink;
}
```
🔹 Styles all <p> after <h1>.
10. Attribute Selector ([attr])
📌 Selects elements based on attributes.
```
input[type="text"] {
    border: 2px solid blue;
}
```
🔹 Targets all text <input> fields.
11. Pseudo-classes (:state)
📌 Targets elements based on state.
```
button:hover {
    background-color: yellow;
}
p:first-child {
    font-weight: bold;
}
````
12. Pseudo-elements (::element)
📌 Targets specific parts of an element.
```
p::first-letter {
    font-size: 2em;
    color: red;
}
h1::before {
    content: "🔥 ";
}
h1::after {
    content: " 🎉";
}
```
13. nth-child() Selector
📌 Targets elements based on order.
```
tr:nth-child(even) {
    background-color: lightgray;
} 
p:nth-child(3) {
    color: blue;
}
```
### What is the difference between visibility: hidden; and display: none;?
Property	Effect
visibility: hidden;	Element is hidden but still takes up space.
display: none;	Element is removed from the document flow and does not take up space.

### What are media queries and how are they used?
Media queries allow responsive designs by applying styles based on screen size.
```
@media (max-width: 768px) {
    body {
        background-color: lightblue;
    }
}
```
✅ Breakpoints for responsive design:
Device	Width
Mobile	< 600px
Tablet	600px - 1024px
Desktop	> 1024px


### What is the difference between inline, internal, and external CSS?
Type	Usage
Inline CSS	style="color: red;" (applied directly to elements)
Internal CSS	Inside <style> in the <head> section
External CSS	Linked using <link rel="stylesheet" href="style.css">

<!-- Inline CSS -->
<p style="color: red;">Hello</p>

<!-- Internal CSS -->
<style>
    p { color: blue; }
</style>

<!-- External CSS -->
<link rel="stylesheet" href="style.css">
✅ Best Practice: Use external CSS for maintainability.

### How can you create an animation using CSS?
Use @keyframes to define an animation and animation property to apply it.
```
@keyframes slide {
    0% { transform: translateX(0); }
    100% { transform: translateX(100px); }
}

.box {
    width: 50px;
    height: 50px;
    background: red;
    animation: slide 2s infinite alternate;
}
```
✅ Properties:

animation-duration: How long the animation runs.

animation-delay: When the animation starts.

animation-iteration-count: Number of times it repeats.

### What is the difference between nth-child() and nth-of-type()?
Selector	Description
nth-child(n)	Selects the nth child of any type.
nth-of-type(n)	Selects the nth occurrence of a specific type.
```
p:nth-child(2) { color: red; } /* Selects the second child, regardless of type */
p:nth-of-type(2) { color: blue; } /* Selects the second `<p>` only */
```


##  CSS Viewport Units
CSS provides viewport-relative units to make layouts responsive:


Unit	Description	Example
vw	1% of the viewport width	width: 50vw = 50% of screen width
vh	1% of the viewport height	height: 100vh = full screen height
vmin	1% of the smaller of vw or vh	Adapts to smallest side
vmax	1% of the larger of vw or vh	Adapts to largest side

### example
```
.fullscreen {
  width: 100vw;
  height: 100vh;
  background-color: lightblue;
}
```
