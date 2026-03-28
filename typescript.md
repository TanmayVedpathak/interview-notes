## Core TypeScript Concepts

### Q. What is TypeScript and how is it different from JavaScript?

**Answer:**

🔹 Definition

- TypeScript is a superset of JavaScript developed by Microsoft.
- It adds static typing, modern features, and better tooling on top of JavaScript.

🔹 Key Concept

- TypeScript code compiles into JavaScript
- Browsers do not understand TypeScript directly

🔹 Differences

| Feature         | TypeScript                           | JavaScript   |
| --------------- | ------------------------------------ | ------------ |
| Typing          | Static (optional)                    | Dynamic      |
| Compilation     | Required                             | Not required |
| Error Detection | Compile-time                         | Runtime      |
| OOP Support     | Strong (interfaces, enums)           | Limited      |
| Tooling         | Better (IntelliSense, auto-complete) | Basic        |

🔹 Example

```ts
// TypeScript
let age: number = 25;

// JavaScript
let age = 25;
```

🔥 Interview Line

TypeScript is a statically typed superset of JavaScript that helps catch errors at compile time and improves code maintainability.

### Q. Benefits of using TypeScript in large applications

**Answer:**

🔹 Key Benefits

1. Early Error Detection
   - Errors caught at compile time
   - Reduces runtime bugs

2. Better Code Maintainability
   - Types act as documentation
   - Easier for teams to understand code

3. Scalability
   - Ideal for large codebases
   - Helps manage complexity

4. Improved Developer Experience
   - IntelliSense
   - Autocomplete
   - Refactoring support

5. Strong Refactoring Support
   - Safe renaming, restructuring

6. OOP Features
   - Interfaces, Generics, Enums

🔹 Example

```ts
function add(a: number, b: number) {
  return a + b;
}

add(5, "10"); // ❌ Error in TypeScript
```

🔥 Interview Line

TypeScript improves scalability, maintainability, and reliability of large applications by enforcing type safety and better tooling.

### Q. What are types in TypeScript? Primitive vs Non-Primitive

**Answer:**

🔹 Definition

- Types define the kind of value a variable can hold

🔹 Primitive Types

| Type      | Example                        |
| --------- | ------------------------------ |
| number    | `let age: number = 25`         |
| string    | `let name: string = "Tanmay"`  |
| boolean   | `let isActive: boolean = true` |
| null      | `let x: null = null`           |
| undefined | `let y: undefined = undefined` |
| symbol    | Unique identifiers             |
| bigint    | Large numbers                  |

🔹 Non-Primitive Types

| Type     | Example                 |
| -------- | ----------------------- |
| object   | `{name: "Tanmay"}`      |
| array    | `number[]`              |
| tuple    | `[string, number]`      |
| enum     | `enum Role { Admin }`   |
| function | `(a: number) => number` |

🔥 Interview Line

Primitive types represent single values, while non-primitive types represent collections or complex structures.

### Q. What is Type Inference?

**Answer:**

🔹 Definition

- TypeScript automatically infers (guesses) the type based on the value.

🔹 Example

```ts
let name = "Tanmay"; // inferred as string
let age = 25; // inferred as number
```

🔹 Key Point

- You don’t always need to explicitly define types

🔥 Interview Line

Type inference allows TypeScript to automatically determine variable types without explicit annotations.

### Q. What is the any type? When should you avoid it?

**Answer:**

🔹 Definition

- any disables type checking

🔹 Example

```ts
let data: any = 10;
data = "hello"; // ✅ allowed
data = true; // ✅ allowed
```

🔹 Why Avoid It?

- Removes type safety ❌
- Defeats purpose of TypeScript ❌
- Can introduce runtime bugs ❌

🔹 When to Use

- Migrating from JavaScript
- Working with unknown third-party data (temporary)

🔥 Interview Line

any should be avoided because it bypasses type safety and makes TypeScript behave like JavaScript.

### Q. Difference between unknown and any

**Answer:**

🔹 Key Difference

| Feature     | any              | unknown          |
| ----------- | ---------------- | ---------------- |
| Type Safety | ❌ None          | ✅ Strict        |
| Assignment  | Anything allowed | Needs type check |
| Usage       | Unsafe           | Safe alternative |

🔹 Example

```ts
let value: unknown = "Hello";

// ❌ Error
value.toUpperCase();

// ✅ Safe usage
if (typeof value === "string") {
  value.toUpperCase();
}
```

🔥 Interview Line

unknown is a safer version of any because it forces type checking before usage.

### Q. What is never type and when is it used?

**Answer:**

🔹 Definition

- Represents values that never occur

🔹 Use Cases

1. Functions that never return

```ts
function throwError(): never {
  throw new Error("Error");
}
```

2. Infinite loops

```ts
function infiniteLoop(): never {
  while (true) {}
}
```

🔹 Key Point

- never ≠ void
- never means no value ever returned

🔥 Interview Line

The never type represents unreachable code or functions that never complete.

### Q. Difference between void and undefined

**Answer:**

🔹 Key Difference

| Feature | void            | undefined |
| ------- | --------------- | --------- |
| Meaning | No return value | A value   |
| Usage   | Functions       | Variables |
| Type    | Special         | Primitive |

🔹 Example

```ts
function log(): void {
  console.log("Hello");
}

let x: undefined = undefined;
```

🔹 Key Insight

- void → absence of return
- undefined → actual value

🔥 Interview Line

void represents absence of return value, while undefined is an actual primitive value.

## Interfaces & Types

### Q. What is the difference between interface and type?

**Answer:**

🔹 Definition
interface → Used to define the structure of an object
type → Used to define any type (primitive, union, object, etc.)
🔹 Key Differences
Feature interface type
Object Definition ✅ Yes ✅ Yes
Union / Intersection ❌ No ✅ Yes
Primitive Alias ❌ No ✅ Yes
Extensibility extends & (intersection)
Declaration Merging ✅ Supported ❌ Not supported
🔹 Example
// Interface
interface User {
name: string;
age: number;
}

// Type
type UserType = {
name: string;
age: number;
};
🔥 Interview Line

Interfaces are mainly for object structures, while types are more flexible and can represent unions, primitives, and complex compositions.

### Q. Can interfaces extend multiple interfaces?

**Answer:**

🔹 Answer: ✅ Yes
🔹 Example
interface Person {
name: string;
}

interface Employee {
employeeId: number;
}

interface Manager extends Person, Employee {
department: string;
}
🔹 Key Point
TypeScript supports multiple inheritance with interfaces
🔥 Interview Line

Yes, interfaces can extend multiple interfaces, allowing composition of multiple types into one.

### Q. What are optional properties in interfaces?

**Answer:**

🔹 Definition
Properties that are not required when creating an object
🔹 Syntax
Use ? after property name
🔹 Example
interface User {
name: string;
age?: number;
}

const user1: User = {
name: "Tanmay"
};
🔹 Use Cases
API responses
Partial data
Forms
🔥 Interview Line

Optional properties allow flexibility by making certain fields non-mandatory using the ? operator.

### Q. What is readonly in TypeScript?

**Answer:**

🔹 Definition
Prevents modification of a property after initialization
🔹 Example
interface User {
readonly id: number;
name: string;
}

const user: User = { id: 1, name: "Tanmay" };

// ❌ Error
user.id = 2;
🔹 Key Point
Ensures immutability
🔥 Interview Line

readonly ensures that a property cannot be changed after it is assigned, improving data safety.

### Q. Difference between type alias and interface in real-world usage

**Answer:**

🔹 When to Use Interface
Object structures
Class contracts
Extendable APIs
Large scalable apps
🔹 When to Use Type
Unions (string | number)
Intersections
Utility types
Complex transformations
🔹 Example
// Interface (best for objects)
interface User {
name: string;
}

// Type (best for unions)
type Status = "success" | "error";
🔹 Practical Rule

👉 Use interface by default for objects
👉 Use type when you need flexibility

🔥 Interview Line

Interfaces are preferred for object contracts, while types are better for unions and complex type compositions.

### Q. How do you create index signatures?

**Answer:**

🔹 Definition
Used when you don’t know property names in advance
🔹 Syntax
interface Dictionary {
[key: string]: string;
}
🔹 Example
interface UserRoles {
[username: string]: string;
}

const roles: UserRoles = {
Tanmay: "admin",
Rahul: "user"
};
🔹 Key Points
Key type → string, number, or symbol
Value type → defined by you
🔹 Advanced Example
interface ApiResponse {
[key: string]: string | number;
}
🔥 Interview Line

Index signatures allow dynamic object keys with predefined value types, useful for dictionaries or API responses.

### Final Summary

interface vs type → flexibility vs structure
multiple inheritance → interfaces support it
optional + readonly → control object behavior
index signatures → dynamic keys

## Functions & Generics

### Q. How do you define types for functions in TypeScript?

**Answer:**

🔹 Definition

In TypeScript, you can define types for:

- Parameters
- Return value

🔹 Syntax

```ts
function functionName(param: type): returnType {
  return value;
}
```

🔹 Example

```ts
function add(a: number, b: number): number {
  return a + b;
}
```

🔹 Function Type (Variable)

```ts
let multiply: (a: number, b: number) => number;

multiply = (x, y) => x * y;
```

🔹 Key

- Parameters and return types improve safety
- Helps avoid runtime errors

🔥 Interview Line

Function types in TypeScript define both parameter types and return types to ensure type safety.

### Q. What are optional and default parameters?

**Answer:**

🔹 Optional Parameters

- Marked using ?
- Not required while calling function

```ts
function greet(name: string, age?: number) {
  return `Hello ${name}`;
}
```

🔹 Default Parameters

- Assign default value
- Used when argument is not provided

```ts
function greet(name: string, age: number = 25) {
  return `Hello ${name}, age ${age}`;
}
```

🔹 Key Difference

| Feature       | Optional | Default |
| ------------- | -------- | ------- |
| Required      | ❌ No    | ❌ No   |
| Default Value | ❌ No    | ✅ Yes  |

🔥 Interview Line

Optional parameters are not required, while default parameters automatically assign a value if none is provided.

### Q. What are generics? Why are they useful?

**Answer:**

🔹 Definition

- Generics allow you to write reusable, flexible, type-safe code

🔹 Problem Without Generics

```ts
function identity(value: any): any {
  return value;
}
```

❌ Loses type safety

🔹 With Generics

```ts
function identity<T>(value: T): T {
  return value;
}
```

🔹 Benefits

- Reusability ✅
- Type safety ✅
- Better IntelliSense ✅
- Avoids any ✅

🔥 Interview Line

Generics allow writing reusable components that maintain type safety across different data types.

### Q. Example of generic function

**Answer:**

🔹 Basic Example

```ts
function getValue<T>(value: T): T {
  return value;
}

getValue<string>("Hello");
getValue<number>(10);
```

🔹 Generic with Arrays

```ts
function getFirstElement<T>(arr: T[]): T {
  return arr[0];
}
```

🔹 Key Insight

Type is decided at runtime usage (but checked at compile time)

🔥 Interview Line

A generic function adapts to different types while preserving type information.

### Q. What are generic constraints?

**Answer:**

🔹 Definition

Restrict generic types using extends

🔹 Example

```ts
function getLength<T extends { length: number }>(item: T): number {
  return item.length;
}
```

🔹 Usage

```ts
getLength("Hello"); // ✅ string has length
getLength([1, 2, 3]); // ✅ array has length
getLength(10); // ❌ number doesn't have
```

🔹 Why

- Prevent invalid operations
- Add type safety to generics

🔥 Interview Line

Generic constraints restrict types to ensure only valid operations are performed.

### Q. Difference between T extends object vs T extends {}

**Answer:**

🔹 Key Difference

| Feature            | `T extends object` | `T extends {}` |
| ------------------ | ------------------ | -------------- |
| Accepts primitives | ❌ No              | ✅ Yes         |
| Accepts objects    | ✅ Yes             | ✅ Yes         |
| Strictness         | More strict        | Less strict    |

🔹 Explanation

✅ T extends object

```ts
function test<T extends object>(val: T) {}

test({}); // ✅
test(10); // ❌
```

✅ T extends {}

```ts
function test<T extends {}>(val: T) {}

test({}); // ✅
test(10); // ✅
```

🔹 Important Insight

- {} means any non-null/undefined value
- bject means only non-primitive objects

🔥 Interview Line

T extends object restricts to non-primitive types, while T extends {} allows any non-nullish value, including primitives.

## Advanced Types

### Q. What are union and intersection types?

**Answer:**

🔹 Union Types (|)

✅ Definition

Allows a variable to hold multiple possible types

🔹 Example

```ts
let value: string | number;

value = "Hello"; // ✅
value = 10; // ✅
```

🔹 Key Point

- You can only access common properties

🔹 Intersection Types (&)

✅ Definition

Combines multiple types into one

🔹 Example

```ts
type A = { name: string };
type B = { age: number };

type Person = A & B;

const user: Person = {
  name: "Tanmay",
  age: 25,
};
```

🔹 Key Point

Must satisfy all types

🔥 Interview Line

Union types allow multiple possible types, while intersection types combine multiple types into one.

### Q. What is type narrowing?

**Answer:**

🔹 Definition

Process of refining a broad type into a specific type
🔹 Example

```ts
function print(value: string | number) {
  if (typeof value === "string") {
    console.log(value.toUpperCase()); // narrowed to string
  }
}
```

🔹 Why Important

- Enables safe operations
- Prevents runtime errors

🔥 Interview Line

Type narrowing refines a union type into a more specific type using checks like typeof or conditions.

### Q. Explain type guards (typeof, instanceof, custom guards)

**Answer:**

🔹 Definition

Techniques used to narrow types safely

🔹 1. typeof Guard

```ts
function check(value: string | number) {
  if (typeof value === "string") {
    return value.length;
  }
}
```

🔹 2. instanceof Guard

```ts
class Animal {}
class Dog extends Animal {}

function check(animal: Animal) {
  if (animal instanceof Dog) {
    console.log("Dog detected");
  }
}
```

🔹 3. Custom Type Guard

```ts
type User = { name: string };

function isUser(obj: any): obj is User {
  return obj && typeof obj.name === "string";
}
```

🔹 Key Insight

Custom guards use obj is Type

🔥 Interview Line

Type guards are techniques to narrow types safely using typeof, instanceof, or custom predicates.

### Q. What is discriminated union?

**Answer:**

🔹 Definition

A union type with a common literal property (discriminator)

🔹 Example

```ts
type Circle = { kind: "circle"; radius: number };
type Square = { kind: "square"; size: number };

type Shape = Circle | Square;

function area(shape: Shape) {
  if (shape.kind === "circle") {
    return Math.PI * shape.radius ** 2;
  }
}
```

🔹 Key Points

- Uses a common field (kind)
- Helps TypeScript automatically narrow types

🔥 Interview Line

Discriminated unions use a common property to differentiate types and enable automatic type narrowing.

### Q. What are mapped types?

**Answer:**

🔹 Definition

Create new types by transforming existing types

🔹 Syntax

```ts
type NewType = {
  [Key in keyof OldType]: OldType[Key];
};
```

🔹 Example

```ts
type User = {
  name: string;
  age: number;
};

type ReadOnlyUser = {
  readonly [K in keyof User]: User[K];
};
```

🔹 Built-in Examples

- Partial<T>
- Readonly<T>
- Pick<T, K>

🔥 Interview Line

Mapped types transform existing types by iterating over their keys.

### Q. What are conditional types?

**Answer:**

🔹 Definition

Types that depend on a condition
🔹 Syntax

```ts
type Result<T> = T extends string ? string : number;
```

🔹 Example

```ts
type Check<T> = T extends number ? "Number" : "Other";

type A = Check<number>; // "Number"
type B = Check<string>; // "Other"
```

🔹 Advanced Example

```ts
type NonNullable<T> = T extends null | undefined ? never : T;
```

🔹 Key Insight

Works like ternary operator for types

🔥 Interview Line

Conditional types allow type logic using conditions, similar to a ternary operator.

## Utility Types

### Q. What are utility types in TypeScript?

**Answer:**

🔹 Definition

Utility types are predefined generic types in TypeScript that help transform and manipulate existing types.

🔹 Why They Are Useful

- Reduce code duplication ✅
- Improve readability ✅
- Enable powerful type transformations ✅
- Widely used in large-scale apps ✅

🔹 Common Utility Types

- Partial<T>
- Required<T>
- Readonly<T>
- Pick<T, K>
- Omit<T, K>
- Record<K, T>
- ReturnType<T>
- Parameters<T>

🔥 Interview Line

Utility types are built-in generic helpers that transform existing types to make code more reusable and maintainable.

### Q. Partial<T>

**Answer:**

🔹 Definition

Makes all properties optional

🔹 Example

```ts
type User = {
  name: string;
  age: number;
};

type PartialUser = Partial<User>;
```

🔹 Result

```ts
{
name?: string;
age?: number;
}
```

🔹 Use Case

Updating objects (e.g., PATCH API)

🔥 Interview Line

Partial<T> makes all properties optional, useful for updates and flexible objects.

### Q. Required<T>

**Answer:**

🔹 Definition

Makes all properties mandatory

🔹 Example

```ts
type User = {
  name?: string;
  age?: number;
};

type RequiredUser = Required<User>;
```

🔹 Result

```ts
{
  name: string;
  age: number;
}
```

🔹 Use Case

Ensuring complete data

🔥 Interview Line

Required<T> converts all optional properties into required ones.

### Q. Readonly<T>

**Answer:**

🔹 Definition

Makes all properties immutable

🔹 Example

```ts
type User = {
  name: string;
};

type ReadonlyUser = Readonly<User>;
```

🔹 Result

```ts
{
readonly name: string;
}
```

🔹 Use Case

Prevent accidental mutation (e.g., state management)

🔥 Interview Line

Readonly<T> ensures properties cannot be modified after assignment.

### Q. Pick<T, K>

**Answer:**

🔹 Definition

Select specific properties from a type

🔹 Example

```ts
type User = {
  name: string;
  age: number;
  email: string;
};

type UserPreview = Pick<User, "name" | "age">;
```

🔹 Result

```ts
{
  name: string;
  age: number;
}
```

🔹 Use Case

API response shaping

🔥 Interview Line

Pick<T, K> creates a new type by selecting specific keys from an existing type.

### Q. Omit<T, K>

**Answer:**

🔹 Definition

Removes specific properties from a type

🔹 Example

```ts
type User = {
  name: string;
  age: number;
  password: string;
};

type SafeUser = Omit<User, "password">;
```

🔹 Result

```ts
{
  name: string;
  age: number;
}
```

🔹 Use Case

Excluding sensitive data

🔥 Interview Line

Omit<T, K> removes specified properties from a type.

### Q. Record<K, T>

**Answer:**

🔹 Definition

Creates an object type with keys of type K and values of type T

🔹 Example

```ts
type Roles = "admin" | "user";

type UserRoles = Record<Roles, string>;
```

🔹 Result

```ts
{
  admin: string;
  user: string;
}
```

🔹 Use Case

Dictionaries / Maps

🔥 Interview Line

Record<K, T> creates a type with predefined keys and uniform value types.

### Q. When would you use ReturnType or Parameters?

**Answer:**

🔹 ReturnType<T>

Extracts return type of a function

🔹 Example

```ts
function getUser() {
  return { name: "Tanmay" };
}

type User = ReturnType<typeof getUser>;
```

🔹 Use Case

Reusing function return types

🔹 Parameters<T>

Extracts parameter types as a tuple

🔹 Example

```ts
function add(a: number, b: number) {}

type Params = Parameters<typeof add>;
```

🔹 Result

```ts
[number, number];
```

🔹 Use Case

- Function wrappers
- Middleware
- Higher-order functions

🔥 Interview Line

ReturnType and Parameters help extract function types, enabling better reuse and consistency.

## Classes & OOP in TypeScript

### Q. How does TypeScript support OOP?

**Answer:**

🔹 Definition

TypeScript supports Object-Oriented Programming (OOP) by adding features on top of JavaScript such as:

- Classes
- Interfaces
- Inheritance
- Encapsulation
- Abstraction
- Polymorphism

🔹 Key Features

✅ Classes

```ts
class Person {
  name: string;

  constructor(name: string) {
    this.name = name;
  }
}
```

✅ Inheritance

```ts
class Employee extends Person {
  role: string;
}
```

✅ Interfaces (Contracts)

```ts
interface User {
  name: string;
}
```

✅ Encapsulation

Using access modifiers (`private`, `protected`, `public`)

🔥 Interview Line

TypeScript supports OOP through classes, interfaces, inheritance, and access modifiers, enabling better structure and maintainability.

### Q. What are access modifiers (public, private, protected)?

**Answer:**

🔹 Definition

Access modifiers control visibility and accessibility of class members

🔹 Types

✅ public (default)

Accessible everywhere

```ts
class A {
  public name = "Tanmay";
}
```

✅ private

Accessible only within the same class

```ts
class A {
  private age = 25;
}
```

✅ protected

Accessible within class and subclasses

```ts
class A {
  protected value = 10;
}

class B extends A {
  getValue() {
    return this.value; // ✅ allowed
  }
}
```

🔹 Comparison

| Modifier  | Same Class | Subclass | Outside |
| --------- | ---------- | -------- | ------- |
| public    | ✅         | ✅       | ✅      |
| private   | ✅         | ❌       | ❌      |
| protected | ✅         | ✅       | ❌      |

🔥 Interview Line

Access modifiers control visibility: public is open, private is restricted to the class, and protected allows access in subclasses.

### Q. What is a constructor in TypeScript?

**Answer:**

🔹 Definition

A special method used to initialize objects

🔹 Example

```ts
class User {
  name: string;

  constructor(name: string) {
    this.name = name;
  }
}
```

🔹 Shortcut (Parameter Properties)

```ts
class User {
  constructor(public name: string) {}
}
```

🔹 Key Points

- Called automatically when object is created
- Used for initial setup

🔥 Interview Line

A constructor initializes class properties when an object is created.

### Q. What are abstract classes?

**Answer:**

🔹 Definition

- A class that cannot be instantiated
- Used as a base class

🔹 Example

```ts
abstract class Animal {
  abstract makeSound(): void;

  move() {
    console.log("Moving...");
  }
}

class Dog extends Animal {
  makeSound() {
    console.log("Bark");
  }
}
```

🔹 Key Points

- Can have abstract + concrete methods
- Forces subclasses to implement methods

🔥 Interview Line

Abstract classes define a blueprint with optional implementation and must be extended by subclasses.

### Q. Difference between interface and abstract class

**Answer:**

🔹 Key Differences

| Feature              | Interface         | Abstract Class |
| -------------------- | ----------------- | -------------- |
| Implementation       | ❌ No             | ✅ Yes         |
| Methods              | Only declarations | Both           |
| Multiple inheritance | ✅ Yes            | ❌ No          |
| Constructor          | ❌ No             | ✅ Yes         |
| Access modifiers     | ❌ No             | ✅ Yes         |

🔹 Example

```ts
interface A {
  method(): void;
}

abstract class B {
  abstract method(): void;
  log() {
    console.log("Hello");
  }
}
```

🔹 Key Insight

- Interface = contract
- Abstract class = partial implementation

🔥 Interview Line

Interfaces define structure only, while abstract classes provide both structure and partial implementation.

### Q. Can TypeScript enforce design patterns?

**Answer:**

🔹 Short Answer

👉 Yes (at compile-time), but not strictly at runtime

🔹 Explanation

TypeScript helps enforce patterns using:

- Interfaces
- Abstract classes
- Access modifiers
- Generics

🔹 Example (Singleton Pattern)

```ts
class Singleton {
  private static instance: Singleton;

  private constructor() {}

  static getInstance() {
    if (!Singleton.instance) {
      Singleton.instance = new Singleton();
    }
    return Singleton.instance;
  }
}
```

🔹 What TypeScript Ensures

- Correct structure ✅
- Type safety ✅
- Proper usage ✅

🔹 What It Cannot Enforce

- Runtime behavior ❌
- Business logic ❌

🔥 Interview Line

TypeScript helps enforce design patterns through types and structure at compile time, but cannot guarantee runtime behavior.

## Modules & Configuration

### Q. What is `tsconfig.json`?

**Answer:**

🔹 Definition

`tsconfig.json` is the configuration file for the TypeScript compiler (tsc)

🔹 Purpose

Defines how TypeScript should:

- Compile code
- Handle files
- Apply type checking rules

🔹 Basic Example

```json
{
  "compilerOptions": {
    "target": "ES6",
    "module": "commonjs",
    "strict": true
  }
}
```

🔹 Key Sections

- `compilerOptions` → compiler behavior
- `include` / `exclude` → files to compile
- `extends` → inherit configs

🔥 Interview Line

`tsconfig.json` controls how TypeScript compiles code and enforces type checking rules.

### Q. What are common compiler options (`strict`, `target`, `module`)?

**Answer:**

🔹 1. `strict`

Enables all strict type-checking options

🔹 Example

```json
{
  "compilerOptions": {
    "strict": true
  }
}
```

🔹 Includes

- noImplicitAny
- strictNullChecks
- strictFunctionTypes

🔥 Interview Line

`strict` enables maximum type safety by turning on all strict checks.

🔹 2. `target`

Specifies the JavaScript version to compile to

🔹 Example

```json
{
  "compilerOptions": {
    "target": "ES5"
  }
}
```

🔹 Common Values

ES5, ES6 (ES2015), ESNext

🔥 Interview Line

`target` defines which JavaScript version TypeScript compiles into.

🔹 3. `module`

Specifies the module system

🔹 Example

```json
{
  "compilerOptions": {
    "module": "commonjs"
  }
}
```

🔹 Common Values

- commonjs
- esnext
- es6

🔥 Interview Line

`module` determines how imports and exports are handled in the compiled output.

### Q. Difference between ESModule and CommonJS

**Answer:**

🔹 ESModule (ESM)

✅ Features

- Uses `import` / `export`
- Static analysis (compile-time)
- Modern standard

🔹 Example

```ts
import { add } from "./math";
export const value = 10;
```

🔹 CommonJS (CJS)

✅ Features

- Uses `require` / `module.exports`
- Dynamic (runtime)
- Used in Node.js (older)

🔹 Example

```js
const math = require("./math");
module.exports = { value: 10 };
```

🔹 Key Differences

| Feature      | ESModule      | CommonJS               |
| ------------ | ------------- | ---------------------- |
| Syntax       | import/export | require/module.exports |
| Loading      | Static        | Dynamic                |
| Usage        | Modern JS     | Node.js (legacy)       |
| Tree Shaking | ✅ Supported  | ❌ Not supported       |

🔥 Interview Line

ESModules use modern static imports/exports, while CommonJS uses dynamic require and module.exports.

### Q. How does TypeScript handle imports/exports?

**Answer:**

🔹 Core Idea

- TypeScript uses ESModule syntax
- Compiles based on `module` setting in `tsconfig.json`

🔹 Example

TypeScript Code

```ts
export function add(a: number, b: number) {
  return a + b;
}
```

```ts
import { add } from "./math";
```

🔹 Compiled Output (CommonJS)

```js
exports.add = function (a, b) {
  return a + b;
};
```

🔹 Important Concepts

1. Named Exports

```ts
export const a = 10;
```

2. Default Export

```ts
export default function () {}
```

3. Type-only Imports

```ts
import type { User } from "./types";
```

🔹 Key Insight

TypeScript separates:

- Type system (compile-time)
- JavaScript output (runtime)

🔥 Interview Line

TypeScript uses ESModule syntax but compiles it into different module systems like CommonJS based on configuration.

## Real-world / Practical Questions

### Q. How do you type an API response?

**Answer:**

🔹 Approach

- Define a type/interface matching API structure
- Use it in fetch/axios calls

🔹 Example

```ts
interface User {
  id: number;
  name: string;
  email: string;
}

async function fetchUsers(): Promise<User[]> {
  const res = await fetch("/api/users");
  return res.json();
}
```

🔹 With Generic API Wrapper

```ts
async function fetchData<T>(url: string): Promise<T> {
  const res = await fetch(url);
  return res.json();
}

// Usage
const users = await fetchData<User[]>("/api/users");
```

🔹 Best Practices

- Match backend contract
- Use optional fields for uncertain data
- Validate if needed (e.g., runtime checks)

🔥 Interview Line

API responses are typed using interfaces or generics to ensure type safety and predictable data handling.

### Q. How do you handle nullable values safely?

**Answer:**

🔹 Problem

Values can be `null` or `undefined`

🔹 Solutions

✅ 1. Union Types

```ts
let name: string | null = null;
```

✅ 2. Optional Chaining

```ts
user?.profile?.name;
```

✅ 3. Nullish Coalescing

```ts
const username = user.name ?? "Guest";
```

✅ 4. Type Guards

```ts
if (user.name !== null) {
  console.log(user.name);
}
```

⚠️ 5. Non-null Assertion (use carefully)

```ts
user.name!;
```

🔹 Best Practice

Prefer safe checks over forcing (!)

🔥 Interview Line

Nullable values are handled using union types, optional chaining, and null checks to ensure safe access.

### Q. How do you migrate a JavaScript project to TypeScript?

**Answer:**

🔹 Step-by-Step

1. Install TypeScript

```bash
npm install typescript
```

2. Create config

```bash
npx tsc --init
```

3. Rename files

`.js` → `.ts` / `.tsx`

4. Enable gradual typing

```json
{
  "compilerOptions": {
    "allowJs": true,
    "checkJs": false
  }
}
```

5. Fix errors gradually

Start with critical modules

6. Enable strict mode later

```json
{
  "strict": true
}
```

🔹 Strategy

Incremental migration (not all at once)

🔥 Interview Line

Migrate gradually by enabling TypeScript, renaming files, and progressively adding types instead of converting everything at once.

### Q. How do you avoid overusing any?

**Answer:**

🔹 Problems with `any`

- No type safety ❌
- Runtime bugs ❌

🔹 Alternatives

✅ Use `unknown`

```ts
let value: unknown;
```

✅ Use Generics

```ts
function identity<T>(val: T): T {
  return val;
}
```

✅ Define Proper Types

```ts
interface User {
  name: string;
}
```

✅ Use Utility Types

- `Partial`
- `Record`
- `Pick`

🔹 Rule

👉 Use `any` only as a last resort

🔥 Interview Line

Avoid `any` by using `unknown`, generics, and proper type definitions to maintain type safety.

### Q. How do you structure types in a large project?

**Answer:**

🔹 Recommended Structure

```
src/
├── components/
├── features/
├── services/
├── types/
│ ├── user.types.ts
│ ├── api.types.ts
│ └── index.ts
```

🔹 Best Practices

✅ 1. Centralized Types

Keep reusable types in `/types`

✅ 2. Feature-based Types

Co-locate types with features

✅ 3. Use Naming Conventions

`User`, `UserResponse`, `UserDTO`

✅ 4. Barrel Files

```ts
export \* from "./user.types";
```

✅ 5. Separate API vs UI Types

Backend vs frontend mapping

🔹 Key Insight

Scalability depends on organized types

🔥 Interview Line

In large projects, types should be modular, reusable, and organized by feature or domain.

### Q. How do you type React props in TypeScript?

**Answer:**

🔹 Using Interface

```ts
interface Props {
name: string;
age?: number;
}

function User({ name, age }: Props) {
return <div>{name}</div>;
}
```

🔹 Using Type

```ts
type Props = {
name: string;
};

const User = ({ name }: Props) => <div>{name}</div>;
```

🔹 With Children

```ts
type Props = {
children: React.ReactNode;
};

function Wrapper({ children }: Props) {
return <div>{children}</div>;
}
```

🔹 With Default Props

```ts
type Props = {
  name?: string;
};

function User({ name = "Guest" }: Props) {}
```

🔹 Best Practices

- Prefer interface for props
- Use strict typing
- Avoid `any`

🔥 Interview Line

React props are typed using interfaces or types to ensure component reliability and better developer experience.

## React + TypeScript

### Q. How do you type functional components?

**Answer:**

🔹 Using `interface` (Recommended)

```ts
interface Props {
name: string;
}

function User({ name }: Props) {
return <div>{name}</div>;
}
```

🔹 Using `type`

```ts
type Props = {
name: string;
};

const User = ({ name }: Props) => <div>{name}</div>;
```

🔹 Key Point

Explicitly type props for better safety

🔥 Interview Line

Functional components are typed by defining a props interface or type and applying it to the component parameters.

### Q. Difference between `React.FC` and normal function typing

**Answer:**

🔹 `React.FC`

```ts
const User: React.FC<{ name: string }> = ({ name }) => {
return <div>{name}</div>;
};
```

🔹 Normal Function (Preferred)

```ts
interface Props {
name: string;
}

function User({ name }: Props) {
return <div>{name}</div>;
}
```

🔹 Key Differences

| Feature        | React.FC            | Normal Function      |
| -------------- | ------------------- | -------------------- |
| children       | Included by default | Must define manually |
| Readability    | Less clean          | Cleaner              |
| Flexibility    | Limited             | More flexible        |
| Recommendation | ❌ Avoid            | ✅ Preferred         |

🔹 Why Avoid `React.FC`

- Implicit children
- Less control
- Can hide bugs

🔥 Interview Line

`React.FC` adds implicit children and less flexibility, so normal function typing is preferred in modern React.

### Q. How to type `useState`, `useRef`, `useReducer`

**Answer:**

🔹 useState

```ts
const [count, setCount] = useState<number>(0);
```

With Union

```ts
const [user, setUser] = useState<User | null>(null);
```

🔹 useRef

```ts
const inputRef = useRef<HTMLInputElement | null>(null);
```

🔹 useReducer

```ts
type State = { count: number };

type Action = { type: "increment" } | { type: "decrement" };

function reducer(state: State, action: Action): State {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    default:
      return state;
  }
}

const [state, dispatch] = useReducer(reducer, { count: 0 });
```

🔥 Interview Line

Hooks are typed using generics, such as `useState<Type>` and `useRef<ElementType>`.

### Q. How to type event handlers

**Answer:**

🔹 Input Change Event

```ts
function handleChange(e: React.ChangeEvent<HTMLInputElement>) {
  console.log(e.target.value);
}
```

🔹 Button Click

```ts
function handleClick(e: React.MouseEvent<HTMLButtonElement>) {}
```

🔹 Form Submit

```ts
function handleSubmit(e: React.FormEvent<HTMLFormElement>) {
  e.preventDefault();
}
```

🔹 Key Tip

👉 Use `React.<EventType>`

🔥 Interview Line

Event handlers are typed using React-specific event types like `React.ChangeEvent` and `React.MouseEvent`.

### Q. How to type props with children

**Answer:**

🔹 Method 1: Explicit

```ts
type Props = {
children: React.ReactNode;
};

function Wrapper({ children }: Props) {
return <div>{children}</div>;
}
```

🔹 Method 2: With PropsWithChildren

```ts
import { PropsWithChildren } from "react";

type Props = {
  title: string;
};

function Card({ title, children }: PropsWithChildren<Props>) {}
```

🔹 Key Point

`React.ReactNode` covers all renderable content

🔥 Interview Line

Props with children are typed using `React.ReactNode` or `PropsWithChildren`.

### Q. Controlled vs Uncontrolled components typing

**Answer:**

🔹 Controlled Components

State is controlled by React

🔹 Example

```ts
const [value, setValue] = useState<string>("");

<input
value={value}
onChange={(e) => setValue(e.target.value)}
/>;
```

🔹 Typing

State + event types required

🔹 Uncontrolled Components

Uses DOM via `ref`

🔹 Example

```ts
const inputRef = useRef<HTMLInputElement>(null);

<input ref={inputRef} />;
```

🔹 Typing

Focus on useRef

🔹 Key Differences

| Feature        | React.FC            | Normal Function      |
| -------------- | ------------------- | -------------------- |
| children       | Included by default | Must define manually |
| Readability    | Less clean          | Cleaner              |
| Flexibility    | Limited             | More flexible        |
| Recommendation | ❌ Avoid            | ✅ Preferred         |

🔥 Interview Line

Controlled components use React state and require state/event typing, while uncontrolled components rely on refs and direct DOM access.

## Debugging & Best Practices

### Q. What are common TypeScript errors you’ve faced?

**Answer:**

🔹 1. Type Mismatch

```ts
let age: number = "25"; // ❌
```

👉 Assigning wrong type

🔹 2. Property Does Not Exist

```ts
user.name; // ❌ if type not defined
```

👉 Missing or incorrect type definition

🔹 3. Possibly Null / Undefined

```ts
user.name.toUpperCase(); // ❌
```

👉 user might be null

🔹 4. Implicit any

```ts
function add(a, b) {
  // ❌
  return a + b;
}
```

👉 Happens when noImplicitAny is enabled

🔹 5. Union Type Errors

```ts
let val: string | number;
val.toUpperCase(); // ❌
```

👉 Need type narrowing

🔹 6. Incorrect Function Types

```ts
function fn(): string {
  return 10; // ❌
}
```

🔥 Interview Line

Common TypeScript errors include type mismatches, null safety issues, implicit any, and improper handling of union types.

### Q. How do you improve type safety?

**Answer:**

🔹 Best Practices

✅ Enable strict mode

`"strict": true`

✅ Avoid `any`

Use `unknown`, generics

✅ Use proper types/interfaces

```ts
interface User {
  name: string;
}
```

✅ Use type guards

```ts
if (typeof val === "string") {
}
```

✅ Use utility types

`Partial`, `Pick`, etc.

✅ Handle null safely

- Optional chaining (`?.`)
- Nullish coalescing (`??`)

🔥 Interview Line

Type safety is improved by enabling strict mode, avoiding any, using proper types, and applying type guards.

### Q. What is strict mode?

**Answer:**

🔹 Definition

A set of strict type-checking rules in TypeScript

🔹 Enable

```json
{
  "compilerOptions": {
    "strict": true
  }
}
```

🔹 Includes

- noImplicitAny
- strictNullChecks
- strictFunctionTypes
- strictPropertyInitialization

🔹 Benefits

- Early error detection ✅
- Safer code ✅
- Better maintainability ✅

🔥 Interview Line

Strict mode enables all strict type checks, improving code reliability and preventing common runtime errors.

### Q. How do you debug type issues?

**Answer:**

🔹 Techniques

✅ 1. Hover / IntelliSense

Check inferred types in editor

✅ 2. Use typeof

```ts
type T = typeof variable;
```

✅ 3. Break complex types

```ts
type Step1 = ...
type Step2 = ...
```

✅ 4. Add temporary types

```ts
const test: SomeType = value;
```

✅ 5. Use as const

```ts
const obj = { role: "admin" } as const;
```

✅ 6. Read error messages carefully

TS errors are very descriptive

🔥 Interview Line

Debugging type issues involves inspecting inferred types, breaking complex types, and leveraging TypeScript’s detailed error messages.

### Q. When should you use `as` (type assertion)?

**Answer:**

🔹 Definition

Tells TypeScript to treat a value as a specific type

🔹 Example

```ts
const input = document.getElementById("name") as HTMLInputElement;
```

🔹 When to Use

✅ DOM elements

```ts
const el = document.querySelector("input") as HTMLInputElement;
```

✅ When TS cannot infer correctly

```ts
const value = data as string;
```

✅ Third-party libraries

🔹 Rule

👉 Use only when you're sure about the type

🔥 Interview Line

Type assertions are used when TypeScript cannot infer types, but should be used cautiously as they bypass type checking.

### Q. Risks of type assertions

**Answer:**

🔹 Main Problem

👉 TypeScript trusts you blindly

🔹 Example

```ts
const value = "hello" as unknown as number;
```

❌ No error, but wrong type → runtime bug

🔹 Risks

- Runtime errors ❌
- Loss of type safety ❌
- Hard-to-debug issues ❌

🔹 Safer Alternatives

- Type guards ✅
- Proper typing ✅
- Generics ✅

🔥 Interview Line

Type assertions can introduce runtime bugs by bypassing type checks, so they should be used sparingly.

## Bonus Coding Questions

### Q. Write a generic function to reverse an array

**Answer:**

🔹 Solution

```ts
function reverseArray<T>(arr: T[]): T[] {
  return [...arr].reverse();
}
```

🔹 Usage

```ts
reverseArray<number>([1, 2, 3]); // [3, 2, 1]
reverseArray<string>(["a", "b"]); // ["b", "a"]
```

🔹 Key Point

Generic `<T>` ensures type safety

🔥 Interview Line

A generic reverse function ensures type safety while working with any array type.

### Q. Create a type-safe function for API calls

**Answer:**

🔹 Generic API Function

```ts
async function fetchData<T>(url: string): Promise<T> {
  const res = await fetch(url);

  if (!res.ok) {
    throw new Error("API Error");
  }

  return res.json();
}
```

🔹 Usage

```ts
interface User {
  id: number;
  name: string;
}

const users = await fetchData<User[]>("/api/users");
```

🔹 Improved Version (with response wrapper)

```ts
type ApiResponse<T> = {
  data: T;
  success: boolean;
};

async function fetchApi<T>(url: string): Promise<ApiResponse<T>> {
  const res = await fetch(url);
  return res.json();
}
```

🔥 Interview Line

Generic API functions allow reusable and type-safe data fetching across different response types.

### Q. Implement a utility type like MyPartial<T>

**Answer:**

🔹 Implementation

```ts
type MyPartial<T> = {
  [K in keyof T]?: T[K];
};
```

🔹 Example

```ts
type User = {
  name: string;
  age: number;
};

type PartialUser = MyPartial<User>;
```

🔹 Result

```ts
{
name?: string;
age?: number;
}
```

🔹 Key Concept

Uses mapped types + optional modifier (`?`)

🔥 Interview Line

`MyPartial<T>` is created using mapped types to make all properties optional.

### Q. Type a nested object safely

**Answer:**

🔹 Example

```ts
type User = {
  id: number;
  profile: {
    name: string;
    address: {
      city: string;
      pincode: number;
    };
  };
};
```

🔹 Safe Access

```ts
const user: User = {
  id: 1,
  profile: {
    name: "Tanmay",
    address: {
      city: "Mumbai",
      pincode: 400001,
    },
  },
};

// Safe usage
console.log(user.profile.address.city);
```

🔹 Optional Nested Fields

```ts
type User = {
  profile?: {
    name?: string;
  };
};
```

🔹 Safe Access with Optional Chaining

```ts
user.profile?.name;
```

🔥 Interview Line

Nested objects are typed using structured types and accessed safely using optional chaining.

### Q. Create a discriminated union example

**Answer:**

🔹 Definition

Union with a common property (discriminator)

🔹 Example

```ts
type Success = {
  status: "success";
  data: string;
};

type ErrorResponse = {
  status: "error";
  message: string;
};

type ApiResult = Success | ErrorResponse;
```

🔹 Usage

```ts
function handleResponse(res: ApiResult) {
  if (res.status === "success") {
    console.log(res.data);
  } else {
    console.log(res.message);
  }
}
```

🔹 Key Point

TypeScript auto-narrows based on status

🔥 Interview Line

Discriminated unions use a shared literal property to safely distinguish between types.
