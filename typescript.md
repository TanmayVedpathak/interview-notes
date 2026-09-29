# Typescript

## Core TypeScript Concepts

### Q. What is TypeScript and how is it different from JavaScript?

**Answer:**

Definition

- TypeScript is a superset of JavaScript developed by Microsoft.
- It adds static typing, modern features, and better tooling on top of JavaScript.

Key Concept

- TypeScript code compiles into JavaScript
- Browsers do not understand TypeScript directly

Differences

| Feature         | TypeScript                           | JavaScript   |
| --------------- | ------------------------------------ | ------------ |
| Typing          | Static (optional)                    | Dynamic      |
| Compilation     | Required                             | Not required |
| Error Detection | Compile-time                         | Runtime      |
| OOP Support     | Strong (interfaces, enums)           | Limited      |
| Tooling         | Better (IntelliSense, auto-complete) | Basic        |

Example

```ts
// TypeScript
let age: number = 25;

// JavaScript
let age = 25;
```

**Interview Line**

TypeScript is a statically typed superset of JavaScript that helps catch errors at compile time and improves code maintainability.

### Q. Benefits of using TypeScript in large applications

**Answer:**

Key Benefits

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

Example

```ts
function add(a: number, b: number) {
  return a + b;
}

add(5, "10"); // ❌ Error in TypeScript
```

**Interview Line**

TypeScript improves scalability, maintainability, and reliability of large applications by enforcing type safety and better tooling.

### Q. What are types in TypeScript? Primitive vs Non-Primitive

**Answer:**

Definition

- Types define the kind of value a variable can hold

Primitive Types

| Type      | Example                        |
| --------- | ------------------------------ |
| number    | `let age: number = 25`         |
| string    | `let name: string = "Tanmay"`  |
| boolean   | `let isActive: boolean = true` |
| null      | `let x: null = null`           |
| undefined | `let y: undefined = undefined` |
| symbol    | Unique identifiers             |
| bigint    | Large numbers                  |

Non-Primitive Types

| Type     | Example                 |
| -------- | ----------------------- |
| object   | `{name: "Tanmay"}`      |
| array    | `number[]`              |
| tuple    | `[string, number]`      |
| enum     | `enum Role { Admin }`   |
| function | `(a: number) => number` |

**Interview Line**

Primitive types represent single values, while non-primitive types represent collections or complex structures.

### Q. What is Type Inference?

**Answer:**

Definition

- TypeScript automatically infers (guesses) the type based on the value.

Example

```ts
let name = "Tanmay"; // inferred as string
let age = 25; // inferred as number
```

Key Point

- You don’t always need to explicitly define types

**Interview Line**

Type inference allows TypeScript to automatically determine variable types without explicit annotations.

### Q. What is the `any` type? When should you avoid it?

**Answer:**

Definition

- `any` disables type checking

Example

```ts
let data: any = 10;
data = "hello"; // ✅ allowed
data = true; // ✅ allowed
```

Why Avoid It?

- Removes type safety ❌
- Defeats purpose of TypeScript ❌
- Can introduce runtime bugs ❌

When to Use

- Migrating from JavaScript
- Working with unknown third-party data (temporary)

**Interview Line**

`any` should be avoided because it bypasses type safety and makes TypeScript behave like JavaScript.

### Q. Difference between `unknown` and `any`

**Answer:**

Key Difference

| Feature     | `any`            | `unknown`        |
| ----------- | ---------------- | ---------------- |
| Type Safety | ❌ None          | ✅ Strict        |
| Assignment  | Anything allowed | Needs type check |
| Usage       | Unsafe           | Safe alternative |

Example

```ts
let value: unknown = "Hello";

// ❌ Error
value.toUpperCase();

// ✅ Safe usage
if (typeof value === "string") {
  value.toUpperCase();
}
```

**Interview Line**

`unknown` is a safer version of `any` because it forces type checking before usage.

### Q. What is `never` type and when is it used?

**Answer:**

Definition

- Represents values that never occur

Use Cases

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

Key Point

- `never` ≠ `void`
- `never` means no value ever returned

**Interview Line**

The `never` type represents unreachable code or functions that never complete.

### Q. Difference between `void` and `undefined`

**Answer:**

Key Difference

| Feature | `void`          | `undefined` |
| ------- | --------------- | ----------- |
| Meaning | No return value | A value     |
| Usage   | Functions       | Variables   |
| Type    | Special         | Primitive   |

Example

```ts
function log(): void {
  console.log("Hello");
}

let x: undefined = undefined;
```

Key Insight

- `void` → absence of return
- `undefined` → actual value

**Interview Line**

`void` represents absence of return value, while `undefined` is an actual primitive value.

### Q. What is structural typing in TypeScript?

**Answer:**

Structural typing means TypeScript determines type compatibility based on the **shape of a value** rather than its explicit name.

If two objects have compatible properties, they can often be assigned to each other even if they were declared with different type names.

**Example:**

```ts
type User = {
  name: string;
};

type Employee = {
  name: string;
  id: number;
};

const employee: Employee = {
  name: "John",
  id: 101,
};

const user: User = employee;
```

This works because `Employee` contains at least the structure required by `User`.

TypeScript mainly asks:

```text
Does this value have the properties required by the target type?
```

**Interview Line**

TypeScript uses structural typing, so compatibility is based mainly on object shape rather than explicit type names.

### Q. What is nominal typing, and does TypeScript support it?

**Answer:**

Nominal typing means two types are compatible only when they have an explicit declared relationship or identity.

Languages such as Java and C# commonly use nominal typing for classes.

Conceptually:

```text
Type A
Type B
```

may have identical properties but still be treated as different because they have different names.

TypeScript is primarily structurally typed, not nominally typed.

However, nominal-like behavior can be created using techniques such as:

- Branded types
- Unique symbols
- Private/protected class members

**Example:**

```ts
type UserId = string & {
  readonly __brand: "UserId";
};

type OrderId = string & {
  readonly __brand: "OrderId";
};
```

Now `UserId` and `OrderId` are harder to mix accidentally.

**Interview Line**

TypeScript is primarily structural, but nominal-like typing can be simulated with branding, unique symbols, or private class members.

### Q. What is duck typing in TypeScript?

**Answer:**

Duck typing is the idea:

```text
If it looks like a duck and behaves like a duck, treat it as a duck.
```

In TypeScript, this is closely related to structural typing.

**Example:**

```ts
type Printable = {
  print: () => void;
};

const report = {
  title: "Sales",
  print() {
    console.log("Printing");
  },
};

function runPrint(value: Printable) {
  value.print();
}

runPrint(report);
```

`report` does not explicitly declare that it implements `Printable`, but it has the required structure.

**Interview Line**

Duck typing means values are accepted based on available behavior or properties, which aligns closely with TypeScript's structural type system.

### Q. Difference between structural typing and nominal typing

**Answer:**

The difference is how type identity is determined.

| Structural Typing       | Nominal Typing                  |
| ----------------------- | ------------------------------- |
| Based on shape          | Based on declared identity      |
| Matching members matter | Type names/relationships matter |
| Common in TypeScript    | Common in Java/C#               |
| More flexible           | More strict by identity         |

**Example:**

With structural typing:

```ts
type A = {
  value: string;
};

type B = {
  value: string;
};
```

`A` and `B` are compatible because their structures match.

In a nominal system, they could still be considered different types.

**Interview Line**

Structural typing compares shape, while nominal typing compares explicit type identity or declared relationships.

### Q. What is type compatibility in TypeScript?

**Answer:**

Type compatibility describes whether a value of one type can be assigned to another type.

Because TypeScript is structurally typed, compatibility is usually based on required members.

**Example:**

```ts
type Person = {
  name: string;
};

const employee = {
  name: "John",
  age: 30,
};

const person: Person = employee;
```

This is allowed because `employee` contains the required `name` property.

Type compatibility also applies to:

- Functions
- Classes
- Generics
- Arrays
- Objects

**Interview Line**

Type compatibility determines whether one TypeScript value can safely be used where another type is expected.

### Q. What is excess property checking?

**Answer:**

Excess property checking is an extra TypeScript check applied mainly to fresh object literals.

It catches properties that are not declared in the target type.

**Example:**

```ts
type User = {
  name: string;
};

const user: User = {
  name: "John",
  age: 30,
};
```

TypeScript reports an error because `age` is not part of `User`.

This helps catch typos and accidental extra fields.

**Interview Line**

Excess property checking detects undeclared properties on fresh object literals assigned to a known object type.

### Q. When does excess property checking happen?

**Answer:**

It mainly happens when a fresh object literal is:

- Assigned directly to a typed variable
- Passed directly as a function argument

**Example:**

```ts
type User = {
  name: string;
};

function printUser(user: User) {}
```

This may error:

```ts
printUser({
  name: "John",
  age: 30,
});
```

But this often works:

```ts
const value = {
  name: "John",
  age: 30,
};

printUser(value);
```

Why?

Because `value` is no longer treated as a fresh object literal for excess property checking, and structural compatibility is applied.

**Interview Line**

Excess property checking is strongest on fresh object literals, especially during direct assignment or function calls.

### Q. What is literal type in TypeScript?

**Answer:**

A literal type represents one exact value instead of a broad primitive category.

**Example:**

```ts
type Status = "idle" | "loading" | "success";
```

Here each string is a string literal type.

Another example:

```ts
type Direction = 1 | -1;
```

Literal types are useful for:

- State machines
- Restricted options
- Discriminated unions
- Safer APIs

**Interview Line**

A literal type represents a specific exact value such as `"loading"` or `1`, not the whole primitive category.

### Q. Difference between literal type and primitive type

**Answer:**

A primitive type represents a broad category of values.

Examples:

```ts
string;
number;
boolean;
```

A literal type represents one exact value.

**Example:**

```ts
let name: string = "John";
```

`name` can later hold any string.

But:

```ts
let role: "admin" = "admin";
```

can only hold:

```text
"admin"
```

Comparison:

| Primitive | Literal   |
| --------- | --------- |
| `string`  | `"admin"` |
| `number`  | `10`      |
| `boolean` | `true`    |

**Interview Line**

Primitive types describe a category of values, while literal types represent one exact value.

### Q. What is type widening?

**Answer:**

Type widening is when TypeScript generalizes a specific literal value into a broader type.

**Example:**

```ts
let status = "loading";
```

Because `status` can later change, TypeScript usually widens the type to:

```ts
string;
```

Another example:

```ts
let count = 1;
```

The type becomes:

```ts
number;
```

rather than the literal type:

```ts
1;
```

Widening makes mutable variables practical.

**Interview Line**

Type widening converts narrow literal values into broader types such as `string` or `number` when mutation is expected.

### Q. What is type narrowing vs type widening?

**Answer:**

They move types in opposite directions.

#### Widening

Makes a type broader.

```ts
"hello"
→ string
```

#### Narrowing

Makes a type more specific based on runtime checks or control flow.

**Example:**

```ts
function print(value: string | number) {
  if (typeof value === "string") {
    value.toUpperCase();
  }
}
```

Inside the `if`, TypeScript narrows:

```ts
string | number;
```

to:

```ts
string;
```

**Interview Line**

Widening broadens a type, while narrowing reduces a union to a more specific type through control-flow analysis.

### Q. What is `as const`?

**Answer:**

`as const` is a const assertion that tells TypeScript to keep values as narrow literal types and make object or array members readonly.

**Example:**

```ts
const config = {
  mode: "dark",
} as const;
```

Without `as const`, `mode` may be inferred as:

```ts
string;
```

With `as const`, it becomes:

```ts
"dark";
```

and the property is readonly.

**Interview Line**

`as const` preserves literal values as exact types and makes object properties or array elements readonly.

### Q. How does `as const` affect object and array types?

**Answer:**

For objects, `as const`:

- Preserves literal values
- Makes properties readonly

**Example:**

```ts
const user = {
  role: "admin",
} as const;
```

Type becomes conceptually:

```ts
{
  readonly role:
    "admin";
}
```

For arrays:

```ts
const colors = ["red", "blue"] as const;
```

Type becomes a readonly tuple:

```ts
readonly[("red", "blue")];
```

instead of:

```ts
string[]
```

**Interview Line**

`as const` turns object properties readonly and converts arrays into readonly literal tuples.

### Q. Difference between `let`, `const`, and `as const` in TypeScript

**Answer:**

They affect both reassignment and type inference.

#### `let`

Allows reassignment and usually widens literal values.

```ts
let mode = "dark";
```

Type:

```ts
string;
```

#### `const`

Prevents variable reassignment.

```ts
const mode = "dark";
```

Type is often inferred as:

```ts
"dark";
```

But object properties are still mutable:

```ts
const config = {
  mode: "dark",
};

config.mode = "light";
```

#### `as const`

Makes nested literal values readonly at the asserted level.

```ts
const config = {
  mode: "dark",
} as const;
```

Now `config.mode` is readonly and typed as `"dark"`.

**Interview Line**

`let` allows reassignment, `const` fixes the variable binding, and `as const` additionally preserves literal types and readonly members.

### Q. What is the difference between compile-time type checking and runtime validation?

**Answer:**

Compile-time type checking happens before the code runs.

TypeScript checks whether the source code is consistent with declared types.

**Example:**

```ts
const age: number = "25";
```

TypeScript reports an error during development.

Runtime validation happens while the application is actually executing.

**Example:**

```ts
const data = JSON.parse(apiResponse);
```

TypeScript cannot guarantee that `data` has the expected structure.

Runtime validation may be required using:

- Manual checks
- Zod
- Valibot
- Yup
- Custom validators

**Interview Line**

TypeScript checks types at compile time, while runtime validation verifies real values that enter the running application.

### Q. Does TypeScript provide runtime type safety?

**Answer:**

No.

TypeScript types are erased when code is compiled to JavaScript.

**Example:**

```ts
type User = {
  id: number;
};
```

The `User` type does not exist in the generated JavaScript.

Therefore, TypeScript cannot validate data arriving at runtime from:

- APIs
- LocalStorage
- User input
- JSON files
- External libraries

Runtime validation must be implemented separately where necessary.

**Interview Line**

TypeScript does not provide runtime type safety because its types are erased during compilation.

### Q. Why can TypeScript code still fail at runtime?

**Answer:**

TypeScript catches many type-related mistakes before execution, but it cannot guarantee that every runtime value matches the declared type.

Runtime failures can still come from:

- Invalid API responses
- `any`
- Type assertions
- Null or undefined values
- Network failures
- Browser APIs
- Incorrect business logic
- External JavaScript
- Runtime exceptions

**Example:**

```ts
const user = response as User;

console.log(user.name.toUpperCase());
```

If the API does not actually contain `name`, the code can still fail.

**Interview Line**

TypeScript reduces type errors but cannot prevent runtime failures caused by bad external data, unsafe assertions, or normal execution errors.

### Q. What are ambient declarations in TypeScript?

**Answer:**

Ambient declarations describe types for values that already exist at runtime but are defined somewhere else.

They tell TypeScript:

```text
This value exists.
Here is its type.
```

They commonly use:

```ts
declare;
```

**Example:**

```ts
declare const APP_VERSION: string;
```

TypeScript now understands `APP_VERSION`, even though it is created by some external script or build tool.

Ambient declarations do not generate JavaScript.

**Interview Line**

Ambient declarations describe externally existing runtime values to TypeScript without providing their implementation.

### Q. What is declaration file `.d.ts`?

**Answer:**

A declaration file is a TypeScript file ending in:

```text
.d.ts
```

It contains type declarations but no runtime implementation.

**Example:**

```ts
// math-library.d.ts

export function add(a: number, b: number): number;
```

This tells TypeScript how a JavaScript library behaves.

Declaration files are commonly used for:

- JavaScript packages
- Global variables
- Browser extensions
- Internal JavaScript modules
- Library publishing

**Interview Line**

A `.d.ts` file describes the type surface of JavaScript code without generating runtime code.

### Q. When do you need a declaration file?

**Answer:**

You need a declaration file when TypeScript cannot determine the types of existing JavaScript code or global runtime values.

Common cases include:

- A JavaScript library has no built-in types
- You are wrapping a legacy JavaScript module
- A global variable is injected externally
- You are publishing a library
- You need custom module declarations

**Example:**

```ts
declare module
  "*.svg" {
  const src: string;

  export default src;
}
```

This tells TypeScript how to handle imported SVG files.

For popular libraries, type declarations may already come from:

```text
@types/*
```

packages or be bundled with the library itself.

**Interview Line**

Use declaration files when TypeScript needs type information for JavaScript modules, globals, assets, or published library APIs.

## Interfaces & Types

### Q. What is the difference between `interface` and `type`?

**Answer:**

Definition

- `interface` → Used to define the structure of an object
- `type` → Used to define any type (primitive, union, object, etc.)

Key Differences

| Feature              | interface    | type               |
| -------------------- | ------------ | ------------------ |
| Object Definition    | ✅ Yes       | ✅ Yes             |
| Union / Intersection | ❌ No        | ✅ Yes             |
| Primitive Alias      | ❌ No        | ✅ Yes             |
| Extensibility        | `extends`    | `&` (intersection) |
| Declaration Merging  | ✅ Supported | ❌ Not supported   |

Example

```ts
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
```

**Interview Line**

`Interfaces` are mainly for object structures, while `types` are more flexible and can represent unions, primitives, and complex compositions.

### Q. Can interfaces extend multiple interfaces?

**Answer:**

Answer: ✅ Yes

Example

```ts
interface Person {
  name: string;
}

interface Employee {
  employeeId: number;
}

interface Manager extends Person, Employee {
  department: string;
}
```

Key Point

TypeScript supports multiple inheritance with `interfaces`

**Interview Line**

Yes, `interfaces` can extend multiple `interfaces`, allowing composition of multiple types into one.

### Q. What are optional properties in `interfaces`?

**Answer:**

Definition

Properties that are not required when creating an object

Syntax

Use `?` after property name

Example

```ts
interface User {
  name: string;
  age?: number;
}

const user1: User = {
  name: "Tanmay",
};
```

Use Cases

- API responses
- Partial data
- Forms

**Interview Line**

Optional properties allow flexibility by making certain fields non-mandatory using the `?` operator.

### Q. What is `readonly` in TypeScript?

**Answer:**

Definition

Prevents modification of a property after initialization

Example

```ts
interface User {
  readonly id: number;
  name: string;
}

const user: User = { id: 1, name: "Tanmay" };

// ❌ Error
user.id = 2;
```

Key Point

Ensures immutability

**Interview Line**

`readonly` ensures that a property cannot be changed after it is assigned, improving data safety.

### Q. Difference between type alias and interface in real-world usage

**Answer:**

When to Use Interface

- Object structures
- Class contracts
- Extendable APIs
- Large scalable apps

When to Use Type

- Unions (`string | number`)
- Intersections
- Utility types
- Complex transformations

Example

```ts
// Interface (best for objects)
interface User {
  name: string;
}

// Type (best for unions)
type Status = "success" | "error";
```

Practical Rule

👉 Use interface by default for objects

👉 Use type when you need flexibility

**Interview Line**

Interfaces are preferred for object contracts, while types are better for unions and complex type compositions.

### Q. How do you create index signatures?

**Answer:**

Definition

Used when you don’t know property names in advance

Syntax

```ts
interface Dictionary {
  [key: string]: string;
}
```

Example

```ts
interface UserRoles {
  [username: string]: string;
}

const roles: UserRoles = {
  Tanmay: "admin",
  Rahul: "user",
};
```

Key Points

- Key type → `string`, `number`, or `symbol`
- Value type → defined by you

Advanced Example

```ts
interface ApiResponse {
  [key: string]: string | number;
}
```

**Interview Line**

Index signatures allow dynamic object keys with predefined value types, useful for dictionaries or API responses.

### Final Summary

- interface vs type → flexibility vs structure
- multiple inheritance → interfaces support it
- optional + readonly → control object behavior
- index signatures → dynamic keys

### Q. What is declaration merging in TypeScript?

**Answer:**

Declaration merging is a TypeScript feature where multiple declarations with the same name are combined into one type definition.

It commonly works with interfaces.

**Example:**

```ts
interface User {
  name: string;
}

interface User {
  age: number;
}
```

TypeScript merges them into:

```ts
interface User {
  name: string;
  age: number;
}
```

Usage:

```ts
const user: User = {
  name: "John",
  age: 30,
};
```

Declaration merging is useful for extending existing type definitions without editing the original declaration.

**Interview Line**

Declaration merging combines compatible declarations with the same name into one final type definition.

### Q. Why does declaration merging work with interfaces but not type aliases?

**Answer:**

Interfaces are designed as open declarations that can be extended or merged later.

Type aliases are closed aliases.

**Interface Example:**

```ts
interface User {
  name: string;
}

interface User {
  age: number;
}
```

This is valid.

With type aliases:

```ts
type User = {
  name: string;
};

type User = {
  age: number;
};
```

TypeScript reports a duplicate identifier error.

If you need to combine type aliases, use an intersection:

```ts
type User = UserName & UserAge;
```

**Interview Line**

Interfaces are open and support declaration merging, while type aliases are fixed definitions and must be combined explicitly.

### Q. What is interface augmentation?

**Answer:**

Interface augmentation means extending an existing interface by declaring additional members for it.

This is often used when existing type definitions need extra properties.

**Example:**

```ts
interface Window {
  appVersion: string;
}
```

Now TypeScript understands:

```ts
window.appVersion;
```

This works because the built-in `Window` interface can be augmented.

**Interview Line**

Interface augmentation adds new members to an existing interface without modifying its original declaration.

### Q. How do you extend third-party library types?

**Answer:**

Third-party library types can often be extended through module augmentation.

Suppose a library exports:

```ts
interface User {
  id: string;
}
```

You can augment it:

```ts
declare module "some-library" {
  interface User {
    role: string;
  }
}
```

After augmentation, `User` includes both:

```text
id
role
```

This is useful when:

- A plugin adds runtime properties
- Your framework extends a library object
- Library typings are incomplete for your setup

The runtime implementation must actually provide the property.

**Interview Line**

Extend third-party types with module augmentation when runtime behavior adds members that the original library typings do not describe.

### Q. What is module augmentation?

**Answer:**

Module augmentation lets you add declarations to an existing module.

**Example:**

```ts
import "express";

declare module "express" {
  interface Request {
    userId?: string;
  }
}
```

Now code using the Express request type can access:

```ts
req.userId;
```

Module augmentation changes only TypeScript's type information.

It does not add the property at runtime.

Your application must still assign it.

**Interview Line**

Module augmentation extends the type declarations of an existing module without changing its runtime implementation.

### Q. What is global type augmentation?

**Answer:**

Global augmentation adds or extends types in the global namespace.

This is useful for values available globally in the runtime environment.

**Example:**

```ts
export {};

declare global {
  interface Window {
    analyticsId: string;
  }
}
```

Now:

```ts
window.analyticsId;
```

is recognized by TypeScript.

The `export {}` makes the file a module, which allows the `declare global` block to augment global declarations safely.

**Interview Line**

Global augmentation extends globally available types such as `Window`, `NodeJS`, or other environment-wide interfaces.

### Q. What is the difference between extending an interface and intersecting types?

**Answer:**

Both combine type shapes, but they behave differently.

#### Interface extension

```ts
interface Base {
  id: string;
}

interface User extends Base {
  name: string;
}
```

This creates an explicit inheritance-like relationship.

#### Type intersection

```ts
type Base = {
  id: string;
};

type User = Base & {
  name: string;
};
```

Intersections are more flexible because they can combine unions and other type expressions.

Interfaces often give clearer errors for object hierarchies.

**Interview Line**

Interface extension builds an explicit object-type hierarchy, while intersections combine arbitrary type expressions more flexibly.

### Q. Can type intersections produce unexpected results?

**Answer:**

Yes.

Intersections require a value to satisfy all intersected types at the same time.

This can create impossible property types.

**Example:**

```ts
type A = {
  id: string;
};

type B = {
  id: number;
};

type C = A & B;
```

Now `id` must satisfy both:

```text
string
and
number
```

which results in:

```ts
never;
```

This can make the resulting type impossible to construct.

**Interview Line**

Intersections can produce impossible types when the combined members conflict with each other.

### Q. What happens when two intersected types have the same property with different types?

**Answer:**

The property becomes the intersection of those property types.

**Example:**

```ts
type A = {
  value: string;
};

type B = {
  value: number;
};

type C = A & B;
```

The resulting property is effectively:

```ts
value: string & number;
```

which becomes:

```ts
never;
```

So this is impossible:

```ts
const value: C = {
  value: ???
};
```

No normal value can be both a string and a number.

**Interview Line**

Conflicting properties in an intersection are intersected themselves, often producing `never`.

### Q. How do you make only some properties optional?

**Answer:**

Combine `Pick`, `Partial`, and `Omit`.

**Example:**

```ts
type User = {
  id: number;
  name: string;
  email: string;
};
```

Make only `email` optional:

```ts
type UserWithOptionalEmail = Omit<User, "email"> & Partial<Pick<User, "email">>;
```

Result:

```ts
{
  id: number;
  name: string;
  email?: string;
}
```

You can also create a reusable utility type.

**Interview Line**

Make selected properties optional by combining `Omit` with `Partial<Pick<...>>`.

### Q. How do you make only some properties readonly?

**Answer:**

Combine `Pick`, `Readonly`, and `Omit`.

**Example:**

```ts
type User = {
  id: number;
  name: string;
  email: string;
};
```

Make only `id` readonly:

```ts
type UserWithReadonlyId = Omit<User, "id"> & Readonly<Pick<User, "id">>;
```

Result conceptually:

```ts
{
  readonly id:
    number;
  name: string;
  email: string;
}
```

**Interview Line**

Make selected properties readonly by combining `Omit` with `Readonly<Pick<...>>`.

### Q. How do you create a type from object keys?

**Answer:**

Use `keyof`.

**Example:**

```ts
type User = {
  id: number;
  name: string;
  email: string;
};
```

Then:

```ts
type UserKey = keyof User;
```

Result:

```ts
"id" | "name" | "email";
```

This is useful for:

- Dynamic property access
- Generic utilities
- Safe field names

**Interview Line**

Use `keyof` to create a union of all property keys from an object type.

### Q. How do you create a type from object values?

**Answer:**

Use indexed access with `keyof typeof`.

**Example:**

```ts
const status = {
  idle: "IDLE",
  loading: "LOADING",
  success: "SUCCESS",
} as const;
```

Create a union of values:

```ts
type StatusValue = (typeof status)[keyof typeof status];
```

Result:

```ts
"IDLE" | "LOADING" | "SUCCESS";
```

**Interview Line**

Create a union of object values with `typeof Object[keyof typeof Object]`.

### Q. How do you create a union from an array?

**Answer:**

Use `as const` and indexed access with `number`.

**Example:**

```ts
const roles = ["admin", "editor", "viewer"] as const;
```

Then:

```ts
type Role = (typeof roles)[number];
```

Result:

```ts
"admin" | "editor" | "viewer";
```

Without `as const`, the array would usually widen to:

```ts
string[]
```

and the resulting type would simply be `string`.

**Interview Line**

Use `as const` with `typeof array[number]` to create a union from array values.

### Q. What is `keyof typeof`?

**Answer:**

`typeof` gets the type of a runtime value.

`keyof` then extracts the keys of that type.

**Example:**

```ts
const routes = {
  home: "/",
  profile: "/profile",
  admin: "/admin",
};
```

Then:

```ts
type RouteName = keyof typeof routes;
```

Result:

```ts
"home" | "profile" | "admin";
```

This is useful when you want the runtime object to be the source of truth and derive types from it.

**Interview Line**

`keyof typeof` creates a union of keys from an existing runtime object.

### Q. Difference between `keyof` and `typeof`

**Answer:**

They operate on different things.

#### `typeof`

Gets the TypeScript type of a runtime value.

```ts
const user = {
  name: "John",
};

type User = typeof user;
```

#### `keyof`

Gets the property keys of a type.

```ts
type UserKey = keyof User;
```

Result:

```ts
"name";
```

They are often combined:

```ts
keyof typeof user
```

**Interview Line**

`typeof` derives a type from a value, while `keyof` derives a key union from a type.

### Q. What is an indexed access type?

**Answer:**

An indexed access type extracts the type of a property from another type.

**Example:**

```ts
type User = {
  id: number;
  name: string;
};
```

Access the `name` type:

```ts
type Name = User["name"];
```

Result:

```ts
string;
```

You can also access multiple properties:

```ts
type Value = User["id" | "name"];
```

Result:

```ts
number | string;
```

**Interview Line**

Indexed access types use `Type["key"]` syntax to extract property types from existing types.

### Q. How do you access nested property types?

**Answer:**

Chain indexed access types.

**Example:**

```ts
type User = {
  profile: {
    address: {
      city: string;
    };
  };
};
```

Access the city type:

```ts
type City = User["profile"]["address"]["city"];
```

Result:

```ts
string;
```

This keeps nested type definitions connected to the original source type.

**Interview Line**

Access nested property types by chaining indexed access expressions through the nested object structure.

### Q. What is a recursive type?

**Answer:**

A recursive type references itself directly or indirectly.

It is useful for hierarchical or nested data.

**Example:**

```ts
type TreeNode = {
  value: string;
  children: TreeNode[];
};
```

Another example:

```ts
type JsonValue =
  | string
  | number
  | boolean
  | null
  | JsonValue[]
  | {
      [key: string]: JsonValue;
    };
```

Recursive types are useful for:

- Trees
- Nested menus
- JSON structures
- File systems
- Comment threads

**Interview Line**

A recursive type references itself and is useful for modeling naturally nested or hierarchical data.

### Q. When should recursive types be avoided?

**Answer:**

Avoid recursive types when they add complexity without providing real modeling value.

Problems can include:

- Hard-to-read types
- Slow type checking
- Deep instantiation errors
- Difficult debugging
- Overly complex generic recursion

For example, a deeply recursive utility type may trigger errors such as:

```text
Type instantiation is excessively deep
```

If the data structure has a practical maximum depth, a simpler bounded type may be easier to maintain.

**Interview Line**

Avoid recursive types when they make the type system harder to understand, slower to evaluate, or more complex than the domain requires.

## Functions & Generics

### Q. How do you define types for functions in TypeScript?

**Answer:**

Definition

In TypeScript, you can define types for:

- Parameters
- Return value

Syntax

```ts
function functionName(param: type): returnType {
  return value;
}
```

Example

```ts
function add(a: number, b: number): number {
  return a + b;
}
```

Function Type (Variable)

```ts
let multiply: (a: number, b: number) => number;

multiply = (x, y) => x * y;
```

Key

- Parameters and return types improve safety
- Helps avoid runtime errors

**Interview Line**

Function types in TypeScript define both parameter types and return types to ensure type safety.

### Q. What are optional and default parameters?

**Answer:**

Optional Parameters

- Marked using `?`
- Not required while calling function

```ts
function greet(name: string, age?: number) {
  return `Hello ${name}`;
}
```

Default Parameters

- Assign default value
- Used when argument is not provided

```ts
function greet(name: string, age: number = 25) {
  return `Hello ${name}, age ${age}`;
}
```

Key Difference

| Feature       | Optional | Default |
| ------------- | -------- | ------- |
| Required      | ❌ No    | ❌ No   |
| Default Value | ❌ No    | ✅ Yes  |

**Interview Line**

Optional parameters are not required, while default parameters automatically assign a value if none is provided.

### Q. What are generics? Why are they useful?

**Answer:**

Definition

- Generics allow you to write reusable, flexible, type-safe code

Problem Without Generics

```ts
function identity(value: any): any {
  return value;
}
```

❌ Loses type safety

With Generics

```ts
function identity<T>(value: T): T {
  return value;
}
```

Benefits

- Reusability ✅
- Type safety ✅
- Better IntelliSense ✅
- Avoids `any` ✅

**Interview Line**

Generics allow writing reusable components that maintain type safety across different data types.

### Q. Example of generic function

**Answer:**

Basic Example

```ts
function getValue<T>(value: T): T {
  return value;
}

getValue<string>("Hello");
getValue<number>(10);
```

Generic with Arrays

```ts
function getFirstElement<T>(arr: T[]): T {
  return arr[0];
}
```

Key Insight

Type is decided at runtime usage (but checked at compile time)

**Interview Line**

A generic function adapts to different types while preserving type information.

### Q. What are generic constraints?

**Answer:**

Definition

Restrict generic types using `extends`

Example

```ts
function getLength<T extends { length: number }>(item: T): number {
  return item.length;
}
```

Usage

```ts
getLength("Hello"); // ✅ string has length
getLength([1, 2, 3]); // ✅ array has length
getLength(10); // ❌ number doesn't have
```

Why

- Prevent invalid operations
- Add type safety to generics

**Interview Line**

Generic constraints restrict types to ensure only valid operations are performed.

### Q. Difference between `T extends object` vs `T extends {}`

**Answer:**

Key Difference

| Feature            | `T extends object` | `T extends {}` |
| ------------------ | ------------------ | -------------- |
| Accepts primitives | ❌ No              | ✅ Yes         |
| Accepts objects    | ✅ Yes             | ✅ Yes         |
| Strictness         | More strict        | Less strict    |

Explanation

✅ `T extends object`

```ts
function test<T extends object>(val: T) {}

test({}); // ✅
test(10); // ❌
```

✅ `T extends {}`

```ts
function test<T extends {}>(val: T) {}

test({}); // ✅
test(10); // ✅
```

Important Insight

- `{}` means any non-null/undefined value
- `object` means only non-primitive objects

**Interview Line**

`T extends object` restricts to non-primitive types, while `T extends {}` allows any non-nullish value, including primitives.

### Q. What is function overload in TypeScript?

**Answer:**

Function overloads let one function expose multiple valid call signatures while using a single implementation.

This is useful when the function behaves differently depending on the types or number of arguments.

**Example:**

```ts
function format(value: string): string;

function format(value: number): string;

function format(value: string | number): string {
  return String(value);
}
```

Valid calls:

```ts
format("hello");
format(123);
```

The overload signatures define how callers can use the function.

The final function contains the implementation.

**Interview Line**

Function overloads let one TypeScript function expose multiple type-safe call signatures with a single implementation.

### Q. How do you write function overloads?

**Answer:**

Write one or more overload signatures first, followed by one implementation signature.

**Example:**

```ts
function getValue(id: number): string;

function getValue(key: string): number;

function getValue(input: number | string): string | number {
  if (typeof input === "number") {
    return "User";
  }

  return 100;
}
```

Only the overload signatures are exposed to callers.

The implementation signature must be broad enough to support every overload.

**Interview Line**

Function overloads are written as multiple call signatures followed by one compatible implementation.

### Q. Function overloads vs union parameters: which one should you use?

**Answer:**

Use union parameters when all supported inputs follow roughly the same behavior and return type.

**Example:**

```ts
function print(value: string | number) {
  console.log(value);
}
```

Use overloads when different inputs produce different return types or distinct call signatures.

**Example:**

```ts
function parse(value: string): number;

function parse(value: number): string;
```

A union may lose the precise relationship between each input type and its corresponding return type.

**Interview Line**

Prefer unions for simple shared behavior, and overloads when inputs need distinct call signatures or return types.

### Q. What is generic default type parameter?

**Answer:**

A generic default type parameter provides a fallback type when the caller does not explicitly supply one.

**Example:**

```ts
type ApiResponse<T = unknown> = {
  data: T;
  success: boolean;
};
```

Usage:

```ts
type DefaultResponse = ApiResponse;
```

Here `T` defaults to:

```ts
unknown;
```

It can still be overridden:

```ts
type UserResponse = ApiResponse<User>;
```

**Interview Line**

A generic default type parameter provides a fallback type when no explicit generic argument is supplied.

### Q. How do you provide default values for generic types?

**Answer:**

Use `=` in the generic parameter declaration.

**Example:**

```ts
type Result<T = string> = {
  value: T;
};
```

For functions:

```ts
function createState<T = string>(value: T) {
  return value;
}
```

Defaults are useful when one generic type is common but consumers should still be able to customize it.

**Interview Line**

Provide default generic types with syntax such as `T = SomeType`.

### Q. What are multiple generic parameters?

**Answer:**

A generic function, type, interface, or class can accept multiple generic type parameters.

**Example:**

```ts
function pair<T, U>(first: T, second: U): [T, U] {
  return [first, second];
}
```

Usage:

```ts
const result = pair("age", 30);
```

TypeScript infers:

```ts
[string, number];
```

**Interview Line**

Multiple generic parameters let one reusable API preserve relationships between several independent types.

### Q. How do you constrain one generic based on another generic?

**Answer:**

Use `extends` to restrict one generic parameter based on another.

**Example:**

```ts
function getProperty<T, K extends keyof T>(obj: T, key: K) {
  return obj[key];
}
```

Here `K` can only be a valid key from `T`.

**Interview Line**

Use constraints such as `K extends keyof T` to ensure one generic is valid relative to another.

### Q. What does `K extends keyof T` mean?

**Answer:**

It means generic type `K` must be one of the property keys of type `T`.

**Example:**

```ts
type User = {
  id: number;
  name: string;
};
```

Then:

```ts
keyof User
```

produces:

```ts
"id" | "name";
```

Therefore `K extends keyof User` means `K` must be either `"id"` or `"name"`.

**Interview Line**

`K extends keyof T` restricts `K` to valid property keys of `T`.

### Q. How do you write a type-safe `getProperty` function?

**Answer:**

Use generics with `keyof` and indexed access.

**Example:**

```ts
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}
```

Usage:

```ts
const user = {
  id: 1,
  name: "John",
};

const name = getProperty(user, "name");
```

`name` is inferred as:

```ts
string;
```

Invalid keys are rejected.

**Interview Line**

A type-safe `getProperty` uses `K extends keyof T` and returns `T[K]`.

### Q. How do you write a type-safe `setProperty` function?

**Answer:**

Use `keyof` and indexed access so the value type matches the selected property.

**Example:**

```ts
function setProperty<T, K extends keyof T>(obj: T, key: K, value: T[K]): void {
  obj[key] = value;
}
```

Usage:

```ts
const user = {
  id: 1,
  name: "John",
};

setProperty(user, "name", "Mike");
```

This is valid.

But:

```ts
setProperty(user, "id", "wrong");
```

is rejected because `id` requires a number.

**Interview Line**

A type-safe `setProperty` uses `T[K]` so the assigned value must match the selected property's type.

### Q. What is generic interface?

**Answer:**

A generic interface accepts type parameters so the same interface can describe different data types.

**Example:**

```ts
interface ApiResponse<T> {
  data: T;
  success: boolean;
}
```

Usage:

```ts
type UserResponse = ApiResponse<User>;

type ProductResponse = ApiResponse<Product>;
```

**Interview Line**

A generic interface defines a reusable object contract whose member types vary through type parameters.

### Q. What is generic type alias?

**Answer:**

A generic type alias is a reusable type expression that accepts type parameters.

**Example:**

```ts
type ApiResult<T> = {
  data: T;
  error: string | null;
};
```

Usage:

```ts
type UserResult = ApiResult<User>;
```

Type aliases can represent:

- Objects
- Unions
- Intersections
- Tuples
- Conditional types

**Interview Line**

A generic type alias creates reusable type expressions parameterized by one or more types.

### Q. What is generic class?

**Answer:**

A generic class accepts type parameters so its properties and methods can work with different types safely.

**Example:**

```ts
class Box<T> {
  constructor(public value: T) {}

  getValue(): T {
    return this.value;
  }
}
```

Usage:

```ts
const numberBox = new Box<number>(10);

const stringBox = new Box<string>("Hello");
```

**Interview Line**

A generic class preserves type safety while allowing one class implementation to work with multiple data types.

### Q. How do generics improve reusable API utilities?

**Answer:**

Generics preserve type information instead of falling back to broad types such as `any`.

Without generics:

```ts
function wrap(value: any) {
  return {
    data: value,
  };
}
```

The returned type loses useful information.

With generics:

```ts
function wrap<T>(value: T) {
  return {
    data: value,
  };
}
```

Now:

```ts
const result = wrap("hello");
```

preserves:

```ts
{
  data: string;
}
```

**Interview Line**

Generics make reusable utilities type-safe by preserving the specific types passed into them.

### Q. How do you infer generic types automatically?

**Answer:**

TypeScript usually infers generic types from function arguments.

**Example:**

```ts
function identity<T>(value: T): T {
  return value;
}
```

Usage:

```ts
const result = identity("hello");
```

TypeScript infers:

```ts
T = string;
```

No explicit generic argument is required.

**Interview Line**

TypeScript infers generic types automatically from values and arguments passed to generic APIs.

### Q. When should you explicitly pass generic types?

**Answer:**

Pass generic types explicitly when inference is impossible, too broad, or different from the intended type.

**Example:**

```ts
const [user, setUser] = useState<User | null>(null);
```

TypeScript cannot infer `User` from `null`.

Another example:

```ts
fetchData<User>("/api/user");
```

Do not specify generics unnecessarily when inference is already precise.

**Interview Line**

Pass generics explicitly when TypeScript lacks enough information or would infer a broader or unintended type.

### Q. What is generic type inference limitation?

**Answer:**

Generic inference depends on the information available at the call site.

TypeScript cannot always infer the intended type.

**Example:**

```ts
function createValue<T>(): T {
  throw new Error();
}
```

There is no argument from which `T` can be inferred.

So the caller must provide it:

```ts
createValue<User>();
```

Inference can also become too broad when:

- Inputs are unions
- Generic relationships conflict
- Values have already widened
- The return type is the only clue

**Interview Line**

Generic inference is limited when there is not enough input information for TypeScript to determine the intended type precisely.

### Q. What is a higher-order function type?

**Answer:**

A higher-order function either accepts another function, returns another function, or both.

**Example:**

```ts
type Callback = (value: number) => string;

function run(callback: Callback) {
  return callback(10);
}
```

Another example:

```ts
function createLogger() {
  return (message: string) => {
    console.log(message);
  };
}
```

**Interview Line**

A higher-order function accepts or returns functions and can be typed with function signatures or generic function types.

### Q. How do you type a function that accepts another function?

**Answer:**

Define the callback signature as a parameter type.

**Example:**

```ts
function processValue(value: number, callback: (value: number) => string): string {
  return callback(value);
}
```

Usage:

```ts
processValue(10, (value) => value.toString());
```

You can also extract the callback type:

```ts
type Formatter = (value: number) => string;
```

**Interview Line**

Type callback parameters with a function signature describing their arguments and return type.

### Q. How do you type a function that returns another function?

**Answer:**

Use a function signature as the return type.

**Example:**

```ts
function multiplier(factor: number): (value: number) => number {
  return (value: number) => value * factor;
}
```

Usage:

```ts
const double = multiplier(2);

double(10);
```

Result:

```text
20
```

**Interview Line**

Type a function-returning function by using another function signature as its return type.

### Q. How do you type rest parameters?

**Answer:**

Rest parameters are usually typed as arrays or tuples.

**Example with array:**

```ts
function sum(...values: number[]): number {
  return values.reduce((total, value) => total + value, 0);
}
```

Usage:

```ts
sum(1, 2, 3);
```

For a fixed positional pattern:

```ts
function log(...args: [string, number]) {}
```

**Interview Line**

Type rest parameters with arrays for variable arguments or tuples for fixed positional argument patterns.

### Q. How do you type destructured function parameters?

**Answer:**

Define an object type and apply it to the destructured parameter.

**Example:**

```ts
type UserOptions = {
  name: string;
  age?: number;
};

function createUser({ name, age }: UserOptions) {
  return {
    name,
    age,
  };
}
```

You can also type inline:

```ts
function createUser({ name }: { name: string }) {}
```

Named types are usually cleaner for reusable APIs.

**Interview Line**

Type destructured parameters by applying an object type to the entire destructured parameter.

### Q. How do you type async functions?

**Answer:**

Async functions always return a `Promise`.

The return type should therefore be:

```ts
Promise<T>;
```

**Example:**

```ts
type User = {
  id: number;
  name: string;
};

async function fetchUser(id: number): Promise<User> {
  const response = await fetch(`/api/users/${id}`);

  if (!response.ok) {
    throw new Error("Request failed");
  }

  return response.json();
}
```

For an async function with no returned value:

```ts
async function logData(): Promise<void> {
  console.log("done");
}
```

**Interview Line**

Async functions return `Promise<T>`, where `T` is the type of the resolved value.

## Advanced Types

### Q. What are union and intersection types?

**Answer:**

Union Types (`|`)

✅ Definition

Allows a variable to hold multiple possible types

Example

```ts
let value: string | number;

value = "Hello"; // ✅
value = 10; // ✅
```

Key Point

- You can only access common properties

Intersection Types (`&`)

✅ Definition

Combines multiple types into one

Example

```ts
type A = { name: string };
type B = { age: number };

type Person = A & B;

const user: Person = {
  name: "Tanmay",
  age: 25,
};
```

Key Point

Must satisfy all types

**Interview Line**

Union types allow multiple possible types, while intersection types combine multiple types into one.

### Q. What is type narrowing?

**Answer:**

Definition

Process of refining a broad type into a specific type

Example

```ts
function print(value: string | number) {
  if (typeof value === "string") {
    console.log(value.toUpperCase()); // narrowed to string
  }
}
```

Why Important

- Enables safe operations
- Prevents runtime errors

**Interview Line**

Type narrowing refines a union type into a more specific type using checks like `typeof` or conditions.

### Q. Explain type guards (`typeof`, `instanceof`, custom guards)

**Answer:**

Definition

Techniques used to narrow types safely

1. `typeof` Guard

```ts
function check(value: string | number) {
  if (typeof value === "string") {
    return value.length;
  }
}
```

2. `instanceof` Guard

```ts
class Animal {}
class Dog extends Animal {}

function check(animal: Animal) {
  if (animal instanceof Dog) {
    console.log("Dog detected");
  }
}
```

3. Custom Type Guard

```ts
type User = { name: string };

function isUser(obj: any): obj is User {
  return obj && typeof obj.name === "string";
}
```

Key Insight

Custom guards use `obj is Type`

**Interview Line**

Type guards are techniques to narrow types safely using `typeof`, `instanceof`, or custom predicates.

### Q. What is discriminated union?

**Answer:**

Definition

A union type with a common literal property (discriminator)

Example

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

Key Points

- Uses a common field (`kind`)
- Helps TypeScript automatically narrow types

**Interview Line**

Discriminated unions use a common property to differentiate types and enable automatic type narrowing.

### Q. What are mapped types?

**Answer:**

Definition

Create new types by transforming existing types

Syntax

```ts
type NewType = {
  [Key in keyof OldType]: OldType[Key];
};
```

Example

```ts
type User = {
  name: string;
  age: number;
};

type ReadOnlyUser = {
  readonly [K in keyof User]: User[K];
};
```

Built-in Examples

- `Partial<T>`
- `Readonly<T>`
- `Pick<T, K>`

**Interview Line**

Mapped types transform existing types by iterating over their keys.

### Q. What are conditional types?

**Answer:**

Definition

Types that depend on a condition

Syntax

```ts
type Result<T> = T extends string ? string : number;
```

Example

```ts
type Check<T> = T extends number ? "Number" : "Other";

type A = Check<number>; // "Number"
type B = Check<string>; // "Other"
```

Advanced Example

```ts
type NonNullable<T> = T extends null | undefined ? never : T;
```

Key Insight

Works like ternary operator for types

**Interview Line**

Conditional types allow type logic using conditions, similar to a ternary operator.

### Q. what is Typescript helper ?

**Answer:**

A TypeScript helper is a reusable type utility that transforms, extracts, combines, or constrains other types.

Some helpers are built into TypeScript.

Common examples include:

```ts
Partial<T>;
Required<T>;
Readonly<T>;
Pick<T, K>;
Omit<T, K>;
Record<K, T>;
ReturnType<T>;
Parameters<T>;
Awaited<T>;
```

You can also create custom helper types.

**Example:**

```ts
type Nullable<T> = T | null;
```

Usage:

```ts
type UserOrNull = Nullable<User>;
```

Helper types reduce repetition and make advanced type logic reusable.

**Interview Line**

TypeScript helper types are reusable type utilities that transform or derive new types from existing ones.

### Q. What is template literal type?

**Answer:**

A template literal type creates string literal types using syntax similar to JavaScript template strings.

**Example:**

```ts
type Size = "sm" | "md" | "lg";

type ClassName = `btn-${Size}`;
```

Result:

```ts
"btn-sm" | "btn-md" | "btn-lg";
```

Template literal types work at compile time.

They are useful for generating type-safe string patterns.

**Interview Line**

Template literal types build new string literal unions from existing literal types.

### Q. How are template literal types useful?

**Answer:**

They are useful when valid strings follow a predictable pattern.

Common use cases include:

- Event names
- CSS-like variants
- Route names
- API method names
- Getter/setter names
- Localization keys

**Example:**

```ts
type EventName = "click" | "change";

type HandlerName = `on${Capitalize<EventName>}`;
```

Result:

```ts
"onClick" | "onChange";
```

**Interview Line**

Template literal types make patterned string APIs type-safe without manually writing every string combination.

### Q. How do you create dynamic string union types?

**Answer:**

Combine unions with template literal types.

**Example:**

```ts
type Entity = "user" | "order";

type Action = "create" | "delete";

type Permission = `${Action}:${Entity}`;
```

Result:

```ts
"create:user" | "create:order" | "delete:user" | "delete:order";
```

**Interview Line**

Dynamic string unions are created by combining literal unions inside template literal types.

### Q. What is `infer` keyword in TypeScript?

**Answer:**

`infer` lets TypeScript capture part of a type inside a conditional type.

It is commonly used to extract inner types.

**Example:**

```ts
type ReturnTypeOf<T> = T extends (...args: any[]) => infer R ? R : never;
```

For:

```ts
type Fn = () => string;
```

Result:

```ts
ReturnTypeOf<Fn>;
```

becomes:

```ts
string;
```

**Interview Line**

`infer` captures a type inside a conditional type so that inner type information can be extracted and reused.

### Q. How does `infer` work inside conditional types?

**Answer:**

`infer` declares a temporary type variable while matching a type pattern.

**Example:**

```ts
type ElementType<T> = T extends Array<infer U> ? U : T;
```

For:

```ts
type A = ElementType<string[]>;
```

TypeScript infers:

```ts
U = string;
```

So `A` becomes:

```ts
string;
```

**Interview Line**

Inside a conditional type, `infer` extracts the part of a matching type and binds it to a temporary type variable.

### Q. How do you extract array element type using `infer`?

**Answer:**

Match the array shape and infer its element type.

**Example:**

```ts
type ArrayElement<T> = T extends readonly (infer U)[] ? U : never;
```

Usage:

```ts
type Item = ArrayElement<number[]>;
```

Result:

```ts
number;
```

**Interview Line**

Extract an array element type by matching `T` against an array pattern containing `infer U`.

### Q. How do you extract Promise resolved type using `infer`?

**Answer:**

Match the type against `Promise<infer U>`.

**Example:**

```ts
type PromiseValue<T> = T extends Promise<infer U> ? U : T;
```

Usage:

```ts
type Result = PromiseValue<Promise<User>>;
```

Result:

```ts
User;
```

TypeScript also provides:

```ts
Awaited<T>;
```

for more complete Promise-like unwrapping.

**Interview Line**

Extract a Promise's resolved type with `Promise<infer U>` or use `Awaited<T>`.

### Q. What is distributive conditional type?

**Answer:**

A distributive conditional type applies the conditional separately to each member of a union.

**Example:**

```ts
type ToArray<T> = T extends any ? T[] : never;
```

For:

```ts
type Result = ToArray<string | number>;
```

Result:

```ts
string[]
|
number[]
```

**Interview Line**

A distributive conditional type evaluates each member of a union independently.

### Q. When do conditional types distribute over unions?

**Answer:**

Distribution happens when the checked type is a naked generic type parameter.

**Example:**

```ts
type Check<T> = T extends string ? "yes" : "no";
```

For:

```ts
Check<string | number>;
```

TypeScript evaluates each union member separately.

Result:

```ts
"yes" | "no";
```

**Interview Line**

Conditional types distribute when the checked side is a naked generic type parameter such as `T extends ...`.

### Q. How do you prevent distributive conditional behavior?

**Answer:**

Wrap the checked type in a tuple.

**Example:**

```ts
type Check<T> = [T] extends [string] ? "yes" : "no";
```

Now:

```ts
type Result = Check<string | number>;
```

is checked as a whole union instead of distributing.

**Interview Line**

Prevent conditional distribution by wrapping both sides of the `extends` check in tuples.

### Q. What is recursive conditional type?

**Answer:**

A recursive conditional type calls itself while progressively transforming or unwrapping a type.

**Example:**

```ts
type DeepUnwrap<T> = T extends Promise<infer U> ? DeepUnwrap<U> : T;
```

For:

```ts
type Result = DeepUnwrap<Promise<Promise<string>>>;
```

Result:

```ts
string;
```

**Interview Line**

A recursive conditional type repeatedly applies type logic until a base type is reached.

### Q. What is key remapping in mapped types?

**Answer:**

Key remapping lets a mapped type transform property names using the `as` clause.

**Example:**

```ts
type Getters<T> = {
  [K in keyof T as `get${Capitalize<string & K>}`]: () => T[K];
};
```

For:

```ts
type User = {
  name: string;
  age: number;
};
```

Result:

```ts
{
  getName: () => string;
  getAge: () => number;
}
```

**Interview Line**

Key remapping uses the mapped-type `as` clause to rename, transform, or remove keys.

### Q. How do you rename keys using mapped types?

**Answer:**

Use key remapping with `as`.

**Example:**

```ts
type PrefixKeys<T> = {
  [K in keyof T as `app_${string & K}`]: T[K];
};
```

For:

```ts
type Config = {
  theme: string;
  mode: string;
};
```

Result:

```ts
{
  app_theme: string;
  app_mode: string;
}
```

**Interview Line**

Rename mapped-type keys by producing a new key expression after the `as` keyword.

### Q. How do you remove keys using mapped types?

**Answer:**

Remap unwanted keys to `never`.

**Example:**

```ts
type RemoveId<T> = {
  [K in keyof T as K extends "id" ? never : K]: T[K];
};
```

For:

```ts
type User = {
  id: number;
  name: string;
};
```

Result:

```ts
{
  name: string;
}
```

**Interview Line**

Remove mapped-type keys by remapping those keys to `never`.

### Q. How do you filter keys by value type?

**Answer:**

Use a mapped type to keep keys whose value type matches a target type.

**Example:**

```ts
type KeysOfType<T, V> = {
  [K in keyof T]: T[K] extends V ? K : never;
}[keyof T];
```

Usage:

```ts
type User = {
  id: number;
  name: string;
  active: boolean;
};
```

```ts
type StringKeys = KeysOfType<User, string>;
```

Result:

```ts
"name";
```

**Interview Line**

Filter keys by value type by mapping each property to its key or `never`, then indexing the mapped type.

### Q. What are modifier operators in mapped types?

**Answer:**

Mapped types can add or remove property modifiers.

Main modifiers include:

```text
readonly
-readonly
?
-?
```

**Example:**

```ts
type Mutable<T> = {
  -readonly [K in keyof T]: T[K];
};
```

Another example:

```ts
type RequiredProps<T> = {
  [K in keyof T]-?: T[K];
};
```

**Interview Line**

Mapped-type modifier operators add or remove `readonly` and optional property modifiers.

### Q. Difference between `readonly`, `-readonly`, `?`, and `-?` in mapped types

**Answer:**

These operators control property modifiers.

#### `readonly`

Adds readonly.

```ts
type ReadonlyType<T> = {
  readonly [K in keyof T]: T[K];
};
```

#### `-readonly`

Removes readonly.

```ts
type Mutable<T> = {
  -readonly [K in keyof T]: T[K];
};
```

#### `?`

Makes properties optional.

```ts
type Optional<T> = {
  [K in keyof T]?: T[K];
};
```

#### `-?`

Removes optionality.

```ts
type RequiredType<T> = {
  [K in keyof T]-?: T[K];
};
```

**Interview Line**

`readonly` and `?` add modifiers, while `-readonly` and `-?` remove them.

### Q. What is branded type?

**Answer:**

A branded type adds an artificial marker to a primitive or structural type to create nominal-like type safety.

**Example:**

```ts
type UserId = string & {
  readonly __brand: "UserId";
};
```

Now a normal string is not automatically treated as `UserId`.

**Interview Line**

A branded type adds a compile-time marker to create nominal-like distinctions between structurally identical values.

### Q. Why are branded types useful?

**Answer:**

They prevent accidentally mixing values that share the same primitive type.

**Example:**

```ts
type UserId = string & {
  readonly __brand: "UserId";
};

type OrderId = string & {
  readonly __brand: "OrderId";
};
```

Both are strings at runtime, but TypeScript treats them as different logical types.

**Interview Line**

Branded types prevent mixing logically different values that share the same underlying primitive representation.

### Q. How do you create a type-safe ID using branded types?

**Answer:**

Create a branded primitive and expose a constructor or validation function.

**Example:**

```ts
type UserId = string & {
  readonly __brand: "UserId";
};

function createUserId(value: string): UserId {
  return value as UserId;
}
```

Usage:

```ts
const userId = createUserId("u-123");
```

A stronger implementation can validate the ID format before applying the brand.

**Interview Line**

Create a type-safe ID by branding a primitive and centralizing creation through a constructor or validation function.

### Q. What is opaque type pattern in TypeScript?

**Answer:**

An opaque type hides the underlying representation of a value from consumers and exposes only the intended public type.

TypeScript does not have a built-in opaque keyword, but the pattern can be simulated with branding and module encapsulation.

**Example:**

```ts
declare const brand: unique symbol;

export type UserId = string & {
  readonly [brand]: "UserId";
};
```

Consumers can use `UserId`, while creation can be restricted to functions exported by the defining module.

**Interview Line**

The opaque type pattern hides a type's internal representation and exposes controlled creation and usage APIs.

### Q. How do you model impossible states using TypeScript?

**Answer:**

Use discriminated unions so invalid combinations cannot be represented.

**Bad Model:**

```ts
type State = {
  loading: boolean;
  data?: User;
  error?: string;
};
```

This allows contradictory combinations.

A better model is:

```ts
type State =
  | {
      status: "idle";
    }
  | {
      status: "loading";
    }
  | {
      status: "success";
      data: User;
    }
  | {
      status: "error";
      error: string;
    };
```

Now each state contains only the data that belongs to that state.

**Interview Line**

Model impossible states with discriminated unions so invalid state combinations cannot be expressed.

## Utility Types

### Q. What are utility types in TypeScript?

**Answer:**

Definition

Utility types are predefined generic types in TypeScript that help transform and manipulate existing types.

Why They Are Useful

- Reduce code duplication ✅
- Improve readability ✅
- Enable powerful type transformations ✅
- Widely used in large-scale apps ✅

Common Utility Types

- `Partial<T>`
- `Required<T>`
- `Readonly<T>`
- `Pick<T, K>`
- `Omit<T, K>`
- `Record<K, T>`
- `ReturnType<T>`
- `Parameters<T>`

**Interview Line**

Utility types are built-in generic helpers that transform existing types to make code more reusable and maintainable.

### Q. Partial<T>

**Answer:**

Definition

Makes all properties optional

Example

```ts
type User = {
  name: string;
  age: number;
};

type PartialUser = Partial<User>;
```

Result

```ts
{
name?: string;
age?: number;
}
```

Use Case

Updating objects (e.g., PATCH API)

**Interview Line**

`Partial<T>` makes all properties optional, useful for updates and flexible objects.

### Q. Required<T>

**Answer:**

Definition

Makes all properties mandatory

Example

```ts
type User = {
  name?: string;
  age?: number;
};

type RequiredUser = Required<User>;
```

Result

```ts
{
  name: string;
  age: number;
}
```

Use Case

Ensuring complete data

**Interview Line**

`Required<T>` converts all optional properties into required ones.

### Q. Readonly<T>

**Answer:**

Definition

Makes all properties immutable

Example

```ts
type User = {
  name: string;
};

type ReadonlyUser = Readonly<User>;
```

Result

```ts
{
readonly name: string;
}
```

Use Case

Prevent accidental mutation (e.g., state management)

**Interview Line**

`Readonly<T>` ensures properties cannot be modified after assignment.

### Q. Pick<T, K>

**Answer:**

Definition

Select specific properties from a type

Example

```ts
type User = {
  name: string;
  age: number;
  email: string;
};

type UserPreview = Pick<User, "name" | "age">;
```

Result

```ts
{
  name: string;
  age: number;
}
```

Use Case

API response shaping

**Interview Line**

`Pick<T, K>` creates a new type by selecting specific keys from an existing type.

### Q. Omit<T, K>

**Answer:**

Definition

Removes specific properties from a type

Example

```ts
type User = {
  name: string;
  age: number;
  password: string;
};

type SafeUser = Omit<User, "password">;
```

Result

```ts
{
  name: string;
  age: number;
}
```

Use Case

Excluding sensitive data

**Interview Line**

`Omit<T, K>` removes specified properties from a type.

### Q. Record<K, T>

**Answer:**

Definition

Creates an object type with keys of type K and values of type T

Example

```ts
type Roles = "admin" | "user";

type UserRoles = Record<Roles, string>;
```

Result

```ts
{
  admin: string;
  user: string;
}
```

Use Case

Dictionaries / Maps

**Interview Line**

`Record<K, T>` creates a type with predefined keys and uniform value types.

### Q. When would you use ReturnType or Parameters?

**Answer:**

ReturnType<T>

Extracts return type of a function

Example

```ts
function getUser() {
  return { name: "Tanmay" };
}

type User = ReturnType<typeof getUser>;
```

Use Case

Reusing function return types

Parameters<T>

Extracts parameter types as a tuple

Example

```ts
function add(a: number, b: number) {}

type Params = Parameters<typeof add>;
```

Result

```ts
[number, number];
```

Use Case

- Function wrappers
- Middleware
- Higher-order functions

**Interview Line**

`ReturnType` and `Parameters` help extract function types, enabling better reuse and consistency.

### Q. What is `NonNullable<T>`?

**Answer:**

`NonNullable<T>` removes `null` and `undefined` from a type.

**Example:**

```ts
type Value = string | null | undefined;

type CleanValue = NonNullable<Value>;
```

Result:

```ts
string;
```

It is useful when a value has already been validated and you want a type that excludes nullable states.

**Interview Line**

`NonNullable<T>` removes `null` and `undefined` from a type.

### Q. What is `Exclude<T, U>`?

**Answer:**

`Exclude<T, U>` removes from union `T` all members assignable to `U`.

**Example:**

```ts
type Status = "idle" | "loading" | "success" | "error";

type FinalStatus = Exclude<Status, "idle" | "loading">;
```

Result:

```ts
"success" | "error";
```

**Interview Line**

`Exclude<T, U>` removes union members from `T` that are assignable to `U`.

### Q. What is `Extract<T, U>`?

**Answer:**

`Extract<T, U>` keeps only members of union `T` that are assignable to `U`.

**Example:**

```ts
type Value = string | number | boolean;

type TextLike = Extract<Value, string | boolean>;
```

Result:

```ts
string | boolean;
```

`Extract` is conceptually the opposite of `Exclude`.

**Interview Line**

`Extract<T, U>` keeps only the members of `T` that are compatible with `U`.

### Q. Difference between `Exclude` and `Omit`

**Answer:**

They operate on different kinds of types.

#### `Exclude`

Works on union members.

```ts
type Result = Exclude<"a" | "b" | "c", "b">;
```

Result:

```ts
"a" | "c";
```

#### `Omit`

Works on object properties.

```ts
type User = {
  id: number;
  name: string;
  email: string;
};

type PublicUser = Omit<User, "email">;
```

Result:

```ts
{
  id: number;
  name: string;
}
```

**Interview Line**

`Exclude` removes union members, while `Omit` removes properties from object types.

### Q. What is `Awaited<T>`?

**Answer:**

`Awaited<T>` extracts the resolved value type from a Promise-like type.

**Example:**

```ts
type Result = Awaited<Promise<string>>;
```

Result:

```ts
string;
```

It also handles nested promises.

```ts
type DeepResult = Awaited<Promise<Promise<number>>>;
```

Result:

```ts
number;
```

This is useful when typing async APIs.

**Interview Line**

`Awaited<T>` recursively extracts the resolved value type from Promise-like types.

### Q. What is `InstanceType<T>`?

**Answer:**

`InstanceType<T>` extracts the instance type created by a constructor.

**Example:**

```ts
class User {
  name = "John";
}
```

Then:

```ts
type UserInstance = InstanceType<typeof User>;
```

Result:

```ts
User;
```

This is useful when working with constructor types dynamically.

**Interview Line**

`InstanceType<T>` gets the instance type produced by a class or constructor type.

### Q. What is `ConstructorParameters<T>`?

**Answer:**

`ConstructorParameters<T>` extracts constructor arguments as a tuple type.

**Example:**

```ts
class User {
  constructor(
    public name: string,
    public age: number,
  ) {}
}
```

Then:

```ts
type UserArgs = ConstructorParameters<typeof User>;
```

Result:

```ts
[string, number];
```

**Interview Line**

`ConstructorParameters<T>` extracts a constructor's parameter types into a tuple.

### Q. What is `ThisParameterType<T>`?

**Answer:**

`ThisParameterType<T>` extracts the explicit `this` parameter type from a function type.

**Example:**

```ts
function greet(
  this: {
    name: string;
  },
  message: string,
) {
  return message + this.name;
}
```

Then:

```ts
type Context = ThisParameterType<typeof greet>;
```

Result:

```ts
{
  name: string;
}
```

**Interview Line**

`ThisParameterType<T>` extracts the explicitly declared `this` type from a function.

### Q. What is `OmitThisParameter<T>`?

**Answer:**

`OmitThisParameter<T>` removes the explicit `this` parameter from a function type.

**Example:**

```ts
function greet(
  this: {
    name: string;
  },
  message: string,
) {}
```

Then:

```ts
type BoundGreet = OmitThisParameter<typeof greet>;
```

Conceptually the result becomes:

```ts
(
  message: string
) => void
```

This is useful after a function has already been bound to a context.

**Interview Line**

`OmitThisParameter<T>` removes an explicit `this` parameter from a function type.

### Q. What is `ThisType<T>`?

**Answer:**

`ThisType<T>` is a marker utility that provides contextual typing for `this` inside object literals.

It does not transform a type by itself.

**Example:**

```ts
type ObjectDescriptor<D, M> = {
  data?: D;
  methods?: M & ThisType<D & M>;
};
```

Now methods can get a strongly typed `this` representing both data and methods.

`ThisType<T>` is more advanced and is typically used in framework-style object APIs.

**Interview Line**

`ThisType<T>` provides contextual typing for `this` inside object literals.

### Q. What is `Uppercase<T>`?

**Answer:**

`Uppercase<T>` converts a string literal type to uppercase.

**Example:**

```ts
type Role = Uppercase<"admin">;
```

Result:

```ts
"ADMIN";
```

It is often used with template literal types.

**Interview Line**

`Uppercase<T>` transforms string literal types to uppercase.

### Q. What is `Lowercase<T>`?

**Answer:**

`Lowercase<T>` converts a string literal type to lowercase.

**Example:**

```ts
type Value = Lowercase<"HELLO">;
```

Result:

```ts
"hello";
```

**Interview Line**

`Lowercase<T>` transforms string literal types to lowercase.

### Q. What is `Capitalize<T>`?

**Answer:**

`Capitalize<T>` converts the first character of a string literal type to uppercase.

**Example:**

```ts
type Name = Capitalize<"user">;
```

Result:

```ts
"User";
```

This is useful when building generated property names.

**Example:**

```ts
type Getter = `get${Capitalize<"name">}`;
```

Result:

```ts
"getName";
```

**Interview Line**

`Capitalize<T>` uppercases the first character of a string literal type.

### Q. What is `Uncapitalize<T>`?

**Answer:**

`Uncapitalize<T>` converts the first character of a string literal type to lowercase.

**Example:**

```ts
type Name = Uncapitalize<"User">;
```

Result:

```ts
"user";
```

**Interview Line**

`Uncapitalize<T>` lowercases the first character of a string literal type.

### Q. How do you create a custom `Nullable<T>` utility type?

**Answer:**

A custom nullable utility can add `null`, or both `null` and `undefined`, depending on your design.

**Example:**

```ts
type Nullable<T> = T | null;
```

Usage:

```ts
type UserState = Nullable<User>;
```

Result:

```ts
User | null;
```

If your project wants both:

```ts
type Maybe<T> = T | null | undefined;
```

**Interview Line**

A custom `Nullable<T>` utility is usually defined as `T | null`.

### Q. How do you create a custom `DeepPartial<T>` utility type?

**Answer:**

`Partial<T>` only makes top-level properties optional.

A recursive `DeepPartial<T>` can make nested properties optional too.

**Example:**

```ts
type DeepPartial<T> = T extends object
  ? {
      [K in keyof T]?: DeepPartial<T[K]>;
    }
  : T;
```

For:

```ts
type User = {
  profile: {
    name: string;
    address: {
      city: string;
    };
  };
};
```

`DeepPartial<User>` makes all nested fields optional.

In production, special handling may be needed for arrays, functions, dates, maps, and other non-plain objects.

**Interview Line**

`DeepPartial<T>` recursively applies optional properties through nested object structures.

### Q. How do you create a custom `DeepReadonly<T>` utility type?

**Answer:**

Create a recursive mapped type that applies `readonly` at every nested level.

**Example:**

```ts
type DeepReadonly<T> = T extends object
  ? {
      readonly [K in keyof T]: DeepReadonly<T[K]>;
    }
  : T;
```

Now nested properties cannot be reassigned through the resulting type.

Again, real-world implementations may need special handling for functions and collection types.

**Interview Line**

`DeepReadonly<T>` recursively makes nested properties readonly instead of only applying readonly at the top level.

### Q. How do you create a custom `RequiredByKeys<T, K>` utility type?

**Answer:**

Make selected keys required while leaving the remaining properties unchanged.

**Example:**

```ts
type RequiredByKeys<T, K extends keyof T> = Omit<T, K> & Required<Pick<T, K>>;
```

For:

```ts
type User = {
  id?: number;
  name?: string;
  email?: string;
};
```

Then:

```ts
type UserWithRequiredId = RequiredByKeys<User, "id">;
```

Now `id` is required while the others remain unchanged.

**Interview Line**

`RequiredByKeys<T, K>` combines `Omit` with `Required<Pick<...>>` to require only selected properties.

### Q. How do you create a custom `ReadonlyByKeys<T, K>` utility type?

**Answer:**

Make only selected keys readonly.

**Example:**

```ts
type ReadonlyByKeys<T, K extends keyof T> = Omit<T, K> & Readonly<Pick<T, K>>;
```

For:

```ts
type User = {
  id: number;
  name: string;
};
```

Then:

```ts
type UserWithReadonlyId = ReadonlyByKeys<User, "id">;
```

Now `id` is readonly while `name` remains mutable.

**Interview Line**

`ReadonlyByKeys<T, K>` makes only selected properties readonly by combining `Omit` and `Readonly<Pick<...>>`.

### Q. How do you create a custom `PickByValue<T, ValueType>` utility type?

**Answer:**

Use key remapping to keep only properties whose value type matches `ValueType`.

**Example:**

```ts
type PickByValue<T, ValueType> = {
  [K in keyof T as T[K] extends ValueType ? K : never]: T[K];
};
```

For:

```ts
type User = {
  id: number;
  name: string;
  email: string;
  active: boolean;
};
```

Then:

```ts
type StringFields = PickByValue<User, string>;
```

Result:

```ts
{
  name: string;
  email: string;
}
```

**Interview Line**

`PickByValue<T, V>` uses key remapping to keep only properties whose values match `V`.

### Q. When can utility types make code harder to understand?

**Answer:**

Utility types become harmful when type expressions become more complex than the domain they describe.

Warning signs include:

- Deeply nested conditional types
- Too many intersections
- Recursive generic chains
- Hard-to-read mapped types
- Error messages that are difficult to understand
- Clever abstractions used only once

**Example:**

A type such as:

```ts
DeepReadonly<RequiredByKeys<PickByValue<SomeLargeType, string>, "name">>;
```

may technically work but be difficult for the team to maintain.

In such cases, a named intermediate type or explicit interface may be clearer.

**Interview Line**

Utility types are useful until they make intent harder to read, error messages harder to understand, or maintenance more difficult than explicit types.

## Classes & OOP in TypeScript

### Q. How does TypeScript support OOP?

**Answer:**

Definition

TypeScript supports Object-Oriented Programming (OOP) by adding features on top of JavaScript such as:

- Classes
- Interfaces
- Inheritance
- Encapsulation
- Abstraction
- Polymorphism

Key Features

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

**Interview Line**

TypeScript supports OOP through classes, interfaces, inheritance, and access modifiers, enabling better structure and maintainability.

### Q. What are access modifiers (public, private, protected)?

**Answer:**

Definition

Access modifiers control visibility and accessibility of class members

Types

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

Comparison

| Modifier  | Same Class | Subclass | Outside |
| --------- | ---------- | -------- | ------- |
| public    | ✅         | ✅       | ✅      |
| private   | ✅         | ❌       | ❌      |
| protected | ✅         | ✅       | ❌      |

**Interview Line**

Access modifiers control visibility: public is open, private is restricted to the class, and protected allows access in subclasses.

### Q. What is a constructor in TypeScript?

**Answer:**

Definition

A special method used to initialize objects

Example

```ts
class User {
  name: string;

  constructor(name: string) {
    this.name = name;
  }
}
```

Shortcut (Parameter Properties)

```ts
class User {
  constructor(public name: string) {}
}
```

Key Points

- Called automatically when object is created
- Used for initial setup

**Interview Line**

A constructor initializes class properties when an object is created.

### Q. What are abstract classes?

**Answer:**

Definition

- A class that cannot be instantiated
- Used as a base class

Example

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

Key Points

- Can have abstract + concrete methods
- Forces subclasses to implement methods

**Interview Line**

Abstract classes define a blueprint with optional implementation and must be extended by subclasses.

### Q. Difference between interface and abstract class

**Answer:**

Key Differences

| Feature              | Interface         | Abstract Class |
| -------------------- | ----------------- | -------------- |
| Implementation       | ❌ No             | ✅ Yes         |
| Methods              | Only declarations | Both           |
| Multiple inheritance | ✅ Yes            | ❌ No          |
| Constructor          | ❌ No             | ✅ Yes         |
| Access modifiers     | ❌ No             | ✅ Yes         |

Example

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

Key Insight

- Interface = contract
- Abstract class = partial implementation

**Interview Line**

Interfaces define structure only, while abstract classes provide both structure and partial implementation.

### Q. Can TypeScript enforce design patterns?

**Answer:**

Short Answer

👉 Yes (at compile-time), but not strictly at runtime

Explanation

TypeScript helps enforce patterns using:

- Interfaces
- Abstract classes
- Access modifiers
- Generics

Example (Singleton Pattern)

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

What TypeScript Ensures

- Correct structure ✅
- Type safety ✅
- Proper usage ✅

What It Cannot Enforce

- Runtime behavior ❌
- Business logic ❌

**Interview Line**

TypeScript helps enforce design patterns through types and structure at compile time, but cannot guarantee runtime behavior.

### Q. What are parameter properties in TypeScript?

**Answer:**

Parameter properties let you declare and initialize class properties directly from constructor parameters.

Instead of writing:

```ts
class User {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }
}
```

you can write:

```ts
class User {
  constructor(public name: string) {}
}
```

TypeScript automatically creates the property and assigns the constructor argument to it.

Parameter properties work with modifiers such as:

```text
public
private
protected
readonly
```

**Example:**

```ts
class User {
  constructor(
    public readonly id: number,
    private name: string,
  ) {}
}
```

**Interview Line**

Parameter properties combine constructor parameters, property declarations, and assignments into one concise syntax.

### Q. Difference between private keyword and JavaScript `#private` fields

**Answer:**

TypeScript's `private` keyword and JavaScript `#private` fields both restrict access, but they work differently.

#### TypeScript `private`

```ts
class User {
  private name = "John";
}
```

This restriction is mainly enforced by TypeScript at compile time.

After compilation, the property is usually still a normal JavaScript property.

#### JavaScript `#private`

```ts
class User {
  #name = "John";
}
```

This is enforced by JavaScript at runtime.

Code outside the class cannot access:

```js
user.#name;
```

even through normal JavaScript execution.

**Interview Line**

TypeScript `private` is primarily compile-time access control, while `#private` is true JavaScript runtime privacy.

### Q. What is static property in TypeScript class?

**Answer:**

A static property belongs to the class itself rather than to individual instances.

**Example:**

```ts
class User {
  static count = 0;

  constructor() {
    User.count++;
  }
}
```

Usage:

```ts
new User();
new User();

console.log(User.count);
```

Output:

```text
2
```

You access static properties through the class name, not an instance.

**Interview Line**

A static property belongs to the class constructor itself and is shared across all instances.

### Q. What is static method in TypeScript class?

**Answer:**

A static method belongs to the class itself and can be called without creating an instance.

**Example:**

```ts
class MathUtil {
  static add(a: number, b: number) {
    return a + b;
  }
}
```

Usage:

```ts
MathUtil.add(10, 20);
```

You do not need:

```ts
new MathUtil();
```

Static methods are useful for:

- Factory methods
- Utility methods
- Class-level operations

**Interview Line**

A static method is called on the class itself and does not require an instance.

### Q. What is static block in TypeScript class?

**Answer:**

A static block runs once when the class is initialized.

It is useful for complex static initialization logic.

**Example:**

```ts
class Config {
  static settings: Record<string, string>;

  static {
    Config.settings = {
      mode: "dark",
      region: "IN",
    };
  }
}
```

A static block can access private static members and perform multi-step initialization.

**Interview Line**

A static block executes once during class initialization and is useful for complex setup of static state.

### Q. What is method overriding in TypeScript?

**Answer:**

Method overriding happens when a subclass provides its own implementation of a method defined in a parent class.

**Example:**

```ts
class Animal {
  speak() {
    return "Sound";
  }
}

class Dog extends Animal {
  speak() {
    return "Bark";
  }
}
```

Usage:

```ts
const dog = new Dog();

dog.speak();
```

Output:

```text
Bark
```

The subclass method replaces the inherited behavior for that instance.

**Interview Line**

Method overriding lets a subclass replace an inherited method with a more specific implementation.

### Q. How do you use `override` keyword?

**Answer:**

Use `override` before a subclass member that intentionally overrides a parent member.

**Example:**

```ts
class Animal {
  speak() {
    return "Sound";
  }
}

class Dog extends Animal {
  override speak() {
    return "Bark";
  }
}
```

If the parent method is renamed or removed, TypeScript can report an error because the child method no longer overrides anything.

**Interview Line**

The `override` keyword explicitly marks a subclass member as replacing a parent member and helps catch accidental mismatches.

### Q. Why is `noImplicitOverride` useful?

**Answer:**

`noImplicitOverride` requires members that override base-class members to use the `override` keyword.

Example configuration:

```json
{
  "compilerOptions": {
    "noImplicitOverride": true
  }
}
```

This helps detect mistakes during refactoring.

Suppose the parent changes:

```ts
speak();
```

to:

```ts
makeSound();
```

A child method still named:

```ts
speak();
```

might silently become an unrelated method.

With `override`, TypeScript catches this.

**Interview Line**

`noImplicitOverride` makes inheritance safer by requiring explicit `override` annotations for overridden members.

### Q. What is polymorphism in TypeScript?

**Answer:**

Polymorphism means different classes can be used through the same shared interface or base type while providing different behavior.

**Example:**

```ts
interface Shape {
  area(): number;
}
```

Implementations:

```ts
class Circle implements Shape {
  constructor(private radius: number) {}

  area() {
    return Math.PI * this.radius ** 2;
  }
}

class Square implements Shape {
  constructor(private size: number) {}

  area() {
    return this.size ** 2;
  }
}
```

Then:

```ts
function printArea(shape: Shape) {
  console.log(shape.area());
}
```

The function works with either class.

**Interview Line**

Polymorphism lets different implementations be used through one common contract while preserving their own behavior.

### Q. What is dependency injection in TypeScript?

**Answer:**

Dependency injection means a class receives the objects it depends on instead of creating them internally.

**Bad Example:**

```ts
class UserService {
  private db = new Database();
}
```

This tightly couples `UserService` to `Database`.

Better:

```ts
class UserService {
  constructor(private db: Database) {}
}
```

Now the dependency is supplied externally.

This improves:

- Testability
- Flexibility
- Loose coupling
- Replacement of implementations

**Interview Line**

Dependency injection supplies dependencies from outside a class instead of letting the class construct them internally.

### Q. How do interfaces help with dependency injection?

**Answer:**

Interfaces let classes depend on behavior instead of concrete implementations.

**Example:**

```ts
interface UserRepository {
  findById(id: number): User;
}
```

Service:

```ts
class UserService {
  constructor(private repository: UserRepository) {}
}
```

Now different implementations can be injected:

```ts
class SqlRepository implements UserRepository {
  findById(id: number) {
    // database logic
  }
}
```

For testing:

```ts
class MockRepository implements UserRepository {
  findById() {
    return mockUser;
  }
}
```

**Interview Line**

Interfaces make dependency injection flexible by letting classes depend on contracts instead of concrete implementations.

### Q. What is composition over inheritance?

**Answer:**

Composition over inheritance means building behavior by combining smaller objects or functions instead of creating deep class hierarchies.

Inheritance:

```text
Base
↓
Intermediate
↓
Specialized
↓
More specialized
```

Composition:

```text
Object
+
logger
+
validator
+
repository
```

**Example:**

```ts
class UserService {
  constructor(
    private logger: Logger,
    private repository: UserRepository,
  ) {}
}
```

The service gets capabilities through dependencies rather than inheriting from a large base class.

**Interview Line**

Composition over inheritance favors combining small reusable behaviors instead of relying on deep class hierarchies.

### Q. When should you avoid class inheritance?

**Answer:**

Avoid inheritance when:

- The relationship is not truly "is-a"
- Subclasses need only a small part of the parent
- Parent changes frequently break children
- Hierarchies become deep
- Behavior needs to be mixed flexibly
- Testing requires replacing dependencies

For example, instead of:

```text
AdminService
extends
UserService
extends
BaseService
extends
LoggerService
```

prefer composing specific dependencies.

Inheritance is most useful when subclasses genuinely share a stable conceptual base.

**Interview Line**

Avoid inheritance when it creates tight coupling, deep hierarchies, or when composition can express the relationship more flexibly.

### Q. What is an abstract property?

**Answer:**

An abstract property is declared in an abstract class but must be implemented by concrete subclasses.

**Example:**

```ts
abstract class Animal {
  abstract name: string;

  abstract speak(): string;
}
```

Subclass:

```ts
class Dog extends Animal {
  name = "Dog";

  speak() {
    return "Bark";
  }
}
```

The abstract class defines the required contract without supplying the property value itself.

**Interview Line**

An abstract property declares a required class member that concrete subclasses must provide.

### Q. Can abstract classes implement interfaces?

**Answer:**

Yes.

An abstract class can implement an interface, but it may leave some members abstract for subclasses to complete.

**Example:**

```ts
interface Shape {
  area(): number;
}

abstract class BaseShape implements Shape {
  abstract area(): number;

  print() {
    console.log(this.area());
  }
}
```

A concrete subclass must implement `area()`.

**Interview Line**

Abstract classes can implement interfaces and delegate some required members to concrete subclasses through abstract declarations.

### Q. Can interfaces extend classes?

**Answer:**

Yes, an interface can extend a class type.

When it does, the interface inherits the class's instance members.

**Example:**

```ts
class Control {
  private state: boolean = false;
}

interface SelectableControl extends Control {
  select(): void;
}
```

Because private members are included in the inherited shape, only subclasses of `Control` can usually satisfy that interface.

This is an advanced and less commonly used feature.

**Interview Line**

An interface can extend a class's instance type, including inherited private or protected member relationships.

### Q. What is `implements` keyword?

**Answer:**

`implements` checks that a class satisfies an interface or object-type contract.

**Example:**

```ts
interface Printable {
  print(): void;
}

class Report implements Printable {
  print() {
    console.log("Printing");
  }
}
```

If `Report` does not provide `print()`, TypeScript reports an error.

`implements` does not copy implementation code into the class.

**Interview Line**

`implements` verifies that a class conforms to a required interface contract without inheriting implementation.

### Q. Difference between `extends` and `implements`

**Answer:**

They serve different purposes.

#### `extends`

Used for inheritance.

```ts
class Dog extends Animal {}
```

The child inherits implementation and members from the parent.

#### `implements`

Used for contract checking.

```ts
class Dog implements Pet {}
```

The class must satisfy the interface but does not inherit implementation from it.

Comparison:

| `extends`                  | `implements`                         |
| -------------------------- | ------------------------------------ |
| Inherits implementation    | Checks a contract                    |
| Class-to-class inheritance | Class-to-interface/type relationship |
| Runtime relationship       | Type-system relationship             |

**Interview Line**

`extends` inherits behavior, while `implements` only verifies that a class satisfies a required contract.

### Q. How do you type `this` inside a class method?

**Answer:**

Inside normal class methods, TypeScript usually infers `this` as the class instance automatically.

**Example:**

```ts
class Counter {
  count = 0;

  increment() {
    this.count++;
  }
}
```

You can also explicitly type `this` in methods when needed.

**Example:**

```ts
class Counter {
  count = 0;

  increment(this: Counter) {
    this.count++;
  }
}
```

Explicit `this` types are especially useful in standalone functions or APIs that depend on invocation context.

**Interview Line**

TypeScript normally infers class-method `this`, but explicit `this` parameters can document or restrict the expected calling context.

### Q. What is fluent API pattern in TypeScript classes?

**Answer:**

A fluent API lets methods return `this` so multiple operations can be chained.

**Example:**

```ts
class QueryBuilder {
  private query = "";

  select(fields: string) {
    this.query += `SELECT ${fields} `;

    return this;
  }

  from(table: string) {
    this.query += `FROM ${table} `;

    return this;
  }

  build() {
    return this.query;
  }
}
```

Usage:

```ts
const query = new QueryBuilder().select("*").from("users").build();
```

Returning `this` also works well with subclasses because the return type remains the specific derived instance type.

**Interview Line**

The fluent API pattern returns `this` from methods so related operations can be chained in a readable, type-safe sequence.

## DOM & Browser APIs

### Q. Explain `!` in document selector.

**Answer:**

The `!` after an expression is the **non-null assertion operator**.

It tells TypeScript:

```text
I know this value is not null or undefined.
```

**Example:**

```ts
const button = document.querySelector("#submit")!;
```

Normally, TypeScript infers:

```ts
Element | null;
```

because the selector might not match anything.

After adding `!`, TypeScript treats it as:

```ts
Element;
```

Important: `!` does not perform any runtime check.

If the element is actually missing, your code can still fail at runtime.

**Interview Line**

The non-null assertion `!` removes `null` and `undefined` from a type without performing a runtime check.

### Q. How do you type `document.querySelector` safely?

**Answer:**

Use a generic type parameter and still handle the possible `null` result.

**Example:**

```ts
const button = document.querySelector<HTMLButtonElement>("#submit");
```

The type becomes:

```ts
HTMLButtonElement | null;
```

Then check it:

```ts
if (button) {
  button.disabled = true;
}
```

If the element must exist, fail explicitly:

```ts
if (!button) {
  throw new Error("Submit button not found");
}
```

After the check, TypeScript narrows it to `HTMLButtonElement`.

**Interview Line**

Type `querySelector` with a generic element type and handle `null` through narrowing instead of blindly asserting.

### Q. Why can `document.querySelector` return `null`?

**Answer:**

`querySelector` returns `null` when no element matches the selector at the time the query runs.

This can happen because:

- The selector is incorrect
- The element has not rendered yet
- The element was removed
- The query runs before the DOM is ready
- The element exists only conditionally

That is why TypeScript includes `null` in the return type.

**Interview Line**

`querySelector` can return `null` because the requested DOM element may not exist when the query executes.

### Q. Difference between non-null assertion `!` and type assertion `as`

**Answer:**

They solve different problems.

#### Non-null assertion `!`

Removes `null` and `undefined`.

```ts
const input = document.querySelector("#name")!;
```

#### Type assertion `as`

Tells TypeScript to treat a value as another compatible type.

```ts
const input = document.querySelector("#name") as HTMLInputElement;
```

Neither performs runtime validation.

A safer approach is runtime narrowing:

```ts
const input = document.querySelector("#name");

if (input instanceof HTMLInputElement) {
  console.log(input.value);
}
```

**Interview Line**

`!` removes nullability, while `as` changes TypeScript's view of a value's type; neither validates the runtime value.

### Q. When should you avoid non-null assertion?

**Answer:**

Avoid `!` when the value can genuinely be missing.

**Risky Example:**

```ts
const modal = document.querySelector("#modal")!;

modal.classList.add("open");
```

If the element is missing, the code fails at runtime.

Prefer:

```ts
const modal = document.querySelector("#modal");

if (!modal) {
  return;
}
```

Use `!` only when the guarantee is strong and obvious.

**Interview Line**

Avoid non-null assertions when absence is possible; prefer runtime checks and type narrowing.

### Q. How do you type DOM event listeners?

**Answer:**

TypeScript provides built-in event maps for DOM elements, `Window`, and `Document`.

**Example:**

```ts
const button = document.querySelector<HTMLButtonElement>("#save");

button?.addEventListener("click", (event) => {
  console.log(event);
});
```

TypeScript infers `event` as:

```ts
MouseEvent;
```

For keyboard events:

```ts
document.addEventListener("keydown", (event) => {
  console.log(event.key);
});
```

Here the event is inferred as `KeyboardEvent`.

**Interview Line**

DOM event listeners are usually typed automatically through built-in event maps based on the event name and target object.

### Q. How do you type `addEventListener` callback?

**Answer:**

In most cases, let TypeScript infer the callback event type from the event name.

**Example:**

```ts
window.addEventListener("resize", (event) => {
  console.log(event);
});
```

For explicit typing:

```ts
const handleClick = (event: MouseEvent) => {
  console.log(event.clientX);
};

button?.addEventListener("click", handleClick);
```

Use the appropriate DOM event type such as:

```text
MouseEvent
KeyboardEvent
InputEvent
FocusEvent
SubmitEvent
```

**Interview Line**

Type `addEventListener` callbacks with the DOM event type corresponding to the event name, or let TypeScript infer it.

### Q. How do you type `event.target` safely?

**Answer:**

`event.target` is broadly typed, so narrow it before accessing element-specific properties.

**Example:**

```ts
function handleInput(event: Event) {
  const target = event.target;

  if (target instanceof HTMLInputElement) {
    console.log(target.value);
  }
}
```

A type assertion can also be used when the runtime guarantee is strong:

```ts
const input = event.target as HTMLInputElement;
```

But runtime narrowing is safer.

**Interview Line**

Type `event.target` safely by narrowing it with `instanceof` before using element-specific properties.

### Q. Difference between `event.target` and `event.currentTarget` in TypeScript

**Answer:**

`event.target` is the element where the event originally occurred.

`event.currentTarget` is the element whose event listener is currently executing.

For:

```html
<button id="save">
  <span>Save</span>
</button>
```

If the user clicks the `span`:

```text
event.target
→ span
```

while:

```text
event.currentTarget
→ button
```

`currentTarget` is often easier to reason about because it corresponds to the listener's element.

**Interview Line**

`target` is the original event source, while `currentTarget` is the element whose listener is executing.

### Q. Why does TypeScript not know the exact type of `event.target`?

**Answer:**

Because events can bubble from descendant elements.

A listener attached to a button can receive a click originating from:

```html
<span>
  <img />
  <svg></svg
></span>
```

inside that button.

So TypeScript cannot safely assume that `event.target` is exactly the listener element.

It is therefore generally typed as:

```ts
EventTarget | null;
```

**Interview Line**

TypeScript keeps `event.target` broad because events may originate from any descendant element due to bubbling.

### Q. How do you type custom DOM events?

**Answer:**

Use `CustomEvent<T>` where `T` is the `detail` payload type.

**Example:**

```ts
type UserSelectedDetail = {
  userId: number;
};

const event = new CustomEvent<UserSelectedDetail>("userSelected", {
  detail: {
    userId: 42,
  },
});
```

Then:

```ts
window.dispatchEvent(event);
```

For frequently used custom events, you can augment the relevant event map for better inference.

**Interview Line**

Type custom DOM events with `CustomEvent<T>` so the `detail` payload is strongly typed.

### Q. How do you type `localStorage` data safely?

**Answer:**

`localStorage` stores only strings.

So:

```ts
const value = localStorage.getItem("user");
```

returns:

```ts
string | null;
```

If the stored value is structured data, parse it and validate the result.

**Example:**

```ts
const raw = localStorage.getItem("user");

if (raw) {
  const parsed: unknown = JSON.parse(raw);

  // validate before
  // treating as User
}
```

Avoid blindly doing:

```ts
JSON.parse(raw) as User;
```

because stored data may be malformed or outdated.

**Interview Line**

Treat `localStorage` data as untrusted strings, parse it, and validate its runtime shape before assigning application types.

### Q. How do you parse JSON safely in TypeScript?

**Answer:**

Use `try...catch` because invalid JSON can throw at runtime.

**Example:**

```ts
function safeParse(value: string): unknown {
  try {
    return JSON.parse(value);
  } catch {
    return null;
  }
}
```

Then validate or narrow the returned `unknown`.

**Interview Line**

Parse JSON inside `try...catch` and treat the result as `unknown` until it has been validated.

### Q. How do you validate data coming from browser storage?

**Answer:**

Validate browser storage because the data may be:

- Missing
- Corrupted
- Outdated
- Manually modified
- Written by an older app version

You can use a type guard.

**Example:**

```ts
type User = {
  id: number;
  name: string;
};

function isUser(value: unknown): value is User {
  if (typeof value !== "object" || value === null) {
    return false;
  }

  const user = value as Record<string, unknown>;

  return typeof user.id === "number" && typeof user.name === "string";
}
```

For larger schemas, runtime validation libraries such as Zod can simplify this.

**Interview Line**

Validate browser-storage data at runtime before trusting it because stored values can be stale, malformed, or manually changed.

### Q. How do you type `fetch` response?

**Answer:**

Type the data returned after parsing and validation rather than trying to type the `Response` object itself.

**Example:**

```ts
type User = {
  id: number;
  name: string;
};

async function fetchUser(): Promise<User> {
  const response = await fetch("/api/user");

  if (!response.ok) {
    throw new Error("Request failed");
  }

  const data: unknown = await response.json();

  if (!isUser(data)) {
    throw new Error("Invalid user response");
  }

  return data;
}
```

**Interview Line**

Type `fetch` results by validating parsed response data and returning a typed `Promise<T>` from your API function.

### Q. Why is `response.json()` typed as `any`?

**Answer:**

The browser cannot know the schema of arbitrary JSON returned by a server.

A response could be:

```json
{
  "name": "John"
}
```

or an array, primitive, or completely different object.

TypeScript cannot infer the runtime schema from the request URL.

Therefore, `response.json()` is broadly typed in the DOM APIs and does not guarantee your expected application shape.

**Interview Line**

`response.json()` is broadly typed because TypeScript cannot know the runtime JSON schema returned by an arbitrary server.

### Q. How do you avoid unsafe typing with `response.json()`?

**Answer:**

Treat parsed JSON as `unknown` and validate it before converting it into a domain type.

**Example:**

```ts
type Product = {
  id: number;
  title: string;
};

async function getProduct(): Promise<Product> {
  const response = await fetch("/api/product");

  if (!response.ok) {
    throw new Error("Request failed");
  }

  const data: unknown = await response.json();

  if (!isProduct(data)) {
    throw new Error("Invalid response");
  }

  return data;
}
```

For large applications, runtime schema validation can reduce repetitive manual checks.

The important distinction is:

```text
Type assertion
≠
Runtime validation
```

**Interview Line**

Avoid unsafe `response.json()` typing by treating parsed data as `unknown` and validating it before returning a typed result.

## Modules & Configuration

### Q. What is `tsconfig.json`?

**Answer:**

Definition

`tsconfig.json` is the configuration file for the TypeScript compiler (tsc)

Purpose

Defines how TypeScript should:

- Compile code
- Handle files
- Apply type checking rules

Basic Example

```json
{
  "compilerOptions": {
    "target": "ES6",
    "module": "commonjs",
    "strict": true
  }
}
```

Key Sections

- `compilerOptions` → compiler behavior
- `include` / `exclude` → files to compile
- `extends` → inherit configs

**Interview Line**

`tsconfig.json` controls how TypeScript compiles code and enforces type checking rules.

### Q. What are common compiler options (`strict`, `target`, `module`)?

**Answer:**

1. `strict`

Enables all strict type-checking options

Example

```json
{
  "compilerOptions": {
    "strict": true
  }
}
```

Includes

- `noImplicitAny`
- `strictNullChecks`
- `strictFunctionTypes`

**Interview Line**

`strict` enables maximum type safety by turning on all strict checks.

2. `target`

Specifies the JavaScript version to compile to

Example

```json
{
  "compilerOptions": {
    "target": "ES5"
  }
}
```

Common Values

ES5, ES6 (ES2015), ESNext

**Interview Line**

`target` defines which JavaScript version TypeScript compiles into.

3. `module`

Specifies the module system

Example

```json
{
  "compilerOptions": {
    "module": "commonjs"
  }
}
```

Common Values

- `commonjs`
- `esnext`
- `es6`

**Interview Line**

`module` determines how imports and exports are handled in the compiled output.

### Q. Difference between ESModule and CommonJS

**Answer:**

ESModule (ESM)

✅ Features

- Uses `import` / `export`
- Static analysis (compile-time)
- Modern standard

Example

```ts
import { add } from "./math";
export const value = 10;
```

CommonJS (CJS)

✅ Features

- Uses `require` / `module.exports`
- Dynamic (runtime)
- Used in Node.js (older)

Example

```js
const math = require("./math");
module.exports = { value: 10 };
```

Key Differences

| Feature      | ESModule      | CommonJS               |
| ------------ | ------------- | ---------------------- |
| Syntax       | import/export | require/module.exports |
| Loading      | Static        | Dynamic                |
| Usage        | Modern JS     | Node.js (legacy)       |
| Tree Shaking | ✅ Supported  | ❌ Not supported       |

**Interview Line**

ESModules use modern static imports/exports, while CommonJS uses dynamic require and module.exports.

### Q. How does TypeScript handle imports/exports?

**Answer:**

Core Idea

- TypeScript uses ESModule syntax
- Compiles based on `module` setting in `tsconfig.json`

Example

TypeScript Code

```ts
export function add(a: number, b: number) {
  return a + b;
}
```

```ts
import { add } from "./math";
```

Compiled Output (CommonJS)

```js
exports.add = function (a, b) {
  return a + b;
};
```

Important Concepts

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

Key Insight

TypeScript separates:

- Type system (compile-time)
- JavaScript output (runtime)

**Interview Line**

TypeScript uses ESModule syntax but compiles it into different module systems like CommonJS based on configuration.

### Q. tsconfig.json Configuration

**Answer:**

[tsconfig](https://www.typescriptlang.org/tsconfig)

This project's TypeScript configuration is defined in the `tsconfig.json` file. Here's a breakdown of the configuration options:

- `include`: Set to `["src"]`. This tells TypeScript to only convert files in the `src` directory.

- `target`: Set to `ES2020`. This is the JavaScript version that the TypeScript code will be compiled to.

- `useDefineForClassFields`: Set to `true`. This enables the use of the `define` semantics for initializing class fields.

- `module`: Set to `ESNext`. This is the module system for the compiled code.

- `lib`: Set to `["ES2020", "DOM", "DOM.Iterable"]`. This specifies the library files to be included in the compilation.

- `skipLibCheck`: Set to `true`. This makes TypeScript skip type checking of declaration files (`*.d.ts`).

- `moduleResolution`: Set to `bundler`. This sets the strategy TypeScript uses to resolve modules.

- `allowImportingTsExtensions`: Set to `true`. This allows importing of TypeScript files from JavaScript files.

- `resolveJsonModule`: Set to `true`. This allows importing of `.json` modules from TypeScript files.

- `isolatedModules`: Set to `true`. This ensures that each file can be safely transpiled without relying on other import/export files.

- `noEmit`: Set to `true`. This tells TypeScript to not emit any output files (`*.js` and `*.d.ts` files) after compilation.

- `strict`: Set to `true`. This enables all strict type-checking options.

- `noUnusedLocals`: Set to `true`. This reports an error when local variables are declared but never used.

- `noUnusedParameters`: Set to `true`. This reports an error when function parameters are declared but never used.

- `noFallthroughCasesInSwitch`: Set to `true`. This reports an error for fall through cases in switch statements.

- `erasableSyntaxOnly` : Allows only TypeScript syntax that can be safely removed without changing runtime JavaScript behavior.

- `"moduleDetection": "force"` : Treats every file as a module, even if it has no `import` or `export`.

- `"module": "ESNext"` : Emits JavaScript using the latest ECMAScript module syntax.

- `"allowJs": true` :Allows JavaScript files to be included and checked/compiled by TypeScript.

### Q. What is `baseUrl` in tsconfig?

**Answer:**

`baseUrl` defines the base directory TypeScript uses when resolving non-relative module imports.

**Example:**

```json
{
  "compilerOptions": {
    "baseUrl": "./src"
  }
}
```

Now an import such as:

```ts
import Button from "components/Button";
```

can be resolved relative to:

```text
src/
```

instead of requiring:

```ts
import Button from "../../components/Button";
```

In modern projects, path aliases are often configured with `paths`, and some bundlers can handle aliases independently.

**Interview Line**

`baseUrl` tells TypeScript which directory to treat as the starting point for non-relative module resolution.

### Q. What are `paths` in tsconfig?

**Answer:**

`paths` lets you define custom import aliases.

**Example:**

```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"]
    }
  }
}
```

Now:

```ts
import Button from "@/components/Button";
```

can map to:

```text
src/components/Button
```

`paths` affects TypeScript resolution, but your runtime, bundler, or Node environment may also need matching alias configuration.

**Interview Line**

`paths` maps custom import aliases to actual project directories for cleaner and more stable imports.

### Q. How do you configure path aliases?

**Answer:**

Define the alias in `tsconfig.json`, then ensure the build tool or runtime understands the same mapping.

**Example:**

```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"]
    }
  }
}
```

Usage:

```ts
import { apiClient } from "@/services/apiClient";
```

With tools such as Vite, Next.js, or Webpack, the alias may be supported automatically or require matching configuration depending on the tool and setup.

Important:

```text
TypeScript path mapping
!=
Runtime path mapping
```

**Interview Line**

Configure aliases in `paths` and make sure your bundler or runtime resolves the same aliases.

### Q. What is `rootDir`?

**Answer:**

`rootDir` tells TypeScript which directory should be treated as the root of the input source tree.

**Example:**

```json
{
  "compilerOptions": {
    "rootDir": "./src"
  }
}
```

If the source file is:

```text
src/utils/math.ts
```

and `outDir` is:

```text
dist
```

the emitted file will normally preserve the structure:

```text
dist/utils/math.js
```

`rootDir` mainly affects emitted directory structure.

**Interview Line**

`rootDir` defines the logical root of TypeScript source files for output path calculation.

### Q. What is `outDir`?

**Answer:**

`outDir` specifies the directory where TypeScript places generated files.

**Example:**

```json
{
  "compilerOptions": {
    "outDir": "./dist"
  }
}
```

Source:

```text
src/index.ts
```

may compile to:

```text
dist/index.js
```

Generated files can include:

- JavaScript
- Declaration files
- Source maps

depending on the compiler options.

**Interview Line**

`outDir` defines where TypeScript writes generated output files.

### Q. What is `lib` in tsconfig?

**Answer:**

`lib` specifies the built-in JavaScript and environment API type definitions available to TypeScript.

**Example:**

```json
{
  "compilerOptions": {
    "lib": ["ES2023", "DOM"]
  }
}
```

`ES2023` provides type definitions for modern JavaScript features.

`DOM` provides browser APIs such as:

```ts
document;
window;
fetch;
HTMLElement;
```

`lib` affects available types, not the JavaScript syntax emitted by the compiler.

**Interview Line**

`lib` controls which built-in JavaScript and environment API type definitions TypeScript makes available.

### Q. Difference between `target` and `lib`

**Answer:**

`target` controls the JavaScript version TypeScript emits.

`lib` controls which built-in APIs TypeScript knows about during type checking.

**Example:**

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "lib": ["ES2023", "DOM"]
  }
}
```

Here TypeScript may emit ES2020-compatible syntax while still understanding types for newer APIs if you explicitly include them.

However, adding a newer `lib` does not automatically provide those APIs at runtime.

You may still need:

- A modern runtime
- Polyfills

**Interview Line**

`target` controls emitted JavaScript syntax, while `lib` controls the built-in APIs available to the type checker.

### Q. What is `moduleResolution`?

**Answer:**

`moduleResolution` controls how TypeScript finds the file associated with an import.

For:

```ts
import { helper } from "./utils";
```

or:

```ts
import React from "react";
```

TypeScript must determine:

- Which file to load
- Whether extensions are required
- How `package.json` exports are interpreted
- How ESM and CommonJS rules apply

Common strategies include:

```text
node
node16
nodenext
bundler
```

**Interview Line**

`moduleResolution` defines the algorithm TypeScript uses to resolve imports to actual files or packages.

### Q. Difference between `node`, `node16`, `nodenext`, and `bundler` module resolution

**Answer:**

These modes model different module environments.

#### `node`

The older Node-style resolution mode.

It models traditional Node/CommonJS resolution and does not fully model modern ESM package behavior.

#### `node16`

Models Node.js 16+ behavior, including:

- ESM
- CommonJS
- `package.json` `exports`
- File-extension rules

Behavior depends on the module format of the current file.

#### `nodenext`

Very similar to `node16`, but tracks newer Node.js module behavior and is intended for modern Node ESM/CommonJS projects.

It is commonly paired with:

```json
{
  "module": "NodeNext",
  "moduleResolution": "NodeNext"
}
```

#### `bundler`

Designed for projects where a bundler handles module resolution.

It understands modern package exports but generally does not require Node-style explicit relative file extensions.

This often fits tools such as:

```text
Vite
Webpack
Rollup
esbuild
```

**Interview Line**

Use Node-specific resolution modes for code executed directly by Node, and `bundler` when a modern bundler controls module loading.

### Q. What is `esModuleInterop`?

**Answer:**

`esModuleInterop` improves interoperability between CommonJS modules and ES module import syntax.

**Example:**

A CommonJS package may export with:

```js
module.exports = value;
```

With `esModuleInterop`, TypeScript can make default-style imports easier:

```ts
import express from "express";
```

instead of requiring patterns such as:

```ts
import * as express from "express";
```

It may also emit compatibility helper functions when TypeScript generates JavaScript.

**Interview Line**

`esModuleInterop` improves compatibility between CommonJS packages and ES module-style imports.

### Q. What is `allowSyntheticDefaultImports`?

**Answer:**

`allowSyntheticDefaultImports` lets TypeScript allow a default import even when the module's type definition does not explicitly declare a default export.

**Example:**

```ts
import React from "react";
```

It mainly affects type checking.

It does not itself change the generated runtime interoperability behavior.

**Interview Line**

`allowSyntheticDefaultImports` permits default-import syntax for modules that may not declare a real default export in their typings.

### Q. Difference between `esModuleInterop` and `allowSyntheticDefaultImports`

**Answer:**

They are related but not identical.

#### `allowSyntheticDefaultImports`

Affects whether TypeScript accepts default-import syntax during type checking.

#### `esModuleInterop`

Adds broader CommonJS/ESM interoperability behavior and can affect emitted helper code when TypeScript performs the emit.

In practice, enabling:

```json
{
  "esModuleInterop": true
}
```

also enables synthetic default import behavior.

**Interview Line**

`allowSyntheticDefaultImports` mainly relaxes type checking, while `esModuleInterop` provides broader runtime-oriented CommonJS/ESM interoperability.

### Q. What is `skipLibCheck`?

**Answer:**

`skipLibCheck` tells TypeScript not to fully type-check declaration files such as:

```text
.d.ts
```

from dependencies and libraries.

**Example:**

```json
{
  "compilerOptions": {
    "skipLibCheck": true
  }
}
```

This can:

- Speed up compilation
- Avoid duplicate type conflicts in dependency trees
- Reduce noise from third-party declaration files

Your own application code is still type-checked.

**Interview Line**

`skipLibCheck` skips detailed checking of declaration files to improve build speed and reduce third-party type noise.

### Q. Should `skipLibCheck` be enabled?

**Answer:**

In many application projects, enabling it is reasonable.

Benefits include:

- Faster builds
- Fewer dependency-related type conflicts
- Less noise from external declaration files

However, library authors or projects that need maximum declaration correctness may choose to disable it.

It should not be used to hide errors in your own source code.

**Interview Line**

`skipLibCheck` is commonly enabled in applications for faster builds, but libraries may disable it when declaration-file correctness matters more.

### Q. What is `noEmit`?

**Answer:**

`noEmit` tells TypeScript to type-check the project without generating JavaScript or other output files.

**Example:**

```json
{
  "compilerOptions": {
    "noEmit": true
  }
}
```

This is common when another tool handles compilation.

Examples:

```text
Vite
Next.js
Babel
esbuild
SWC
```

TypeScript is then used primarily as a type checker.

**Interview Line**

`noEmit` runs TypeScript for type checking only and leaves code generation to another tool.

### Q. What is `declaration` option?

**Answer:**

`declaration` tells TypeScript to generate `.d.ts` declaration files for your source code.

**Example:**

```json
{
  "compilerOptions": {
    "declaration": true
  }
}
```

From:

```ts
export function add(a: number, b: number): number {
  return a + b;
}
```

TypeScript can generate:

```ts
export declare function add(a: number, b: number): number;
```

This is especially important when publishing TypeScript libraries.

**Interview Line**

`declaration` generates `.d.ts` files describing the public type API of compiled code.

### Q. What is `sourceMap` option?

**Answer:**

`sourceMap` generates `.map` files that connect generated JavaScript back to the original TypeScript source.

**Example:**

```json
{
  "compilerOptions": {
    "sourceMap": true
  }
}
```

This improves debugging because browser or Node.js developer tools can show:

```text
original .ts source
```

instead of only compiled JavaScript.

**Interview Line**

`sourceMap` generates mappings from emitted JavaScript back to the original TypeScript source for debugging.

### Q. What is `isolatedModules`?

**Answer:**

`isolatedModules` checks that every source file can be safely transpiled independently.

**Example:**

```json
{
  "compilerOptions": {
    "isolatedModules": true
  }
}
```

This matters because tools such as Babel, SWC, and esbuild often transpile one file at a time instead of analyzing the entire TypeScript program.

It catches TypeScript patterns that require cross-file type information during transformation.

**Interview Line**

`isolatedModules` ensures each TypeScript file can be transformed independently without relying on whole-program compilation.

### Q. Why is `isolatedModules` important with Babel or Vite?

**Answer:**

Tools such as Babel and Vite commonly transpile TypeScript syntax without performing TypeScript's full multi-file type analysis.

They process files independently.

So TypeScript code must be safe for isolated transformation.

`isolatedModules` warns about patterns that may work with `tsc`'s full program analysis but fail or behave differently under single-file transpilation.

Type checking is typically performed separately with:

```bash
tsc --noEmit
```

**Interview Line**

`isolatedModules` is important with Vite or Babel because those tools transform TypeScript one file at a time.

### Q. What is `noUncheckedIndexedAccess`?

**Answer:**

`noUncheckedIndexedAccess` makes indexed access safer by adding `undefined` when TypeScript cannot guarantee the key exists.

Without it:

```ts
const names: string[] = [];

const first = names[0];
```

TypeScript may treat `first` as:

```ts
string;
```

With:

```json
{
  "noUncheckedIndexedAccess": true
}
```

it becomes:

```ts
string | undefined;
```

The same idea applies to index signatures.

**Interview Line**

`noUncheckedIndexedAccess` adds `undefined` to potentially missing array and object-index access results.

### Q. What is `exactOptionalPropertyTypes`?

**Answer:**

`exactOptionalPropertyTypes` makes optional properties more precise.

Consider:

```ts
type User = {
  name?: string;
};
```

Without this option, TypeScript may allow:

```ts
const user: User = {
  name: undefined,
};
```

With:

```json
{
  "exactOptionalPropertyTypes": true
}
```

`name?: string` means:

```text
the property may be absent
```

but if present, it should be a `string`.

If you explicitly want `undefined` as a value, write:

```ts
name?:
  string | undefined;
```

**Interview Line**

`exactOptionalPropertyTypes` distinguishes an absent optional property from a property explicitly set to `undefined`.

### Q. What is `noImplicitReturns`?

**Answer:**

`noImplicitReturns` reports functions where not all code paths explicitly return a value when a return is expected.

**Example:**

```ts
function getStatus(value: number) {
  if (value > 0) {
    return "positive";
  }
}
```

The other path returns:

```ts
undefined;
```

With `noImplicitReturns`, TypeScript warns about the missing return path.

**Interview Line**

`noImplicitReturns` catches functions where some execution paths accidentally return nothing.

### Q. What is `noFallthroughCasesInSwitch`?

**Answer:**

`noFallthroughCasesInSwitch` reports switch cases that unintentionally continue into the next case.

**Example:**

```ts
switch (status) {
  case "loading":
    console.log("Loading");

  case "success":
    console.log("Success");
}
```

The missing:

```ts
break;
```

may be accidental.

With this option enabled, TypeScript can warn about fallthrough cases.

**Interview Line**

`noFallthroughCasesInSwitch` catches accidental switch-case fallthrough caused by missing termination logic.

### Q. What is `strictNullChecks`?

**Answer:**

`strictNullChecks` treats `null` and `undefined` as distinct types instead of allowing them almost everywhere.

With it enabled:

```ts
let name: string = null;
```

is an error.

You must explicitly allow nullable values:

```ts
let name: string | null = null;
```

It also makes APIs such as:

```ts
document.querySelector();
```

correctly return:

```ts
Element | null;
```

**Interview Line**

`strictNullChecks` makes `null` and `undefined` explicit parts of the type system.

### Q. Why is `strictNullChecks` important?

**Answer:**

Many JavaScript runtime errors come from unexpectedly accessing values that are:

```text
null
undefined
```

For example:

```ts
user.name;
```

fails if `user` is actually `null`.

With `strictNullChecks`, TypeScript forces you to handle that possibility.

**Example:**

```ts
if (user) {
  console.log(user.name);
}
```

This catches a major class of runtime bugs during development.

**Interview Line**

`strictNullChecks` is important because it forces nullable cases to be handled explicitly instead of failing later at runtime.

### Q. What is project references in TypeScript?

**Answer:**

Project references let one TypeScript project reference another TypeScript project.

They are useful in large codebases and monorepos.

**Example structure:**

```text
packages/
  shared/
    tsconfig.json

  api/
    tsconfig.json

  web/
    tsconfig.json
```

A project can reference another:

```json
{
  "references": [
    {
      "path": "../shared"
    }
  ]
}
```

Referenced projects usually use:

```json
{
  "compilerOptions": {
    "composite": true
  }
}
```

Benefits include:

- Faster incremental builds
- Clear package boundaries
- Build ordering
- Separate TypeScript configurations

You can build referenced projects with:

```bash
tsc --build
```

**Interview Line**

Project references connect multiple TypeScript projects for scalable, incremental, dependency-aware builds.

### Q. When would you use multiple tsconfig files?

**Answer:**

Use multiple `tsconfig` files when different parts of a project need different compiler settings.

Common cases include:

- Frontend and backend
- Browser and Node code
- Tests
- Build scripts
- Libraries
- Monorepo packages

**Example:**

```text
tsconfig.json
tsconfig.app.json
tsconfig.node.json
tsconfig.test.json
```

A shared base configuration can be reused with:

```json
{
  "extends": "./tsconfig.base.json"
}
```

For example:

```text
frontend
→ DOM libs

backend
→ Node types

tests
→ test framework globals
```

This keeps environment-specific settings isolated while sharing common strictness rules.

**Interview Line**

Use multiple `tsconfig` files when different application areas, environments, or packages require different compiler settings.

## Real-world / Practical Questions

### Q. How do you type an API response?

**Answer:**

Approach

- Define a type/interface matching API structure
- Use it in fetch/axios calls

Example

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

With Generic API Wrapper

```ts
async function fetchData<T>(url: string): Promise<T> {
  const res = await fetch(url);
  return res.json();
}

// Usage
const users = await fetchData<User[]>("/api/users");
```

Best Practices

- Match backend contract
- Use optional fields for uncertain data
- Validate if needed (e.g., runtime checks)

**Interview Line**

API responses are typed using interfaces or generics to ensure type safety and predictable data handling.

### Q. How do you handle nullable values safely?

**Answer:**

Problem

Values can be `null` or `undefined`

Solutions

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

Best Practice

Prefer safe checks over forcing (`!`)

**Interview Line**

Nullable values are handled using union types, optional chaining, and null checks to ensure safe access.

### Q. How do you migrate a JavaScript project to TypeScript?

**Answer:**

Step-by-Step

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

Strategy

Incremental migration (not all at once)

**Interview Line**

Migrate gradually by enabling TypeScript, renaming files, and progressively adding types instead of converting everything at once.

### Q. How do you avoid overusing `any`?

**Answer:**

Problems with `any`

- No type safety ❌
- Runtime bugs ❌

Alternatives

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

Rule

👉 Use `any` only as a last resort

**Interview Line**

Avoid `any` by using `unknown`, generics, and proper type definitions to maintain type safety.

### Q. How do you structure types in a large project?

**Answer:**

Recommended Structure

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

Best Practices

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

Key Insight

Scalability depends on organized types

**Interview Line**

In large projects, types should be modular, reusable, and organized by feature or domain.

### Q. How do you type React props in TypeScript?

**Answer:**

Using Interface

```ts
interface Props {
name: string;
age?: number;
}

function User({ name, age }: Props) {
return <div>{name}</div>;
}
```

Using Type

```ts
type Props = {
name: string;
};

const User = ({ name }: Props) => <div>{name}</div>;
```

With Children

```ts
type Props = {
children: React.ReactNode;
};

function Wrapper({ children }: Props) {
return <div>{children}</div>;
}
```

With Default Props

```ts
type Props = {
  name?: string;
};

function User({ name = "Guest" }: Props) {}
```

Best Practices

- Prefer interface for props
- Use strict typing
- Avoid `any`

**Interview Line**

React props are typed using interfaces or types to ensure component reliability and better developer experience.

### Q. How do you type API error responses?

**Answer:**

Define a dedicated error shape that represents the error contract returned by the backend.

**Example:**

```ts
type ApiError = {
  message: string;
  code: string;
  details?: Record<string, string[]>;
};
```

A request function can then return or throw typed error information.

**Example:**

```ts
type ApiResult<T> =
  | {
      success: true;
      data: T;
    }
  | {
      success: false;
      error: ApiError;
    };
```

This makes error handling explicit instead of relying on arbitrary strings.

**Interview Line**

Type API errors with a dedicated error contract so consumers can safely handle message, code, and validation details.

### Q. How do you type paginated API responses?

**Answer:**

Create a generic paginated response type where the item type is reusable.

**Example:**

```ts
type PaginatedResponse<T> = {
  data: T[];
  page: number;
  pageSize: number;
  total: number;
  totalPages: number;
};
```

Usage:

```ts
type UserPage = PaginatedResponse<User>;
```

For cursor-based APIs:

```ts
type CursorResponse<T> = {
  data: T[];
  nextCursor: string | null;
  hasMore: boolean;
};
```

**Interview Line**

Use a generic pagination wrapper so metadata stays reusable while the item type changes per endpoint.

### Q. How do you type generic API response wrappers?

**Answer:**

Use a generic type parameter for the endpoint-specific payload.

**Example:**

```ts
type ApiResponse<T> = {
  success: boolean;
  data: T;
  message?: string;
};
```

Usage:

```ts
type UserResponse = ApiResponse<User>;

type ProductListResponse = ApiResponse<Product[]>;
```

If success and failure have different shapes, a discriminated union is usually safer than one object with many optional fields.

**Interview Line**

Generic API wrappers use a type parameter to preserve the exact payload type while reusing common response metadata.

### Q. How do you type success and error API states?

**Answer:**

Use a discriminated union.

**Example:**

```ts
type ApiResult<T> =
  | {
      success: true;
      data: T;
    }
  | {
      success: false;
      error: ApiError;
    };
```

Then TypeScript narrows automatically:

```ts
function handleResult(result: ApiResult<User>) {
  if (result.success) {
    console.log(result.data.name);
  } else {
    console.log(result.error.message);
  }
}
```

**Interview Line**

Model API success and failure with discriminated unions so each state exposes only valid fields.

### Q. How do you model loading, success, and error state using discriminated unions?

**Answer:**

Use a status field as the discriminator.

**Example:**

```ts
type RequestState<T> =
  | {
      status: "idle";
    }
  | {
      status: "loading";
    }
  | {
      status: "success";
      data: T;
    }
  | {
      status: "error";
      error: string;
    };
```

This prevents invalid combinations such as:

```text
loading = true
data exists
error exists
```

at the same time.

**Interview Line**

Use a discriminated union with a status field so each request state contains only the data valid for that state.

### Q. How do you handle unknown API data safely?

**Answer:**

Treat external API data as `unknown` until it has been validated.

**Example:**

```ts
const data: unknown = await response.json();
```

Then validate it using:

- A type guard
- Zod
- Valibot
- Yup
- Another runtime schema library

Only after validation should it become a domain type.

**Interview Line**

Treat external API data as `unknown`, validate it at runtime, and only then promote it to a trusted application type.

### Q. Why should API data be validated at runtime even when using TypeScript?

**Answer:**

TypeScript types disappear at runtime.

The backend can still return:

- Missing fields
- Wrong types
- Unexpected `null`
- Outdated contracts
- Invalid enum values

**Example:**

```ts
type User = {
  id: number;
  name: string;
};
```

This declaration does not force the server to actually return that shape.

Therefore runtime validation is needed at trust boundaries.

**Interview Line**

TypeScript checks your source code, but runtime validation verifies whether real external data actually matches the expected contract.

### Q. What libraries can be used for runtime validation with TypeScript?

**Answer:**

Common libraries include:

- Zod
- Valibot
- Yup
- io-ts
- Superstruct
- ArkType

Zod is especially common because it provides both runtime validation and strong TypeScript inference.

**Example concept:**

```ts
const UserSchema = z.object({
  id: z.number(),
  name: z.string(),
});
```

**Interview Line**

Runtime validation libraries such as Zod or Valibot validate external data and integrate well with TypeScript types.

### Q. How do you use Zod with TypeScript?

**Answer:**

Define a schema and validate unknown data with `parse` or `safeParse`.

**Example:**

```ts
import { z } from "zod";

const UserSchema = z.object({
  id: z.number(),
  name: z.string(),
});
```

Validate:

```ts
const result = UserSchema.safeParse(data);
```

Then:

```ts
if (!result.success) {
  console.log(result.error);

  return;
}

console.log(result.data.name);
```

After successful validation, `result.data` is strongly typed.

**Interview Line**

Zod validates runtime values with schemas and gives TypeScript-safe data after successful parsing.

### Q. What is schema inference?

**Answer:**

Schema inference means deriving a TypeScript type automatically from a runtime validation schema.

Instead of defining both:

```text
schema
and
type
```

separately, the schema becomes the source of truth.

This reduces duplication and contract drift.

**Interview Line**

Schema inference derives static TypeScript types directly from runtime validation schemas.

### Q. How do you infer TypeScript types from Zod schemas?

**Answer:**

Use:

```ts
z.infer<typeof Schema>;
```

**Example:**

```ts
const UserSchema = z.object({
  id: z.number(),
  name: z.string(),
});

type User = z.infer<typeof UserSchema>;
```

Now the `User` type automatically stays aligned with the schema.

**Interview Line**

Use `z.infer<typeof Schema>` to derive a TypeScript type directly from a Zod schema.

### Q. How do you keep frontend types in sync with backend contracts?

**Answer:**

Avoid manually duplicating the same contract in multiple places when possible.

Common approaches include:

- Shared TypeScript packages
- OpenAPI-generated types
- GraphQL code generation
- tRPC-style end-to-end typing
- Shared runtime schemas such as Zod
- Generated SDKs

For separate frontend and backend repositories, generated contracts are often safer than manually copying interfaces.

**Interview Line**

Keep frontend and backend types synchronized through shared contracts or generated types instead of duplicating definitions manually.

### Q. What is DTO in TypeScript?

**Answer:**

DTO stands for **Data Transfer Object**.

A DTO describes the structure of data transferred between system boundaries.

Examples include:

- API request body
- API response body
- Message queue payload
- Service-to-service contract

**Example:**

```ts
type UserDto = {
  id: number;
  first_name: string;
  created_at: string;
};
```

A DTO should represent the transport contract, not necessarily how the UI wants to use the data.

**Interview Line**

A DTO is a typed data structure used to transfer data across application or service boundaries.

### Q. Difference between API DTO and UI model

**Answer:**

An API DTO represents the backend transport format.

A UI model represents the shape most convenient for rendering and frontend logic.

**Example DTO:**

```ts
type UserDto = {
  first_name: string;
  created_at: string;
};
```

**Example UI model:**

```ts
type User = {
  firstName: string;
  createdAt: Date;
};
```

The UI model may:

- Rename fields
- Convert strings to dates
- Combine fields
- Remove transport-only values
- Add derived values

**Interview Line**

DTOs model transport data, while UI models are shaped for frontend rendering and interaction.

### Q. Why should you avoid directly using backend response types in UI state?

**Answer:**

Backend contracts are optimized for transport and persistence, not necessarily for UI needs.

Direct usage can create tight coupling.

Problems include:

- Snake_case leaking into UI code
- Date strings used everywhere
- Backend-specific nullability spreading through components
- Transport fields becoming UI dependencies
- Harder backend contract changes

A transformation layer creates a cleaner boundary.

**Interview Line**

Avoid storing raw backend DTOs directly in UI state because it tightly couples presentation logic to transport contracts.

### Q. How do you transform API response types into UI-friendly types?

**Answer:**

Create a mapper function between the DTO and UI model.

**Example:**

```ts
type UserDto = {
  id: number;
  first_name: string;
  created_at: string;
};

type User = {
  id: number;
  firstName: string;
  createdAt: Date;
};
```

Mapper:

```ts
function mapUser(dto: UserDto): User {
  return {
    id: dto.id,
    firstName: dto.first_name,
    createdAt: new Date(dto.created_at),
  };
}
```

This centralizes conversion logic.

**Interview Line**

Transform API DTOs into UI models with dedicated mapper functions at the application boundary.

### Q. How do you type environment variables?

**Answer:**

Type environment variables according to the platform.

For Node.js, you can augment `ProcessEnv`.

**Example:**

```ts
declare namespace NodeJS {
  interface ProcessEnv {
    API_URL: string;
    NODE_ENV: "development" | "production" | "test";
  }
}
```

In Vite, you can augment:

```ts
interface ImportMetaEnv {
  readonly VITE_API_URL: string;
}
```

Type declarations improve autocomplete, but runtime validation is still required.

**Interview Line**

Type environment variables with environment-specific declaration augmentation, but still validate them at runtime.

### Q. Why are environment variables always strings?

**Answer:**

Environment variables come from the operating system or process environment as text values.

For example:

```text
PORT=3000
DEBUG=true
```

At runtime, they are read as strings such as:

```ts
"3000";
"true";
```

They are not automatically converted to numbers or booleans.

So parsing is required.

**Example:**

```ts
const port = Number(process.env.PORT);
```

**Interview Line**

Environment variables are text-based process values, so numbers and booleans must be parsed explicitly.

### Q. How do you safely read environment variables?

**Answer:**

Validate and parse them at application startup.

**Example:**

```ts
const EnvSchema = z.object({
  API_URL: z.string().url(),

  PORT: z.coerce.number().int().positive(),

  NODE_ENV: z.enum(["development", "production", "test"]),
});
```

Then:

```ts
const env = EnvSchema.parse(process.env);
```

This fails early if configuration is invalid.

**Interview Line**

Safely read environment variables by validating and coercing them once during startup instead of scattering raw `process.env` access.

### Q. How do you type feature flags?

**Answer:**

Define the supported feature names explicitly.

**Example:**

```ts
type FeatureFlag = "newDashboard" | "betaSearch" | "darkMode";
```

Then:

```ts
type FeatureFlags = Record<FeatureFlag, boolean>;
```

Example:

```ts
const flags: FeatureFlags = {
  newDashboard: true,
  betaSearch: false,
  darkMode: true,
};
```

This prevents misspelled or unknown flag names.

**Interview Line**

Type feature flags with a literal key union and `Record` so all supported flags are explicit and type-safe.

### Q. How do you type configuration objects?

**Answer:**

Define a configuration type or derive one from a validated schema.

**Example:**

```ts
type AppConfig = {
  apiUrl: string;

  retryCount: number;

  environment: "dev" | "staging" | "prod";
};
```

Then:

```ts
const config: AppConfig = {
  apiUrl: "https://api.example.com",

  retryCount: 3,

  environment: "prod",
};
```

For immutable configuration:

```ts
const config = {
  retryCount: 3,
} as const;
```

Runtime-loaded config should still be validated.

**Interview Line**

Type configuration objects with explicit contracts or schema-derived types and validate externally loaded config at runtime.

### Q. How do you type permission maps?

**Answer:**

Define permission names as a literal union and use `Record`.

**Example:**

```ts
type Permission = "user.read" | "user.write" | "user.delete";
```

Then:

```ts
type PermissionMap = Record<Permission, boolean>;
```

Example:

```ts
const permissions: PermissionMap = {
  "user.read": true,
  "user.write": true,
  "user.delete": false,
};
```

For more complex systems, the value can be a richer object instead of a boolean.

**Interview Line**

Type permission maps with a permission-key union and `Record` so valid permissions are centrally defined.

### Q. How do you type role-based access rules?

**Answer:**

Define roles and permissions explicitly, then map each role to its allowed permissions.

**Example:**

```ts
type Role = "admin" | "editor" | "viewer";

type Permission = "user.read" | "user.write" | "user.delete";
```

Then:

```ts
type RolePermissions = Record<Role, readonly Permission[]>;
```

Example:

```ts
const rolePermissions: RolePermissions = {
  admin: ["user.read", "user.write", "user.delete"],

  editor: ["user.read", "user.write"],

  viewer: ["user.read"],
};
```

Frontend access checks are useful for UI behavior, but backend authorization must still enforce permissions securely.

**Interview Line**

Type role-based access with explicit role and permission unions plus a typed role-to-permission mapping, while enforcing real authorization on the server.

## React + TypeScript

### Q. React.JSX.Element vs React.ReactNode

**Answer:**

`React.JSX.Element` represents a React element returned by JSX.

`React.ReactNode` is broader and represents anything React can render.

**Example:**

```tsx
function Header(): React.JSX.Element {
  return <h1>Hello</h1>;
}
```

`React.JSX.Element` usually represents values such as:

```tsx
<div />
<MyComponent />
```

`React.ReactNode` can include:

```text
React elements
strings
numbers
arrays
null
undefined
booleans
```

**Example:**

```tsx
type Props = {
  children: React.ReactNode;
};
```

Use `React.ReactNode` for props such as `children`.

Use `React.JSX.Element` when describing a component result that must be a JSX element.

**Interview Line**

`React.JSX.Element` represents a JSX element, while `React.ReactNode` represents any value React can render.

### Q. How do you type functional components?

**Answer:**

Using `interface` (Recommended)

```ts
interface Props {
name: string;
}

function User({ name }: Props) {
return <div>{name}</div>;
}
```

Using `type`

```ts
type Props = {
name: string;
};

const User = ({ name }: Props) => <div>{name}</div>;
```

Key Point

Explicitly type props for better safety

**Interview Line**

Functional components are typed by defining a props interface or type and applying it to the component parameters.

### Q. Difference between `React.FC` and normal function typing

**Answer:**

`React.FC`

```ts
const User: React.FC<{ name: string }> = ({ name }) => {
return <div>{name}</div>;
};
```

Normal Function (Preferred)

```ts
interface Props {
name: string;
}

function User({ name }: Props) {
return <div>{name}</div>;
}
```

Key Differences

| Feature        | React.FC            | Normal Function      |
| -------------- | ------------------- | -------------------- |
| children       | Included by default | Must define manually |
| Readability    | Less clean          | Cleaner              |
| Flexibility    | Limited             | More flexible        |
| Recommendation | ❌ Avoid            | ✅ Preferred         |

Why Avoid `React.FC`

- Implicit `children`
- Less control
- Can hide bugs

**Interview Line**

`React.FC` adds implicit children and less flexibility, so normal function typing is preferred in modern React.

### Q. How to type `useState`, `useRef`, `useReducer`

**Answer:**

useState

```ts
const [count, setCount] = useState<number>(0);
```

With Union

```ts
const [user, setUser] = useState<User | null>(null);
```

useRef

```ts
const inputRef = useRef<HTMLInputElement | null>(null);
```

useReducer

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

**Interview Line**

Hooks are typed using generics, such as `useState<Type>` and `useRef<ElementType>`.

### Q. How to type event handlers

**Answer:**

Input Change Event

```ts
function handleChange(e: React.ChangeEvent<HTMLInputElement>) {
  console.log(e.target.value);
}
```

Button Click

```ts
function handleClick(e: React.MouseEvent<HTMLButtonElement>) {}
```

Form Submit

```ts
function handleSubmit(e: React.FormEvent<HTMLFormElement>) {
  e.preventDefault();
}
```

Key Tip

👉 Use `React.<EventType>`

**Interview Line**

Event handlers are typed using React-specific event types like `React.ChangeEvent` and `React.MouseEvent`.

### Q. How to type props with children

**Answer:**

Method 1: Explicit

```ts
type Props = {
children: React.ReactNode;
};

function Wrapper({ children }: Props) {
return <div>{children}</div>;
}
```

Method 2: With PropsWithChildren

```ts
import { PropsWithChildren } from "react";

type Props = {
  title: string;
};

function Card({ title, children }: PropsWithChildren<Props>) {}
```

Key Point

`React.ReactNode` covers all renderable content

**Interview Line**

Props with children are typed using `React.ReactNode` or `PropsWithChildren`.

### Q. Controlled vs Uncontrolled components typing

**Answer:**

Controlled Components

State is controlled by React

Example

```ts
const [value, setValue] = useState<string>("");

<input
value={value}
onChange={(e) => setValue(e.target.value)}
/>;
```

Typing

State + event types required

Uncontrolled Components

Uses DOM via `ref`

Example

```ts
const inputRef = useRef<HTMLInputElement>(null);

<input ref={inputRef} />;
```

Typing

Focus on useRef

Key Differences

| Feature        | React.FC            | Normal Function      |
| -------------- | ------------------- | -------------------- |
| children       | Included by default | Must define manually |
| Readability    | Less clean          | Cleaner              |
| Flexibility    | Limited             | More flexible        |
| Recommendation | ❌ Avoid            | ✅ Preferred         |

**Interview Line**

Controlled components use React state and require state/event typing, while uncontrolled components rely on refs and direct DOM access.

### Q. How do you type component props using discriminated unions?

**Answer:**

Use a shared discriminator property so TypeScript can narrow the valid prop shape.

**Example:**

```tsx
type Props =
  | {
      variant: "text";
      label: string;
      icon?: never;
    }
  | {
      variant: "icon";
      icon: React.ReactNode;
      label?: never;
    };

function Button(props: Props) {
  if (props.variant === "text") {
    return <button>{props.label}</button>;
  }

  return <button>{props.icon}</button>;
}
```

The `variant` field lets TypeScript narrow the branch safely.

**Interview Line**

Use discriminated unions when different component modes require different valid prop shapes.

### Q. How do you type mutually exclusive props?

**Answer:**

Use union types with `never` for props that must not appear together.

**Example:**

```tsx
type LinkButtonProps =
  | {
      href: string;
      onClick?: never;
    }
  | {
      href?: never;
      onClick: () => void;
    };
```

Now providing either `href` or `onClick` is valid, but providing both is rejected.

**Interview Line**

Use union branches and `never` to enforce mutually exclusive props at compile time.

### Q. How do you prevent invalid prop combinations?

**Answer:**

Model only valid combinations instead of making every property optional.

**Bad Example:**

```tsx
type Props = {
  loading?: boolean;
  data?: User;
  error?: string;
};
```

This allows contradictory combinations.

Better:

```tsx
type Props =
  | {
      status: "loading";
    }
  | {
      status: "success";
      data: User;
    }
  | {
      status: "error";
      error: string;
    };
```

**Interview Line**

Prevent invalid prop combinations by modeling valid states as union branches rather than unrelated optional fields.

### Q. How do you type a Button component with variant-specific props?

**Answer:**

Use a discriminated union for variant-specific behavior.

**Example:**

```tsx
type ButtonProps =
  | {
      variant: "primary";
      onClick: () => void;
      href?: never;
    }
  | {
      variant: "link";
      href: string;
      onClick?: never;
    };
```

Then:

```tsx
function Button(props: ButtonProps) {
  if (props.variant === "link") {
    return <a href={props.href}>Link</a>;
  }

  return <button onClick={props.onClick}>Button</button>;
}
```

**Interview Line**

Variant-specific props are best modeled with discriminated unions so each variant exposes only valid fields.

### Q. How do you type polymorphic components?

**Answer:**

Use a generic element type and merge custom props with the props of the selected element.

**Example:**

```tsx
type BoxProps<T extends React.ElementType> = {
  as?: T;
  children?: React.ReactNode;
} & Omit<React.ComponentPropsWithoutRef<T>, "as" | "children">;

function Box<T extends React.ElementType = "div">({ as, children, ...props }: BoxProps<T>) {
  const Component = as || "div";

  return <Component {...props}>{children}</Component>;
}
```

**Interview Line**

Polymorphic components use `React.ElementType` plus derived element props so the API changes safely based on the rendered element.

### Q. How do you type the `as` prop in React?

**Answer:**

Make the `as` prop generic.

**Example:**

```tsx
type TextProps<T extends React.ElementType> = {
  as?: T;
  children: React.ReactNode;
} & Omit<React.ComponentPropsWithoutRef<T>, "as" | "children">;
```

Usage:

```tsx
<Text as="a" href="/docs">
  Docs
</Text>
```

TypeScript knows `href` is valid because `as="a"`.

**Interview Line**

Type `as` with a generic `React.ElementType` and derive valid props from the selected element.

### Q. How do you type forwarded refs?

**Answer:**

Use the element type as the first generic to `forwardRef`.

**Example:**

```tsx
type InputProps = {
  label: string;
};

const Input = React.forwardRef<HTMLInputElement, InputProps>(({ label }, ref) => {
  return (
    <label>
      {label}
      <input ref={ref} />
    </label>
  );
});
```

The parent can use:

```tsx
const ref = useRef<HTMLInputElement>(null);
```

**Interview Line**

Type forwarded refs with `forwardRef<ElementType, Props>`.

### Q. How do you type `forwardRef` with generics?

**Answer:**

Generic `forwardRef` components are trickier because `forwardRef` can lose the generic relationship during inference.

A common approach is to write a generic inner function and then assign an explicit generic callable signature to the result.

**Example:**

```tsx
type ListProps<T> = {
  items: T[];
  renderItem: (item: T) => React.ReactNode;
};

function ListInner<T>(props: ListProps<T>, ref: React.ForwardedRef<HTMLUListElement>) {
  return (
    <ul ref={ref}>
      {props.items.map((item, index) => (
        <li key={index}>{props.renderItem(item)}</li>
      ))}
    </ul>
  );
}
```

The final component can then be exposed with a generic signature that preserves `T`.

**Interview Line**

Generic `forwardRef` components often need a generic inner render function plus an explicit final component signature.

### Q. How do you type `useImperativeHandle`?

**Answer:**

Define the handle interface exposed through the ref.

**Example:**

```tsx
type InputHandle = {
  focus: () => void;
  clear: () => void;
};
```

Then:

```tsx
const Input = React.forwardRef<InputHandle>((props, ref) => {
  const inputRef = useRef<HTMLInputElement>(null);

  useImperativeHandle(ref, () => ({
    focus() {
      inputRef.current?.focus();
    },

    clear() {
      if (inputRef.current) {
        inputRef.current.value = "";
      }
    },
  }));

  return <input ref={inputRef} />;
});
```

**Interview Line**

Type `useImperativeHandle` by defining a dedicated ref-handle interface containing the methods consumers may call.

### Q. How do you type custom input components?

**Answer:**

Reuse native input props and add your custom fields.

**Example:**

```tsx
type InputProps = {
  label: string;
  error?: string;
} & React.ComponentPropsWithoutRef<"input">;
```

Then:

```tsx
function Input({ label, error, ...props }: InputProps) {
  return (
    <label>
      {label}
      <input {...props} />

      {error && <span>{error}</span>}
    </label>
  );
}
```

This preserves native props such as `value`, `onChange`, `disabled`, and `name`.

**Interview Line**

Type custom inputs by extending native input props instead of manually redefining every HTML attribute.

### Q. How do you type reusable form components?

**Answer:**

Use generics when the component should preserve relationships between field names and values.

**Example:**

```tsx
type FieldProps<T, K extends keyof T> = {
  name: K;
  value: T[K];
  onChange: (value: T[K]) => void;
};
```

This is safer than using broad types such as `string` for every field.

**Interview Line**

Reusable form components should use generics to preserve relationships between field names, values, and callbacks.

### Q. How do you type controlled input props?

**Answer:**

Require `value` and `onChange`.

**Example:**

```tsx
type ControlledInputProps = {
  value: string;
  onChange: (value: string) => void;
};
```

Component:

```tsx
function Input({ value, onChange }: ControlledInputProps) {
  return <input value={value} onChange={(event) => onChange(event.target.value)} />;
}
```

**Interview Line**

Controlled input props require the current value and a change callback because the parent owns the state.

### Q. How do you type uncontrolled input props?

**Answer:**

Use initial values such as `defaultValue` and optionally expose a ref.

**Example:**

```tsx
type UncontrolledInputProps = {
  defaultValue?: string;
};
```

A stricter reusable API can model controlled and uncontrolled modes as mutually exclusive unions.

**Example:**

```tsx
type InputProps =
  | {
      value: string;
      onChange: (value: string) => void;
      defaultValue?: never;
    }
  | {
      value?: never;
      onChange?: never;
      defaultValue?: string;
    };
```

**Interview Line**

Uncontrolled inputs use initial-value props and refs instead of requiring the parent to own the current value.

### Q. How do you type React context?

**Answer:**

Define the context value type and pass it to `createContext`.

**Example:**

```tsx
type AuthContextValue = {
  user: User | null;
  logout: () => void;
};

const AuthContext = createContext<AuthContextValue | undefined>(undefined);
```

**Interview Line**

Type Context by defining its value contract and supplying that type to `createContext`.

### Q. How do you avoid nullable context values?

**Answer:**

Create the context with `undefined` and hide the check inside a custom hook.

**Example:**

```tsx
const AuthContext = createContext<AuthContextValue | undefined>(undefined);

function useAuth() {
  const context = useContext(AuthContext);

  if (!context) {
    throw new Error("useAuth must be used within AuthProvider");
  }

  return context;
}
```

Consumers now receive `AuthContextValue` directly.

**Interview Line**

Hide nullable Context handling inside a custom hook so normal consumers receive a guaranteed typed value.

### Q. How do you create a custom hook for typed context?

**Answer:**

Wrap `useContext`, check for a missing provider, and return the narrowed value.

**Example:**

```tsx
function useTheme(): ThemeContextValue {
  const context = useContext(ThemeContext);

  if (!context) {
    throw new Error("useTheme must be used within ThemeProvider");
  }

  return context;
}
```

**Interview Line**

A typed context hook wraps `useContext`, checks for the provider, and returns the non-null context type.

### Q. How do you type `useReducer` actions with discriminated unions?

**Answer:**

Define each action as a branch of a union.

**Example:**

```tsx
type Action =
  | {
      type: "increment";
    }
  | {
      type: "set";
      payload: number;
    };

function reducer(state: State, action: Action): State {
  switch (action.type) {
    case "increment":
      return {
        count: state.count + 1,
      };

    case "set":
      return {
        count: action.payload,
      };
  }
}
```

TypeScript narrows `action` based on `type`.

**Interview Line**

Use discriminated unions for reducer actions so each action type exposes only its valid payload.

### Q. How do you type Redux Toolkit slices?

**Answer:**

Type the slice state and use `PayloadAction<T>` for payloads.

**Example:**

```tsx
type CounterState = {
  value: number;
};

const initialState: CounterState = {
  value: 0,
};

const counterSlice = createSlice({
  name: "counter",
  initialState,

  reducers: {
    increment(state) {
      state.value++;
    },

    setValue(state, action: PayloadAction<number>) {
      state.value = action.payload;
    },
  },
});
```

**Interview Line**

Type Redux Toolkit slice state explicitly and use `PayloadAction<T>` for reducer payloads.

### Q. How do you type Redux Toolkit async thunks?

**Answer:**

Use `createAsyncThunk` generic parameters when return, argument, or rejection types need to be explicit.

**Example:**

```tsx
type ThunkError = {
  message: string;
};

const fetchUser = createAsyncThunk<
  User,
  number,
  {
    rejectValue: ThunkError;
  }
>("users/fetchUser", async (id, thunkApi) => {
  try {
    return await api.getUser(id);
  } catch {
    return thunkApi.rejectWithValue({
      message: "Failed",
    });
  }
});
```

**Interview Line**

Type async thunks with explicit return, argument, and rejection-value generics when inference is insufficient.

### Q. How do you type RTK Query endpoints?

**Answer:**

Provide the response type and argument type to `build.query` or `build.mutation`.

**Example:**

```tsx
getUser: build.query<User, number>({
  query: (id) => `/users/${id}`,
});
```

Mutation:

```tsx
updateUser: build.mutation<User, UpdateUserInput>({
  query: (body) => ({
    url: "/users",
    method: "PUT",
    body,
  }),
});
```

**Interview Line**

RTK Query endpoints are typed with response and argument generics such as `build.query<Result, Arg>`.

### Q. How do you type React Query response data?

**Answer:**

Type the query function return value and let TanStack Query infer `data`.

**Example:**

```tsx
async function fetchUsers(): Promise<User[]> {
  const response = await fetch("/api/users");

  if (!response.ok) {
    throw new Error("Request failed");
  }

  return response.json();
}

const query = useQuery({
  queryKey: ["users"],
  queryFn: fetchUsers,
});
```

`query.data` is inferred as:

```ts
User[] | undefined
```

**Interview Line**

Type the query function return value and let React Query infer the response data from that function.

### Q. How do you type React Query errors?

**Answer:**

Use a consistent custom error type in the query layer.

**Example:**

```ts
class ApiError extends Error {
  constructor(
    message: string,
    public status: number,
  ) {
    super(message);
  }
}
```

Then throw `ApiError` from API functions.

Depending on the TanStack Query version and project configuration, the error type can be inferred, configured globally, or supplied through generics.

**Interview Line**

Type React Query errors by throwing a consistent custom error type from the API layer.

### Q. How do you type route params in React Router?

**Answer:**

Use the generic form of `useParams`.

**Example:**

```tsx
const { id } = useParams<{
  id: string;
}>();
```

Because params may be absent depending on route context, you may still need to handle `undefined`.

**Interview Line**

Type React Router route params with `useParams<{ id: string }>()` and handle possible absence where necessary.

### Q. How do you type search params in React Router?

**Answer:**

`useSearchParams` returns `URLSearchParams`, so values are strings or `null`.

**Example:**

```tsx
const [searchParams] = useSearchParams();

const page = searchParams.get("page");
```

`page` is:

```ts
string | null;
```

If you expect a number:

```tsx
const pageNumber = Number(page ?? "1");
```

For complex query state, parse and validate with a helper or schema.

**Interview Line**

Search params are string-based, so parse and validate them into application-specific types.

### Q. How do you type `location.state` in React Router?

**Answer:**

Define the expected state shape and narrow or assert it carefully.

**Example:**

```tsx
type LocationState = {
  from?: string;
};

const location = useLocation();

const state = location.state as LocationState | null;
```

Because navigation state can come from different places, runtime validation may be appropriate for critical data.

**Interview Line**

Type `location.state` with an explicit state shape, but remember that navigation state may still require validation.

### Q. How do you type children as a render function?

**Answer:**

Type `children` as a callback that receives typed data and returns `React.ReactNode`.

**Example:**

```tsx
type DataProps<T> = {
  data: T;
  children: (value: T) => React.ReactNode;
};
```

Usage:

```tsx
<Data data={user}>{(user) => <p>{user.name}</p>}</Data>
```

**Interview Line**

Render-function children are typed as callbacks that receive typed data and return `React.ReactNode`.

### Q. How do you type compound components?

**Answer:**

Type the parent component and add typed static subcomponents.

**Example:**

```tsx
type TabsComponent = React.FC<TabsProps> & {
  List: typeof TabsList;
  Tab: typeof Tab;
  Panel: typeof TabsPanel;
};

const Tabs = TabsRoot as TabsComponent;

Tabs.List = TabsList;
Tabs.Tab = Tab;
Tabs.Panel = TabsPanel;
```

The shared Context used internally should also be typed.

**Interview Line**

Compound components are typed by combining the parent component type with typed static subcomponent properties.

### Q. How do you type slot-based components?

**Answer:**

Define each slot according to what it accepts.

For simple named slots:

```tsx
type CardProps = {
  header?: React.ReactNode;
  body: React.ReactNode;
  footer?: React.ReactNode;
};
```

Usage:

```tsx
<Card header={<CardTitle />} body={<CardContent />} />
```

If a slot needs data from the component, type it as a render function instead.

**Interview Line**

Slot-based components type each named slot as a node, component, or render function depending on the required API.

### Q. How do you type CSS modules in TypeScript?

**Answer:**

CSS Modules are typed through module declarations or generated typings.

A common declaration is:

```ts
declare module "*.module.css" {
  const classes: Record<string, string>;

  export default classes;
}
```

Then:

```tsx
import styles from "./button.module.css";

<button className={styles.primary} />;
```

For stricter typing, tools can generate exact class-name declarations.

**Interview Line**

CSS Modules are typed through module declarations or generated typings that map class names to strings.

### Q. How do you type inline styles in React?

**Answer:**

Use `React.CSSProperties`.

**Example:**

```tsx
const style: React.CSSProperties = {
  display: "flex",
  gap: 8,
  alignItems: "center",
};
```

Then:

```tsx
<div style={style} />
```

For a style prop:

```tsx
type Props = {
  style?: React.CSSProperties;
};
```

**Interview Line**

Use `React.CSSProperties` to type React inline style objects and style props.

## TypeScript with Node.js

### Q. How do you configure TypeScript for Node.js?

**Answer:**

Install TypeScript and Node.js type definitions:

```bash
npm install -D typescript @types/node
```

A typical modern Node.js configuration may look like:

```json
{
  "compilerOptions": {
    "target": "ES2022",
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "rootDir": "./src",
    "outDir": "./dist",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "types": ["node"]
  },
  "include": ["src"]
}
```

For projects bundled with another tool, `moduleResolution: "bundler"` may be more appropriate.

The configuration should match how the final JavaScript is executed.

**Interview Line**

Configure Node.js TypeScript with Node type definitions, strict checking, and module settings that match the actual Node runtime.

### Q. How do you type `process.env`?

**Answer:**

By default, values from `process.env` are typically typed as:

```ts
string | undefined;
```

because environment variables may be missing.

**Example:**

```ts
const apiUrl = process.env.API_URL;
```

Before using it, validate it:

```ts
if (!apiUrl) {
  throw new Error("API_URL is required");
}
```

You can also augment `ProcessEnv` for known variable names, but runtime validation is still necessary.

**Interview Line**

`process.env` values should be treated as `string | undefined` and validated before use.

### Q. How do you extend `NodeJS.ProcessEnv`?

**Answer:**

Use declaration merging in a `.d.ts` file.

**Example:**

```ts
declare namespace NodeJS {
  interface ProcessEnv {
    NODE_ENV: "development" | "test" | "production";

    API_URL: string;

    PORT?: string;
  }
}
```

A common file name is:

```text
src/types/env.d.ts
```

Make sure the file is included by `tsconfig.json`.

Important: this only changes TypeScript's understanding.

It does not guarantee the variables exist at runtime.

**Interview Line**

Extend `NodeJS.ProcessEnv` through declaration merging, but still validate environment variables at startup.

### Q. How do you type Express request and response?

**Answer:**

Express provides generic `Request` and `Response` types.

**Example:**

```ts
import type { Request, Response } from "express";

function getUsers(req: Request, res: Response) {
  res.json([]);
}
```

For more precise typing, use the generics provided by `Request`.

Conceptually:

```ts
Request<Params, ResponseBody, RequestBody, Query>;
```

This gives better type safety for route handlers.

**Interview Line**

Use Express `Request` and `Response` types, and provide generics when you need typed params, body, query, or response data.

### Q. How do you extend Express Request object?

**Answer:**

Use module augmentation when middleware adds custom properties to `req`.

**Example:**

```ts
import "express";

declare module "express-serve-static-core" {
  interface Request {
    user?: {
      id: string;
      role: string;
    };
  }
}
```

Then:

```ts
app.use((req, res, next) => {
  req.user = {
    id: "1",
    role: "admin",
  };

  next();
});
```

The runtime middleware must actually assign the property.

**Interview Line**

Extend Express `Request` with module augmentation when middleware adds custom request properties.

### Q. How do you type Express middleware?

**Answer:**

Use Express's `RequestHandler` type.

**Example:**

```ts
import type { RequestHandler } from "express";

const logger: RequestHandler = (req, res, next) => {
  console.log(req.method, req.url);

  next();
};
```

For error middleware, use:

```ts
ErrorRequestHandler;
```

because its signature includes the error parameter.

**Interview Line**

Type normal Express middleware with `RequestHandler` and error middleware with `ErrorRequestHandler`.

### Q. How do you type async Express handlers?

**Answer:**

An async Express handler usually returns a `Promise`.

**Example:**

```ts
import type { RequestHandler } from "express";

const getUser: RequestHandler = async (req, res, next) => {
  try {
    const user = await userService.getUser();

    res.json(user);
  } catch (error) {
    next(error);
  }
};
```

Depending on the Express version and project style, rejected async handlers may be forwarded automatically or explicitly through `next(error)`.

The important part is to keep error propagation consistent.

**Interview Line**

Async Express handlers return promises and should forward failures consistently into the application's error-handling pipeline.

### Q. How do you type request body, params, and query?

**Answer:**

Use the generic parameters of `Request`.

**Example:**

```ts
type Params = {
  id: string;
};

type Body = {
  name: string;
};

type Query = {
  includePosts?: string;
};
```

Then:

```ts
import type { Request, Response } from "express";

function updateUser(req: Request<Params, unknown, Body, Query>, res: Response) {
  req.params.id;
  req.body.name;
  req.query.includePosts;
}
```

The generic order is commonly:

```text
Params
ResponseBody
RequestBody
Query
```

**Interview Line**

Type Express route inputs through `Request` generics for params, response body, request body, and query.

### Q. How do you type database models?

**Answer:**

Use types that reflect the domain or persistence model returned by your database layer.

**Example:**

```ts
type UserRecord = {
  id: number;
  email: string;
  createdAt: Date;
};
```

If the database library generates types, prefer generated types where practical.

Keep database models separate from transport DTOs when their shapes differ.

For example:

```text
Database model
→ Service/domain model
→ API DTO
```

This prevents persistence details from leaking into higher layers.

**Interview Line**

Type database models around persistence data, but keep them separate from API and UI contracts when the shapes serve different purposes.

### Q. How do you type service-layer functions?

**Answer:**

Give service functions explicit input and output contracts.

**Example:**

```ts
type CreateUserInput = {
  email: string;
  name: string;
};

type User = {
  id: number;
  email: string;
  name: string;
};
```

Service:

```ts
async function createUser(input: CreateUserInput): Promise<User> {
  // business logic
}
```

Service-layer types should focus on business behavior rather than HTTP-specific objects such as `Request` and `Response`.

**Interview Line**

Type service functions with domain-specific inputs and outputs so business logic remains independent of transport concerns.

### Q. How do you type repository pattern in TypeScript?

**Answer:**

Define an interface describing persistence operations.

**Example:**

```ts
interface UserRepository {
  findById(id: number): Promise<User | null>;

  create(input: CreateUserInput): Promise<User>;
}
```

Implementation:

```ts
class SqlUserRepository implements UserRepository {
  async findById(id: number) {
    // SQL logic
  }

  async create(input: CreateUserInput) {
    // SQL logic
  }
}
```

The service can depend on the interface instead of a concrete database implementation.

**Interview Line**

Type repositories with interfaces so services depend on persistence contracts rather than concrete database implementations.

### Q. How do you handle errors in TypeScript backend apps?

**Answer:**

Use structured error types and a centralized error-handling layer.

Typical categories include:

- Validation errors
- Authentication errors
- Authorization errors
- Not-found errors
- Conflict errors
- Infrastructure errors
- Unexpected programmer errors

**Example:**

```ts
class AppError extends Error {
  constructor(
    message: string,
    public statusCode: number,
    public code: string,
  ) {
    super(message);

    this.name = "AppError";
  }
}
```

Then centralized middleware can convert errors into API responses.

Avoid scattering duplicate response logic across every route.

**Interview Line**

Backend errors should be represented consistently and translated into HTTP responses through centralized error handling.

### Q. How do you create typed custom errors?

**Answer:**

Extend the built-in `Error` class and add structured fields.

**Example:**

```ts
class NotFoundError extends Error {
  readonly statusCode = 404;

  readonly code = "NOT_FOUND";

  constructor(resource: string) {
    super(`${resource} not found`);

    this.name = "NotFoundError";
  }
}
```

Usage:

```ts
throw new NotFoundError("User");
```

Then narrow with:

```ts
if (error instanceof NotFoundError) {
  // typed handling
}
```

**Interview Line**

Create typed custom errors by extending `Error` with structured metadata such as status codes and application error codes.

### Q. How do you share types between frontend and backend?

**Answer:**

Share only contracts that genuinely belong to both sides.

Common approaches include:

- Shared workspace package
- Monorepo package
- OpenAPI-generated types
- GraphQL code generation
- Shared Zod schemas
- tRPC-style end-to-end typing
- Generated SDKs

**Example structure:**

```text
packages/
  contracts/
    user.ts

apps/
  frontend/
  backend/
```

A shared contract might contain:

```ts
export type UserDto = {
  id: number;
  name: string;
};
```

Both apps can import the contract.

**Interview Line**

Share stable transport contracts through a dedicated package or generated schema rather than duplicating them manually.

### Q. What are the risks of sharing too many backend types with frontend?

**Answer:**

Sharing too many backend types creates unnecessary coupling.

Risks include:

- Database models leaking into UI code
- Internal fields becoming frontend dependencies
- Security-sensitive properties being exposed conceptually
- Backend refactors breaking frontend code
- Persistence concerns shaping UI architecture
- Large shared packages becoming difficult to maintain

For example, a database model may contain:

```text
passwordHash
internalStatus
audit fields
database-only relations
```

The frontend usually needs a smaller DTO.

Prefer:

```text
Database model
→ API DTO
→ Frontend model
```

rather than sharing every backend type directly.

**Interview Line**

Share API contracts, not the entire backend domain or persistence model, to avoid tight coupling and accidental exposure of internal details.

## Testing TypeScript Code

### Q. How do you test TypeScript code?

**Answer:**

TypeScript code should be tested at two different levels:

1. **Runtime behavior**
2. **Type-level behavior**

Runtime tests verify what the program actually does.

Common tools include:

```text
Jest
Vitest
React Testing Library
Playwright
```

**Example:**

```ts
function add(a: number, b: number) {
  return a + b;
}
```

Runtime test:

```ts
import { expect, test } from "vitest";

test("adds two numbers", () => {
  expect(add(2, 3)).toBe(5);
});
```

Type-level testing verifies that valid types compile and invalid types are rejected.

**Interview Line**

Test TypeScript with normal runtime tests for behavior and type-level tests for compile-time contracts.

### Q. Does TypeScript remove the need for unit tests?

**Answer:**

No.

TypeScript checks type correctness, but it does not verify business logic or runtime behavior.

For example:

```ts
function add(a: number, b: number): number {
  return a - b;
}
```

This code is perfectly valid TypeScript, but the logic is wrong.

A unit test would catch it:

```ts
expect(add(2, 3)).toBe(5);
```

TypeScript also cannot guarantee:

- API responses are correct
- Database results are correct
- Network calls succeed
- UI behavior is correct
- Edge cases are handled
- Algorithms produce correct output

**Interview Line**

TypeScript prevents many type-related mistakes, but unit tests are still required to verify actual program behavior and business logic.

### Q. What should be tested if TypeScript already checks types?

**Answer:**

Focus tests on behavior rather than re-testing what TypeScript already guarantees.

Good things to test include:

- Business rules
- Edge cases
- State transitions
- Error handling
- API behavior
- Data transformations
- User interactions
- Integration between modules

Avoid tests such as:

```text
"this function accepts a string"
```

when TypeScript already enforces that statically.

**Example:**

Instead of testing that:

```ts
calculateDiscount(
  price: number
)
```

accepts a number, test:

```text
correct discount calculation
minimum values
maximum values
invalid business cases
```

**Interview Line**

Use runtime tests for behavior, edge cases, and integrations, while letting TypeScript handle static type correctness.

### Q. How do you test runtime behavior separately from types?

**Answer:**

Use normal test runners for runtime behavior and the TypeScript compiler or type-testing tools for type behavior.

Runtime:

```bash
vitest
```

or:

```bash
jest
```

Type checking:

```bash
tsc --noEmit
```

A project may run both:

```json
{
  "scripts": {
    "test": "vitest",
    "typecheck": "tsc --noEmit"
  }
}
```

This separates:

```text
Does the code behave correctly?
```

from:

```text
Does the code satisfy its type contracts?
```

**Interview Line**

Run runtime tests and type checks as separate validation layers because they catch different classes of problems.

### Q. How do you test custom type utilities?

**Answer:**

Custom type utilities can be tested by asserting their resulting types.

Suppose you have:

```ts
type Nullable<T> = T | null;
```

You can test it using type assertions such as:

```ts
type Result = Nullable<string>;
```

and verify that it equals:

```ts
string | null;
```

With tools such as `expectTypeOf`:

```ts
expectTypeOf<Nullable<string>>().toEqualTypeOf<string | null>();
```

You should also test invalid cases when relevant.

**Interview Line**

Test custom utility types by asserting the types they produce and verifying that invalid usages fail compilation.

### Q. What is type-level testing?

**Answer:**

Type-level testing verifies TypeScript contracts without testing runtime behavior.

It checks things such as:

- Inferred types
- Generic behavior
- Utility types
- Invalid assignments
- Overload behavior
- Public library APIs

**Example:**

```ts
type Result = DeepPartial<User>;
```

A type-level test may verify:

```text
nested properties became optional
unexpected properties remain invalid
```

Type-level tests are especially useful for reusable libraries and advanced generic APIs.

**Interview Line**

Type-level testing verifies compile-time TypeScript behavior such as inference, constraints, utility types, and invalid usages.

### Q. What is `tsd`?

**Answer:**

`tsd` is a testing tool designed for TypeScript type definitions.

It is commonly used by library authors to verify public TypeScript APIs.

**Example:**

```ts
import { expectType } from "tsd";

const value = identity("hello");

expectType<string>(value);
```

It can also verify expected type errors.

**Example concept:**

```ts
expectError(someInvalidCall());
```

This is useful when publishing libraries whose type behavior is part of the product API.

**Interview Line**

`tsd` is a dedicated tool for testing whether TypeScript APIs infer valid types and reject invalid usages.

### Q. What is `expectTypeOf`?

**Answer:**

`expectTypeOf` is a type assertion utility commonly available in Vitest.

It lets you verify types during tests without checking runtime values.

**Example:**

```ts
import { expectTypeOf } from "vitest";

const user = {
  id: 1,
  name: "John",
};

expectTypeOf(user.id).toEqualTypeOf<number>();
```

It can also compare function signatures and generic results.

**Example:**

```ts
expectTypeOf<ReturnType<typeof getUser>>().toEqualTypeOf<Promise<User>>();
```

**Interview Line**

`expectTypeOf` is a compile-time assertion helper for verifying inferred and declared TypeScript types.

### Q. How do you verify that invalid types fail compilation?

**Answer:**

Use tools or compiler directives designed for expected type errors.

One built-in approach is:

```ts
// @ts-expect-error
```

**Example:**

```ts
function square(value: number) {
  return value * value;
}

// @ts-expect-error
square("10");
```

The test succeeds only if TypeScript actually reports an error on the next line.

If the line unexpectedly becomes valid, TypeScript reports that the `@ts-expect-error` directive is unused.

For library testing, tools such as `tsd` provide dedicated error assertions.

**Interview Line**

Use `@ts-expect-error` or type-testing tools such as `tsd` to verify that invalid usages are rejected by the compiler.

### Q. How do you mock typed functions in Jest or Vitest?

**Answer:**

Use the mocking APIs provided by the test framework while preserving the original function signature.

With Vitest:

```ts
import { vi } from "vitest";

const fetchUser = vi.fn<(id: number) => Promise<User>>();
```

With Jest, you can use typed mocks such as:

```ts
jest.MockedFunction<typeof fetchUser>;
```

**Example:**

```ts
const mockedFetchUser = fetchUser as jest.MockedFunction<typeof fetchUser>;
```

The goal is to keep argument and return types aligned with the real function.

**Interview Line**

Mock functions with the framework's typed mock helpers so test doubles preserve the real function's parameters and return type.

### Q. How do you type mocked API responses?

**Answer:**

Use the same DTO or schema-derived type used by the production API layer.

**Example:**

```ts
type UserDto = {
  id: number;
  name: string;
};
```

Mock:

```ts
const mockUser: UserDto = {
  id: 1,
  name: "John",
};
```

For generic wrappers:

```ts
const response: ApiResponse<UserDto> = {
  success: true,
  data: mockUser,
};
```

Avoid using:

```ts
as any
```

because that can hide broken mock data.

**Interview Line**

Type mocked API responses with the same DTO or contract type used in production so test data stays aligned with the real API shape.

### Q. How do you type mocked React props?

**Answer:**

Reuse the real component prop type instead of duplicating it.

**Example:**

```tsx
type ButtonProps = {
  label: string;
  disabled?: boolean;
};
```

Mock props:

```tsx
const props: ButtonProps = {
  label: "Save",
  disabled: false,
};
```

If the prop type is not exported directly, derive it:

```tsx
type ButtonProps = React.ComponentProps<typeof Button>;
```

Then use:

```tsx
const props: ButtonProps = {
  label: "Save",
};
```

**Interview Line**

Reuse or derive the actual component prop type so mocked props stay synchronized with the component API.

### Q. How do you handle TypeScript errors in test files?

**Answer:**

Treat test files like production code and keep them type-safe.

Good approaches include:

- Fix actual type errors
- Type mocks correctly
- Use proper test framework types
- Use `@ts-expect-error` only for intentional compile-failure tests
- Avoid broad `any`

For setup files, ensure framework globals are included.

For Vitest:

```json
{
  "compilerOptions": {
    "types": ["vitest/globals"]
  }
}
```

For Jest:

```json
{
  "compilerOptions": {
    "types": ["jest"]
  }
}
```

**Interview Line**

Keep test code type-safe and use compiler-error directives only when intentionally testing invalid TypeScript.

### Q. How do you configure TypeScript with Jest?

**Answer:**

A common setup uses Jest with either `ts-jest` or a JavaScript transformer such as Babel or SWC.

With `ts-jest`:

```bash
npm install -D \
  jest \
  ts-jest \
  @types/jest
```

Example configuration:

```ts
import type { Config } from "jest";

const config: Config = {
  preset: "ts-jest",

  testEnvironment: "node",
};

export default config;
```

Your `tsconfig` should include Jest types when using Jest globals:

```json
{
  "compilerOptions": {
    "types": ["node", "jest"]
  }
}
```

In larger projects, test-specific settings may live in:

```text
tsconfig.test.json
```

**Interview Line**

Configure Jest with TypeScript through `ts-jest` or another transformer and include Jest's type definitions in the test TypeScript configuration.

### Q. How do you configure TypeScript with Vitest?

**Answer:**

Vitest works naturally with Vite and TypeScript because Vite already transpiles TypeScript syntax.

Install:

```bash
npm install -D vitest
```

Example test:

```ts
import { describe, expect, test } from "vitest";
```

If you use global test APIs, include:

```json
{
  "compilerOptions": {
    "types": ["vitest/globals"]
  }
}
```

A typical project keeps runtime testing and full type checking separate:

```json
{
  "scripts": {
    "test": "vitest",
    "typecheck": "tsc --noEmit"
  }
}
```

Vitest runs the tests, while `tsc --noEmit` performs full TypeScript checking.

**Interview Line**

Vitest integrates directly with Vite's TypeScript pipeline, while `tsc --noEmit` should still be used for full project type checking.

## Debugging & Best Practices

### Q. What are common TypeScript errors you’ve faced?

**Answer:**

1. Type Mismatch

```ts
let age: number = "25"; // ❌
```

👉 Assigning wrong type

2. Property Does Not Exist

```ts
user.name; // ❌ if type not defined
```

👉 Missing or incorrect type definition

3. Possibly Null / Undefined

```ts
user.name.toUpperCase(); // ❌
```

👉 user might be null

4. Implicit any

```ts
function add(a, b) {
  // ❌
  return a + b;
}
```

👉 Happens when noImplicitAny is enabled

5. Union Type Errors

```ts
let val: string | number;
val.toUpperCase(); // ❌
```

👉 Need type narrowing

6. Incorrect Function Types

```ts
function fn(): string {
  return 10; // ❌
}
```

**Interview Line**

Common TypeScript errors include type mismatches, null safety issues, implicit any, and improper handling of union types.

### Q. How do you improve type safety?

**Answer:**

Best Practices

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

**Interview Line**

Type safety is improved by enabling strict mode, avoiding any, using proper types, and applying type guards.

### Q. What is strict mode?

**Answer:**

Definition

A set of strict type-checking rules in TypeScript

Enable

```json
{
  "compilerOptions": {
    "strict": true
  }
}
```

Includes

- noImplicitAny
- strictNullChecks
- strictFunctionTypes
- strictPropertyInitialization

Benefits

- Early error detection ✅
- Safer code ✅
- Better maintainability ✅

**Interview Line**

Strict mode enables all strict type checks, improving code reliability and preventing common runtime errors.

### Q. How do you debug type issues?

**Answer:**

Techniques

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

**Interview Line**

Debugging type issues involves inspecting inferred types, breaking complex types, and leveraging TypeScript’s detailed error messages.

### Q. When should you use `as` (type assertion)?

**Answer:**

Definition

Tells TypeScript to treat a value as a specific type

Example

```ts
const input = document.getElementById("name") as HTMLInputElement;
```

When to Use

✅ DOM elements

```ts
const el = document.querySelector("input") as HTMLInputElement;
```

✅ When TS cannot infer correctly

```ts
const value = data as string;
```

✅ Third-party libraries

Rule

👉 Use only when you're sure about the type

**Interview Line**

Type assertions are used when TypeScript cannot infer types, but should be used cautiously as they bypass type checking.

### Q. Risks of type assertions

**Answer:**

Main Problem

👉 TypeScript trusts you blindly

Example

```ts
const value = "hello" as unknown as number;
```

❌ No error, but wrong type → runtime bug

Risks

- Runtime errors ❌
- Loss of type safety ❌
- Hard-to-debug issues ❌

Safer Alternatives

- Type guards ✅
- Proper typing ✅
- Generics ✅

**Interview Line**

Type assertions can introduce runtime bugs by bypassing type checks, so they should be used sparingly.

### Q. How do you read complex TypeScript error messages?

**Answer:**

Start from the top-level incompatibility and work inward instead of reading the entire message at once.

A useful approach is:

1. Identify the source type.
2. Identify the target type.
3. Find the first property or generic parameter that differs.
4. Ignore repeated nested details until the root mismatch is clear.

**Example:**

```ts
type User = {
  id: number;
  name: string;
};

const value = {
  id: "1",
  name: "John",
};

const user: User = value;
```

The important part of the error is that:

```text
string
```

is not assignable to:

```text
number
```

For large generic errors, temporarily create named intermediate types or variables so TypeScript produces smaller messages.

**Interview Line**

Read TypeScript errors from the outer assignment inward and focus first on the earliest concrete type mismatch.

### Q. What is the most common cause of generic type errors?

**Answer:**

A common cause is that TypeScript cannot infer the intended relationship between generic parameters.

Typical reasons include:

- Generic constraints are too broad
- Generic constraints are too strict
- Input values were widened
- Multiple generic arguments conflict
- A callback returns a different type than expected
- The API has too many generic relationships

**Example:**

```ts
function getProperty<T, K extends keyof T>(obj: T, key: K) {
  return obj[key];
}
```

If the key is typed simply as:

```ts
string;
```

TypeScript may reject it because not every string is a valid key of `T`.

**Interview Line**

Generic errors usually come from broken relationships between inferred types, constraints, or widened values.

### Q. How do you simplify complex types?

**Answer:**

Break large type expressions into smaller named types.

Instead of:

```ts
type Result = Partial<Pick<Omit<User, "id">, "name" | "email">>;
```

create intermediate concepts:

```ts
type EditableUser = Omit<User, "id">;

type ContactFields = Pick<EditableUser, "name" | "email">;

type OptionalContact = Partial<ContactFields>;
```

Also consider replacing clever generic utilities with an explicit interface when the explicit version is easier to understand.

**Interview Line**

Simplify complex types by introducing named intermediate types and preferring explicit models over unnecessary type-level cleverness.

### Q. When should you create a named type instead of inline typing?

**Answer:**

Use a named type when the shape is:

- Reused
- Complex
- Part of a public API
- Important to the domain
- Difficult to understand inline

Inline typing is fine for very small one-off shapes.

**Example:**

Inline:

```ts
function printUser(user: { id: number; name: string }) {}
```

Named:

```ts
type User = {
  id: number;
  name: string;
};

function printUser(user: User) {}
```

The named version communicates intent more clearly.

**Interview Line**

Create a named type when a structure is reused, domain-relevant, or complex enough that naming improves readability.

### Q. Why should types be readable?

**Answer:**

Types are part of the codebase's documentation and API design.

Readable types help developers understand:

- What data is expected
- Which states are valid
- Which fields are optional
- How functions relate to each other
- Why a type error occurred

A technically correct type that takes significant effort to understand can reduce maintainability.

**Interview Line**

Readable types improve documentation, debugging, onboarding, and long-term maintainability.

### Q. What is over-engineering in TypeScript?

**Answer:**

Over-engineering happens when type logic becomes more complex than the problem being solved.

Examples include:

- Deep conditional types for simple objects
- Generic abstractions used once
- Multiple helper types around trivial data
- Complex branded types without a real domain need
- Large mapped-type pipelines that are harder than explicit types

**Example:**

If this is sufficient:

```ts
type User = {
  id: number;
  name: string;
};
```

there is little value in deriving it through several layers of mapped and conditional types.

**Interview Line**

TypeScript is over-engineered when type abstractions add more complexity than safety or reuse.

### Q. When should you avoid advanced types?

**Answer:**

Avoid advanced types when:

- The domain is simple
- The type is used only once
- Team members cannot easily understand it
- Compiler errors become unreadable
- Build performance suffers
- A normal interface expresses the intent clearly

Advanced types are useful when they remove duplication or preserve important relationships.

They should not be used only because they are possible.

**Interview Line**

Use advanced types when they clearly improve correctness or reuse, not when a simple explicit type communicates the model better.

### Q. How do you balance type safety and readability?

**Answer:**

Use the simplest type that still prevents meaningful bugs.

A practical approach is:

- Use strict TypeScript settings
- Prefer inference for local values
- Name important domain types
- Use generics only where relationships matter
- Use runtime validation at external boundaries
- Avoid assertions unless necessary
- Simplify complex utility chains

The goal is not maximum type complexity.

The goal is useful safety with understandable code.

**Interview Line**

Balance type safety and readability by using strict but simple types that model real constraints without unnecessary abstraction.

### Q. Why should you avoid too many type assertions?

**Answer:**

Type assertions tell TypeScript to trust the developer without proving the value actually matches the asserted type.

**Example:**

```ts
const user = data as User;
```

If `data` does not really match `User`, TypeScript will not protect you.

Frequent assertions can hide:

- API contract bugs
- Nullability problems
- Incorrect DOM assumptions
- Broken generic designs

Prefer narrowing and validation instead.

**Interview Line**

Too many assertions weaken TypeScript because they bypass the compiler instead of proving type safety.

### Q. Why should you avoid double assertion like `as unknown as Type`?

**Answer:**

A double assertion forces TypeScript to accept conversions between otherwise incompatible types.

**Example:**

```ts
const user = value as unknown as User;
```

This effectively says:

```text
Ignore compatibility checks.
Trust me.
```

It can hide real modeling problems and cause runtime failures.

Use it only in rare interoperability cases where you have an external guarantee that TypeScript cannot represent.

**Interview Line**

`as unknown as Type` bypasses normal compatibility checks and should be treated as an escape hatch, not normal application code.

### Q. What is unsafe type casting?

**Answer:**

Unsafe type casting is forcing TypeScript to treat a value as a type without sufficient runtime or structural proof.

**Example:**

```ts
const input = document.querySelector("#age") as HTMLInputElement;
```

If the selector actually points to another element, the assertion is wrong.

Another example:

```ts
const user = response as User;
```

without validating the response.

**Interview Line**

Unsafe type casting forces a type assumption that the runtime value may not actually satisfy.

### Q. How do you replace type assertions with type guards?

**Answer:**

Use runtime checks that also narrow the TypeScript type.

**Unsafe:**

```ts
const user = value as User;
```

Safer:

```ts
function isUser(value: unknown): value is User {
  if (typeof value !== "object" || value === null) {
    return false;
  }

  const candidate = value as Record<string, unknown>;

  return typeof candidate.id === "number" && typeof candidate.name === "string";
}
```

Then:

```ts
if (isUser(value)) {
  console.log(value.name);
}
```

**Interview Line**

Replace assertions with type guards when runtime data needs to be proven before TypeScript can safely narrow it.

### Q. How do you make impossible states impossible?

**Answer:**

Use discriminated unions so invalid state combinations cannot be represented.

**Bad Model:**

```ts
type State = {
  loading: boolean;
  data?: User;
  error?: string;
};
```

This allows conflicting combinations.

Better:

```ts
type State =
  | {
      status: "loading";
    }
  | {
      status: "success";
      data: User;
    }
  | {
      status: "error";
      error: string;
    };
```

Now each state contains only the fields that make sense.

**Interview Line**

Make impossible states impossible by modeling valid states explicitly with discriminated unions.

### Q. What are good naming conventions for types and interfaces?

**Answer:**

Use names that describe the role of the type rather than how it was implemented.

Good examples:

```text
User
UserDto
UserFormValues
CreateUserInput
ApiResponse
AuthContextValue
PermissionMap
```

Avoid vague names such as:

```text
Data
ObjectType
Info
Temp
Thing
```

Useful suffixes include:

```text
Props
State
Action
Input
Output
Dto
Response
Config
Options
```

**Interview Line**

Type names should describe domain meaning or responsibility so their purpose is obvious at the point of use.

### Q. Should interface names start with `I`?

**Answer:**

Usually no.

Older conventions sometimes used:

```ts
IUser;
IRepository;
```

Modern TypeScript projects more commonly use:

```ts
User;
Repository;
```

The type system already tells you whether something is an interface.

Prefixes can add noise without useful information.

However, if an existing codebase consistently uses the `I` convention, following team consistency may be more important.

**Interview Line**

Modern TypeScript usually avoids the `I` prefix for interfaces and prefers domain-focused names.

### Q. Where should shared types be placed?

**Answer:**

Place shared types at the narrowest scope where they are genuinely shared.

Examples:

```text
feature-local type
→ inside feature

shared UI type
→ shared UI module

API contract
→ contracts package/module

global application type
→ shared types area
```

Avoid putting every type into one large:

```text
types.ts
```

file because it becomes difficult to navigate and increases coupling.

**Interview Line**

Shared types should live close to the scope where they are reused instead of being collected into one global type file.

### Q. When should types be colocated with components?

**Answer:**

Colocate types when they belong only to that component or feature.

**Example:**

```text
UserCard.tsx
UserCard.types.ts
```

or directly:

```tsx
type UserCardProps = {
  user: User;
};
```

inside the component file.

Move a type outward only when multiple modules genuinely need it.

This prevents premature global abstractions.

**Interview Line**

Colocate component-specific types and promote them to shared modules only when real reuse appears.

### Q. How do you avoid circular type dependencies?

**Answer:**

Keep dependency direction clear.

Useful strategies include:

- Move shared contracts into a lower-level module
- Avoid feature A importing feature B while feature B imports feature A
- Separate domain types from feature implementation files
- Use `import type` for type-only imports
- Split large shared files by responsibility

**Example structure:**

```text
domain/
  user.ts

features/
  profile/
  admin/
```

Both features can import from `domain/user.ts` without importing each other.

**Interview Line**

Avoid circular type dependencies by moving shared contracts into neutral lower-level modules and keeping feature dependencies one-directional.

### Q. How do you organize types in feature-based architecture?

**Answer:**

Keep types close to the feature that owns them.

**Example:**

```text
features/
  users/
    api/
      user.dto.ts

    components/
      UserCard.tsx

    model/
      user.types.ts

    services/
      user.service.ts
```

Cross-feature contracts can move into:

```text
shared/
contracts/
domain/
```

depending on the architecture.

The key idea is ownership.

A feature should own its internal types instead of depending on one giant global type directory.

**Interview Line**

In feature-based architecture, colocate internal types with the owning feature and move only truly shared contracts into shared modules.

### Q. How do you review TypeScript code in pull requests?

**Answer:**

Review both runtime logic and type-system quality.

Useful questions include:

- Are types modeling real domain rules?
- Are there unnecessary `any` values?
- Are assertions hiding problems?
- Are nullable values handled?
- Are external inputs validated?
- Are generics actually needed?
- Are types readable?
- Are impossible states prevented?
- Are shared types placed at the correct scope?
- Are API and UI models unnecessarily coupled?

Also check compiler configuration changes carefully because options such as:

```text
strict
skipLibCheck
noUncheckedIndexedAccess
```

can affect the whole codebase.

**Interview Line**

TypeScript code review should check correctness, readability, unsafe escapes, domain modeling, and whether type complexity is justified.

## Build Tools & Ecosystem

### Q. Difference between `tsc`, Babel, SWC, and esbuild

**Answer:**

These tools can all be part of a TypeScript build pipeline, but they serve different purposes.

#### `tsc`

`tsc` is the official TypeScript compiler. It can type-check TypeScript, transpile TypeScript to JavaScript, generate declaration files, and build project references.

#### Babel

Babel transforms JavaScript and TypeScript syntax. With `@babel/preset-typescript`, Babel removes TypeScript syntax, but it does not perform TypeScript type checking.

#### SWC

SWC is a high-performance compiler written in Rust and is commonly used for fast JavaScript and TypeScript transformation.

#### esbuild

esbuild is a very fast JavaScript/TypeScript bundler and transformer written in Go. It removes TypeScript syntax during transformation but does not replace full TypeScript type checking.

A common architecture is:

```text
Fast transpiler/bundler
+
tsc --noEmit
```

**Interview Line**

`tsc` performs TypeScript type checking and compilation, while Babel, SWC, and esbuild are primarily fast transformation/build tools and generally rely on separate type checking.

### Q. Does Babel type-check TypeScript?

**Answer:**

No.

Babel can parse TypeScript syntax and remove type annotations using:

```text
@babel/preset-typescript
```

but it does not validate whether those types are correct.

**Example:**

```ts
const age: number = "hello";
```

Babel can still transform this because it strips the TypeScript annotation.

Type checking should be performed separately with:

```bash
tsc --noEmit
```

**Interview Line**

Babel transpiles TypeScript syntax but does not perform TypeScript type checking.

### Q. Why do some projects use both `tsc` and Babel?

**Answer:**

They use each tool for a different responsibility.

A common setup is:

```text
Babel
→ JavaScript transformation

tsc
→ Type checking
→ Declaration generation
```

For library projects, TypeScript may generate only declarations:

```json
{
  "compilerOptions": {
    "declaration": true,
    "emitDeclarationOnly": true
  }
}
```

**Interview Line**

Projects often use Babel for transpilation and `tsc` separately for type checking and declaration generation.

### Q. How does Vite handle TypeScript?

**Answer:**

Vite supports `.ts` and `.tsx` files directly.

It transpiles TypeScript syntax quickly during development rather than running the full TypeScript type checker as part of each module transformation.

Conceptually:

```text
TypeScript source
↓
Fast transpilation
↓
Browser-compatible JavaScript
```

Type checking is handled separately.

**Interview Line**

Vite transpiles TypeScript as part of its fast development pipeline but keeps full type checking separate.

### Q. Does Vite perform type checking by default?

**Answer:**

No.

Vite transpiles TypeScript but does not perform full TypeScript type checking by default.

A common dedicated check is:

```bash
tsc --noEmit
```

Your editor may show type errors during development, but CI and production builds should also run an explicit type-check step.

**Interview Line**

Vite transpiles TypeScript by default but does not run full TypeScript type checking.

### Q. How do you add type checking to Vite build?

**Answer:**

Run TypeScript checking separately before the Vite build.

**Example:**

```json
{
  "scripts": {
    "typecheck": "tsc --noEmit",
    "build": "tsc --noEmit && vite build"
  }
}
```

During development:

```bash
tsc --noEmit --watch
```

can run in a separate process.

Some projects also use `vite-plugin-checker` to surface type errors during development.

**Interview Line**

Add Vite type checking by running `tsc --noEmit` separately, typically before the production build or continuously in watch mode.

### Q. What is `ts-loader`?

**Answer:**

`ts-loader` is a Webpack loader that lets Webpack process TypeScript files through the TypeScript compiler.

**Example:**

```js
module: {
  rules: [
    {
      test: /\.tsx?$/,
      use: "ts-loader",
      exclude: /node_modules/,
    },
  ],
}
```

It can perform transpilation and type checking.

For faster builds, projects may use:

```js
transpileOnly: true;
```

and move type checking to another process.

**Interview Line**

`ts-loader` integrates the TypeScript compiler into Webpack so `.ts` and `.tsx` files can be compiled through the Webpack pipeline.

### Q. What is `babel-loader` with TypeScript?

**Answer:**

`babel-loader` lets Webpack process files through Babel.

With `@babel/preset-typescript`, it can transform TypeScript files.

A common setup is:

```text
babel-loader
→ transpilation

tsc --noEmit
or
fork-ts-checker-webpack-plugin
→ type checking
```

Babel removes TypeScript syntax but does not perform type checking.

**Interview Line**

`babel-loader` can transpile TypeScript through Babel, but type checking must be handled separately.

### Q. What is `fork-ts-checker-webpack-plugin`?

**Answer:**

`fork-ts-checker-webpack-plugin` performs TypeScript type checking in a separate process from Webpack's main compilation work.

It is commonly paired with:

```text
ts-loader with transpileOnly
```

or:

```text
babel-loader
```

Conceptually:

```text
Webpack
├── fast transpilation
└── separate type-checking process
```

This can improve development build responsiveness.

**Interview Line**

`fork-ts-checker-webpack-plugin` moves TypeScript type checking out of Webpack's main transformation process.

### Q. What is incremental compilation?

**Answer:**

Incremental compilation lets TypeScript reuse information from a previous build instead of analyzing the whole project from scratch each time.

Enable it with:

```json
{
  "compilerOptions": {
    "incremental": true
  }
}
```

This is useful for large applications, monorepos, and repeated builds.

**Interview Line**

Incremental compilation speeds up repeated TypeScript builds by reusing information from previous compilations.

### Q. What is `tsbuildinfo` file?

**Answer:**

A `.tsbuildinfo` file stores metadata used by TypeScript for incremental builds.

It can contain information about:

- Project graph
- Source versions
- Build state
- Dependency relationships

**Example:**

```json
{
  "compilerOptions": {
    "incremental": true,
    "tsBuildInfoFile": "./node_modules/.cache/app.tsbuildinfo"
  }
}
```

The file is not used by your application at runtime and can be regenerated.

**Interview Line**

`.tsbuildinfo` stores TypeScript incremental-build metadata so later compilations can avoid unnecessary work.

### Q. How do you speed up TypeScript compilation?

**Answer:**

Common strategies include:

- Enable `incremental`
- Use project references for large codebases
- Keep `include` and `exclude` focused
- Use `skipLibCheck` when appropriate
- Separate fast transpilation from type checking
- Avoid unnecessarily complex recursive or conditional types

**Example architecture:**

```text
Vite / SWC / esbuild
→ transpilation

tsc --noEmit
→ type checking
```

**Interview Line**

Speed up TypeScript with incremental builds, focused project scopes, project references, and separate fast transpilation from type checking.

### Q. How do you handle type checking in CI/CD?

**Answer:**

Run type checking as an explicit CI step.

**Example:**

```json
{
  "scripts": {
    "typecheck": "tsc --noEmit",
    "test": "vitest run",
    "build": "vite build"
  }
}
```

A CI pipeline can run:

```bash
npm ci
npm run typecheck
npm test
npm run build
```

If type checking fails, the pipeline should fail.

**Interview Line**

CI should run TypeScript checking explicitly so code with type errors cannot pass the deployment pipeline.

### Q. How do you publish a TypeScript package?

**Answer:**

A typical TypeScript package publishes compiled JavaScript plus declaration files.

**Example structure:**

```text
src/
  index.ts

dist/
  index.js
  index.d.ts
```

Typical flow:

```text
Write TypeScript
↓
Build JavaScript
↓
Generate .d.ts files
↓
Configure package.json
↓
Publish package
```

Modern packages often use the `exports` field for precise public entry points.

**Interview Line**

Publish TypeScript libraries as JavaScript runtime files plus declaration files, with package metadata pointing to the correct entries.

### Q. How do you generate declaration files for a package?

**Answer:**

Enable:

```json
{
  "compilerOptions": {
    "declaration": true
  }
}
```

TypeScript then generates `.d.ts` files.

If another tool handles JavaScript generation, use:

```json
{
  "compilerOptions": {
    "declaration": true,
    "emitDeclarationOnly": true
  }
}
```

**Interview Line**

Generate package typings with `declaration: true`, and use `emitDeclarationOnly` when another tool produces the JavaScript.

### Q. What is the `types` field in package.json?

**Answer:**

The `types` field tells TypeScript where the package's main declaration file is located.

**Example:**

```json
{
  "types": "./dist/index.d.ts"
}
```

When a consumer imports the package, TypeScript uses this file to understand the public API.

**Interview Line**

The `types` field points TypeScript to the package's main `.d.ts` declaration entry.

### Q. What is the `exports` field in package.json?

**Answer:**

The `exports` field defines which package entry points are public and which files should be used for different module conditions.

**Example:**

```json
{
  "exports": {
    ".": {
      "types": "./dist/index.d.ts",
      "import": "./dist/index.js",
      "require": "./dist/index.cjs"
    }
  }
}
```

It can:

- Restrict private internal files
- Define subpath exports
- Provide separate ESM and CommonJS entries
- Associate declaration files with exports

**Interview Line**

The `exports` field defines public package entry points and can map consumers to ESM, CommonJS, and type declarations.

### Q. How do you support both ESM and CommonJS in a TypeScript package?

**Answer:**

Build separate ESM and CommonJS outputs and expose them through conditional exports.

**Example structure:**

```text
dist/
  index.js
  index.cjs
  index.d.ts
```

Example `package.json`:

```json
{
  "type": "module",
  "exports": {
    ".": {
      "types": "./dist/index.d.ts",
      "import": "./dist/index.js",
      "require": "./dist/index.cjs"
    }
  }
}
```

Tools such as `tsup`, Rollup, esbuild, or Vite library mode can produce multiple module formats.

Dual packages should be tested carefully because ESM and CommonJS resolution differ.

If all consumers support modern ESM, publishing ESM-only can be simpler.

**Interview Line**

Support both ESM and CommonJS by producing separate outputs and routing `import` and `require` consumers through conditional `exports`.

## Scenario-Based Questions

### Q. An API returns different response shapes for success and failure. How will you type it?

**Answer:**

Use a discriminated union so TypeScript can narrow the response based on a common discriminator.

**Example:**

```ts
type ApiSuccess<T> = {
  success: true;
  data: T;
};

type ApiFailure = {
  success: false;
  error: {
    code: string;
    message: string;
  };
};

type ApiResponse<T> = ApiSuccess<T> | ApiFailure;
```

Usage:

```ts
function handleResponse(response: ApiResponse<User>) {
  if (response.success) {
    console.log(response.data.name);
  } else {
    console.log(response.error.message);
  }
}
```

This is safer than creating one object with optional `data` and `error` fields.

**Interview Line**

Model different API response shapes with a discriminated union so success and failure fields stay mutually exclusive.

### Q. A value can be string, number, or boolean. How will you safely handle it?

**Answer:**

Use union types and type narrowing.

**Example:**

```ts
function processValue(value: string | number | boolean) {
  if (typeof value === "string") {
    return value.toUpperCase();
  }

  if (typeof value === "number") {
    return value.toFixed(2);
  }

  return value ? "Yes" : "No";
}
```

TypeScript narrows the type in each branch.

Avoid assertions such as:

```ts
value as string;
```

unless you have a real guarantee.

**Interview Line**

Handle union values with runtime narrowing such as `typeof`, not unsafe casting.

### Q. You receive unknown JSON from localStorage. How will you type and validate it?

**Answer:**

Treat the parsed value as `unknown`, then validate it before using it as an application type.

**Example:**

```ts
type User = {
  id: number;
  name: string;
};

function isUser(value: unknown): value is User {
  if (typeof value !== "object" || value === null) {
    return false;
  }

  const user = value as Record<string, unknown>;

  return typeof user.id === "number" && typeof user.name === "string";
}
```

Usage:

```ts
const raw = localStorage.getItem("user");

if (raw) {
  try {
    const parsed: unknown = JSON.parse(raw);

    if (isUser(parsed)) {
      console.log(parsed.name);
    }
  } catch {
    // malformed JSON
  }
}
```

A schema library such as Zod is useful for larger structures.

**Interview Line**

Parse browser storage into `unknown`, then validate the runtime shape before promoting it to a trusted type.

### Q. TypeScript says object is possibly null. How will you fix it safely?

**Answer:**

Handle the nullable case instead of immediately using the non-null assertion operator.

**Example:**

```ts
const button = document.querySelector<HTMLButtonElement>("#save");

if (!button) {
  return;
}

button.disabled = true;
```

Other safe options include:

```ts
button?.click();
```

or throwing explicitly when absence is a programming error:

```ts
if (!button) {
  throw new Error("Save button not found");
}
```

Avoid:

```ts
button!.click();
```

unless the guarantee is truly reliable.

**Interview Line**

Fix nullable errors with narrowing, optional chaining, or explicit failure rather than blindly using `!`.

### Q. A component prop should accept either `href` or `onClick`, but not both. How will you type it?

**Answer:**

Use mutually exclusive union branches and `never`.

**Example:**

```tsx
type ButtonProps =
  | {
      href: string;
      onClick?: never;
    }
  | {
      href?: never;
      onClick: () => void;
    };
```

Now these are valid:

```tsx
<Button
  href="/docs"
/>

<Button
  onClick={() => {}}
/>
```

But this is rejected:

```tsx
<Button href="/docs" onClick={() => {}} />
```

**Interview Line**

Use a union with `never` to make props mutually exclusive at compile time.

### Q. You need a reusable table component with typed rows. How will you design its types?

**Answer:**

Use a generic row type and tie column keys to `keyof T`.

**Example:**

```tsx
type Column<T> = {
  key: keyof T;
  header: string;
  render?: (row: T) => React.ReactNode;
};

type TableProps<T> = {
  rows: T[];
  columns: Column<T>[];
};
```

Usage:

```tsx
type User = {
  id: number;
  name: string;
};

const columns: Column<User>[] = [
  {
    key: "name",
    header: "Name",
  },
];
```

This prevents invalid keys such as:

```ts
"email";
```

when `email` does not exist on `User`.

**Interview Line**

Design reusable tables with generics and `keyof T` so columns stay type-safe against the row model.

### Q. You need a form component where field names must match form data keys. How will you type it?

**Answer:**

Use generics with `K extends keyof T`.

**Example:**

```tsx
type FieldProps<T, K extends keyof T> = {
  name: K;
  value: T[K];
  onChange: (value: T[K]) => void;
};
```

For:

```ts
type FormData = {
  name: string;
  age: number;
};
```

valid names are:

```text
"name"
"age"
```

and the value type is automatically tied to the selected field.

**Interview Line**

Use `K extends keyof T` and `T[K]` so form field names and values stay correctly linked.

### Q. You need a function that accepts only keys of an object. How will you type it?

**Answer:**

Use `keyof`.

**Example:**

```ts
function getValue<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}
```

Usage:

```ts
const user = {
  id: 1,
  name: "John",
};

getValue(user, "name");
```

Invalid keys are rejected.

**Interview Line**

Use `K extends keyof T` to restrict a function argument to valid object keys.

### Q. You need to map API status codes to messages. How will you type the object?

**Answer:**

Use `Record` when every supported key must have a value.

**Example:**

```ts
type ApiStatus = 400 | 401 | 403 | 404 | 500;

const messages: Record<ApiStatus, string> = {
  400: "Bad request",
  401: "Unauthorized",
  403: "Forbidden",
  404: "Not found",
  500: "Server error",
};
```

Now TypeScript checks both:

- Missing status codes
- Invalid extra keys

**Interview Line**

Use `Record<StatusCode, string>` when each known status code must map to a message.

### Q. You need to ensure every role has permission configuration. How will you type it?

**Answer:**

Define role and permission unions and use `Record`.

**Example:**

```ts
type Role = "admin" | "editor" | "viewer";

type Permission = "read" | "write" | "delete";

const rolePermissions: Record<Role, readonly Permission[]> = {
  admin: ["read", "write", "delete"],

  editor: ["read", "write"],

  viewer: ["read"],
};
```

If a role is missing, TypeScript reports an error.

**Interview Line**

Use `Record<Role, Permission[]>` to guarantee configuration exists for every supported role.

### Q. A third-party library has missing types. What will you do?

**Answer:**

First check whether official types or an `@types` package already exists.

Possible approaches are:

1. Install bundled or DefinitelyTyped definitions.
2. Add a local declaration file.
3. Declare only the subset of the API you use.
4. Contribute missing types upstream if appropriate.

**Example:**

```ts
declare module
  "legacy-library" {
  export function format(
    value: string
  ): string;
}
```

Avoid declaring the entire library as:

```ts
any;
```

unless it is only a temporary migration step.

**Interview Line**

For missing third-party types, prefer official typings, then add a focused local `.d.ts` declaration for the API you actually use.

### Q. A third-party type is incorrect. How will you override or extend it?

**Answer:**

Use module augmentation when the library's declarations are designed to be augmented.

**Example:**

```ts
import
  "some-library";

declare module
  "some-library" {
  interface User {
    role: string;
  }
}
```

If the original declaration is fundamentally incorrect and cannot be augmented safely, alternatives include:

- A local wrapper with corrected types
- A patch to the package types
- Contributing a fix upstream

Do not globally force incorrect types with broad assertions.

**Interview Line**

Use module augmentation for extendable third-party declarations, or wrap/patch the library when the original type contract is fundamentally wrong.

### Q. A type is becoming too complex for the team. How will you simplify it?

**Answer:**

Reduce type-level abstraction and introduce named intermediate concepts.

Instead of:

```ts
type Result = DeepReadonly<RequiredByKeys<PickByValue<User, string>, "name">>;
```

break it down:

```ts
type StringUserFields = PickByValue<User, string>;

type RequiredStringFields = RequiredByKeys<StringUserFields, "name">;
```

If the explicit model is clearer, use a normal interface instead.

**Interview Line**

Simplify complex types with named intermediate types and prefer explicit models when advanced utilities hurt readability.

### Q. A developer used `any` everywhere. How will you refactor it gradually?

**Answer:**

Refactor incrementally instead of replacing every `any` at once.

A practical sequence is:

1. Replace boundary `any` with `unknown`.
2. Type function parameters and return values.
3. Add domain models.
4. Type API contracts.
5. Add type guards or runtime schemas.
6. Enable stricter compiler options gradually.

**Example:**

Before:

```ts
function parse(value: any) {
  return value.name;
}
```

Improved:

```ts
function parse(value: unknown) {
  if (isUser(value)) {
    return value.name;
  }

  return null;
}
```

**Interview Line**

Refactor `any` gradually by starting at boundaries, replacing it with `unknown`, then adding real domain types and narrowing.

### Q. A strict TypeScript migration creates too many errors. How will you handle it?

**Answer:**

Migrate in controlled steps rather than weakening the entire type system.

Possible strategy:

1. Enable strictness per package or tsconfig.
2. Fix core domain and shared utilities first.
3. Replace obvious `any` with proper types.
4. Add null handling.
5. Isolate legacy code behind typed wrappers.
6. Track temporary exceptions.

If necessary, use multiple configs:

```text
tsconfig.json
tsconfig.strict.json
```

or migrate feature by feature.

Avoid solving the migration by adding:

```ts
as any
```

everywhere.

**Interview Line**

Handle strict migration incrementally with scoped configs, typed boundaries, and tracked exceptions instead of bypassing errors globally.

### Q. Build is failing because of declaration file errors. How will you debug it?

**Answer:**

First identify whether the problem is:

- Your own `.d.ts` file
- A dependency declaration
- Conflicting package versions
- Duplicate global declarations
- Incorrect module augmentation

Then inspect the exact declaration mentioned in the error.

Useful checks include:

```bash
npm ls <package>
```

and verifying:

```text
@types package versions
TypeScript version
duplicate dependencies
tsconfig types/include
```

For third-party declaration noise, `skipLibCheck` can sometimes reduce dependency errors, but it should not hide broken declarations you own.

**Interview Line**

Debug declaration errors by identifying the exact `.d.ts` source, checking version conflicts and augmentations, and using `skipLibCheck` only for external library noise when appropriate.

### Q. Path aliases work in TypeScript but fail at runtime. Why can this happen?

**Answer:**

Because TypeScript path mapping affects type/module resolution during development, but it does not automatically rewrite runtime imports.

**Example:**

```json
{
  "compilerOptions": {
    "paths": {
      "@/*": ["src/*"]
    }
  }
}
```

TypeScript may understand:

```ts
import { helper } from "@/utils/helper";
```

but Node.js may not.

Your runtime or bundler must also understand the alias.

Possible solutions include:

- Configure Vite/Webpack aliases
- Use package imports
- Use a runtime path resolver
- Use relative imports
- Bundle the application

**Interview Line**

TypeScript aliases can fail at runtime because `paths` affects TypeScript resolution, not the runtime module loader by itself.

### Q. TypeScript allows code but runtime crashes. What could be the reason?

**Answer:**

TypeScript provides compile-time checks, not complete runtime guarantees.

Common causes include:

- Unsafe type assertions
- `any`
- Invalid API responses
- Missing environment variables
- Null values from external systems
- Incorrect business logic
- Third-party JavaScript behavior

**Example:**

```ts
const user = response as User;

console.log(user.name.toUpperCase());
```

If the runtime response has no `name`, the code crashes even though TypeScript accepted the assertion.

**Interview Line**

TypeScript cannot prevent runtime failures caused by unvalidated external data, unsafe assertions, or ordinary logic errors.

### Q. You need to prevent invalid UI states in a component. How will you model the state?

**Answer:**

Use a discriminated union instead of unrelated booleans and optional fields.

**Bad Model:**

```ts
type State = {
  loading: boolean;
  data?: User;
  error?: string;
};
```

Better:

```ts
type State =
  | {
      status: "idle";
    }
  | {
      status: "loading";
    }
  | {
      status: "success";
      data: User;
    }
  | {
      status: "error";
      error: string;
    };
```

Now impossible combinations cannot be represented.

**Interview Line**

Model UI state with discriminated unions so only valid state combinations exist.

### Q. You need to type a reusable API client. What approach will you use?

**Answer:**

Use generics for response types, explicit request types, centralized error handling, and runtime validation at the external boundary.

**Example:**

```ts
type RequestOptions<TBody> = {
  method?: "GET" | "POST" | "PUT" | "DELETE";

  body?: TBody;
};
```

Client:

```ts
async function request<TResponse, TBody = never>(url: string, options?: RequestOptions<TBody>): Promise<TResponse> {
  const response = await fetch(url, {
    method: options?.method,

    body: options?.body ? JSON.stringify(options.body) : undefined,
  });

  if (!response.ok) {
    throw new Error("Request failed");
  }

  const data: unknown = await response.json();

  return data as TResponse;
}
```

For production-quality safety, improve this further by passing a runtime parser or schema:

```ts
request("/api/user", UserSchema);
```

so the response is validated instead of only asserted.

**Interview Line**

A reusable API client should combine generic request/response types with centralized error handling and runtime schema validation for external data.

## Bonus Coding Questions

### Q. Write a generic function to reverse an array

**Answer:**

Solution

```ts
function reverseArray<T>(arr: T[]): T[] {
  return [...arr].reverse();
}
```

Usage

```ts
reverseArray<number>([1, 2, 3]); // [3, 2, 1]
reverseArray<string>(["a", "b"]); // ["b", "a"]
```

Key Point

Generic `<T>` ensures type safety

**Interview Line**

A generic reverse function ensures type safety while working with any array type.

### Q. Create a type-safe function for API calls

**Answer:**

Generic API Function

```ts
async function fetchData<T>(url: string): Promise<T> {
  const res = await fetch(url);

  if (!res.ok) {
    throw new Error("API Error");
  }

  return res.json();
}
```

Usage

```ts
interface User {
  id: number;
  name: string;
}

const users = await fetchData<User[]>("/api/users");
```

Improved Version (with response wrapper)

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

**Interview Line**

Generic API functions allow reusable and type-safe data fetching across different response types.

### Q. Implement a utility type like MyPartial<T>

**Answer:**

Implementation

```ts
type MyPartial<T> = {
  [K in keyof T]?: T[K];
};
```

Example

```ts
type User = {
  name: string;
  age: number;
};

type PartialUser = MyPartial<User>;
```

Result

```ts
{
name?: string;
age?: number;
}
```

Key Concept

Uses mapped types + optional modifier (`?`)

**Interview Line**

`MyPartial<T>` is created using mapped types to make all properties optional.

### Q. Type a nested object safely

**Answer:**

Example

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

Safe Access

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

Optional Nested Fields

```ts
type User = {
  profile?: {
    name?: string;
  };
};
```

Safe Access with Optional Chaining

```ts
user.profile?.name;
```

**Interview Line**

Nested objects are typed using structured types and accessed safely using optional chaining.

### Q. Create a discriminated union example

**Answer:**

Definition

Union with a common property (discriminator)

Example

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

Usage

```ts
function handleResponse(res: ApiResult) {
  if (res.status === "success") {
    console.log(res.data);
  } else {
    console.log(res.message);
  }
}
```

Key Point

TypeScript auto-narrows based on status

**Interview Line**

Discriminated unions use a shared literal property to safely distinguish between types.

### Q. Create a custom `MyReadonly<T>` utility type.

**Answer:**

Use a mapped type and add the `readonly` modifier to every key.

**Example:**

```ts
type MyReadonly<T> = {
  readonly [K in keyof T]: T[K];
};
```

Usage:

```ts
type User = {
  id: number;
  name: string;
};

type ReadonlyUser = MyReadonly<User>;
```

Equivalent shape:

```ts
{
  readonly id: number;
  readonly name: string;
}
```

**Interview Line**

`MyReadonly<T>` maps over `keyof T` and adds `readonly` to every property.

### Q. Create a custom `MyPick<T, K>` utility type.

**Answer:**

Restrict `K` to keys of `T`, then map over only those selected keys.

**Example:**

```ts
type MyPick<T, K extends keyof T> = {
  [P in K]: T[P];
};
```

Usage:

```ts
type User = {
  id: number;
  name: string;
  email: string;
};

type UserPreview = MyPick<User, "id" | "name">;
```

Result:

```ts
{
  id: number;
  name: string;
}
```

**Interview Line**

`MyPick<T, K>` maps only the selected keys `K` and preserves their original value types.

### Q. Create a custom `MyOmit<T, K>` utility type.

**Answer:**

Create a new type by removing selected keys from `keyof T`.

One implementation can reuse `Exclude`.

**Example:**

```ts
type MyOmit<T, K extends keyof T> = {
  [P in Exclude<keyof T, K>]: T[P];
};
```

Usage:

```ts
type User = {
  id: number;
  name: string;
  password: string;
};

type PublicUser = MyOmit<User, "password">;
```

Result:

```ts
{
  id: number;
  name: string;
}
```

**Interview Line**

`MyOmit<T, K>` maps over all keys of `T` except the keys listed in `K`.

### Q. Create a custom `MyRecord<K, T>` utility type.

**Answer:**

Use a mapped type where each key maps to the same value type.

**Example:**

```ts
type MyRecord<K extends PropertyKey, T> = {
  [P in K]: T;
};
```

Usage:

```ts
type Role = "admin" | "editor" | "viewer";

type AccessMap = MyRecord<Role, boolean>;
```

Result:

```ts
{
  admin: boolean;
  editor: boolean;
  viewer: boolean;
}
```

**Interview Line**

`MyRecord<K, T>` creates an object type where every key in `K` has value type `T`.

### Q. Create a custom `MyExclude<T, U>` utility type.

**Answer:**

Use a distributive conditional type.

**Example:**

```ts
type MyExclude<T, U> = T extends U ? never : T;
```

Usage:

```ts
type Status = "idle" | "loading" | "success";

type FinalStatus = MyExclude<Status, "idle">;
```

Result:

```ts
"loading" | "success";
```

Because `T` is a generic union, the conditional distributes over each member.

**Interview Line**

`MyExclude<T, U>` removes each union member of `T` that is assignable to `U`.

### Q. Create a custom `MyReturnType<T>` utility type.

**Answer:**

Use a conditional type with `infer` to extract the function return type.

**Example:**

```ts
type MyReturnType<T extends (...args: any[]) => any> = T extends (...args: any[]) => infer R ? R : never;
```

Usage:

```ts
function getUser() {
  return {
    id: 1,
    name: "John",
  };
}

type UserResult = MyReturnType<typeof getUser>;
```

**Interview Line**

`MyReturnType<T>` matches a function type and uses `infer` to extract its return type.

### Q. Create a custom `MyParameters<T>` utility type.

**Answer:**

Use `infer` to extract the function parameter tuple.

**Example:**

```ts
type MyParameters<T extends (...args: any[]) => any> = T extends (...args: infer P) => any ? P : never;
```

Usage:

```ts
function createUser(name: string, age: number) {}
```

Then:

```ts
type Params = MyParameters<typeof createUser>;
```

Result:

```ts
[string, number];
```

**Interview Line**

`MyParameters<T>` extracts a function's argument types as a tuple using `infer`.

### Q. Create a custom `MyAwaited<T>` utility type.

**Answer:**

Use a recursive conditional type to unwrap Promise-like values.

A simplified version is:

```ts
type MyAwaited<T> = T extends PromiseLike<infer U> ? MyAwaited<U> : T;
```

Usage:

```ts
type Result = MyAwaited<Promise<Promise<string>>>;
```

Result:

```ts
string;
```

A production-grade implementation may need extra handling for `null`, `undefined`, and malformed thenables.

**Interview Line**

`MyAwaited<T>` recursively unwraps Promise-like types until it reaches the resolved value type.

### Q. Create a custom `DeepPartial<T>` utility type.

**Answer:**

Recursively make nested object properties optional.

A basic implementation is:

```ts
type DeepPartial<T> = T extends object
  ? {
      [K in keyof T]?: DeepPartial<T[K]>;
    }
  : T;
```

Usage:

```ts
type User = {
  profile: {
    name: string;
    address: {
      city: string;
    };
  };
};
```

Then:

```ts
type PartialUser = DeepPartial<User>;
```

Every nested property becomes optional.

For production utilities, special handling may be needed for arrays, functions, dates, maps, and sets.

**Interview Line**

`DeepPartial<T>` recursively applies optional modifiers to nested properties.

### Q. Create a custom `DeepReadonly<T>` utility type.

**Answer:**

Recursively add `readonly` to nested object properties.

**Example:**

```ts
type DeepReadonly<T> = T extends object
  ? {
      readonly [K in keyof T]: DeepReadonly<T[K]>;
    }
  : T;
```

Usage:

```ts
type Config = {
  api: {
    url: string;
  };
};
```

Then:

```ts
type LockedConfig = DeepReadonly<Config>;
```

Both `api` and `url` become readonly through the resulting type.

**Interview Line**

`DeepReadonly<T>` recursively applies `readonly` through nested object structures.

### Q. Create a type-safe `getValue<T, K extends keyof T>()` function.

**Answer:**

Use two generics:

- `T` for the object
- `K` for one valid key of that object

**Example:**

```ts
function getValue<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}
```

Usage:

```ts
const user = {
  id: 1,
  name: "John",
};

const name = getValue(user, "name");
```

`name` is inferred as:

```ts
string;
```

Invalid keys are rejected.

**Interview Line**

Use `K extends keyof T` and return `T[K]` to preserve the exact property type.

### Q. Create a type-safe `updateObject<T>()` function.

**Answer:**

For a partial update, accept `Partial<T>` and return a new object.

**Example:**

```ts
function updateObject<T>(obj: T, updates: Partial<T>): T {
  return {
    ...obj,
    ...updates,
  };
}
```

Usage:

```ts
const user = {
  id: 1,
  name: "John",
};

const updated = updateObject(user, {
  name: "Mike",
});
```

TypeScript prevents updates with unknown keys or incorrect value types.

For even stricter APIs, expose a key-based updater using `K extends keyof T` and `T[K]`.

**Interview Line**

A generic `updateObject<T>` can safely accept `Partial<T>` so only valid properties and value types are allowed.

### Q. Create a generic `ApiResponse<T>` type.

**Answer:**

Use a generic payload type and preferably model success and failure separately.

**Example:**

```ts
type ApiResponse<T> =
  | {
      success: true;
      data: T;
    }
  | {
      success: false;
      error: {
        code: string;
        message: string;
      };
    };
```

Usage:

```ts
type UserResponse = ApiResponse<User>;
```

This prevents invalid combinations such as having both success data and failure error at the same time.

**Interview Line**

A reusable `ApiResponse<T>` should preserve the payload type and model success and failure as separate union branches.

### Q. Create a discriminated union for async request state.

**Answer:**

Use a common `status` property.

**Example:**

```ts
type AsyncState<T> =
  | {
      status: "idle";
    }
  | {
      status: "loading";
    }
  | {
      status: "success";
      data: T;
    }
  | {
      status: "error";
      error: string;
    };
```

Usage:

```ts
type UserState = AsyncState<User>;
```

Now invalid combinations such as:

```text
loading + data + error
```

cannot be represented.

**Interview Line**

Model async state with a discriminated union so each status exposes only the fields valid for that state.

### Q. Create a type-safe event emitter.

**Answer:**

Define an event map where each event name maps to its payload type.

**Example:**

```ts
type EventMap = {
  userCreated: {
    id: number;
  };

  logout: undefined;
};
```

Emitter:

```ts
class EventEmitter<Events extends Record<string, unknown>> {
  private listeners: {
    [K in keyof Events]?: Array<(payload: Events[K]) => void>;
  } = {};

  on<K extends keyof Events>(event: K, listener: (payload: Events[K]) => void) {
    const list = this.listeners[event] ?? [];

    list.push(listener);

    this.listeners[event] = list;

    return () => {
      this.listeners[event] = list.filter((item) => item !== listener);
    };
  }

  emit<K extends keyof Events>(event: K, payload: Events[K]) {
    this.listeners[event]?.forEach((listener) => {
      listener(payload);
    });
  }
}
```

Usage:

```ts
const emitter = new EventEmitter<EventMap>();

emitter.emit("userCreated", {
  id: 1,
});
```

Invalid event names or payload shapes are rejected.

**Interview Line**

A type-safe event emitter uses an event-to-payload map and generics so each event accepts only its correct payload.

### Q. Create a typed permission map for user roles.

**Answer:**

Define role and permission unions, then use `Record`.

**Example:**

```ts
type Role = "admin" | "editor" | "viewer";

type Permission = "read" | "write" | "delete";

type PermissionMap = Record<Role, readonly Permission[]>;
```

Configuration:

```ts
const permissions: PermissionMap = {
  admin: ["read", "write", "delete"],

  editor: ["read", "write"],

  viewer: ["read"],
};
```

TypeScript ensures every role is configured.

**Interview Line**

Use `Record<Role, Permission[]>` so every role has a type-safe permission configuration.

### Q. Create a typed route configuration object.

**Answer:**

Define route names and route metadata explicitly.

**Example:**

```ts
type RouteName = "home" | "users" | "settings";

type RouteConfig = {
  path: string;
  requiresAuth: boolean;
};
```

Then:

```ts
const routes: Record<RouteName, RouteConfig> = {
  home: {
    path: "/",
    requiresAuth: false,
  },

  users: {
    path: "/users",
    requiresAuth: true,
  },

  settings: {
    path: "/settings",
    requiresAuth: true,
  },
};
```

For literal preservation, `satisfies` can also be useful:

```ts
const routes2 = {
  home: {
    path: "/",
    requiresAuth: false,
  },
} satisfies Record<string, RouteConfig>;
```

**Interview Line**

Use literal route keys plus `Record` or `satisfies` to enforce a consistent route configuration shape.

### Q. Create a typed form validation error object.

**Answer:**

Map form keys to optional error messages.

**Example:**

```ts
type FormErrors<T> = Partial<Record<keyof T, string>>;
```

Usage:

```ts
type LoginForm = {
  email: string;
  password: string;
};

const errors: FormErrors<LoginForm> = {
  email: "Invalid email",
};
```

An invalid field name is rejected.

**Interview Line**

Use `Partial<Record<keyof T, string>>` to create a validation-error map tied to the form's real field names.

### Q. Create a generic function to group array items by key.

**Answer:**

Use a generic key constrained to object keys and group by values that can safely become object keys.

**Example:**

```ts
function groupBy<T, K extends keyof T>(items: T[], key: K): Record<PropertyKey, T[]> {
  return items.reduce(
    (groups, item) => {
      const groupKey = item[key] as PropertyKey;

      (groups[groupKey] ??= []).push(item);

      return groups;
    },
    {} as Record<PropertyKey, T[]>,
  );
}
```

Usage:

```ts
const users = [
  {
    id: 1,
    role: "admin",
  },
  {
    id: 2,
    role: "viewer",
  },
  {
    id: 3,
    role: "admin",
  },
];

const grouped = groupBy(users, "role");
```

A stricter production version can constrain the selected property to `PropertyKey` values and preserve the exact key union.

**Interview Line**

A generic `groupBy` ties the grouping key to `keyof T` so only real object properties can be selected.

### Q. Create a generic function to remove duplicates by key.

**Answer:**

Use a generic key and a `Set` to track values already seen.

**Example:**

```ts
function uniqueBy<T, K extends keyof T>(items: T[], key: K): T[] {
  const seen = new Set<T[K]>();

  return items.filter((item) => {
    const value = item[key];

    if (seen.has(value)) {
      return false;
    }

    seen.add(value);

    return true;
  });
}
```

Usage:

```ts
const users = [
  {
    id: 1,
    name: "A",
  },
  {
    id: 1,
    name: "B",
  },
  {
    id: 2,
    name: "C",
  },
];

const uniqueUsers = uniqueBy(users, "id");
```

Result keeps the first item for each unique key value.

**Complexity:**

```text
Time: O(n)
Space: O(n)
```

**Interview Line**

Use `K extends keyof T` plus a `Set<T[K]>` to remove duplicate items by a type-safe object key.
