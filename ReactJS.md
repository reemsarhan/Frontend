# React

### What is React?
React is an open-source JavaScript library for building user interfaces, especially single-page applications (SPAs). It is component-based, declarative, and efficiently updates the UI using a virtual DOM.
```
function Hello() {
  return <h1>Hello, React!</h1>;
}
```
### What are Components in React?
Components are reusable, independent UI pieces in React. There are two types:
Class Components (older, stateful)
Functional Components (modern, hooks-based)
```
function Welcome(props) {
  return <h1>Hello, {props.name}!</h1>;
}
```
### What is JSX in React?
JSX (JavaScript XML) is a syntax extension that allows writing HTML inside JavaScript.
```
const element = <h1>Hello, World!</h1>;
```
#### Babel	Transforms syntax (e.g. JSX → JS)
JSX gets compiled into JavaScript
```
React.createElement("h1", null, "Hello, World!");
```
### What is Props in React?
Props (short for "properties") are read-only values passed from a parent component to a child.
```
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

function App() {
  return <Greeting name="Alice" />;
}
```
### What is the Virtual DOM in React?
The Virtual DOM is a lightweight JavaScript representation of the real DOM. React updates the Virtual DOM first, then efficiently updates only the changed parts in the real DOM.

## 🧠 What is Reconciliation?
**Reconciliation** is the process React uses to **compare the Virtual DOM with a previous version** and **update the Real DOM** in the most efficient way.
React uses a **diffing algorithm** to find what has changed and applies only the minimal set of changes to the Real DOM.


### What is the difference between Controlled and Uncontrolled Components?
Feature	Controlled Component	Uncontrolled Component
State Management	State is managed by React (useState)	State is managed by the DOM (ref)
Example	<input value={state} onChange={setState} />	<input ref={inputRef} />
✅ Example of Controlled Component:
```
function ControlledInput() {
  const [value, setValue] = useState("");
  return <input value={value} onChange={(e) => setValue(e.target.value)} />;
}
```
✅ Example of Uncontrolled Component:
```
import { useRef } from "react";

function UncontrolledInput() {
  const inputRef = useRef();
  return <input ref={inputRef} />;
}
 ```
 
### What is React Router?
React Router is a library for handling navigation in React applications.

```
import { BrowserRouter, Routes, Route } from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

##  5 types of React hooks
React Hooks are functions that allow functional components to use state and lifecycle methods.
### 🧠 State Hooks – useState, useReducer
```
// useState Example
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  return (
    <button onClick={() => setCount(count + 1)}>
      Count: {count}
    </button>
  );
}
```
```
Edit
// useReducer Example
import React, { useReducer } from 'react';
function reducer(state, action) {
  switch (action.type) {
    case 'increment': return { count: state.count + 1 };
    case 'decrement': return { count: state.count - 1 };
    default: return state;
  }
}
function Counter() {
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <>
      <p>{state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
    </>
  );
}
```
### 🌐 Context Hook – useContext
To avoid prop drilling.
```
import React, { useContext, createContext } from 'react';

const ThemeContext = createContext('light');

function ThemedComponent() {
  const theme = useContext(ThemeContext);
  return <div>Current theme: {theme}</div>;
}

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <ThemedComponent />
    </ThemeContext.Provider>
  );
}
```
### 📌 Ref Hook – useRef
```
import React, { useRef } from 'react';

function FocusInput() {
  const inputRef = useRef();

  const handleFocus = () => {
    inputRef.current.focus();
  };

  return (
    <>
      <input ref={inputRef} type="text" />
      <button onClick={handleFocus}>Focus Input</button>
    </>
  );
}
```
###  🌊 Effect Hook – useEffect
``` 
import React, { useState, useEffect } from 'react';

function Timer() {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setSeconds(s => s + 1);
    }, 1000);
    return () => clearInterval(interval); // cleanup
  }, []);

  return <p>Seconds: {seconds}</p>;
}
```
### 🚀 Performance Hooks – useMemo, useCallback  (can be removed after appearnce of React Compiler)
```
// useMemo Example
import React, { useMemo, useState } from 'react';

function ExpensiveCalculation({ num }) {
  const result = useMemo(() => {
    console.log("Calculating...");
    return num * 2;
  }, [num]);

  return <p>Result: {result}</p>;
}

```
```
// useCallback Example
import React, { useCallback, useState } from 'react';

function Button({ handleClick }) {
  return <button onClick={handleClick}>Click Me</button>;
}

function Parent() {
  const [count, setCount] = useState(0);

  const memoizedCallback = useCallback(() => {
    console.log("Clicked!");
  }, []);

  return (
    <>
      <p>Count: {count}</p>
      <Button handleClick={memoizedCallback} />
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </>
  );
}

```

## axios
is a popular JavaScript library used to make HTTP requests (GET, POST, PUT, DELETE, etc.) from the browser or Node.js.
In React, it's often used to fetch data from APIs
```
import axios from 'axios';
axios.get('https://api.example.com/data')
  .then(response => console.log(response.data))
  .catch(error => console.error(error));
```


## Redux 
is a predictable state container for JavaScript applications, commonly used with frameworks like React. 
It provides a centralized way to manage and update the state of your application in a consistent and structured manner.

``` 
import { createStore } from 'redux';

// Initial state
const initialState = {
  count: 0
};

// Reducer function
function counterReducer(state = initialState, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

// Create store
const store = createStore(counterReducer);

export default store;

```

## What is the React Compiler?
The React Compiler is an upcoming tool (still experimental) that automatically optimizes your React code — without you needing to do anything manually.

Think of it as: A smart engine that rewrites your components behind the scenes to make them faster and more efficient.

  What does it help with?
Here’s what the React Compiler is designed to do:

### 1. Automatic Memoization
It figures out which parts of your components depend on what props/state.

Then it skips re-rendering parts of your component tree that didn’t change.

You no longer need to use React.memo, useMemo, or useCallback yourself.
   Imagine not needing useCallback at all — and still getting the same performance wins.

### 2. Avoiding Unnecessary Re-renders
It tracks dependencies like a compiler would in a functional language.

It only re-renders parts of the UI when their actual inputs (props/state) change.

This helps with:
Better runtime performance
Less boilerplate
Fewer bugs from misused memoization

### 3. Smarter Optimization
Since it's built with a deep understanding of how React works, the compiler can optimize your code in ways manual tuning can’t — kind of like what a compiler does for C/C++ code.

 
