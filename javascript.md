# JAVASCRIPT

## 1️⃣ JavaScript Basics (Must-Know)

### Q. What is JavaScript? Is it interpreted or compiled?What is JavaScript? Is it interpreted or compiled?

**Answer:**

JavaScript is a high-level, dynamically typed scripting language used for web development. While it was traditionally interpreted, modern JavaScript engines use Just-In-Time compilation, making it both interpreted and compiled at runtime for better performance.

### Q. Difference between var, let, and const

**Answer:**

var is function-scoped and hoisted with initialization, while let and const are block-scoped, hoisted into the Temporal Dead Zone, and safer to use. const prevents reassignment.

### Q. What is the Temporal Dead Zone?

**Answer:**

The Temporal Dead Zone is the phase during execution where let and const variables are hoisted but not yet initialized, and accessing them results in a ReferenceError.

### Q. What are primitive and non-primitive data types?

**Answer:**

Primitive data types store immutable values and are compared by value, while non-primitive data types store references to mutable objects and are compared by reference.

### Q. Difference between mutable and immutable

**Answer:**

Mutable values can be changed after creation, while immutable values cannot; any modification to an immutable value creates a new instance.

### Q. Difference between == and ===

**Answer:**

== checks equality after type coercion, whereas === checks equality without type coercion by comparing both value and type.

### Q. What is type coercion?

**Answer:**

Type coercion is JavaScript’s automatic or manual conversion of values between data types during operations and comparisons.

### Q. What is NaN? How do you check if a value is NaN?

**Answer:**

NaN is a special numeric value representing an invalid mathematical result, and the correct way to check for it is Number.isNaN().

### Q. Difference between null and undefined

**Answer:**

undefined means a variable has been declared but not assigned a value, while null is an explicitly assigned value representing intentional absence.

### Q. What is hoisting?

**Answer:**

Hoisting is JavaScript’s behavior of moving declarations to the top of their scope during compilation, allowing variables and functions to be accessed before their declaration in code.

### Q. What is strict mode ("use strict")?

**Answer:**

Strict mode is a JavaScript feature that enforces stricter syntax and runtime checks, preventing common bugs and making code more secure and predictable.

### Q. What is the difference between alert, prompt, and confirm?

**Answer:**

alert shows a message, prompt collects user input, and confirm asks for user confirmation, all using blocking browser dialogs.

### Q. What are template literals?

**Answer:**

Template literals are ES6 string literals enclosed in backticks (`) that support string interpolation (${}), multi-line strings, and expression embedding.

### Q. What is the typeof operator?

**Answer:**

typeof is a unary operator that returns a string indicating the data type of a value (e.g., "string", "number", "undefined", "object", "function").

### Q. What are falsy values in JavaScript?

**Answer:**

Values that evaluate to false in a Boolean context:
false, 0, -0, 0n, "", null, undefined, NaN.

### Q. Difference between isNaN() and Number.isNaN()

**Answer:**

isNaN() performs type coercion before checking.

Number.isNaN() checks without type coercion and is more reliable.

### Q. Explain parseInt() vs Number()

**Answer:**

parseInt() parses a string up to the first non-numeric character and can take a radix.

Number() converts the entire value to a number and returns NaN if conversion fails.

## 2️⃣ Functions & Scope

### Q. What is a function declaration vs function expression?

**Answer:**

Function declaration defines a named function and is fully hoisted.

Function expression assigns a function to a variable and is not hoisted as a function.

### Q. What is an arrow function?

**Answer:**

An arrow function is a concise ES6 function syntax that does not have its own this, arguments, or prototype.

### Q. Difference between arrow function and normal function

**Answer:**

Arrow functions have lexical this; normal functions have dynamic this.

Arrow functions cannot be used as constructors.

Arrow functions do not have arguments.

### Q. What is function hoisting?

**Answer:**

Function declarations are hoisted with their implementation, while function expressions are not hoisted as functions.

### Q. What is scope (global, function, block)?

**Answer:**

Global scope: Accessible everywhere

Function scope: Accessible only inside the function

Block scope: Accessible only within {} using let and const

### Q. What is lexical scope?

**Answer:**

Lexical scope means a function can access variables from its parent scope where it was defined, not where it is called.

### Q. What are default parameters?

**Answer:**

Default parameters allow function parameters to have default values if no argument or undefined is passed.

### Q. What is a callback function?

**Answer:**

A callback function is a function passed as an argument to another function and executed later.

### Q. What is a higher-order function?

**Answer:**

A higher-order function is a function that accepts another function as an argument or returns a function.

### Q. What is IIFE?

**Answer:**

An IIFE is a function that executes immediately after it is defined, commonly used to create private scope.

### Q. What is recursion?

**Answer:**

Recursion is a technique where a function calls itself until a base condition is met.

### Q. What is currying?

**Answer:**

Currying is the process of transforming a function with multiple arguments into a sequence of functions each taking one argument.

### Q. What is function overloading in JS?

**Answer:**

JavaScript does not support traditional function overloading; it is achieved by checking arguments length or types at runtime.

### Q. What is the arguments object?

**Answer:**

arguments is an array-like object available in normal functions that contains all passed arguments.

### Q. What is rest parameter (...args)?

**Answer:**

The rest parameter collects remaining function arguments into a real array, replacing the need for arguments.

## 3️⃣ Closures

### Q. What is a closure?

**Answer:**

A closure is a function that remembers and can access variables from its lexical scope even after the outer function has finished execution.

### Q. Why are closures useful?

**Answer:**

Closures enable state persistence, data encapsulation, and functional patterns without using global variables.

### Q. Real-world use cases of closures

**Answer:**

Data privacy / encapsulation

Event handlers

Callbacks and async operations

Function factories

Memoization

State management

### Q. How closures help in data hiding?

**Answer:**

Closures allow variables to remain private inside a function scope, accessible only through controlled inner functions.

### Q. Closure vs scope

**Answer:**

Scope: Where variables are defined and accessible

Closure: A function + its preserved lexical scope after execution

### Q. Example of closure in async code

**Answer:**

```js
function fetchData(id) {
  setTimeout(function () {
    console.log(id);
  }, 1000);
}
fetchData(10);
```

### Q. Memory implications of closures

**Answer:**

Closures retain references to outer variables, preventing garbage collection as long as the closure exists.

### Q. Can closures cause memory leaks?

**Answer:**

Yes — if closures unnecessarily retain large objects or DOM references, memory leaks can occur.

### Q. Difference between closure and lexical scope

**Answer:**

Lexical scope: Scope determined at write time

Closure: Runtime behavior that preserves lexical scope

### Q. Write a closure example

**Answer:**

```js
function counter() {
  let count = 0;
  return function () {
    count++;
    return count;
  };
}

const increment = counter();
increment(); // 1
increment(); // 2
```

## Objects & Prototypes

What is an object in JS?

Different ways to create objects

What is this keyword?

How does this work in arrow functions?

What is prototype?

Prototype vs **proto**

What is prototypal inheritance?

Difference between classical and prototypal inheritance

What is Object.create()?

What is hasOwnProperty()?

Difference between Object.freeze() and Object.seal()

How to clone an object?

Shallow copy vs deep copy

How does inheritance work in JS?

What is new keyword?

## 5️⃣ Arrays & Array Methods

Difference between map, filter, and reduce

Difference between forEach and map

What does reduce() do?

How to flatten an array?

Difference between slice and splice

Difference between find and filter

What is some() and every()?

Difference between push, pop, shift, unshift

How to remove duplicates from an array?

How to sort array of objects?

What is Array.from()?

What is flatMap()?

How to check if value is array?

How to merge arrays?

What is array destructuring?

## 6️⃣ Strings

Difference between slice, substring, and substr

How to reverse a string?

How to check palindrome?

How to count occurrences of characters?

Difference between replace and replaceAll

What is string immutability?

What is split()?

Template literals vs string concatenation

How to capitalize first letter?

How to remove spaces from string?

## 7️⃣ Asynchronous JavaScript

What is asynchronous JavaScript?

What is callback hell?

What are Promises?

Promise states

Difference between then() and async/await

How does async/await work internally?

What is Promise.all()?

Difference between Promise.all, allSettled, race, any

What is event loop?

Microtask queue vs macrotask queue

What is setTimeout?

What is setInterval?

How to cancel a promise?

Error handling in async/await

What happens when promise rejects?

## 8️⃣ Execution Context & Internals ⭐

What is execution context?

Phases of execution context

What is call stack?

What is memory heap?

What is event loop?

How JS handles single-threading?

What is temporal dead zone?

What is garbage collection?

How JS handles async operations?

Difference between stack and heap

## 9️⃣ DOM & Browser APIs

What is DOM?

How to select elements in DOM?

Difference between innerHTML and innerText

What is event bubbling?

What is event capturing?

Event delegation

Difference between addEventListener and onclick

What is preventDefault()?

What is stopPropagation()?

What is dataset?

What is localStorage vs sessionStorage?

What are cookies?

How to manipulate styles in JS?

How to create elements dynamically?

What is requestAnimationFrame()?

## 🔟 ES6+ Features (Very Important)

What is ES6?

Let/const vs var

Arrow functions

Destructuring

Spread vs rest operator

Modules (import / export)

Default parameters

Optional chaining

Nullish coalescing

Classes in JS

Difference between CommonJS and ES Modules

Symbol datatype

BigInt

What is Object.entries()?

What is Object.values()?

## 1️⃣1️⃣ Error Handling

What is try...catch?

What is finally?

Custom errors

Difference between runtime and syntax errors

Error handling in promises

Global error handling

What is throw?

How to handle async errors?

What is stack trace?

Best practices for error handling

## 1️⃣2️⃣ Performance & Optimization

How to improve JS performance?

What is debouncing?

What is throttling?

Difference between debounce and throttle

Memory leaks in JS

How closures cause memory leaks?

Lazy loading

Code splitting

Minification & tree shaking

Web Workers

## 1️⃣3️⃣ Security (Frontend Focus)

What is XSS?

What is CSRF?

How to prevent XSS in JS?

What is CORS?

Same-origin policy

How cookies are secured?

What is Content Security Policy?

Secure localStorage usage

JWT vs sessions

Why not store sensitive data in localStorage?

## 1️⃣4️⃣ Coding Questions (Common)

Reverse a string

Check palindrome

Flatten nested array

Remove duplicates from array

Find max/min in array

Debounce function implementation

Throttle function implementation

Deep clone object

Implement Promise.all

Implement once() function

## 1️⃣5️⃣ Tricky Output-Based Questions ⭐

Output of console.log(typeof null)

Output of [] == []

Output of 0 == false

Output of setTimeout inside loop

Output of closure inside loop

Output of this in different contexts

Hoisting output questions

Promise output order

Event loop output questions

Temporal dead zone examples

### Q.

**Answer:**

### Q. What is Event Delegation?

**Answer:**  
Event delegation is a technique where a single event listener is attached to a parent element to handle events for its child elements using event bubbling.

```js
document.querySelector("ul").addEventListener("click", (e) => {
  if (e.target.tagName === "LI") {
    console.log(e.target.textContent);
  }
});
```
