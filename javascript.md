# JAVASCRIPT

## JavaScript Basics (Must-Know)

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

## Functions & Scope

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

## Closures

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

### What is an object in JavaScript?

**Answer:**

An object in JavaScript is a collection of key–value pairs used to store related data and behavior.

Explanation:

- Keys are strings (or symbols)
- Values can be any data type, including functions (methods)
- Objects represent real-world entities

Example:

```js
var user = {
  name: "Tanmay",
  age: 25,
  greet: function () {
    return "Hello";
  },
};
```

### Different ways to create objects

**Answer:**

1. Object literal (most common)

```js
var obj = { a: 1 };
```

2. Using new Object()

```js
var obj = new Object();
obj.a = 1;
```

3. Constructor function

```js
function User(name) {
  this.name = name;
}
var u1 = new User("Tanmay");
```

4. Object.create()

```js
var proto = { greet: "hi" };
var obj = Object.create(proto);
```

5. ES6 Class (syntactic sugar)

```js
class User {
  constructor(name) {
    this.name = name;
  }
}
```

### What is this keyword?

**Answer:**

this refers to the object that is currently calling the function.

Explanation (depends on how function is called):

- Method call → object
- Function call → window (non-strict) / undefined (strict)
- Constructor → newly created object

Example:

```js
var obj = {
  name: "JS",
  getName: function () {
    return this.name;
  },
};
```

### How does this work in arrow functions?

**Answer:**

Arrow functions do not have their own this.

They inherit this from their lexical scope.

Example:

```js
var obj = {
  name: "JS",
  arrow: () => this.name,
  normal: function () {
    return this.name;
  },
};
```

👉 arrow() → undefined

👉 normal() → "JS"

Key point for interview:

Arrow functions are best for callbacks, not object methods.

### What is prototype?

**Answer:**

Prototype is an object from which other objects inherit properties.

Explanation:

- Every JavaScript object has a hidden reference to another object (prototype)
- If a property is not found, JS looks up the prototype chain

### Prototype vs **proto**

**Answer:**

| Prototype                     | `__proto__`                       |
| ----------------------------- | --------------------------------- |
| Exists on constructor         | Exists on instance                |
| Used to define shared methods | Points to constructor’s prototype |
| `Func.prototype`              | `obj.__proto__`                   |

Example:

```js
function User() {}
var u = new User();

User.prototype === u.**proto** // true
```

### What is prototypal inheritance?

**Answer:**

Prototypal inheritance is a mechanism where objects inherit directly from other objects.

Explanation:

Instead of classes, JavaScript uses objects inheriting from objects.

```js
var parent = { role: "admin" };
var child = Object.create(parent);
```

### Classical vs Prototypal inheritance

**Answer:**

| Classical         | Prototypal         |
| ----------------- | ------------------ |
| Class-based       | Object-based       |
| Used in Java, C++ | Used in JavaScript |
| Rigid hierarchy   | Flexible           |
| Requires classes  | No classes needed  |

### What is Object.create()?

**Answer:**

Creates a new object with the specified object as its prototype.

```js
var parent = { greet: "hi" };
var child = Object.create(parent);
```

Use case:

When you want pure inheritance without constructor functions.

### What is hasOwnProperty()?

**Answer:**

Checks if a property belongs directly to the object, not inherited.

```js
obj.hasOwnProperty("name");
```

Why important:

Avoid accessing prototype properties unintentionally.

### Difference between Object.freeze() and Object.seal()

**Answer:**

| Feature         | freeze | seal |
| --------------- | ------ | ---- |
| Add property    | ❌     | ❌   |
| Delete property | ❌     | ❌   |
| Modify value    | ❌     | ✅   |
| Fully immutable | ✅     | ❌   |

### How to clone an object?

**Answer:**

Shallow copy

```js
var copy = Object.assign({}, obj);
// OR
var copy = { ...obj };
```

Deep copy

```
var deep = JSON.parse(JSON.stringify(obj));
```

⚠️ JSON method fails for functions, dates, undefined.

### Shallow copy vs Deep copy

**Answer:**

| Shallow               | Deep              |
| --------------------- | ----------------- |
| Copies reference      | Copies value      |
| Nested objects shared | Fully independent |
| Faster                | Slower            |

### How does inheritance work in JavaScript?

**Answer:**

Inheritance works via prototype chain lookup.

Flow:

```js
Object → Prototype → Prototype → null
```

If property not found → search continues up the chain.

### What is new keyword?

**Answer:**

new creates an instance from a constructor function.

What happens internally:

- Creates empty object
- Sets prototype
- Binds this
- Returns object

```js
function User(name) {
  this.name = name;
}

var u = new User("Tanmay");
```

## Arrays & Array Methods

### Difference between `map`, `filter`, and `reduce`

**Answer:**

| Method     | Purpose                            | Returns   |
| ---------- | ---------------------------------- | --------- |
| `map()`    | Transform each element             | New array |
| `filter()` | Select elements based on condition | New array |
| `reduce()` | Reduce array to a single value     | Any value |

```js
arr.map((x) => x * 2);
arr.filter((x) => x > 10);
arr.reduce((sum, x) => sum + x, 0);
```

### Difference between forEach and map

**Answer:**

| forEach                  | map                     |
| ------------------------ | ----------------------- |
| Used for side effects    | Used for transformation |
| Does not return anything | Returns a new array     |
| Cannot be chained        | Can be chained          |

```js
arr.forEach((x) => console.log(x));
var doubled = arr.map((x) => x * 2);
```

### What does reduce() do?

**Answer:**

reduce() executes a reducer function on each element and returns a single accumulated value.

```js
var sum = [1, 2, 3].reduce((acc, val) => acc + val, 0);
```

Common use cases:

- Sum / product
- Grouping data
- Flatten arrays
- Creating objects from arrays

### How to flatten an array?

**Answer:**

Using flat()

```js
var arr = [1, [2, [3]]];
arr.flat(2);
```

Using reduce()

```js
arr.reduce((acc, val) => acc.concat(val), []);
```

### Difference between slice and splice

**Answer:**

| slice             | splice                   |
| ----------------- | ------------------------ |
| Non-mutating      | Mutates original array   |
| Extracts elements | Adds / removes elements  |
| Returns new array | Returns removed elements |

```js
arr.slice(1, 3);
arr.splice(1, 2);
```

### Difference between find and filter

**Answer:**

| find                 | filter                |
| -------------------- | --------------------- |
| Returns first match  | Returns all matches   |
| Returns single value | Returns array         |
| Stops once found     | Iterates entire array |

```js
arr.find((x) => x > 10);
arr.filter((x) => x > 10);
```

### What is some() and every()?

**Answer:**

- some() → returns true if at least one element matches
- every() → returns true if all elements match

```js
arr.some((x) => x > 5);
arr.every((x) => x > 0);
```

### Difference between push, pop, shift, unshift

**Answer:**

| Method  | Action | Position |
| ------- | ------ | -------- |
| push    | Add    | End      |
| pop     | Remove | End      |
| unshift | Add    | Start    |
| shift   | Remove | Start    |

```js
arr.push(4);
arr.pop();
arr.unshift(1);
arr.shift();
```

### How to remove duplicates from an array?

**Answer:**

Using Set

```js
var unique = [...new Set(arr)];
```

Using filter

```js
arr.filter((v, i, a) => a.indexOf(v) === i);
```

### How to sort array of objects?

**Answer:**

```js
users.sort((a, b) => a.age - b.age);
```

String sort

```js
users.sort((a, b) => a.name.localeCompare(b.name));
```

### What is Array.from()?

**Answer:**

Creates a new array from:

- Array-like objects
- Iterables (Set, Map, string)

```js
Array.from("hello");
Array.from(new Set([1, 2, 2]));
```

### What is flatMap()?

**Answer:**

flatMap() maps and flattens one level deep in a single operation.

```js
arr.flatMap((x) => [x, x * 2]);
```

Equivalent to:

```js
arr.map().flat(1);
```

### How to check if value is an array?

**Answer:**

```js
Array.isArray(value);
```

✔ Recommended over typeof

### How to merge arrays?

**Answer:**

```js
    Using spread operator
    var merged = [...arr1, ...arr2];
```

Using concat

```js
var merged = arr1.concat(arr2);
```

### What is array destructuring?

**Answer:**

Array destructuring allows extracting values into variables.

```js
var [a, b] = [1, 2];
```

Skipping values

```js
var [, , third] = [1, 2, 3];
```

Default values

```js
var [a = 10] = [];
```

## Strings

### Q. Difference between `slice`, `substring`, and `substr`

**Answer:**

| Method                  | Parameters    | Supports negative index | Description                           |
| ----------------------- | ------------- | ----------------------- | ------------------------------------- |
| `slice(start, end)`     | start, end    | ✅ Yes                  | Extracts part of a string             |
| `substring(start, end)` | start, end    | ❌ No                   | Negative values treated as `0`        |
| `substr(start, length)` | start, length | ✅ Yes                  | Extracts based on length (deprecated) |

```js
var str = "JavaScript";

str.slice(4, 10); // "Script"
str.substring(4, 10); // "Script"
str.substr(4, 6); // "Script"
```

⚠️ substr() is deprecated and should be avoided.

### Q. How to reverse a string?

**Answer:**

```js
var reversed = str.split("").reverse().join("");
```

### Q. How to check palindrome?

**Answer:**

A palindrome reads the same forward and backward.

```js
function isPalindrome(str) {
  var cleaned = str.toLowerCase().replace(/[^a-z0-9]/g, "");
  return cleaned === cleaned.split("").reverse().join("");
}
```

### Q. How to count occurrences of characters?

**Answer:**

```js
function countChars(str) {
  var count = {};
  for (var char of str) {
    count[char] = (count[char] || 0) + 1;
  }
  return count;
}
```

### Q. Difference between replace and replaceAll

**Answer:**

| replace              | replaceAll              |
| -------------------- | ----------------------- |
| Replaces first match | Replaces all matches    |
| Supports regex       | Supports string & regex |
| Older method         | ES2021                  |

```js
str.replace("a", "b");
str.replaceAll("a", "b");
```

### Q. What is string immutability?

**Answer:**

Strings in JavaScript are immutable, meaning:

- They cannot be changed once created
- Any operation returns a new string

```js
var str = "hello";
str[0] = "H"; // No effect
```

### Q. What is split()?

**Answer:**

split() converts a string into an array using a separator.

```js
"hello world".split(" ");
```

```js
"abc".split("");
```

### Q. Template literals vs string concatenation

**Answer:**

| Template Literals      | Concatenation    |
| ---------------------- | ---------------- |
| Uses backticks `` ` `` | Uses `+`         |
| Supports interpolation | No interpolation |
| Supports multi-line    | Single-line only |

```js
`Hello ${name}`;
"Hello " + name;
```

### Q. How to capitalize first letter?

**Answer:**

```js
function capitalize(str) {
  return str.charAt(0).toUpperCase() + str.slice(1);
}
```

### Q. How to remove spaces from string?

**Answer:**

Remove all spaces

```js
str.replace(/\s+/g, "");
```

Trim start and end

```js
str.trim();
```

## Asynchronous JavaScript

### Q. What is asynchronous JavaScript?

**Answer:**

Asynchronous JavaScript allows execution of **long-running tasks** (like API calls, timers, file operations) **without blocking the main thread**.

- JavaScript is **single-threaded**
- Async operations are handled using:
  - Callbacks
  - Promises
  - async/await

```js
setTimeout(() => {
  console.log("Async");
}, 1000);

console.log("Sync");
```

### Q. What is callback hell?

**Answer:**

Callback hell occurs when multiple nested callbacks make code:

- Hard to read
- Hard to debug
- Hard to maintain

```js
login(user, () => {
  getProfile(() => {
    getPosts(() => {
      getComments(() => {
        // callback hell
      });
    });
  });
});
```

Solution: Promises and async/await.

### Q. What are Promises?

**Answer:**

A Promise represents a value that will be available now, later, or never.

```js
var promise = new Promise((resolve, reject) => {
  resolve("Success");
});
```

Used to handle asynchronous operations in a cleaner way.

### Q. Promise states

**Answer:**

A Promise can be in one of three states:

| State     | Description                      |
| --------- | -------------------------------- |
| Pending   | Initial state                    |
| Fulfilled | Operation completed successfully |
| Rejected  | Operation failed                 |

Once settled (fulfilled/rejected), state cannot change.

### Q. Difference between then() and async/await

**Answer:**

| then()                | async/await         |
| --------------------- | ------------------- |
| Chain-based           | Synchronous-looking |
| Callback-style        | Cleaner & readable  |
| Harder error handling | Easy `try/catch`    |
| Older syntax          | Modern ES2017       |

```js
promise.then((res) => console.log(res));

async function getData() {
  var res = await promise;
}
```

### Q. How does async/await work internally?

**Answer:**

- async function always returns a Promise
- await pauses execution until Promise resolves
- Internally, it is syntactic sugar over .then()

```js
async function test() {
  return "Hello";
}
```

Equivalent to:

```js
function test() {
  return Promise.resolve("Hello");
}
```

### Q. What is Promise.all()?

**Answer:**

Promise.all() executes multiple promises in parallel and:

- Resolves when all promises resolve
- Rejects if any one promise rejects

```js
Promise.all([p1, p2, p3])
  .then((results) => console.log(results))
  .catch((err) => console.log(err));
```

### Q. Difference between Promise.all, allSettled, race, any

**Answer:**

| Method               | Resolves when          | Rejects when          |
| -------------------- | ---------------------- | --------------------- |
| `Promise.all`        | All promises resolve   | Any promise rejects   |
| `Promise.allSettled` | All promises settle    | Never                 |
| `Promise.race`       | First promise settles  | First promise rejects |
| `Promise.any`        | First promise resolves | All promises reject   |

### Q. What is event loop?

**Answer:**

The Event Loop continuously checks:

- Call stack
- Microtask queue
- Macrotask queue

It ensures non-blocking execution by pushing async callbacks to the stack when it’s empty.

### Q. Microtask queue vs Macrotask queue

**Answer:**

| Microtask Queue            | Macrotask Queue         |
| -------------------------- | ----------------------- |
| Higher priority            | Lower priority          |
| Promise callbacks          | setTimeout, setInterval |
| `then`, `catch`, `finally` | DOM events              |

Execution order:

Call Stack → Microtasks → Macrotasks

### Q. What is setTimeout?

**Answer:**

Executes a function after a specified delay (minimum time).

```js
setTimeout(() => {
  console.log("Executed later");
}, 1000);
```

Delay is not guaranteed exact due to event loop.

### Q. What is setInterval?

**Answer:**

Executes a function repeatedly at fixed intervals.

```js
var id = setInterval(() => {
  console.log("Repeats");
}, 1000);
```

### Q. How to cancel a promise?

**Answer:**

Promises cannot be cancelled natively.

Workarounds:

- Use flags
- Use AbortController
- Ignore promise result

```js
const controller = new AbortController();
controller.abort();
```

### Q. Error handling in async/await

**Answer:**

Use try...catch blocks.

```js
async function fetchData() {
  try {
    var res = await fetch(url);
  } catch (error) {
    console.log(error);
  }
}
```

### Q. What happens when a promise rejects?

**Answer:**

- Control jumps to nearest .catch()
- In async/await, it throws an error
- If unhandled → Unhandled Promise Rejection

```js
promise.catch((err) => console.log(err));
```

## Execution Context & Internals ⭐

### Q. What is execution context?

**Answer:**

An **Execution Context** is the environment where JavaScript code is **evaluated and executed**.

It contains:

- Variable Environment (variables, functions)
- Scope chain
- Value of `this`

**Types of Execution Context:**

- Global Execution Context (GEC)
- Function Execution Context (FEC)
- Eval Execution Context (rare)

---

### Q. Phases of execution context

**Answer:**

Execution context is created in **two phases**:

1. Memory Creation Phase (Hoisting Phase)
   - Memory allocated for variables & functions
   - Variables initialized as `undefined`
   - Functions stored with full definition

2. Execution Phase
   - Code executed line by line
   - Variables assigned actual values
   - Functions invoked

```js
console.log(a); // undefined
var a = 10;
```

### Q. What is call stack?

**Answer:**

The Call Stack is a data structure that keeps track of function execution order.

- Uses LIFO (Last In, First Out)
- Each function call creates a new execution context
- Removed once execution finishes

```js
function a() {
  b();
}
function b() {
  console.log("Hello");
}
a();
```

Call Stack Flow:

Global → a() → b() → pop → pop

### Q. What is memory heap?

**Answer:**

The Memory Heap is a region of memory used for dynamic memory allocation.

- Stores objects, arrays, functions
- Unstructured memory
- Managed by garbage collector

```js
var obj = { name: "JS" };
```

### Q. What is event loop?

**Answer:**

The Event Loop monitors:

- Call Stack
- Microtask Queue
- Macrotask Queue

Its job is to push async callbacks to the call stack when it is empty.

Execution order:

Call Stack → Microtasks → Macrotasks

### Q. How does JavaScript handle single-threading?

**Answer:**

JavaScript is single-threaded, meaning:

- One call stack
- One task executed at a time

Non-blocking behavior is achieved using:

- Web APIs
- Callback queue
- Promises
- Event Loop

```js
setTimeout(() => console.log("Async"), 0);
console.log("Sync");
```

### Q. What is Temporal Dead Zone (TDZ)?

**Answer:**

TDZ is the time between:

- Variable declaration
- Variable initialization

Applies to let and const.

```js
console.log(a); // ReferenceError
let a = 10;
```

Variables exist but cannot be accessed before initialization.

### Q. What is garbage collection?

**Answer:**

Garbage collection is the process of automatically freeing memory that is no longer used.

JavaScript uses Mark-and-Sweep algorithm:

- Marks reachable objects
- Removes unreachable objects

```js
var obj = { name: "JS" };
obj = null; // eligible for GC
```

### Q. How does JavaScript handle async operations?

**Answer:**

Steps:

1. Async task sent to Web APIs
2. Callback registered
3. Promise resolved/rejected
4. Callback added to task queue
5. Event loop moves it to call stack

```js
fetch(url).then((res) => console.log(res));
```

### Q. Difference between stack and heap

**Answer:**

| Stack                    | Heap                        |
| ------------------------ | --------------------------- |
| Stores execution context | Stores objects & references |
| Fast access              | Slower access               |
| Size limited             | Large memory                |
| Automatic memory         | Dynamic allocation          |

## DOM & Browser APIs

### Q. What is DOM?

DOM (Document Object Model) is a **tree-like representation of an HTML document** that allows JavaScript to:

- Read
- Modify
- Add
- Delete elements dynamically

Each HTML element becomes a **node** in the DOM tree.

### Q. How to select elements in DOM?

Common DOM selectors

```js
document.getElementById("id");
document.getElementsByClassName("class");
document.getElementsByTagName("div");
document.querySelector(".class");
document.querySelectorAll(".class");
querySelector → first match
```

querySelectorAll → NodeList of matches

### Q. Difference between innerHTML and innerText

**Answer:**

| innerHTML         | innerText              |
| ----------------- | ---------------------- |
| Parses HTML       | Treats content as text |
| Faster but unsafe | Safer                  |
| Can cause XSS     | No HTML execution      |

```js
el.innerHTML = "<b>Hello</b>";
el.innerText = "<b>Hello</b>";
```

### Q. What is event bubbling?

**Answer:**

Event bubbling means the event starts from the target element and propagates upward to parent elements.

Order:

Target → Parent → Document

Default behavior for most events.

### Q. What is event capturing?

**Answer:**

Event capturing (trickling) means the event travels from root to target element.

Order:

Document → Parent → Target

Enabled using:

```js
element.addEventListener("click", handler, true);
```

### Q. Event delegation

**Answer:**

Event delegation is a technique where a single event listener is added to a parent instead of multiple child elements.

```js
parent.addEventListener("click", function (e) {
  if (e.target.matches(".child")) {
    console.log("Clicked child");
  }
});
```

Benefits:

- Better performance
- Handles dynamically added elements

### Q. Difference between addEventListener and onclick

**Answer:**

| addEventListener          | onclick          |
| ------------------------- | ---------------- |
| Multiple handlers allowed | Only one handler |
| Supports capture/bubble   | No capture       |
| Preferred modern approach | Older approach   |

### Q. What is preventDefault()?

**Answer:**

Stops the browser’s default behavior.

```js
form.addEventListener("submit", (e) => {
  e.preventDefault();
});
```

Example: Prevent form submission, link navigation.

### Q. What is stopPropagation()?

**Answer:**

Stops the event from bubbling or capturing further.

```js
button.addEventListener("click", (e) => {
  e.stopPropagation();
});
```

### Q. What is dataset?

**Answer:**

dataset provides access to data- attributes\*.

```html
<div data-user-id="101"></div>
```

```js
el.dataset.userId; // "101"
```

### Q. What is localStorage vs sessionStorage?

**Answer:**

| localStorage       | sessionStorage      |
| ------------------ | ------------------- |
| Persistent         | Clears on tab close |
| 5–10 MB            | 5–10 MB             |
| Shared across tabs | Tab-specific        |
| String only        | String only         |

### Q. What are cookies?

**Answer:**

Cookies are small pieces of data stored in the browser and sent with every HTTP request.

- Size limit ~4KB
- Used for authentication, tracking
- Can have expiry

```js
document.cookie = "user=Tanmay";
```

### Q. How to manipulate styles in JS?

**Answer:**

Inline styles

```js
el.style.color = "red";
```

Using class

```js
el.classList.add("active");
el.classList.remove("active");
```

### Q. How to create elements dynamically?

**Answer:**

```js
var div = document.createElement("div");
div.innerText = "Hello";
document.body.appendChild(div);
```

### Q. What is requestAnimationFrame()?

**Answer:**

requestAnimationFrame() schedules a function to run before the next repaint.

```js
function animate() {
  // animation logic
  requestAnimationFrame(animate);
}
requestAnimationFrame(animate);
```

Advantages:

- Smooth animations
- Better performance than setTimeout
- Syncs with screen refresh rate

## ES6+ Features (Very Important)

### Q. What is ES6?

**Answer**

ES6 (ECMAScript 2015) is a major update to JavaScript that introduced modern syntax and features to write cleaner, more maintainable, and scalable code.

Explanation

Before ES6, JavaScript had limitations in variable scoping, modularity, and readability. ES6 solved these by adding features like:

- let and const
- Arrow functions
- Classes
- Modules
- Destructuring
- Spread / Rest operators

Example

```js
const name = "Tanmay";
const greet = () => `Hello ${name}`;
```

### Q. let / const vs var

**Answer**

let and const are block-scoped, while var is function-scoped.

| Feature    | var             | let       | const     |
| ---------- | --------------- | --------- | --------- |
| Scope      | Function        | Block     | Block     |
| Re-declare | ✅ Yes          | ❌ No     | ❌ No     |
| Re-assign  | ✅ Yes          | ✅ Yes    | ❌ No     |
| Hoisting   | Yes (undefined) | Yes (TDZ) | Yes (TDZ) |

Explanation

- var can cause bugs due to scope leakage
- let is used when value changes
- const is preferred by default for safety

```js
if (true) {
  let x = 10;
}
console.log(x); // ❌ ReferenceError
```

### Q. Arrow Functions

**Answer**

Arrow functions are a shorter syntax for writing functions and they do not have their own this.

Explanation

- this is inherited from the surrounding scope
- Ideal for callbacks and functional programming

Example

```js
const add = (a, b) => a + b;
```

❗ Important Interview Point

Arrow functions cannot be used as constructors.

### Q. Destructuring

**Answer**

Destructuring allows extracting values from arrays or objects into variables.

Example

```js
const user = { name: "Amit", age: 25 };
const { name, age } = user;
```

Why it’s useful

- Cleaner code
- Avoid repetitive access (user.name)

### Q. Spread vs Rest Operator

**Answer**

Both use ... but serve different purposes.

Spread (...)

Used to expand elements.

```js
const arr1 = [1, 2];
const arr2 = [...arr1, 3];
```

Rest (...)

Used to collect multiple values.

```js
function sum(...nums) {
  return nums.reduce((a, b) => a + b);
}
```

### Q. Modules (import / export)

**Answer**

Modules allow splitting code into reusable files.

Explanation

- Each file is its own scope
- Improves maintainability and performance

Example

```js
// math.js
export const add = (a, b) => a + b;

// main.js
import { add } from "./math.js";
```

### Q. Default Parameters

**Answer**

Default parameters provide fallback values for function arguments.

Example

```js
function greet(name = "Guest") {
  return `Hello ${name}`;
}
```

Why useful

- Avoids manual checks
- Cleaner function logic

### Q. Optional Chaining (?.)

**Answer**

Optional chaining safely accesses nested object properties without throwing errors.

Example

```js
user?.address?.city;
```

Explanation

If any part is null or undefined, it returns undefined instead of crashing.

### Q. Nullish Coalescing (??)

**Answer**

Returns the right-hand value only if the left-hand value is null or undefined.

Example

```js
const value = input ?? "default";
```

Difference from ||

```js
0 || 10; // 10 ❌
0 ?? 10; // 0 ✅
```

### Q. Classes in JavaScript

**Answer**

Classes are syntactic sugar over JavaScript’s prototype-based inheritance.

Example

```js
class Person {
  constructor(name) {
    this.name = name;
  }
  greet() {
    return `Hello ${this.name}`;
  }
}
```

Important

- Under the hood, JS still uses prototypes
- Classes improve readability

### Q. CommonJS vs ES Modules

**Answer**

They are two different module systems in JavaScript.

| Feature | CommonJS         | ES Modules     |
| ------- | ---------------- | -------------- |
| Syntax  | `require()`      | `import`       |
| Export  | `module.exports` | `export`       |
| Loading | Synchronous      | Asynchronous   |
| Used in | Node.js          | Browser + Node |

```js
// CommonJS
const fs = require("fs");

// ES Module
import fs from "fs";
```

### Q. Symbol Data Type

**Answer**

A Symbol is a unique and immutable primitive used as object keys.

Example

```js
const id = Symbol("id");
const user = { [id]: 101 };
```

Why useful

- Avoids property name collisions
- Used in libraries and meta-programming

### Q. BigInt

**Answer**

BigInt is used to represent numbers larger than Number.MAX_SAFE_INTEGER.

Example

```js
const big = 12345678901234567890n;
```

Interview Tip

- Cannot mix BigInt and Number directly

### Q. What is Object.entries()?

**Answer**

Returns an array of [key, value] pairs from an object.

Example

```js
const obj = { a: 1, b: 2 };
Object.entries(obj);
// [["a",1], ["b",2]]
```

Use Case

- Iterating objects easily

### Q. What is Object.values()?

**Answer**

Returns an array of all values of an object.

Example

```js
Object.values({ a: 1, b: 2 });
// [1, 2]
```

Common Use

- Calculations
- Transforming object data

## Error Handling

### Q. What is try...catch?

**Answer**

try...catch is used to handle runtime errors gracefully without crashing the application.

Explanation

- Code that might fail is placed inside try
- If an error occurs, control moves to catch
- Prevents app from breaking

Example

```js
try {
  const data = JSON.parse("{invalid}");
} catch (error) {
  console.error("Parsing failed");
}
```

### Q. What is finally?

**Answer**

finally is a block that always executes, whether an error occurs or not.

Explanation

- Used for cleanup operations
- Runs after try and catch

Example

```js
try {
  console.log("Try");
} catch (e) {
  console.log("Catch");
} finally {
  console.log("Always runs");
}
```

Common Use

- Closing resources
- Stopping loaders
- Logging

### Q. Custom Errors

**Answer**

Custom errors allow developers to create meaningful, application-specific errors.

Explanation

JavaScript provides the Error class which can be extended.

Example

```js
class ValidationError extends Error {
  constructor(message) {
    super(message);
    this.name = "ValidationError";
  }
}

throw new ValidationError("Invalid input");
```

Why Important

- Better debugging
- Cleaner error handling logic

### Q. Difference Between Runtime and Syntax Errors

**Answer**

Syntax errors occur during parsing, while runtime errors occur during execution.

Comparison

| Feature     | Syntax Error     | Runtime Error    |
| ----------- | ---------------- | ---------------- |
| When        | Before execution | During execution |
| Detected by | JS engine        | While running    |
| Recoverable | ❌ No            | ✅ Yes           |

Example

```js
// Syntax Error
if (true { }

// Runtime Error
console.log(a); // ReferenceError
```

### Q. Error Handling in Promises

**Answer**

Errors in promises are handled using .catch().

Explanation

- Any rejection in the chain flows to .catch()
- Prevents unhandled promise rejections

Example

```js
fetch(url)
  .then((res) => res.json())
  .catch((err) => console.error(err));
```

### Q. Global Error Handling

**Answer**

Global error handling captures uncaught errors at the application level.

Browser Example

```js
window.onerror = function (message, source, line, col, error) {
  console.error("Global Error:", message);
};
```

Promise Errors

```js
window.addEventListener("unhandledrejection", (event) => {
  console.error(event.reason);
});
```

Why Needed

- Centralized logging
- Monitoring production errors

### Q. What is throw?

**Answer**

throw is used to manually generate an error.

Explanation

- Can throw built-in or custom errors
- Immediately stops execution

Example

```js
if (!user) {
  throw new Error("User not found");
}
```

### Q. How to Handle Async Errors?

**Answer**

Async errors are handled using try...catch with async/await or .catch() with promises.

Example (async/await)

```js
async function fetchData() {
  try {
    const res = await fetch(url);
    const data = await res.json();
  } catch (error) {
    console.error(error);
  }
}
```

Important Interview Point

try...catch only works with await, not raw promises.

### Q. What is a Stack Trace?

**Answer**

A stack trace shows the sequence of function calls that led to an error.

Explanation

- Helps locate where the error originated
- Printed automatically when an error occurs

Example

```js
function a() {
  b();
}
function b() {
  throw new Error("Oops");
}
a();
```

Output

Shows call order → a → b

### Q. Best Practices for Error Handling

**Answer**

- Use try...catch only where necessary
- Create custom error classes
- Never swallow errors silently
- Log errors with context
- Handle promise rejections
- Use global error handlers
- Show user-friendly messages

Bad Practice ❌

```js
try {
  riskyCode();
} catch (e) {}
```

Good Practice ✅

```js
catch (e) {
logError(e);
showMessage("Something went wrong");
}
```

### 🔥 Common Interview Follow-ups

Be ready to answer:

Can try...catch catch async errors? ❌ (without await)

Difference between Error and TypeError

How error handling differs in frontend vs backend

What happens if promise rejection is not handled?

## Performance & Optimization

Q. How to improve JS performance?
Q. What is debouncing?
Q. What is throttling?
Q. Difference between debounce and throttle
Q. Memory leaks in JS
Q. How closures cause memory leaks?
Q. Lazy loading
Q. Code splitting
Q. Minification & tree shaking
Q. Web Workers

## Security (Frontend Focus)

Q. What is XSS?
Q. What is CSRF?
Q. How to prevent XSS in JS?
Q. What is CORS?
Q. Same-origin policy
Q. How cookies are secured?
Q. What is Content Security Policy?
Q. Secure localStorage usage
Q. JWT vs sessions
Q. Why not store sensitive data in localStorage?

## Coding Questions (Common)

Q. Reverse a string
Q. Check palindrome
Q. Flatten nested array
Q. Remove duplicates from array
Q. Find max/min in array
Q. Debounce function implementation
Q. Throttle function implementation
Q. Deep clone object
Q. Implement Promise.all
Q. Implement once() function

## Tricky Output-Based Questions ⭐

Q. Output of console.log(typeof null)
Q. Output of [] == []
Q. Output of 0 == false
Q. Output of setTimeout inside loop
Q. Output of closure inside loop
Q. Output of this in different contexts
Q. Hoisting output questions
Q. Promise output order
Q. Event loop output questions
Q. Temporal dead zone examples
