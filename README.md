# JavaScript Notes

Comprehensive notes from **Basics to Advanced** in JavaScript. Perfect for interview prep, revision, and quick reference.

---

## 📌 Table of Contents

1. [Introduction](#introduction)
2. [Basics](#basics)

   * Variables
   * Data Types
   * Operators
3. [Control Flow](#control-flow)

   * Conditional Statements
   * Loops
4. [Functions](#functions)

   * Function Declarations & Expressions
   * Arrow Functions
   * Parameters & Arguments
   * Return Values
   * Scope & Closures
5. [Objects](#objects)

   * Object Literals
   * Methods
   * `this` Keyword
   * Object Destructuring
6. [Arrays](#arrays)

   * Array Methods
   * Iteration
7. [ES6+ Features](#es6-features)

   * Let & Const
   * Template Literals
   * Destructuring
   * Spread & Rest Operators
   * Modules (import/export)
8. [DOM Manipulation](#dom-manipulation)

   * Selecting Elements
   * Modifying Content & Styles
   * Event Listeners
9. [Asynchronous JavaScript](#asynchronous-javascript)

   * Callbacks
   * Promises
   * Async/Await
   * Fetch API
10. [Error Handling](#error-handling)

    * try...catch
    * Throwing Errors
11. [Object-Oriented JavaScript](#object-oriented-javascript)

    * Prototypes
    * Classes
    * Inheritance
12. [Advanced Topics](#advanced-topics)

    * Event Loop
    * Hoisting
    * Execution Context
    * Closures in Depth
    * `this` Binding
    * Currying
    * Debouncing & Throttling
13. [JavaScript in Browser](#javascript-in-browser)

    * LocalStorage & SessionStorage
    * Cookies
    * Web APIs
14. [JavaScript in Node.js](#javascript-in-nodejs)

    * NPM & Packages
    * CommonJS vs ES Modules
15. [Interview Prep Snippets](#interview-prep-snippets)

    * Common Patterns
    * Tricky Questions

---

## 🚀 Introduction

JavaScript is a **high-level, dynamic, interpreted programming language** primarily used for adding interactivity to web pages. It can run in the browser and on the server (Node.js).

```js
console.log("Hello, JavaScript!");
```

---

## 🟢 Basics

### Variables

* Declared using `var`, `let`, or `const`.
* `let` and `const` are block-scoped, `var` is function-scoped.

```js
var oldVar = "I am function scoped";
let modernVar = "I am block scoped";
const constantVar = "Cannot be reassigned";
```

### Data Types

* Primitive: String, Number, Boolean, Null, Undefined, Symbol, BigInt
* Non-Primitive: Objects, Arrays, Functions

```js
let name = "John"; // String
let age = 25;      // Number
let isLogged = true; // Boolean
let person = { name: "John", age: 25 }; // Object
```

### Operators

* Arithmetic: `+`, `-`, `*`, `/`, `%`
* Comparison: `==`, `===`, `!=`, `!==`, `<`, `>`
* Logical: `&&`, `||`, `!`

```js
console.log(5 === "5"); // false (strict equality)
```

---

## 🔁 Control Flow

### Conditional Statements

```js
if (age >= 18) {
  console.log("Adult");
} else {
  console.log("Minor");
}
```

### Loops

```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}

while (age < 30) {
  age++;
}
```

---

## ✨ Functions

```js
// Function Declaration
function greet(name) {
  return `Hello, ${name}`;
}

// Arrow Function
const greetArrow = (name) => `Hello, ${name}`;

console.log(greet("John"));
```

Closures example:

```js
function outer() {
  let count = 0;
  return function inner() {
    count++;
    return count;
  };
}

const counter = outer();
console.log(counter()); // 1
console.log(counter()); // 2
```

---

## 📦 Objects

```js
const car = {
  brand: "Toyota",
  start() {
    console.log("Car started");
  }
};

car.start();
```

---

## 📚 Arrays

```js
let numbers = [1, 2, 3, 4];
numbers.push(5);
numbers.map(num => num * 2);
```

---

## ⚡ ES6+ Features

```js
// Destructuring
const user = { name: "Ali", age: 22 };
const { name, age } = user;

// Spread Operator
let arr = [1, 2, 3];
let newArr = [...arr, 4, 5];
```

---

## 🌐 DOM Manipulation

```js
const heading = document.querySelector("h1");
heading.textContent = "Updated Title";

document.querySelector("button")
  .addEventListener("click", () => alert("Button clicked!"));
```

---

## ⏳ Asynchronous JavaScript

```js
// Promise
fetch("https://jsonplaceholder.typicode.com/posts")
  .then(res => res.json())
  .then(data => console.log(data));

// Async/Await
async function getData() {
  const res = await fetch("https://jsonplaceholder.typicode.com/posts");
  const data = await res.json();
  console.log(data);
}
getData();
```

---

## ⚠️ Error Handling

```js
try {
  throw new Error("Something went wrong");
} catch (error) {
  console.log(error.message);
}
```

---

## 🏗️ Object-Oriented JavaScript

```js
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks.`);
  }
}

const dog = new Dog("Rex");
dog.speak();
```

---

## 🎯 Advanced Topics

* **Event Loop**: Handles async operations using call stack, web APIs, callback queue.
* **Hoisting**: Variable/function declarations moved to top of scope.
* **Closures**: Inner function remembers outer function’s scope.
* **Currying**:

```js
const add = a => b => a + b;
console.log(add(2)(3)); // 5
```

---

## 🌍 JavaScript in Browser

```js
// Local Storage
localStorage.setItem("theme", "dark");
console.log(localStorage.getItem("theme"));
```

---

## 🖥️ JavaScript in Node.js

```js
// Import module
const fs = require("fs");
fs.writeFileSync("test.txt", "Hello Node");
```

---

## 💡 Interview Prep Snippets

```js
// Reverse a string
const reverse = str => str.split('').reverse().join('');

// Flatten array
const flatten = arr => arr.flat(Infinity);

// Debounce
function debounce(fn, delay) {
  let timeout;
  return (...args) => {
    clearTimeout(timeout);
    timeout = setTimeout(() => fn(...args), delay);
  };
}
```

---

## 📖 Resources

* [MDN JavaScript Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
* [JavaScript.info](https://javascript.info/)
* [Node.js Docs](https://nodejs.org/en/docs/)

---

✅ **Ready to use on GitHub!**
