# JAVASCRIPT

## JavaScript Basics (Must-Know)

### Q. What is JavaScript? Is it interpreted or compiled?What is JavaScript? Is it interpreted or compiled?

**Answer:**

JavaScript is a high-level, dynamically typed scripting language used for web development. While it was traditionally interpreted, modern JavaScript engines use Just-In-Time compilation, making it both interpreted and compiled at runtime for better performance.

### Q. Difference between `var`, `let`, and `const`

**Answer:**

`var` is function-scoped and hoisted with initialization, while `let` and `const` are block-scoped, hoisted into the Temporal Dead Zone, and safer to use. const prevents reassignment.

### Q. What is the Temporal Dead Zone?

**Answer:**

The Temporal Dead Zone is the phase during execution where let and const variables are hoisted but not yet initialized, and accessing them results in a ReferenceError.

### Q. What are primitive and non-primitive data types?

**Answer:**

Primitive data types store immutable values and are compared by value, while non-primitive data types store references to mutable objects and are compared by reference.

### Q. Difference between mutable and immutable

**Answer:**

Mutable values can be changed after creation, while immutable values cannot; any modification to an immutable value creates a new instance.

### Q. Difference between `==` and `===`

**Answer:**

`==` checks equality after type coercion, whereas `===` checks equality without type coercion by comparing both value and type.

### Q. What is type coercion?

**Answer:**

Type coercion is JavaScript’s automatic or manual conversion of values between data types during operations and comparisons.

### Q. What is NaN? How do you check if a value is NaN?

**Answer:**

`NaN` is a special numeric value representing an invalid mathematical result, and the correct way to check for it is `Number.isNaN()`.

### Q. Difference between null and undefined

**Answer:**

`undefined` means a variable has been declared but not assigned a value, while `null` is an explicitly assigned value representing intentional absence.

### Q. What is hoisting?

**Answer:**

Hoisting is JavaScript’s behavior of moving declarations to the top of their scope during compilation, allowing variables and functions to be accessed before their declaration in code.

### Q. What is strict mode ("use strict")?

**Answer:**

Strict mode is a JavaScript feature that enforces stricter syntax and runtime checks, preventing common bugs and making code more secure and predictable.

### Q. What is the difference between `alert`, `prompt`, and `confirm`?

**Answer:**

`alert` shows a message, `prompt` collects user input, and `confirm` asks for user confirmation, all using blocking browser dialogs.

### Q. What are template literals?

**Answer:**

Template literals are ES6 string literals enclosed in backticks (`) that support string interpolation (${}), multi-line strings, and expression embedding.

### Q. What is the `typeof` operator?

**Answer:**

`typeof` is a unary operator that returns a string indicating the data type of a value (e.g., "string", "number", "undefined", "object", "function").

### Q. What are falsy values in JavaScript?

**Answer:**

Values that evaluate to false in a Boolean context:
`false`, `0`, `-0`, `0n`, `""`, `null`, `undefined`, `NaN`.

### Q. Difference between `isNaN()` and `Number.isNaN()`

**Answer:**

`isNaN()` performs type coercion before checking.

`Number.isNaN()` checks without type coercion and is more reliable.

### Q. Explain `parseInt()` vs `Number()`

**Answer:**

`parseInt()` parses a string up to the first non-numeric character and can take a radix.

`Number()` converts the entire value to a number and returns NaN if conversion fails.

### Q. What is the difference between `undefined`, `null`, and `not defined`?

**Answer:**

`undefined`, `null`, and `not defined` are different concepts in JavaScript.

#### 1. `undefined`

`undefined` means a variable has been declared but has not been assigned any value.

Example:

```js
let name;

console.log(name); // undefined
```

Here, the variable `name` exists, but no value has been assigned to it yet.

JavaScript also returns `undefined` in cases like:

```js
function greet() {}

console.log(greet()); // undefined
```

A function that does not explicitly return anything returns `undefined`.

Another example:

```js
const user = {
  name: "John",
};

console.log(user.age); // undefined
```

Here, `age` does not exist on the object, so JavaScript returns `undefined`.

#### 2. `null`

`null` is an explicitly assigned value that represents intentional absence of value.

Example:

```js
let user = null;

console.log(user); // null
```

Here, we are intentionally saying that `user` has no value right now.

Common use case:

```js
let selectedUser = null;

// Later
selectedUser = {
  id: 1,
  name: "John",
};
```

`null` is usually used when we want to manually clear or reset a value.

#### 3. `not defined`

`not defined` means the variable has not been declared at all.

Example:

```js
console.log(age); // ReferenceError: age is not defined
```

Here, `age` was never declared, so JavaScript throws a `ReferenceError`.

#### Difference Table

| Term          | Meaning                                   | Example                              | Result           |
| ------------- | ----------------------------------------- | ------------------------------------ | ---------------- |
| `undefined`   | Variable exists but value is not assigned | `let x;`                             | `undefined`      |
| `null`        | Intentional empty value                   | `let x = null;`                      | `null`           |
| `not defined` | Variable does not exist                   | `console.log(x)` without declaration | `ReferenceError` |

**Interview Line**

`undefined` means a variable is declared but not assigned, `null` means intentional empty value, and `not defined` means the variable was never declared.

### Q. Why is `typeof null` equal to `"object"`?

**Answer:**

In JavaScript:

```js
console.log(typeof null); // "object"
```

This is a well-known historical bug in JavaScript.

`null` is not actually an object. It is a primitive value that represents intentional absence of value.

However, in the original implementation of JavaScript, values were stored with internal type tags. Objects had a type tag of `0`, and due to the way `null` was represented internally, it also matched the object type tag.

Because of that, `typeof null` returned `"object"`.

This behavior was never fixed because changing it would break a lot of existing JavaScript code on the web.

#### Important Point

Even though `typeof null` returns `"object"`, `null` is a primitive value.

Example:

```js
let value = null;

console.log(typeof value); // "object"
console.log(value === null); // true
```

The correct way to check for `null` is:

```js
if (value === null) {
  console.log("Value is null");
}
```

#### Difference from Object

```js
const obj = {};

console.log(typeof obj); // "object"
console.log(typeof null); // "object"
```

Both return `"object"`, but only `{}` is actually an object.

**Interview Line**

`typeof null` returns `"object"` because of a historical bug in JavaScript, but `null` is actually a primitive value, not an object.

### Q. What is the difference between primitive values and reference values?

**Answer:**

JavaScript values are mainly divided into two categories:

1. Primitive values
2. Reference values

#### 1. Primitive Values

Primitive values are simple, immutable values.

Examples of primitive types:

```js
string;
number;
boolean;
null;
undefined;
symbol;
bigint;
```

Example:

```js
let a = 10;
let b = a;

b = 20;

console.log(a); // 10
console.log(b); // 20
```

Here, `b` gets a copy of the value of `a`. Changing `b` does not affect `a`.

Primitive values are compared by value.

Example:

```js
console.log(10 === 10); // true
console.log("hello" === "hello"); // true
```

#### 2. Reference Values

Reference values are objects stored by reference.

Examples:

```js
object
array
function
date
map
set
```

Example:

```js
let obj1 = {
  name: "John",
};

let obj2 = obj1;

obj2.name = "Amit";

console.log(obj1.name); // Amit
console.log(obj2.name); // Amit
```

Here, `obj1` and `obj2` both point to the same object in memory. Changing one affects the other.

Reference values are compared by reference, not by content.

Example:

```js
console.log({} === {}); // false
console.log([] === []); // false
```

Both objects look the same, but they are stored at different memory locations.

#### Difference Table

| Primitive Values                  | Reference Values                  |
| --------------------------------- | --------------------------------- |
| Store actual value                | Store reference/address           |
| Compared by value                 | Compared by reference             |
| Immutable                         | Usually mutable                   |
| Stored directly                   | Stored in heap memory             |
| Examples: string, number, boolean | Examples: object, array, function |

#### Example Comparison

```js
let x = "hello";
let y = "hello";

console.log(x === y); // true
```

Because strings are primitives, they are compared by value.

```js
let a = { name: "John" };
let b = { name: "John" };

console.log(a === b); // false
```

Because objects are reference values, they are compared by memory reference.

**Interview Line**

Primitive values are compared by value, while reference values like objects and arrays are compared by memory reference.

### Q. How does JavaScript compare objects?

**Answer:**

JavaScript compares objects by reference, not by their actual content.

Example:

```js
const obj1 = {
  name: "John",
};

const obj2 = {
  name: "John",
};

console.log(obj1 === obj2); // false
```

Even though both objects have the same property and value, JavaScript returns `false`.

This is because both objects are created separately in memory.

#### Same Reference Example

```js
const obj1 = {
  name: "John",
};

const obj2 = obj1;

console.log(obj1 === obj2); // true
```

Here, `obj2` is not a new object. It points to the same object as `obj1`.

So the comparison returns `true`.

#### Arrays Are Also Compared by Reference

```js
console.log([] === []); // false
```

Both arrays are different references.

```js
const arr1 = [1, 2, 3];
const arr2 = arr1;

console.log(arr1 === arr2); // true
```

Here, both variables refer to the same array.

#### How to Compare Object Values

To compare object values, we need to manually compare their properties.

Example:

```js
const obj1 = {
  name: "John",
  age: 25,
};

const obj2 = {
  name: "John",
  age: 25,
};

function shallowEqual(a, b) {
  const keysA = Object.keys(a);
  const keysB = Object.keys(b);

  if (keysA.length !== keysB.length) {
    return false;
  }

  return keysA.every((key) => a[key] === b[key]);
}

console.log(shallowEqual(obj1, obj2)); // true
```

This works for shallow objects.

#### JSON.stringify Approach

```js
console.log(JSON.stringify(obj1) === JSON.stringify(obj2)); // true
```

But this approach has limitations:

- Property order matters
- Does not handle functions
- Does not handle `undefined` properly
- Does not work well with circular references
- Does not handle Date, Map, Set properly

**Interview Line**

JavaScript compares objects by reference, not by content. Two objects are equal only if they point to the same memory location.

### Q. What is implicit type conversion in JavaScript?

**Answer:**

Implicit type conversion means JavaScript automatically converts one data type into another when needed.

It is also called type coercion.

Example:

```js
console.log("5" + 2); // "52"
```

Here, JavaScript converts `2` into a string and performs string concatenation.

Another example:

```js
console.log("5" - 2); // 3
```

Here, JavaScript converts `"5"` into a number and performs subtraction.

#### Common Examples

```js
console.log(1 + "2"); // "12"
console.log("10" - 5); // 5
console.log("10" * 2); // 20
console.log("10" / 2); // 5
console.log(true + 1); // 2
console.log(false + 1); // 1
```

#### In Comparisons

```js
console.log(5 == "5"); // true
```

JavaScript converts `"5"` to number `5`, then compares.

```js
console.log(false == 0); // true
console.log(null == undefined); // true
```

These results happen because of implicit coercion.

#### Why It Can Be Dangerous

Implicit conversion can create unexpected results.

Example:

```js
console.log([] == false); // true
console.log("" == false); // true
console.log("0" == false); // true
```

These are valid JavaScript results, but they can be confusing.

**Interview Line**

Implicit type conversion is JavaScript’s automatic conversion of values from one type to another during operations or comparisons.

### Q. What is explicit type conversion in JavaScript?

**Answer:**

Explicit type conversion means manually converting one data type into another using built-in functions.

It is also called type casting.

#### Convert to Number

```js
const value = "123";

console.log(Number(value)); // 123
```

Other examples:

```js
Number("10"); // 10
Number("10.5"); // 10.5
Number(""); // 0
Number("abc"); // NaN
Number(true); // 1
Number(false); // 0
```

#### Convert to String

```js
const num = 100;

console.log(String(num)); // "100"
```

Other examples:

```js
String(123); // "123"
String(true); // "true"
String(null); // "null"
String(undefined); // "undefined"
```

#### Convert to Boolean

```js
console.log(Boolean(1)); // true
console.log(Boolean(0)); // false
console.log(Boolean("hello")); // true
console.log(Boolean("")); // false
```

#### Using Unary Plus

```js
const str = "50";

console.log(+str); // 50
```

Unary plus converts a value into a number.

#### Explicit vs Implicit Conversion

```js
console.log("5" - 2); // 3
```

This is implicit conversion.

```js
console.log(Number("5") - 2); // 3
```

This is explicit conversion.

Explicit conversion is usually preferred because it makes the developer’s intention clear.

**Interview Line**

Explicit type conversion means manually converting values using functions like `Number()`, `String()`, and `Boolean()`.

### Q. What is the difference between `Number()`, `parseInt()`, and `parseFloat()`?

**Answer:**

`Number()`, `parseInt()`, and `parseFloat()` are used to convert values into numbers, but they behave differently.

#### 1. `Number()`

`Number()` converts the entire value into a number.

Example:

```js
console.log(Number("123")); // 123
console.log(Number("12.5")); // 12.5
console.log(Number("123abc")); // NaN
```

If the full string cannot be converted into a valid number, it returns `NaN`.

More examples:

```js
Number(""); // 0
Number(" "); // 0
Number(true); // 1
Number(false); // 0
Number(null); // 0
Number(undefined); // NaN
```

#### 2. `parseInt()`

`parseInt()` parses a value and returns an integer.

Example:

```js
console.log(parseInt("123")); // 123
console.log(parseInt("12.9")); // 12
console.log(parseInt("123abc")); // 123
```

It reads the string from left to right and stops when it finds an invalid character.

Example:

```js
console.log(parseInt("abc123")); // NaN
```

Because the string starts with invalid characters, it returns `NaN`.

`parseInt()` can also accept a radix.

```js
console.log(parseInt("10", 10)); // 10
console.log(parseInt("10", 2)); // 2
```

Here, radix `2` means binary.

#### 3. `parseFloat()`

`parseFloat()` parses a value and returns a decimal number.

Example:

```js
console.log(parseFloat("12.5")); // 12.5
console.log(parseFloat("12.5abc")); // 12.5
console.log(parseFloat("abc12.5")); // NaN
```

Like `parseInt()`, it stops when it finds an invalid character.

#### Difference Table

| Method         | Converts Entire Value? | Allows Decimal? | Stops at Invalid Character? |
| -------------- | ---------------------- | --------------- | --------------------------- |
| `Number()`     | Yes                    | Yes             | No, returns `NaN`           |
| `parseInt()`   | No                     | No              | Yes                         |
| `parseFloat()` | No                     | Yes             | Yes                         |

#### Example Comparison

```js
Number("10px"); // NaN
parseInt("10px"); // 10
parseFloat("10.5px"); // 10.5
```

#### When to Use

Use `Number()` when the complete value must be a valid number.

Use `parseInt()` when you need an integer from a string.

Use `parseFloat()` when you need a decimal number from a string.

**Interview Line**

`Number()` converts the entire value, `parseInt()` extracts an integer, and `parseFloat()` extracts a decimal number from the beginning of a string.

### Q. What are truthy and falsy values?

**Answer:**

In JavaScript, every value is treated as either truthy or falsy when used in a Boolean context.

A Boolean context means places like:

```js
if condition
while loop
logical operators
ternary operator
```

#### Falsy Values

Falsy values are values that become `false` when converted to Boolean.

JavaScript has these falsy values:

```js
false;
0 - 0;
0n;
("");
null;
undefined;
NaN;
```

Example:

```js
if (0) {
  console.log("Runs");
} else {
  console.log("Does not run");
}
```

Output:

```js
Does not run
```

Because `0` is falsy.

#### Truthy Values

Truthy values are values that become `true` when converted to Boolean.

Examples:

```js
true
1
-1
"hello"
"0"
"false"
[]
{}
function () {}
```

Example:

```js
if ("hello") {
  console.log("Runs");
}
```

Output:

```js
Runs;
```

Because non-empty strings are truthy.

#### Important Examples

```js
Boolean(""); // false
Boolean(" "); // true
Boolean("false"); // true
Boolean([]); // true
Boolean({}); // true
Boolean(null); // false
Boolean(undefined); // false
Boolean(NaN); // false
```

#### Common Use Case

```js
const username = "";

if (!username) {
  console.log("Username is required");
}
```

Since an empty string is falsy, this condition runs.

#### Be Careful

```js
const count = 0;

if (!count) {
  console.log("No count");
}
```

This runs because `0` is falsy. But sometimes `0` may be a valid value.

In such cases, use explicit checks:

```js
if (count === null || count === undefined) {
  console.log("Count is missing");
}
```

**Interview Line**

Falsy values are values that behave like `false` in Boolean contexts, while all other values are truthy.

### Q. Why should we avoid using `==` in production code?

**Answer:**

We should avoid using `==` because it performs type coercion before comparison.

This means JavaScript may automatically convert values to another type before comparing them.

Example:

```js
console.log(5 == "5"); // true
```

Here, `"5"` is converted to number `5`, so the result is `true`.

With strict equality:

```js
console.log(5 === "5"); // false
```

Here, both value and type are compared.

#### Problem with `==`

`==` can produce confusing and unexpected results.

Examples:

```js
console.log(false == 0); // true
console.log("" == 0); // true
console.log("0" == false); // true
console.log(null == undefined); // true
console.log([] == false); // true
```

These comparisons are valid JavaScript, but they are not always easy to understand.

#### Why `===` is Better

`===` checks both value and type.

Example:

```js
console.log(0 === false); // false
console.log("5" === 5); // false
console.log(null === undefined); // false
```

This makes code more predictable and easier to debug.

#### Production Code Best Practice

In production code, clarity and predictability are very important. Using `===` avoids hidden type conversion and reduces bugs.

Bad:

```js
if (userId == "10") {
  // confusing
}
```

Good:

```js
if (userId === 10) {
  // clear
}
```

If conversion is needed, do it explicitly:

```js
if (Number(userId) === 10) {
  // clear intention
}
```

**Interview Line**

We avoid `==` because it performs implicit type conversion, which can lead to unexpected bugs. `===` is preferred because it compares both value and type.

### Q. What is the difference between `Object.is()` and `===`?

**Answer:**

Both `Object.is()` and `===` are used to compare values, but they have small differences.

In most cases, they behave the same.

Example:

```js
console.log(10 === 10); // true
console.log(Object.is(10, 10)); // true

console.log("hello" === "hello"); // true
console.log(Object.is("hello", "hello")); // true
```

#### Difference 1: `NaN`

With `===`:

```js
console.log(NaN === NaN); // false
```

With `Object.is()`:

```js
console.log(Object.is(NaN, NaN)); // true
```

This is one major difference.

`Object.is()` treats `NaN` as equal to `NaN`.

#### Difference 2: `+0` and `-0`

With `===`:

```js
console.log(+0 === -0); // true
```

With `Object.is()`:

```js
console.log(Object.is(+0, -0)); // false
```

`Object.is()` treats `+0` and `-0` as different values.

#### Comparison Table

| Comparison      | `===`   | `Object.is()` |
| --------------- | ------- | ------------- |
| `10` and `10`   | `true`  | `true`        |
| `"a"` and `"a"` | `true`  | `true`        |
| `NaN` and `NaN` | `false` | `true`        |
| `+0` and `-0`   | `true`  | `false`       |
| `{}` and `{}`   | `false` | `false`       |

#### Object Comparison

Both compare objects by reference.

```js
console.log(Object.is({}, {})); // false
console.log({} === {}); // false
```

#### When to Use

Use `===` in most normal comparisons.

Use `Object.is()` when you specifically care about `NaN`, `+0`, or `-0`.

**Interview Line**

`Object.is()` is similar to `===`, but it treats `NaN` as equal to `NaN` and treats `+0` and `-0` as different.

### Q. What is short-circuit evaluation?

**Answer:**

Short-circuit evaluation means JavaScript stops evaluating an expression as soon as the final result is already known.

It commonly happens with logical operators:

```js
&&
||
??
```

#### Short-Circuit with `&&`

The `&&` operator returns the first falsy value, or the last value if all are truthy.

Example:

```js
console.log(false && "Hello"); // false
```

JavaScript stops at `false` because the whole expression cannot be true.

Another example:

```js
const user = null;

user && console.log(user.name);
```

Since `user` is `null`, the second part does not execute.

This prevents an error.

#### Short-Circuit with `||`

The `||` operator returns the first truthy value.

Example:

```js
console.log("John" || "Guest"); // "John"
```

JavaScript stops at `"John"` because it is truthy.

Example:

```js
const username = "";

const displayName = username || "Guest";

console.log(displayName); // "Guest"
```

Since `username` is falsy, `"Guest"` is used.

#### Short-Circuit with `??`

The `??` operator returns the right-hand value only when the left-hand value is `null` or `undefined`.

Example:

```js
const count = 0;

const value = count ?? 10;

console.log(value); // 0
```

Here, `0` is not null or undefined, so it is preserved.

#### Common React Example

```jsx
{
  isLoggedIn && <Dashboard />;
}
```

If `isLoggedIn` is false, `<Dashboard />` is not rendered.

**Interview Line**

Short-circuit evaluation means JavaScript stops evaluating an expression once the result is already determined.

### Q. Difference between `||`, `&&`, and `??`

**Answer:**

`||`, `&&`, and `??` are logical operators, but they behave differently.

#### 1. `||` OR Operator

The `||` operator returns the first truthy value.

Example:

```js
console.log("" || "Guest"); // "Guest"
console.log("John" || "Guest"); // "John"
```

It is commonly used for fallback values.

Example:

```js
const username = inputName || "Guest";
```

But it treats all falsy values as invalid.

```js
console.log(0 || 10); // 10
console.log(false || true); // true
console.log("" || "default"); // "default"
```

This can be a problem if `0`, `false`, or `""` are valid values.

#### 2. `&&` AND Operator

The `&&` operator returns the first falsy value, or the last value if all are truthy.

Example:

```js
console.log("John" && "Admin"); // "Admin"
console.log(null && "Admin"); // null
```

Common use case:

```js
isLoggedIn && showDashboard();
```

If `isLoggedIn` is false, `showDashboard()` will not run.

#### 3. `??` Nullish Coalescing Operator

The `??` operator returns the right-hand value only if the left-hand value is `null` or `undefined`.

Example:

```js
console.log(null ?? "Guest"); // "Guest"
console.log(undefined ?? "Guest"); // "Guest"
console.log(0 ?? 10); // 0
console.log(false ?? true); // false
console.log("" ?? "default"); // ""
```

This is safer than `||` when `0`, `false`, or empty string are valid values.

#### Difference Table

| Operator | Meaning            | Checks For                 | Example                          |
| -------- | ------------------ | -------------------------- | -------------------------------- |
| `\|\|`   | OR / fallback      | Any falsy value            | `0  \|\| 10` gives `10`          |
| `&&`     | AND / guard        | First falsy value          | `null && user.name` gives `null` |
| `??`     | Nullish coalescing | Only `null` or `undefined` | `0 ?? 10` gives `0`              |

#### Practical Example

```js
const value1 = 0 || 100;
console.log(value1); // 100
```

Here, `0` is treated as falsy.

```js
const value2 = 0 ?? 100;
console.log(value2); // 0
```

Here, `0` is preserved because it is not `null` or `undefined`.

**Interview Line**

`||` returns the first truthy value, `&&` returns the first falsy value, and `??` returns the fallback only for `null` or `undefined`.

### Q. What is optional chaining and where should we avoid overusing it?

**Answer:**

Optional chaining is a JavaScript feature that allows safe access to nested object properties without throwing an error if a value is `null` or `undefined`.

It uses the `?.` operator.

#### Problem Without Optional Chaining

```js
const user = null;

console.log(user.name); // TypeError
```

This throws an error because we are trying to access `name` from `null`.

#### With Optional Chaining

```js
const user = null;

console.log(user?.name); // undefined
```

Instead of throwing an error, JavaScript returns `undefined`.

#### Nested Object Example

```js
const user = {
  profile: {
    address: {
      city: "Mumbai",
    },
  },
};

console.log(user?.profile?.address?.city); // Mumbai
```

If any property in the chain is `null` or `undefined`, the result becomes `undefined`.

Example:

```js
const user = {};

console.log(user?.profile?.address?.city); // undefined
```

#### Optional Chaining with Functions

```js
const user = {
  greet() {
    return "Hello";
  },
};

console.log(user.greet?.()); // Hello
```

If `greet` does not exist, it will not throw an error.

#### Optional Chaining with Arrays

```js
const users = null;

console.log(users?.[0]); // undefined
```

#### Where Should We Avoid Overusing It?

Optional chaining is useful, but overusing it can hide bugs.

Bad example:

```js
const city = user?.profile?.address?.city;
```

This is safe, but if `user.profile` is required in your application, optional chaining may hide a data problem.

Better:

```js
if (!user.profile) {
  throw new Error("User profile is missing");
}
```

Avoid overusing optional chaining in these cases:

1. When the property is required
2. When missing data should be treated as an error
3. When it hides backend/API contract issues
4. When it makes debugging difficult
5. When validation should happen earlier

#### Good Use Case

```js
const city = user?.profile?.address?.city ?? "Unknown";
```

This is good when the value is genuinely optional.

#### Bad Use Case

```js
submitOrder?.();
```

If `submitOrder` is required, this hides the problem instead of failing clearly.

**Interview Line**

Optional chaining safely accesses nested properties without throwing errors, but it should not be overused because it can hide real bugs or missing required data.

### Q. What happens when you access a property on a primitive value?

**Answer:**

In JavaScript, primitive values are not objects. However, JavaScript allows us to access properties and methods on primitives.

Example:

```js
const name = "john";

console.log(name.toUpperCase()); // JOHN
```

Here, `name` is a string primitive, but we are able to call the `toUpperCase()` method.

This happens because JavaScript temporarily wraps the primitive value in an object wrapper.

This process is called boxing.

#### Example

```js
const str = "hello";

console.log(str.length); // 5
console.log(str.toUpperCase()); // HELLO
```

Internally, JavaScript temporarily behaves like this:

```js
const temp = new String("hello");
temp.toUpperCase();
```

After the operation is complete, the temporary object is removed.

#### Primitive Wrapper Objects

JavaScript has wrapper objects for primitives:

| Primitive | Wrapper Object |
| --------- | -------------- |
| `string`  | `String`       |
| `number`  | `Number`       |
| `boolean` | `Boolean`      |
| `bigint`  | `BigInt`       |
| `symbol`  | `Symbol`       |

#### Important Example

```js
let str = "hello";

str.customProperty = "test";

console.log(str.customProperty); // undefined
```

Why?

Because JavaScript creates a temporary wrapper object, adds the property to it, and then immediately discards it.

So the custom property is lost.

#### With Object Wrapper

```js
const strObj = new String("hello");

strObj.customProperty = "test";

console.log(strObj.customProperty); // test
```

But using wrapper objects like `new String()` is not recommended.

**Interview Line**

When we access a property or method on a primitive, JavaScript temporarily wraps it in an object wrapper, performs the operation, and then discards the wrapper.

### Q. What is boxing and unboxing in JavaScript?

**Answer:**

Boxing and unboxing are internal JavaScript processes related to primitive values and object wrappers.

#### Boxing

Boxing means converting a primitive value into a temporary object wrapper so that properties or methods can be accessed.

Example:

```js
const message = "hello";

console.log(message.toUpperCase()); // HELLO
```

Here, `"hello"` is a primitive string.

But JavaScript temporarily wraps it into a `String` object so that the `toUpperCase()` method can be used.

Conceptually:

```js
const temp = new String("hello");
temp.toUpperCase();
```

After the operation, the temporary object is removed.

#### Wrapper Objects

| Primitive | Wrapper Object |
| --------- | -------------- |
| `string`  | `String`       |
| `number`  | `Number`       |
| `boolean` | `Boolean`      |
| `bigint`  | `BigInt`       |
| `symbol`  | `Symbol`       |

#### Number Example

```js
const price = 99.99;

console.log(price.toFixed(1)); // "100.0"
```

Here, JavaScript temporarily boxes the number primitive into a `Number` object.

#### Boolean Example

```js
const isActive = true;

console.log(isActive.toString()); // "true"
```

Here, JavaScript temporarily boxes the boolean primitive into a `Boolean` object.

#### Unboxing

Unboxing means converting an object wrapper back into its primitive value.

Example:

```js
const strObj = new String("hello");

console.log(strObj.valueOf()); // "hello"
```

The `valueOf()` method returns the primitive value from the wrapper object.

Another example:

```js
const numObj = new Number(100);

console.log(numObj.valueOf()); // 100
```

#### Why Wrapper Objects Should Be Avoided

Creating wrapper objects manually can cause confusing behavior.

Example:

```js
const str1 = "hello";
const str2 = new String("hello");

console.log(typeof str1); // "string"
console.log(typeof str2); // "object"

console.log(str1 === str2); // false
```

`str1` is a primitive string, while `str2` is an object.

Another confusing example:

```js
const bool = new Boolean(false);

if (bool) {
  console.log("Runs");
}
```

This runs because objects are always truthy, even if the wrapped value is `false`.

#### Best Practice

Use primitive values directly:

```js
const name = "John";
const age = 25;
const isActive = true;
```

Avoid this:

```js
const name = new String("John");
const age = new Number(25);
const isActive = new Boolean(false);
```

**Interview Line**

Boxing is the temporary conversion of a primitive into an object wrapper, while unboxing is converting the wrapper object back into a primitive value.

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

### Q. What is scope (`global`, `function`, `block`)?

**Answer:**

Scope determines where a variable or function can be accessed in your code.

In simple terms:

Scope answers the question — “Can I use this variable here?”

Global scope: Accessible everywhere

Function scope: Accessible only inside the function

Block scope: Accessible only within `{}` using `let` and `const`

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

### Q. What is the `arguments` object?

**Answer:**

`arguments` is an array-like object available in normal functions that contains all passed arguments.

### Q. What is rest parameter (...args)?

**Answer:**

The rest parameter collects remaining function arguments into a real array, replacing the need for arguments.

### Q. Explain Pure and Impure function.

**Answer:**

#### Pure Function

A pure function is a function that always gives the same output for the same input and does not change anything outside the function.

In simple words, a pure function depends only on its input values and does not produce any side effects.

Characteristics of a Pure Function

1. It always returns the same result for the same arguments.
2. It does not modify variables, objects, arrays, or data outside its scope.
3. It does not depend on external changing values.
4. It does not perform side effects like API calls, DOM updates, file changes, or console logging.

Example of Pure Function

```js
function add(a, b) {
  return a + b;
}

console.log(add(2, 3)); // 5
console.log(add(2, 3)); // 5
```

Here, `add()` is a pure function because whenever we pass 2 and 3, it always returns 5. It does not modify any external value.

Another Example

```js
function square(num) {
  return num * num;
}

console.log(square(4)); // 16
```

This function is pure because its output depends only on the input `num`.

#### Impure Function

An impure function is a function that may give different results for the same input or changes something outside the function.

In simple words, an impure function depends on external data or creates side effects.

Characteristics of an Impure Function

1. It may return different results for the same input.
2. It may modify external variables, arrays, or objects.
3. It may depend on values outside the function.
4. It may perform side effects such as API calls, DOM manipulation, database updates, file operations, or logging.

Example of Impure Function

```js
let total = 0;

function addToTotal(value) {
  total += value;
  return total;
}

console.log(addToTotal(5)); // 5
console.log(addToTotal(5)); // 10
```

Here, `addToTotal()` is an impure function because it modifies the external variable total. Even though we pass the same input 5, the output changes.

Another Example

```js
function getRandomNumber() {
  return Math.random();
}

console.log(getRandomNumber());
console.log(getRandomNumber());
```

This is impure because Math.random() returns a different value each time, even though no input is passed.

Difference Between Pure and Impure Function

| Pure Function                                     | Impure Function                                |
| ------------------------------------------------- | ---------------------------------------------- |
| Always returns the same output for the same input | May return different output for the same input |
| Does not modify external data                     | Can modify external data                       |
| Has no side effects                               | Can have side effects                          |
| Easy to test and debug                            | Harder to test and debug                       |
| Depends only on input parameters                  | May depend on external state                   |

Why Pure Functions Are Important

Pure functions are important because they make code easier to understand, test, and debug. Since they do not depend on external data and do not modify anything outside the function, their behavior is predictable.

Pure functions are commonly used in functional programming and are very useful in JavaScript libraries and frameworks like React.

For example, in React, components and state update functions should often behave predictably. Pure functions help avoid unexpected bugs caused by changing data directly.

### Q. What is the difference between function declaration, function expression, and arrow function?

**Answer:**

A function declaration creates a named function and is fully hoisted, so it can be called before it appears in the code.

```js
sayHi();

function sayHi() {
  console.log("Hi");
}
```

A function expression stores a function inside a variable. The variable is hoisted, but the function value is assigned only when that line executes.

```js
// greet(); // ReferenceError with let/const
const greet = function () {
  console.log("Hello");
};
```

An arrow function is a shorter function expression. It does not have its own `this`, `arguments`, or `prototype`.

```js
const add = (a, b) => a + b;
```

| Feature            | Function Declaration     | Function Expression           | Arrow Function         |
| ------------------ | ------------------------ | ----------------------------- | ---------------------- |
| Hoisted with body  | Yes                      | No                            | No                     |
| Own `this`         | Yes                      | Yes                           | No                     |
| Can be constructor | Yes                      | Yes                           | No                     |
| Best use           | Reusable named functions | Conditional/dynamic functions | Callbacks, short logic |

**Interview Line**

Function declarations are hoisted, function expressions are assigned at runtime, and arrow functions are concise but use lexical `this`.

### Q. Can arrow functions be used as methods? Why or why not?

**Answer:**

Arrow functions can technically be used as object properties, but they are usually not recommended as object methods because they do not have their own `this`.

```js
const user = {
  name: "John",
  normal() {
    return this.name;
  },
  arrow: () => {
    return this.name;
  },
};

console.log(user.normal()); // "John"
console.log(user.arrow()); // undefined in most cases
```

The `normal` method gets `this` from the object that calls it. The arrow function gets `this` from the surrounding lexical scope, not from `user`.

Use arrow functions for callbacks where lexical `this` is useful, but use normal function syntax for object methods.

**Interview Line**

Arrow functions are not ideal for object methods because they do not bind `this` to the calling object.

### Q. Why arrow functions cannot be used as constructors?

**Answer:**

Arrow functions cannot be used as constructors because they do not have their own `this` binding and do not have a `prototype` property.

```js
const User = (name) => {
  this.name = name;
};

// const u = new User("John"); // TypeError: User is not a constructor
```

Constructor functions need their own `this` because `new` creates a new object and binds `this` to that object. Arrow functions are designed to capture `this` from the surrounding scope, so they cannot work with `new`.

```js
function User(name) {
  this.name = name;
}

const u = new User("John");
console.log(u.name); // John
```

**Interview Line**

Arrow functions cannot be constructors because they lack their own `this` and `prototype`.

### Q. What is lexical `this`?

**Answer:**

Lexical `this` means `this` is taken from the place where the function is defined, not from where it is called.

Arrow functions use lexical `this`.

```js
const user = {
  name: "John",
  greet() {
    const inner = () => {
      console.log(this.name);
    };

    inner();
  },
};

user.greet(); // John
```

The arrow function `inner` does not create its own `this`; it uses `this` from `greet()`, where `this` points to `user`.

This is very useful in callbacks, timers, and event handlers where normal functions may lose `this`.

**Interview Line**

Lexical `this` means an arrow function uses `this` from its surrounding scope.

### Q. What is the difference between `call`, `apply`, and `bind`?

**Answer:**

`call`, `apply`, and `bind` are used to control the value of `this` inside a function.

```js
function greet(city) {
  return `${this.name} from ${city}`;
}

const user = { name: "John" };

console.log(greet.call(user, "Mumbai"));
console.log(greet.apply(user, ["Delhi"]));

const boundGreet = greet.bind(user);
console.log(boundGreet("Pune"));
```

| Method    | Executes Immediately? | Arguments                    |
| --------- | --------------------- | ---------------------------- |
| `call()`  | Yes                   | Passed one by one            |
| `apply()` | Yes                   | Passed as an array           |
| `bind()`  | No                    | Returns a new bound function |

Use `call` when arguments are separate, `apply` when arguments are in an array, and `bind` when you want to create a reusable function with fixed `this`.

**Interview Line**

`call` and `apply` invoke immediately, while `bind` returns a new function with fixed `this`.

### Q. What is function borrowing?

**Answer:**

Function borrowing means using a method from one object on another object using `call`, `apply`, or `bind`.

```js
const user1 = {
  name: "John",
  getName() {
    return this.name;
  },
};

const user2 = {
  name: "Amit",
};

console.log(user1.getName.call(user2)); // Amit
```

Here, `user2` does not have `getName`, but it borrows the method from `user1`.

This is useful when multiple objects have similar structure and you want to reuse behavior without duplicating methods.

**Interview Line**

Function borrowing allows one object to use another object’s method by explicitly setting `this`.

### Q. What is partial application?

**Answer:**

Partial application means fixing some arguments of a function and returning a new function that accepts the remaining arguments.

```js
function multiply(a, b, c) {
  return a * b * c;
}

function partialMultiply(a) {
  return function (b, c) {
    return multiply(a, b, c);
  };
}

const doubleAndMultiply = partialMultiply(2);

console.log(doubleAndMultiply(3, 4)); // 24
```

A common real-world example is pre-configuring a function.

```js
const logWithPrefix = (prefix) => (message) => {
  console.log(`[${prefix}] ${message}`);
};

const errorLog = logWithPrefix("ERROR");
errorLog("Something went wrong");
```

**Interview Line**

Partial application creates a new function by pre-filling some arguments of an existing function.

### Q. Difference between currying and partial application

**Answer:**

Currying and partial application are related, but they are not the same.

Currying converts a function with multiple arguments into a chain of functions, each taking one argument.

```js
const add = (a) => (b) => (c) => a + b + c;

console.log(add(1)(2)(3)); // 6
```

Partial application fixes some arguments and returns a function for the remaining arguments.

```js
function add(a, b, c) {
  return a + b + c;
}

const addFive = (b, c) => add(5, b, c);

console.log(addFive(2, 3)); // 10
```

| Feature                | Currying                | Partial Application                     |
| ---------------------- | ----------------------- | --------------------------------------- |
| Converts function into | One-argument chain      | Function with fewer remaining arguments |
| Call style             | `fn(a)(b)(c)`           | `fn(a)(b, c)`                           |
| Main goal              | Function transformation | Pre-fill arguments                      |

**Interview Line**

Currying breaks a function into one-argument functions, while partial application pre-fills some arguments.

### Q. What is a first-class function?

**Answer:**

A first-class function means functions are treated like values in JavaScript.

This means functions can be:

- Stored in variables
- Passed as arguments
- Returned from other functions
- Stored in objects or arrays

```js
const greet = function () {
  return "Hello";
};

function execute(fn) {
  return fn();
}

console.log(execute(greet)); // Hello
```

This is the foundation for callbacks, higher-order functions, functional programming, and many JavaScript patterns.

**Interview Line**

JavaScript functions are first-class citizens because they can be assigned, passed, and returned like any other value.

### Q. What is a unary function?

**Answer:**

A unary function is a function that accepts exactly one argument.

```js
function square(num) {
  return num * num;
}

console.log(square(4)); // 16
```

Unary functions are common in array methods.

```js
const numbers = [1, 2, 3];

const doubled = numbers.map((num) => num * 2);
```

The callback receives one main value and returns a result.

**Interview Line**

A unary function takes one argument and returns a result based on that single input.

### Q. What is a predicate function?

**Answer:**

A predicate function is a function that returns a Boolean value: `true` or `false`.

It is commonly used for filtering, validation, and condition checks.

```js
function isEven(num) {
  return num % 2 === 0;
}

console.log(isEven(4)); // true
console.log(isEven(5)); // false
```

Predicate functions are widely used with array methods.

```js
const numbers = [1, 2, 3, 4];

const evenNumbers = numbers.filter(isEven);

console.log(evenNumbers); // [2, 4]
```

**Interview Line**

A predicate function checks a condition and returns `true` or `false`.

### Q. What are side effects in functions?

**Answer:**

Side effects are changes or interactions that happen outside a function’s local scope.

Examples of side effects:

- Modifying a global variable
- Updating the DOM
- Making an API call
- Writing to localStorage
- Logging to console
- Mutating an object or array passed as input

```js
let count = 0;

function increment() {
  count++;
}
```

Here, `increment` has a side effect because it modifies external state.

Pure functions avoid side effects.

```js
function add(a, b) {
  return a + b;
}
```

**Interview Line**

A side effect is anything a function does outside returning a value, such as modifying external state or calling an API.

### Q. How do pure functions help in testing?

**Answer:**

Pure functions are easy to test because their output depends only on their input and they do not modify external state.

```js
function calculateTotal(price, quantity) {
  return price * quantity;
}
```

Test cases are simple:

```js
console.log(calculateTotal(100, 2)); // 200
console.log(calculateTotal(100, 2)); // 200
```

There is no dependency on API calls, DOM, time, random values, or global variables.

Benefits in testing:

- Predictable output
- No setup-heavy external state
- Easier mocking
- Fewer flaky tests
- Easier debugging

**Interview Line**

Pure functions improve testing because the same input always produces the same output without side effects.

### Q. What is memoization?

**Answer:**

Memoization is an optimization technique where the result of an expensive function call is cached and reused when the same inputs occur again.

```js
function slowSquare(num) {
  console.log("Calculating...");
  return num * num;
}
```

Without memoization, the calculation runs every time.

With memoization, repeated input returns cached output.

Use cases:

- Expensive calculations
- Recursive functions
- Derived data
- Filtering or transforming large arrays

**Interview Line**

Memoization improves performance by caching function results based on input arguments.

### Q. How would you implement memoization in JavaScript?

**Answer:**

Memoization can be implemented using a closure and a cache object or `Map`.

```js
function memoize(fn) {
  const cache = new Map();

  return function (...args) {
    const key = JSON.stringify(args);

    if (cache.has(key)) {
      return cache.get(key);
    }

    const result = fn(...args);
    cache.set(key, result);
    return result;
  };
}

function add(a, b) {
  console.log("Calculating...");
  return a + b;
}

const memoizedAdd = memoize(add);

console.log(memoizedAdd(2, 3)); // Calculating... 5
console.log(memoizedAdd(2, 3)); // 5 from cache
```

Important points:

- Cache key should uniquely represent arguments.
- `JSON.stringify` is simple but not perfect for all cases.
- Be careful with memory usage if cache grows too much.

**Interview Line**

Memoization is implemented by storing previous results in a cache and returning cached results for repeated inputs.

### Q. What is the difference between parameters and arguments?

**Answer:**

Parameters are variables listed in a function definition. Arguments are actual values passed when calling the function.

```js
function greet(name, age) {
  console.log(`${name} is ${age}`);
}

greet("John", 25);
```

Here:

- `name` and `age` are parameters.
- `"John"` and `25` are arguments.

Parameters act like placeholders. Arguments are real values.

**Interview Line**

Parameters are defined in the function declaration, while arguments are values passed during function call.

### Q. What is named function expression?

**Answer:**

A named function expression is a function expression that has its own name.

```js
const factorial = function fact(n) {
  if (n <= 1) return 1;
  return n * fact(n - 1);
};

console.log(factorial(5)); // 120
```

The internal name `fact` is useful for recursion and debugging stack traces.

Important point:

```js
// fact(5); // ReferenceError
```

The name is usually available only inside the function body.

**Interview Line**

A named function expression is a function assigned to a variable but with an internal name useful for recursion and debugging.

### Q. What are higher-order functions used for in real projects?

**Answer:**

Higher-order functions are used heavily in real projects because they make code reusable and composable.

Common real-world uses:

- Array transformations: `map`, `filter`, `reduce`
- Event handlers
- Middleware
- Function decorators
- Retry wrappers
- Debounce/throttle utilities
- Authorization wrappers

Example:

```js
function withLogging(fn) {
  return function (...args) {
    console.log("Function called");
    return fn(...args);
  };
}

const add = (a, b) => a + b;
const loggedAdd = withLogging(add);

console.log(loggedAdd(2, 3)); // 5
```

**Interview Line**

Higher-order functions are used to reuse behavior by accepting or returning functions.

### Q. What is function composition?

**Answer:**

Function composition means combining multiple small functions to create a new function.

```js
const trim = (str) => str.trim();
const lowercase = (str) => str.toLowerCase();
const removeSpaces = (str) => str.replace(/\s+/g, "-");

const slugify = (str) => removeSpaces(lowercase(trim(str)));

console.log(slugify(" Hello World ")); // hello-world
```

It helps keep functions small, reusable, and testable.

A generic compose function:

```js
const compose =
  (...fns) =>
  (value) => {
    return fns.reduceRight((acc, fn) => fn(acc), value);
  };

const slug = compose(removeSpaces, lowercase, trim);

console.log(slug(" Hello World ")); // hello-world
```

**Interview Line**

Function composition builds complex logic by combining small reusable functions.

## Closures

### Q. What is a closure?

**Answer:**

A closure is a function that remembers and can access variables from its lexical scope even after the outer function has finished execution.

### Q. Why are closures useful?

**Answer:**

Closures enable state persistence, data encapsulation, and functional patterns without using global variables.

### Q. Real-world use cases of closures

**Answer:**

- Data privacy / encapsulation
- Event handlers
- Callbacks and async operations
- Function factories
- Memoization
- State management

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

### Q. How does closure work internally?

**Answer:**

Internally, a closure is created when a function keeps access to variables from its lexical environment even after the outer function has finished execution.

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

When `outer()` finishes, its execution context is removed from the call stack. But `inner()` still references `count`, so JavaScript keeps that variable in memory.

This preserved environment is the closure.

**Interview Line**

A closure works because the inner function keeps a reference to its outer lexical environment.

### Q. What is the practical use of closure in JavaScript applications?

**Answer:**

Closures are used in JavaScript applications to preserve state and hide private data.

Practical use cases:

- Private variables
- Counter functions
- Debounce and throttle
- Memoization
- Event handlers
- Module pattern
- Function factories

Example:

```js
function createCounter() {
  let count = 0;

  return {
    increment() {
      count++;
      return count;
    },
    getCount() {
      return count;
    },
  };
}

const counter = createCounter();

console.log(counter.increment()); // 1
console.log(counter.getCount()); // 1
```

The `count` variable cannot be accessed directly from outside.

**Interview Line**

Closures are useful for private state, reusable logic, and maintaining data without global variables.

### Q. How can closures be used to create private variables?

**Answer:**

Closures can create private variables by keeping data inside an outer function and exposing controlled methods.

```js
function createUser(name) {
  let password = "secret";

  return {
    getName() {
      return name;
    },
    checkPassword(input) {
      return input === password;
    },
  };
}

const user = createUser("John");

console.log(user.getName()); // John
console.log(user.password); // undefined
console.log(user.checkPassword("secret")); // true
```

Here, `password` is private because it exists only inside `createUser`. The returned methods can access it because of closure.

**Interview Line**

Closures hide variables inside a function scope and expose only controlled access methods.

### Q. How can closures cause memory leaks?

**Answer:**

Closures can cause memory leaks when they keep references to large objects or DOM elements that are no longer needed.

```js
function createHandler() {
  const largeData = new Array(1000000).fill("data");

  return function handler() {
    console.log(largeData.length);
  };
}

const handler = createHandler();
```

As long as `handler` exists, `largeData` cannot be garbage collected because the closure still references it.

Common causes:

- Closures holding large arrays or objects
- Event listeners not removed
- Timers using closed-over variables
- Detached DOM nodes referenced by closures

**Interview Line**

Closures can leak memory when they keep unnecessary references alive after they are no longer needed.

### Q. How do you avoid memory leaks caused by closures?

**Answer:**

To avoid memory leaks caused by closures, release references when they are no longer needed.

Best practices:

1. Remove unused event listeners.
2. Clear timers and intervals.
3. Avoid closing over large objects unnecessarily.
4. Set references to `null` when cleanup is needed.
5. Keep closure scope small.
6. Use cleanup functions in frameworks like React.

Example:

```js
function setup() {
  const button = document.querySelector("button");

  function handleClick() {
    console.log("clicked");
  }

  button.addEventListener("click", handleClick);

  return function cleanup() {
    button.removeEventListener("click", handleClick);
  };
}

const cleanup = setup();

// Later
cleanup();
```

**Interview Line**

Avoid closure leaks by cleaning up listeners, timers, and unnecessary references.

### Q. What is the difference between closure and callback?

**Answer:**

A callback is a function passed to another function to be executed later. A closure is a function that remembers variables from its lexical scope.

```js
function outer(message) {
  return function callback() {
    console.log(message);
  };
}

setTimeout(outer("Hello"), 1000);
```

Here, the returned function is both:

- A callback because it is passed to `setTimeout`
- A closure because it remembers `message`

| Closure                   | Callback                        |
| ------------------------- | ------------------------------- |
| Remembers outer variables | Passed to another function      |
| Related to scope          | Related to execution timing     |
| May or may not be async   | Often used in async/event logic |

**Interview Line**

A callback is about passing functions; a closure is about preserving lexical scope.

### Q. Explain closure using a counter example.

**Answer:**

A closure counter keeps the `count` variable private and remembers it between function calls.

```js
function createCounter() {
  let count = 0;

  return function increment() {
    count++;
    return count;
  };
}

const counter = createCounter();

console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3
```

`count` is not available globally, but the inner function can still access it because of closure.

**Interview Line**

A closure counter works because the inner function remembers the outer `count` variable.

### Q. Explain closure using a once function.

**Answer:**

A `once` function ensures that a function runs only one time.

```js
function once(fn) {
  let called = false;
  let result;

  return function (...args) {
    if (!called) {
      called = true;
      result = fn.apply(this, args);
    }

    return result;
  };
}

const initialize = once(function () {
  console.log("Initialized");
  return true;
});

initialize(); // Initialized
initialize(); // No output
```

The variables `called` and `result` are preserved using closure.

Use cases:

- App initialization
- Event handlers that should run once
- Payment or submit protection

**Interview Line**

`once` uses closure to remember whether the function has already been executed.

### Q. What will be the output of closure inside a loop using `var`?

**Answer:**

When `var` is used inside a loop, it has function scope, not block scope. All callbacks share the same variable.

```js
for (var i = 1; i <= 3; i++) {
  setTimeout(function () {
    console.log(i);
  }, 1000);
}
```

Output:

```js
4;
4;
4;
```

By the time the callbacks run, the loop has finished and `i` is `4`.

Fix using `let`:

```js
for (let i = 1; i <= 3; i++) {
  setTimeout(function () {
    console.log(i);
  }, 1000);
}
```

Output:

```js
1;
2;
3;
```

**Interview Line**

With `var`, all loop callbacks share the same variable, so they print the final value.

### Q. How does `let` solve closure issues inside loops?

**Answer:**

`let` solves closure issues in loops because it creates a new block-scoped variable for each loop iteration.

```js
for (let i = 1; i <= 3; i++) {
  setTimeout(function () {
    console.log(i);
  }, 1000);
}
```

Output:

```js
1;
2;
3;
```

Each callback closes over a different `i`.

With `var`, there is only one shared `i`.

```js
for (var i = 1; i <= 3; i++) {
  setTimeout(() => console.log(i), 1000);
}
```

Output:

```js
4;
4;
4;
```

**Interview Line**

`let` creates a fresh binding for each loop iteration, so closures capture the correct value.

### Q. How are closures used in debounce and throttle?

**Answer:**

Closures are used in debounce and throttle to remember timer or execution state between function calls.

Debounce example:

```js
function debounce(fn, delay) {
  let timer;

  return function (...args) {
    clearTimeout(timer);

    timer = setTimeout(() => {
      fn.apply(this, args);
    }, delay);
  };
}
```

The returned function remembers `timer` through closure.

Throttle example:

```js
function throttle(fn, limit) {
  let waiting = false;

  return function (...args) {
    if (!waiting) {
      fn.apply(this, args);
      waiting = true;

      setTimeout(() => {
        waiting = false;
      }, limit);
    }
  };
}
```

The returned function remembers `waiting`.

**Interview Line**

Debounce and throttle use closures to persist timer or execution state across calls.

### Q. How are closures used in module patterns?

**Answer:**

Closures are used in the module pattern to create private variables and expose only selected methods.

```js
const counterModule = (function () {
  let count = 0;

  return {
    increment() {
      count++;
      return count;
    },
    reset() {
      count = 0;
    },
  };
})();

console.log(counterModule.increment()); // 1
console.log(counterModule.count); // undefined
```

The `count` variable is private because it is inside the IIFE. The returned object methods can access it using closure.

**Interview Line**

Closures power the module pattern by keeping private variables hidden inside a function scope.

### Q. How do closures help in maintaining state without global variables?

**Answer:**

Closures maintain state without global variables by keeping data inside a function scope.

```js
function createCart() {
  const items = [];

  return {
    add(item) {
      items.push(item);
    },
    getItems() {
      return [...items];
    },
  };
}

const cart = createCart();

cart.add("Phone");
console.log(cart.getItems()); // ["Phone"]
```

The `items` array is not global and cannot be modified directly from outside.

This reduces bugs because state is controlled through specific methods.

**Interview Line**

Closures allow private state to persist without polluting the global scope.

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

### What is `this` keyword?

**Answer:**

`this` refers to the object that is currently calling the function.

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

### How does `this` work in arrow functions?

**Answer:**

Arrow functions do not have their own `this`.

They inherit `this` from their lexical scope.

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

### `Prototype` vs `**proto**`

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

### `Classical` vs `Prototypal` inheritance

**Answer:**

| Classical         | Prototypal         |
| ----------------- | ------------------ |
| Class-based       | Object-based       |
| Used in Java, C++ | Used in JavaScript |
| Rigid hierarchy   | Flexible           |
| Requires classes  | No classes needed  |

### What is `Object.create()`?

**Answer:**

Creates a new object with the specified object as its prototype.

```js
var parent = { greet: "hi" };
var child = Object.create(parent);
```

Use case:

When you want pure inheritance without constructor functions.

### What is `hasOwnProperty()`?

**Answer:**

Checks if a property belongs directly to the object, not inherited.

```js
obj.hasOwnProperty("name");
```

Why important:

Avoid accessing prototype properties unintentionally.

### Difference between `Object.freeze()` and `Object.seal()`

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

### What is `new` keyword?

**Answer:**

`new` creates an instance from a constructor function.

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

### Q. What is the prototype chain?

**Answer:**

The prototype chain is the chain of objects JavaScript follows when looking for a property or method.

```js
const parent = {
  greet() {
    return "Hello";
  },
};

const child = Object.create(parent);

console.log(child.greet()); // Hello
```

`child` does not have `greet`, so JavaScript looks at its prototype `parent`.

Lookup flow:

```txt
child → parent → Object.prototype → null
```

If the property is not found anywhere in the chain, JavaScript returns `undefined`.

**Interview Line**

The prototype chain is JavaScript’s mechanism for property lookup and inheritance.

### Q. What happens when JavaScript cannot find a property on an object?

**Answer:**

When JavaScript cannot find a property directly on an object, it searches the object’s prototype chain.

```js
const parent = { role: "admin" };
const user = Object.create(parent);

console.log(user.role); // admin
```

If the property is not found on the object, JavaScript checks its prototype, then the prototype’s prototype, and so on.

If the property is still not found, it returns `undefined`.

```js
console.log(user.name); // undefined
```

**Interview Line**

JavaScript searches up the prototype chain; if the property is not found, it returns `undefined`.

### Q. Difference between own property and inherited property

**Answer:**

An own property belongs directly to the object. An inherited property comes from the prototype chain.

```js
const parent = {
  role: "admin",
};

const user = Object.create(parent);
user.name = "John";

console.log(user.name); // own property
console.log(user.role); // inherited property
```

Check own property:

```js
console.log(Object.hasOwn(user, "name")); // true
console.log(Object.hasOwn(user, "role")); // false
```

Older syntax:

```js
user.hasOwnProperty("name");
```

**Interview Line**

Own properties exist directly on the object, while inherited properties come from its prototype.

### Q. Difference between `Object.keys()`, `Object.values()`, and `Object.entries()`

**Answer:**

`Object.keys()`, `Object.values()`, and `Object.entries()` are used to extract object data in array form.

```js
const user = {
  name: "John",
  age: 25,
};

console.log(Object.keys(user)); // ["name", "age"]
console.log(Object.values(user)); // ["John", 25]
console.log(Object.entries(user)); // [["name", "John"], ["age", 25]]
```

| Method             | Returns                       |
| ------------------ | ----------------------------- |
| `Object.keys()`    | Array of keys                 |
| `Object.values()`  | Array of values               |
| `Object.entries()` | Array of `[key, value]` pairs |

They only return own enumerable properties, not inherited ones.

**Interview Line**

`keys` gives property names, `values` gives values, and `entries` gives key-value pairs.

### Q. Difference between `for...in` and `Object.keys()`

**Answer:**

`for...in` loops over enumerable properties, including inherited enumerable properties. `Object.keys()` returns only own enumerable properties.

```js
const parent = { role: "admin" };
const user = Object.create(parent);

user.name = "John";

for (let key in user) {
  console.log(key); // name, role
}

console.log(Object.keys(user)); // ["name"]
```

To use `for...in` safely:

```js
for (let key in user) {
  if (Object.hasOwn(user, key)) {
    console.log(key);
  }
}
```

**Interview Line**

`for...in` can include inherited properties, while `Object.keys()` returns only own enumerable properties.

### Q. Difference between `Object.assign()` and spread operator for object cloning

**Answer:**

Both `Object.assign()` and spread operator create shallow copies of objects.

```js
const user = { name: "John", age: 25 };

const copy1 = Object.assign({}, user);
const copy2 = { ...user };
```

Both copy only the first level.

```js
const obj = {
  name: "John",
  address: { city: "Mumbai" },
};

const copy = { ...obj };

copy.address.city = "Delhi";

console.log(obj.address.city); // Delhi
```

Main differences:

| Feature        | `Object.assign()`          | Spread                     |
| -------------- | -------------------------- | -------------------------- |
| Syntax         | Function call              | Cleaner syntax             |
| Mutates target | Yes                        | Creates new object literal |
| Common use     | Merge into existing object | Create new object          |
| Shallow copy   | Yes                        | Yes                        |

**Interview Line**

Both create shallow copies, but spread is cleaner while `Object.assign()` can mutate a target object.

### Q. What is the limitation of shallow copying?

**Answer:**

The main limitation of shallow copying is that nested objects are still shared by reference.

```js
const user = {
  name: "John",
  address: {
    city: "Mumbai",
  },
};

const copy = { ...user };

copy.address.city = "Delhi";

console.log(user.address.city); // Delhi
```

Only the top-level object is copied. The nested `address` object is still the same reference.

This can cause unexpected mutation bugs in state management and React applications.

Use deep cloning when nested data should be independent.

```js
const deepCopy = structuredClone(user);
```

**Interview Line**

Shallow copy copies only the first level; nested objects remain shared references.

### Q. How does `structuredClone()` work?

**Answer:**

`structuredClone()` creates a deep copy of many JavaScript values.

```js
const user = {
  name: "John",
  address: {
    city: "Mumbai",
  },
};

const copy = structuredClone(user);

copy.address.city = "Delhi";

console.log(user.address.city); // Mumbai
```

Unlike `JSON.parse(JSON.stringify())`, `structuredClone()` supports many complex types like:

- Objects
- Arrays
- Dates
- Maps
- Sets
- Typed arrays

Limitations:

- Cannot clone functions
- Cannot clone DOM nodes
- Throws error for unsupported values

**Interview Line**

`structuredClone()` is a modern built-in way to deep clone structured data safely.

### Q. Difference between `Object.freeze()`, `Object.seal()`, and `Object.preventExtensions()`

**Answer:**

`Object.freeze()`, `Object.seal()`, and `Object.preventExtensions()` restrict object modifications at different levels.

```js
const obj = { name: "John" };
```

| Method                       | Add property | Delete property | Modify existing value |
| ---------------------------- | ------------ | --------------- | --------------------- |
| `Object.preventExtensions()` | No           | Yes             | Yes                   |
| `Object.seal()`              | No           | No              | Yes                   |
| `Object.freeze()`            | No           | No              | No                    |

Example:

```js
const user = { name: "John" };

Object.freeze(user);

user.name = "Amit"; // ignored or error in strict mode
console.log(user.name); // John
```

Important: These methods are shallow. Nested objects can still be changed unless frozen separately.

**Interview Line**

`preventExtensions` blocks adding, `seal` blocks adding/deleting, and `freeze` blocks adding/deleting/modifying.

### Q. What are property descriptors?

**Answer:**

Property descriptors define the behavior of object properties.

A property descriptor can include:

- `value`
- `writable`
- `enumerable`
- `configurable`
- `get`
- `set`

Example:

```js
const user = {};

Object.defineProperty(user, "name", {
  value: "John",
  writable: false,
  enumerable: true,
  configurable: false,
});

console.log(user.name); // John
```

Here, `name` cannot be changed because `writable` is `false`.

Property descriptors help control how object properties behave.

**Interview Line**

Property descriptors define whether a property can be changed, listed, deleted, or accessed through getters/setters.

### Q. What is `Object.defineProperty()`?

**Answer:**

`Object.defineProperty()` is used to add or modify a property with specific descriptors.

```js
const user = {};

Object.defineProperty(user, "id", {
  value: 101,
  writable: false,
  enumerable: true,
  configurable: false,
});

console.log(user.id); // 101

user.id = 202;
console.log(user.id); // 101
```

It is useful when you need fine control over property behavior.

You can also define getters and setters:

```js
const person = {
  firstName: "John",
  lastName: "Doe",
};

Object.defineProperty(person, "fullName", {
  get() {
    return `${this.firstName} ${this.lastName}`;
  },
});

console.log(person.fullName); // John Doe
```

**Interview Line**

`Object.defineProperty()` lets us define properties with controlled behavior using descriptors.

### Q. What are getter and setter methods?

**Answer:**

Getter and setter methods allow controlled access to object properties.

```js
const user = {
  firstName: "John",
  lastName: "Doe",

  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  },

  set fullName(value) {
    const [first, last] = value.split(" ");
    this.firstName = first;
    this.lastName = last;
  },
};

console.log(user.fullName); // John Doe

user.fullName = "Amit Sharma";

console.log(user.firstName); // Amit
console.log(user.lastName); // Sharma
```

Getters are used to compute values. Setters are used to validate or transform data before assigning.

**Interview Line**

Getters read computed values, while setters control how values are assigned.

### Q. What is the difference between enumerable and non-enumerable properties?

**Answer:**

Enumerable properties appear during object iteration methods like `Object.keys()` and `for...in`. Non-enumerable properties do not.

```js
const user = {
  name: "John",
};

Object.defineProperty(user, "secret", {
  value: "hidden",
  enumerable: false,
});

console.log(Object.keys(user)); // ["name"]
console.log(user.secret); // hidden
```

The property exists, but it does not appear in normal enumeration.

Common examples of non-enumerable properties are many built-in methods on prototypes.

**Interview Line**

Enumerable properties show up in iteration; non-enumerable properties exist but are hidden from enumeration.

### Q. What is the difference between prototype and class?

**Answer:**

A prototype is the actual inheritance mechanism in JavaScript. A class is cleaner syntax built on top of prototypes.

Prototype example:

```js
function User(name) {
  this.name = name;
}

User.prototype.greet = function () {
  return `Hello ${this.name}`;
};
```

Class example:

```js
class User {
  constructor(name) {
    this.name = name;
  }

  greet() {
    return `Hello ${this.name}`;
  }
}
```

Both use prototypes internally.

| Prototype                     | Class                          |
| ----------------------------- | ------------------------------ |
| Original JS inheritance model | ES6 syntax                     |
| More manual                   | Cleaner and readable           |
| Function-based                | Class-like syntax              |
| Actual mechanism              | Syntactic sugar over prototype |

**Interview Line**

Classes are syntactic sugar over JavaScript’s prototype-based inheritance.

### Q. Are JavaScript classes truly classes?

**Answer:**

JavaScript classes are not traditional classes like Java or C++. They are syntactic sugar over prototype-based inheritance.

```js
class User {
  constructor(name) {
    this.name = name;
  }

  greet() {
    return `Hello ${this.name}`;
  }
}

console.log(typeof User); // function
```

Internally, methods are added to `User.prototype`.

```js
const user = new User("John");

console.log(user.__proto__ === User.prototype); // true
```

So JavaScript still uses prototypes behind the scenes.

**Interview Line**

JavaScript classes look like traditional classes, but internally they still use prototypes.

### Q. What happens internally when we use the `new` keyword?

**Answer:**

When we use the `new` keyword, JavaScript performs four steps.

```js
function User(name) {
  this.name = name;
}

const user = new User("John");
```

Internally:

1. Creates a new empty object.
2. Links the object to the constructor’s prototype.
3. Binds `this` inside the constructor to the new object.
4. Returns the object automatically, unless the constructor explicitly returns another object.

Conceptually:

```js
const obj = {};
obj.__proto__ = User.prototype;
User.call(obj, "John");
```

Result:

```js
console.log(user.name); // John
```

**Interview Line**

`new` creates an object, links its prototype, binds `this`, and returns the object.

### Q. How can you create inheritance without using class?

**Answer:**

In JavaScript, inheritance can be created without using the `class` keyword because JavaScript is prototype-based internally.

Before ES6 classes, inheritance was commonly created using:

1. Constructor functions
2. `prototype`
3. `Object.create()`

JavaScript objects can inherit directly from other objects through the prototype chain.

#### 1. Inheritance using `Object.create()`

`Object.create()` creates a new object and sets another object as its prototype.

Example:

```js
const animal = {
  eat() {
    console.log("Animal is eating");
  },
};

const dog = Object.create(animal);

dog.bark = function () {
  console.log("Dog is barking");
};

dog.eat(); // Animal is eating
dog.bark(); // Dog is barking
```

Here, `dog` does not have the `eat()` method directly. JavaScript looks for `eat()` on `dog`, does not find it, and then checks its prototype `animal`.

So `dog` inherits from `animal`.

#### 2. Inheritance using constructor functions

Before ES6 classes, constructor functions were used to create reusable object blueprints.

Example:

```js
function Animal(name) {
  this.name = name;
}

Animal.prototype.eat = function () {
  console.log(`${this.name} is eating`);
};

function Dog(name, breed) {
  Animal.call(this, name);
  this.breed = breed;
}

Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

Dog.prototype.bark = function () {
  console.log(`${this.name} is barking`);
};

const dog1 = new Dog("Tommy", "Labrador");

dog1.eat(); // Tommy is eating
dog1.bark(); // Tommy is barking
```

#### Explanation

```js
Animal.call(this, name);
```

This calls the `Animal` constructor inside `Dog`, so `Dog` objects can get properties from `Animal`.

```js
Dog.prototype = Object.create(Animal.prototype);
```

This connects `Dog.prototype` to `Animal.prototype`, so `Dog` instances can access methods from `Animal`.

```js
Dog.prototype.constructor = Dog;
```

This resets the constructor reference back to `Dog`.

#### Prototype Chain

For the above example, the prototype chain looks like this:

```txt
dog1 → Dog.prototype → Animal.prototype → Object.prototype → null
```

#### **Interview Line**

Inheritance without classes can be created using constructor functions, prototypes, and `Object.create()`. ES6 classes are just cleaner syntax over JavaScript’s prototype-based inheritance.

### Q. What is constructor function?

**Answer:**

A constructor function is a normal JavaScript function used to create multiple objects with the same structure.

Constructor functions were commonly used before ES6 classes.

By convention, constructor function names start with a capital letter.

Example:

```js
function User(name, age) {
  this.name = name;
  this.age = age;
}

const user1 = new User("John", 25);
const user2 = new User("Amit", 30);

console.log(user1.name); // John
console.log(user2.name); // Amit
```

Here, `User` is a constructor function.

When we call it with the `new` keyword, JavaScript creates a new object.

#### What happens internally with `new`?

When we write:

```js
const user1 = new User("John", 25);
```

JavaScript internally does these steps:

1. Creates a new empty object.
2. Sets the prototype of the new object to `User.prototype`.
3. Binds `this` inside the constructor to the new object.
4. Executes the constructor function.
5. Returns the new object automatically.

Conceptually:

```js
const user1 = {};
user1.__proto__ = User.prototype;
User.call(user1, "John", 25);
```

#### Adding methods using prototype

If we define methods inside the constructor, a new copy of the method is created for every object.

Bad approach:

```js
function User(name) {
  this.name = name;

  this.sayHello = function () {
    console.log(`Hello ${this.name}`);
  };
}
```

Better approach:

```js
function User(name) {
  this.name = name;
}

User.prototype.sayHello = function () {
  console.log(`Hello ${this.name}`);
};

const user1 = new User("John");
const user2 = new User("Amit");

user1.sayHello(); // Hello John
user2.sayHello(); // Hello Amit
```

Here, `sayHello()` is shared by all instances through the prototype.

#### Why constructor functions are useful

Constructor functions are useful because they allow us to:

- Create multiple objects with the same structure
- Reuse methods using prototype
- Implement inheritance before ES6 classes
- Organize object creation logic

#### Important Point

A constructor function should be called with `new`.

Without `new`:

```js
function User(name) {
  this.name = name;
}

const user = User("John");

console.log(user); // undefined
```

In non-strict mode, `this` may point to the global object, which can create bugs.

#### **Interview Line**

A constructor function is a function used with the `new` keyword to create object instances. It initializes object properties and shares methods using its prototype.

### Q. Difference between constructor function and ES6 class

**Answer:**

Constructor functions and ES6 classes are both used to create objects and implement inheritance in JavaScript.

ES6 classes provide a cleaner and more readable syntax, but internally JavaScript still uses prototypes.

#### Constructor Function Example

```js
function User(name) {
  this.name = name;
}

User.prototype.sayHello = function () {
  console.log(`Hello ${this.name}`);
};

const user1 = new User("John");

user1.sayHello(); // Hello John
```

#### ES6 Class Example

```js
class User {
  constructor(name) {
    this.name = name;
  }

  sayHello() {
    console.log(`Hello ${this.name}`);
  }
}

const user1 = new User("John");

user1.sayHello(); // Hello John
```

Both examples work similarly.

#### Difference Table

| Constructor Function                    | ES6 Class                                                       |
| --------------------------------------- | --------------------------------------------------------------- |
| Older way to create objects             | Modern ES6 syntax                                               |
| Uses normal function syntax             | Uses `class` keyword                                            |
| Methods are manually added to prototype | Methods are automatically added to prototype                    |
| Can be called without `new`             | Cannot be called without `new`                                  |
| Function declarations are hoisted       | Class declarations are not usable before declaration due to TDZ |
| Inheritance is more verbose             | Inheritance is cleaner using `extends` and `super`              |
| Less strict by default                  | Class body runs in strict mode automatically                    |

#### Calling without `new`

Constructor function:

```js
function User(name) {
  this.name = name;
}

User("John"); // Possible, but can cause bugs
```

ES6 class:

```js
class User {
  constructor(name) {
    this.name = name;
  }
}

User("John"); // TypeError: Class constructor User cannot be invoked without 'new'
```

Classes are safer because they must be called with `new`.

#### Inheritance using constructor function

```js
function Animal(name) {
  this.name = name;
}

Animal.prototype.eat = function () {
  console.log(`${this.name} is eating`);
};

function Dog(name) {
  Animal.call(this, name);
}

Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;
```

#### Inheritance using ES6 class

```js
class Animal {
  constructor(name) {
    this.name = name;
  }

  eat() {
    console.log(`${this.name} is eating`);
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name);
    this.breed = breed;
  }
}
```

The class version is easier to read and maintain.

#### Important Interview Point

ES6 classes are not the same as traditional classes in languages like Java or C++.

They are mostly syntactic sugar over JavaScript’s prototype-based inheritance.

Example:

```js
class User {
  sayHello() {
    console.log("Hello");
  }
}

console.log(typeof User); // function
```

A class in JavaScript is still a special type of function internally.

#### **Interview Line**

Constructor functions are the older prototype-based way to create objects, while ES6 classes provide cleaner syntax over the same prototype-based inheritance model.

### Q. What is the difference between `__proto__` and `Object.getPrototypeOf()`?

**Answer:**

Both `__proto__` and `Object.getPrototypeOf()` are used to access the prototype of an object.

However, `Object.getPrototypeOf()` is the standard and recommended way, while `__proto__` is older and should generally be avoided in modern code.

#### `__proto__`

`__proto__` is an accessor property that points to the prototype of an object.

Example:

```js
const animal = {
  eat() {
    console.log("Eating");
  },
};

const dog = Object.create(animal);

console.log(dog.__proto__ === animal); // true
```

Here, `dog.__proto__` points to `animal`.

#### `Object.getPrototypeOf()`

`Object.getPrototypeOf()` is a built-in method used to get the prototype of an object.

Example:

```js
const animal = {
  eat() {
    console.log("Eating");
  },
};

const dog = Object.create(animal);

console.log(Object.getPrototypeOf(dog) === animal); // true
```

This gives the same result but in a standard and safer way.

#### Difference Table

| `__proto__`                          | `Object.getPrototypeOf()`      |
| ------------------------------------ | ------------------------------ |
| Older accessor property              | Standard built-in method       |
| Used to get or set prototype         | Used to get prototype          |
| Can be slower and unsafe if modified | Safer and recommended          |
| Not preferred in production code     | Preferred in modern JavaScript |
| Can make code less clear             | More explicit and readable     |

#### Example with constructor function

```js
function User(name) {
  this.name = name;
}

const user1 = new User("John");

console.log(user1.__proto__ === User.prototype); // true
console.log(Object.getPrototypeOf(user1) === User.prototype); // true
```

Both show that the prototype of `user1` is `User.prototype`.

#### Setting prototype

`__proto__` can also be used to set the prototype, but this is not recommended.

```js
const parent = { role: "admin" };
const child = {};

child.__proto__ = parent;

console.log(child.role); // admin
```

Recommended alternative:

```js
const parent = { role: "admin" };
const child = Object.create(parent);

console.log(child.role); // admin
```

If you need to set an existing object’s prototype, use:

```js
Object.setPrototypeOf(child, parent);
```

But even `Object.setPrototypeOf()` should be used carefully because changing prototypes at runtime can affect performance.

#### **Interview Line**

`__proto__` is an older accessor for an object’s prototype, while `Object.getPrototypeOf()` is the standard and recommended method to read an object’s prototype.

### Q. Why should we avoid directly modifying `__proto__`?

**Answer:**

We should avoid directly modifying `__proto__` because it can cause performance issues, security problems, and unexpected behavior in JavaScript applications.

`__proto__` controls the prototype chain of an object. Changing it at runtime changes how JavaScript searches for properties on that object.

Example:

```js
const parent = {
  role: "admin",
};

const user = {
  name: "John",
};

user.__proto__ = parent;

console.log(user.role); // admin
```

This works, but it is not recommended.

#### 1. It can hurt performance

JavaScript engines optimize objects based on their structure.

When we change an object’s prototype dynamically, the engine may lose those optimizations.

Example:

```js
const user = {
  name: "John",
};

user.__proto__ = {
  role: "admin",
};
```

This can make property lookup slower because the engine has to recalculate the prototype chain.

#### 2. It can create unexpected behavior

Changing `__proto__` affects property lookup.

Example:

```js
const user = {
  name: "John",
};

user.__proto__ = {
  isAdmin: true,
};

console.log(user.isAdmin); // true
```

Now `user` appears to have `isAdmin`, even though it is not its own property.

This can make debugging difficult.

#### 3. It can cause security issues

Direct prototype modification can lead to prototype pollution.

If user-controlled data modifies `__proto__`, it can affect many objects in the application.

Example:

```js
const payload = JSON.parse('{ "__proto__": { "isAdmin": true } }');

const user = {};

Object.assign(user, payload);

console.log(user.isAdmin); // may become true in unsafe cases
```

This can be dangerous if the application checks properties like `isAdmin`.

#### 4. Better alternatives exist

Instead of modifying `__proto__`, create objects with the correct prototype from the beginning.

Recommended:

```js
const parent = {
  greet() {
    console.log("Hello");
  },
};

const child = Object.create(parent);
```

This is cleaner and safer.

If you must read the prototype:

```js
Object.getPrototypeOf(child);
```

If you must set the prototype:

```js
Object.setPrototypeOf(child, parent);
```

But even `Object.setPrototypeOf()` should be used carefully.

#### Best Practice

Avoid this:

```js
obj.__proto__ = anotherObj;
```

Prefer this:

```js
const obj = Object.create(anotherObj);
```

#### **Interview Line**

We should avoid directly modifying `__proto__` because it can hurt performance, create confusing behavior, and introduce security risks like prototype pollution.

### Q. What is prototype pollution?

**Answer:**

Prototype pollution is a security vulnerability where an attacker modifies the prototype of built-in JavaScript objects, usually `Object.prototype`.

Because many objects inherit from `Object.prototype`, changing it can affect many objects across the application.

#### Simple Example

```js
Object.prototype.isAdmin = true;

const user = {
  name: "John",
};

console.log(user.isAdmin); // true
```

Here, `user` does not have its own `isAdmin` property. But because it inherits from `Object.prototype`, JavaScript finds `isAdmin` in the prototype chain.

This is dangerous.

#### How prototype pollution can happen

Prototype pollution often happens when an application blindly merges user input into an object.

Example:

```js
const payload = {
  __proto__: {
    isAdmin: true,
  },
};

const user = {};

Object.assign(user, payload);
```

In unsafe cases, this can modify the prototype and make `isAdmin` available on other objects.

Another example:

```js
function merge(target, source) {
  for (let key in source) {
    target[key] = source[key];
  }
}

const maliciousInput = JSON.parse('{ "__proto__": { "isAdmin": true } }');

merge({}, maliciousInput);

console.log({}.isAdmin); // true in vulnerable implementations
```

If the merge function does not block dangerous keys like `__proto__`, `constructor`, or `prototype`, it may pollute the prototype chain.

#### Why prototype pollution is dangerous

Prototype pollution can cause serious issues such as:

- Privilege escalation
- Bypassing authorization checks
- Unexpected application behavior
- Denial of service
- Data corruption
- Security vulnerabilities in backend or frontend apps

Example:

```js
const user = {
  name: "John",
};

if (user.isAdmin) {
  console.log("Allow admin access");
}
```

If `Object.prototype.isAdmin` was polluted, this condition may become true even if the user is not actually an admin.

#### How to prevent prototype pollution

1. Validate user input

Do not blindly trust incoming objects.

```js
if (key === "__proto__" || key === "constructor" || key === "prototype") {
  return;
}
```

2. Use safe merge utilities

Use libraries that protect against prototype pollution and keep dependencies updated.

3. Avoid merging untrusted data directly

Bad:

```js
Object.assign(config, userInput);
```

Better:

```js
const safeConfig = {
  theme: userInput.theme,
  language: userInput.language,
};
```

4. Use `Object.create(null)` for dictionary objects

```js
const dictionary = Object.create(null);

dictionary.name = "John";
```

Objects created with `Object.create(null)` do not inherit from `Object.prototype`.

5. Check own properties only

Use:

```js
Object.hasOwn(user, "isAdmin");
```

or:

```js
Object.prototype.hasOwnProperty.call(user, "isAdmin");
```

Avoid relying on inherited properties for security checks.

Bad:

```js
if (user.isAdmin) {
  // risky
}
```

Better:

```js
if (Object.hasOwn(user, "isAdmin") && user.isAdmin === true) {
  // safer
}
```

#### **Interview Line**

Prototype pollution is a vulnerability where an attacker modifies the prototype chain, usually `Object.prototype`, causing malicious properties to appear on many objects in the application.

## Arrays & Array Methods

### What is an Array in JavaScript?

**Answer:**

An Array in JavaScript is an ordered, zero-indexed collection of values that can store multiple elements (of any type) in a single variable.

```js
const arr = [1, 2, 3];
```

Arrays in JS are:

- Dynamic (size can change)
- Can store mixed data types
- Prototype-based objects

Array Methods (Categorized for Easy Interview Recall)

1️⃣ Mutating Methods (Modify Original Array)

`push()`

Adds element at the end.

```js
arr.push(4);
```

`pop()`

Removes last element.

```js
arr.pop();
```

`unshift()`

Adds element at beginning.

```js
arr.unshift(0);
```

`shift()`

Removes first element.

```js
arr.shift();
```

`splice()`

Add/remove elements at specific index.

```js
arr.splice(1, 2); // remove 2 items from index 1
```

```js
arr.splice(2, 0, "Lemon", "Kiwi");
```

- The first parameter (2) defines the position where new elements should be added (spliced in)
- The second parameter (0) defines how many elements should be removed
- The rest of the parameters ("Lemon" , "Kiwi") define the new elements to be added

`sort()`

Sorts array (mutates original).

```js
arr.sort((a, b) => a - b);
```

`reverse()`

Reverses array.

```js
arr.reverse();
```

2️⃣ Non-Mutating Methods (Return New Array)

`map()`

Transforms each element.

```js
arr.map(x => x \* 2);
```

📌 Returns new array.

`filter()`

Filters elements based on condition.

```js
arr.filter((x) => x > 2);
```

`reduce()`

Reduces array to single value.

```js
arr.reduce((acc, curr) => acc + curr, 0);
```

📌 Very important in interviews.

`slice()`

Extracts part of array.

```js
arr.slice(1, 3);
```

`concat()`

Merges arrays.

```js
arr.concat([5, 6]);
```

`flat()`

Flattens nested arrays.

```js
[1, [2, 3]].flat();
```

3️⃣ Searching Methods

`includes()`

Checks if value exists.

```js
arr.includes(3);
```

`indexOf()`

Returns first index.

```js
arr.indexOf(2);
```

`lastIndexOf()`

Returns last index.

`find()`

Returns first matching element.

```js
arr.find((x) => x > 2);
```

`findIndex()`

Returns index of matching element.

4️⃣ Iteration Methods

`forEach()`

Loops through array.

```js
arr.forEach((x) => console.log(x));
```

❌ Does not return new array.

`some()`

Returns true if at least one matches.

```js
arr.some((x) => x > 5);
```

`every()`

Returns true if all match.

```js
arr.every((x) => x > 0);
```

5️⃣ Conversion Methods

`join()`

Converts array to string.

```js
arr.join("-");
```

`toString()`

Converts to string.

`Array.from()`

Creates array from iterable.

```js
Array.from("hello");
```

`Array.isArray()`

Checks if value is array.

```js
Array.isArray(arr);
```

6️⃣ New Modern Methods

`at()`

Access element by index (supports negative).

```js
arr.at(-1);
```

`flatMap()`

Map + flatten.

```js
arr.flatMap((x) => [x * 2]);
```

Important Interview Comparison

| Method | Mutates? | Returns New? |
| ------ | -------- | ------------ |
| push   | ✅       | ❌           |
| map    | ❌       | ✅           |
| filter | ❌       | ✅           |
| reduce | ❌       | ✅           |
| splice | ✅       | ❌           |
| slice  | ❌       | ✅           |

Common Interview Questions

- Difference between map() and forEach()
- Difference between slice() and splice()
- Implement reduce()
- How to remove duplicates?
- How to flatten array?

One-Line Interview Summary

“An array in JavaScript is a dynamic, ordered collection of values that provides powerful built-in methods for iteration, transformation, searching, and mutation.”

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

### Difference between `forEach` and `map`

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

### What does `reduce()` do?

**Answer:**

`reduce()` executes a reducer function on each element and returns a single accumulated value.

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

Using `flat()`

```js
var arr = [1, [2, [3]]];
arr.flat(2);
```

Using `reduce()`

```js
arr.reduce((acc, val) => acc.concat(val), []);
```

### Difference between `slice` and `splice`

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

### Difference between `find` and `filter`

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

### What is `some()` and `every()`?

**Answer:**

- `some()` → returns true if at least one element matches
- `every()` → returns true if all elements match

```js
arr.some((x) => x > 5);
arr.every((x) => x > 0);
```

### Difference between `push`, `pop`, `shift`, `unshift`

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

### What is `Array.from()`?

**Answer:**

Creates a new array from:

- Array-like objects
- Iterables (Set, Map, string)

```js
Array.from("hello");
Array.from(new Set([1, 2, 2]));
```

### What is `flatMap()`?

**Answer:**

`flatMap()` maps and flattens one level deep in a single operation.

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

Using spread operator

```js
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

### Q. Difference between `map()` and `flatMap()`

**Answer:**

`map()` transforms each element and returns a new array. `flatMap()` transforms each element and then flattens the result by one level.

```js
const arr = [1, 2, 3];

console.log(arr.map((x) => [x, x * 2]));
// [[1, 2], [2, 4], [3, 6]]

console.log(arr.flatMap((x) => [x, x * 2]));
// [1, 2, 2, 4, 3, 6]
```

`flatMap()` is equivalent to:

```js
arr.map(callback).flat(1);
```

Use `map()` when each input produces one output item. Use `flatMap()` when each input may produce multiple output items.

**Interview Line**

`flatMap()` is `map()` followed by one-level flattening.

### Q. Difference between `find()` and `findIndex()`

**Answer:**

`find()` returns the first matching element. `findIndex()` returns the index of the first matching element.

```js
const users = [
  { id: 1, name: "John" },
  { id: 2, name: "Amit" },
];

const user = users.find((u) => u.id === 2);
console.log(user); // { id: 2, name: "Amit" }

const index = users.findIndex((u) => u.id === 2);
console.log(index); // 1
```

If no match is found:

```js
find(); // undefined
findIndex(); // -1
```

**Interview Line**

`find()` gives the item, while `findIndex()` gives the position of the item.

### Q. Difference between `some()` and `every()`

**Answer:**

`some()` and `every()` are JavaScript array methods used to check conditions on array elements. Both return a Boolean value: `true` or `false`.

The main difference is:

- `some()` checks if **at least one element** satisfies the condition.
- `every()` checks if **all elements** satisfy the condition.

#### 1. `some()`

`some()` returns `true` if **at least one element** in the array passes the given condition.

If no element satisfies the condition, it returns `false`.

**Example:**

```js
const numbers = [1, 2, 3, 4, 5];

const result = numbers.some((num) => num > 3);

console.log(result); // true
```

Here, `4` and `5` are greater than `3`, so `some()` returns `true`.

**Another Example:**

```js
const numbers = [1, 2, 3];

const result = numbers.some((num) => num > 10);

console.log(result); // false
```

No number is greater than `10`, so it returns `false`.

**Real-world use case:**

```js
const users = [
  { name: "Amit", isAdmin: false },
  { name: "Rahul", isAdmin: false },
  { name: "Priya", isAdmin: true },
];

const hasAdmin = users.some((user) => user.isAdmin);

console.log(hasAdmin); // true
```

Here, we are checking if at least one user is an admin.

#### 2. `every()`

`every()` returns `true` only if **all elements** in the array pass the given condition.

If even one element fails the condition, it returns `false`.

**Example:**

```js
const numbers = [2, 4, 6, 8];

const result = numbers.every((num) => num % 2 === 0);

console.log(result); // true
```

All numbers are even, so `every()` returns `true`.

**Another Example:**

```js
const numbers = [2, 4, 5, 8];

const result = numbers.every((num) => num % 2 === 0);

console.log(result); // false
```

Here, `5` is not even, so `every()` returns `false`.

**Real-world use case:**

```js
const formFields = [
  { name: "email", isValid: true },
  { name: "password", isValid: true },
  { name: "username", isValid: true },
];

const isFormValid = formFields.every((field) => field.isValid);

console.log(isFormValid); // true
```

Here, we are checking if all form fields are valid.

#### Difference Table

| Feature              | `some()`                                   | `every()`                                |
| -------------------- | ------------------------------------------ | ---------------------------------------- |
| Meaning              | Checks if at least one element matches     | Checks if all elements match             |
| Return value         | Boolean                                    | Boolean                                  |
| Returns `true` when  | One or more elements satisfy the condition | All elements satisfy the condition       |
| Returns `false` when | No element satisfies the condition         | At least one element fails the condition |
| Stops execution when | It finds the first matching element        | It finds the first failing element       |
| Common use case      | Check if any item exists/matches           | Validate all items                       |

#### Short-circuit behavior

Both `some()` and `every()` use short-circuit evaluation.

#### `some()` stops when it finds `true`

```js
const numbers = [1, 2, 3, 4];

const result = numbers.some((num) => {
  console.log(num);
  return num > 2;
});

console.log(result);
```

**Output:**

```js
1;
2;
3;
true;
```

It stops at `3` because the condition becomes true.

#### `every()` stops when it finds `false`

```js
const numbers = [2, 4, 5, 6];

const result = numbers.every((num) => {
  console.log(num);
  return num % 2 === 0;
});

console.log(result);
```

**Output:**

```js
2;
4;
5;
false;
```

It stops at `5` because the condition becomes false.

#### Practical Examples

**Using `some()` for permission check**

```js
const permissions = ["read", "write"];

const canDelete = permissions.some((permission) => permission === "delete");

console.log(canDelete); // false
```

This checks whether the user has at least one required permission.

**Using `every()` for validation**

```js
const answers = ["Yes", "Yes", "Yes"];

const allAgreed = answers.every((answer) => answer === "Yes");

console.log(allAgreed); // true
```

This checks whether all users agreed.

**Important Point**

For an empty array:

```js
console.log([].some((item) => item > 0)); // false
console.log([].every((item) => item > 0)); // true
```

#### Why?

- `some()` returns `false` because there is no element that satisfies the condition.
- `every()` returns `true` because no element failed the condition.

This behavior can be confusing, so be careful when using `every()` on arrays that may be empty.

**Interview Line**

`some()` returns `true` if at least one array element satisfies the condition, while `every()` returns `true` only if all elements satisfy the condition. Both methods short-circuit once the final result is known.

### Q. Difference between `includes()` and `indexOf()`

**Answer:**

`includes()` checks whether an array contains a value and returns a Boolean. `indexOf()` returns the index of the value.

```js
const arr = [10, 20, 30];

console.log(arr.includes(20)); // true
console.log(arr.indexOf(20)); // 1
```

If value is not found:

```js
arr.includes(50); // false
arr.indexOf(50); // -1
```

Important difference with `NaN`:

```js
const values = [NaN];

console.log(values.includes(NaN)); // true
console.log(values.indexOf(NaN)); // -1
```

**Interview Line**

`includes()` is best for existence checks, while `indexOf()` is useful when you need the index.

### Q. Difference between `slice()` and `splice()`

**Answer:**

`slice()` and `splice()` are JavaScript array methods, but they are used for different purposes.

The main difference is:

- `slice()` is used to **copy/extract** part of an array.
- `splice()` is used to **add, remove, or replace** elements in the original array.

#### 1. `slice()`

`slice()` returns a shallow copy of a portion of an array.

It does **not modify the original array**.

**Syntax:**

```js
array.slice(start, end);
```

- `start` is the index where extraction begins.
- `end` is the index where extraction stops.
- The `end` index is not included.

**Example:**

```js
const numbers = [10, 20, 30, 40, 50];

const result = numbers.slice(1, 4);

console.log(result); // [20, 30, 40]
console.log(numbers); // [10, 20, 30, 40, 50]
```

Here, `slice(1, 4)` extracts elements from index `1` to index `3`.

The original array remains unchanged.

#### 2. `splice()`

`splice()` is used to add, remove, or replace elements in an array.

It **modifies the original array**.

**Syntax:**

```js
array.splice(start, deleteCount, item1, item2, ...);
```

- `start` is the index where changes begin.
- `deleteCount` is the number of elements to remove.
- `item1, item2, ...` are optional elements to add.

#### Removing Elements with `splice()`

```js
const numbers = [10, 20, 30, 40, 50];

const removed = numbers.splice(1, 2);

console.log(removed); // [20, 30]
console.log(numbers); // [10, 40, 50]
```

Here, `splice(1, 2)` starts at index `1` and removes `2` elements.

So `20` and `30` are removed from the original array.

#### Adding Elements with `splice()`

```js
const fruits = ["Apple", "Banana", "Mango"];

fruits.splice(1, 0, "Orange", "Grapes");

console.log(fruits);
// ["Apple", "Orange", "Grapes", "Banana", "Mango"]
```

Here:

```js
fruits.splice(1, 0, "Orange", "Grapes");
```

Means:

- Start at index `1`
- Remove `0` elements
- Add `"Orange"` and `"Grapes"`

#### Replacing Elements with `splice()`

```js
const fruits = ["Apple", "Banana", "Mango"];

fruits.splice(1, 1, "Orange");

console.log(fruits);
// ["Apple", "Orange", "Mango"]
```

Here:

```js
fruits.splice(1, 1, "Orange");
```

Means:

- Start at index `1`
- Remove `1` element
- Add `"Orange"`

So `"Banana"` is replaced with `"Orange"`.

#### Difference Table

| Feature                  | `slice()`                        | `splice()`                          |
| ------------------------ | -------------------------------- | ----------------------------------- |
| Purpose                  | Extracts part of an array        | Adds, removes, or replaces elements |
| Modifies original array? | No                               | Yes                                 |
| Return value             | New array with selected elements | Array of removed elements           |
| Used for                 | Copying or extracting            | Updating original array             |
| Parameters               | `start, end`                     | `start, deleteCount, items`         |
| Safe for immutability?   | Yes                              | No                                  |

**Example Comparison**

```js
const arr = [1, 2, 3, 4, 5];

const sliced = arr.slice(1, 3);

console.log(sliced); // [2, 3]
console.log(arr); // [1, 2, 3, 4, 5]
```

`slice()` does not change the original array.

```js
const arr = [1, 2, 3, 4, 5];

const spliced = arr.splice(1, 3);

console.log(spliced); // [2, 3, 4]
console.log(arr); // [1, 5]
```

`splice()` changes the original array.

#### Negative Index with `slice()`

`slice()` supports negative indexes.

```js
const numbers = [10, 20, 30, 40, 50];

console.log(numbers.slice(-2)); // [40, 50]
```

Here, `-2` means start from the second-last element.

#### Negative Index with `splice()`

`splice()` also supports negative start index.

```js
const numbers = [10, 20, 30, 40, 50];

numbers.splice(-2, 1);

console.log(numbers); // [10, 20, 30, 50]
```

Here, `-2` points to `40`, so `40` is removed.

#### Real-world Use Cases

**Use `slice()` when you want a copy**

```js
const users = ["Amit", "Rahul", "Priya", "Neha"];

const firstTwoUsers = users.slice(0, 2);

console.log(firstTwoUsers); // ["Amit", "Rahul"]
console.log(users); // ["Amit", "Rahul", "Priya", "Neha"]
```

This is useful when you do not want to change the original data.

**Use `splice()` when you want to update the original array**

```js
const todos = ["Learn JS", "Practice React", "Build Project"];

todos.splice(1, 1);

console.log(todos); // ["Learn JS", "Build Project"]
```

This removes `"Practice React"` from the original array.

#### React Important Point

In React, we usually avoid `splice()` directly on state arrays because it mutates the original array.

Bad:

```jsx
const removeItem = (index) => {
  items.splice(index, 1);
  setItems(items);
};
```

This mutates the existing state array.

Better:

```jsx
const removeItem = (index) => {
  const updatedItems = items.filter((_, i) => i !== index);
  setItems(updatedItems);
};
```

Or using `slice()`:

```jsx
const removeItem = (index) => {
  const updatedItems = [...items.slice(0, index), ...items.slice(index + 1)];

  setItems(updatedItems);
};
```

This creates a new array instead of mutating the old one.

**Interview Line**

`slice()` is a non-mutating method used to extract a portion of an array, while `splice()` is a mutating method used to add, remove, or replace elements in the original array.

### Q. Difference between `sort()` and `toSorted()`

**Answer:**

`sort()` sorts the original array and mutates it. `toSorted()` returns a new sorted array without changing the original.

```js
const nums = [3, 1, 2];

const sorted = nums.sort((a, b) => a - b);

console.log(nums); // [1, 2, 3]
console.log(sorted); // [1, 2, 3]
```

Using `toSorted()`:

```js
const nums = [3, 1, 2];

const sorted = nums.toSorted((a, b) => a - b);

console.log(nums); // [3, 1, 2]
console.log(sorted); // [1, 2, 3]
```

Use `toSorted()` when immutability is important, such as in React state updates.

**Interview Line**

`sort()` mutates the array, while `toSorted()` returns a new sorted array.

### Q. Difference between `reverse()` and `toReversed()`

**Answer:**

`reverse()` reverses the original array and mutates it. `toReversed()` returns a new reversed array.

```js
const arr = [1, 2, 3];

const reversed = arr.reverse();

console.log(arr); // [3, 2, 1]
console.log(reversed); // [3, 2, 1]
```

Using `toReversed()`:

```js
const arr = [1, 2, 3];

const reversed = arr.toReversed();

console.log(arr); // [1, 2, 3]
console.log(reversed); // [3, 2, 1]
```

**Interview Line**

`reverse()` mutates, while `toReversed()` keeps the original array unchanged.

### Q. What are mutable and immutable array methods?

**Answer:**

Mutable array methods modify the original array. Immutable methods return a new value without changing the original array.

Mutable methods:

```js
push();
pop();
shift();
unshift();
splice();
sort();
reverse();
fill();
```

Immutable methods:

```js
map();
filter();
reduce();
slice();
concat();
flat();
flatMap();
toSorted();
toReversed();
toSpliced();
```

Example:

```js
const arr = [1, 2, 3];

arr.push(4);
console.log(arr); // [1, 2, 3, 4]
```

Immutable example:

```js
const arr = [1, 2, 3];

const newArr = arr.map((x) => x * 2);

console.log(arr); // [1, 2, 3]
console.log(newArr); // [2, 4, 6]
```

**Interview Line**

Mutable methods change the original array; immutable methods return a new result.

### Q. How do you sort numbers correctly in JavaScript?

**Answer:**

To sort numbers correctly in JavaScript, pass a compare function to `sort()`.

```js
const nums = [10, 2, 5, 1];

nums.sort((a, b) => a - b);

console.log(nums); // [1, 2, 5, 10]
```

Ascending order:

```js
arr.sort((a, b) => a - b);
```

Descending order:

```js
arr.sort((a, b) => b - a);
```

Without a compare function, JavaScript converts values to strings and sorts lexicographically.

**Interview Line**

Always use a numeric comparator like `(a, b) => a - b` when sorting numbers.

### Q. Why does `[10, 2, 5].sort()` give unexpected output?

**Answer:**

`[10, 2, 5].sort()` gives unexpected output because JavaScript sorts elements as strings by default.

```js
const nums = [10, 2, 5];

console.log(nums.sort()); // [10, 2, 5]
```

Internally it compares:

```txt
"10", "2", "5"
```

Since `"10"` comes before `"2"` lexicographically, the result is not numeric order.

Correct way:

```js
nums.sort((a, b) => a - b);

console.log(nums); // [2, 5, 10]
```

**Interview Line**

Default `sort()` performs string-based sorting, so numbers need a compare function.

### Q. How do you group array data by a property?

**Answer:**

You can group array data by a property using `reduce()`.

```js
const users = [
  { name: "John", role: "admin" },
  { name: "Amit", role: "user" },
  { name: "Sara", role: "admin" },
];

const grouped = users.reduce((acc, user) => {
  const key = user.role;

  if (!acc[key]) {
    acc[key] = [];
  }

  acc[key].push(user);
  return acc;
}, {});

console.log(grouped);
```

Output:

```js
{
  admin: [
    { name: "John", role: "admin" },
    { name: "Sara", role: "admin" }
  ],
  user: [
    { name: "Amit", role: "user" }
  ]
}
```

**Interview Line**

Grouping is commonly done with `reduce()` by using the group value as an object key.

### Q. How do you convert an array into an object?

**Answer:**

You can convert an array into an object using `reduce()`.

```js
const users = [
  { id: 1, name: "John" },
  { id: 2, name: "Amit" },
];

const userMap = users.reduce((acc, user) => {
  acc[user.id] = user;
  return acc;
}, {});

console.log(userMap);
```

Output:

```js
{
  1: { id: 1, name: "John" },
  2: { id: 2, name: "Amit" }
}
```

This is useful for quick lookup by ID.

Another way:

```js
const obj = Object.fromEntries(users.map((user) => [user.id, user]));
```

**Interview Line**

Use `reduce()` or `Object.fromEntries()` to convert arrays into object maps.

### Q. How do you remove duplicate objects from an array?

**Answer:**

To remove duplicate objects from an array, use a unique property like `id`.

```js
const users = [
  { id: 1, name: "John" },
  { id: 2, name: "Amit" },
  { id: 1, name: "John" },
];

const uniqueUsers = Array.from(new Map(users.map((user) => [user.id, user])).values());

console.log(uniqueUsers);
```

Output:

```js
[
  { id: 1, name: "John" },
  { id: 2, name: "Amit" },
];
```

Using `filter()`:

```js
const unique = users.filter((user, index, arr) => index === arr.findIndex((u) => u.id === user.id));
```

**Interview Line**

Duplicate objects are usually removed by comparing a stable key like `id`.

### Q. How do you find the frequency of elements in an array?

**Answer:**

You can find the frequency of elements using `reduce()`.

```js
const arr = ["a", "b", "a", "c", "b", "a"];

const frequency = arr.reduce((acc, item) => {
  acc[item] = (acc[item] || 0) + 1;
  return acc;
}, {});

console.log(frequency);
```

Output:

```js
{
  a: 3,
  b: 2,
  c: 1
}
```

This is useful for counting characters, votes, categories, and repeated values.

**Interview Line**

Frequency counting is commonly done with `reduce()` and an object accumulator.

### Q. How do you flatten deeply nested arrays?

**Answer:**

To flatten a deeply nested array, use `flat(Infinity)`.

```js
const arr = [1, [2, [3, [4]]]];

console.log(arr.flat(Infinity)); // [1, 2, 3, 4]
```

Recursive approach:

```js
function deepFlatten(arr) {
  return arr.reduce((acc, item) => {
    if (Array.isArray(item)) {
      acc.push(...deepFlatten(item));
    } else {
      acc.push(item);
    }

    return acc;
  }, []);
}

console.log(deepFlatten([1, [2, [3]]])); // [1, 2, 3]
```

**Interview Line**

Use `flat(Infinity)` for simple cases, or recursion when you need custom flattening logic.

### Q. Difference between `Array.from()` and spread operator

**Answer:**

Both `Array.from()` and the spread operator (`...`) can be used to convert iterable values into arrays, but they are not exactly the same.

#### `Array.from()`

`Array.from()` creates a new array from:

- Iterable objects
- Array-like objects

Example:

```js
const str = "hello";

const result = Array.from(str);

console.log(result); // ["h", "e", "l", "l", "o"]
```

It also works with array-like objects.

```js
const arrayLike = {
  0: "A",
  1: "B",
  length: 2,
};

console.log(Array.from(arrayLike)); // ["A", "B"]
```

#### Spread Operator

The spread operator works only with iterable objects.

Example:

```js
const str = "hello";

const result = [...str];

console.log(result); // ["h", "e", "l", "l", "o"]
```

But it does not work directly with normal array-like objects.

```js
const arrayLike = {
  0: "A",
  1: "B",
  length: 2,
};

console.log([...arrayLike]); // TypeError
```

#### Difference Table

| Feature                       | `Array.from()`                   | Spread Operator            |
| ----------------------------- | -------------------------------- | -------------------------- |
| Works with iterables          | Yes                              | Yes                        |
| Works with array-like objects | Yes                              | No                         |
| Can use mapping function      | Yes                              | No                         |
| Syntax                        | `Array.from(value)`              | `[...value]`               |
| Best use                      | Array-like + iterable conversion | Simple iterable conversion |

#### Mapping with `Array.from()`

```js
const numbers = [1, 2, 3];

const doubled = Array.from(numbers, (num) => num * 2);

console.log(doubled); // [2, 4, 6]
```

#### **Interview Line**

`Array.from()` can convert both iterable and array-like objects into arrays, while the spread operator works only with iterable objects.

### Q. What is an array-like object?

**Answer:**

An array-like object is an object that looks like an array but is not a real array.

It usually has:

- Numeric indexes
- A `length` property

But it does not have array methods like `map()`, `filter()`, `reduce()`, etc.

Example:

```js
const arrayLike = {
  0: "HTML",
  1: "CSS",
  2: "JavaScript",
  length: 3,
};

console.log(arrayLike[0]); // HTML
console.log(arrayLike.length); // 3
```

This object looks like an array because we can access values using indexes, but it is not an actual array.

```js
console.log(Array.isArray(arrayLike)); // false
```

#### Common examples of array-like objects

```js
arguments;
NodeList;
HTMLCollection;
```

Example with `arguments`:

```js
function showArgs() {
  console.log(arguments);
  console.log(Array.isArray(arguments)); // false
}

showArgs(10, 20, 30);
```

#### Converting array-like object to array

```js
const arr = Array.from(arrayLike);

console.log(arr); // ["HTML", "CSS", "JavaScript"]
```

After conversion, we can use array methods.

```js
arr.map((item) => item.toUpperCase());
```

#### **Interview Line**

An array-like object has indexes and a length property like an array, but it is not a real array and does not have array methods.

### Q. How do you convert NodeList to Array?

**Answer:**

A `NodeList` is returned by methods like `document.querySelectorAll()`.

Example:

```js
const items = document.querySelectorAll("li");
```

A NodeList looks like an array, but it may not have all array methods in every environment.

So, we often convert it into a real array.

#### 1. Using `Array.from()`

```js
const items = document.querySelectorAll("li");

const itemsArray = Array.from(items);

itemsArray.map((item) => console.log(item.textContent));
```

This is the most clear and readable way.

#### 2. Using spread operator

```js
const items = document.querySelectorAll("li");

const itemsArray = [...items];

itemsArray.forEach((item) => console.log(item.textContent));
```

This works because `NodeList` returned by `querySelectorAll()` is iterable.

#### 3. Older way using `slice.call()`

```js
const items = document.querySelectorAll("li");

const itemsArray = Array.prototype.slice.call(items);
```

This was commonly used before ES6.

#### Difference

```js
const items = document.querySelectorAll("li");

console.log(Array.isArray(items)); // false

const arr = Array.from(items);

console.log(Array.isArray(arr)); // true
```

#### **Interview Line**

A NodeList can be converted into an array using `Array.from(nodeList)` or `[...nodeList]`, so we can use array methods like `map`, `filter`, and `reduce`.

### Q. What is the difference between sparse array and dense array?

**Answer:**

A dense array is an array where most or all indexes have values.

A sparse array is an array where some indexes are empty or missing.

#### Dense Array

```js
const arr = [10, 20, 30];

console.log(arr.length); // 3
```

Here, all indexes are filled:

```js
0 → 10
1 → 20
2 → 30
```

This is a dense array.

#### Sparse Array

```js
const arr = [10, , 30];

console.log(arr.length); // 3
console.log(arr[1]); // undefined
```

Here, index `1` is empty. It is not the same as explicitly storing `undefined`.

Another example:

```js
const arr = [];

arr[5] = "Hello";

console.log(arr.length); // 6
console.log(arr); // [empty × 5, "Hello"]
```

Indexes `0` to `4` are empty slots.

#### Important Difference

```js
const sparse = [1, , 3];
const dense = [1, undefined, 3];

console.log(1 in sparse); // false
console.log(1 in dense); // true
```

In sparse array, the index does not exist.

In dense array, the index exists but its value is `undefined`.

#### Behavior with array methods

Some array methods skip empty slots.

```js
const arr = [1, , 3];

arr.map((num) => {
  console.log(num);
  return num * 2;
});
```

Output:

```js
1;
3;
```

The empty slot is skipped.

#### **Interview Line**

A dense array has values at its indexes, while a sparse array has missing or empty indexes. Sparse arrays can behave unexpectedly because many array methods skip empty slots.

### Q. What happens if array length is manually changed?

**Answer:**

In JavaScript, the `length` property of an array can be changed manually.

Changing it can either remove elements or create empty slots.

#### Reducing array length

```js
const arr = [10, 20, 30, 40];

arr.length = 2;

console.log(arr); // [10, 20]
```

When we reduce the length, JavaScript removes elements from the end of the array.

Here, `30` and `40` are removed permanently.

#### Increasing array length

```js
const arr = [10, 20];

arr.length = 5;

console.log(arr); // [10, 20, empty × 3]
```

When we increase the length, JavaScript creates empty slots.

These empty slots are not actual `undefined` values.

```js
console.log(arr[3]); // undefined
console.log(3 in arr); // false
```

#### Setting length to zero

```js
const arr = [1, 2, 3];

arr.length = 0;

console.log(arr); // []
```

This is a quick way to clear an array.

#### Important Point

```js
const arr = [1, 2, 3];

arr[10] = 100;

console.log(arr.length); // 11
```

If we assign a value to a higher index, the array length automatically increases.

#### **Interview Line**

If array length is reduced, elements are removed from the end. If length is increased, empty slots are created. Setting length to `0` clears the array.

### Q. How does `reduce()` work internally?

**Answer:**

`reduce()` executes a callback function on each array element and carries an accumulated result.

It reduces an array into a single value.

That single value can be:

- Number
- String
- Object
- Array
- Boolean

#### Syntax

```js
array.reduce((accumulator, currentValue, index, array) => {
  return updatedAccumulator;
}, initialValue);
```

#### Example

```js
const numbers = [1, 2, 3, 4];

const sum = numbers.reduce((acc, curr) => {
  return acc + curr;
}, 0);

console.log(sum); // 10
```

#### Internal flow

For this code:

```js
[1, 2, 3, 4].reduce((acc, curr) => acc + curr, 0);
```

The flow is:

| Step | Accumulator | Current Value | Return |
| ---- | ----------: | ------------: | -----: |
| 1    |           0 |             1 |      1 |
| 2    |           1 |             2 |      3 |
| 3    |           3 |             3 |      6 |
| 4    |           6 |             4 |     10 |

Final result:

```js
10;
```

#### Without initial value

```js
const numbers = [1, 2, 3];

const sum = numbers.reduce((acc, curr) => acc + curr);

console.log(sum); // 6
```

If no initial value is provided, the first element becomes the accumulator and iteration starts from the second element.

Flow:

| Step | Accumulator | Current Value |
| ---- | ----------: | ------------: |
| 1    |           1 |             2 |
| 2    |           3 |             3 |

#### Important Point

For an empty array, `reduce()` without an initial value throws an error.

```js
[].reduce((acc, curr) => acc + curr);
// TypeError
```

Safe way:

```js
[].reduce((acc, curr) => acc + curr, 0);
```

#### **Interview Line**

`reduce()` works by passing an accumulator from one iteration to the next and returning a final accumulated result.

### Q. When should you avoid using `reduce()`?

**Answer:**

`reduce()` is powerful, but it should not be used everywhere.

You should avoid `reduce()` when it makes the code harder to read.

#### 1. Avoid `reduce()` for simple transformations

Bad:

```js
const doubled = numbers.reduce((acc, num) => {
  acc.push(num * 2);
  return acc;
}, []);
```

Better:

```js
const doubled = numbers.map((num) => num * 2);
```

For transformation, `map()` is clearer.

#### 2. Avoid `reduce()` for simple filtering

Bad:

```js
const activeUsers = users.reduce((acc, user) => {
  if (user.isActive) {
    acc.push(user);
  }
  return acc;
}, []);
```

Better:

```js
const activeUsers = users.filter((user) => user.isActive);
```

For filtering, `filter()` is more readable.

#### 3. Avoid complex nested logic inside `reduce()`

```js
const result = data.reduce((acc, item) => {
  // many conditions
  // nested loops
  // mutation
  // complex grouping
  return acc;
}, {});
```

This can become difficult to understand and debug.

In such cases, a normal `for...of` loop may be better.

```js
const result = {};

for (const item of data) {
  // clear step-by-step logic
}
```

#### 4. Avoid when team readability matters

In production code, readability is very important.

If a junior developer or teammate cannot understand the `reduce()` easily, prefer simpler methods.

#### Good use cases for `reduce()`

Use `reduce()` when you really need to accumulate values.

Examples:

```js
const total = numbers.reduce((sum, num) => sum + num, 0);
```

```js
const grouped = users.reduce((acc, user) => {
  const role = user.role;

  if (!acc[role]) {
    acc[role] = [];
  }

  acc[role].push(user);

  return acc;
}, {});
```

#### **Interview Line**

Avoid `reduce()` when `map()`, `filter()`, or a simple loop makes the code clearer. Use `reduce()` when you need to accumulate values into a single result.

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

⚠️ `substr()` is deprecated and should be avoided.

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

### Q. What is `split()`?

**Answer:**

`split()` converts a string into an array using a separator.

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

### Q. Are strings mutable or immutable in JavaScript?

**Answer:**

Strings are immutable in JavaScript. Once a string is created, its characters cannot be changed directly.

```js
let str = "hello";

str[0] = "H";

console.log(str); // hello
```

String methods return new strings instead of modifying the original string.

```js
const upper = str.toUpperCase();

console.log(str); // hello
console.log(upper); // HELLO
```

This behavior makes strings predictable and safe to share.

**Interview Line**

JavaScript strings are immutable; operations create new strings instead of modifying the original.

### Q. Difference between `charAt()` and bracket notation

**Answer:**

Both `charAt()` and bracket notation are used to access characters in a string.

```js
const str = "JavaScript";

console.log(str.charAt(0)); // J
console.log(str[0]); // J
```

Difference when index is out of range:

```js
console.log(str.charAt(100)); // ""
console.log(str[100]); // undefined
```

Bracket notation is shorter and commonly used. `charAt()` is older and returns an empty string for invalid indexes.

**Interview Line**

Both access characters, but `charAt()` returns an empty string for invalid index while bracket notation returns `undefined`.

### Q. Difference between `slice()`, `substring()`, and `substr()`.

**Answer:**

`slice()`, `substring()`, and `substr()` are JavaScript string methods used to extract part of a string, but they work slightly differently.

```js
const str = "JavaScript";
```

#### 1. `slice(start, end)`

`slice()` extracts characters from `start` index to `end` index, but it does not include the `end` index.

```js
console.log(str.slice(0, 4)); // "Java"
console.log(str.slice(4, 10)); // "Script"
```

It supports negative indexes.

```js
console.log(str.slice(-6)); // "Script"
```

Here, `-6` means start from the 6th character from the end.

#### 2. `substring(start, end)`

`substring()` also extracts characters from `start` to `end`, excluding the `end` index.

```js
console.log(str.substring(0, 4)); // "Java"
console.log(str.substring(4, 10)); // "Script"
```

But `substring()` does not support negative indexes. Negative values are treated as `0`.

```js
console.log(str.substring(-4, 4)); // "Java"
```

Another difference is that `substring()` swaps the arguments if `start` is greater than `end`.

```js
console.log(str.substring(4, 0)); // "Java"
```

This behaves like:

```js
str.substring(0, 4);
```

#### 3. `substr(start, length)`

`substr()` extracts characters starting from `start` index and takes the given number of characters.

```js
console.log(str.substr(4, 6)); // "Script"
```

Here, `4` is the starting index and `6` is the number of characters to extract.

It also supports negative start index.

```js
console.log(str.substr(-6, 6)); // "Script"
```

#### Difference Table

| Method        | Parameters      | Supports Negative Index | Mutates Original String | Status                  |
| ------------- | --------------- | ----------------------- | ----------------------- | ----------------------- |
| `slice()`     | `start, end`    | Yes                     | No                      | Recommended             |
| `substring()` | `start, end`    | No                      | No                      | Used, but less flexible |
| `substr()`    | `start, length` | Yes                     | No                      | Not recommended         |

**Example Comparison**

```js
const str = "JavaScript";

console.log(str.slice(4, 10)); // "Script"
console.log(str.substring(4, 10)); // "Script"
console.log(str.substr(4, 6)); // "Script"
```

All three return `"Script"`, but their parameters are different.

**Interview Line**

slice() and substring() use start and end indexes, while substr() uses start index and length. slice() is generally preferred because it supports negative indexes and has predictable behavior.

### Q. Why is substr() not recommended?

**Answer:**

`substr()` is not recommended because it is considered a legacy method.

Although it still works in many browsers, it is not part of the modern recommended JavaScript standard for string extraction.

```JS
const str = "JavaScript";

console.log(str.substr(4, 6)); // "Script"
```

The main issue is not that `substr()` is broken, but that modern JavaScript prefers `slice()` or `substring()` instead.

#### Why avoid `substr()`?

1. Legacy method

`substr()` is older and kept mainly for backward compatibility.

2. Different parameter meaning

Unlike `slice()` and `substring()`, `substr()` uses:

```js
substr(start, length);
```

But `slice()` and `substring()` use:

```js
slice(start, end);
substring(start, end);
```

This difference can confuse developers.

**Example:**

```js
const str = "JavaScript";

console.log(str.slice(4, 6)); // "Sc"
console.log(str.substr(4, 6)); // "Script"
```

The same numbers give different results.

3. Better alternatives exist

Use `slice()` instead:

```js
const str = "JavaScript";

console.log(str.slice(4)); // "Script"
```

Or if you need a fixed length:

```js
console.log(str.slice(4, 10)); // "Script"
```

**Best Practice**

Prefer this:

```js
str.slice(start, end);
```

Avoid this:

```js
str.substr(start, length);
```

**Interview Line**

`substr()` is not recommended because it is a legacy method and its parameter behavior is different from `slice()` and `substring()`. In modern JavaScript, `slice()` is usually the preferred method.

### Q. How do you reverse words in a sentence?

**Answer:**

To reverse words in a sentence, split the sentence by spaces, reverse the words, and join them back.

```js
function reverseWords(sentence) {
  return sentence.split(" ").reverse().join(" ");
}

console.log(reverseWords("I love JavaScript"));
// JavaScript love I
```

If you want to handle extra spaces better:

```js
function reverseWords(sentence) {
  return sentence.trim().split(/\s+/).reverse().join(" ");
}
```

**Interview Line**

Reverse words by splitting the sentence into words, reversing the array, and joining it again.

### Q. How do you check if two strings are anagrams?

**Answer:**

Two strings are anagrams if they contain the same characters with the same frequency.

Simple approach:

```js
function isAnagram(str1, str2) {
  const normalize = (str) => str.toLowerCase().replace(/\s/g, "").split("").sort().join("");

  return normalize(str1) === normalize(str2);
}

console.log(isAnagram("listen", "silent")); // true
console.log(isAnagram("hello", "world")); // false
```

Frequency approach is more efficient for larger strings.

```js
function isAnagram(a, b) {
  if (a.length !== b.length) return false;

  const count = {};

  for (let char of a) {
    count[char] = (count[char] || 0) + 1;
  }

  for (let char of b) {
    if (!count[char]) return false;
    count[char]--;
  }

  return true;
}
```

**Interview Line**

Anagrams contain the same characters with the same frequency.

### Q. How do you find the first non-repeating character in a string?

**Answer:**

To find the first non-repeating character, count character frequency and then scan the string again.

```js
function firstNonRepeatingChar(str) {
  const count = {};

  for (let char of str) {
    count[char] = (count[char] || 0) + 1;
  }

  for (let char of str) {
    if (count[char] === 1) {
      return char;
    }
  }

  return null;
}

console.log(firstNonRepeatingChar("aabbcde")); // c
```

This runs in linear time: `O(n)`.

**Interview Line**

Count characters first, then return the first character whose count is one.

### Q. How do you remove duplicate characters from a string?

**Answer:**

Duplicate characters can be removed using `Set`.

```js
function removeDuplicateChars(str) {
  return [...new Set(str)].join("");
}

console.log(removeDuplicateChars("programming")); // progamin
```

Using loop:

```js
function removeDuplicateChars(str) {
  let result = "";
  const seen = new Set();

  for (let char of str) {
    if (!seen.has(char)) {
      seen.add(char);
      result += char;
    }
  }

  return result;
}
```

**Interview Line**

Use `Set` to keep only the first occurrence of each character.

### Q. Difference between `trim()`, `trimStart()`, and `trimEnd()`

**Answer:**

`trim()`, `trimStart()`, and `trimEnd()` remove whitespace from strings.

```js
const str = "  hello  ";

console.log(str.trim()); // "hello"
console.log(str.trimStart()); // "hello  "
console.log(str.trimEnd()); // "  hello"
```

| Method        | Removes                       |
| ------------- | ----------------------------- |
| `trim()`      | Both start and end whitespace |
| `trimStart()` | Start whitespace              |
| `trimEnd()`   | End whitespace                |

They do not modify the original string because strings are immutable.

**Interview Line**

`trim()` removes both sides, while `trimStart()` and `trimEnd()` remove only one side.

### Q. Difference between `replace()` and `replaceAll()`

**Answer:**

`replace()` and `replaceAll()` are JavaScript string methods used to replace text inside a string.

The main difference is:

- `replace()` replaces only the first matching value by default.
- `replaceAll()` replaces all matching values.

#### 1. `replace()`

`replace()` replaces the first occurrence of the matched string.

```js
const text = "JavaScript is good. JavaScript is powerful.";

const result = text.replace("JavaScript", "React");

console.log(result);
// "React is good. JavaScript is powerful."
```

In this example, only the first `"JavaScript"` is replaced.

To replace all occurrences using `replace()`, we need to use a regular expression with the global `g` flag.

```js
const text = "JavaScript is good. JavaScript is powerful.";

const result = text.replace(/JavaScript/g, "React");

console.log(result);
// "React is good. React is powerful."
```

#### 2. replaceAll()

`replaceAll()` replaces all occurrences of the matched string.

```js
const text = "JavaScript is good. JavaScript is powerful.";

const result = text.replaceAll("JavaScript", "React");

console.log(result);
// "React is good. React is powerful."
```

Here, all `"JavaScript"` values are replaced with `"React"`.

#### Difference Table

| Feature                       | `replace()`                    | `replaceAll()`                    |
| ----------------------------- | ------------------------------ | --------------------------------- |
| Replaces by default           | First match only               | All matches                       |
| Can replace all values        | Yes, using regex with `g` flag | Yes, directly                     |
| Supports string pattern       | Yes                            | Yes                               |
| Supports regex pattern        | Yes                            | Yes, but regex must have `g` flag |
| Readability for replacing all | Less direct                    | More clear                        |

**Important Point**

If you use a regular expression with `replaceAll()`, the regex must include the global `g` flag.

```js
const text = "a-b-a";

console.log(text.replaceAll(/a/g, "x"));
// "x-b-x"
```

Without the global flag, `replaceAll()` throws an error.

```js
const text = "a-b-a";

text.replaceAll(/a/, "x");
// TypeError
```

#### When to Use `replace()`

Use `replace()` when you want to replace only the first matching value.

```js
const message = "Hello Hello";

const result = message.replace("Hello", "Hi");

console.log(result);
// "Hi Hello"
```

#### When to Use `replaceAll()`

Use `replaceAll()` when you want to replace every matching value.

```js
const message = "Hello Hello";

const result = message.replaceAll("Hello", "Hi");

console.log(result);
// "Hi Hi"
```

**Interview Line**

`replace()` replaces only the first match by default, while `replaceAll()` replaces all matches. To replace all matches with `replace()`, we need to use a global regular expression.

### Q. How does regex help in string manipulation?

**Answer:**

Regular expressions help search, match, validate, and replace patterns in strings.

Examples:

```js
const email = "test@example.com";

console.log(/^[^@]+@[^@]+\.[^@]+$/.test(email)); // true
```

Remove all spaces:

```js
const str = "hello world from js";

console.log(str.replace(/\s+/g, "")); // helloworldfromjs
```

Extract numbers:

```js
const text = "Order ID: 12345";

console.log(text.match(/\d+/)[0]); // 12345
```

Regex is useful for validation, parsing, search, and cleanup.

**Interview Line**

Regex helps perform pattern-based string matching, validation, and replacement.

### Q. How do you escape special characters in a string?

**Answer:**

Special characters can be escaped using a backslash `\`.

```js
const str = 'He said, "Hello"';

console.log(str); // He said, "Hello"
```

Common escapes:

```js
\n  // new line
\t  // tab
\\  // backslash
\"  // double quote
\'  // single quote
```

In regular expressions, special regex characters also need escaping.

```js
const regex = /\./; // matches a dot character
```

**Interview Line**

Special characters are escaped using backslash so JavaScript treats them as normal characters.

### Q. What is Unicode in JavaScript strings?

**Answer:**

Unicode is a character encoding standard that allows JavaScript strings to represent characters from many languages and symbols.

```js
const rupee = "₹";
const emoji = "😊";

console.log(rupee);
console.log(emoji);
```

JavaScript strings are based on UTF-16 code units. Some characters, especially emojis, may use more than one code unit.

```js
console.log("😊".length); // 2
```

This is important when reversing strings, counting characters, or slicing text.

**Interview Line**

JavaScript strings use Unicode/UTF-16, so some visible characters may use more than one code unit.

### Q. What is the problem with reversing emoji strings using `split("").reverse()`?

**Answer:**

Reversing emoji strings using `split("").reverse()` can break emojis because many emojis use multiple UTF-16 code units.

```js
const emoji = "😊";

console.log(emoji.length); // 2
console.log(emoji.split("").reverse().join("")); // broken output
```

Better approach:

```js
const str = "hello 😊";

const reversed = Array.from(str).reverse().join("");

console.log(reversed);
```

For complex emojis made with multiple joined characters, even `Array.from()` may not be enough. In such cases, use `Intl.Segmenter`.

```js
const segmenter = new Intl.Segmenter("en", { granularity: "grapheme" });

const reversed = [...segmenter.segment(str)]
  .map((x) => x.segment)
  .reverse()
  .join("");
```

**Interview Line**

`split("")` works on code units, so it can break emojis and complex Unicode characters.

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

### Q. Difference between `then()` and `async/await`

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

### Q. How does `async/await` work internally?

**Answer:**

- async function always returns a Promise
- await pauses execution until Promise resolves
- Internally, it is syntactic sugar over `.then()`

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

### Q. What is `Promise.all()`?

**Answer:**

`Promise.all()` executes multiple promises in parallel and:

- Resolves when all promises resolve
- Rejects if any one promise rejects

```js
Promise.all([p1, p2, p3])
  .then((results) => console.log(results))
  .catch((err) => console.log(err));
```

### Q. Difference between `Promise.all`, `allSettled`, `race`, `any`

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

### Q. What is `setTimeout`?

**Answer:**

Executes a function after a specified delay (minimum time).

```js
setTimeout(() => {
  console.log("Executed later");
}, 1000);
```

Delay is not guaranteed exact due to event loop.

### Q. What is `setInterval`?

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

- Control jumps to nearest `.catch()`
- In async/await, it throws an error
- If unhandled → Unhandled Promise Rejection

```js
promise.catch((err) => console.log(err));
```

### Q. What is the difference between synchronous and asynchronous code?

**Answer:**

Synchronous code executes line by line and blocks the next line until the current task finishes.

```js
console.log("A");
console.log("B");
console.log("C");
```

Output:

```js
A;
B;
C;
```

Asynchronous code allows long-running tasks to complete later without blocking the main thread.

```js
console.log("A");

setTimeout(() => {
  console.log("B");
}, 1000);

console.log("C");
```

Output:

```js
A;
C;
B;
```

Async code is commonly used for API calls, timers, file operations, and event handling.

**Interview Line**

Synchronous code blocks execution, while asynchronous code allows non-blocking operations to complete later.

### Q. What is callback hell and how do you avoid it?

**Answer:**

Callback hell happens when callbacks are nested deeply, making code hard to read and maintain.

```js
login(user, () => {
  getProfile(() => {
    getPosts(() => {
      getComments(() => {
        console.log("Done");
      });
    });
  });
});
```

Problems:

- Difficult to read
- Difficult to debug
- Error handling becomes messy
- Logic becomes tightly coupled

Solutions:

1. Use named functions.
2. Use Promises.
3. Use async/await.

```js
async function loadData() {
  const user = await login();
  const profile = await getProfile(user);
  const posts = await getPosts(profile);
  const comments = await getComments(posts);

  return comments;
}
```

**Interview Line**

Callback hell is nested callback complexity, and it is avoided using Promises or async/await.

### Q. What is inversion of control in callbacks?

**Answer:**

Inversion of control in callbacks means we give control of our function execution to another function or library.

```js
function payment(callback) {
  // third-party logic
  callback();
}

payment(() => {
  console.log("Payment done");
});
```

The problem is that we trust the external function to call our callback correctly.

Risks:

- Callback may never be called
- Callback may be called multiple times
- Callback may be called too early or too late
- Error handling may be inconsistent

Promises reduce this issue by providing a more predictable contract.

**Interview Line**

Inversion of control happens when callback execution is controlled by another function, which can lead to trust and reliability issues.

### Q. What is a Promise chain?

**Answer:**

A Promise chain is a sequence of `.then()`, `.catch()`, and `.finally()` calls where each step depends on the previous result.

```js
fetch("/api/user")
  .then((res) => res.json())
  .then((user) => fetch(`/api/posts/${user.id}`))
  .then((res) => res.json())
  .then((posts) => console.log(posts))
  .catch((error) => console.error(error));
```

Each `.then()` returns a new Promise.

If a value is returned, it is passed to the next `.then()`.
If a Promise is returned, the next `.then()` waits for it.

**Interview Line**

Promise chaining allows async operations to run in sequence by returning values or Promises from `.then()`.

### Q. What happens if you return a value from `.then()`?

**Answer:**

If you return a normal value from `.then()`, that value becomes the resolved value of the next Promise in the chain.

```js
Promise.resolve(10)
  .then((value) => {
    return value * 2;
  })
  .then((result) => {
    console.log(result); // 20
  });
```

The returned value is automatically wrapped in a resolved Promise.

Conceptually:

```js
return 20;
```

becomes:

```js
return Promise.resolve(20);
```

**Interview Line**

Returning a value from `.then()` passes that value to the next `.then()` as a resolved result.

### Q. What happens if you return a Promise from `.then()`?

**Answer:**

If you return a Promise from `.then()`, the next `.then()` waits for that Promise to settle.

```js
Promise.resolve(1)
  .then((value) => {
    return new Promise((resolve) => {
      setTimeout(() => resolve(value + 1), 1000);
    });
  })
  .then((result) => {
    console.log(result); // 2 after 1 second
  });
```

This allows sequential async operations.

```js
fetchUser()
  .then((user) => fetchPosts(user.id))
  .then((posts) => console.log(posts));
```

The second `.then()` waits for `fetchPosts()`.

**Interview Line**

Returning a Promise from `.then()` pauses the chain until that Promise resolves or rejects.

### Q. What is the difference between resolved and fulfilled promise?

**Answer:**

A Promise is fulfilled when it has successfully completed with a value. A Promise is resolved when it is settled or locked into following another Promise.

Simple case:

```js
const p = Promise.resolve("Done");
```

This Promise is both resolved and fulfilled.

But a Promise can be resolved with another Promise:

```js
const p1 = new Promise((resolve) => {
  resolve(Promise.resolve("Done"));
});
```

Here, `p1` is resolved to follow another Promise. It becomes fulfilled only when the inner Promise fulfills.

In everyday interviews, people often use "resolved" to mean "fulfilled", but technically they are different.

**Interview Line**

Fulfilled means completed successfully; resolved means the Promise has been settled or is following another Promise’s state.

### Q. What is Promise composition?

**Answer:**

Promise composition means combining multiple Promises to build async flows.

Common composition methods:

```js
Promise.all();
Promise.allSettled();
Promise.race();
Promise.any();
```

Example using `Promise.all()`:

```js
const userPromise = fetchUser();
const postsPromise = fetchPosts();

const [user, posts] = await Promise.all([userPromise, postsPromise]);
```

Sequential composition:

```js
fetchUser()
  .then((user) => fetchPosts(user.id))
  .then((posts) => console.log(posts));
```

Parallel composition improves performance when tasks are independent.

**Interview Line**

Promise composition combines async tasks either sequentially or in parallel using Promise utilities.

### Q. Difference between `Promise.all()` and `Promise.allSettled()`

**Answer:**

Both `Promise.all()` and `Promise.allSettled()` are used to handle multiple promises together, but they behave differently when one promise fails.

#### `Promise.all()`

`Promise.all()` runs multiple promises in parallel and waits for all of them to resolve.

If all promises resolve, it returns an array of resolved values.

```js
const p1 = Promise.resolve("User");
const p2 = Promise.resolve("Posts");
const p3 = Promise.resolve("Comments");

Promise.all([p1, p2, p3]).then((result) => {
  console.log(result);
});
```

**Output:**

```js
["User", "Posts", "Comments"];
```

But if any one promise rejects, `Promise.all()` immediately rejects.

```js
const p1 = Promise.resolve("User");
const p2 = Promise.reject("Posts API failed");
const p3 = Promise.resolve("Comments");

Promise.all([p1, p2, p3])
  .then((result) => console.log(result))
  .catch((error) => console.log(error));
```

**Output:**

```js
Posts API failed
```

Here, even if other promises succeed, the final result goes to `catch()` because one promise failed.

#### `Promise.allSettled()`

`Promise.allSettled()` waits for all promises to finish, whether they resolve or reject.

It does not fail immediately if one promise rejects.

```js
const p1 = Promise.resolve("User");
const p2 = Promise.reject("Posts API failed");
const p3 = Promise.resolve("Comments");

Promise.allSettled([p1, p2, p3]).then((result) => {
  console.log(result);
});
```

**Output:**

```js
[
  { status: "fulfilled", value: "User" },
  { status: "rejected", reason: "Posts API failed" },
  { status: "fulfilled", value: "Comments" },
];
```

Each result contains:

- `status: "fulfilled"` with `value`
- `status: "rejected"` with `reason`

#### Difference Table

| Feature                | `Promise.all()`           | `Promise.allSettled()`            |
| ---------------------- | ------------------------- | --------------------------------- |
| Waits for all promises | Yes, only if all resolve  | Yes, always                       |
| If one promise fails   | Immediately rejects       | Still waits for all               |
| Return result          | Array of resolved values  | Array of status objects           |
| Error handling         | Goes to `catch()`         | Rejection appears in result array |
| Best use case          | All promises are required | Partial success is acceptable     |

#### When to Use

Use `Promise.all()` when all API calls are required.

```js
const [user, orders] = await Promise.all([fetchUser(), fetchOrders()]);
```

If either fails, the whole operation should fail.

Use `Promise.allSettled()` when some failures are acceptable.

```js
const results = await Promise.allSettled([fetchUser(), fetchNotifications(), fetchRecommendations()]);
```

Even if recommendations fail, user data can still be shown.

**Interview Line**

`Promise.all()` rejects immediately if any promise fails, while `Promise.allSettled()` waits for all promises to complete and returns the status of each promise.

### Q. Difference between `Promise.race()` and `Promise.any()`

**Answer:**

Both `Promise.race()` and `Promise.any()` deal with the first completed promise, but they handle resolved and rejected promises differently.

#### `Promise.race()`

`Promise.race()` returns the result of the first promise that settles.

A promise is settled when it is either:

- Resolved
- Rejected

So `Promise.race()` does not care whether the first promise succeeds or fails.

```js
const p1 = new Promise((resolve) => setTimeout(() => resolve("First success"), 1000));

const p2 = new Promise((resolve) => setTimeout(() => resolve("Second success"), 500));

Promise.race([p1, p2]).then((result) => {
  console.log(result);
});
```

**Output:**

```js
Second success
```

Because `p2` resolves first.

If the first settled promise rejects, `Promise.race()` rejects.

```js
const p1 = new Promise((_, reject) => setTimeout(() => reject("Failed first"), 500));

const p2 = new Promise((resolve) => setTimeout(() => resolve("Success later"), 1000));

Promise.race([p1, p2])
  .then((result) => console.log(result))
  .catch((error) => console.log(error));
```

Output:

```js
Failed first
```

#### `Promise.any()`

`Promise.any()` returns the first successfully resolved promise.

It ignores rejected promises until it finds one resolved promise.

```js
const p1 = Promise.reject("API 1 failed");

const p2 = new Promise((resolve) => setTimeout(() => resolve("API 2 success"), 1000));

const p3 = new Promise((resolve) => setTimeout(() => resolve("API 3 success"), 500));

Promise.any([p1, p2, p3]).then((result) => {
  console.log(result);
});
```

Output:

```js
API 3 success
```

Here, `p1` failed, but `Promise.any()` ignored it and returned the first successful result.

If all promises reject, `Promise.any()` rejects with `AggregateError`.

```js
const p1 = Promise.reject("API 1 failed");
const p2 = Promise.reject("API 2 failed");

Promise.any([p1, p2]).catch((error) => {
  console.log(error instanceof AggregateError); // true
  console.log(error.errors);
});
```

#### Difference Table

| Feature                | `Promise.race()`                         | `Promise.any()`                          |
| ---------------------- | ---------------------------------------- | ---------------------------------------- |
| Returns                | First settled promise                    | First fulfilled promise                  |
| Handles rejection      | Rejects if first settled promise rejects | Ignores rejected promises until all fail |
| If all promises reject | Rejects with first rejection             | Rejects with `AggregateError`            |
| Best use case          | Timeout handling                         | Get first successful response            |

#### Real-world Use Case of `Promise.race()`

`Promise.race()` is useful for timeout logic.

```js
const timeout = new Promise((\_, reject) =>
setTimeout(() => reject("Request timed out"), 3000)
);

const apiCall = fetch("/api/users");

Promise.race([apiCall, timeout])
.then((res) => console.log("API success"))
.catch((err) => console.log(err));
```

If the API takes more than 3 seconds, timeout wins.

#### Real-world Use Case of `Promise.any()`

`Promise.any()` is useful when multiple sources can provide the same data, and we only need the first successful response.

```js
Promise.any([fetch("/server-1/data"), fetch("/server-2/data"), fetch("/server-3/data")])
  .then((response) => console.log("First successful response"))
  .catch((error) => console.log("All servers failed"));
```

**Interview Line**

`Promise.race()` returns the first settled promise, whether resolved or rejected, while Promise.any() returns the first fulfilled promise and ignores rejections unless all promises fail.

### Q. What is `AggregateError` in Promise.any?

**Answer:**

`AggregateError` is the error thrown by `Promise.any()` when all promises reject.

```js
Promise.any([Promise.reject("Error 1"), Promise.reject("Error 2")]).catch((error) => {
  console.log(error instanceof AggregateError); // true
  console.log(error.errors); // ["Error 1", "Error 2"]
});
```

`Promise.any()` resolves as soon as one Promise fulfills. It rejects only if every Promise rejects.

The rejection contains all individual errors inside `error.errors`.

**Interview Line**

`AggregateError` groups multiple rejection reasons when `Promise.any()` fails completely.

### Q. How do you run async tasks sequentially?

**Answer:**

To run async tasks sequentially, use `await` one after another.

```js
async function runTasks() {
  const user = await fetchUser();
  const posts = await fetchPosts(user.id);
  const comments = await fetchComments(posts[0].id);

  return comments;
}
```

Each task waits for the previous task to complete.

For an array of tasks:

```js
for (const task of tasks) {
  await task();
}
```

Use sequential execution when each task depends on the previous result or when order matters.

**Interview Line**

Sequential async tasks are run by awaiting each task one by one.

### Q. How do you run async tasks in parallel?

**Answer:**

To run async tasks in parallel, start them together and wait using `Promise.all()`.

```js
async function loadData() {
  const userPromise = fetchUser();
  const postsPromise = fetchPosts();
  const settingsPromise = fetchSettings();

  const [user, posts, settings] = await Promise.all([userPromise, postsPromise, settingsPromise]);

  return { user, posts, settings };
}
```

This is faster when tasks are independent.

Do not use parallel execution if one task depends on another.

**Interview Line**

Independent async tasks should be run in parallel using `Promise.all()` for better performance.

### Q. How do you limit concurrent API calls?

**Answer:**

To limit concurrent API calls, run only a fixed number of promises at a time.

Simple concurrency limiter:

```js
async function runWithLimit(tasks, limit) {
  const results = [];
  const executing = [];

  for (const task of tasks) {
    const promise = task().then((result) => {
      executing.splice(executing.indexOf(promise), 1);
      return result;
    });

    results.push(promise);
    executing.push(promise);

    if (executing.length >= limit) {
      await Promise.race(executing);
    }
  }

  return Promise.all(results);
}
```

Use cases:

- Avoid overloading server
- Avoid browser request limits
- Handle large batches safely

**Interview Line**

Concurrency limiting controls how many async tasks run at the same time.

### Q. What is async error propagation?

**Answer:**

Async error propagation means errors move through Promise chains or async/await until they are caught.

In Promise chains:

```js
fetchData()
  .then((data) => processData(data))
  .then((result) => saveData(result))
  .catch((error) => {
    console.error(error);
  });
```

Any error in the chain goes to `.catch()`.

In async/await:

```js
async function run() {
  try {
    const data = await fetchData();
    const result = processData(data);
  } catch (error) {
    console.error(error);
  }
}
```

A rejected Promise behaves like a thrown error when awaited.

**Interview Line**

Async errors propagate through Promise chains or async functions until handled by `.catch()` or `try...catch`.

### Q. Can `finally()` change the result of a Promise?

**Answer:**

Normally, `.finally()` **does not change the resolved value or rejected reason** of a Promise.

It is mainly used for cleanup operations that should run whether the Promise succeeds or fails, such as:

- Hiding a loader
- Closing a database connection
- Releasing resources
- Resetting some state

The value returned from a normal `.finally()` callback is ignored.

#### When the Promise Resolves

```js
Promise.resolve("Success")
  .finally(() => {
    console.log("Cleanup");
    return "Changed value";
  })
  .then((result) => {
    console.log(result);
  });
```

**Output:**

```js
Cleanup;
Success;
```

Even though `finally()` returns `"Changed value"`, the original resolved value `"Success"` is passed to `.then()`.

When the Promise Rejects

```js
Promise.reject("Something went wrong")
  .finally(() => {
    console.log("Cleanup");
    return "Recovered";
  })
  .catch((error) => {
    console.log(error);
  });
```

**Output:**

```js
Cleanup
Something went wrong
```

Returning `"Recovered"` from `finally()` does not convert the rejected Promise into a fulfilled Promise.

The original rejection continues through the Promise chain.

#### When Can `finally()` Change the Result?

`finally()` can affect the result if it throws an error or returns a Promise that rejects.

```js
Promise.resolve("Success")
  .finally(() => {
    throw new Error("Error inside finally");
  })
  .then((result) => {
    console.log(result);
  })
  .catch((error) => {
    console.log(error.message);
  });
```

**Output:**

```js
Error inside finally
```

Here, the original value `"Success"` is replaced by the error thrown inside `finally()`.

Similarly:

```js
Promise.resolve("Success")
  .finally(() => {
    return Promise.reject("Finally failed");
  })
  .catch((error) => {
    console.log(error);
  });
```

**Output:**

```js
Finally failed
```

So, if the `finally()` callback fails, the resulting Promise becomes rejected with that new error.

#### Behavior Summary

| `finally()` Callback        | Result                                 |
| --------------------------- | -------------------------------------- |
| Returns a normal value      | Original Promise result is preserved   |
| Returns a fulfilled Promise | Original Promise result is preserved   |
| Throws an error             | Promise rejects with the new error     |
| Returns a rejected Promise  | Promise rejects with the new rejection |

#### Difference from `then()`

Unlike `finally()`, `.then()` can directly transform the resolved value.

```js
Promise.resolve(10)
.then((value) => {
return value \* 2;
})
.then((result) => {
console.log(result);
});
```

Output:

```js
20;
```

But with `finally()`:

```js
Promise.resolve(10)
  .finally(() => {
    return 20;
  })
  .then((result) => {
    console.log(result);
  });
```

Output:

```js
10;
```

The value returned by `finally()` is ignored because `finally()` is designed for cleanup rather than transforming Promise results.

#### Real-world Use Case

A common use case is hiding a loading indicator after an API request finishes.

```js
showLoader();

fetch("/api/users")
  .then((response) => response.json())
  .then((data) => {
    console.log(data);
  })
  .catch((error) => {
    console.log(error);
  })
  .finally(() => {
    hideLoader();
  });
```

Whether the API call succeeds or fails, `hideLoader()` will execute without changing the original result of the Promise chain.

**Interview Line**

`finally()` normally does not change a Promise's resolved value or rejection reason. However, if the `finally()` callback throws an error or returns a rejected Promise, the chain becomes rejected with that new error.

### Q. What happens if an error is thrown inside `.then()`?

**Answer:**

If an error is thrown inside `.then()`, the returned Promise becomes rejected and control moves to the nearest `.catch()`.

```js
Promise.resolve(10)
  .then((value) => {
    throw new Error("Something went wrong");
  })
  .then(() => {
    console.log("Skipped");
  })
  .catch((error) => {
    console.log(error.message); // Something went wrong
  });
```

This makes Promise error handling similar to synchronous `try...catch`.

**Interview Line**

An error inside `.then()` rejects the chain and is handled by the next `.catch()`.

### Q. Why does async function always return a Promise?

**Answer:**

An async function always returns a Promise, even if it returns a normal value.

```js
async function greet() {
  return "Hello";
}

console.log(greet()); // Promise
```

To get the value:

```js
greet().then((value) => console.log(value)); // Hello
```

This:

```js
async function test() {
  return 10;
}
```

is similar to:

```js
function test() {
  return Promise.resolve(10);
}
```

If an async function throws an error, it returns a rejected Promise.

**Interview Line**

Async functions always wrap return values in a Promise.

### Q. What is top-level await?

**Answer:**

Top-level await allows using `await` outside an async function in ES modules.

```js
const response = await fetch("/api/config");
const config = await response.json();

export default config;
```

It works only in modules, not regular scripts.

Use cases:

- Load configuration
- Initialize database connection
- Import data before module execution continues

Important: top-level await can delay module loading, so it should be used carefully.

**Interview Line**

Top-level await allows awaiting Promises directly at module level.

### Q. How do you cancel a fetch request?

**Answer:**

A fetch request can be cancelled using `AbortController`.

```js
const controller = new AbortController();

fetch("/api/users", {
  signal: controller.signal,
})
  .then((res) => res.json())
  .then((data) => console.log(data))
  .catch((error) => {
    if (error.name === "AbortError") {
      console.log("Request cancelled");
    } else {
      console.error(error);
    }
  });

controller.abort();
```

`AbortController` provides a `signal` that is passed to `fetch`. Calling `abort()` cancels the request.

Use cases:

- Cancel stale search requests
- Cleanup API calls when component unmounts
- Avoid race conditions

**Interview Line**

`AbortController` cancels fetch requests by passing its signal and calling `abort()`.

### Q. What is AbortController?

**Answer:**

A fetch request can be cancelled using `AbortController`.

```js
const controller = new AbortController();

fetch("/api/users", {
  signal: controller.signal,
})
  .then((res) => res.json())
  .then((data) => console.log(data))
  .catch((error) => {
    if (error.name === "AbortError") {
      console.log("Request cancelled");
    } else {
      console.error(error);
    }
  });

controller.abort();
```

`AbortController` provides a `signal` that is passed to `fetch`. Calling `abort()` cancels the request.

Use cases:

- Cancel stale search requests
- Cleanup API calls when component unmounts
- Avoid race conditions

**Interview Line**

`AbortController` cancels fetch requests by passing its signal and calling `abort()`.

### Q. Difference between callback queue and microtask queue

**Answer:**

The callback queue, also called macrotask queue, stores callbacks from APIs like `setTimeout`, `setInterval`, DOM events, and I/O.

The microtask queue stores callbacks from Promises, `queueMicrotask`, and MutationObserver.

```js
setTimeout(() => console.log("timeout"), 0);

Promise.resolve().then(() => console.log("promise"));

console.log("sync");
```

Output:

```js
sync;
promise;
timeout;
```

Microtasks run before macrotasks after the call stack becomes empty.

**Interview Line**

Promise callbacks in the microtask queue run before timer callbacks in the macrotask queue.

### Q. Why do Promise callbacks run before `setTimeout()`?

**Answer:**

Promise callbacks run before `setTimeout()` because Promise callbacks go to the microtask queue, while `setTimeout()` callbacks go to the macrotask queue.

```js
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

Promise.resolve().then(() => {
  console.log("Promise");
});

console.log("End");
```

Output:

```js
Start;
End;
Promise;
Timeout;
```

Execution order:

1. Synchronous code
2. Microtasks
3. Macrotasks

**Interview Line**

Microtasks have higher priority than macrotasks, so Promise callbacks run before `setTimeout()`.

## Execution Context & Internals

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

### Q. What is the Global Execution Context?

**Answer:**

The Global Execution Context (GEC) is the first execution context created when JavaScript starts running a script.

It represents the environment in which the top-level code is executed.

JavaScript creates only one global execution context for a script.

The global execution context has two major phases:

1. Creation Phase
2. Execution Phase

During the creation phase, JavaScript sets up memory for variables and functions.

During the execution phase, JavaScript executes the code line by line.

**Example:**

```js
var name = "John";

function greet() {
  console.log("Hello");
}

greet();
```

Before executing the code, JavaScript creates the global execution context and allocates memory for:

```js
name -> undefined
greet -> complete function definition
```

Then the execution phase begins:

name = "John";
greet();

In browsers, the global execution context is associated with the global object, traditionally `window`.

```js
var age = 25;

console.log(window.age);
```

In classic browser scripts, this can output:

```js
25;
```

However, global behavior differs in environments such as ES modules and Node.js.

**Interview Line**

The Global Execution Context is the first execution context created by JavaScript. It handles top-level code and goes through a creation phase followed by an execution phase.

### Q. What is Function Execution Context?

**Answer:**

A Function Execution Context (FEC) is created whenever a JavaScript function is invoked.

Each function call gets its own execution context.

**Example:**

```js
function add(a, b) {
  const result = a + b;
  return result;
}

add(10, 20);
```

When `add(10, 20)` is called, JavaScript creates a new function execution context.

Conceptually, it contains things such as:

```
a -> 10
b -> 20
result -> uninitialized initially
```

The function execution context also goes through:

1. Creation Phase
2. Execution Phase

Once the function finishes execution, its execution context is removed from the call stack.

**Example:**

```jss
function first() {
  second();
}

function second() {
  console.log("Hello");
}

first();
```

The contexts are created roughly like this:

```
Global Execution Context
        ↓
first() Execution Context
        ↓
second() Execution Context
```

After `second()` finishes, its execution context is removed, followed by `first()`.

**Interview Line**

A Function Execution Context is created every time a function is called. It contains the function's local variables, parameters, scope information, and execution state.

### Q. What is the difference between creation phase and execution phase?

**Answer:**

Every execution context goes through two important phases:

#### Creation Phase

Before executing the code, JavaScript prepares the environment.

During this phase, it:

- Allocates memory for variables
- Registers function declarations
- Creates lexical environments
- Establishes scope relationships
- Initializes var with undefined
- Keeps let and const uninitialized

**Example:**

```js
console.log(name);

var name = "John";
```

During creation:

```js
name -> undefined
```

Then during execution:

```js
console.log(name); // undefined
name = "John";
```

#### Execution Phase

During the execution phase, JavaScript actually runs the statements line by line.

**Example:**

```js
var x = 10;
var y = 20;

console.log(x + y);
```

Creation phase:

```
x -> undefined
y -> undefined
```

Execution phase:

```
x -> 10
y -> 20
console.log(30)
```

#### Difference Table

| Feature              | Creation Phase                       | Execution Phase                         |
| -------------------- | ------------------------------------ | --------------------------------------- |
| Purpose              | Prepare memory and scope             | Execute code                            |
| `var`                | Initialized as `undefined`           | Assigned actual value                   |
| `let` / `const`      | Created but uninitialized            | Initialized when declaration is reached |
| Function declaration | Full function stored                 | Can be called                           |
| Code execution       | Does not execute statements normally | Runs statements line by line            |

**Interview Line**

The creation phase prepares memory, scopes, and declarations, while the execution phase runs the actual JavaScript code and assigns values.

### Q. What gets stored in the memory creation phase?

**Answer:**

During the memory creation phase, JavaScript prepares bindings for variables and functions before normal code execution begins.

**For example:**

```js
var age = 25;

let city = "Delhi";

const country = "India";

function greet() {
  console.log("Hello");
}
```

Conceptually, the creation phase looks like:

```txt
age -> undefined
city -> uninitialized
country -> uninitialized
greet -> complete function definition
```

#### `var`

`var` is created and initialized with:

```js
undefined;
```

#### `let` and `const`

They are created but remain uninitialized until JavaScript reaches their declaration.

This period is called the Temporal Dead Zone.

#### Function declarations

The complete function definition becomes available during creation.

```js
function greet() {
  console.log("Hello");
}
```

So the function can be called before its declaration appears in the source code.

**Interview Line**

During the creation phase, JavaScript allocates bindings for variables and functions. `var` gets `undefined`, `let` and `const` stay uninitialized, and function declarations are fully available.

### Q. How are `var`, `let`, and `const` handled during hoisting?

**Answer:**

All three declarations are hoisted, but they are initialized differently.

#### `var`

`var` is hoisted and initialized with `undefined`.

```js
console.log(name);

var name = "John";
```

Output:

```js
undefined;
```

Conceptually:

```js
var name;

console.log(name);

name = "John";
```

#### `let`

`let` is hoisted, but it remains uninitialized until its declaration executes.

```js
console.log(age);

let age = 25;
```

This throws:

```js
ReferenceError;
```

#### `const`

`const` behaves similarly to let.

```js
console.log(country);

const country = "India";
```

This also throws:

```
ReferenceError
```

The period between entering the scope and reaching the declaration is known as the Temporal Dead Zone (TDZ).

#### Difference Table

| Declaration | Hoisted | Initialized During Creation | Accessible Before Declaration |
| ----------- | ------- | --------------------------- | ----------------------------- |
| `var`       | Yes     | `undefined`                 | Yes                           |
| `let`       | Yes     | No                          | No                            |
| `const`     | Yes     | No                          | No                            |

**Interview Line**

`var`, `let`, and `const` are all hoisted, but `var` is initialized with `undefined`, while `let` and `const` remain uninitialized in the Temporal Dead Zone until their declaration executes.

### Q. How are function declarations hoisted?

**Answer:**

Function declarations are fully hoisted.

That means both the function name and its complete function body are available during the creation phase.

**Example:**

```js
greet();

function greet() {
  console.log("Hello");
}
```

**Output:**

```js
Hello;
```

This works because JavaScript already has access to the entire function definition before normal execution begins.

**Conceptually:**

```
greet -> function greet() {
console.log("Hello");
}
```

This is different from many function expressions, where only the variable declaration may be initialized during hoisting.

**Interview Line**

Function declarations are fully hoisted, meaning their complete function definition is available before the line where the function appears in the source code.

### Q. How are function expressions hoisted?

**Answer:**

Function expressions follow the hoisting behavior of the variable used to store them.

**Example using var:**

```js
greet();

var greet = function () {
  console.log("Hello");
};
```

This throws:

```js
TypeError: greet is not a function
```

#### Why?

During the creation phase:

```js
greet -> undefined
```

So JavaScript effectively tries:

```js
undefined();
```

Function expression with let

```js
greet();

let greet = function () {
  console.log("Hello");
};
```

This throws:

```js
ReferenceError;
```

because greet is in the Temporal Dead Zone.

The same applies to const.

Arrow functions behave similarly

```js
hello();

const hello = () => {
  console.log("Hello");
};
```

This also throws a

```js
ReferenceError.
```

Difference Table

| Function Type               | Hoisting Behavior                        |
| --------------------------- | ---------------------------------------- |
| Function declaration        | Entire function is hoisted               |
| `var` function expression   | Variable becomes `undefined`             |
| `let` function expression   | Binding exists but is uninitialized      |
| `const` function expression | Binding exists but is uninitialized      |
| Arrow function              | Depends on `var`, `let`, or `const` used |

**Interview Line**

Function expressions are not fully hoisted like function declarations. Their behavior depends on the variable declaration used to store them.

### Q. What is the call stack?

**Answer:**

The call stack is a mechanism JavaScript uses to keep track of currently executing functions.

It follows the LIFO principle:

```
Last In, First Out
```

Whenever a function is called, its execution context is pushed onto the stack.

When the function finishes, its context is popped from the stack.

Example:

```js
function first() {
  second();
}

function second() {
  third();
}

function third() {
  console.log("Hello");
}

first();
```

The call stack changes roughly like this:

```js
Global;
```

Then:

```js
Global;
first();
```

Then:

```js
Global;
first();
second();
```

Then:

```js
Global;
first();
second();
third();
```

After third() finishes:

```js
Global;
first();
second();
```

Then everything is removed until only the global context remains.

**Interview Line**

The call stack is a LIFO data structure JavaScript uses to track active execution contexts and function calls.

### Q. What causes stack overflow?

**Answer:**

A stack overflow happens when too many function execution contexts are added to the call stack without being removed.

A common cause is infinite or excessively deep recursion.

Example:

```js
function test() {
  test();
}

test();
```

Each call creates another function execution context:

```
test()
test()
test()
test()
...
```

Because the function never reaches a stopping condition, the call stack eventually runs out of space.

A browser may show an error such as:

```
RangeError: Maximum call stack size exceeded
```

Stack overflow can also happen with very deeply nested synchronous function calls.

**Interview Line**

A stack overflow occurs when the call stack exceeds its maximum size, usually because of infinite recursion or excessively deep synchronous function calls.

### Q. What is recursion and how can it affect the call stack?

**Answer:**

Recursion is when a function calls itself, directly or indirectly.

Example:

```js
function countdown(n) {
  if (n === 0) {
    return;
  }

  console.log(n);

  countdown(n - 1);
}

countdown(3);
```

Output:

```js
3;
2;
1;
```

Each recursive call creates a new function execution context.

The call stack may look like:

```js
countdown(3);
countdown(2);
countdown(1);
countdown(0);
```

Once the base condition is reached, the calls return one by one.

A proper recursive function therefore needs a base case.

Without one:

```js
function count() {
  count();
}

count();
```

the call stack continues growing until a stack overflow occurs.

**Interview Line**

Recursion occurs when a function calls itself. Every recursive call adds a new frame to the call stack, so missing or unreachable base cases can cause stack overflow.

### Q. What is the memory heap?

**Answer:**

The heap is a region of memory used for dynamically allocated data, especially objects, arrays, functions, and other reference-based values.

Example:

```js
const user = {
  name: "John",
  age: 25,
};
```

Conceptually:

```
user ──────► { name: "John", age: 25 }

stored in heap
```

The variable user holds a reference to the object rather than containing the entire object directly.

Arrays also behave similarly:

```js
const numbers = [10, 20, 30];
```

The array data is managed in dynamically allocated memory.

JavaScript engines automatically manage this memory and reclaim unreachable objects through garbage collection.

**Interview Line**

The heap is dynamically managed memory where JavaScript engines store objects, arrays, functions, and other dynamically allocated data.

### Q. Difference between stack memory and heap memory

**Answer:**

Stack and heap are two concepts commonly used to explain how memory is managed during program execution.

#### Stack

The stack is closely associated with:

- Function calls
- Execution contexts
- Local execution state
- Call frames

It follows a **LIFO** structure.

#### Heap

The heap is used for dynamically allocated data such as objects and arrays.

**Example:**

```js
let age = 25;

const user = {
  name: "John",
};
```

Conceptually:

```txt
Stack / execution state:

age  -> 25
user -> reference
          |
          v

Heap:

{ name: "John" }
```

The exact memory layout is engine-dependent, so it is safer not to assume that every primitive is always physically stored on the stack.

#### Difference Table

| Feature                  | Stack                            | Heap                                        |
| ------------------------ | -------------------------------- | ------------------------------------------- |
| Commonly associated with | Function execution               | Dynamic data                                |
| Structure                | LIFO                             | Dynamically managed                         |
| Typical contents         | Call frames and execution state  | Objects, arrays, functions                  |
| Allocation               | Structured around calls          | Dynamic                                     |
| Cleanup                  | Frames disappear as calls return | Garbage collector reclaims unreachable data |

**Interview Line**

The stack primarily manages function execution and call frames, while the heap stores dynamically allocated data such as objects and arrays.

### Q. What is garbage collection?

**Answer:**

Garbage collection is the automatic process JavaScript engines use to reclaim memory that is no longer reachable by the program.

**Example:**

```js
let user = {
  name: "John",
};

user = null;
```

Initially:

```txt
user -> { name: "John" }
```

After:

```js
user = null;
```

If nothing else references that object, it becomes unreachable.

The JavaScript engine can eventually reclaim its memory.

Developers do not normally manually free memory in JavaScript, unlike languages such as C.

However, garbage collection does not prevent all memory problems. If your application accidentally keeps references to unused objects, they remain reachable and cannot be collected.

**Interview Line**

Garbage collection is JavaScript's automatic memory-management process that removes objects that are no longer reachable by the application.

### Q. What is reachability in garbage collection?

**Answer:**

Reachability means whether a value can still be accessed from one of the program's root references.

Garbage collectors generally preserve reachable objects and reclaim unreachable objects.

Common roots include things such as:

- Global variables
- Currently executing functions
- Active closures
- References held by other reachable objects

**Example:**

```js
let user = {
  name: "John",
};
```

The object is reachable because `user` references it.

```txt
user -> object
```

Now:

```js
user = null;
```

If no other reference exists, the object becomes unreachable.

But consider:

```js
let user = {
  name: "John",
};

let anotherUser = user;

user = null;
```

The object is still reachable through:

```txt
anotherUser
```

Therefore, it cannot yet be garbage-collected.

**Interview Line**

Reachability means whether an object can still be accessed from program roots. Reachable objects stay in memory, while unreachable objects become eligible for garbage collection.

### Q. What is mark-and-sweep algorithm?

**Answer:**

Mark-and-sweep is a common garbage-collection strategy used conceptually by JavaScript engines.

It works in two major steps:

#### 1. Mark

The garbage collector starts from root references such as global variables and active execution contexts.

It marks all objects that can be reached from those roots.

**Example:**

```txt
Root
 |
 v
Object A
 |
 v
Object B
```

Both objects are reachable, so they are marked.

#### 2. Sweep

Objects that were not marked are considered unreachable and their memory can be reclaimed.

**Example:**

```txt
Root -> Object A -> Object B

       Object C
```

If nothing references `Object C`, it is not marked.

During the sweep phase, its memory becomes available for reuse.

Modern JavaScript engines use more sophisticated optimizations in addition to this basic idea, but mark-and-sweep is the core concept interviewers usually expect.

**Interview Line**

Mark-and-sweep garbage collection marks every object reachable from roots and then reclaims memory belonging to objects that were not marked.

### Q. What are common causes of memory leaks?

**Answer:**

A memory leak happens when memory that is no longer useful remains reachable and therefore cannot be garbage-collected.

Common causes include:

- Forgotten event listeners
- Uncleared timers or intervals
- Detached DOM nodes
- Global variables
- Closures holding unnecessary references
- Large caches that never remove entries
- Long-lived data structures

**Example:**

```js
const cache = [];

function saveData(data) {
  cache.push(data);
}
```

If `saveData()` keeps adding large objects forever:

```js
saveData(largeObject);
```

the `cache` array keeps references to them.

Because those objects remain reachable, garbage collection cannot remove them.

Another example is a timer:

```js
setInterval(() => {
  console.log("Running");
}, 1000);
```

If it is no longer needed but never cleared, its callback and referenced values may remain active.

**Interview Line**

Memory leaks occur when unused data remains reachable. Common causes include forgotten listeners, timers, detached DOM nodes, global references, closures, and unbounded caches.

### Q. How do event listeners cause memory leaks?

**Answer:**

Event listeners can contribute to memory leaks when they remain attached longer than necessary and their callbacks keep references to data that should otherwise be released.

**Example:**

```js
const button = document.querySelector("#button");

function handleClick() {
  console.log("Clicked");
}

button.addEventListener("click", handleClick);
```

If the listener is temporary, it should be removed when no longer needed:

```js
button.removeEventListener("click", handleClick);
```

A more problematic example is:

```js
function setup() {
  const largeData = new Array(1000000).fill("data");

  function handleClick() {
    console.log(largeData.length);
  }

  window.addEventListener("click", handleClick);
}
```

The event listener references `handleClick`, and the closure references `largeData`.

So `largeData` can remain reachable as long as the listener exists.

A common cleanup pattern is:

```js
window.removeEventListener("click", handleClick);
```

You can also use an `AbortController` in modern browser code:

```js
const controller = new AbortController();

window.addEventListener("click", handleClick, {
  signal: controller.signal,
});

controller.abort();
```

**Interview Line**

Event listeners can cause memory leaks when long-lived targets retain callbacks that reference unused data. Removing listeners or using cleanup mechanisms allows those references to be released.

### Q. How do timers cause memory leaks?

**Answer:**

Timers can cause memory leaks when callbacks remain scheduled and continue holding references to objects that are no longer needed.

This commonly happens with `setInterval()`.

**Example:**

```js
const intervalId = setInterval(() => {
  console.log("Running...");
}, 1000);
```

The interval continues until it is explicitly cleared:

```js
clearInterval(intervalId);
```

Consider:

```js
function startTask() {
  const largeData = new Array(1000000).fill("data");

  const intervalId = setInterval(() => {
    console.log(largeData.length);
  }, 1000);
}
```

The interval callback closes over `largeData`.

Even after `startTask()` finishes, the timer still references the callback, and the callback references `largeData`.

So the data may remain reachable.

Cleanup:

```js
clearInterval(intervalId);
```

`setTimeout()` can also temporarily retain references until it runs or is cleared, although repeating intervals are a more common source of long-lived leaks.

**Interview Line**

Timers can cause memory leaks when active callbacks keep references to unused data. Long-running `setInterval()` calls should be cleared when they are no longer needed.

### Q. How do detached DOM nodes cause memory leaks?

**Answer:**

A detached DOM node is an element that has been removed from the document but is still referenced somewhere in JavaScript.

**Example:**

```js
const element = document.querySelector("#box");

element.remove();
```

The element is removed from the DOM, but the variable still references it:

```txt
element
```

Therefore, the object can still remain in memory.

A more common pattern is storing DOM elements inside long-lived collections:

```js
const elements = [];

const element = document.querySelector("#box");

elements.push(element);

element.remove();
```

Even though the element is no longer visible on the page, the array still references it.

Conceptually:

```txt
elements
   |
   v
detached DOM node
```

Therefore, garbage collection cannot reclaim it.

Cleanup may involve removing unnecessary references:

```js
elements.length = 0;
```

Detached DOM nodes become particularly problematic when they reference large DOM subtrees or are retained by listeners and closures.

**Interview Line**

A detached DOM node is removed from the document but still referenced by JavaScript. Because it remains reachable, garbage collection cannot remove it.

### Q. What is the event loop?

**Answer:**

The event loop is the mechanism that coordinates asynchronous JavaScript operations with the call stack.

JavaScript executes synchronous code using the call stack.

Asynchronous operations such as timers, network callbacks, and Promise handlers are scheduled for later execution.

A simplified model contains:

- Call stack
- Web APIs or runtime APIs
- Task queue
- Microtask queue
- Event loop

**Example:**

```js
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

console.log("End");
```

**Output:**

```txt
Start
End
Timeout
```

Even though the timeout is `0`, its callback does not execute immediately.

It is scheduled as a task.

The event loop waits until the current call stack becomes empty before allowing queued work to run.

Promises have special scheduling behavior because Promise callbacks go into the microtask queue, which is normally processed before the next regular task.

**Interview Line**

The event loop coordinates the call stack and asynchronous queues, allowing JavaScript to execute asynchronous callbacks after the current synchronous code finishes.

### Q. Explain event loop with Promise and setTimeout example.

**Answer:**

The difference between Promise callbacks and `setTimeout()` callbacks is one of the most common event-loop interview questions.

Consider:

```js
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

Promise.resolve().then(() => {
  console.log("Promise");
});

console.log("End");
```

**Output:**

```txt
Start
End
Promise
Timeout
```

Let's understand why.

#### Step 1: Execute synchronous code

JavaScript starts with:

```js
console.log("Start");
```

Output:

```txt
Start
```

#### Step 2: Schedule the timer

```js
setTimeout(() => {
  console.log("Timeout");
}, 0);
```

The callback is scheduled for a future task.

It does not execute immediately.

#### Step 3: Schedule the Promise callback

```js
Promise.resolve().then(() => {
  console.log("Promise");
});
```

The `.then()` callback is scheduled in the microtask queue.

#### Step 4: Continue synchronous execution

```js
console.log("End");
```

Output now becomes:

```txt
Start
End
```

#### Step 5: Process microtasks

After the current call stack becomes empty, JavaScript processes the microtask queue.

So:

```txt
Promise
```

runs next.

#### Step 6: Process the next task

After microtasks are drained, the event loop can process the timer task.

So:

```txt
Timeout
```

runs last.

#### Queue Priority

A simplified order is:

```txt
Synchronous Code
↓
Microtasks
↓
Next Task
```

Promise callbacks such as:

- `.then()`
- `.catch()`
- `.finally()`

are scheduled as microtasks.

Timer callbacks such as:

- `setTimeout()`
- `setInterval()`

are processed as tasks.

**Interview Line**

After synchronous code finishes, the event loop drains the microtask queue before processing the next task. Therefore, Promise callbacks usually run before `setTimeout(..., 0)` callbacks scheduled in the same turn.

### Q. What is starvation in the microtask queue?

**Answer:**

Microtask starvation occurs when new microtasks are continuously added to the microtask queue, preventing the event loop from moving on to regular tasks such as timers or rendering work.

The event loop generally drains the microtask queue before moving to the next task.

Consider:

```js
function repeat() {
  Promise.resolve().then(() => {
    console.log("Microtask");
    repeat();
  });
}

repeat();

setTimeout(() => {
  console.log("Timeout");
}, 0);
```

The Promise callback runs as a microtask.

Inside that callback, another Promise microtask is created:

```js
repeat();
```

So the process becomes:

```txt
Microtask
↓
creates another microtask
↓
Microtask
↓
creates another microtask
↓
...
```

The queue may never become empty.

As a result, the event loop may have difficulty reaching:

```js
setTimeout(...)
```

and other regular tasks.

This can also delay:

- UI rendering
- User input handling
- Timers
- Other queued work

#### Another Example

```js
function endlessMicrotasks() {
  queueMicrotask(endlessMicrotasks);
}

endlessMicrotasks();

setTimeout(() => {
  console.log("May be delayed indefinitely");
}, 0);
```

Each microtask schedules another microtask before the queue has a chance to fully drain.

#### How to Avoid It

Avoid creating unlimited chains of microtasks.

If a long-running process needs to allow other work to execute, occasionally yield control using an appropriate task-based mechanism.

For example:

```js
function processItems(items, index = 0) {
  if (index >= items.length) return;

  // Process a portion of work

  setTimeout(() => {
    processItems(items, index + 1);
  }, 0);
}
```

This allows the event loop to process other tasks between chunks of work.

**Interview Line**

Microtask starvation happens when microtasks continuously schedule more microtasks, preventing the queue from emptying and delaying timers, rendering, and other regular tasks.

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

### Q. Difference between event.target and event.currentTarget

**Answer:**

1. `event.target`

Definition

Refers to the actual element that triggered the event

Example

```html
<div onclick="handleClick(event)">
  <button>Click Me</button>
</div>
```

```js
function handleClick(e) {
  console.log(e.target);
}
```

👉 If you click the button, `event.target` = button

Key Point

- Always points to the deepest (origin) element

2. `event.currentTarget`

Definition

Refers to the element on which the event listener is attached

Example

```js
function handleClick(e) {
  console.log(e.currentTarget);
}
```

👉 If listener is on div, then

event.currentTarget = div

🔥 Key Differences

| Feature                  | `event.target`               | `event.currentTarget`  |
| ------------------------ | ---------------------------- | ---------------------- |
| Meaning                  | Element that triggered event | Element with listener  |
| Changes during bubbling? | ❌ No                        | ✅ Yes                 |
| Use case                 | Identify clicked element     | Handle event on parent |

Example with Both

```js
document.querySelector("div").addEventListener("click", (e) => {
  console.log("target:", e.target);
  console.log("currentTarget:", e.currentTarget);
});
```

👉 Clicking button inside div:

```
target → button
currentTarget → div
```

Real Use Case

✅ Event Delegation

```js
document.querySelector("ul").addEventListener("click", (e) => {
  if (e.target.tagName === "LI") {
    console.log("Item clicked:", e.target.textContent);
  }
});
```

🚀 Final Summary

- target → where event originated
- currentTarget → where handler is attached
- Important for event delegation

**🔥 Interview Line**

event.target is the element that triggered the event, while event.currentTarget is the element where the event listener is attached.

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

### Q. What is `requestAnimationFrame()`?

**Answer:**

`requestAnimationFrame()` schedules a function to run before the next repaint.

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

### Q. Difference between DOM and BOM

**Answer:**

The **DOM (Document Object Model)** represents the HTML document loaded in the browser. It allows JavaScript to read, modify, add, or remove elements from the page.

Examples of DOM objects:

```js
document;
document.body;
document.querySelector();
```

The **BOM (Browser Object Model)** represents browser-related features outside the HTML document.

Examples of BOM objects:

```js
window;
navigator;
location;
history;
screen;
```

Example:

```js
document.querySelector("h1"); // DOM
window.location.href; // BOM
```

In short:

- DOM deals with the **web page/document**
- BOM deals with the **browser environment**

### Q. Difference between NodeList and HTMLCollection

**Answer:**

Both `NodeList` and `HTMLCollection` are array-like collections returned by some DOM APIs, but they are different.

| Feature             | NodeList                 | HTMLCollection             |
| ------------------- | ------------------------ | -------------------------- |
| Can contain         | Different types of nodes | HTML elements only         |
| Usually returned by | `querySelectorAll()`     | `getElementsByClassName()` |
| `forEach()`         | Usually available        | Not directly available     |
| Live/static         | Can be live or static    | Usually live               |

Example:

```js
const nodes = document.querySelectorAll(".item");
const elements = document.getElementsByClassName("item");
```

A `NodeList` may contain element nodes, text nodes, and other node types depending on the API.

An `HTMLCollection` contains only HTML elements.

### Q. Difference between live and static collections

**Answer:**

A **live collection** automatically updates when the DOM changes.

Example:

```js
const items = document.getElementsByClassName("item");

console.log(items.length);

const div = document.createElement("div");
div.className = "item";
document.body.appendChild(div);

console.log(items.length);
```

The second length automatically includes the new element.

A **static collection** is a snapshot of the DOM at the time the query was executed.

```js
const items = document.querySelectorAll(".item");
```

If new matching elements are later added, the existing `NodeList` does not automatically update.

Common examples:

- `getElementsByClassName()` → live
- `getElementsByTagName()` → live
- `querySelectorAll()` → static

Static collections are often easier to work with because they do not unexpectedly change while being iterated.

### Q. Difference between `querySelector()` and `getElementById()`

**Answer:**

`getElementById()` searches for an element using its `id`.

```js
const element = document.getElementById("title");
```

`querySelector()` accepts any valid CSS selector.

```js
const element = document.querySelector("#title");
const button = document.querySelector(".btn");
const input = document.querySelector('input[type="text"]');
```

Important differences:

| `getElementById()`            | `querySelector()`                        |
| ----------------------------- | ---------------------------------------- |
| Searches only by ID           | Supports any CSS selector                |
| No `#` required               | Uses CSS selector syntax                 |
| Very specific API             | More flexible                            |
| Returns one element or `null` | Returns first matching element or `null` |

For normal application code, the performance difference is usually insignificant. Choose based on readability and selector requirements.

### Q. Difference between `innerHTML`, `innerText`, and `textContent`

**Answer:**

All three access element content, but they behave differently.

#### `innerHTML`

Reads or writes HTML markup.

```js
element.innerHTML = "<strong>Hello</strong>";
```

The browser parses the string as HTML.

#### `innerText`

Returns the text as it is visually rendered.

```js
console.log(element.innerText);
```

It considers CSS visibility and layout.

For example, text inside an element with `display: none` may not appear in `innerText`.

#### `textContent`

Returns all text content inside the node regardless of whether it is visually hidden.

```js
console.log(element.textContent);
```

It does not parse HTML when assigning values.

```js
element.textContent = "<strong>Hello</strong>";
```

This displays the literal text:

```text
<strong>Hello</strong>
```

For inserting plain text, `textContent` is generally safer than `innerHTML`.

### Q. Why can `innerHTML` be dangerous?

**Answer:**

`innerHTML` can be dangerous when untrusted user input is inserted directly into the DOM because the browser interprets the value as HTML.

Example:

```js
const userInput = '<img src="x" onerror="alert(1)">';

element.innerHTML = userInput;
```

This can create a **Cross-Site Scripting (XSS)** vulnerability.

An attacker may inject malicious HTML or JavaScript that runs in another user's browser.

Safer options include:

```js
element.textContent = userInput;
```

or creating DOM elements explicitly:

```js
const p = document.createElement("p");
p.textContent = userInput;
element.appendChild(p);
```

If HTML must be accepted, it should be sanitized using a trusted HTML sanitization solution.

The main rule is:

> Never insert untrusted data directly into `innerHTML`.

### Q. What is event delegation?

**Answer:**

Event delegation is a technique where we attach one event listener to a parent element instead of attaching separate listeners to many child elements.

Because many DOM events bubble upward, the parent can inspect `event.target` to determine which child triggered the event.

Example:

```html
<ul id="list">
  <li data-id="1">Item 1</li>
  <li data-id="2">Item 2</li>
  <li data-id="3">Item 3</li>
</ul>
```

```js
const list = document.getElementById("list");

list.addEventListener("click", (event) => {
  const item = event.target.closest("li");

  if (!item) return;

  console.log(item.dataset.id);
});
```

Only one event listener is required for all list items.

It also works for list items added dynamically later.

### Q. How does event delegation improve performance?

**Answer:**

Without event delegation, a large list may require one event listener for every element.

For example, 1,000 buttons could result in 1,000 separate click listeners.

With delegation:

```js
container.addEventListener("click", handler);
```

only one listener is attached to the parent.

Benefits include:

- Fewer event listeners
- Lower memory usage
- Less setup work
- Automatically supports dynamically added children
- Simpler cleanup

The performance benefit becomes more noticeable when handling large or frequently changing DOM collections.

However, event delegation only works well for events that participate appropriately in event propagation.

### Q. Difference between event bubbling and capturing

**Answer:**

When an event occurs on a nested element, it moves through the DOM in phases.

Consider:

```html
<div id="parent">
  <button id="child">Click</button>
</div>
```

#### Capturing phase

The event travels from the top of the DOM toward the target:

```text
window
↓
document
↓
parent
↓
button
```

#### Bubbling phase

After reaching the target, it travels back upward:

```text
button
↑
parent
↑
document
↑
window
```

By default, event listeners usually listen during the bubbling phase.

```js
parent.addEventListener("click", handler);
```

To listen during capturing:

```js
parent.addEventListener("click", handler, {
  capture: true,
});
```

Event delegation usually relies on bubbling.

### Q. What is event propagation?

**Answer:**

Event propagation describes how an event travels through the DOM hierarchy.

It mainly consists of three phases:

1. **Capturing phase**
2. **Target phase**
3. **Bubbling phase**

For example, clicking a button inside a `<div>` may cause listeners on the button, parent div, document, and other ancestors to run depending on how those listeners were registered.

Understanding propagation is important for:

- Event delegation
- Preventing unwanted parent handlers
- Modal and dropdown behavior
- Nested clickable components

### Q. Difference between `stopPropagation()` and `stopImmediatePropagation()`

**Answer:**

`stopPropagation()` prevents the event from continuing to propagate to ancestor or descendant propagation targets.

Example:

```js
button.addEventListener("click", (event) => {
  event.stopPropagation();
});
```

The parent click listener will not receive the bubbling event.

`stopImmediatePropagation()` goes further.

It prevents:

1. Further propagation
2. Other listeners registered on the same element from running

Example:

```js
button.addEventListener("click", (event) => {
  event.stopImmediatePropagation();
  console.log("First");
});

button.addEventListener("click", () => {
  console.log("Second");
});
```

The second listener will not execute.

So:

- `stopPropagation()` → stops propagation through the DOM
- `stopImmediatePropagation()` → also stops remaining listeners on the same element

### Q. Difference between `preventDefault()` and `stopPropagation()`

**Answer:**

They solve completely different problems.

`preventDefault()` prevents the browser's default behavior.

Example:

```js
link.addEventListener("click", (event) => {
  event.preventDefault();
});
```

The link click event still exists and can still bubble, but the browser will not navigate to the link.

`stopPropagation()` prevents the event from continuing through the DOM hierarchy.

```js
button.addEventListener("click", (event) => {
  event.stopPropagation();
});
```

It does not automatically prevent the browser's default behavior.

For example, stopping propagation on a link does not necessarily prevent navigation.

### Q. What is passive event listener?

**Answer:**

A passive event listener tells the browser that the listener will **not call `preventDefault()`**.

Example:

```js
window.addEventListener("touchmove", handleTouch, { passive: true });
```

This is especially useful for scrolling-related events such as:

- `touchstart`
- `touchmove`
- `wheel`

Without knowing whether the handler might call `preventDefault()`, the browser may need to wait before performing scrolling.

With `passive: true`, the browser knows scrolling can proceed immediately.

This can improve scrolling performance.

However, a passive listener should not be used when the handler genuinely needs to call `preventDefault()`.

### Q. What is the use of `dataset`?

**Answer:**

`dataset` provides access to custom HTML `data-*` attributes.

Example:

```html
<button data-user-id="101" data-role="admin">Delete</button>
```

JavaScript:

```js
const button = document.querySelector("button");

console.log(button.dataset.userId);
console.log(button.dataset.role);
```

Output:

```text
101
admin
```

`data-user-id` becomes:

```js
dataset.userId;
```

It is useful for storing small pieces of UI-related metadata directly on elements, especially for event delegation.

However, sensitive information should not be stored in `data-*` attributes because users can inspect and modify DOM values.

### Q. Difference between localStorage, sessionStorage, and cookies

**Answer:**

All three store data in the browser, but they have different purposes.

| Feature                      | localStorage  | sessionStorage           | Cookies                       |
| ---------------------------- | ------------- | ------------------------ | ----------------------------- |
| Persistence                  | Until removed | Until tab/session closes | Based on expiry               |
| Sent to server automatically | No            | No                       | Yes                           |
| Typical capacity             | Several MB    | Several MB               | Small, around a few KB each   |
| Scope                        | Origin        | Origin + tab/session     | Domain/path rules             |
| JavaScript access            | Yes           | Yes                      | Usually yes unless `HttpOnly` |

`localStorage` is useful for persistent non-sensitive browser preferences.

`sessionStorage` is useful for temporary data that should exist only for that browser tab/session.

Cookies are commonly used for server-related state such as sessions because the browser can automatically send them with HTTP requests.

For authentication, secure `HttpOnly` cookies are generally safer than storing sensitive tokens in JavaScript-accessible storage.

### Q. When should you not use localStorage?

**Answer:**

Avoid `localStorage` for sensitive information such as:

- Passwords
- Authentication secrets
- Refresh tokens
- Highly sensitive personal information

The main reason is that JavaScript running on the page can access `localStorage`.

If an application has an XSS vulnerability, malicious JavaScript may read stored data:

```js
localStorage.getItem("token");
```

`localStorage` is also synchronous, so very large or frequent reads and writes can block the main thread.

It is best suited for small, non-sensitive values such as:

- Theme preference
- UI settings
- Draft state
- Non-sensitive cache hints

### Q. What is IndexedDB?

**Answer:**

IndexedDB is a browser database designed for storing larger amounts of structured data.

Unlike `localStorage`, it supports:

- Objects
- Indexed searching
- Transactions
- Large datasets
- Asynchronous operations
- Offline application data

Typical use cases include:

- Offline-first applications
- Large cached API datasets
- Draft documents
- File/blob storage
- Complex client-side application state

IndexedDB is transactional and works more like a small database than a simple key-value storage mechanism.

### Q. Difference between localStorage and IndexedDB

**Answer:**

`localStorage` is a simple synchronous key-value store.

```js
localStorage.setItem("user", JSON.stringify(user));
```

IndexedDB is an asynchronous structured database.

Major differences:

| Feature      | localStorage  | IndexedDB       |
| ------------ | ------------- | --------------- |
| API          | Simple        | More complex    |
| Async        | No            | Yes             |
| Data type    | Strings       | Structured data |
| Large data   | Not ideal     | Designed for it |
| Indexes      | No            | Yes             |
| Transactions | No            | Yes             |
| Files/Blobs  | Not practical | Supported       |

Use `localStorage` for small settings.

Use IndexedDB for larger, structured, queryable, or offline data.

### Q. What is `requestAnimationFrame()`?

**Answer:**

`requestAnimationFrame()` asks the browser to execute a callback before the next repaint.

Example:

```js
function animate() {
  updatePosition();

  requestAnimationFrame(animate);
}

requestAnimationFrame(animate);
```

It is designed specifically for visual animation.

The browser coordinates the callback with its rendering cycle, making animations smoother and more efficient than repeatedly using arbitrary timers.

It also allows the browser to reduce or pause animation work when the page is not visible.

### Q. Difference between `requestAnimationFrame()` and `setTimeout()`

**Answer:**

`setTimeout()` executes a callback after a minimum delay.

```js
setTimeout(() => {
  console.log("Executed");
}, 16);
```

It is not synchronized with browser repainting.

`requestAnimationFrame()` runs before the browser's next repaint and is specifically designed for animations.

```js
requestAnimationFrame(() => {
  updateAnimation();
});
```

For visual animations, `requestAnimationFrame()` is preferred because it:

- Synchronizes with rendering
- Avoids unnecessary frames
- Produces smoother animation
- Can reduce work in background tabs

Use `setTimeout()` for general delayed execution and `requestAnimationFrame()` for frame-based visual updates.

### Q. What is Intersection Observer API?

**Answer:**

The Intersection Observer API detects when an element enters or leaves a viewport or another specified container.

Example:

```js
const observer = new IntersectionObserver((entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      console.log("Element is visible");
    }
  });
});

observer.observe(document.querySelector(".target"));
```

Common use cases include:

- Lazy loading images
- Infinite scrolling
- Detecting visible sections
- Triggering animations
- Analytics for viewed content

It is generally better than repeatedly checking element positions using scroll events and `getBoundingClientRect()`.

### Q. What is MutationObserver?

**Answer:**

`MutationObserver` watches for changes in the DOM.

It can detect changes such as:

- Elements being added or removed
- Attribute changes
- Text changes

Example:

```js
const observer = new MutationObserver((mutations) => {
  console.log(mutations);
});

observer.observe(document.body, {
  childList: true,
  subtree: true,
});
```

It is useful when code needs to react to DOM changes made by another component, library, browser extension, or external script.

It should not normally replace proper application state management.

### Q. What is ResizeObserver?

**Answer:**

`ResizeObserver` watches changes to an element's dimensions.

Example:

```js
const observer = new ResizeObserver((entries) => {
  for (const entry of entries) {
    console.log(entry.contentRect.width);
  }
});

observer.observe(document.querySelector(".container"));
```

It is useful when behavior depends on the size of a particular element rather than the entire browser window.

Common use cases include:

- Responsive components
- Charts
- Canvas resizing
- Dynamic layouts
- Virtualized interfaces

It is usually more appropriate than listening to `window.resize` when the actual requirement concerns an individual element.

### Q. What is History API?

**Answer:**

The History API allows JavaScript to interact with the browser's session history.

Important methods include:

```js
history.pushState();
history.replaceState();
history.back();
history.forward();
history.go();
```

It enables client-side applications to change the URL without performing a full page reload.

For example:

```js
history.pushState({ page: 2 }, "", "/products?page=2");
```

The browser URL changes, but the page is not automatically reloaded.

This API is one of the foundations used by client-side routers in SPAs.

### Q. Difference between `pushState()` and `replaceState()`

**Answer:**

`pushState()` creates a new browser history entry.

```js
history.pushState({ page: 2 }, "", "/page-2");
```

The user can press Back to return to the previous entry.

`replaceState()` modifies the current history entry instead of creating a new one.

```js
history.replaceState({ page: 2 }, "", "/page-2");
```

Use `pushState()` when navigation should become part of browser history.

Use `replaceState()` when the current URL should be corrected or updated without adding another Back-button step.

### Q. What is Service Worker?

**Answer:**

A Service Worker is a background script that sits between the browser application and the network.

It can intercept network requests and control how responses are handled.

Common capabilities include:

- Offline caching
- Network request interception
- Cache-first/network-first strategies
- Push notifications
- Background synchronization
- Progressive Web App functionality

A simplified registration looks like:

```js
if ("serviceWorker" in navigator) {
  navigator.serviceWorker.register("/service-worker.js");
}
```

A Service Worker does not directly manipulate the page DOM.

It runs separately from the page and communicates with pages through messaging APIs.

### Q. What is Web Worker?

**Answer:**

A Web Worker allows JavaScript to execute CPU-intensive work on a separate background thread from the browser's main UI thread.

Example:

```js
const worker = new Worker("worker.js");

worker.postMessage({
  numbers: [1, 2, 3],
});

worker.onmessage = (event) => {
  console.log(event.data);
};
```

Inside `worker.js`:

```js
self.onmessage = (event) => {
  const result = event.data.numbers.reduce((sum, value) => sum + value, 0);

  self.postMessage(result);
};
```

Web Workers are useful for:

- Large calculations
- Parsing large datasets
- Image processing
- Data transformations
- CPU-intensive algorithms

A Web Worker cannot directly access the DOM. It communicates with the main thread using messages.

#### Service Worker vs Web Worker

A useful interview distinction is:

| Web Worker                         | Service Worker                                       |
| ---------------------------------- | ---------------------------------------------------- |
| Used for background computation    | Used mainly for network/background capabilities      |
| Created by a page                  | Registered for an origin/scope                       |
| Usually lives while needed by page | Can run independently from a specific open page      |
| Good for CPU-heavy tasks           | Good for offline caching, push, network interception |
| Cannot access DOM                  | Cannot access DOM                                    |

Both run outside the main browser UI thread, but they solve different problems.

## ES6+ Features (Very Important)

### Q. What is ES6?

**Answer:**

ES6 (ECMAScript 2015) is a major update to JavaScript that introduced modern syntax and features to write cleaner, more maintainable, and scalable code.

Explanation

Before ES6, JavaScript had limitations in variable scoping, modularity, and readability. ES6 solved these by adding features like:

- `let` and `const`
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

**Answer:**

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

**Answer:**

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

**Answer:**

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

**Answer:**

Both use `...` but serve different purposes.

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

**Answer:**

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

**Answer:**

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

**Answer:**

Optional chaining safely accesses nested object properties without throwing errors.

Example

```js
user?.address?.city;
```

Explanation

If any part is null or undefined, it returns undefined instead of crashing.

### Q. Nullish Coalescing (??)

**Answer:**

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

**Answer:**

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

**Answer:**

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

**Answer:**

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

**Answer:**

`BigInt` is used to represent numbers larger than Number.MAX_SAFE_INTEGER.

Example

```js
const big = 12345678901234567890n;
```

Interview Tip

- Cannot mix `BigInt` and `Number` directly

### Q. What is `Object.entries()`?

**Answer:**

Returns an array of [key, value] pairs from an object.

Example

```js
const obj = { a: 1, b: 2 };
Object.entries(obj);
// [["a",1], ["b",2]]
```

Use Case

- Iterating objects easily

### Q. What is `Object.values()`?

**Answer:**

Returns an array of all values of an object.

Example

```js
Object.values({ a: 1, b: 2 });
// [1, 2]
```

Common Use

- Calculations
- Transforming object data

### Q. Explain `new Map()`

**Answer:**

`Map` is a built-in JavaScript collection used to store key-value pairs.

Unlike normal objects, a `Map` allows keys of any data type.

Keys can be:

- Strings
- Numbers
- Objects
- Functions
- Symbols

A `Map` also preserves insertion order and provides built-in methods to add, retrieve, delete, and check values.

**Example:**

```js
const userMap = new Map();

userMap.set("name", "John");
userMap.set("age", 25);

console.log(userMap.get("name"));
console.log(userMap.has("age"));
console.log(userMap.size);
```

Output:

```js
John;
true;
2;
```

Objects can also be used as keys:

```js
const user = { id: 1 };

const map = new Map();

map.set(user, "Admin");

console.log(map.get(user));
```

Output:

```js
Admin;
```

This is one major advantage over normal objects because object keys are usually strings or symbols.

**Interview Line**

`Map` is a key-value collection that supports keys of any data type, preserves insertion order, and provides convenient methods such as `set()`, `get()`, `has()`, and `delete()`.

### Q. Difference between `import` and `require`

**Answer:**

Both `import` and `require` are used to load modules, but they belong to different module systems.

`import` belongs to ES Modules.

```js
import { add } from "./math.js";
```

`require` belongs to CommonJS.

```js
const { add } = require("./math");
```

The main differences are:

| `import`                          | `require`                      |
| --------------------------------- | ------------------------------ |
| ES Modules                        | CommonJS                       |
| Static by default                 | Runtime function call          |
| Supports tree shaking better      | Harder to tree shake           |
| Uses `export`                     | Uses `module.exports`          |
| Standard JavaScript module syntax | Mainly associated with Node.js |

Because static `import` statements are analyzed before execution, bundlers can understand module dependencies more easily.

Modern JavaScript and modern Node.js projects generally prefer ES Modules.

**Interview Line**

`import` is the standard ES Module syntax and is statically analyzable, while `require` belongs to CommonJS and loads modules through a runtime function call.

### Q. What are the most important ES6 features?

**Answer:**

ES6, also called ECMAScript 2015, introduced many major JavaScript features that are now commonly used in modern development.

Important ES6 features include:

1. `let` and `const`
2. Arrow functions
3. Template literals
4. Destructuring
5. Default parameters
6. Rest and spread syntax
7. Classes
8. Modules using `import` and `export`
9. Promises
10. `Map` and `Set`
11. Symbols
12. Enhanced object literals

**Example:**

```js
const user = {
  name: "John",
  age: 25,
};

const { name, age } = user;

const greet = () => {
  console.log(`Hello ${name}`);
};

greet();
```

Here we are using:

- `const`
- Object destructuring
- Arrow function
- Template literal

ES6 made JavaScript more expressive and significantly improved modularity and readability.

**Interview Line**

ES6 introduced major modern JavaScript features such as `let`, `const`, arrow functions, destructuring, classes, modules, promises, template literals, and rest/spread syntax.

### Q. Difference between CommonJS and ES Modules

**Answer:**

CommonJS and ES Modules are two different module systems used in JavaScript.

CommonJS mainly became popular through Node.js.

**CommonJS Example:**

```js
const math = require("./math");

module.exports = {
  add,
};
```

ES Modules are the official JavaScript module standard.

**ES Module Example:**

```js
import { add } from "./math.js";

export { add };
```

Major differences:

| CommonJS                       | ES Modules                           |
| ------------------------------ | ------------------------------------ |
| Uses `require()`               | Uses `import`                        |
| Uses `module.exports`          | Uses `export`                        |
| Traditionally synchronous      | Designed for static module structure |
| Mainly associated with Node.js | Standard in browsers and Node.js     |
| Harder for tree shaking        | Better suited for tree shaking       |

Modern frontend projects and newer Node.js applications generally prefer ES Modules.

**Interview Line**

CommonJS uses `require` and `module.exports`, while ES Modules use `import` and `export` and are the standard module system in modern JavaScript.

### Q. Difference between named export and default export

**Answer:**

A named export exports a value using its specific name.

**Example:**

```js
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
```

Import:

```js
import { add, subtract } from "./math.js";
```

A default export represents the primary exported value of a module.

**Example:**

```js
export default function Calculator() {
  return "Calculator";
}
```

Import:

```js
import Calculator from "./Calculator.js";
```

With named exports, the imported name normally matches the exported name.

With a default export, the importer can choose a different local name.

```js
import MyCalculator from "./Calculator.js";
```

A module can have multiple named exports but only one default export.

**Interview Line**

Named exports allow multiple explicitly named exports from a module, while a module can have only one default export and it can be imported using any local name.

### Q. Can we mix default and named exports?

**Answer:**

Yes.

A module can contain one default export along with multiple named exports.

**Example:**

```js
export const API_URL = "https://api.example.com";

export function validateUser() {
  return true;
}

export default function UserService() {
  return "User Service";
}
```

Import:

```js
import UserService, { API_URL, validateUser } from "./userService.js";
```

Here:

- `UserService` is the default export
- `API_URL` is a named export
- `validateUser` is a named export

This pattern can be useful when a module has one primary export and a few supporting utilities.

**Interview Line**

Yes, a module can have one default export together with multiple named exports.

### Q. What is dynamic import?

**Answer:**

Dynamic import allows a module to be loaded only when it is needed.

It uses the `import()` function-like syntax and returns a Promise.

**Example:**

```js
async function loadModule() {
  const module = await import("./math.js");

  console.log(module.add(2, 3));
}

loadModule();
```

Unlike a normal static import:

```js
import { add } from "./math.js";
```

dynamic import happens at runtime.

It is useful for:

- Code splitting
- Lazy loading
- Loading optional features
- Reducing initial JavaScript bundle size

For example, a large chart library can be loaded only when the user opens the analytics page.

**Interview Line**

Dynamic import uses `import()` to load modules at runtime and is commonly used for lazy loading and code splitting.

### Q. What is tree shaking?

**Answer:**

Tree shaking is a build optimization technique that removes unused code from the final JavaScript bundle.

Suppose a module exports two functions:

```js
export function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}
```

But the application only imports:

```js
import { add } from "./math.js";
```

A bundler may remove the unused `subtract` function from the production bundle.

This reduces:

- Bundle size
- Download time
- Parsing time
- JavaScript execution cost

Tree shaking is commonly performed by bundlers such as Webpack, Rollup, and modern build systems.

**Interview Line**

Tree shaking removes unused exported code from production bundles, helping reduce JavaScript bundle size.

### Q. How do ES Modules help tree shaking?

**Answer:**

ES Modules use a static module structure.

For example:

```js
import { add } from "./math.js";
```

The bundler can determine which exports are being used without executing the code.

Similarly:

```js
export function add() {}
export function subtract() {}
```

The exported names are known during build time.

Because imports and exports can be statically analyzed, bundlers can safely identify unused exports and remove them.

CommonJS is more difficult to analyze because `require()` can be called dynamically at runtime.

**Example:**

```js
const moduleName = "./" + fileName;

const module = require(moduleName);
```

The dependency cannot always be determined at build time.

**Interview Line**

ES Modules help tree shaking because their static `import` and `export` syntax allows bundlers to determine module dependencies and unused exports during build time.

### Q. What is destructuring?

**Answer:**

Destructuring is a JavaScript syntax used to extract values from arrays or properties from objects into variables.

**Object Example:**

```js
const user = {
  name: "John",
  age: 25,
};

const { name, age } = user;

console.log(name);
console.log(age);
```

**Array Example:**

```js
const colors = ["red", "blue"];

const [first, second] = colors;

console.log(first);
console.log(second);
```

Output:

```js
red;
blue;
```

Destructuring reduces repetitive property access and makes assignments more concise.

Instead of:

```js
const name = user.name;
const age = user.age;
```

we can write:

```js
const { name, age } = user;
```

**Interview Line**

Destructuring is a concise syntax for extracting values from arrays or properties from objects into separate variables.

### Q. Difference between array destructuring and object destructuring

**Answer:**

Array destructuring extracts values based on their position.

**Example:**

```js
const colors = ["red", "blue", "green"];

const [first, second] = colors;
```

Here:

```js
first = "red";
second = "blue";
```

Object destructuring extracts values based on property names.

**Example:**

```js
const user = {
  name: "John",
  age: 25,
};

const { name, age } = user;
```

The important difference is:

- Array destructuring is based on **position**
- Object destructuring is based on **property name**

For arrays, changing the order changes the assigned values.

For objects, property order does not matter.

**Interview Line**

Array destructuring matches values by position, while object destructuring matches values by property name.

### Q. What are default values in destructuring?

**Answer:**

Default values allow a fallback value to be assigned when the destructured value is `undefined`.

**Example:**

```js
const user = {
  name: "John",
};

const { name, age = 18 } = user;

console.log(name);
console.log(age);
```

Output:

```js
John;
18;
```

The same works with arrays:

```js
const numbers = [10];

const [first, second = 20] = numbers;

console.log(second);
```

Output:

```js
20;
```

Default values are applied when the value is `undefined`.

They are not automatically applied for `null`.

**Interview Line**

Default values in destructuring provide fallback values when the extracted value is `undefined`.

### Q. What is renaming in object destructuring?

**Answer:**

Renaming allows an object property to be assigned to a variable with a different name.

**Example:**

```js
const user = {
  name: "John",
  age: 25,
};

const { name: userName, age: userAge } = user;

console.log(userName);
console.log(userAge);
```

Output:

```js
John;
25;
```

Here:

```js
name;
```

is the object property.

```js
userName;
```

is the local variable.

This is useful when:

- Two objects contain properties with the same name
- A property name is not descriptive enough locally
- We want to avoid variable name conflicts

**Interview Line**

Renaming in object destructuring uses `propertyName: variableName` to store an object property in a differently named local variable.

### Q. What is nested destructuring?

**Answer:**

Nested destructuring allows us to extract values from nested objects or arrays directly.

**Example:**

```js
const user = {
  name: "John",
  address: {
    city: "Mumbai",
    pinCode: 400001,
  },
};

const {
  name,
  address: { city, pinCode },
} = user;

console.log(city);
console.log(pinCode);
```

Output:

```js
Mumbai;
400001;
```

Without nested destructuring, we might write:

```js
const city = user.address.city;
const pinCode = user.address.pinCode;
```

Nested destructuring is useful, but deeply nested patterns can become difficult to read.

**Interview Line**

Nested destructuring extracts values directly from nested objects or arrays using the same destructuring syntax at multiple levels.

### Q. Difference between spread and rest operator

**Answer:**

Spread and rest use the same `...` syntax, but they perform opposite operations depending on the context.

The **spread operator** expands values.

**Example:**

```js
const numbers = [1, 2, 3];

const newNumbers = [...numbers, 4, 5];

console.log(newNumbers);
```

Output:

```js
[1, 2, 3, 4, 5];
```

The **rest operator** collects multiple values into one variable.

**Example:**

```js
function sum(...numbers) {
  return numbers.reduce((total, value) => total + value, 0);
}

console.log(sum(1, 2, 3));
```

Here:

```js
...numbers
```

collects all arguments into an array.

Another example:

```js
const [first, ...remaining] = [1, 2, 3, 4];
```

**Interview Line**

Spread expands values from an array or object, while rest collects multiple values into a single array or object variable.

### Q. What is optional chaining?

**Answer:**

Optional chaining allows safe access to nested properties when an intermediate value might be `null` or `undefined`.

It uses the `?.` operator.

**Example:**

```js
const user = {
  profile: {
    name: "John",
  },
};

console.log(user.profile?.name);
console.log(user.address?.city);
```

Output:

```js
John;
undefined;
```

Without optional chaining, accessing:

```js
user.address.city;
```

would throw an error if `address` is undefined.

Optional chaining can also be used with methods:

```js
user.printDetails?.();
```

and array/property access:

```js
users?.[0];
```

**Interview Line**

Optional chaining `?.` safely accesses nested properties, methods, or array values and returns `undefined` if the previous value is `null` or `undefined`.

### Q. What is nullish coalescing?

**Answer:**

Nullish coalescing uses the `??` operator to provide a fallback value when the left-hand value is `null` or `undefined`.

**Example:**

```js
const userName = null;

const name = userName ?? "Guest";

console.log(name);
```

Output:

```js
Guest;
```

Another example:

```js
const count = 0;

console.log(count ?? 10);
```

Output:

```js
0;
```

This is important because `0` is a valid value and should not always be replaced.

Nullish coalescing only treats these values as missing:

```js
null;
undefined;
```

**Interview Line**

The nullish coalescing operator `??` returns the right-hand fallback only when the left-hand value is `null` or `undefined`.

### Q. Difference between `||` and `??`

**Answer:**

The logical OR operator `||` returns the fallback when the left-hand value is any falsy value.

Falsy values include:

```js
false;
0;
("");
null;
undefined;
NaN;
```

**Example:**

```js
const count = 0;

console.log(count || 10);
```

Output:

```js
10;
```

The nullish coalescing operator `??` only uses the fallback for `null` or `undefined`.

```js
console.log(count ?? 10);
```

Output:

```js
0;
```

This makes `??` better when values such as `0`, `false`, or an empty string are valid application values.

**Interview Line**

`||` falls back for any falsy value, while `??` falls back only when the value is `null` or `undefined`.

### Q. What is Symbol?

**Answer:**

`Symbol` is a primitive data type used to create unique values.

**Example:**

```js
const id1 = Symbol("id");
const id2 = Symbol("id");

console.log(id1 === id2);
```

Output:

```js
false;
```

Even though both symbols have the same description, they are different values.

Symbols are commonly used as unique object property keys.

```js
const id = Symbol("id");

const user = {
  name: "John",
  [id]: 101,
};

console.log(user[id]);
```

Symbol-keyed properties reduce the chance of accidental property name conflicts.

JavaScript also provides built-in well-known symbols such as:

```js
Symbol.iterator;
Symbol.toStringTag;
```

These allow objects to customize certain language behaviors.

**Interview Line**

`Symbol` is a primitive type that creates unique values and is commonly used for unique object keys and customizing built-in JavaScript behavior.

### Q. Where is Symbol used in real projects?

**Answer:**

Symbols are not used as frequently as strings or numbers, but they are useful in certain advanced cases.

One use is creating unique internal object properties.

**Example:**

```js
const internalId = Symbol("internalId");

const user = {
  name: "John",
  [internalId]: 101,
};
```

A library can use a Symbol key without worrying that application code will accidentally create another property with the same string name.

Symbols are also used internally by JavaScript through well-known symbols.

For example:

```js
Symbol.iterator;
```

controls how an object behaves in iteration.

```js
const range = {
  start: 1,
  end: 3,

  *[Symbol.iterator]() {
    for (let value = this.start; value <= this.end; value++) {
      yield value;
    }
  },
};

console.log([...range]);
```

Output:

```js
[1, 2, 3];
```

Real-world uses are common in libraries, frameworks, metadata systems, and custom iterable implementations.

**Interview Line**

In real projects, Symbols are mainly used for collision-free internal properties and for implementing language protocols such as `Symbol.iterator`.

### Q. What is BigInt?

**Answer:**

`BigInt` is a primitive numeric type used to represent integers larger than JavaScript's safe `Number` integer range.

The maximum safe integer for normal `Number` is:

```js
Number.MAX_SAFE_INTEGER;
```

which is:

```js
9007199254740991;
```

A BigInt is created by adding `n` to an integer.

**Example:**

```js
const largeNumber = 900719925474099123456789n;

console.log(largeNumber);
```

It can also be created using:

```js
const value = BigInt("900719925474099123456789");
```

One important rule is that BigInt and Number cannot normally be mixed directly in arithmetic.

```js
const result = 10n + 5;
```

This throws an error.

Instead:

```js
const result = 10n + 5n;
```

**Interview Line**

`BigInt` represents integers beyond JavaScript's safe `Number` range and is created using the `n` suffix or the `BigInt()` function.

### Q. What is `globalThis`?

**Answer:**

`globalThis` provides a standard way to access the global object across different JavaScript environments.

Previously, different environments used different names.

In browsers:

```js
window;
```

In Web Workers:

```js
self;
```

In Node.js:

```js
global;
```

With `globalThis`, the same code can work across environments.

**Example:**

```js
globalThis.appName = "My App";

console.log(globalThis.appName);
```

In a browser:

```js
console.log(globalThis === window);
```

This is generally true for the browser's main window context.

`globalThis` is useful when writing libraries or environment-independent JavaScript.

**Interview Line**

`globalThis` is the standard cross-environment reference to the global object, replacing environment-specific references such as `window`, `self`, or `global`.

### Q. What are private class fields?

**Answer:**

Private class fields are class properties that can only be accessed from inside the class.

They are declared using the `#` prefix.

**Example:**

```js
class BankAccount {
  #balance = 0;

  deposit(amount) {
    this.#balance += amount;
  }

  getBalance() {
    return this.#balance;
  }
}

const account = new BankAccount();

account.deposit(1000);

console.log(account.getBalance());
```

Output:

```js
1000;
```

Trying to access:

```js
account.#balance;
```

outside the class causes an error.

Private fields provide actual language-level encapsulation rather than relying only on naming conventions such as `_balance`.

**Interview Line**

Private class fields use the `#` syntax and can only be accessed within the class that declares them, providing true encapsulation.

### Q. What are static methods in classes?

**Answer:**

Static methods belong to the class itself rather than to individual objects created from the class.

They are declared using the `static` keyword.

**Example:**

```js
class MathUtil {
  static add(a, b) {
    return a + b;
  }
}

console.log(MathUtil.add(2, 3));
```

Output:

```js
5;
```

We do not need to create an object:

```js
const util = new MathUtil();
```

to call the method.

Calling:

```js
util.add();
```

would not work because `add()` belongs to the class.

Static methods are useful for:

- Utility functions
- Factory methods
- Validation helpers
- Class-level operations

**Interview Line**

Static methods belong to the class itself and are called using the class name rather than an instance of the class.

### Q. Difference between instance methods and static methods

**Answer:**

Instance methods belong to objects created from a class.

Static methods belong to the class itself.

**Example:**

```js
class User {
  constructor(name) {
    this.name = name;
  }

  greet() {
    return `Hello ${this.name}`;
  }

  static createGuest() {
    return new User("Guest");
  }
}
```

Instance method:

```js
const user = new User("John");

console.log(user.greet());
```

Static method:

```js
const guest = User.createGuest();
```

The main difference is:

| Instance Method                         | Static Method                       |
| --------------------------------------- | ----------------------------------- |
| Called on an object                     | Called on the class                 |
| Can access instance data through `this` | Mainly works with class-level logic |
| Example: `user.greet()`                 | Example: `User.createGuest()`       |

**Interview Line**

Instance methods operate on individual class instances, while static methods belong to the class itself and are called without creating an instance.

### Q. What is `super` keyword?

**Answer:**

The `super` keyword is used inside a child class to access functionality from its parent class.

It is commonly used in two ways:

1. Calling the parent constructor
2. Calling parent class methods

**Example:**

```js
class Person {
  constructor(name) {
    this.name = name;
  }

  greet() {
    return `Hello ${this.name}`;
  }
}

class Employee extends Person {
  constructor(name, role) {
    super(name);

    this.role = role;
  }

  greet() {
    return `${super.greet()}, role: ${this.role}`;
  }
}

const employee = new Employee("John", "Developer");

console.log(employee.greet());
```

In a derived class constructor, `super()` must be called before accessing `this`.

**Interview Line**

`super` is used in a child class to call the parent constructor or access parent class methods.

### Q. What is class inheritance?

**Answer:**

Class inheritance allows one class to reuse and extend the behavior of another class.

JavaScript uses the `extends` keyword for inheritance.

**Example:**

```js
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound`);
  }
}

class Dog extends Animal {
  bark() {
    console.log(`${this.name} barks`);
  }
}

const dog = new Dog("Bruno");

dog.speak();
dog.bark();
```

`Dog` inherits:

```js
speak();
```

from `Animal` and also defines its own:

```js
bark();
```

method.

Under the hood, JavaScript classes still use prototype-based inheritance.

Class syntax provides a cleaner and more familiar way to work with prototypes.

**Interview Line**

Class inheritance uses `extends` to allow a child class to reuse and extend properties and methods from a parent class.

### Q. What are tagged template literals?

**Answer:**

Tagged template literals allow a function to process a template literal before the final string value is produced.

Normally:

```js
const name = "John";

const message = `Hello ${name}`;
```

With a tagged template:

```js
function tag(strings, value) {
  console.log(strings);
  console.log(value);
}

const name = "John";

tag`Hello ${name}`;
```

The tag function receives:

1. An array containing the static string parts
2. The evaluated expression values

A more practical example:

```js
function highlight(strings, ...values) {
  return strings.reduce((result, string, index) => {
    const value = values[index] ? `<strong>${values[index]}</strong>` : "";

    return result + string + value;
  }, "");
}

const name = "John";

const result = highlight`Hello ${name}`;

console.log(result);
```

Tagged templates are used in real libraries for:

- CSS-in-JS
- SQL query builders
- Localization
- Escaping or sanitizing values
- Custom string processing

For example, libraries can use tagged templates to distinguish static text from dynamic values.

**Interview Line**

Tagged template literals pass template string parts and interpolated values to a function, allowing custom processing such as styling, escaping, localization, or query construction.

## Error Handling

### Q. What is `try...catch`?

**Answer:**

`try...catch` is used to handle runtime errors gracefully without crashing the application.

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

### Q. What is `finally`?

**Answer:**

`finally` is a block that always executes, whether an error occurs or not.

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

**Answer:**

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

**Answer:**

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

**Answer:**

Errors in promises are handled using `.catch()`.

Explanation

- Any rejection in the chain flows to `.catch()`
- Prevents unhandled promise rejections

Example

```js
fetch(url)
  .then((res) => res.json())
  .catch((err) => console.error(err));
```

### Q. Global Error Handling

**Answer:**

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

### Q. What is `throw`?

**Answer:**

`throw` is used to manually generate an error.

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

**Answer:**

Async errors are handled using `try...catch` with `async/await` or `.catch()` with promises.

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

**Answer:**

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

**Answer:**

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

### Q. Can try...catch catch async errors?

**Answer:**

Short Answer

👉 Yes, but only with await

👉 ❌ No, if using plain promises without await

Explanation

✅ Works with async/await

```js
async function fetchData() {
  try {
    const res = await fetch("api-url");
    const data = await res.json();
  } catch (error) {
    console.log("Error caught:", error);
  }
}
```

✔ `await` makes async code behave like synchronous → `try...catch` works

❌ Does NOT catch without await

```js
try {
  fetch("api-url")
    .then((res) => res.json())
    .then((data) => console.log(data));
} catch (error) {
  console.log("Won't catch!");
}
```

❌ Error inside .then() is NOT caught

✅ Correct way (Promises)

```js
fetch("api-url")
  .then((res) => res.json())
  .catch((err) => console.log(err));
```

Key Insight

`try...catch` only works for:

- synchronous code
- awaited async code

**🔥 Interview Line**

`try...catch` can catch async errors only when using `await`; otherwise, you must use `.catch()` for promises.

### Q. Difference between Error and TypeError

**Answer:**

Error

✅ Definition

Base class for all errors

Example

```js
throw new Error("Something went wrong");
```

TypeError

✅ Definition

Occurs when a value is not of expected type

Example

```js
let num = null;
num.toString(); // ❌ TypeError
```

Key Differences

| Feature     | Error         | TypeError     |
| ----------- | ------------- | ------------- |
| Type        | Generic       | Specific      |
| Use Case    | Custom errors | Type mismatch |
| Inheritance | Base class    | Extends Error |

Real Insight

TypeError is more specific and descriptive

**🔥 Interview Line**

Error is a generic base class, while TypeError is a specific error thrown when operations are performed on incompatible types.

### Q. How error handling differs in frontend vs backend

**Answer:**

Frontend (Client-side)

✅ Goals

- Show user-friendly messages
- Prevent app crash
- Handle UI gracefully

Examples

- Toast messages
- Retry buttons
- Fallback UI

Tools

- `try...catch`
- `.catch()`
- React Error Boundaries

Backend (Server-side)

✅ Goals

- Maintain server stability
- Log errors
- Send proper HTTP responses

Examples

- Logging (Winston, Morgan)
- HTTP status codes (500, 404)
- Error middleware

Key Differences

| Feature      | Frontend        | Backend             |
| ------------ | --------------- | ------------------- |
| Focus        | UX              | Stability & logging |
| Error Output | UI messages     | Logs + API response |
| Impact       | User experience | System reliability  |

**🔥 Interview Line**

Frontend focuses on user experience and graceful UI handling, while backend focuses on stability, logging, and correct API responses.

### Q. What happens if promise rejection is not handled?

**Answer:**

Result

👉 Unhandled Promise Rejection

Behavior

In Browser:

- Shows warning in console
- May not crash app immediately

In Node.js:

- Can terminate process (in strict modes)
- Emits unhandledRejection event

Example

```js
Promise.reject("Error!");
```

❌ No `.catch()` → unhandled rejection

Risks

- Silent failures ❌
- Debugging difficulty ❌
- App instability ❌

Best Practice

```js
promise.then((data) => {}).catch((err) => console.error(err));
```

OR

```js
try {
  await promise;
} catch (err) {
  console.error(err);
}
```

Global Handling (Node.js)

```js
process.on("unhandledRejection", (err) => {
  console.log("Unhandled:", err);
});
```

**🔥 Interview Line**

Unhandled promise rejections can lead to silent failures or crashes, so they should always be handled using .catch() or try...catch.

### Q. Difference between `throw` and `return`

**Answer:**

`return` is used to end the execution of a function and optionally send a value back to the caller.

**Example:**

```js
function add(a, b) {
  return a + b;
}

const result = add(2, 3);

console.log(result);
```

Output:

```js
5;
```

`throw` is used to signal that an error or exceptional condition has occurred.

**Example:**

```js
function divide(a, b) {
  if (b === 0) {
    throw new Error("Division by zero is not allowed");
  }

  return a / b;
}
```

When `throw` executes, normal function execution stops immediately and JavaScript looks for the nearest matching error handler, such as a `catch` block.

Main difference:

- `return` represents normal function completion
- `throw` represents exceptional or error flow

A thrown error can propagate through multiple function calls until it is handled.

**Interview Line**

`return` ends a function normally and optionally returns a value, while `throw` stops normal execution and propagates an error until it is caught.

### Q. Difference between `Error`, `TypeError`, `ReferenceError`, and `SyntaxError`

**Answer:**

JavaScript provides different built-in error types to describe different categories of problems.

`Error` is the general base error type.

**Example:**

```js
throw new Error("Something went wrong");
```

`TypeError` occurs when an operation is performed on a value of an inappropriate type.

**Example:**

```js
const value = null;

value.toString();
```

This can throw a `TypeError`.

`ReferenceError` occurs when code tries to access a variable that does not exist in the current scope.

**Example:**

```js
console.log(userName);
```

If `userName` was never declared, JavaScript throws a `ReferenceError`.

`SyntaxError` occurs when JavaScript code violates the language syntax.

**Example:**

```js
if (true {
  console.log("Hello");
}
```

This is invalid JavaScript syntax.

Summary:

| Error Type       | Meaning                              |
| ---------------- | ------------------------------------ |
| `Error`          | General application error            |
| `TypeError`      | Invalid operation for a value/type   |
| `ReferenceError` | Variable or reference does not exist |
| `SyntaxError`    | Invalid JavaScript syntax            |

**Interview Line**

`Error` is the general error type, while `TypeError`, `ReferenceError`, and `SyntaxError` represent more specific categories of JavaScript failures.

### Q. How do you create a custom error class?

**Answer:**

A custom error class is created by extending JavaScript's built-in `Error` class.

Custom errors are useful when an application needs to distinguish between different business or technical error types.

**Example:**

```js
class ValidationError extends Error {
  constructor(message, field) {
    super(message);

    this.name = "ValidationError";
    this.field = field;
  }
}
```

Usage:

```js
function validateUser(user) {
  if (!user.email) {
    throw new ValidationError("Email is required", "email");
  }
}
```

Handling:

```js
try {
  validateUser({});
} catch (error) {
  if (error instanceof ValidationError) {
    console.log(error.field);
    console.log(error.message);
  }
}
```

Custom error classes can also include extra information such as:

- Error code
- HTTP status
- Field name
- Resource ID
- Additional context

**Interview Line**

A custom error class extends the built-in `Error` class and can add application-specific properties such as error codes, fields, or metadata.

### Q. Why should custom errors extend the Error class?

**Answer:**

Custom errors should extend `Error` so they behave like standard JavaScript errors.

**Example:**

```js
class AuthenticationError extends Error {
  constructor(message) {
    super(message);

    this.name = "AuthenticationError";
  }
}
```

Because it extends `Error`, we can use:

```js
error instanceof Error;
```

and:

```js
error instanceof AuthenticationError;
```

This also gives the custom error standard properties such as:

```js
message;
stack;
name;
```

Without extending `Error`, the object may not behave consistently with JavaScript's normal error-handling system.

**Interview Line**

Custom errors should extend `Error` so they preserve standard error behavior, stack traces, and `instanceof` checks while adding application-specific information.

### Q. What is stack trace?

**Answer:**

A stack trace is information that shows the sequence of function calls that led to an error.

It helps developers identify:

- Where the error occurred
- Which function called the failing function
- The file and line number involved
- The call path that produced the error

**Example:**

```js
function first() {
  second();
}

function second() {
  third();
}

function third() {
  throw new Error("Something went wrong");
}

first();
```

The stack trace may look conceptually like:

```text
Error: Something went wrong
    at third (...)
    at second (...)
    at first (...)
```

The most recent failing call appears near the top, followed by the functions that led to it.

**Interview Line**

A stack trace shows the chain of function calls that led to an error and helps identify where and how the failure occurred.

### Q. How do you handle errors in async/await?

**Answer:**

Errors in `async/await` code are commonly handled using `try...catch`.

If an awaited Promise rejects, `await` behaves as if the rejection was thrown as an error.

**Example:**

```js
async function getUser() {
  try {
    const response = await fetch("/api/user");

    if (!response.ok) {
      throw new Error(`Request failed: ${response.status}`);
    }

    const user = await response.json();

    return user;
  } catch (error) {
    console.error("Unable to load user", error);

    throw error;
  }
}
```

It is important to remember that `fetch()` does not reject automatically for every HTTP error status such as `404` or `500`.

Therefore, application code often needs to check `response.ok` manually.

Errors should normally be caught where the application can meaningfully handle, transform, log, or recover from them.

**Interview Line**

With `async/await`, rejected Promises can be handled using `try...catch`, and errors should usually be caught where meaningful recovery or logging can happen.

### Q. How do you handle errors in Promise chains?

**Answer:**

Promise chain errors are usually handled using `.catch()`.

**Example:**

```js
fetch("/api/user")
  .then((response) => {
    if (!response.ok) {
      throw new Error(`Request failed: ${response.status}`);
    }

    return response.json();
  })
  .then((user) => {
    console.log(user);
  })
  .catch((error) => {
    console.error("Unable to load user", error);
  });
```

If an error is thrown inside a `.then()` callback, it automatically becomes a rejected Promise and travels to the next rejection handler.

**Example:**

```js
Promise.resolve()
  .then(() => {
    throw new Error("Failed");
  })
  .catch((error) => {
    console.log(error.message);
  });
```

**Interview Line**

Promise-chain errors are handled using `.catch()`, and errors thrown inside `.then()` callbacks automatically propagate as Promise rejections.

### Q. What is unhandled promise rejection?

**Answer:**

An unhandled Promise rejection occurs when a Promise rejects but no rejection handler is attached to handle the failure.

**Example:**

```js
async function loadData() {
  throw new Error("API failed");
}

loadData();
```

`loadData()` returns a rejected Promise, but nothing handles that rejection.

A handled version would be:

```js
loadData().catch((error) => {
  console.error(error);
});
```

or:

```js
async function main() {
  try {
    await loadData();
  } catch (error) {
    console.error(error);
  }
}

main();
```

Unhandled Promise rejections are dangerous because failures may remain unnoticed until they affect application behavior.

**Interview Line**

An unhandled Promise rejection happens when a Promise rejects without a `.catch()` or equivalent rejection handler.

### Q. How do you globally handle JavaScript errors in browser?

**Answer:**

Browsers provide global events that can observe errors that were not handled locally.

Two important mechanisms are:

1. `window.onerror`
2. `unhandledrejection`

For normal uncaught JavaScript errors:

```js
window.addEventListener("error", (event) => {
  console.error("Global error:", event.error);
});
```

For unhandled Promise rejections:

```js
window.addEventListener("unhandledrejection", (event) => {
  console.error("Unhandled Promise:", event.reason);
});
```

These handlers are useful for error monitoring and production logging.

They should not replace local error handling where the application knows how to recover.

**Interview Line**

Global browser errors can be observed using the `error` event or `window.onerror`, while unhandled Promise rejections can be observed using `unhandledrejection`.

### Q. What is `window.onerror`?

**Answer:**

`window.onerror` is a global browser error handler that is called when an uncaught JavaScript runtime error reaches the global scope.

**Example:**

```js
window.onerror = function (message, source, line, column, error) {
  console.log("Message:", message);
  console.log("Source:", source);
  console.log("Line:", line);
  console.log("Error:", error);
};
```

It can provide details such as:

- Error message
- File URL
- Line number
- Column number
- Error object

Modern code can also use:

```js
window.addEventListener("error", handler);
```

which allows multiple event listeners and follows the standard event model.

**Interview Line**

`window.onerror` is a global browser handler for uncaught JavaScript errors and can provide the message, source file, line number, and error object.

### Q. What is `unhandledrejection` event?

**Answer:**

The `unhandledrejection` event is fired when a Promise is rejected and no rejection handler handles it in time.

**Example:**

```js
window.addEventListener("unhandledrejection", (event) => {
  console.error("Unhandled rejection:", event.reason);
});
```

For example:

```js
Promise.reject(new Error("Request failed"));
```

If no `.catch()` is attached, the browser can trigger the `unhandledrejection` event.

The rejection reason is available through:

```js
event.reason;
```

This event is useful as a final monitoring safety net for asynchronous failures.

**Interview Line**

`unhandledrejection` is a browser event fired when a Promise rejects without an appropriate rejection handler.

### Q. Difference between operational errors and programmer errors

**Answer:**

Operational errors are expected failures that can happen even when the application code is correct.

Examples include:

- API timeout
- Network failure
- Invalid user input
- Missing file
- Database temporarily unavailable
- Authentication token expired

Programmer errors are bugs caused by incorrect application code.

Examples include:

- Accessing a property on `undefined`
- Calling a non-function
- Incorrect assumptions
- Invalid logic
- Using undeclared variables

**Example:**

```js
const user = undefined;

console.log(user.name);
```

This is a programmer error because the code made an invalid assumption about `user`.

Operational errors should usually be handled gracefully.

Programmer errors should normally be fixed rather than silently ignored.

**Interview Line**

Operational errors are expected runtime failures such as network or validation issues, while programmer errors are bugs caused by incorrect application logic.

### Q. Should every function have try...catch?

**Answer:**

No.

Adding `try...catch` to every function creates unnecessary code and can make error handling harder to understand.

A function should catch an error when it can do something meaningful with it.

Examples include:

- Recovering from the failure
- Converting it into a custom error
- Adding useful context
- Logging at an application boundary
- Returning an intentional fallback value

**Bad Example:**

```js
function getUser() {
  try {
    return database.getUser();
  } catch (error) {
    throw error;
  }
}
```

The `catch` block adds no value.

Better:

```js
function getUser() {
  return database.getUser();
}
```

The error can naturally propagate to a higher layer that knows how to handle it.

**Interview Line**

`try...catch` should be used where an error can be meaningfully handled, transformed, logged, or recovered from, not in every function.

### Q. Why is swallowing errors a bad practice?

**Answer:**

Swallowing an error means catching it and then ignoring it without handling, logging, or propagating it.

**Bad Example:**

```js
try {
  await saveUser();
} catch (error) {
  // ignored
}
```

The application may continue as if the operation succeeded even though it actually failed.

This can cause:

- Hidden production bugs
- Incorrect application state
- Difficult debugging
- Missing monitoring information
- Misleading user experience

If the current layer cannot handle the error, it should usually propagate it.

**Example:**

```js
try {
  await saveUser();
} catch (error) {
  console.error("Failed to save user", error);

  throw error;
}
```

**Interview Line**

Swallowing errors hides failures and can leave the application in an incorrect state, so errors should be handled, logged, or propagated intentionally.

### Q. What are best practices for error logging?

**Answer:**

Good error logging should provide enough information to understand and debug the failure without exposing sensitive information.

Useful information may include:

- Error message
- Stack trace
- Error type
- Operation name
- Timestamp
- Application version
- Safe request context
- Environment such as production or staging

**Example:**

```js
console.error("User fetch failed", {
  message: error.message,
  stack: error.stack,
  userId,
  endpoint: "/api/users",
});
```

In production applications, dedicated monitoring tools are normally more useful than relying only on `console.error`.

Avoid logging sensitive information such as:

- Passwords
- Access tokens
- Private keys
- Authentication cookies
- Payment information

Also avoid logging the same error repeatedly at every layer unless each log provides additional useful context.

**Interview Line**

Good error logging records useful context and stack information while avoiding sensitive data and unnecessary duplicate logs.

### Q. How do frontend and backend error handling differ?

**Answer:**

Frontend and backend error handling have different responsibilities.

Frontend error handling focuses mainly on user experience and UI recovery.

Typical frontend responsibilities include:

- Showing user-friendly messages
- Retrying failed requests
- Displaying fallback UI
- Handling network failures
- Redirecting after authentication failures
- Reporting client runtime errors

**Example:**

```js
try {
  await loadProducts();
} catch (error) {
  showMessage("Unable to load products. Please try again.");
}
```

Backend error handling focuses more on:

- Request validation
- Authentication and authorization
- Data consistency
- Logging technical failures
- Returning appropriate HTTP status codes
- Protecting internal implementation details

The backend may log a complete stack trace internally while returning only a safe message to the frontend.

**Interview Line**

Frontend error handling focuses on user experience and recovery, while backend error handling focuses on validation, security, data consistency, status codes, and safe error responses.

### Q. How do React Error Boundaries relate to JavaScript error handling?

**Answer:**

React Error Boundaries are a React-specific mechanism for catching certain errors in a component tree and displaying fallback UI.

They complement JavaScript error handling but do not replace `try...catch`.

Error Boundaries can catch errors that occur during:

- Rendering
- Lifecycle methods
- Constructors of descendant components

Conceptually:

```jsx
<ErrorBoundary fallback={<ErrorPage />}>
  <Dashboard />
</ErrorBoundary>
```

If a descendant fails while rendering, the Error Boundary can prevent the entire UI from crashing.

However, traditional Error Boundaries do not automatically catch every type of error.

For example, event handler and asynchronous errors may still require normal JavaScript handling.

**Example:**

```js
async function handleSubmit() {
  try {
    await saveData();
  } catch (error) {
    console.error(error);
  }
}
```

So Error Boundaries protect UI rendering, while `try...catch` handles procedural and asynchronous application logic.

**Interview Line**

React Error Boundaries protect parts of the component tree from rendering failures, while normal JavaScript error handling is still required for async operations, event handlers, and other application logic.

## Performance & Optimization

### Q. How to Improve JavaScript Performance?

**Answer:**

JavaScript performance can be improved by optimizing execution, reducing re-renders, minimizing bundle size, and efficient memory usage.

Key Techniques

- Avoid unnecessary DOM manipulation
- Use debounce/throttle
- Optimize loops and algorithms
- Use code splitting & lazy loading
- Cache results (memoization)
- Use Web Workers for heavy tasks
- Minify and tree-shake code

🔥 One-liner

“I improve JS performance by reducing unnecessary work, optimizing rendering, and minimizing bundle size.”

### Q. What is Debouncing?

**Answer:**

Debouncing ensures a function is executed only after a delay once the user stops triggering it.

Example (Search Input)

```js
function debounce(fn, delay) {
  let timer;
  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => fn(...args), delay);
  };
}
```

Use Cases

- Search input
- Auto-save
- Resize events

### Q. What is Throttling?

**Answer:**

Throttling ensures a function is executed at most once in a specified time interval.

Example

```js
function throttle(fn, limit) {
  let inThrottle;
  return function (...args) {
    if (!inThrottle) {
      fn(...args);
      inThrottle = true;
      setTimeout(() => (inThrottle = false), limit);
    }
  };
}
```

Use Cases

- Scroll events
- Mouse movement
- Button clicks

### Q. Difference: Debounce vs Throttle

| Feature   | Debounce     | Throttle          |
| --------- | ------------ | ----------------- |
| Execution | After delay  | At intervals      |
| Trigger   | Stops events | Continuous events |
| Use case  | Search input | Scroll/resize     |

**🔥 Interview Line**

“Debounce waits for inactivity, while throttle limits execution frequency.”

### Q. Memory Leaks in JavaScript

**Answer:**

A memory leak occurs when memory is not released even after it’s no longer needed.

Common Causes

- Unremoved event listeners
- Timers not cleared
- Closures holding references
- Detached DOM nodes

### Q. How Closures Cause Memory Leaks?

**Answer:**

Closures retain references to variables from outer scope, preventing garbage collection.

Example

```js
function outer() {
  let largeData = new Array(1000000);

  return function inner() {
    console.log("Using data");
  };
}

const fn = outer();
```

👉 largeData stays in memory because closure holds it.

### Q. Lazy Loading

**Answer:**

Lazy loading delays loading of resources until they are needed.

Example (React)

```jsx
const Component = React.lazy(() => import("./Component"));
```

Use Cases

- Images
- Routes
- Components

### Q. Code Splitting

**Answer:**

Code splitting breaks the bundle into smaller chunks that are loaded on demand.

Example

```jsx
import("./Dashboard");
```

Benefits

- Faster initial load
- Better performance

### Q. Minification & Tree Shaking

Minification

Removes unnecessary code (spaces, comments).

```js
// Before
function add(a, b) {
  return a + b;
}

// After
function add(a, b) {
  return a + b;
}
```

Tree Shaking

Removes unused code from bundle.

```js
import { add } from "lib"; // only add is included
```

### Q. Web Workers

**Answer:**

Web Workers allow running JavaScript in a background thread, separate from the main UI thread.

Why Needed

JS is single-threaded → heavy tasks block UI

Web Workers:

- Run tasks in background
- Keep UI responsive

Example

```js
const worker = new Worker("worker.js");

worker.postMessage("start");

worker.onmessage = (e) => {
  console.log(e.data);
};
```

Use Cases

- Image processing
- Large calculations
- Data parsing

🔥 Final Interview Summary (Power Answer)

“JavaScript performance can be improved using techniques like debouncing, throttling, lazy loading, code splitting, and Web Workers, while avoiding memory leaks and optimizing bundle size using minification and tree shaking.”

### Q. How do you identify performance issues in JavaScript?

**Answer:**

JavaScript performance issues should be identified through measurement rather than guessing.

Common signs of performance problems include:

- Slow page load
- Delayed button response
- Scroll jank
- Long-running JavaScript tasks
- High CPU usage
- Large memory growth
- Slow API rendering
- Poor Core Web Vitals

Useful tools include:

- Chrome DevTools Performance panel
- Memory panel
- Network panel
- Lighthouse
- Performance API
- Browser task timing information

**Example:**

If a page freezes while rendering a large table, we can record a Performance profile and check which JavaScript function is consuming the most CPU time.

We should then determine whether the issue comes from:

```text
JavaScript execution
DOM updates
network requests
layout calculations
large images
memory leaks
```

The key is to first find the bottleneck and then optimize the specific problem.

**Interview Line**

JavaScript performance issues should be identified using profiling tools such as Chrome DevTools and Lighthouse, then optimized based on measured CPU, memory, network, and rendering bottlenecks.

### Q. What is debounce and where is it used?

**Answer:**

Debounce is a technique that delays function execution until a certain amount of time has passed without the event occurring again.

If the event keeps happening, the timer keeps resetting.

**Example:**

```js
function debounce(fn, delay) {
  let timer;

  return function (...args) {
    clearTimeout(timer);

    timer = setTimeout(() => {
      fn.apply(this, args);
    }, delay);
  };
}
```

Usage:

```js
const handleSearch = debounce((value) => {
  console.log("Searching:", value);
}, 500);
```

If the user types continuously, the search runs only after typing stops for 500 milliseconds.

Common use cases include:

- Search inputs
- Form validation
- Window resize handlers
- Auto-save
- Expensive filtering operations

**Interview Line**

Debounce delays execution until events stop for a specified time and is commonly used for search boxes, resize handlers, validation, and auto-save.

### Q. What is throttle and where is it used?

**Answer:**

Throttle limits how frequently a function can execute during repeated events.

Unlike debounce, throttle allows the function to run at regular intervals while the event continues.

**Example:**

```js
function throttle(fn, delay) {
  let lastRun = 0;

  return function (...args) {
    const now = Date.now();

    if (now - lastRun >= delay) {
      lastRun = now;
      fn.apply(this, args);
    }
  };
}
```

Usage:

```js
window.addEventListener(
  "scroll",
  throttle(() => {
    console.log("Scroll handled");
  }, 200),
);
```

Even if the scroll event fires many times per second, the handler runs only once every 200 milliseconds.

Common use cases include:

- Scroll events
- Mouse movement
- Drag events
- Resize events
- Rate-limited UI updates

**Interview Line**

Throttle limits a function to run at most once within a defined interval and is useful for frequent events such as scroll, mousemove, and resize.

### Q. Difference between debounce and throttle

**Answer:**

Both debounce and throttle control how often a function runs, but they behave differently.

Debounce waits until events stop.

Throttle allows execution at regular intervals while events continue.

**Example Scenario: Search Input**

With debounce:

```text
User types continuously
↓
No API request yet
↓
User stops typing
↓
API request runs
```

With throttle:

```text
User types continuously
↓
API request can run every fixed interval
```

Comparison:

| Debounce                       | Throttle                   |
| ------------------------------ | -------------------------- |
| Waits until activity stops     | Executes periodically      |
| Good for search input          | Good for scroll events     |
| Resets timer on every event    | Limits execution frequency |
| Often executes once at the end | Can execute multiple times |

**Interview Line**

Debounce waits until repeated events stop, while throttle allows execution at a controlled interval during continuous events.

### Q. How do you optimize scroll events?

**Answer:**

Scroll events can fire many times per second, so expensive work inside the handler can cause jank.

Common optimizations include:

1. Throttle the handler.
2. Use passive listeners where appropriate.
3. Use `requestAnimationFrame()` for visual updates.
4. Avoid repeated layout calculations.
5. Use Intersection Observer instead of manual viewport checks when possible.

**Example:**

```js
window.addEventListener("scroll", handleScroll, { passive: true });
```

For visual updates:

```js
let ticking = false;

window.addEventListener("scroll", () => {
  if (!ticking) {
    requestAnimationFrame(() => {
      updateUI();
      ticking = false;
    });

    ticking = true;
  }
});
```

For checking whether elements are visible, Intersection Observer is usually more efficient than repeatedly calling:

```js
element.getBoundingClientRect();
```

inside every scroll event.

**Interview Line**

Scroll performance can be improved using throttling, passive listeners, `requestAnimationFrame()`, Intersection Observer, and by reducing expensive DOM and layout work.

### Q. How do you optimize search input API calls?

**Answer:**

The most common optimization is debouncing the search input so an API request is not sent for every keystroke.

**Example:**

```js
const search = debounce(async (query) => {
  const response = await fetch(`/api/search?q=${encodeURIComponent(query)}`);

  const data = await response.json();

  console.log(data);
}, 400);
```

Additional optimizations include:

- Ignore very short search terms
- Cancel old requests using `AbortController`
- Cache repeated queries
- Avoid duplicate requests
- Show loading state appropriately

**Example with cancellation:**

```js
let controller;

async function searchUsers(query) {
  controller?.abort();

  controller = new AbortController();

  const response = await fetch(`/api/users?q=${query}`, {
    signal: controller.signal,
  });

  return response.json();
}
```

This prevents an older request from overwriting newer search results.

**Interview Line**

Search API calls are usually optimized with debouncing, request cancellation, caching, and avoiding duplicate or unnecessary queries.

### Q. What is memoization?

**Answer:**

Memoization is an optimization technique where the result of a function is stored and reused when the same input is provided again.

It is especially useful for expensive calculations.

**Example:**

```js
function memoize(fn) {
  const cache = new Map();

  return function (value) {
    if (cache.has(value)) {
      return cache.get(value);
    }

    const result = fn(value);

    cache.set(value, result);

    return result;
  };
}
```

Usage:

```js
const square = memoize((number) => {
  console.log("Calculating");
  return number * number;
});

console.log(square(5));
console.log(square(5));
```

The calculation runs only the first time for the same input.

Memoization works best when:

- The function is expensive
- The same inputs occur repeatedly
- The output is deterministic

**Interview Line**

Memoization stores function results by input so repeated calls with the same arguments can reuse the previous result instead of recalculating it.

### Q. What is caching?

**Answer:**

Caching means storing previously computed or fetched data so future requests can be served faster.

Caching is a broad concept and can happen at many levels.

Examples include:

- Browser cache
- API cache
- CDN cache
- In-memory cache
- Database cache
- Application cache
- Service Worker cache

**Example:**

```js
const cache = new Map();

async function getUser(id) {
  if (cache.has(id)) {
    return cache.get(id);
  }

  const response = await fetch(`/api/users/${id}`);

  const user = await response.json();

  cache.set(id, user);

  return user;
}
```

The next request for the same user can reuse the stored result.

Caching reduces repeated work, but stale data and invalidation must be considered.

**Interview Line**

Caching stores reusable data or results so future access is faster and can happen across the browser, application, network, CDN, or server layers.

### Q. Difference between memoization and caching

**Answer:**

Memoization is a specific type of caching focused on function results.

Caching is a broader concept.

Memoization usually uses function arguments as the cache key.

**Example:**

```js
calculateTax(1000);
```

If the same argument is used again, memoization can return the previous result.

Caching may store many other things, such as:

```text
API responses
images
HTML
database queries
files
network responses
```

Comparison:

| Memoization                         | Caching                                  |
| ----------------------------------- | ---------------------------------------- |
| Mainly function-result optimization | Broad storage optimization               |
| Usually keyed by function inputs    | Can use URLs, IDs, files, requests, etc. |
| Often in memory                     | Can exist in browser, server, CDN, disk  |
| Common for repeated calculations    | Common for data and network optimization |

**Interview Line**

Memoization is caching specifically for function outputs based on inputs, while caching is the broader concept of storing reusable data or results.

### Q. How do you reduce unnecessary DOM manipulation?

**Answer:**

Direct DOM operations can become expensive when performed repeatedly, especially in large loops.

A better approach is to minimize the number of DOM reads and writes.

Instead of repeatedly appending elements:

```js
for (let i = 0; i < 1000; i++) {
  const div = document.createElement("div");

  document.body.appendChild(div);
}
```

we can prepare the changes first.

**Example:**

```js
const fragment = document.createDocumentFragment();

for (let i = 0; i < 1000; i++) {
  const div = document.createElement("div");

  fragment.appendChild(div);
}

document.body.appendChild(fragment);
```

Other techniques include:

- Batch DOM updates
- Update parent classes instead of many children
- Cache DOM references
- Avoid querying the same element repeatedly
- Use event delegation
- Avoid unnecessary element creation and removal

**Interview Line**

Unnecessary DOM manipulation can be reduced by batching updates, caching element references, using fragments, event delegation, and minimizing repeated reads and writes.

### Q. What is layout thrashing?

**Answer:**

Layout thrashing happens when JavaScript repeatedly alternates between reading layout information and writing DOM styles.

This can force the browser to recalculate layout many times.

**Bad Example:**

```js
const elements = document.querySelectorAll(".item");

elements.forEach((element) => {
  const height = element.offsetHeight;

  element.style.height = `${height + 10}px`;
});
```

Reading:

```js
offsetHeight;
```

may require layout calculation.

Then changing:

```js
style.height;
```

invalidates layout again.

Repeating this for many elements can create expensive synchronous layout work.

**Interview Line**

Layout thrashing occurs when repeated DOM reads and writes force the browser to recalculate layout multiple times in a short period.

### Q. How do you avoid layout thrashing?

**Answer:**

The main strategy is to batch DOM reads separately from DOM writes.

Instead of:

```text
read
write
read
write
read
write
```

prefer:

```text
read
read
read

then

write
write
write
```

**Example:**

```js
const elements = [...document.querySelectorAll(".item")];

const heights = elements.map((element) => element.offsetHeight);

elements.forEach((element, index) => {
  element.style.height = `${heights[index] + 10}px`;
});
```

Other strategies include:

- Use `requestAnimationFrame()` for visual updates
- Avoid unnecessary layout-dependent properties
- Cache measurement values
- Prefer transforms for animations
- Batch class changes

Properties such as these can trigger layout calculations:

```js
offsetWidth;
offsetHeight;
getBoundingClientRect();
clientWidth;
scrollTop;
```

**Interview Line**

Layout thrashing is avoided by batching DOM reads and writes, caching layout measurements, and using frame-synchronized updates.

### Q. What is reflow and repaint?

**Answer:**

Reflow and repaint are browser rendering operations.

**Reflow**, also called layout, happens when the browser recalculates the size and position of elements.

Examples of changes that can cause reflow include:

```text
width
height
margin
padding
font size
adding or removing elements
```

**Repaint** happens when the visual appearance changes without necessarily changing layout.

Examples include:

```text
background color
text color
visibility
box shadow
```

A reflow can often lead to repaint because changing layout may require the browser to redraw affected pixels.

**Interview Line**

Reflow recalculates element geometry and layout, while repaint redraws visual appearance without necessarily changing the layout structure.

### Q. Difference between reflow and repaint

**Answer:**

Reflow is generally more expensive than repaint because the browser must recalculate element positions and dimensions.

**Example of reflow:**

```js
element.style.width = "500px";
```

Changing width can affect nearby elements and the page layout.

**Example of repaint:**

```js
element.style.backgroundColor = "red";
```

The element's appearance changes, but its position and size may remain the same.

Comparison:

| Reflow                          | Repaint                     |
| ------------------------------- | --------------------------- |
| Recalculates layout             | Redraws appearance          |
| Can affect surrounding elements | Usually affects pixels only |
| Generally more expensive        | Usually cheaper             |
| Width/height changes            | Color/background changes    |

**Interview Line**

Reflow changes layout geometry and is generally more expensive, while repaint only redraws visual changes when layout does not need recalculation.

### Q. What is lazy loading?

**Answer:**

Lazy loading means delaying the loading of a resource until it is actually needed.

Instead of loading everything during the initial page load, less important resources are loaded later.

Common lazy-loaded resources include:

- Images
- Videos
- JavaScript modules
- Components
- Routes
- Large datasets

**Example:**

```html
<img src="photo.jpg" loading="lazy" alt="Photo" />
```

JavaScript modules can also be loaded dynamically:

```js
const module = await import("./analytics.js");
```

Lazy loading can improve:

- Initial page load
- Network usage
- Time to interactive
- Bundle size for first render

**Interview Line**

Lazy loading delays resources until they are needed, reducing initial download and rendering work.

### Q. What is code splitting?

**Answer:**

Code splitting divides a JavaScript bundle into smaller chunks that can be loaded separately.

Without code splitting, an application may send one large JavaScript bundle containing code for every page.

With code splitting, users download only the code required for the current feature or route.

**Example:**

```js
const module = await import("./chart.js");
```

The chart code can be placed in a separate chunk and loaded only when required.

Benefits include:

- Smaller initial bundle
- Faster startup
- Lower network usage
- Better route loading performance

Modern frameworks and bundlers often provide route-level and dynamic code splitting automatically.

**Interview Line**

Code splitting divides JavaScript into smaller chunks so users load only the code required for the current route or feature.

### Q. What is bundle size optimization?

**Answer:**

Bundle size optimization means reducing the amount of JavaScript, CSS, and other code users must download.

Common techniques include:

- Tree shaking
- Code splitting
- Dynamic imports
- Removing unused dependencies
- Replacing heavy libraries
- Minification
- Compression
- Importing only required modules
- Keeping client-side code small

**Example:**

Instead of importing an entire utility library:

```js
import _ from "lodash";
```

we may import only the required function:

```js
import debounce from "lodash/debounce";
```

depending on the package and bundler behavior.

A smaller bundle usually improves download, parsing, compilation, and execution time.

**Interview Line**

Bundle optimization reduces shipped JavaScript through tree shaking, code splitting, selective imports, minification, dependency cleanup, and compression.

### Q. What is minification?

**Answer:**

Minification reduces file size by removing unnecessary characters from source code without changing behavior.

It can remove or shorten:

- Whitespace
- Comments
- Formatting
- Local variable names
- Unnecessary syntax

**Example:**

Original code:

```js
function add(first, second) {
  return first + second;
}
```

Minified code might look like:

```js
function add(n, d) {
  return n + d;
}
```

Minification reduces file size and improves network transfer.

It is normally performed automatically during production builds by modern bundlers.

**Interview Line**

Minification reduces source-code size by removing unnecessary formatting and shortening code while preserving the same behavior.

### Q. What is compression?

**Answer:**

Compression reduces the number of bytes sent over the network when transferring files such as JavaScript, CSS, HTML, and JSON.

Unlike minification, compression happens at the transport level.

For example, a server may store:

```text
app.js
```

and send a compressed representation to the browser using:

```text
Content-Encoding: gzip
```

or:

```text
Content-Encoding: br
```

The browser automatically decompresses the response.

Common web compression methods include:

- gzip
- Brotli

Minification and compression are often used together.

**Interview Line**

Compression reduces network transfer size using algorithms such as gzip or Brotli, while the browser automatically decompresses the response.

### Q. Difference between gzip and Brotli

**Answer:**

gzip and Brotli are both compression algorithms commonly used for web resources.

Brotli generally provides better compression ratios for text-based resources such as:

- JavaScript
- CSS
- HTML
- JSON

gzip is older and has extremely broad support.

Comparison:

| gzip                                      | Brotli                                         |
| ----------------------------------------- | ---------------------------------------------- |
| Older algorithm                           | Newer algorithm                                |
| Very widely supported                     | Widely supported in modern browsers            |
| Good compression                          | Often better compression                       |
| Usually faster at some compression levels | Higher compression can require more server CPU |

Static production assets are often precompressed because the compression cost is paid during build or deployment rather than for every request.

**Interview Line**

Both gzip and Brotli reduce network payload size, but Brotli generally achieves better compression for modern web assets while gzip remains broadly compatible.

### Q. How do Web Workers improve performance?

**Answer:**

Web Workers allow JavaScript to perform CPU-intensive work on a background thread instead of blocking the browser's main UI thread.

Normally, heavy JavaScript on the main thread can block:

- User input
- Rendering
- Scrolling
- Animations

A worker can perform computation separately.

**Example:**

Main thread:

```js
const worker = new Worker("worker.js");

worker.postMessage(data);

worker.onmessage = (event) => {
  console.log(event.data);
};
```

Worker:

```js
self.onmessage = (event) => {
  const result = expensiveCalculation(event.data);

  self.postMessage(result);
};
```

The main thread remains available for UI work while the worker performs the calculation.

**Interview Line**

Web Workers improve responsiveness by moving CPU-heavy JavaScript off the main UI thread onto a background worker thread.

### Q. When should you use Web Workers?

**Answer:**

Web Workers are useful when JavaScript performs CPU-intensive work that would otherwise block the main thread for a noticeable amount of time.

Good use cases include:

- Processing large datasets
- Complex mathematical calculations
- Image processing
- Parsing large files
- Encryption or hashing
- Data transformation
- Simulation algorithms

They are usually unnecessary for:

- Simple calculations
- Normal API requests
- Basic DOM updates

Workers also cannot directly manipulate the DOM.

Communication happens through messages:

```js
worker.postMessage(data);
```

and:

```js
worker.onmessage = handler;
```

There is some communication and serialization overhead, so workers should be used when the computation is heavy enough to justify it.

**Interview Line**

Use Web Workers for CPU-heavy tasks that would block the main thread, not for small operations or direct DOM manipulation.

### Q. How do you detect memory leaks?

**Answer:**

A memory leak occurs when memory that is no longer needed remains referenced and cannot be garbage collected.

Common causes include:

- Forgotten event listeners
- Unremoved timers
- Detached DOM nodes
- Global variables
- Large caches without eviction
- Closures retaining unnecessary objects
- Subscriptions not cleaned up

Chrome DevTools Memory panel can be used to capture heap snapshots and compare memory usage over time.

A common test is:

1. Open a feature.
2. Perform the same action repeatedly.
3. Close or remove the feature.
4. Force or wait for garbage collection.
5. Check whether memory continues growing.

Detached DOM trees are especially useful to inspect when debugging UI leaks.

**Interview Line**

Memory leaks are detected by profiling heap usage over time, comparing snapshots, and looking for retained objects such as detached DOM nodes, listeners, timers, and growing caches.

### Q. How do you profile JavaScript performance in Chrome DevTools?

**Answer:**

Chrome DevTools provides a Performance panel for recording what happens while a page is running.

A typical profiling process is:

1. Open DevTools.
2. Go to the Performance panel.
3. Start recording.
4. Perform the slow interaction.
5. Stop recording.
6. Inspect the timeline and flame chart.

Look for:

- Long tasks
- Expensive JavaScript functions
- Repeated layout calculations
- Excessive rendering
- Forced reflows
- Heavy event handlers
- Large scripting time

The Network and Memory panels can also help determine whether the bottleneck comes from network or memory rather than CPU execution.

The goal is to identify the specific task that is expensive before changing the code.

**Interview Line**

Chrome DevTools performance profiling records browser activity and helps identify long JavaScript tasks, expensive functions, layout work, rendering costs, and other bottlenecks.

### Q. What is Lighthouse?

**Answer:**

Lighthouse is an auditing tool used to evaluate the quality and performance of a web page.

It can analyze areas such as:

- Performance
- Accessibility
- SEO
- Best practices

It also reports useful performance metrics and provides recommendations.

Examples of recommendations include:

- Reduce unused JavaScript
- Optimize images
- Remove render-blocking resources
- Improve caching
- Reduce main-thread work

Lighthouse can be run from Chrome DevTools and is also available through automated tools and CI workflows.

It should be used as one performance signal, not the only source of truth.

Real-user monitoring and manual profiling are also important.

**Interview Line**

Lighthouse audits web pages for performance, accessibility, SEO, and best practices and provides metrics and optimization recommendations.

### Q. What is Core Web Vitals?

**Answer:**

Core Web Vitals are user-experience metrics used to measure important aspects of real-world page performance.

The current main Core Web Vitals are:

1. **LCP — Largest Contentful Paint**
2. **INP — Interaction to Next Paint**
3. **CLS — Cumulative Layout Shift**

**LCP** measures loading performance.

It focuses on how quickly the largest visible content element is rendered.

**INP** measures responsiveness.

It evaluates how quickly the page responds visually to user interactions such as clicks, taps, and keyboard input.

**CLS** measures visual stability.

It detects unexpected layout movement while the page loads or updates.

Typical good targets are approximately:

```text
LCP <= 2.5 seconds
INP <= 200 milliseconds
CLS <= 0.1
```

Core Web Vitals are especially useful because they focus on the user's actual experience rather than only raw technical timings.

**Interview Line**

Core Web Vitals measure loading, responsiveness, and visual stability through LCP, INP, and CLS and are important indicators of real user experience.

## Security (Frontend Focus)

### Q. What is XSS?

**Answer:**

XSS stands for **Cross-Site Scripting**.

It is a web security vulnerability where malicious JavaScript or HTML is injected into a trusted website and executed in another user's browser.

An attacker may use XSS to:

- Steal session information
- Read sensitive page data
- Modify the UI
- Perform actions as the logged-in user
- Redirect users to malicious websites

**Example:**

Suppose an application directly inserts user input using:

```js
element.innerHTML = userInput;
```

If `userInput` contains:

```html
<img src="x" onerror="alert('XSS')" />
```

the injected script-like behavior may execute in the browser.

XSS happens because the application treats untrusted data as executable HTML or JavaScript.

**Interview Line**

XSS is a vulnerability where untrusted input is executed as JavaScript or HTML in another user's browser.

### Q. What is CSRF?

**Answer:**

CSRF stands for **Cross-Site Request Forgery**.

It is an attack where a malicious website tricks a user's browser into sending an authenticated request to another website where the user is already logged in.

This works because browsers automatically include certain credentials, such as cookies, with matching requests.

**Example:**

Suppose a banking application supports:

```http
POST /transfer
```

and authentication is based only on cookies.

A malicious site may try to trigger a request to that endpoint while the user's authentication cookie is automatically included.

The server may think the request came from the legitimate user.

**Interview Line**

CSRF tricks an authenticated user's browser into sending an unwanted request to a trusted website.

### Q. How to prevent XSS in JS?

**Answer:**

The main goal is to ensure untrusted data is treated as data, not executable HTML or JavaScript.

Common protections include:

1. Use `textContent` instead of `innerHTML` for plain text.
2. Escape or sanitize untrusted HTML.
3. Avoid dangerous APIs such as `eval()`.
4. Use framework escaping correctly.
5. Validate and sanitize input when HTML is intentionally supported.
6. Apply a strong Content Security Policy.

**Example:**

Unsafe:

```js
output.innerHTML = userInput;
```

Safer for plain text:

```js
output.textContent = userInput;
```

If HTML must be supported, use a trusted sanitization library rather than writing custom sanitization logic.

**Interview Line**

Prevent XSS by avoiding unsafe HTML injection, escaping or sanitizing untrusted content, and using defenses such as CSP.

### Q. What is CORS?

**Answer:**

CORS stands for **Cross-Origin Resource Sharing**.

It is a browser security mechanism that allows a server to explicitly tell the browser which other origins are allowed to access its resources.

An origin is based on:

```text
protocol + host + port
```

For example:

```text
https://app.example.com
```

and:

```text
https://api.example.com
```

are different origins.

A server may return:

```http
Access-Control-Allow-Origin: https://app.example.com
```

This tells the browser that JavaScript running on that origin is allowed to read the response.

CORS is enforced mainly by browsers.

**Interview Line**

CORS allows servers to explicitly permit controlled cross-origin browser requests that would otherwise be restricted by the Same-Origin Policy.

### Q. Same-origin policy

**Answer:**

The Same-Origin Policy is a browser security rule that restricts JavaScript from accessing resources from a different origin.

Two URLs are considered the same origin when their:

- Protocol
- Host
- Port

match.

**Example:**

These are same-origin:

```text
https://example.com/page
https://example.com/api
```

These are different origins:

```text
https://example.com
http://example.com
```

and:

```text
https://example.com
https://api.example.com
```

The policy helps prevent a malicious website from freely reading sensitive data from another site where the user may already be authenticated.

**Interview Line**

The Same-Origin Policy prevents browser JavaScript from freely reading data from different origins unless an explicit mechanism such as CORS allows it.

### Q. How cookies are secured?

**Answer:**

Cookies should be secured using appropriate cookie attributes and safe server-side practices.

Important protections include:

- `HttpOnly`
- `Secure`
- `SameSite`
- Limited expiration time
- Narrow domain and path scope
- HTTPS
- Server-side validation

**Example:**

```http
Set-Cookie: session=abc123; HttpOnly; Secure; SameSite=Lax
```

This helps reduce exposure to common attacks.

Authentication cookies should usually not be readable by frontend JavaScript unless there is a strong reason.

Sensitive session identifiers should also be rotated and invalidated appropriately.

**Interview Line**

Cookies are secured with attributes such as `HttpOnly`, `Secure`, and `SameSite`, plus HTTPS, limited lifetime, and proper server-side session management.

### Q. What is Content Security Policy?

**Answer:**

Content Security Policy, or CSP, is a browser security feature that lets a website define which sources are allowed to load or execute content.

CSP is usually delivered through an HTTP response header.

**Example:**

```http
Content-Security-Policy: default-src 'self'; script-src 'self'
```

This policy restricts resources to the same origin and limits where scripts can come from.

CSP can control:

- Scripts
- Styles
- Images
- Frames
- Fonts
- Connections
- Other resource types

CSP is an important defense-in-depth mechanism, especially against XSS.

**Interview Line**

CSP is a browser-enforced policy that restricts which sources can load scripts and other resources, reducing the impact of injection attacks.

### Q. Secure localStorage usage

**Answer:**

`localStorage` should only be used for non-sensitive data.

Good examples include:

- Theme preference
- UI settings
- Non-sensitive cached values
- Draft state

Avoid storing:

- Passwords
- Refresh tokens
- Sensitive access tokens
- Private personal data
- Security secrets

Any JavaScript running on the page can access `localStorage`.

**Example:**

```js
localStorage.setItem("theme", "dark");
```

This is reasonable.

Storing:

```js
localStorage.setItem("refreshToken", sensitiveToken);
```

creates a larger risk if XSS occurs.

**Interview Line**

Use `localStorage` only for non-sensitive browser state because any script running on the page can read it.

### Q. JWT vs sessions

**Answer:**

JWT and session-based authentication are two common ways to maintain authenticated user state.

With sessions, the server stores session state and the browser usually stores only a session identifier.

With JWT authentication, authentication information is encoded into a signed token.

Comparison:

| Session                        | JWT                            |
| ------------------------------ | ------------------------------ |
| Server stores session state    | Token carries claims           |
| Usually uses session ID cookie | Often uses access token        |
| Easy server-side invalidation  | Revocation can be more complex |
| Good for traditional web apps  | Useful for distributed APIs    |

Neither approach is automatically more secure.

Security depends heavily on token storage, expiration, rotation, cookie settings, and backend validation.

**Interview Line**

Sessions store authentication state on the server, while JWTs carry signed claims in the token itself; the right choice depends on architecture and security requirements.

### Q. Why not store sensitive data in localStorage?

**Answer:**

The biggest issue is that `localStorage` is accessible to JavaScript running on the page.

If the application has an XSS vulnerability, malicious JavaScript can read stored values.

**Example:**

```js
const token = localStorage.getItem("token");
```

An injected script could do the same thing.

Other limitations include:

- No `HttpOnly` protection
- Data persists until removed
- Shared with all scripts running on the same origin
- Easy to inspect and modify through DevTools

For sensitive authentication credentials, secure cookies are often safer because `HttpOnly` cookies cannot be read by normal frontend JavaScript.

**Interview Line**

Sensitive data should not be stored in `localStorage` because XSS can expose anything JavaScript is allowed to read.

### Q. What are reflected, stored, and DOM-based XSS?

**Answer:**

These are three common XSS categories.

### Reflected XSS

Malicious input is sent in a request and immediately reflected into the response.

**Example:**

```text
/search?q=<script>...</script>
```

If the server inserts that value into HTML without proper escaping, the payload may execute.

### Stored XSS

Malicious content is saved permanently, for example in a database.

Examples include:

- Comments
- Profile descriptions
- Forum posts

Every user who views the stored content may execute the malicious payload.

### DOM-based XSS

The vulnerability happens entirely in browser-side JavaScript.

**Example:**

```js
const value = location.hash.slice(1);

output.innerHTML = value;
```

No unsafe server response is required because the frontend itself creates the vulnerable DOM update.

**Interview Line**

Reflected XSS comes from request data, stored XSS comes from persisted malicious content, and DOM-based XSS is caused by unsafe client-side DOM manipulation.

### Q. How do you prevent XSS in JavaScript?

**Answer:**

The safest approach is to avoid interpreting untrusted input as executable content.

Use:

```js
element.textContent = userInput;
```

instead of:

```js
element.innerHTML = userInput;
```

when plain text is enough.

Additional protections include:

- Context-aware escaping
- HTML sanitization
- Avoiding `eval()`
- Avoiding inline event-handler construction
- Using trusted framework rendering
- Content Security Policy
- Validating URLs before assigning them to sensitive attributes

Never rely only on input validation, because valid-looking input can still become dangerous depending on where it is inserted.

**Interview Line**

XSS prevention requires safe output handling, especially escaping or sanitizing untrusted values before they enter HTML, JavaScript, or URL contexts.

### Q. Why is using `innerHTML` risky?

**Answer:**

`innerHTML` tells the browser to parse a string as HTML.

If that string contains untrusted content, attackers may inject dangerous markup.

**Example:**

```js
const comment = getUserComment();

element.innerHTML = comment;
```

If the comment contains malicious HTML, the browser may create unsafe elements or event handlers.

Safer plain-text alternative:

```js
element.textContent = comment;
```

If rich HTML is genuinely required, the content should be sanitized with a well-maintained trusted sanitizer.

**Interview Line**

`innerHTML` is risky because it parses strings as HTML, so untrusted input can become executable markup and create XSS vulnerabilities.

### Q. How do you prevent CSRF?

**Answer:**

Common CSRF protections include:

1. `SameSite` cookies
2. CSRF tokens
3. Origin or Referer validation
4. Avoiding state-changing GET requests
5. Requiring custom headers for API requests where appropriate

A CSRF token is a random value that the attacker cannot normally obtain from another origin.

**Example:**

```http
POST /transfer
X-CSRF-Token: random-secret-value
```

The server validates the token before performing the sensitive operation.

`SameSite=Lax` or `SameSite=Strict` cookies can also reduce unwanted cross-site cookie sending.

**Interview Line**

CSRF is prevented using protections such as SameSite cookies, anti-CSRF tokens, origin checks, and safe HTTP method design.

### Q. What problem does CORS solve?

**Answer:**

CORS solves the problem of legitimate cross-origin browser communication.

The Same-Origin Policy prevents frontend JavaScript from freely reading responses from another origin.

However, modern applications often need architectures such as:

```text
Frontend:
https://app.example.com

API:
https://api.example.com
```

CORS allows the API server to explicitly authorize the frontend origin.

**Example:**

```http
Access-Control-Allow-Origin: https://app.example.com
```

CORS does not act as authentication.

It controls which browser origins are allowed to read certain cross-origin responses.

**Interview Line**

CORS enables approved browser-based cross-origin communication while preserving the protections of the Same-Origin Policy.

### Q. Difference between CORS and Same-Origin Policy

**Answer:**

The Same-Origin Policy is the browser restriction.

CORS is the controlled exception mechanism.

The Same-Origin Policy says:

> JavaScript from one origin cannot freely access another origin.

CORS allows the target server to say:

> This particular origin is allowed.

Comparison:

| Same-Origin Policy                    | CORS                                       |
| ------------------------------------- | ------------------------------------------ |
| Browser security restriction          | Controlled permission mechanism            |
| Blocks cross-origin reads by default  | Allows approved cross-origin reads         |
| Enforced by browser                   | Configured through server response headers |
| Always part of browser security model | Used when cross-origin access is needed    |

**Interview Line**

Same-Origin Policy blocks cross-origin access by default, while CORS allows servers to selectively relax that restriction for trusted origins.

### Q. What is preflight request?

**Answer:**

A preflight request is an automatic `OPTIONS` request sent by the browser before certain cross-origin requests.

The browser uses it to ask the server whether the actual request is allowed.

**Example:**

Before sending:

```http
DELETE /users/10
```

the browser may first send:

```http
OPTIONS /users/10
```

with headers such as:

```http
Origin: https://app.example.com
Access-Control-Request-Method: DELETE
```

The server responds with allowed methods and origins.

If the response does not permit the requested operation, the browser does not expose the actual cross-origin request as allowed.

**Interview Line**

A CORS preflight is an automatic `OPTIONS` request used by the browser to verify that a non-simple cross-origin request is permitted.

### Q. What are simple requests in CORS?

**Answer:**

A simple CORS request is a request that meets specific browser-defined conditions and does not require a preflight request.

Typical simple methods include:

```text
GET
HEAD
POST
```

The request must also use only certain safelisted headers and content types.

Examples of safelisted content types include:

```text
application/x-www-form-urlencoded
multipart/form-data
text/plain
```

A request using:

```http
Content-Type: application/json
```

usually triggers a preflight in cross-origin scenarios.

Even simple requests are still subject to CORS rules for whether JavaScript is allowed to read the response.

**Interview Line**

Simple CORS requests meet safelisted method, header, and content-type rules and therefore do not require a preflight request.

### Q. How does CSP help prevent XSS?

**Answer:**

CSP reduces the ability of injected code to execute.

For example, a policy may allow scripts only from the application's own origin:

```http
Content-Security-Policy: script-src 'self'
```

This can block many injected external scripts.

Stronger policies can use nonces or hashes.

**Example:**

```http
Content-Security-Policy: script-src 'nonce-abc123'
```

Only scripts with the matching nonce are allowed.

CSP should be considered defense in depth.

It does not replace proper escaping and sanitization, but it can significantly reduce the impact of an XSS bug.

**Interview Line**

CSP helps mitigate XSS by restricting which scripts are allowed to execute, especially through trusted sources, hashes, or nonces.

### Q. How should cookies be secured?

**Answer:**

Authentication cookies should usually be configured with secure attributes.

**Example:**

```http
Set-Cookie: session=abc123; HttpOnly; Secure; SameSite=Lax; Path=/
```

Important practices include:

- Use HTTPS
- Enable `HttpOnly`
- Enable `Secure`
- Choose an appropriate `SameSite` value
- Use short expiration where practical
- Rotate session identifiers after login or privilege changes
- Limit `Domain` and `Path`
- Invalidate sessions on logout

Highly sensitive cookies should be scoped as narrowly as possible.

**Interview Line**

Secure cookies should use HTTPS, `HttpOnly`, `Secure`, appropriate `SameSite`, limited scope, expiration, and strong session lifecycle management.

### Q. What are `HttpOnly`, `Secure`, and `SameSite` cookie flags?

**Answer:**

These flags provide different security protections.

#### `HttpOnly`

Prevents normal JavaScript from reading the cookie.

```http
Set-Cookie: session=abc; HttpOnly
```

This helps reduce token theft through XSS.

#### `Secure`

Allows the cookie to be sent only over HTTPS.

```http
Set-Cookie: session=abc; Secure
```

#### `SameSite`

Controls when cookies are sent with cross-site requests.

Common values are:

```text
Strict
Lax
None
```

`SameSite=None` generally requires `Secure`.

These flags protect against different attack classes and are often used together.

**Interview Line**

`HttpOnly` blocks JavaScript access, `Secure` restricts cookies to HTTPS, and `SameSite` controls whether cookies are sent with cross-site requests.

### Q. JWT vs Session-based authentication

**Answer:**

Session-based authentication stores session state on the server.

The browser normally receives a session identifier, often in a cookie.

**Flow:**

```text
Login
↓
Server creates session
↓
Browser receives session ID
↓
Server looks up session on later requests
```

JWT authentication stores signed claims inside a token.

**Flow:**

```text
Login
↓
Server issues JWT
↓
Client sends JWT with later requests
↓
Server validates signature and claims
```

JWTs are useful in distributed systems, but token invalidation and rotation require careful design.

Sessions are often simpler when the application is primarily a traditional web application.

**Interview Line**

Sessions keep authentication state on the server, while JWTs carry signed claims in a token; both can be secure when implemented correctly.

### Q. Where should JWT be stored in frontend applications?

**Answer:**

There is no single answer for every architecture, but sensitive long-lived tokens should generally not be stored in `localStorage`.

For browser-based applications, a common secure design is:

- Store refresh/session credentials in `HttpOnly`, `Secure`, `SameSite` cookies
- Keep short-lived access tokens in memory when appropriate
- Avoid exposing long-lived tokens to JavaScript

Why?

Because JavaScript-readable storage is vulnerable to token theft if XSS occurs.

A backend-for-frontend architecture can go further and keep tokens entirely server-side while the browser uses only a secure session cookie.

The correct design depends on:

- Same-site vs cross-site architecture
- API ownership
- Mobile vs browser client
- Token lifetime
- CSRF protections

**Interview Line**

In browser applications, avoid long-lived JWTs in `localStorage`; prefer secure `HttpOnly` cookies or server-side token handling depending on the architecture.

### Q. What is token expiration?

**Answer:**

Token expiration limits how long an authentication token remains valid.

A token often contains an expiration timestamp.

For JWTs, the standard claim is commonly:

```text
exp
```

Short expiration reduces the damage if an access token is stolen.

For example:

```text
Access token: 10 minutes
Refresh token: several days
```

When the access token expires, the client may use a valid refresh mechanism to obtain a new one.

The server must validate expiration and should not trust expired tokens.

**Interview Line**

Token expiration limits the lifetime of credentials so a stolen token is useful only for a restricted period.

### Q. What is refresh token rotation?

**Answer:**

Refresh token rotation means issuing a new refresh token every time the current refresh token is used.

The old refresh token is then invalidated.

**Flow:**

```text
Refresh token A used
↓
Server invalidates A
↓
Server issues refresh token B
```

Next time:

```text
Refresh token B used
↓
Server invalidates B
↓
Server issues refresh token C
```

If an old refresh token is reused unexpectedly, the server can detect possible token theft.

This is more secure than allowing one long-lived refresh token to be reused indefinitely.

**Interview Line**

Refresh token rotation replaces the refresh token after every use and invalidates the previous one, reducing the risk from stolen long-lived credentials.

### Q. What is clickjacking?

**Answer:**

Clickjacking is an attack where a malicious website places another website inside a hidden or transparent frame and tricks the user into clicking something they did not intend to click.

For example, a visible button may be positioned over a transparent iframe containing:

```text
Delete Account
```

The user thinks they are clicking one thing but actually interacts with the framed site.

Clickjacking targets user interface trust rather than injecting JavaScript directly.

**Interview Line**

Clickjacking tricks users into interacting with hidden or disguised UI from another website, often through transparent iframes.

### Q. How do you prevent clickjacking?

**Answer:**

The main protections prevent unauthorized websites from embedding your pages in frames.

Modern protection uses CSP:

```http
Content-Security-Policy: frame-ancestors 'self'
```

To block all framing:

```http
Content-Security-Policy: frame-ancestors 'none'
```

An older widely used header is:

```http
X-Frame-Options: DENY
```

or:

```http
X-Frame-Options: SAMEORIGIN
```

`frame-ancestors` is more flexible and is generally preferred in modern applications.

**Interview Line**

Prevent clickjacking by restricting framing with CSP `frame-ancestors` and, where needed, `X-Frame-Options`.

## Coding Questions (Common)

### Q. Write a function to reverse a string

**Answer:**

A string can be reversed by converting it into an array, reversing the array, and joining it back into a string.

**Example:**

```js
function reverseString(str) {
  return str.split("").reverse().join("");
}

console.log(reverseString("hello"));
```

Output:

```text
olleh
```

A manual approach can also be written without using `reverse()`:

```js
function reverseString(str) {
  let result = "";

  for (let i = str.length - 1; i >= 0; i--) {
    result += str[i];
  }

  return result;
}
```

Time complexity is approximately `O(n)`.

**Interview Line**

Reverse a string by iterating from the end or by using `split()`, `reverse()`, and `join()`.

### Q. Write a function to check if a string is palindrome

**Answer:**

A palindrome reads the same forward and backward.

Examples:

```text
madam
racecar
level
```

A simple approach is to normalize the string, reverse it, and compare it with the original.

**Example:**

```js
function isPalindrome(str) {
  const normalized = str.toLowerCase().replace(/[^a-z0-9]/g, "");

  return normalized === normalized.split("").reverse().join("");
}

console.log(isPalindrome("Madam"));
```

Output:

```js
true;
```

**Interview Line**

A palindrome can be checked by normalizing the string and comparing it with its reversed version.

### Q. Write a function to check if two strings are anagrams

**Answer:**

Two strings are anagrams when they contain the same characters with the same frequencies but possibly in a different order.

For example:

```text
listen
silent
```

**Example:**

```js
function areAnagrams(str1, str2) {
  const normalize = (str) => str.toLowerCase().replace(/\s/g, "").split("").sort().join("");

  return normalize(str1) === normalize(str2);
}

console.log(areAnagrams("listen", "silent"));
```

Output:

```js
true;
```

Sorting makes this approach approximately `O(n log n)`. A character-frequency approach can be implemented in `O(n)` time.

**Interview Line**

Two strings are anagrams when their normalized character frequencies are identical.

### Q. Write a function to find the first non-repeating character

**Answer:**

The common approach is to count the frequency of every character and then scan the string again to find the first character whose frequency is `1`.

**Example:**

```js
function firstNonRepeatingChar(str) {
  const frequency = {};

  for (const char of str) {
    frequency[char] = (frequency[char] || 0) + 1;
  }

  for (const char of str) {
    if (frequency[char] === 1) {
      return char;
    }
  }

  return null;
}

console.log(firstNonRepeatingChar("swiss"));
```

Output:

```text
w
```

Time complexity is `O(n)`.

**Interview Line**

Count character frequencies first, then scan again and return the first character whose frequency is `1`.

### Q. Write a function to remove duplicate characters from a string

**Answer:**

A `Set` is useful because it stores only unique values while preserving insertion order.

**Example:**

```js
function removeDuplicateCharacters(str) {
  return [...new Set(str)].join("");
}

console.log(removeDuplicateCharacters("programming"));
```

Output:

```text
progamin
```

A manual version can also track characters already seen.

```js
function removeDuplicateCharacters(str) {
  const seen = new Set();
  let result = "";

  for (const char of str) {
    if (!seen.has(char)) {
      seen.add(char);
      result += char;
    }
  }

  return result;
}
```

**Interview Line**

Use a `Set` to preserve the first occurrence of each character and remove later duplicates.

### Q. Write a function to flatten a nested array

**Answer:**

If only one level of nesting must be flattened, JavaScript provides `flat(1)`.

**Example:**

```js
function flattenArray(arr) {
  return arr.flat(1);
}

console.log(flattenArray([1, [2, 3], [4, 5]]));
```

Output:

```js
[1, 2, 3, 4, 5];
```

A manual implementation can use `reduce()` and `concat()`:

```js
function flattenArray(arr) {
  return arr.reduce((result, item) => result.concat(item), []);
}
```

This version only flattens one level.

**Interview Line**

For one-level flattening, use `flat(1)` or combine items using `reduce()` and `concat()`.

### Q. Write a function to deeply flatten an array

**Answer:**

Deep flattening means removing nested array levels regardless of depth.

JavaScript can do this directly with `flat(Infinity)`.

**Example:**

```js
function deepFlatten(arr) {
  return arr.flat(Infinity);
}

console.log(deepFlatten([1, [2, [3, [4]]]]));
```

Output:

```js
[1, 2, 3, 4];
```

A recursive implementation is also commonly asked in interviews:

```js
function deepFlatten(arr) {
  const result = [];

  for (const item of arr) {
    if (Array.isArray(item)) {
      result.push(...deepFlatten(item));
    } else {
      result.push(item);
    }
  }

  return result;
}
```

**Interview Line**

Deep flattening can be implemented recursively or with `flat(Infinity)`.

### Q. Write a function to remove duplicates from an array

**Answer:**

For primitive values, the simplest solution is to use a `Set`.

**Example:**

```js
function removeDuplicates(arr) {
  return [...new Set(arr)];
}

console.log(removeDuplicates([1, 2, 2, 3, 3, 4]));
```

Output:

```js
[1, 2, 3, 4];
```

`Set` keeps unique values and preserves insertion order.

For objects, uniqueness must normally be determined using a property such as `id`.

**Interview Line**

For primitive arrays, `[...new Set(array)]` is the simplest way to remove duplicate values.

### Q. Write a function to remove duplicate objects from an array by id

**Answer:**

For objects, a `Map` can use the object `id` as the unique key.

**Example:**

```js
function removeDuplicateById(items) {
  const map = new Map();

  for (const item of items) {
    if (!map.has(item.id)) {
      map.set(item.id, item);
    }
  }

  return [...map.values()];
}

const users = [
  { id: 1, name: "John" },
  { id: 2, name: "Sam" },
  { id: 1, name: "Johnny" },
];

console.log(removeDuplicateById(users));
```

This implementation keeps the first object for each `id`.

If we always call:

```js
map.set(item.id, item);
```

then the last duplicate will be kept instead.

**Interview Line**

Use a `Map` keyed by `id` to efficiently remove duplicate objects and decide whether to preserve the first or last occurrence.

### Q. Write a function to find max and min in an array

**Answer:**

For normal-sized arrays, `Math.max()` and `Math.min()` can be used with spread syntax.

**Example:**

```js
function findMinMax(arr) {
  return {
    min: Math.min(...arr),
    max: Math.max(...arr),
  };
}

console.log(findMinMax([4, 8, 1, 10, 3]));
```

Output:

```js
{
  min: 1,
  max: 10
}
```

For very large arrays, a loop avoids spreading a huge number of arguments.

```js
function findMinMax(arr) {
  let min = Infinity;
  let max = -Infinity;

  for (const value of arr) {
    if (value < min) min = value;
    if (value > max) max = value;
  }

  return { min, max };
}
```

Time complexity is `O(n)`.

**Interview Line**

Find minimum and maximum in one traversal for an efficient `O(n)` solution.

### Q. Write a function to group array items by property

**Answer:**

Grouping means creating a collection where items with the same property value are stored together.

`reduce()` is a common solution.

**Example:**

```js
function groupBy(items, key) {
  return items.reduce((groups, item) => {
    const groupKey = item[key];

    if (!groups[groupKey]) {
      groups[groupKey] = [];
    }

    groups[groupKey].push(item);

    return groups;
  }, {});
}

const users = [
  { name: "John", role: "admin" },
  { name: "Sam", role: "user" },
  { name: "Jane", role: "admin" },
];

console.log(groupBy(users, "role"));
```

Result:

```js
{
  admin: [
    { name: "John", role: "admin" },
    { name: "Jane", role: "admin" }
  ],
  user: [
    { name: "Sam", role: "user" }
  ]
}
```

**Interview Line**

Use `reduce()` to create a group for each property value and push matching items into that group.

### Q. Write a function to count frequency of elements in an array

**Answer:**

A frequency map stores each value and the number of times it appears.

**Example:**

```js
function countFrequency(arr) {
  return arr.reduce((frequency, item) => {
    frequency[item] = (frequency[item] || 0) + 1;
    return frequency;
  }, {});
}

console.log(countFrequency(["apple", "banana", "apple", "orange"]));
```

Output:

```js
{
  apple: 2,
  banana: 1,
  orange: 1
}
```

A `Map` can be preferred when keys may be values other than strings.

**Interview Line**

Build a frequency map by iterating once and incrementing the count for each encountered value.

### Q. Write a debounce function

**Answer:**

Debounce delays function execution until no new call occurs for a specified amount of time.

Every new call resets the timer.

**Example:**

```js
function debounce(fn, delay) {
  let timer;

  return function (...args) {
    clearTimeout(timer);

    timer = setTimeout(() => {
      fn.apply(this, args);
    }, delay);
  };
}
```

Usage:

```js
const search = debounce((query) => {
  console.log("Searching:", query);
}, 500);
```

It is commonly used for:

- Search inputs
- Auto-save
- Validation
- Resize handlers

Using `fn.apply(this, args)` preserves the caller's `this` value and arguments.

**Interview Line**

Debounce resets a timer on every call and executes the function only after calls stop for the specified delay.

### Q. Write a throttle function

**Answer:**

Throttle limits how frequently a function can execute while repeated calls continue.

**Example:**

```js
function throttle(fn, delay) {
  let lastCall = 0;

  return function (...args) {
    const now = Date.now();

    if (now - lastCall >= delay) {
      lastCall = now;
      fn.apply(this, args);
    }
  };
}
```

Usage:

```js
const handleScroll = throttle(() => {
  console.log("Scroll handled");
}, 200);

window.addEventListener("scroll", handleScroll);
```

Even if the scroll event fires many times, the function runs only at the allowed interval.

**Interview Line**

Throttle limits function execution to a maximum frequency and is commonly used for scroll, resize, and mouse-move events.

### Q. Write a deep clone function

**Answer:**

A deep clone creates new copies of nested data instead of keeping nested references shared with the original object.

For supported values in modern JavaScript, the preferred built-in API is `structuredClone()`.

**Example:**

```js
const original = {
  user: {
    name: "John",
  },
};

const clone = structuredClone(original);

clone.user.name = "Sam";

console.log(original.user.name);
```

Output:

```text
John
```

A simplified recursive interview implementation for arrays and plain objects is:

```js
function deepClone(value) {
  if (value === null || typeof value !== "object") {
    return value;
  }

  if (Array.isArray(value)) {
    return value.map(deepClone);
  }

  const clone = {};

  for (const key of Object.keys(value)) {
    clone[key] = deepClone(value[key]);
  }

  return clone;
}
```

This simplified version does not fully handle special types such as `Date`, `Map`, `Set`, circular references, or typed arrays.

**Interview Line**

Use `structuredClone()` when available; recursive cloning is useful for demonstrating the core deep-clone concept in interviews.

### Q. Write a custom `map()` method

**Answer:**

`map()` creates a new array by calling a callback for every existing array element and storing each returned value.

**Example:**

```js
Array.prototype.myMap = function (callback, thisArg) {
  const result = [];

  for (let i = 0; i < this.length; i++) {
    if (!(i in this)) continue;

    result[i] = callback.call(thisArg, this[i], i, this);
  }

  return result;
};
```

Usage:

```js
const numbers = [1, 2, 3];

const doubled = numbers.myMap((number) => number * 2);

console.log(doubled);
```

Output:

```js
[2, 4, 6];
```

The native specification has additional edge cases, but this implementation demonstrates the main behavior.

**Interview Line**

A custom `map()` iterates through the array, invokes the callback, and stores every callback result in a new array.

### Q. Write a custom `filter()` method

**Answer:**

`filter()` creates a new array containing only elements for which the callback returns a truthy value.

**Example:**

```js
Array.prototype.myFilter = function (callback, thisArg) {
  const result = [];

  for (let i = 0; i < this.length; i++) {
    if (!(i in this)) continue;

    if (callback.call(thisArg, this[i], i, this)) {
      result.push(this[i]);
    }
  }

  return result;
};
```

Usage:

```js
const numbers = [1, 2, 3, 4];

const even = numbers.myFilter((number) => number % 2 === 0);

console.log(even);
```

Output:

```js
[2, 4];
```

**Interview Line**

A custom `filter()` tests each element and adds it to a new array only when the callback returns a truthy value.

### Q. Write a custom `reduce()` method

**Answer:**

`reduce()` processes an array and combines its elements into a single accumulated result.

**Example:**

```js
Array.prototype.myReduce = function (callback, initialValue) {
  let index = 0;
  let accumulator;

  if (arguments.length > 1) {
    accumulator = initialValue;
  } else {
    while (index < this.length && !(index in this)) {
      index++;
    }

    if (index >= this.length) {
      throw new TypeError("Reduce of empty array with no initial value");
    }

    accumulator = this[index++];
  }

  for (; index < this.length; index++) {
    if (!(index in this)) continue;

    accumulator = callback(accumulator, this[index], index, this);
  }

  return accumulator;
};
```

Usage:

```js
const total = [1, 2, 3, 4].myReduce((sum, value) => sum + value, 0);

console.log(total);
```

Output:

```js
10;
```

**Interview Line**

A custom `reduce()` maintains an accumulator and updates it with the reducer callback for each array element.

### Q. Write a custom `bind()` method

**Answer:**

`bind()` creates a new function with a fixed `this` value and optional pre-filled arguments.

A simplified interview implementation is:

```js
Function.prototype.myBind = function (context, ...boundArgs) {
  const fn = this;

  return function (...args) {
    return fn.apply(context, [...boundArgs, ...args]);
  };
};
```

Usage:

```js
function greet(greeting, punctuation) {
  return `${greeting} ${this.name}${punctuation}`;
}

const user = {
  name: "John",
};

const greetJohn = greet.myBind(user, "Hello");

console.log(greetJohn("!"));
```

Output:

```text
Hello John!
```

The real native `bind()` also has special constructor behavior when the bound function is called with `new`, which this simplified version does not fully reproduce.

**Interview Line**

`bind()` returns a new function with a fixed `this` value and can also pre-fill arguments.

### Q. Write a custom `call()` method

**Answer:**

`call()` invokes a function immediately with a specified `this` value and individual arguments.

A simplified implementation temporarily places the function on the context object.

**Example:**

```js
Function.prototype.myCall = function (context, ...args) {
  context = context == null ? globalThis : Object(context);

  const key = Symbol("fn");

  context[key] = this;

  const result = context[key](...args);

  delete context[key];

  return result;
};
```

Usage:

```js
function greet(message) {
  return `${message}, ${this.name}`;
}

const user = {
  name: "John",
};

console.log(greet.myCall(user, "Hello"));
```

Output:

```text
Hello, John
```

A `Symbol` is used to avoid colliding with an existing object property.

**Interview Line**

A custom `call()` invokes the function as a temporary method of the provided context so `this` points to that context.

### Q. Write a custom `apply()` method

**Answer:**

`apply()` behaves similarly to `call()`, except arguments are passed as an array or array-like value.

**Example:**

```js
Function.prototype.myApply = function (context, args = []) {
  context = context == null ? globalThis : Object(context);

  const key = Symbol("fn");

  context[key] = this;

  const result = context[key](...args);

  delete context[key];

  return result;
};
```

Usage:

```js
function add(a, b) {
  return a + b + this.extra;
}

const obj = {
  extra: 10,
};

console.log(add.myApply(obj, [2, 3]));
```

Output:

```js
15;
```

**Interview Line**

`apply()` works like `call()`, but receives function arguments as an array or array-like collection.

### Q. Write a custom `Promise.all()`

**Answer:**

`Promise.all()` waits for all input values to resolve and returns the resolved values in the same order as the input.

If any input Promise rejects, the returned Promise rejects with that reason.

**Example:**

```js
function myPromiseAll(iterable) {
  const items = Array.from(iterable);

  return new Promise((resolve, reject) => {
    if (items.length === 0) {
      resolve([]);
      return;
    }

    const results = new Array(items.length);
    let completed = 0;

    items.forEach((item, index) => {
      Promise.resolve(item)
        .then((value) => {
          results[index] = value;
          completed++;

          if (completed === items.length) {
            resolve(results);
          }
        })
        .catch(reject);
    });
  });
}
```

Usage:

```js
myPromiseAll([Promise.resolve(10), 20, Promise.resolve(30)]).then(console.log);
```

Output:

```js
[10, 20, 30];
```

Using `Promise.resolve()` also supports normal values and Promise-like values.

**Interview Line**

A custom `Promise.all()` stores results by input index, resolves when all complete, and rejects when any input rejects.

### Q. Write a custom `Promise.race()`

**Answer:**

`Promise.race()` settles as soon as the first input Promise settles.

The first settled Promise may either resolve or reject.

**Example:**

```js
function myPromiseRace(iterable) {
  return new Promise((resolve, reject) => {
    for (const item of iterable) {
      Promise.resolve(item).then(resolve).catch(reject);
    }
  });
}
```

Usage:

```js
const slow = new Promise((resolve) => {
  setTimeout(() => resolve("slow"), 1000);
});

const fast = new Promise((resolve) => {
  setTimeout(() => resolve("fast"), 100);
});

myPromiseRace([slow, fast]).then(console.log);
```

Output:

```text
fast
```

**Interview Line**

`Promise.race()` settles with whichever input Promise resolves or rejects first.

### Q. Write a custom `once()` function

**Answer:**

A `once()` function ensures that another function executes only on its first invocation.

Later calls return the previously computed result.

**Example:**

```js
function once(fn) {
  let called = false;
  let result;

  return function (...args) {
    if (!called) {
      result = fn.apply(this, args);
      called = true;
    }

    return result;
  };
}
```

Usage:

```js
const initialize = once(() => {
  console.log("Initialized");
  return 100;
});

console.log(initialize());
console.log(initialize());
```

Output:

```text
Initialized
100
100
```

The closure preserves whether the original function has already run.

**Interview Line**

`once()` uses closure state to guarantee that a function executes only on its first call.

### Q. Write a memoization function

**Answer:**

Memoization stores function results so calls with the same inputs can reuse the previous result.

**Example:**

```js
function memoize(fn) {
  const cache = new Map();

  return function (...args) {
    const key = JSON.stringify(args);

    if (cache.has(key)) {
      return cache.get(key);
    }

    const result = fn.apply(this, args);

    cache.set(key, result);

    return result;
  };
}
```

Usage:

```js
const multiply = memoize((a, b) => {
  console.log("Calculating");
  return a * b;
});

console.log(multiply(5, 10));
console.log(multiply(5, 10));
```

`Calculating` is printed only once for the same arguments.

`JSON.stringify(args)` is acceptable for a simple interview implementation, but it is not a perfect cache key for every value, especially circular objects, functions, or object-identity requirements.

**Interview Line**

Memoization caches function results based on arguments so repeated calls can avoid recalculating the same result.

### Q. Write a function to limit concurrent promises

**Answer:**

Concurrency limiting ensures that only a fixed number of asynchronous tasks execute at the same time.

This is useful when many API calls must be made without overloading the browser or server.

**Example:**

```js
async function runWithLimit(taskFunctions, limit) {
  const results = new Array(taskFunctions.length);
  let nextIndex = 0;

  async function worker() {
    while (true) {
      const currentIndex = nextIndex++;

      if (currentIndex >= taskFunctions.length) {
        return;
      }

      results[currentIndex] = await taskFunctions[currentIndex]();
    }
  }

  const workerCount = Math.min(limit, taskFunctions.length);

  const workers = Array.from({ length: workerCount }, () => worker());

  await Promise.all(workers);

  return results;
}
```

Usage:

```js
const tasks = [() => fetch("/api/1"), () => fetch("/api/2"), () => fetch("/api/3"), () => fetch("/api/4")];

runWithLimit(tasks, 2).then(console.log);
```

At most two tasks execute concurrently.

**Interview Line**

Concurrency limiting uses a fixed number of workers so no more than the configured number of asynchronous tasks run simultaneously.

### Q. Write a function to retry failed API calls

**Answer:**

A retry function attempts an asynchronous operation again when it fails, but the retry count should always be limited.

**Example:**

```js
async function retry(fn, retries = 3, delay = 500) {
  let lastError;

  for (let attempt = 1; attempt <= retries; attempt++) {
    try {
      return await fn();
    } catch (error) {
      lastError = error;

      if (attempt < retries) {
        await new Promise((resolve) => {
          setTimeout(resolve, delay);
        });
      }
    }
  }

  throw lastError;
}
```

Usage:

```js
const fetchUsers = () =>
  fetch("/api/users").then((response) => {
    if (!response.ok) {
      throw new Error("Request failed");
    }

    return response.json();
  });

retry(fetchUsers, 3, 1000).then(console.log).catch(console.error);
```

In production, retries should normally be used only for transient failures such as network problems or selected `5xx` errors.

Permanent failures such as invalid input, authentication failure, or authorization failure generally should not be retried automatically.

A more advanced implementation may use exponential backoff and jitter.

**Interview Line**

A retry function repeats a failed asynchronous operation up to a defined limit and should generally retry only transient failures.

## Tricky Output-Based Questions ⭐

### Q. Output of console.log(typeof null)

**Answer:**

Output:

```js
object;
```

Example:

```js
console.log(typeof null); // "object"
```

This is a historical bug in JavaScript. `null` is not actually an object; it is a primitive value representing intentional absence.

Correct null check:

```js
value === null;
```

**Interview Line**

`typeof null` returns `"object"` due to a legacy JavaScript bug.

### Q. Output of [] == []

**Answer:**

Output:

```js
false;
```

Example:

```js
console.log([] == []); // false
```

Arrays are objects, and objects are compared by reference. Each `[]` creates a new array in memory, so both references are different.

```js
const a = [];
const b = a;

console.log(a == b); // true
```

**Interview Line**

Two arrays are equal only if they reference the same array object.

### Q. Output of 0 == false

**Answer:**

Output:

```js
true;
```

Example:

```js
console.log(0 == false); // true
```

`==` performs type coercion. `false` is converted to `0`, so the comparison becomes:

```js
0 == 0;
```

With strict equality:

```js
console.log(0 === false); // false
```

**Interview Line**

`0 == false` is true because loose equality converts `false` to `0`.

### Q. Output of `setTimeout` inside loop

**Answer:**

A common interview question uses `setTimeout()` inside a loop with `var`.

**Example:**

```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => {
    console.log(i);
  }, 0);
}
```

**Output:**

```text
3
3
3
```

This happens because `var` is function-scoped, not block-scoped.

The loop finishes before the `setTimeout()` callbacks execute.

By the time the callbacks run, the single shared variable `i` has already become:

```js
3;
```

All callbacks reference the same `i`.

If we use `let`:

```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => {
    console.log(i);
  }, 0);
}
```

**Output:**

```text
0
1
2
```

`let` creates a new block-scoped binding for each loop iteration.

**Interview Line**

With `var`, all delayed callbacks share the same loop variable, while `let` creates a separate binding for every iteration.

### Q. Output of closure inside loop

**Answer:**

Closures capture variables from their outer lexical scope.

Consider:

```js
const functions = [];

for (var i = 0; i < 3; i++) {
  functions.push(() => {
    console.log(i);
  });
}

functions[0]();
functions[1]();
functions[2]();
```

**Output:**

```text
3
3
3
```

Each function closes over the same `var i`.

The loop completes first, leaving:

```js
i = 3;
```

Then each stored function reads the current value of that same variable.

Using `let` changes the result:

```js
const functions = [];

for (let i = 0; i < 3; i++) {
  functions.push(() => {
    console.log(i);
  });
}

functions[0]();
functions[1]();
functions[2]();
```

**Output:**

```text
0
1
2
```

This happens because each iteration receives its own `i` binding.

Before `let`, an IIFE was commonly used to create a separate scope:

```js
for (var i = 0; i < 3; i++) {
  ((value) => {
    functions.push(() => {
      console.log(value);
    });
  })(i);
}
```

**Interview Line**

Closures capture variables, not frozen values; with `var`, every closure shares the same binding, while `let` creates a new binding per iteration.

### Q. Output of `this` in different contexts

**Answer:**

The value of `this` depends on how a function is called.

Consider an object method:

```js
const user = {
  name: "John",

  showName() {
    console.log(this.name);
  },
};

user.showName();
```

**Output:**

```text
John
```

Here, `this` refers to `user` because the function is called as:

```js
user.showName();
```

Now consider:

```js
const show = user.showName;

show();
```

In strict mode, `this` inside a normal standalone function call is:

```js
undefined;
```

So accessing:

```js
this.name;
```

can throw an error.

Now consider an arrow function:

```js
const user = {
  name: "John",

  showName: () => {
    console.log(this.name);
  },
};

user.showName();
```

The arrow function does not get its own `this`.

It captures `this` lexically from the surrounding scope, so it does not automatically refer to `user`.

A useful nested example:

```js
const user = {
  name: "John",

  show() {
    const inner = () => {
      console.log(this.name);
    };

    inner();
  },
};

user.show();
```

**Output:**

```text
John
```

The arrow function inherits `this` from `show()`.

**Interview Line**

Normal functions get `this` from the call-site, while arrow functions capture `this` lexically from their surrounding scope.

### Q. Hoisting output questions

**Answer:**

Hoisting means JavaScript processes declarations before executing code, but different declarations behave differently.

Consider `var`:

```js
console.log(a);

var a = 10;
```

**Output:**

```text
undefined
```

Conceptually, JavaScript behaves like:

```js
var a;

console.log(a);

a = 10;
```

The declaration is hoisted, but the assignment is not.

Now consider a function declaration:

```js
greet();

function greet() {
  console.log("Hello");
}
```

**Output:**

```text
Hello
```

Function declarations are hoisted with their complete function body.

Now consider a function expression:

```js
greet();

var greet = function () {
  console.log("Hello");
};
```

This results in an error because `greet` is initially:

```js
undefined;
```

and JavaScript attempts to call:

```js
undefined();
```

With `let` and `const`:

```js
console.log(a);

let a = 10;
```

This throws a `ReferenceError` because the variable is in the Temporal Dead Zone.

**Interview Line**

`var` declarations are hoisted and initialized with `undefined`, function declarations are fully hoisted, while `let` and `const` remain inaccessible in the Temporal Dead Zone until initialization.

### Q. Promise output order

**Answer:**

Promise callbacks run as microtasks.

Microtasks execute after the current synchronous code finishes but before timer callbacks such as `setTimeout()`.

**Example:**

```js
console.log("A");

Promise.resolve().then(() => {
  console.log("B");
});

console.log("C");
```

**Output:**

```text
A
C
B
```

First, synchronous code runs:

```text
A
C
```

Then the Promise callback runs from the microtask queue:

```text
B
```

Another example:

```js
console.log("1");

Promise.resolve()
  .then(() => {
    console.log("2");
  })
  .then(() => {
    console.log("3");
  });

console.log("4");
```

**Output:**

```text
1
4
2
3
```

Each `.then()` callback is scheduled as a microtask after the previous Promise settles.

**Interview Line**

Promise callbacks run in the microtask queue after synchronous code but before macrotasks such as timers.

### Q. Event loop output questions

**Answer:**

The event loop coordinates synchronous code, microtasks, and task queues.

Consider:

```js
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

Promise.resolve().then(() => {
  console.log("Promise");
});

console.log("End");
```

**Output:**

```text
Start
End
Promise
Timeout
```

The execution order is:

1. Run synchronous code.
2. Process all microtasks.
3. Process the next task such as a timer.

So:

```text
Start
End
```

run first.

Then:

```text
Promise
```

runs from the microtask queue.

Finally:

```text
Timeout
```

runs from the timer task queue.

A more complex example:

```js
console.log("A");

setTimeout(() => {
  console.log("B");
}, 0);

Promise.resolve().then(() => {
  console.log("C");

  Promise.resolve().then(() => {
    console.log("D");
  });
});

console.log("E");
```

**Output:**

```text
A
E
C
D
B
```

JavaScript drains the microtask queue completely before moving to the next task.

**Interview Line**

The event loop runs synchronous code first, then drains microtasks such as Promise callbacks, and then processes tasks such as `setTimeout()`.

### Q. Temporal Dead Zone examples

**Answer:**

The Temporal Dead Zone, or TDZ, is the time between entering a scope and initializing a `let` or `const` variable.

During this period, the variable exists but cannot be accessed.

**Example:**

```js
console.log(age);

let age = 25;
```

**Output:**

```text
ReferenceError
```

The variable is hoisted conceptually, but unlike `var`, it is not initialized with `undefined`.

Another example:

```js
{
  console.log(name);

  const name = "John";
}
```

This also throws:

```text
ReferenceError
```

Now compare it with `var`:

```js
console.log(age);

var age = 25;
```

**Output:**

```text
undefined
```

The TDZ also explains this behavior:

```js
let value = 10;

{
  console.log(value);

  let value = 20;
}
```

This throws a `ReferenceError`.

Even though an outer `value` exists, the inner `let value` shadows it for the entire block.

Before the inner declaration executes, that inner variable is still inside its TDZ.

**Interview Line**

The Temporal Dead Zone is the period where a `let` or `const` binding exists in scope but cannot be accessed before its initialization line executes.

### Q. What is the output of `console.log(typeof null)`?

**Answer:**

Output:

```js
object;
```

Example:

```js
console.log(typeof null); // "object"
```

This is a historical bug in JavaScript. `null` is not actually an object; it is a primitive value representing intentional absence.

Correct null check:

```js
value === null;
```

**Interview Line**

`typeof null` returns `"object"` due to a legacy JavaScript bug.

### Q. What is the output of `console.log([] == [])`?

**Answer:**

Output:

```js
false;
```

Example:

```js
console.log([] == []); // false
```

Arrays are objects, and objects are compared by reference. Each `[]` creates a new array in memory, so both references are different.

```js
const a = [];
const b = a;

console.log(a == b); // true
```

**Interview Line**

Two arrays are equal only if they reference the same array object.

### Q. What is the output of `console.log({} == {})`?

**Answer:**

Output:

```js
false;
```

Example:

```js
console.log({} == {}); // false
```

Objects are compared by reference, not by content. Each `{}` creates a new object in memory.

```js
const obj = {};
const same = obj;

console.log(obj == same); // true
```

**Interview Line**

Objects with the same structure are not equal unless they share the same reference.

### Q. What is the output of `console.log(0 == false)`?

**Answer:**

Output:

```js
true;
```

Example:

```js
console.log(0 == false); // true
```

`==` performs type coercion. `false` is converted to `0`, so the comparison becomes:

```js
0 == 0;
```

With strict equality:

```js
console.log(0 === false); // false
```

**Interview Line**

`0 == false` is true because loose equality converts `false` to `0`.

### Q. What is the output of `console.log("" == false)`?

**Answer:**

Output:

```js
true;
```

Example:

```js
console.log("" == false); // true
```

Loose equality converts both values to numbers:

```js
Number(""); // 0
Number(false); // 0
```

So comparison becomes:

```js
0 == 0;
```

Use `===` to avoid this confusion.

**Interview Line**

`"" == false` is true due to type coercion.

### Q. What is the output of `console.log(null == undefined)`?

**Answer:**

Output:

```js
true;
```

Example:

```js
console.log(null == undefined); // true
```

In JavaScript loose equality, `null` and `undefined` are considered equal only to each other.

But with strict equality:

```js
console.log(null === undefined); // false
```

**Interview Line**

`null == undefined` is true by special loose equality rule.

### Q. What is the output of `console.log(null === undefined)`?

**Answer:**

Output:

```js
false;
```

Example:

```js
console.log(null === undefined); // false
```

Strict equality compares both value and type.

```js
typeof null; // "object"
typeof undefined; // "undefined"
```

They are different types.

**Interview Line**

`null === undefined` is false because strict equality checks type also.

### Q. What is the output of `console.log(NaN === NaN)`?

**Answer:**

Output:

```js
false;
```

Example:

```js
console.log(NaN === NaN); // false
```

`NaN` is the only JavaScript value that is not equal to itself.

Correct checks:

```js
Number.isNaN(NaN); // true
Object.is(NaN, NaN); // true
```

**Interview Line**

`NaN === NaN` is false; use `Number.isNaN()` to check for `NaN`.

### Q. What is the output of `console.log(Object.is(NaN, NaN))`?

**Answer:**

Output:

```js
true;
```

Example:

```js
console.log(Object.is(NaN, NaN)); // true
```

Unlike `===`, `Object.is()` treats `NaN` as equal to `NaN`.

```js
console.log(NaN === NaN); // false
```

**Interview Line**

`Object.is()` correctly treats `NaN` as equal to itself.

### Q. What is the output of `console.log(1 + "2" + 3)`?

**Answer:**

Output:

```js
"123";
```

Example:

```js
console.log(1 + "2" + 3); // "123"
```

Evaluation happens left to right:

```js
1 + "2"; // "12"
"12" + 3; // "123"
```

When `+` has a string operand, it performs string concatenation.

**Interview Line**

String concatenation starts once JavaScript encounters a string with `+`.

### Q. What is the output of `console.log(1 + +"2" + 3)`?

**Answer:**

Output:

```js
6;
```

Example:

```js
console.log(1 + +"2" + 3); // 6
```

The unary plus converts `"2"` into number `2`.

```js
+"2"; // 2
```

Then:

```js
1 + 2 + 3; // 6
```

**Interview Line**

Unary plus converts a string to a number before addition.

### Q. What is the output of `console.log([] + [])`?

**Answer:**

Output:

```js
"";
```

Example:

```js
console.log([] + []); // ""
```

Both arrays are converted to strings.

```js
[].toString(); // ""
```

So:

```js
"" + ""; // ""
```

**Interview Line**

Empty arrays convert to empty strings during `+` operation.

### Q. What is the output of `console.log([] + {})`?

**Answer:**

Output:

```js
"[object Object]";
```

Example:

```js
console.log([] + {}); // "[object Object]"
```

`[]` converts to an empty string, and `{}` converts to `"[object Object]"`.

```js
"" + "[object Object]";
```

**Interview Line**

Array becomes `""`, object becomes `"[object Object]"`, so result is `"[object Object]"`.

### Q. What is the output of `console.log({} + [])`?

**Answer:**

Output can depend on context.

Inside `console.log`:

```js
console.log({} + []); // "[object Object]"
```

Here `{}` is treated as an object expression and `[]` becomes an empty string.

But at the beginning of a statement in some environments:

```js
{
}
+[];
```

`{}` may be treated as an empty block, and `+[]` becomes `0`.

**Interview Line**

`{} + []` is tricky because `{}` can be parsed as an object or a block depending on context.

### Q. What is the output of `setTimeout` with 0 delay?

**Answer:**

Even when `setTimeout()` has a delay of `0`, the callback does not execute immediately.

It is placed into the task queue and runs only after the current synchronous code and pending microtasks are completed.

**Example:**

```js
console.log("A");

setTimeout(() => {
  console.log("B");
}, 0);

console.log("C");
```

**Output:**

```text
A
C
B
```

Execution happens like this:

1. `console.log("A")` runs synchronously.
2. `setTimeout()` schedules its callback.
3. `console.log("C")` runs synchronously.
4. After the current call stack becomes empty, the timer callback runs.

So `0` means there is no intentional minimum delay beyond scheduling, not that the callback runs instantly.

**Interview Line**

`setTimeout(fn, 0)` schedules the callback for a future task; it still waits until the current synchronous work and microtasks are finished.

### Q. What is the output order of Promise and `setTimeout`?

**Answer:**

Promise callbacks are scheduled as microtasks, while `setTimeout()` callbacks are scheduled as tasks.

Microtasks are processed before the next task.

**Example:**

```js
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

Promise.resolve().then(() => {
  console.log("Promise");
});

console.log("End");
```

**Output:**

```text
Start
End
Promise
Timeout
```

The order is:

1. Synchronous code
2. Microtasks
3. Tasks such as timers

So the Promise callback runs before the `setTimeout()` callback.

**Interview Line**

Promise callbacks run before `setTimeout()` callbacks because microtasks are drained before the browser moves to the next task.

### Q. What is the output of async/await with `Promise.resolve`?

**Answer:**

An `async` function runs synchronously until it reaches `await`.

When `await` is encountered, the remaining part of the function continues later as a microtask.

**Example:**

```js
console.log("A");

async function test() {
  console.log("B");

  await Promise.resolve();

  console.log("C");
}

test();

console.log("D");
```

**Output:**

```text
A
B
D
C
```

Why?

`test()` starts immediately and prints:

```text
B
```

Then execution pauses at:

```js
await Promise.resolve();
```

The remaining code is scheduled as a microtask.

Meanwhile, synchronous code continues and prints:

```text
D
```

Then the microtask resumes and prints:

```text
C
```

**Interview Line**

`await` pauses the async function and schedules the remaining code as a microtask, so synchronous code outside the function continues first.

### Q. What is the output of closure inside loop using `var`?

**Answer:**

`var` is function-scoped, so every closure created inside the loop shares the same variable.

**Example:**

```js
const functions = [];

for (var i = 0; i < 3; i++) {
  functions.push(() => {
    console.log(i);
  });
}

functions[0]();
functions[1]();
functions[2]();
```

**Output:**

```text
3
3
3
```

By the time the functions execute, the loop has completed and:

```js
i === 3;
```

All three closures reference that same variable.

**Interview Line**

Closures created with `var` inside a loop share one binding, so they all see the final value after the loop finishes.

### Q. What is the output of closure inside loop using `let`?

**Answer:**

`let` creates a new block-scoped binding for each loop iteration.

Each closure therefore remembers a different value of `i`.

**Example:**

```js
const functions = [];

for (let i = 0; i < 3; i++) {
  functions.push(() => {
    console.log(i);
  });
}

functions[0]();
functions[1]();
functions[2]();
```

**Output:**

```text
0
1
2
```

Each iteration has its own separate `i`.

So the closures preserve:

```text
0
1
2
```

independently.

**Interview Line**

`let` creates a separate loop binding for each iteration, so every closure captures its own value.

### Q. What is the output of hoisting with `var`?

**Answer:**

`var` declarations are hoisted and initialized with `undefined`.

The assignment happens only when execution reaches that line.

**Example:**

```js
console.log(a);

var a = 10;

console.log(a);
```

**Output:**

```text
undefined
10
```

Conceptually, JavaScript behaves like:

```js
var a;

console.log(a);

a = 10;

console.log(a);
```

The declaration exists before the first `console.log()`, but the value is still `undefined`.

**Interview Line**

`var` is hoisted and initialized with `undefined`, so accessing it before assignment does not throw an error.

### Q. What is the output of hoisting with `let`?

**Answer:**

`let` declarations are also hoisted, but they are not initialized immediately.

They remain inside the Temporal Dead Zone until execution reaches the declaration.

**Example:**

```js
console.log(a);

let a = 10;
```

**Output:**

```text
ReferenceError
```

The variable exists in the scope, but it cannot be accessed before:

```js
let a = 10;
```

executes.

This behavior is different from `var`, which returns `undefined`.

**Interview Line**

`let` is hoisted but remains inaccessible inside the Temporal Dead Zone until its declaration is initialized.

### Q. What is the output of calling a function before declaration?

**Answer:**

Function declarations are hoisted with their complete function definition.

Because of this, they can be called before the declaration appears in the source code.

**Example:**

```js
greet();

function greet() {
  console.log("Hello");
}
```

**Output:**

```text
Hello
```

During the creation phase, JavaScript makes the full function declaration available.

So by the time execution starts:

```js
greet;
```

already references the function.

**Interview Line**

Function declarations are fully hoisted, so they can be called before their declaration appears in the code.

### Q. What is the output of calling a function expression before initialization?

**Answer:**

A function expression behaves according to the variable declaration used to store it.

With `var`, the variable is hoisted as `undefined`.

**Example:**

```js
greet();

var greet = function () {
  console.log("Hello");
};
```

**Output:**

```text
TypeError
```

Conceptually:

```js
var greet;

greet();

greet = function () {
  console.log("Hello");
};
```

At the time of the call:

```js
greet === undefined;
```

So JavaScript attempts to call:

```js
undefined();
```

which throws a `TypeError`.

With `let` or `const`, calling before initialization would instead throw a `ReferenceError` because of the Temporal Dead Zone.

**Interview Line**

Function expressions are not fully hoisted like function declarations; only the variable declaration is hoisted, so calling them too early causes an error.

### Q. What is the output of `this` inside regular function?

**Answer:**

For a regular function, `this` depends on how the function is called.

Consider a standalone function call.

**Example:**

```js
"use strict";

function showThis() {
  console.log(this);
}

showThis();
```

**Output:**

```text
undefined
```

In strict mode, a normal standalone function call gets:

```js
this === undefined;
```

Without strict mode in a classic browser script, `this` may refer to the global object:

```js
window;
```

So the exact result depends on execution mode and environment.

**Interview Line**

In a regular function, `this` is determined by the call-site; for a standalone call in strict mode, it is `undefined`.

### Q. What is the output of `this` inside arrow function?

**Answer:**

Arrow functions do not create their own `this`.

They capture `this` from the surrounding lexical scope.

**Example:**

```js
const user = {
  name: "John",

  showName: () => {
    console.log(this.name);
  },
};

user.showName();
```

**Output:**

The output is not:

```text
John
```

because the arrow function does not bind `this` to `user`.

It uses the surrounding `this` instead.

In many module contexts, that surrounding `this` is `undefined`.

A better example is:

```js
const user = {
  name: "John",

  showName() {
    const inner = () => {
      console.log(this.name);
    };

    inner();
  },
};

user.showName();
```

**Output:**

```text
John
```

Here the arrow function inherits `this` from `showName()`.

**Interview Line**

Arrow functions do not have their own `this`; they inherit it lexically from the surrounding scope.

### Q. What is the output of `this` inside object method?

**Answer:**

When a regular function is called as an object method, `this` refers to the object before the dot.

**Example:**

```js
const user = {
  name: "John",

  showName() {
    console.log(this.name);
  },
};

user.showName();
```

**Output:**

```text
John
```

The call:

```js
user.showName();
```

makes:

```js
this === user;
```

inside `showName()`.

But if the method is detached:

```js
const show = user.showName;

show();
```

then `this` is no longer automatically `user`.

In strict mode, it becomes:

```js
undefined;
```

for a standalone call.

**Interview Line**

Inside a regular object method, `this` refers to the object used to call the method.

### Q. What is the output of `this` inside nested function?

**Answer:**

A normal nested function does not automatically inherit `this` from its outer method.

**Example:**

```js
"use strict";

const user = {
  name: "John",

  showName() {
    function inner() {
      console.log(this);
    }

    inner();
  },
};

user.showName();
```

**Output:**

```text
undefined
```

`showName()` is called as an object method, so inside it:

```js
this === user;
```

But `inner()` is called as a normal standalone function.

Therefore, in strict mode:

```js
this === undefined;
```

If we want the nested function to use the outer `this`, an arrow function is a common solution.

```js
const user = {
  name: "John",

  showName() {
    const inner = () => {
      console.log(this.name);
    };

    inner();
  },
};

user.showName();
```

**Output:**

```text
John
```

**Interview Line**

A normal nested function gets its own `this` from how it is called, while an arrow function can inherit `this` from the surrounding method.

## Modules & Bundlers

### Q. What is a JavaScript module?

**Answer:**

A JavaScript module is a file that contains reusable code and can explicitly export values for other files to import.

A module can contain:

- Variables
- Functions
- Classes
- Constants
- Configuration
- Utility logic

**Example:**

```js
// math.js
export function add(a, b) {
  return a + b;
}
```

Another file can import it:

```js
import { add } from "./math.js";

console.log(add(2, 3));
```

Modules help divide a large application into smaller, independent units.

**Interview Line**

A JavaScript module is a reusable file that exposes selected values through exports and consumes other modules through imports.

### Q. Why do we use modules?

**Answer:**

Modules help organize large applications by separating responsibilities into smaller files.

Without modules, application code can become difficult to maintain because many variables and functions may exist in the same global scope.

Benefits include:

- Better code organization
- Reusability
- Encapsulation
- Easier testing
- Reduced global namespace pollution
- Clear dependency relationships
- Better collaboration between developers

**Example:**

```text
services/
  userService.js

utils/
  date.js

components/
  modal.js
```

Each file handles one responsibility instead of keeping all logic in a single script.

**Interview Line**

Modules improve maintainability by separating responsibilities, reducing global scope pollution, and making dependencies explicit.

### Q. Difference between ES Modules and CommonJS

**Answer:**

ES Modules and CommonJS are two module systems used in JavaScript.

ES Modules use:

```js
import
export
```

CommonJS uses:

```js
require();
module.exports;
```

**Example:**

ES Module:

```js
export const add = (a, b) => a + b;

import { add } from "./math.js";
```

CommonJS:

```js
const add = (a, b) => a + b;

module.exports = {
  add,
};

const { add } = require("./math");
```

Main differences:

| ES Modules                               | CommonJS                            |
| ---------------------------------------- | ----------------------------------- |
| Standard JavaScript module system        | Traditionally used by Node.js       |
| Uses `import` and `export`               | Uses `require` and `module.exports` |
| Static structure                         | More runtime-oriented               |
| Better suited for tree shaking           | Harder to tree shake                |
| Supported by browsers and modern Node.js | Mainly associated with Node.js      |

**Interview Line**

ES Modules use static `import` and `export`, while CommonJS uses `require()` and `module.exports`.

### Q. What is named export?

**Answer:**

A named export allows a module to export multiple values using their declared names.

**Example:**

```js
export const API_URL = "/api";

export function add(a, b) {
  return a + b;
}
```

Import:

```js
import { API_URL, add } from "./utils.js";
```

The imported names normally need to match the exported names.

They can also be renamed during import:

```js
import { add as calculateSum } from "./utils.js";
```

A module can have multiple named exports.

**Interview Line**

Named exports allow multiple explicitly named values to be exported from one module.

### Q. What is default export?

**Answer:**

A default export represents the primary value exported by a module.

A module can have only one default export.

**Example:**

```js
export default function UserService() {
  return "User Service";
}
```

Import:

```js
import UserService from "./UserService.js";
```

The importer can choose any local name:

```js
import MyService from "./UserService.js";
```

This differs from named exports, where the original export name is normally used.

**Interview Line**

A default export is the main export of a module, and a module can contain only one default export.

### Q. What is dynamic import?

**Answer:**

Dynamic import allows a module to be loaded at runtime instead of during initial module evaluation.

It uses:

```js
import()
```

and returns a Promise.

**Example:**

```js
async function loadChart() {
  const module = await import("./chart.js");

  module.renderChart();
}
```

Dynamic imports are useful when a module is:

- Large
- Optional
- Route-specific
- Needed only after user interaction

**Interview Line**

Dynamic import uses `import()` to load a module at runtime and returns a Promise containing the module.

### Q. What is lazy loading using dynamic import?

**Answer:**

Lazy loading means delaying module loading until the feature is actually needed.

Dynamic import makes this possible.

**Example:**

```js
button.addEventListener("click", async () => {
  const { openEditor } = await import("./editor.js");

  openEditor();
});
```

The editor code is not required during initial page load.

It is downloaded only when the user clicks the button.

Benefits include:

- Smaller initial bundle
- Faster initial page load
- Reduced network usage
- Less JavaScript parsing at startup

**Interview Line**

Lazy loading with dynamic import loads JavaScript only when a feature is required instead of including it in the initial bundle.

### Q. How do bundlers like Webpack, Vite, or Rollup work?

**Answer:**

Bundlers analyze application entry points and their imports to build a dependency graph.

They then process the required files and generate optimized output for the browser.

A typical flow is:

```text
Entry file
↓
Read imports
↓
Build dependency graph
↓
Transform code
↓
Optimize
↓
Generate bundles/chunks
```

Bundlers can perform tasks such as:

- Module resolution
- TypeScript or JSX transformation
- Tree shaking
- Code splitting
- Minification
- Asset processing
- Development hot reloading

Different tools use different architectures, but the general concept is similar.

**Interview Line**

Bundlers start from entry points, build a dependency graph, transform dependencies, and produce optimized browser-ready bundles or chunks.

### Q. What is code splitting?

**Answer:**

Code splitting divides application JavaScript into smaller files that can be loaded independently.

Instead of sending the entire application at startup, the browser can load only the code required for the current route or feature.

**Example:**

```js
const module = await import("./analytics.js");
```

This can create a separate chunk for the analytics module.

Common code-splitting strategies include:

- Route-level splitting
- Component-level splitting
- Feature-level splitting
- Dynamic imports

**Interview Line**

Code splitting reduces initial JavaScript by dividing the application into smaller chunks that can be loaded on demand.

### Q. What is chunking?

**Answer:**

Chunking is the process of grouping modules into separate output files produced by a bundler.

For example:

```text
main.js
vendor.js
dashboard.js
editor.js
```

A chunk may contain:

- Application code
- Third-party dependencies
- Dynamically imported modules
- Shared code

Chunking supports code splitting because different parts of the application can be downloaded independently.

Bundlers usually determine chunk boundaries based on imports and optimization rules.

**Interview Line**

Chunking is the bundler process of grouping modules into separate output files that can be loaded independently.

### Q. What is dependency graph?

**Answer:**

A dependency graph represents the relationship between modules in an application.

The bundler begins from an entry file and follows every import.

**Example:**

```text
main.js
├── app.js
│   ├── api.js
│   └── utils.js
└── analytics.js
```

If `main.js` imports `app.js`, and `app.js` imports `api.js`, these relationships form the graph.

Bundlers use the dependency graph to determine:

- Which files are required
- Which modules are unused
- Which code can be split
- Which modules can share chunks

**Interview Line**

A dependency graph maps how modules import one another and allows bundlers to understand the complete application structure.

### Q. What is circular dependency?

**Answer:**

A circular dependency happens when modules depend on each other in a cycle.

**Example:**

```text
A imports B
B imports C
C imports A
```

A simpler example:

```js
// a.js
import { b } from "./b.js";

// b.js
import { a } from "./a.js";
```

Circular dependencies can cause:

- Partially initialized values
- Unexpected `undefined`
- Difficult debugging
- Tight coupling

Some module systems can technically handle certain cycles, but they often indicate an architectural issue.

**Interview Line**

A circular dependency occurs when modules depend on each other directly or indirectly, creating a dependency cycle.

### Q. How do you handle circular dependencies?

**Answer:**

The best approach is usually to restructure the code so the modules no longer depend on each other.

Common solutions include:

1. Move shared logic to a third module.
2. Extract shared types or constants.
3. Introduce dependency injection.
4. Move responsibilities to a higher-level module.
5. Reduce tightly coupled imports.

**Example:**

Instead of:

```text
userService → authService
authService → userService
```

extract shared functionality:

```text
userService ─┐
             ├→ sharedAuthUtils
authService ─┘
```

Dynamic imports can sometimes break evaluation timing, but they should not be used to hide poor architecture.

**Interview Line**

Circular dependencies are best solved by refactoring shared responsibilities into independent modules and reducing tight coupling.

### Q. What is side effect in module bundling?

**Answer:**

A side effect is code that changes something outside the value it exports when the module is executed.

**Example:**

```js
console.log("Module loaded");
```

Another example:

```js
window.appVersion = "1.0";
```

Or:

```js
import "./global.css";
```

These operations have effects simply by importing the module.

Bundlers must be careful not to remove modules with side effects during tree shaking.

A pure module normally exports values without changing external state during import.

**Interview Line**

A module side effect is any behavior that happens when the module executes beyond simply defining and exporting values.

### Q. Why is `"sideEffects": false` used in package.json?

**Answer:**

`"sideEffects": false` tells compatible bundlers that modules in the package do not have import-time side effects.

**Example:**

```json
{
  "sideEffects": false
}
```

This allows the bundler to remove unused modules more aggressively during tree shaking.

Suppose:

```js
export { add } from "./add.js";
export { subtract } from "./subtract.js";
```

If only `add` is used, the unused module can potentially be removed.

However, this flag must be accurate.

If files such as global CSS or initialization scripts have side effects, they may need to be listed explicitly.

**Example:**

```json
{
  "sideEffects": ["*.css", "./src/setup.js"]
}
```

**Interview Line**

`"sideEffects": false` tells bundlers that unused modules can be safely removed because importing them does not perform external work.

## Browser Rendering

### Q. How does browser rendering work?

**Answer:**

When the browser receives HTML, CSS, and JavaScript, it performs several steps before pixels appear on the screen.

A simplified flow is:

```text
HTML
↓
DOM

CSS
↓
CSSOM

DOM + CSSOM
↓
Render Tree
↓
Layout
↓
Paint
↓
Composite
```

JavaScript can affect this process by changing DOM elements or styles.

If JavaScript performs too much work on the main thread, rendering can be delayed.

**Interview Line**

Browser rendering builds the DOM and CSSOM, creates a render tree, calculates layout, paints pixels, and composites layers onto the screen.

### Q. What is Critical Rendering Path?

**Answer:**

The Critical Rendering Path is the sequence of steps the browser must complete to render the initial visible page.

It includes:

- Parsing HTML
- Building DOM
- Loading and parsing CSS
- Building CSSOM
- Creating render tree
- Calculating layout
- Painting
- Compositing

Render-blocking resources can delay this process.

Examples include:

- Large CSS files
- Blocking JavaScript
- Slow fonts
- Large initial resources

Optimizing the critical rendering path improves how quickly useful content appears.

**Interview Line**

The Critical Rendering Path is the set of browser steps required to turn HTML, CSS, and JavaScript into the first visible pixels.

### Q. What is DOM tree?

**Answer:**

The DOM tree is the browser's object representation of the HTML document.

HTML:

```html
<body>
  <main>
    <h1>Hello</h1>
  </main>
</body>
```

Conceptually becomes:

```text
body
└── main
    └── h1
        └── "Hello"
```

JavaScript interacts with this structure through DOM APIs.

**Example:**

```js
const heading = document.querySelector("h1");

heading.textContent = "Welcome";
```

Changing the DOM can trigger rendering work depending on what changed.

**Interview Line**

The DOM tree is the browser's in-memory tree representation of HTML elements and their relationships.

### Q. What is CSSOM tree?

**Answer:**

CSSOM stands for **CSS Object Model**.

It is the browser's representation of parsed CSS rules.

**Example:**

```css
h1 {
  color: red;
  font-size: 32px;
}
```

The browser parses these rules and determines which styles apply to which DOM elements.

The DOM and CSSOM are combined to create the render tree.

CSS is usually considered render-blocking because the browser needs styles before it can accurately render the page.

**Interview Line**

The CSSOM is the browser's object representation of CSS rules and is combined with the DOM to determine how elements should render.

### Q. What is render tree?

**Answer:**

The render tree represents the visible elements that need to be rendered and their computed styles.

It is created by combining information from:

```text
DOM + CSSOM
```

Not every DOM node appears in the render tree.

For example:

```css
.hidden {
  display: none;
}
```

An element with `display: none` does not participate in layout and therefore is not represented as a visible render object.

The render tree is then used for layout calculations.

**Interview Line**

The render tree combines visible DOM elements with computed CSS styles and is used by the browser for layout and painting.

### Q. Difference between layout, paint, and composite

**Answer:**

These are different stages of browser rendering.

#### Layout

The browser calculates element size and position.

```text
width
height
top
left
```

#### Paint

The browser determines how pixels should look.

Examples:

```text
color
background
border
shadow
text
```

#### Composite

The browser combines painted layers and places them on the screen.

Comparison:

| Stage     | Purpose                |
| --------- | ---------------------- |
| Layout    | Calculate geometry     |
| Paint     | Draw visual appearance |
| Composite | Combine layers         |

Some animations can avoid layout and paint and require only compositing.

**Interview Line**

Layout calculates geometry, paint draws visual pixels, and composite combines layers into the final screen output.

### Q. What is reflow?

**Answer:**

Reflow is another term commonly used for layout recalculation.

It happens when changes affect element size or position.

Examples include:

```js
element.style.width = "500px";
```

or:

```js
element.classList.add("expanded");
```

if the class changes dimensions.

Reflow may affect surrounding elements because changing one element's geometry can change the layout of others.

Typical triggers include:

- Width or height changes
- Font changes
- DOM insertion/removal
- Margin or padding changes
- Window resize

**Interview Line**

Reflow is the recalculation of element sizes and positions after a layout-affecting change.

### Q. What is repaint?

**Answer:**

Repaint occurs when the visual appearance of an element changes but the browser does not necessarily need to recalculate layout.

**Example:**

```js
element.style.color = "red";
```

Other examples include:

```text
background color
visibility
box shadow
outline
```

Repaint is usually cheaper than reflow because geometry may remain unchanged.

However, frequent repainting can still be expensive for large or complex areas.

**Interview Line**

Repaint redraws visual appearance without necessarily recalculating element layout.

### Q. What causes forced synchronous layout?

**Answer:**

Forced synchronous layout happens when JavaScript changes the DOM and then immediately requests layout information.

The browser must calculate layout immediately before returning the requested value.

**Example:**

```js
element.style.width = "500px";

console.log(element.offsetWidth);
```

The style write invalidates layout.

Then reading:

```js
offsetWidth;
```

forces the browser to update layout synchronously.

Other layout-reading APIs include:

```js
offsetHeight;
getBoundingClientRect();
clientWidth;
scrollTop;
```

Repeated read/write patterns can create layout thrashing.

**Interview Line**

Forced synchronous layout occurs when JavaScript writes layout-affecting styles and immediately reads geometry, forcing the browser to calculate layout on demand.

### Q. How do you optimize rendering performance?

**Answer:**

Rendering performance can be improved by reducing unnecessary work on the main thread.

Common techniques include:

- Batch DOM reads and writes
- Avoid layout thrashing
- Reduce unnecessary DOM nodes
- Use `requestAnimationFrame()` for visual updates
- Animate `transform` and `opacity`
- Use virtualized lists for large datasets
- Avoid expensive scroll handlers
- Use passive listeners where appropriate
- Reduce large synchronous JavaScript tasks

**Example:**

Instead of repeatedly reading and writing:

```js
const width = element.offsetWidth;
element.style.width = `${width + 10}px`;
```

for many elements, collect measurements first and then apply writes.

**Interview Line**

Rendering performance improves when DOM work is minimized, layout reads and writes are batched, and animations stay on compositor-friendly properties.

### Q. Why should animations use `transform` and `opacity`?

**Answer:**

Animations using `transform` and `opacity` can often be handled during the compositing stage.

This means they may avoid expensive layout and paint work.

**Example:**

Preferred:

```css
.box {
  transform: translateX(100px);
  opacity: 0.5;
}
```

Less efficient for animation:

```css
.box {
  left: 100px;
  width: 500px;
}
```

Animating `left`, `width`, or `height` may trigger repeated layout recalculations.

Using `transform` is generally smoother for movement and scaling.

**Interview Line**

`transform` and `opacity` are preferred for animations because browsers can often update them at the compositor layer without triggering layout.

### Q. What is GPU acceleration?

**Answer:**

GPU acceleration means using the graphics processor to perform rendering work that is well suited to parallel graphical operations.

Browsers may use the GPU for:

- Layer compositing
- Transforms
- Opacity changes
- Video
- Canvas/WebGL rendering

GPU acceleration can improve animation smoothness because some visual operations avoid main-thread layout work.

However, forcing too many layers can increase memory usage.

So techniques such as:

```css
will-change: transform;
```

should be used only when necessary.

**Interview Line**

GPU acceleration allows the browser to offload suitable graphics and compositing work from the CPU, improving rendering and animation performance.

### Q. What is layout thrashing?

**Answer:**

Layout thrashing happens when code repeatedly alternates between layout reads and DOM writes.

**Bad Example:**

```js
items.forEach((item) => {
  const height = item.offsetHeight;

  item.style.height = `${height + 10}px`;
});
```

Each iteration may:

```text
read layout
↓
write style
↓
read layout again
↓
recalculate
```

This can cause many forced synchronous layouts.

The better approach is:

1. Read all measurements.
2. Then perform all writes.

**Interview Line**

Layout thrashing is repeated layout invalidation caused by alternating DOM reads and writes, leading to unnecessary reflow work.

## Web APIs

### Q. What is Fetch API?

**Answer:**

The Fetch API is a modern browser API for making HTTP requests.

It returns a Promise.

**Example:**

```js
async function getUsers() {
  const response = await fetch("/api/users");

  if (!response.ok) {
    throw new Error(`Request failed: ${response.status}`);
  }

  return response.json();
}
```

Fetch supports:

- GET
- POST
- PUT
- DELETE
- Headers
- Request bodies
- Abort signals
- Credentials

**Interview Line**

The Fetch API is a Promise-based browser API for making HTTP requests and handling responses.

### Q. Difference between Fetch and XMLHttpRequest

**Answer:**

Both can make HTTP requests, but Fetch provides a more modern Promise-based API.

Comparison:

| Fetch                                          | XMLHttpRequest                  |
| ---------------------------------------------- | ------------------------------- |
| Promise-based                                  | Event/callback-based            |
| Cleaner syntax                                 | More verbose                    |
| Works naturally with `async/await`             | Uses events like `onload`       |
| Supports `AbortController`                     | Uses `abort()` directly         |
| HTTP errors require manual `response.ok` check | Status handled manually as well |

**Example:**

Fetch:

```js
const response = await fetch("/api/users");
```

XHR:

```js
const xhr = new XMLHttpRequest();

xhr.open("GET", "/api/users");

xhr.send();
```

XHR still exists for legacy scenarios, but Fetch is usually preferred in modern applications.

**Interview Line**

Fetch is a modern Promise-based replacement for most XMLHttpRequest use cases and works naturally with `async/await`.

### Q. How do you handle errors in Fetch API?

**Answer:**

Fetch can fail in two broad ways:

1. Network-level failure
2. HTTP error response

Network failures reject the Promise.

HTTP errors such as `404` or `500` normally still resolve with a `Response`.

**Example:**

```js
async function getData() {
  try {
    const response = await fetch("/api/data");

    if (!response.ok) {
      throw new Error(`HTTP ${response.status}`);
    }

    return await response.json();
  } catch (error) {
    console.error("Request failed", error);

    throw error;
  }
}
```

Always check:

```js
response.ok;
```

when HTTP status matters.

**Interview Line**

Handle Fetch errors with `try...catch` for network failures and manually check `response.ok` for HTTP error responses.

### Q. Why does fetch not reject on HTTP 404?

**Answer:**

Fetch treats HTTP responses and network failures differently.

A `404` is still a valid HTTP response successfully received from the server.

Therefore:

```js
fetch("/missing");
```

resolves with a `Response` object.

The response may contain:

```js
response.status === 404;
response.ok === false;
```

Fetch rejects mainly when the request cannot be completed at the network level, such as:

- DNS failure
- Connection failure
- Request aborted
- Some network errors

**Interview Line**

Fetch does not reject on `404` because the HTTP exchange succeeded; application code must inspect the status using `response.ok` or `response.status`.

### Q. What is AbortController?

**Answer:**

`AbortController` provides a way to cancel supported asynchronous operations such as Fetch requests.

**Example:**

```js
const controller = new AbortController();

fetch("/api/users", {
  signal: controller.signal,
});

controller.abort();
```

A common use case is canceling stale requests.

**Example:**

```js
let controller;

async function search(query) {
  controller?.abort();

  controller = new AbortController();

  return fetch(`/api/search?q=${query}`, {
    signal: controller.signal,
  });
}
```

**Interview Line**

`AbortController` creates an abort signal that can cancel Fetch requests and other abortable browser operations.

### Q. What is FormData?

**Answer:**

`FormData` represents form fields as key-value pairs and is especially useful for multipart form submissions.

**Example:**

```js
const formData = new FormData();

formData.append("name", "John");

formData.append("avatar", fileInput.files[0]);
```

Then:

```js
await fetch("/api/profile", {
  method: "POST",
  body: formData,
});
```

When using `FormData`, the browser automatically creates the appropriate multipart boundary.

It is useful for:

- File uploads
- Forms
- Mixed text and binary data

**Interview Line**

`FormData` is a browser API for representing form fields and files in a format suitable for multipart HTTP requests.

### Q. What is URLSearchParams?

**Answer:**

`URLSearchParams` provides methods for reading and creating URL query parameters.

**Example:**

```js
const params = new URLSearchParams();

params.set("page", "2");
params.set("sort", "name");

console.log(params.toString());
```

Output:

```text
page=2&sort=name
```

Reading:

```js
const params = new URLSearchParams(window.location.search);

console.log(params.get("page"));
```

It handles encoding automatically and is safer than manually concatenating query strings.

**Interview Line**

`URLSearchParams` provides a structured API for creating, reading, and modifying URL query parameters.

### Q. What is Blob?

**Answer:**

A `Blob` represents immutable binary or text data in the browser.

Blob stands for **Binary Large Object**.

**Example:**

```js
const blob = new Blob(["Hello World"], {
  type: "text/plain",
});
```

A Blob can be converted into an object URL:

```js
const url = URL.createObjectURL(blob);
```

Common use cases include:

- Generated files
- Images
- Downloads
- Binary API responses
- Media processing

**Interview Line**

A Blob is an immutable browser object representing raw binary or text data.

### Q. What is File API?

**Answer:**

The File API allows browser JavaScript to work with files selected by the user.

A `File` extends `Blob` and includes metadata such as:

- File name
- Size
- MIME type
- Last modified time

**Example:**

```js
const file = input.files[0];

console.log(file.name);
console.log(file.size);
console.log(file.type);
```

The file can be read using methods such as:

```js
await file.text();
await file.arrayBuffer();
```

or through `FileReader` in older patterns.

**Interview Line**

The File API allows JavaScript to access metadata and contents of user-selected files without directly accessing the user's filesystem.

### Q. What is Clipboard API?

**Answer:**

The Clipboard API allows web applications to read from or write to the system clipboard, subject to browser permissions and security restrictions.

**Example:**

```js
await navigator.clipboard.writeText("Hello");
```

Reading:

```js
const text = await navigator.clipboard.readText();
```

Clipboard access usually requires:

- Secure context
- User interaction
- Browser permission

Common use cases include:

- Copy buttons
- Paste workflows
- Code snippets
- Sharing links

**Interview Line**

The Clipboard API allows secure programmatic copy and paste operations through `navigator.clipboard`.

### Q. What is Geolocation API?

**Answer:**

The Geolocation API allows a website to request the user's geographical location.

**Example:**

```js
navigator.geolocation.getCurrentPosition(
  (position) => {
    console.log(position.coords.latitude);

    console.log(position.coords.longitude);
  },
  (error) => {
    console.error(error);
  },
);
```

The browser asks the user for permission before sharing location.

Geolocation is commonly used for:

- Nearby stores
- Maps
- Local content
- Delivery location
- Location-based services

**Interview Line**

The Geolocation API allows a browser application to request the user's location after receiving permission.

### Q. What is Notification API?

**Answer:**

The Notification API allows websites to display system notifications outside the page UI.

Permission must be granted first.

**Example:**

```js
const permission = await Notification.requestPermission();

if (permission === "granted") {
  new Notification("New message");
}
```

Notifications are useful for:

- Chat messages
- Alerts
- Reminders
- Background updates

For notifications when the page is not open, Service Workers and push notifications are commonly used.

**Interview Line**

The Notification API allows web applications to display system-level notifications after receiving user permission.

### Q. What is WebSocket?

**Answer:**

WebSocket is a protocol that provides persistent, full-duplex communication between client and server.

After the connection is established, both sides can send messages at any time.

**Example:**

```js
const socket = new WebSocket("wss://example.com/socket");

socket.onmessage = (event) => {
  console.log(event.data);
};

socket.send("Hello");
```

Common use cases include:

- Chat applications
- Live stock prices
- Multiplayer games
- Collaborative editing
- Live dashboards

**Interview Line**

WebSocket provides a persistent two-way connection where both client and server can send messages independently.

### Q. Difference between WebSocket and HTTP

**Answer:**

HTTP is primarily request-response based.

WebSocket creates a persistent bidirectional connection.

Comparison:

| HTTP                                      | WebSocket                  |
| ----------------------------------------- | -------------------------- |
| Request-response                          | Full duplex                |
| Client usually initiates                  | Either side can send       |
| Connection often reused but request-based | Persistent message channel |
| Best for normal APIs                      | Best for real-time updates |

For example, fetching user data is naturally handled with HTTP.

A real-time chat is often better suited to WebSocket.

**Interview Line**

HTTP is request-response oriented, while WebSocket maintains a persistent full-duplex connection for real-time communication.

### Q. Difference between WebSocket and Server-Sent Events

**Answer:**

WebSocket supports two-way communication.

Server-Sent Events, or SSE, mainly provide one-way communication from server to client.

Comparison:

| WebSocket                              | SSE                                              |
| -------------------------------------- | ------------------------------------------------ |
| Bidirectional                          | Server to client                                 |
| Custom WebSocket protocol              | Uses HTTP                                        |
| Supports binary data                   | Primarily text events                            |
| Good for chat/games                    | Good for feeds/status updates                    |
| Manual reconnection logic often needed | Browser provides automatic reconnection behavior |

SSE is simpler when the client only needs to receive continuous updates.

**Interview Line**

WebSocket supports two-way real-time communication, while SSE is simpler for continuous one-way server-to-client updates.

## Testing JavaScript Code

### Q. Why is testing important in JavaScript applications?

**Answer:**

Testing helps verify that application behavior remains correct as code changes.

Benefits include:

- Preventing regressions
- Improving refactoring confidence
- Documenting expected behavior
- Catching edge cases
- Improving code design
- Reducing manual testing effort

Tests are especially useful in large teams where many developers modify the same codebase.

Testing does not guarantee bug-free software, but it greatly reduces risk.

**Interview Line**

Testing provides confidence that existing and new behavior works correctly and reduces regressions during development and refactoring.

### Q. What is unit testing?

**Answer:**

Unit testing checks a small isolated piece of logic.

Examples include:

- Function
- Utility
- Reducer
- Validation rule
- Small class method

**Example:**

```js
function add(a, b) {
  return a + b;
}
```

Test:

```js
expect(add(2, 3)).toBe(5);
```

Unit tests are usually:

- Fast
- Focused
- Easy to debug

**Interview Line**

Unit testing verifies small isolated units of application logic independently.

### Q. What is integration testing?

**Answer:**

Integration testing verifies that multiple units work correctly together.

For example:

```text
Form component
+
Validation
+
API utility
```

An integration test might submit a form and verify that:

- Validation runs
- API function is called
- Success UI appears

Integration tests provide more confidence than isolated unit tests because they test collaboration between parts of the application.

**Interview Line**

Integration testing verifies that multiple modules or components work correctly together as a combined workflow.

### Q. What is end-to-end testing?

**Answer:**

End-to-end, or E2E, testing verifies complete user workflows through the actual application.

**Example:**

```text
Open login page
↓
Enter credentials
↓
Submit form
↓
Navigate to dashboard
↓
Verify user data
```

E2E tests usually run in a real or simulated browser environment.

They provide strong confidence but are generally:

- Slower
- More expensive
- More sensitive to environment issues

**Interview Line**

End-to-end testing validates complete user flows across the full application, often through a browser.

### Q. Difference between Jest, Vitest, and Cypress

**Answer:**

These tools overlap but are commonly used for different testing needs.

#### Jest

Popular JavaScript test runner traditionally used for unit and integration testing.

#### Vitest

Modern test runner designed to work especially well with Vite-based projects.

It has a Jest-like API and fast development feedback.

#### Cypress

Primarily focused on browser-based integration and end-to-end testing.

Comparison:

| Tool    | Common Use                               |
| ------- | ---------------------------------------- |
| Jest    | Unit/integration                         |
| Vitest  | Unit/integration in modern Vite projects |
| Cypress | Browser/E2E testing                      |

**Interview Line**

Jest and Vitest are commonly used for unit and integration tests, while Cypress focuses strongly on browser and end-to-end workflows.

### Q. What is mocking?

**Answer:**

Mocking replaces a real dependency with a controlled test version.

**Example:**

Suppose a function calls:

```js
api.getUser();
```

In a unit test, we may replace the API dependency with:

```js
const api = {
  getUser: vi.fn().mockResolvedValue({
    id: 1,
    name: "John",
  }),
};
```

Mocking is useful for:

- APIs
- Databases
- Browser APIs
- Expensive services
- External dependencies

**Interview Line**

Mocking replaces real dependencies with controlled test implementations so behavior can be tested predictably.

### Q. What is spying?

**Answer:**

A spy observes how a function is used.

It can track:

- Number of calls
- Arguments
- Return behavior
- Invocation order

**Example:**

```js
const spy = vi.spyOn(console, "log");

console.log("Hello");

expect(spy).toHaveBeenCalledWith("Hello");
```

Unlike a full mock, a spy may allow the original implementation to continue running.

**Interview Line**

A spy observes function calls and arguments while optionally preserving the original implementation.

### Q. What is stubbing?

**Answer:**

A stub replaces a dependency with a predefined implementation or response.

For example, instead of making a real network request:

```js
getUser();
```

a test may return:

```js
{
  id: 1,
  name: "John",
}
```

immediately.

Stubs are useful when a test needs predictable behavior without depending on external systems.

In modern testing libraries, the terms mock and stub often overlap in practical usage.

**Interview Line**

A stub replaces real behavior with a controlled predefined response to make testing predictable.

### Q. How do you test async code?

**Answer:**

Async tests should wait for the asynchronous operation to finish before making assertions.

**Example:**

```js
async function getValue() {
  return 10;
}
```

Test:

```js
test("returns 10", async () => {
  const result = await getValue();

  expect(result).toBe(10);
});
```

Promise-based assertions can also be used.

**Example:**

```js
await expect(getValue()).resolves.toBe(10);
```

The important point is that the test must return or await the Promise.

**Interview Line**

Async tests should `await` the operation or return its Promise so assertions execute after the asynchronous work completes.

### Q. How do you test promise rejection?

**Answer:**

A rejected Promise should be explicitly asserted.

**Example:**

```js
async function getUser() {
  throw new Error("User not found");
}
```

Test:

```js
await expect(getUser()).rejects.toThrow("User not found");
```

Another approach uses `try...catch`, but rejection matchers are usually cleaner.

**Interview Line**

Test rejected Promises using rejection assertions such as `rejects.toThrow()` and always await the assertion.

### Q. How do you test functions with timers?

**Answer:**

Timer-based functions can be difficult to test using real time because tests become slow and unreliable.

Fake timers allow the test to control time manually.

**Example:**

```js
setTimeout(() => {
  callback();
}, 1000);
```

With fake timers:

```js
vi.useFakeTimers();

const callback = vi.fn();

setTimeout(callback, 1000);

vi.advanceTimersByTime(1000);

expect(callback).toHaveBeenCalled();
```

**Interview Line**

Timer-based code is usually tested with fake timers so tests can advance time instantly instead of waiting in real time.

### Q. What are fake timers?

**Answer:**

Fake timers replace browser timer APIs with controllable test implementations.

They can simulate:

```js
setTimeout();
setInterval();
Date;
```

depending on the testing framework.

Benefits include:

- Faster tests
- Deterministic timing
- Easy debounce testing
- Easy retry testing
- No real delays

**Interview Line**

Fake timers let tests control time programmatically, making timer-dependent behavior fast and deterministic.

### Q. How do you test DOM events?

**Answer:**

DOM event tests simulate user interactions and verify resulting behavior.

**Example:**

```js
const button = document.createElement("button");

const handler = vi.fn();

button.addEventListener("click", handler);

button.click();

expect(handler).toHaveBeenCalled();
```

In framework applications, testing libraries usually encourage user-focused interactions such as:

```text
click
type
submit
focus
```

instead of directly testing internal implementation details.

**Interview Line**

DOM event tests simulate real interactions and verify the visible behavior or event-driven side effects that follow.

### Q. What is test coverage?

**Answer:**

Test coverage measures how much application code is executed during tests.

Common metrics include:

- Statements
- Branches
- Functions
- Lines

For example:

```text
Statements: 90%
Branches: 75%
Functions: 85%
Lines: 90%
```

High coverage does not automatically mean good tests.

A test can execute code without verifying meaningful behavior.

Coverage is best used to identify untested areas, not as the only quality metric.

**Interview Line**

Test coverage measures which code paths execute during tests, but high coverage does not guarantee high-quality testing.

### Q. What should not be tested?

**Answer:**

Tests should focus on application behavior rather than implementation details.

Usually avoid testing:

- Third-party library internals
- Framework implementation
- Simple language behavior
- Private implementation details
- Trivial getters with no logic

For example, there is little value in testing whether:

```js
Array.prototype.map();
```

works correctly.

Instead, test how your application uses it.

Tests should provide confidence in code your team owns.

**Interview Line**

Avoid testing framework internals, third-party code, and implementation details; focus on meaningful application behavior.

## Design Patterns in JavaScript

### Q. What are design patterns?

**Answer:**

Design patterns are reusable approaches to common software design problems.

They are not copy-paste code templates.

They provide architectural ideas for organizing responsibilities and communication.

Examples include:

- Factory
- Singleton
- Observer
- Strategy
- Decorator
- Module
- Middleware

Patterns are useful when they make code easier to understand, extend, or maintain.

They should not be applied unnecessarily.

**Interview Line**

Design patterns are reusable design approaches that solve common software architecture and communication problems.

### Q. What is module pattern?

**Answer:**

The module pattern uses closures to hide internal state and expose only selected functionality.

**Example:**

```js
const counter = (() => {
  let count = 0;

  return {
    increment() {
      count++;
    },

    getCount() {
      return count;
    },
  };
})();
```

Usage:

```js
counter.increment();

console.log(counter.getCount());
```

The `count` variable cannot be directly accessed from outside.

Before ES Modules became standard, this pattern was commonly used for encapsulation.

**Interview Line**

The module pattern uses closures to keep implementation details private while exposing a controlled public API.

### Q. What is revealing module pattern?

**Answer:**

The revealing module pattern is a variation where internal functions are defined privately and then selected ones are returned as the public API.

**Example:**

```js
const userModule = (() => {
  function saveUser() {
    console.log("Saved");
  }

  function validateUser() {
    return true;
  }

  return {
    save: saveUser,
    validate: validateUser,
  };
})();
```

The public API clearly reveals which internal functions are exposed.

**Interview Line**

The revealing module pattern defines logic privately and explicitly returns the functions that should form the public API.

### Q. What is singleton pattern?

**Answer:**

The singleton pattern ensures that only one shared instance of an object exists.

**Example:**

```js
class Config {
  constructor() {
    if (Config.instance) {
      return Config.instance;
    }

    this.apiUrl = "/api";

    Config.instance = this;
  }
}

const a = new Config();
const b = new Config();

console.log(a === b);
```

Output:

```js
true;
```

Common use cases include:

- Configuration
- Logging
- Shared client instances
- Global caches

Singletons should be used carefully because global shared state can make testing harder.

**Interview Line**

The singleton pattern ensures that an application uses one shared instance of a particular object or service.

### Q. What is factory pattern?

**Answer:**

The factory pattern creates objects without requiring callers to know the exact construction logic.

**Example:**

```js
function createUser(type, name) {
  if (type === "admin") {
    return {
      name,
      permissions: ["all"],
    };
  }

  return {
    name,
    permissions: ["read"],
  };
}
```

Usage:

```js
const admin = createUser("admin", "John");
```

Factories are useful when object creation varies based on configuration or type.

**Interview Line**

The factory pattern centralizes object creation and returns different object implementations based on input or configuration.

### Q. What is observer pattern?

**Answer:**

The observer pattern creates a relationship where one object notifies registered observers when its state changes.

**Example:**

```js
class Store {
  listeners = [];

  subscribe(listener) {
    this.listeners.push(listener);
  }

  notify(data) {
    this.listeners.forEach((listener) => listener(data));
  }
}
```

This pattern appears in:

- State management
- Event systems
- UI updates
- Reactive libraries

Observers are usually directly associated with the subject they observe.

**Interview Line**

The observer pattern lets dependent observers subscribe directly to a subject and receive updates when its state changes.

### Q. What is pub-sub pattern?

**Answer:**

Pub-sub stands for publish-subscribe.

Publishers send events to a central event system without knowing which subscribers receive them.

**Example:**

```js
eventBus.subscribe("user:updated", handleUserUpdate);

eventBus.publish("user:updated", user);
```

The publisher and subscriber do not need direct references to each other.

This reduces coupling.

Common use cases include:

- Event buses
- Analytics
- Cross-module communication
- Plugin architectures

**Interview Line**

Pub-sub decouples publishers and subscribers through an intermediate event channel or event bus.

### Q. Difference between observer and pub-sub pattern

**Answer:**

Both patterns provide event-driven communication, but their relationships differ.

In observer:

```text
Subject
↓
Observers
```

Observers register directly with the subject.

In pub-sub:

```text
Publisher
↓
Event Bus
↓
Subscribers
```

Publisher and subscribers do not know each other directly.

Comparison:

| Observer                             | Pub-Sub                         |
| ------------------------------------ | ------------------------------- |
| Direct subject-observer relationship | Uses intermediary               |
| Tighter coupling                     | More decoupled                  |
| Subject manages observers            | Event bus manages subscriptions |

**Interview Line**

Observer connects subscribers directly to a subject, while pub-sub uses an intermediary event channel to decouple publishers and subscribers.

### Q. What is strategy pattern?

**Answer:**

The strategy pattern defines multiple interchangeable algorithms behind a common interface.

**Example:**

```js
const paymentStrategies = {
  card(amount) {
    return `Card: ${amount}`;
  },

  upi(amount) {
    return `UPI: ${amount}`;
  },
};

function pay(strategy, amount) {
  return strategy(amount);
}

pay(paymentStrategies.upi, 500);
```

The caller chooses the strategy without changing the surrounding workflow.

Common frontend examples include:

- Validation rules
- Sorting
- Payment options
- Formatting
- Different API strategies

**Interview Line**

The strategy pattern allows interchangeable algorithms or behaviors to be selected at runtime through a common interface.

### Q. What is decorator pattern?

**Answer:**

The decorator pattern adds behavior to an existing object or function without modifying its core implementation.

**Example:**

```js
function withLogging(fn) {
  return function (...args) {
    console.log("Calling function");

    return fn(...args);
  };
}
```

Usage:

```js
const add = withLogging((a, b) => a + b);

add(2, 3);
```

Common uses include:

- Logging
- Authorization
- Caching
- Analytics
- Retry logic

**Interview Line**

The decorator pattern wraps existing behavior to add additional functionality without changing the original implementation.

### Q. What is middleware pattern?

**Answer:**

Middleware is a pattern where a request or operation passes through a chain of functions.

Each middleware can:

- Read data
- Modify data
- Stop processing
- Continue to the next middleware

**Example:**

```text
Request
↓
Authentication
↓
Logging
↓
Validation
↓
Handler
```

Conceptually:

```js
function middleware(context, next) {
  console.log("Before");

  next();

  console.log("After");
}
```

This pattern is common in:

- Express
- Redux middleware
- API clients
- Authentication pipelines

**Interview Line**

Middleware creates a processing pipeline where each function can inspect, modify, stop, or forward an operation.

### Q. Where have you used design patterns in frontend applications?

**Answer:**

Frontend applications use design patterns frequently even when developers do not explicitly name them.

Examples include:

- Module pattern for encapsulated utilities
- Observer pattern in state subscriptions
- Pub-sub for application events
- Strategy for validation or formatting
- Factory for creating configured components or services
- Decorator for logging and authorization wrappers
- Middleware for API clients and state management

**Example:**

An Axios interceptor behaves similarly to middleware:

```text
Request
↓
Add auth header
↓
Log request
↓
Send API call
```

The important interview point is to explain where a pattern solved a real problem rather than only defining the pattern.

**Interview Line**

Design patterns appear naturally in frontend architecture through state subscriptions, API middleware, configurable strategies, factories, and reusable wrappers.

## API Handling & Real Project Scenarios

### Q. How do you handle API loading, success, and error states?

**Answer:**

A reliable UI should explicitly represent the main request states.

Typical states are:

```text
idle
loading
success
error
```

**Example:**

```js
let state = {
  status: "idle",
  data: null,
  error: null,
};
```

During loading:

```js
state.status = "loading";
```

After success:

```js
state = {
  status: "success",
  data,
  error: null,
};
```

After failure:

```js
state = {
  status: "error",
  data: null,
  error,
};
```

UI should display appropriate loaders, content, retry actions, and error messages.

**Interview Line**

API state should explicitly model loading, success, and error so the UI always reflects the current request lifecycle.

### Q. How do you prevent duplicate API calls?

**Answer:**

Duplicate API calls can be prevented at multiple levels.

Common techniques include:

- Cache previous results
- Deduplicate in-flight requests
- Disable repeated button submission
- Debounce user input
- Use request libraries with query deduplication
- Track active requests by key

**Example:**

```js
const pending = new Map();

function getUser(id) {
  if (pending.has(id)) {
    return pending.get(id);
  }

  const request = fetch(`/api/users/${id}`).finally(() => {
    pending.delete(id);
  });

  pending.set(id, request);

  return request;
}
```

**Interview Line**

Prevent duplicate calls using caching, in-flight request deduplication, debounce, and UI controls that block repeated submissions.

### Q. How do you retry failed API requests?

**Answer:**

Retries should normally be used only for transient failures.

Examples include:

- Temporary network errors
- Selected `5xx` responses
- Rate limits with proper delay

Avoid retrying permanent failures such as:

```text
400 Bad Request
401 Unauthorized
403 Forbidden
```

without correcting the underlying problem.

**Example:**

```js
async function retry(fn, attempts = 3) {
  let lastError;

  for (let i = 0; i < attempts; i++) {
    try {
      return await fn();
    } catch (error) {
      lastError = error;
    }
  }

  throw lastError;
}
```

Production implementations often use exponential backoff.

**Interview Line**

Retry only transient API failures, limit the number of attempts, and preferably use backoff between retries.

### Q. How do you cancel stale API requests?

**Answer:**

`AbortController` can cancel old Fetch requests when a newer request makes the previous response irrelevant.

**Example:**

```js
let controller;

async function search(query) {
  controller?.abort();

  controller = new AbortController();

  const response = await fetch(`/api/search?q=${query}`, {
    signal: controller.signal,
  });

  return response.json();
}
```

This is especially useful for:

- Search
- Route changes
- Autocomplete
- Filters

**Interview Line**

Cancel stale requests with `AbortController` so outdated responses do not consume resources or update newer UI state.

### Q. How do you handle race conditions in API calls?

**Answer:**

A race condition happens when multiple requests run concurrently and an older request finishes after a newer request.

**Example:**

```text
Search "a" starts
Search "ab" starts
"ab" finishes first
"a" finishes later
```

Without protection, the UI may show results for `"a"`.

Solutions include:

- Abort previous requests
- Track request IDs
- Compare current query before updating state
- Use query libraries that handle stale responses

**Example:**

```js
let requestId = 0;

async function search(query) {
  const id = ++requestId;

  const data = await fetchData(query);

  if (id !== requestId) {
    return;
  }

  render(data);
}
```

**Interview Line**

Prevent API race conditions by canceling stale requests or ignoring responses that no longer belong to the latest request.

### Q. How do you debounce search API calls?

**Answer:**

Debouncing delays the request until the user stops typing for a short period.

**Example:**

```js
function debounce(fn, delay) {
  let timer;

  return (...args) => {
    clearTimeout(timer);

    timer = setTimeout(() => fn(...args), delay);
  };
}
```

Usage:

```js
const search = debounce(fetchSearchResults, 400);
```

This avoids sending an API request for every keystroke.

Combining debounce with `AbortController` provides even stronger protection against stale requests.

**Interview Line**

Debounce search input so requests are sent only after the user pauses typing, reducing unnecessary API traffic.

### Q. How do you handle pagination?

**Answer:**

Pagination loads data in smaller sections rather than requesting the entire dataset.

Common approaches include:

- Page numbers
- Offset/limit
- Cursor-based pagination
- Infinite scroll

**Example:**

```http
GET /users?page=2&limit=20
```

The frontend should usually track:

```text
current page
page size
loading state
total pages or next cursor
```

Pagination reduces:

- Response size
- Memory usage
- Rendering work
- Server load

**Interview Line**

Pagination divides large datasets into smaller requests and requires tracking page, cursor, loading, and whether more data exists.

### Q. Difference between offset-based and cursor-based pagination

**Answer:**

Offset pagination identifies records by position.

**Example:**

```http
GET /users?offset=40&limit=20
```

Cursor pagination uses a stable reference to the last received item.

**Example:**

```http
GET /users?after=abc123&limit=20
```

Comparison:

| Offset                           | Cursor                         |
| -------------------------------- | ------------------------------ |
| Easy to implement                | More scalable                  |
| Supports page numbers            | Usually sequential             |
| Can become slow at large offsets | Efficient for large datasets   |
| Data changes can shift results   | More stable with changing data |

**Interview Line**

Offset pagination uses record position, while cursor pagination uses a stable continuation token and is usually better for large or frequently changing datasets.

### Q. How do you cache API responses?

**Answer:**

API responses can be cached at different layers.

Frontend options include:

- In-memory `Map`
- Query libraries
- Service Worker
- IndexedDB
- Browser HTTP cache

**Example:**

```js
const cache = new Map();

async function getUser(id) {
  if (cache.has(id)) {
    return cache.get(id);
  }

  const response = await fetch(`/api/users/${id}`);

  const user = await response.json();

  cache.set(id, user);

  return user;
}
```

Caching needs a strategy for:

- Expiration
- Invalidation
- Stale data
- Refetching

**Interview Line**

API caching stores reusable responses to reduce repeated requests, but it must define expiration and invalidation rules.

### Q. How do you handle token expiration?

**Answer:**

When an access token expires, the application should avoid blindly retrying the same request.

A common flow is:

```text
API returns 401
↓
Attempt token refresh
↓
Receive new access token
↓
Retry original request
```

If refresh fails:

```text
Clear authentication
↓
Redirect to login
```

Multiple requests failing at the same time should usually share one refresh operation instead of starting many refresh calls.

**Interview Line**

Handle token expiration by refreshing credentials once, retrying eligible requests, and logging the user out if refresh fails.

### Q. How do you refresh access tokens?

**Answer:**

A short-lived access token can be renewed using a longer-lived refresh credential.

A secure browser design commonly stores the refresh credential in an `HttpOnly` cookie.

**Flow:**

```text
Access token expired
↓
POST /auth/refresh
↓
Server validates refresh credential
↓
New access token issued
```

The client then retries the original API request.

Refresh logic should prevent infinite retry loops.

**Interview Line**

Access tokens are refreshed by securely exchanging a valid refresh credential for a new short-lived access token.

### Q. How do you handle 401 and 403 errors?

**Answer:**

`401` and `403` have different meanings.

#### 401 Unauthorized

Usually means authentication is missing, invalid, or expired.

Possible actions:

- Refresh token
- Re-authenticate
- Redirect to login

#### 403 Forbidden

Usually means the user is authenticated but does not have permission.

Possible actions:

- Show access-denied UI
- Disable restricted actions
- Do not keep retrying authentication

**Interview Line**

`401` usually means authentication is required or invalid, while `403` means the authenticated user lacks permission.

### Q. How do you handle network failure gracefully?

**Answer:**

Network failures should produce a recoverable user experience.

Useful strategies include:

- Show clear error state
- Provide retry button
- Preserve unsaved user input
- Retry transient failures
- Detect offline state
- Use cached data when available
- Avoid blank screens

**Example:**

```js
try {
  const data = await loadData();

  render(data);
} catch {
  showError("Unable to connect. Try again.");
}
```

For important forms, preserving draft state is especially valuable.

**Interview Line**

Graceful network failure handling provides retry, fallback UI, preserved state, and cached data instead of leaving the user with a broken screen.

### Q. How do you design a reusable API utility function?

**Answer:**

A reusable API utility should centralize repeated request behavior.

Common responsibilities include:

- Base URL
- Headers
- JSON parsing
- Error normalization
- Authentication
- Abort signals
- Timeouts
- Retry policies

**Example:**

```js
async function apiRequest(url, options = {}) {
  const response = await fetch(`/api${url}`, {
    ...options,
    headers: {
      "Content-Type": "application/json",
      ...options.headers,
    },
  });

  if (!response.ok) {
    throw new Error(`HTTP ${response.status}`);
  }

  return response.json();
}
```

Avoid making one utility responsible for every possible business rule.

**Interview Line**

A reusable API utility centralizes transport-level concerns such as base URL, headers, parsing, and standardized error handling.

## Real Project JavaScript Questions

### Q. How do you structure JavaScript code in a large project?

**Answer:**

Large projects should be organized around clear responsibilities rather than putting all code into generic folders.

A common structure is:

```text
features/
components/
services/
hooks/
utils/
types/
config/
```

In feature-based architecture:

```text
features/
  auth/
  products/
  orders/
```

each feature can contain its own:

```text
components
services
types
tests
```

The main goal is predictable ownership and low coupling.

**Interview Line**

Large JavaScript projects should use clear module boundaries, feature ownership, and separation between UI, services, utilities, and shared infrastructure.

### Q. How do you avoid global variables?

**Answer:**

Global variables create hidden dependencies and can be accidentally modified from anywhere.

Better options include:

- ES Modules
- Function scope
- Closures
- Classes
- Dependency injection
- State management
- Configuration modules

Instead of:

```js
window.currentUser = user;
```

prefer:

```js
export const userStore = createUserStore();
```

or pass dependencies explicitly.

**Interview Line**

Avoid global variables by keeping state inside modules, closures, scoped objects, or explicit dependency containers.

### Q. How do you manage shared utility functions?

**Answer:**

Shared utilities should contain generic logic that is reusable across features.

Examples include:

- Date formatting
- String formatting
- Validation helpers
- URL builders
- Number formatting

A utility should not silently depend on feature-specific global state.

**Example:**

Good:

```js
export function formatCurrency(value, currency) {
  // ...
}
```

Less reusable:

```js
export function formatPrice() {
  return currentUser.currency;
}
```

Utilities should be small, predictable, and testable.

**Interview Line**

Shared utilities should contain generic, stateless, well-tested logic without hidden feature-specific dependencies.

### Q. How do you write reusable JavaScript functions?

**Answer:**

Reusable functions should have:

- Clear inputs
- Predictable outputs
- Minimal side effects
- Single responsibility
- Configurable behavior where needed

**Example:**

Instead of:

```js
function formatUserPrice() {
  // reads globals
}
```

prefer:

```js
function formatPrice(amount, currency) {
  return new Intl.NumberFormat("en", {
    style: "currency",
    currency,
  }).format(amount);
}
```

This function can be reused anywhere because it depends only on its arguments.

**Interview Line**

Reusable functions have clear inputs and outputs, limited side effects, and avoid depending on hidden external state.

### Q. How do you improve code readability?

**Answer:**

Readable code is easier to maintain and review.

Important practices include:

- Clear names
- Small focused functions
- Consistent formatting
- Avoid deeply nested logic
- Early returns
- Meaningful abstractions
- Avoid unnecessary cleverness
- Comments for why, not obvious what

**Example:**

Instead of:

```js
if (user) {
  if (user.active) {
    // logic
  }
}
```

use:

```js
if (!user) return;
if (!user.active) return;

// logic
```

where appropriate.

**Interview Line**

Code readability improves through clear naming, small functions, shallow control flow, consistent conventions, and simple abstractions.

### Q. How do you debug JavaScript issues in production?

**Answer:**

Production debugging requires observability because developers usually cannot reproduce the user's exact environment immediately.

Useful tools include:

- Error monitoring
- Source maps
- Structured logs
- Network tracing
- Performance monitoring
- Application version tracking
- Browser/environment metadata

Important error information includes:

```text
message
stack trace
route
browser
app version
user action
request ID
```

Avoid logging sensitive information.

**Interview Line**

Production debugging relies on source maps, structured logs, error monitoring, request context, and reproducible metadata rather than console debugging alone.

### Q. How do you handle browser compatibility issues?

**Answer:**

Compatibility should be handled based on the browsers the product officially supports.

Common techniques include:

- Feature detection
- Polyfills
- Transpilation
- Progressive enhancement
- Graceful fallback
- Compatibility testing

**Example:**

```js
if ("IntersectionObserver" in window) {
  // use modern API
} else {
  // fallback
}
```

Avoid browser detection based only on user-agent strings when capability detection is enough.

**Interview Line**

Handle browser compatibility through supported-browser targets, feature detection, transpilation, polyfills, and graceful fallbacks.

### Q. How do you decide between using library code and writing custom code?

**Answer:**

The decision depends on complexity, maintenance cost, security, and project requirements.

Use a library when:

- The problem is complex
- Edge cases are numerous
- The package is well maintained
- Reinventing it would be risky

Write custom code when:

- The requirement is small
- The implementation is simple
- A library would add unnecessary bundle size
- The team can maintain it confidently

For example, a small debounce utility may be easy to write.

A date-time library or rich text editor may have many complex edge cases.

**Interview Line**

Choose a library when complexity and maintenance justify it; write custom code when the requirement is small, stable, and easy to own.

### Q. How do you handle third-party script failures?

**Answer:**

Third-party scripts should not be allowed to break critical application functionality.

Strategies include:

- Load non-critical scripts asynchronously
- Add timeout/fallback behavior
- Catch integration errors
- Lazy load optional scripts
- Monitor failures
- Isolate features where possible
- Avoid blocking page rendering

**Example:**

If analytics fails, checkout should still work.

```js
try {
  analytics.track("purchase");
} catch {
  // do not break purchase flow
}
```

For external scripts, CSP and integrity protections may also be relevant.

**Interview Line**

Third-party failures should be isolated so optional integrations cannot break critical user flows.

### Q. How do you prevent memory leaks in a single-page application?

**Answer:**

SPAs keep running for long periods, so cleanup is important.

Common leak sources include:

- Event listeners
- Timers
- WebSocket connections
- Observers
- Subscriptions
- Detached DOM nodes
- Large caches
- Closures retaining objects

Cleanup should happen when components or features are removed.

**Example:**

```js
const handler = () => {};

window.addEventListener("resize", handler);

// later
window.removeEventListener("resize", handler);
```

Memory profiling tools can confirm whether objects remain retained.

**Interview Line**

Prevent SPA memory leaks by cleaning listeners, timers, subscriptions, observers, sockets, and stale object references when features are destroyed.

### Q. How do you optimize JavaScript for low-end devices?

**Answer:**

Low-end devices are more sensitive to CPU, memory, and JavaScript execution cost.

Useful strategies include:

- Ship less JavaScript
- Code split aggressively
- Avoid heavy libraries
- Reduce long tasks
- Virtualize large lists
- Use efficient animations
- Lazy load non-critical features
- Avoid excessive DOM work
- Move heavy computation to Web Workers

Performance should be tested on throttled CPU or real lower-end hardware.

**Interview Line**

Low-end device optimization focuses on smaller bundles, less main-thread work, lower memory usage, and simpler rendering.

### Q. How do you handle large data rendering in frontend?

**Answer:**

Rendering thousands of DOM nodes at once can be expensive.

Common strategies include:

- Pagination
- Virtualization
- Infinite scrolling
- Incremental rendering
- Server-side filtering
- Memoized transformations

Virtualization renders only items currently visible.

**Example:**

Instead of rendering:

```text
10,000 rows
```

the UI may render only:

```text
20 visible rows
```

and reuse them as the user scrolls.

**Interview Line**

Large frontend datasets should usually be paginated or virtualized so only the currently needed items are rendered.

### Q. How do you handle long-running JavaScript tasks?

**Answer:**

Long-running tasks block the main thread and make the UI unresponsive.

Strategies include:

- Break work into smaller chunks
- Schedule work across frames
- Use Web Workers
- Avoid synchronous loops over huge datasets
- Process data incrementally
- Move work to the server when appropriate

**Example:**

Instead of processing one million items synchronously, split the work into batches.

For CPU-heavy work that does not need the DOM:

```js
const worker = new Worker("worker.js");
```

can keep the main thread responsive.

**Interview Line**

Long-running JavaScript should be split into smaller tasks or moved to Web Workers so the main thread remains responsive.
