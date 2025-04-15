# JavaScript Overview

JavaScript is a high-level, interpreted, object-oriented programming language used mainly to create interactive web pages. It runs in the browser and makes websites dynamic, responding to user actions.

## 1. Primitive Data Types
These hold single values and are immutable (can't be changed).

| Type        | Description                              | Example                          |
|-------------|------------------------------------------|----------------------------------|
| String      | Text                                     | `"Hello"` or `'Hi'`             |
| Number      | Integers and floats                      | `42`, `3.14`                    |
| Boolean     | True or false                            | `true`, `false`                 |
| Null        | Intentional empty value                  | `null`                           |
| Undefined   | Variable declared but not assigned       | `let x; // x is undefined`       |
| BigInt      | Very large integers                      | `12345678901234567890n`         |
| Symbol      | Unique, immutable value (used as object keys) | `Symbol("id")`            |

## 2. Non-Primitive (Reference) Data Types
These can hold collections of values or more complex data.

| Type        | Description                              | Example                         |
|-------------|------------------------------------------|---------------------------------|
| Object      | Key-value pairs                          | `{ name: "Reem", age: 25 }`     |
| Array       | Ordered list                             | `[1, 2, 3, 4]`                  |
| Function    | Callable object                          | `function greet() {}`           |
| Date, RegExp, etc. | Built-in objects               | `new Date()`, `/abc/`              |

## 3. var, let, const
| Type       | Function | Block  |
|------------|----------|------- |
| `var`      | ✓        | ✘     |
| `let`      | ✘        | ✓     |
| `const`    | ✘        | ✓     |

### Hoisting
Hoisting is JavaScript's behavior of moving declarations to the top of their scope before the code is executed. Variables and functions are "hoisted" (lifted) to the top of their scope (global or function), even if they’re written later in the code.

### Callback
A callback is a function passed as an argument to another function, which gets called later, usually after a task is completed.

---

## Functions in JavaScript

### 1. Function Declaration
This is when you declare a function using the `function` keyword with a name.

```javascript
function greet() {
  console.log("Hello, World!");
}
```
###  2. Function Expression
This is when you assign a function to a variable.

```javascript
const greet = function() {
  console.log("Hello, World!");
};
```

## Adding JavaScript to HTML
### 1-Inline JavaScript
You can add JS code directly inside an HTML element’s attribute (usually onclick, onmouseover, etc.).


 ```HTML
<button onclick="alert('Hello!')">Click me</button>
```
### 2-Internal JavaScript
Write JavaScript inside a <script> tag within your HTML file.
```
<script>
  console.log('Hello from internal JS!');
</script>
```
### 3-External JavaScript
Link to a separate .js file using the <script src="file.js"> tag.
 ```
<script src="script.js"></script>
```

### Closures in JavaScript
A closure is when a function remembers and accesses variables from its outer (lexical) scope, even after that outer function has finished executing.

```
function outer() {
  let count = 0;

  return function inner() {
    count++;
    console.log("Count is:", count);
  };
}

const counter = outer(); // outer runs and returns inner
counter(); // Count is: 1
counter(); // Count is: 2
counter(); // Count is: 3
```

## DOM (Document Object Model) Methods
To access HTML elements in JavaScript, you use DOM methods:

```
getElementById()
getElementsByClassName()
getElementsByTagName()
querySelector() (matching CSS selector)
querySelectorAll()
```

## Event Propagation
### Event Bubbling
Event bubbling is the default behavior in most cases. When an event is triggered on an element, it first triggers on the innermost element (the target), and then bubbles up to the parent elements in the DOM hierarchy.

Order of propagation:
Target element → Parent → Grandparent → ... → Root (<html>)

## Event Capturing
Event capturing (or trickling) is the opposite of event bubbling. Instead of starting from the target element, it starts from the root of the DOM and travels down to the target element.

Order of propagation:
Root (<html>) → Grandparent → Parent → Target element

To use event capturing, you need to explicitly set the third argument in addEventListener() to true.

## Event Delegation
Event delegation is a technique in JavaScript where you attach a single event listener to a parent element instead of adding multiple listeners to individual child elements. The event listener on the parent element listens for events on its child elements through event bubbling.

## Strict Mode
Strict mode is a way to opt in to a restricted version of JavaScript, which helps catch common coding mistakes and prevents certain behaviors that can lead to bugs or security vulnerabilities.

## call(), apply(), and bind()
These are methods of functions that allow you to explicitly set the value of this and invoke or create a new function with that this value.
```
call(): Invokes the function immediately, passing arguments one by one.
apply(): Same as call(), but arguments are passed as an array.
bind(): Does NOT invoke the function immediately; returns a new function with this bound permanently.
```

## Array Methods: forEach(), map(), and filter()
### forEach(): Loops through each item in the array. Does not return anything (just runs a function for each item).
[1, 2, 3].forEach(num => console.log(num));
### map(): Loops through the array and returns a new array with modified values.
const squares = [1, 2, 3].map(num => num * num);
console.log(squares); // [1, 4, 9]
### filter(): Loops through and returns a new array with only items that pass the condition.

```javascript
const evenNumbers = [1, 2, 3, 4].filter(num => num % 2 === 0);
console.log(evenNumbers); // [2, 4]
Working with Promises and async/await
```

### Using Promises
```
fetch('https://api.example.com/data')
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.log(err));
```
### Using async/await
```
async function getData() {
  try {
    const res = await fetch('https://api.example.com/data');
    const data = await res.json();
    console.log(data);
  } catch (err) {
    console.log(err);
  }
}
getData();
```
