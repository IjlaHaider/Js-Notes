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
8. Promises
- A Promise is an object that represents the eventual completion (or failure) of an asynchronous operation.
- Think of it like a "container for a future value".
- It helps manage async code in a cleaner, structured way instead of relying on callbacks (which led to "callback hell").

<b>Syntax:</b>
```javascript
let promise = new Promise((resolve, reject) => {
    // async operation
    if (success) {
        resolve("Operation successful");
    } else {
        reject("Something went wrong");
    }
});
```

### States
1) Pending → Initial state, operation not completed.
2) Fulfilled → The operation completed successfully (resolve() called).
3) Rejected → The operation failed (reject() called).

### Why Promises?
- Solve callback hell (nested callbacks).
- Provide a chainable way to handle multiple async tasks.
- Improve readability and error handling.

### Consuming Promises
We consume promises using .then(), .catch(), and .finally():
```javascript
promise.then(result => console.log("Fulfilled:", result))  // runs if resolved
  .catch(error => console.error("Rejected:", error))  // runs if rejected
  .finally(() => console.log("Always runs"));        // runs no matter what
```

### :pushpin: Promise Chaining
- Each .then() returns a new promise. The returned promise gets resolved with the return value of the callback inside .then(). This allows sequential execution of async tasks.
- If any .then() throws an error, the chain jumps to the nearest .catch().
- If you return another Promise inside .then(), the chain will wait until that promise settles.

#### Example:
```javascript
new Promise((resolve, reject) => {
    setTimeout(() => resolve(10), 1000);
})
.then(result => {
    console.log("Step 1:", result);
    return result * 2;
})
.then(result => {
    console.log("Step 2:", result);
    return result * 3;
})
.then(result => {
    console.log("Step 3:", result);
});

// Output:
Step 1: 10
Step 2: 20
Step 3: 60
```

### Promise concurrency (4 static methods)
The Promise class offers four static methods to facilitate async task concurrency. All these methods take an iterable of promises and return a new promise.
 
| Promise Method | Behavior Summary | Resolves When | Rejects When | Return Type |
|----------------|------------------|----------------|----------------|--------------|
| **Promise.all()** | :arrow_right: Waits for **all promises** to succeed in sequence (order of definition, not timing). | All promises **fulfilled** | Any one **rejects** | :white_check_mark: `Array` of resolved values <br>e.g., `[1, "Hello"]` |
| **Promise.allSettled()** | :arrow_right: Waits for **all promises to settle** (fulfilled or rejected). <br>Never rejects overall. | When all **settle** | :x: Never | :receipt: `Array` of result objects → `{status, value/reason}` |
| **Promise.race()** | :arrow_right: Returns result of **first settled** promise (fulfilled or rejected). <br>:zap: For `setTimeout()`, the one with **lower delay** wins. | First **fulfilled or rejected** | Same (if first rejects) | :dart: Single value/reason <br>e.g., `"Fast!"` |
| **Promise.any()** | :arrow_right: Returns **first fulfilled** promise (ignores rejections). <br>:zap: Behaves like `.race()` for timing but **ignores early rejects**. | First **fulfilled** | All **reject** → throws `AggregateError` | :dart: Single fulfilled value <br>e.g., `"Success!"` |
| **Edge Cases** | `Promise.race([])` → :hourglass_flowing_sand: *Never resolves/rejects* <br>`Promise.any([])` → :x: *Throws AggregateError* | — | — | — |
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
