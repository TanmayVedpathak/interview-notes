# JAVASCRIPT

## Q. What is JavaScript? Is it interpreted or compiled?What is JavaScript? Is it interpreted or compiled?

**Answer:**
JavaScript is a high-level, dynamically typed scripting language used for web development. While it was traditionally interpreted, modern JavaScript engines use Just-In-Time compilation, making it both interpreted and compiled at runtime for better performance.

## Q. Difference between var, let, and const

**Answer:**
var is function-scoped and hoisted with initialization, while let and const are block-scoped, hoisted into the Temporal Dead Zone, and safer to use. const prevents reassignment.

## Q. What is the Temporal Dead Zone?

**Answer:**
The Temporal Dead Zone is the phase during execution where let and const variables are hoisted but not yet initialized, and accessing them results in a ReferenceError.

## Q. What are primitive and non-primitive data types?

**Answer:**
Primitive data types store immutable values and are compared by value, while non-primitive data types store references to mutable objects and are compared by reference.

## Q. Difference between mutable and immutable

**Answer:**
Mutable values can be changed after creation, while immutable values cannot; any modification to an immutable value creates a new instance.

## Q. Difference between == and ===

**Answer:**
== checks equality after type coercion, whereas === checks equality without type coercion by comparing both value and type.

## Q. What is type coercion?

**Answer:**
Type coercion is JavaScript’s automatic or manual conversion of values between data types during operations and comparisons.

## Q. What is NaN? How do you check if a value is NaN?

**Answer:**
NaN is a special numeric value representing an invalid mathematical result, and the correct way to check for it is Number.isNaN().

## Q. Difference between null and undefined

**Answer:**
undefined means a variable has been declared but not assigned a value, while null is an explicitly assigned value representing intentional absence.

## Q. What is hoisting?

**Answer:**
Hoisting is JavaScript’s behavior of moving declarations to the top of their scope during compilation, allowing variables and functions to be accessed before their declaration in code.

## Q.

**Answer:**

## Q.

**Answer:**

## Q.

**Answer:**

## Q.

**Answer:**

## Q. What is Event Delegation?

**Answer:**  
Event delegation is a technique where a single event listener is attached to a parent element to handle events for its child elements using event bubbling.

```js
document.querySelector("ul").addEventListener("click", (e) => {
  if (e.target.tagName === "LI") {
    console.log(e.target.textContent);
  }
});
```
