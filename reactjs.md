# REACT JS

## React Basics

### Q. What is React and why is it used?

**Answer:**

React is a JavaScript library used to build user interfaces, especially single-page applications. It focuses on the view layer of an application.

Why it’s used:

- Builds reusable UI components
- Fast rendering using Virtual DOM
- Easy to manage dynamic data
- Strong ecosystem and community

### Q. What are the key features of React?

**Answer:**

- Component-based architecture
- Virtual DOM for performance
- JSX for readable UI code
- Unidirectional data flow
- Strong support for hooks

### Q. What is JSX? Can we use React without JSX?

**Answer:**

JSX stands for JavaScript XML. It allows us to write HTML-like syntax inside JavaScript.

Yes, React can be used without JSX.

JSX is not mandatory—it is just syntactic sugar.

Example without JSX:

```js
const element = React.createElement("h1", { className: "title" }, "Hello React");
```

Why JSX is preferred?

- Cleaner and more readable
- Less verbose
- Easier to visualize UI structure

When JSX might not be used?

- Small scripts
- No build tools (Babel)
- Legacy or experimental setups

Interview Tip

JSX is optional in React, but highly recommended for readability and maintainability.

### Q. How does React differ from Angular or Vue?

**Answer:**

| Feature        | React      | Angular        | Vue        |
| -------------- | ---------- | -------------- | ---------- |
| Type           | Library    | Full framework | Framework  |
| Language       | JavaScript | TypeScript     | JavaScript |
| Learning Curve | Moderate   | Steep          | Easy       |
| Data Binding   | One-way    | Two-way        | Two-way    |

“React focuses only on UI, while Angular and Vue are full frameworks.”

### Q. What is the Virtual DOM?

**Answer:**

The Virtual DOM is a lightweight copy of the real DOM stored in memory.

React:

- Updates the Virtual DOM
- Compares it with the previous version (diffing)
- Updates only the changed parts in the real DOM

Why it matters:

- Faster performance
- Fewer expensive DOM operations

### Q. How does React update the DOM efficiently?

**Answer:**

React uses a process called reconciliation:

- Compares old and new Virtual DOM
- Finds minimum changes
- Updates only those parts in the real DOM

Key phrase:

“React updates the DOM efficiently by minimizing direct DOM manipulation.”

### Q. What are components in React?

**Answer:**

Components are independent, reusable pieces of UI.

Example:

```jsx
function Button() {
  return <button>Click</button>;
}
```

Types:

- Functional components
- Class components (older)

Interview tip:

“Everything in React is a component.”

### Q. Difference between functional components and class components

**Answer:**

| Functional     | Class                  |
| -------------- | ---------------------- |
| Uses functions | Uses ES6 classes       |
| Uses hooks     | Uses lifecycle methods |
| Simple & clean | More boilerplate       |
| Preferred now  | Mostly legacy          |

“Functional components with hooks are the modern standard in React.”

### Q. What are props?

**Answer:**

Props (properties) are read-only data passed from parent to child components.

```jsx
<Welcome name="Tanmay" />
```

```jsx
function Welcome(props) {
  return <h1>Hello {props.name}</h1>;
}
```

Interview phrase:

“Props help components communicate with each other.”

### Q. Can props be modified?

**Answer:**

❌ No. Props are immutable.

- Child components cannot change props
- Data flow is one-way

Correct approach:

- Pass a callback from parent
- Update parent state

### Q. What is state?

**Answer:**

State is a mutable object that stores data local to a component.

```jsx
const [count, setCount] = useState(0);
```

- State changes cause re-render
- Used for dynamic data

### Q. Difference between state and props

**Answer:**

| Props                  | State                    |
| ---------------------- | ------------------------ |
| Passed from parent     | Managed inside component |
| Read-only              | Can be changed           |
| Used for communication | Used for internal logic  |

“Props are external, state is internal.”

### Q. Why is React called declarative?

**Answer:**

In React, you describe what the UI should look like, not how to update it.

Example:

```jsx
{
  isLoggedIn && <Dashboard />;
}
```

React handles DOM updates automatically.

Interview phrase:

“Declarative code is easier to understand and debug.”

### Q. What is SPA (Single Page Application)?

**Answer:**

A Single Page Application (SPA) is a web application that loads a single HTML page initially and dynamically updates the content without reloading the entire page.

How It Works

1. Browser loads index.html
2. JavaScript loads
3. Routing and rendering happen on the client
4. Only components update — not full page

Example

React apps created with CRA or Vite are SPAs.

Benefits

- Fast navigation
- Smooth UX
- Less server load

Drawbacks

- SEO challenges (without SSR)
- Slower first load (large JS bundle)

Examples:
Gmail, Facebook, Twitter

### Q. What is CSR (Client Side Rendering)?

**Answer:**

CSR means the browser downloads a minimal HTML file and uses JavaScript to render the page content on the client side.

Flow

```
Request → Empty HTML → JS loads → React renders UI
```

Used In

- React SPA
- Vue SPA
- Angular apps

Pros

- Fast navigation after first load
- Good for dashboards & web apps

Cons

- SEO not ideal
- Slow initial load
- JS-heavy

### Q. What is SSR (Server Side Rendering)?

**Answer:**

SSR means the server generates the complete HTML for each request and sends it to the browser.

Flow

```
Request → Server builds HTML → Send full page → Browser displays immediately
```

Example Framework

- Next.js
- Remix

Pros

- Better SEO
- Faster first paint
- Better performance on slow devices

Cons

- Higher server load
- Slightly slower navigation

### Q. What is SSG (Static Site Generation)?

**Answer:**

SSG generates HTML pages at build time and serves them as static files.

Flow

```
Build Time → HTML generated → CDN serves static file
```

Example

Blog site built using Next.js getStaticProps

Pros

- Very fast
- Excellent SEO
- CDN friendly

Cons

- Content not real-time
- Requires rebuild for updates

### Q. What is ISR (Incremental Static Regeneration)?

**Answer:**

ISR is a hybrid approach that allows static pages to be regenerated after deployment, without rebuilding the entire site.

Flow

```
Build → Serve static page → After interval → Regenerate in background
```

Example (Next.js)

```jsx
export async function getStaticProps() {
  return {
    props: { data },
    revalidate: 10, // regenerate after 10 seconds
  };
}
```

Pros

- Static performance
- Updated content
- No full rebuild needed

🔥 Complete Comparison Table

| Feature      | CSR     | SSR       | SSG        | ISR                |
| ------------ | ------- | --------- | ---------- | ------------------ |
| Render Time  | Client  | Server    | Build Time | Build + Background |
| SEO          | ❌ Weak | ✅ Strong | ✅ Strong  | ✅ Strong          |
| First Load   | Slower  | Fast      | Very Fast  | Very Fast          |
| Server Load  | Low     | High      | Very Low   | Low                |
| Dynamic Data | Yes     | Yes       | No         | Yes (controlled)   |

🔥 Real-World Usage

| Use Case          | Best Approach |
| ----------------- | ------------- |
| Admin dashboard   | CSR           |
| Marketing website | SSG           |
| Blog              | SSG / ISR     |
| E-commerce        | SSR / ISR     |
| News site         | ISR           |

🔥 Final Interview Summary (Strong Answer)

“SPA is an architecture where a single HTML page dynamically updates content. CSR renders pages in the browser, SSR renders them on the server, SSG generates pages at build time, and ISR allows static pages to update incrementally after deployment.”

### Q. Explain reusability, modularity, testability in react js

**Answer:**

#### Reusability in React JS

Reusability means creating components, functions, or logic that can be used in multiple places instead of writing the same code again and again.

React is component-based, so reusability is one of its main advantages.

Example

```jsx
function Button({ text, onClick }) {
  return <button onClick={onClick}>{text}</button>;
}
```

Now the same `Button` component can be reused in different places:

```jsx
<Button text="Login" onClick={handleLogin} />
<Button text="Register" onClick={handleRegister} />
<Button text="Logout" onClick={handleLogout} />
```

Here, we do not need to create separate button code for login, register, and logout. We use the same component with different props.

Why Reusability is Important

Reusability helps reduce duplicate code. It also makes the application easier to maintain because changes can be made in one place and reused everywhere.

For example, if the button design changes, we only update the `Button` component once.

Common Ways to Achieve Reusability

1. Reusable Components

```jsx
function Card({ title, description }) {
  return (
    <div className="card">
      <h3>{title}</h3>
      <p>{description}</p>
    </div>
  );
}
```

Usage:

```jsx
<Card title="React" description="A JavaScript library for building UI" />
<Card title="Vue" description="A progressive JavaScript framework" />
```

2. Custom Hooks

Custom Hooks allow us to reuse logic between components.

```jsx
import { useState } from "react";

function useToggle(initialValue = false) {
  const [value, setValue] = useState(initialValue);

  function toggle() {
    setValue((prev) => !prev);
  }

  return [value, toggle];
}
```

Usage:

```jsx
function Menu() {
  const [isOpen, toggleMenu] = useToggle(false);

  return (
    <>
      <button onClick={toggleMenu}>Toggle Menu</button>
      {isOpen && <p>Menu is open</p>}
    </>
  );
}
```

Here, `useToggle` can be reused in many components.

#### Modularity in React JS

Modularity means dividing an application into small, independent, and manageable parts.

In React, these parts are usually components, hooks, utility functions, services, and modules.

Instead of writing the whole application in one large file, we split it into smaller files and components.

Example

```
src/
  components/
    Header.jsx
    Footer.jsx
    Button.jsx
    Card.jsx
  pages/
    Home.jsx
    About.jsx
    Login.jsx
  hooks/
    useToggle.js
  services/
    api.js
  App.jsx
```

This structure makes the project easier to understand and maintain.

Example of Modular Component

```jsx
function Header() {
  return (
    <header>
      <h1>My App</h1>
      <nav>
        <a href="/">Home</a>
        <a href="/about">About</a>
      </nav>
    </header>
  );
}

export default Header;
```

This `Header` component can be kept in a separate file and imported wherever needed:

```jsx
import Header from "./components/Header";

function App() {
  return (
    <>
      <Header />
      <main>
        <h2>Welcome</h2>
      </main>
    </>
  );
}
```

Why Modularity is Important

Modularity makes code easier to read, debug, test, and maintain.

When each part of the application has a clear responsibility, developers can work on different parts of the project without affecting the entire application.

Benefits of Modularity

| Benefit            | Explanation                                                   |
| ------------------ | ------------------------------------------------------------- |
| Easy maintenance   | Changes are easier because code is separated into small parts |
| Better readability | Small files are easier to understand                          |
| Team collaboration | Different developers can work on different modules            |
| Easier debugging   | Problems can be located quickly                               |
| Better scalability | New features can be added without disturbing existing code    |

#### Testability in React JS

Testability means how easy it is to test a component, function, or feature to make sure it works correctly.

A testable React component is usually simple, predictable, and independent.

Example of Testable Component

```jsx
function Greeting({ name }) {
  return <h1>Hello, {name}</h1>;
}
```

This component is easy to test because it depends only on props.

Example test:

```jsx
import { render, screen } from "@testing-library/react";
import Greeting from "./Greeting";

test("renders greeting message", () => {
  render(<Greeting name="John" />);

  expect(screen.getByText("Hello, John")).toBeInTheDocument();
});
```

The component is testable because it does not depend on external APIs, global variables, or complex side effects.

How to Improve Testability in React

1. Keep Components Small

Small components are easier to test than large components.

```jsx
function UserName({ name }) {
  return <p>{name}</p>;
}
```

This is easier to test than a large component containing UI, API calls, state management, and business logic all together.

2. Pass Data Through Props

Components that receive data through props are easier to test.

```jsx
function UserCard({ user }) {
  return (
    <div>
      <h3>{user.name}</h3>
      <p>{user.email}</p>
    </div>
  );
}
```

In tests, we can pass mock data:

```js
const mockUser = {
  name: "John",
  email: "john@example.com",
};
```

3. Separate Logic from UI

Instead of writing all logic inside JSX, move it into functions or custom Hooks.

```js
function calculateTotal(price, quantity) {
  return price * quantity;
}
```

This function can be tested separately.

4. Avoid Direct Dependency on External Services

Instead of calling APIs directly inside components, use services or custom Hooks.

```js
// api.js
export function getUsers() {
  return fetch("/api/users").then((res) => res.json());
}
```

This makes it easier to mock API calls during testing.

Relationship Between Reusability, Modularity, and Testability

These three concepts are closely related.

| Concept     | Meaning                                 | React Example                                 |
| ----------- | --------------------------------------- | --------------------------------------------- |
| Reusability | Use the same code in multiple places    | Reusable `Button`, `Card`, custom Hooks       |
| Modularity  | Split code into small independent parts | Separate components, hooks, services, pages   |
| Testability | Make code easy to test                  | Small pure components, props-based components |

A reusable component is usually modular. A modular component is usually easier to test. A testable component is usually easier to reuse and maintain.

Practical Example Combining All Three

```jsx
function ProductCard({ product, onAddToCart }) {
  return (
    <div className="product-card">
      <h3>{product.name}</h3>
      <p>Price: ₹{product.price}</p>
      <button onClick={() => onAddToCart(product)}>Add to Cart</button>
    </div>
  );
}
```

Why This Component is Good

Reusable

The `ProductCard` component can be reused for many products.

```jsx
<ProductCard product={phone} onAddToCart={handleAddToCart} />
<ProductCard product={laptop} onAddToCart={handleAddToCart} />

```

Modular

The component handles only one responsibility: displaying product information and triggering add-to-cart action.

Testable

The component receives `product` and `onAddToCart` through props, so we can easily test it with mock data and mock functions.

Example test idea:

```jsx
test("calls onAddToCart when button is clicked", () => {
  const product = { name: "Phone", price: 20000 };
  const mockAddToCart = jest.fn();

  render(<ProductCard product={product} onAddToCart={mockAddToCart} />);

  fireEvent.click(screen.getByText("Add to Cart"));

  expect(mockAddToCart).toHaveBeenCalledWith(product);
});
```

Final Answer

In React JS, reusability means writing components or logic that can be used in multiple places. For example, a common `Button`, `Card`, or custom Hook.

Modularity means dividing the application into small, independent parts such as components, hooks, pages, and services. This makes the code easier to manage and scale.

Testability means writing code in such a way that it can be easily tested. Small components, props-based data, pure functions, and separated business logic improve testability.

Together, these concepts help create React applications that are clean, maintainable, scalable, and easy to debug.

### Q. What is the difference between React element and React component?

**Answer:**

A **React element** is a plain object that describes what should appear on the screen.

It is usually created using JSX.

**Example:**

```jsx
const element = <h1>Hello</h1>;
```

A React element represents a specific UI description at a particular point in time.

A **React component** is a reusable function or class that returns React elements.

**Example:**

```jsx
function Greeting() {
  return <h1>Hello</h1>;
}
```

Here:

```jsx
<Greeting />
```

is used to create an element from the component.

The important difference is:

- Element = UI description
- Component = reusable logic that produces elements

**Interview Line**

A React element is a description of UI, while a React component is a reusable function or class that returns React elements.

### Q. What is the difference between rendering and mounting in React?

**Answer:**

Rendering means React executes a component to determine what UI it should produce.

**Example:**

```jsx
function User() {
  return <h1>John</h1>;
}
```

When React calls `User()`, that is part of the rendering process.

Mounting means the component is being added to the UI for the first time.

The lifecycle can be thought of like:

```text
Component created
↓
Render
↓
Mount to DOM
```

After the component is mounted, future state or prop changes may cause re-renders.

Those updates are not considered initial mounting.

So:

- Rendering can happen many times
- Mounting happens when the component first becomes part of the rendered tree

**Interview Line**

Rendering is the process of calculating UI, while mounting is the first time that component is inserted into the rendered application tree.

### Q. What happens when React state changes?

**Answer:**

When React state changes, React schedules an update for the component.

**Example:**

```jsx
const [count, setCount] = useState(0);

setCount(count + 1);
```

React does not normally update the DOM immediately at the exact line where `setCount()` is called.

Instead, React:

1. Schedules the state update.
2. Re-renders the component.
3. Produces a new React element tree.
4. Compares the new result with the previous result.
5. Commits only the required DOM changes.

This comparison process is part of reconciliation.

Other components may also render depending on the component tree, props, context, and optimization boundaries.

**Interview Line**

When state changes, React schedules a re-render, reconciles the new UI with the previous UI, and commits only the necessary DOM updates.

### Q. Why should component names start with a capital letter?

**Answer:**

React uses capitalization to distinguish custom components from built-in HTML elements.

**Example:**

```jsx
function UserCard() {
  return <div>User</div>;
}
```

Usage:

```jsx
<UserCard />
```

Because `UserCard` starts with a capital letter, React treats it as a component.

If we write:

```jsx
<userCard />
```

React treats it more like a custom HTML tag instead of calling the JavaScript component function.

Lowercase JSX tags are normally interpreted as native DOM elements such as:

```jsx
<div />
<button />
<input />
```

Capitalized tags represent variables or components defined in JavaScript.

**Interview Line**

React component names start with a capital letter because JSX uses capitalization to distinguish custom components from native HTML elements.

### Q. What is the difference between declarative and imperative UI?

**Answer:**

Imperative UI describes **how** to update the interface step by step.

**Example:**

```js
const button = document.querySelector("#btn");

button.addEventListener("click", () => {
  const title = document.querySelector("#title");

  title.textContent = "Updated";
});
```

Here, we manually tell the browser which DOM element to find and how to modify it.

Declarative UI describes **what the UI should look like for the current state**.

**React Example:**

```jsx
function App() {
  const [title, setTitle] = useState("Initial");

  return (
    <>
      <h1>{title}</h1>

      <button onClick={() => setTitle("Updated")}>Update</button>
    </>
  );
}
```

React handles the required DOM changes.

**Interview Line**

Imperative UI describes how to change the DOM step by step, while declarative UI describes what the UI should look like based on state.

### Q. Why is direct DOM manipulation discouraged in React?

**Answer:**

React expects the rendered UI to be derived from state and props.

If application code directly modifies DOM elements, React may not know about those changes.

**Example:**

Avoid:

```js
document.querySelector("#title").textContent = "Updated";
```

Prefer:

```jsx
const [title, setTitle] = useState("Initial");

setTitle("Updated");
```

React can then keep its internal representation and the browser DOM consistent.

Direct DOM manipulation is not completely forbidden.

It is sometimes needed for:

- Focus management
- Integrating third-party libraries
- Measuring elements
- Media controls
- Canvas

In those cases, React provides refs.

**Interview Line**

Direct DOM manipulation is discouraged because it bypasses React's state-driven rendering model and can cause the real DOM to become inconsistent with React's expected UI.

### Q. What are side effects in React components?

**Answer:**

A side effect is any operation that affects something outside the component's render calculation.

Examples include:

- API requests
- Timers
- Event listeners
- DOM manipulation
- Subscriptions
- Updating `localStorage`
- WebSocket connections

**Example:**

```jsx
useEffect(() => {
  document.title = "Dashboard";
}, []);
```

Changing `document.title` is a side effect because it modifies browser state outside the returned JSX.

React components should keep rendering pure and perform synchronization-related side effects in appropriate places such as event handlers or effects.

**Interview Line**

Side effects are operations that interact with systems outside pure rendering, such as APIs, timers, DOM APIs, subscriptions, or browser storage.

### Q. What is the difference between UI state and server state?

**Answer:**

UI state belongs primarily to the client interface.

Examples include:

- Modal open/closed
- Selected tab
- Form input
- Dropdown state
- Theme
- Current local filter

**Example:**

```jsx
const [isOpen, setIsOpen] = useState(false);
```

Server state comes from an external server or backend.

Examples include:

- User list
- Products
- Orders
- Blog posts
- Account information

Server state has additional concerns such as:

- Fetching
- Caching
- Staleness
- Refetching
- Synchronization
- Mutations

Libraries such as TanStack Query are often useful for complex client-side server state.

**Interview Line**

UI state controls local interface behavior, while server state represents remote data that must be fetched, cached, synchronized, and updated.

### Q. What is the difference between presentational and container components?

**Answer:**

A presentational component mainly focuses on how UI looks.

It generally receives data and callbacks through props.

**Example:**

```jsx
function UserCard({ user, onDelete }) {
  return (
    <div>
      <h2>{user.name}</h2>

      <button onClick={() => onDelete(user.id)}>Delete</button>
    </div>
  );
}
```

A container component mainly handles data and behavior.

**Example:**

```jsx
function UserContainer() {
  const [user, setUser] = useState({
    id: 1,
    name: "John",
  });

  function deleteUser() {
    // business logic
  }

  return <UserCard user={user} onDelete={deleteUser} />;
}
```

This separation is less strict in modern React because hooks allow logic to be extracted into custom hooks.

**Interview Line**

Presentational components focus on UI, while container components focus on data, state, and business logic.

### Q. How does React handle updates behind the scenes?

**Answer:**

When props, state, or context changes, React may schedule a render.

A simplified update process is:

```text
State/props/context changes
↓
React schedules work
↓
Component renders
↓
New React tree is created
↓
Reconciliation compares old and new trees
↓
React determines required changes
↓
Commit phase updates the DOM
```

React does not simply rebuild the entire browser DOM on every state update.

Instead, it determines which host elements need to change.

React can also batch multiple state updates and prioritize rendering work.

**Interview Line**

React handles updates by scheduling renders, reconciling the new element tree with the previous one, and committing only necessary changes to the DOM.

### Q. What are React children?

**Answer:**

`children` is a special prop that contains content placed between a component's opening and closing tags.

**Example:**

```jsx
function Card({ children }) {
  return <div className="card">{children}</div>;
}
```

Usage:

```jsx
<Card>
  <h2>Profile</h2>
  <p>User information</p>
</Card>
```

Inside `Card`, the `children` value represents the nested JSX.

Children make wrapper and layout components reusable.

Common examples include:

- Modals
- Cards
- Layouts
- Providers
- Panels

**Interview Line**

`children` is the special React prop that represents the content nested between a component's opening and closing tags.

### Q. How do you pass JSX as props?

**Answer:**

JSX can be passed like any other JavaScript value.

**Example:**

```jsx
function Card({ title, action }) {
  return (
    <div>
      <h2>{title}</h2>

      {action}
    </div>
  );
}
```

Usage:

```jsx
<Card title="Profile" action={<button>Edit</button>} />
```

The `action` prop contains a React element.

Another common pattern is using `children`.

```jsx
<Card>
  <button>Edit</button>
</Card>
```

Passing JSX as props is useful for flexible component APIs such as:

- Header actions
- Icons
- Footer content
- Slots
- Custom fallback UI

**Interview Line**

JSX is a JavaScript value, so it can be passed through props just like strings, numbers, functions, or objects.

### Q. What is the role of Babel in React?

**Answer:**

Babel is a JavaScript compiler commonly used to transform newer JavaScript syntax into syntax supported by the target environment.

Historically, Babel has also commonly transformed JSX into JavaScript.

**Example:**

JSX:

```jsx
const element = <h1>Hello</h1>;
```

Conceptually becomes JavaScript that creates React elements using the configured JSX runtime.

Babel can also transform syntax such as:

- New JavaScript features
- JSX
- TypeScript syntax in some setups
- Experimental language features when plugins are configured

Modern React tooling may use Babel, SWC, esbuild, or other compilers depending on the framework and build system.

**Interview Line**

Babel transforms JSX and modern JavaScript syntax into code that the target JavaScript environment can execute.

### Q. What is the role of a bundler in React applications?

**Answer:**

A bundler processes application modules and generates browser-ready output.

It starts from application entry points and follows imports to build a dependency graph.

**Example flow:**

```text
main.jsx
↓
App.jsx
↓
components
↓
utilities
↓
dependencies
```

A bundler can perform:

- Module resolution
- Code splitting
- Tree shaking
- Minification
- Asset handling
- CSS processing
- Development hot updates
- Production optimization

Common React build tools use technologies such as:

- Vite
- Webpack
- Rollup
- Turbopack

The exact build pipeline depends on the framework.

**Interview Line**

A bundler analyzes React application dependencies and produces optimized browser-ready JavaScript, CSS, and asset chunks.

### Q. Why should React components be pure?

**Answer:**

A pure component should produce the same rendered result when it receives the same props, state, and context.

Rendering should not unexpectedly change external values.

**Bad Example:**

```jsx
let count = 0;

function Counter() {
  count++;

  return <p>{count}</p>;
}
```

Rendering this component changes external state.

That makes behavior depend on how many times React happens to render it.

A better approach is:

```jsx
function Counter({ count }) {
  return <p>{count}</p>;
}
```

Pure rendering is important because React may:

- Render components more than once
- Pause rendering
- Restart rendering
- Reuse rendering work

Side effects should happen outside the render calculation.

**Interview Line**

React components should be pure so rendering remains predictable and React can safely re-run, pause, or restart rendering without causing unintended side effects.

## Components & Rendering

### Q. What is component re-rendering?

**Answer:**

Component re-rendering means React re-executes a component function to calculate a new UI output when data changes.

👉 It does not always mean DOM updates—only changed parts are updated.

**Interview Line**

“Re-rendering is React recalculating the UI, not necessarily updating the DOM.”

### Q. What causes a component to re-render?

**Answer:**

- State change (`setState`, `useState`)
- Props change from parent
- Parent re-render
- Context value change

Example:

```jsx
setCount(count + 1); // triggers re-render
```

One-liner:

“Any change in state, props, or context triggers a re-render.”

### Q. How do you prevent unnecessary re-renders?

**Answer:**

Common techniques:

- `React.memo()` → memoize components
- `useCallback()` → memoize functions
- `useMemo()` → memoize values
- Avoid inline functions in JSX
- Keep state minimal

Example:

```jsx
export default React.memo(MyComponent);
```

Interview phrase:

“Memoization helps React skip unnecessary renders.”

### Q. What is `key` in React and why is it important?

**Answer:**

A `key` is a unique identifier used when rendering lists to help React track elements efficiently.

```jsx
{
  items.map((item) => <li key={item.id}>{item.name}</li>);
}
```

Why important:

- Improves performance
- Helps React correctly update elements

**Interview Line**

“Keys help React identify which items have changed.”

### Q. What happens if keys are not unique?

**Answer:**

❌ Problems:

- Wrong items get updated
- Unexpected UI behavior
- Performance issues

Example issue:

- Input values jump between list items
- Incorrect animations

Interview tip:

“Non-unique keys break React’s diffing algorithm.”

### Q. Can we use index as a `key`?

**Answer:**

⚠️ Not recommended, except for static lists.

Why index is bad:

- Order changes → wrong mapping
- Causes UI bugs

When it’s okay:

- List never changes
- No add/remove/reorder

Interview answer:

“Index as a `key` should be a last resort.”

### Q. What is conditional rendering?

**Answer:**

Conditional rendering means showing UI based on a condition.

Examples:

```jsx
{
  isLoggedIn && <Dashboard />;
}

{
  isAdmin ? <Admin /> : <User />;
}
```

**Interview Line**

“React uses JavaScript conditions to control rendering.”

### Q. How do you render lists in React?

**Answer:**

Using the `map()` method.

```jsx
{
  users.map((user) => <User key={user.id} name={user.name} />);
}
```

Rules:

- Each item must have a unique key
- Prefer IDs over indexes

### Q. What is React.Fragment?

**Answer:**

React.Fragment lets you group multiple elements without adding extra DOM nodes.

```jsx
<>
  <h1>Title</h1>
  <p>Description</p>
</>
```

Why useful:

- Cleaner DOM
- Better styling & layout

### Q. Difference between div and Fragment

**Answer:**

| div                 | Fragment          |
| ------------------- | ----------------- |
| Adds extra DOM node | No extra DOM      |
| Can affect layout   | Cleaner structure |
| Heavier             | Lightweight       |

Interview one-liner:

“Fragments avoid unnecessary wrapper elements.”

### Q. What is lazy loading in React?

**Answer:**

Lazy loading means loading components only when needed, improving performance.

How it works:

```jsx
const Dashboard = React.lazy(() => import("./Dashboard"));

<Suspense fallback={<Loader />}>
  <Dashboard />
</Suspense>;
```

Benefits:

- Faster initial load
- Smaller bundle size

Interview phrase:

“Lazy loading improves performance by splitting code.”

### Q. What is component composition in React?

**Answer:**

Component composition means building larger UI by combining smaller components together.

Instead of creating one large component with all logic and markup, we create focused components and compose them.

**Example:**

```jsx
function Header() {
  return <header>Header</header>;
}

function Footer() {
  return <footer>Footer</footer>;
}

function Page() {
  return (
    <>
      <Header />

      <main>Content</main>

      <Footer />
    </>
  );
}
```

Composition can also happen using `children`.

```jsx
function Card({ children }) {
  return <div className="card">{children}</div>;
}
```

Usage:

```jsx
<Card>
  <h2>Profile</h2>
  <p>User details</p>
</Card>
```

This makes components easier to reuse and combine in different ways.

**Interview Line**

Component composition means building complex UI by combining smaller reusable components instead of placing everything inside one component.

### Q. What is the difference between composition and inheritance in React?

**Answer:**

Composition builds functionality by combining components.

Inheritance creates a parent-child class relationship where one class extends another.

**Composition Example:**

```jsx
function Dialog({ children }) {
  return <div className="dialog">{children}</div>;
}
```

Usage:

```jsx
<Dialog>
  <LoginForm />
</Dialog>
```

Inheritance would look more like traditional object-oriented programming:

```js
class Admin extends User {
  // ...
}
```

React usually does not need component inheritance because behavior and UI can be shared through:

- Props
- `children`
- Hooks
- Utility functions
- Context

**Interview Line**

Composition reuses behavior by combining components, while inheritance reuses behavior through parent-child class relationships.

### Q. Why does React prefer composition over inheritance?

**Answer:**

React prefers composition because UI is naturally built from smaller pieces.

Composition is generally more flexible than inheritance.

With composition, components can receive different content and behavior through props.

**Example:**

```jsx
function Modal({ title, children, footer }) {
  return (
    <div>
      <h2>{title}</h2>

      {children}

      {footer}
    </div>
  );
}
```

The same `Modal` can support many use cases without creating subclasses.

Composition also avoids problems such as:

- Deep inheritance chains
- Tight coupling
- Difficult overrides
- Hard-to-follow behavior

Hooks also allow reusable logic without inheritance.

**Interview Line**

React prefers composition because it provides flexible reuse through props, children, and hooks without creating tightly coupled inheritance hierarchies.

### Q. What is conditional component rendering?

**Answer:**

Conditional rendering means showing different UI depending on state, props, or other conditions.

**Example:**

```jsx
function UserStatus({ isLoggedIn }) {
  if (!isLoggedIn) {
    return <Login />;
  }

  return <Dashboard />;
}
```

Conditional rendering can also use ternary expressions:

```jsx
return isLoading ? <Loader /> : <Content />;
```

Or logical AND:

```jsx
{
  isAdmin && <AdminPanel />;
}
```

Conditional rendering is common for:

- Loading states
- Authentication
- Permissions
- Empty states
- Feature flags

**Interview Line**

Conditional rendering means returning different components or JSX depending on the current state or props.

### Q. What is the difference between hiding a component and unmounting a component?

**Answer:**

Hiding a component keeps it mounted but makes it invisible.

Unmounting removes it from the React tree.

**Hidden Example:**

```jsx
<div
  style={{
    display: isVisible ? "block" : "none",
  }}
>
  <Panel />
</div>
```

`Panel` is still mounted.

Its state is preserved.

Unmounting:

```jsx
{
  isVisible && <Panel />;
}
```

When `isVisible` becomes false, `Panel` is removed.

Its local state is lost unless stored elsewhere.

Cleanup effects also run during unmount.

**Example:**

```jsx
useEffect(() => {
  return () => {
    console.log("Cleanup");
  };
}, []);
```

**Interview Line**

Hiding keeps a component mounted and preserves its state, while unmounting removes it from the React tree and runs cleanup logic.

### Q. What happens when a parent component re-renders?

**Answer:**

When a parent component re-renders, React executes the parent component function again.

By default, React also evaluates its child components as part of the new render tree.

**Example:**

```jsx
function Parent() {
  const [count, setCount] = useState(0);

  return (
    <>
      <button onClick={() => setCount(count + 1)}>{count}</button>

      <Child />
    </>
  );
}
```

When `count` changes:

```text
Parent renders again
↓
Child is considered again
```

However, React may skip some child work through optimization mechanisms such as memoization.

A re-render does not mean the whole browser DOM is rebuilt.

React still commits only necessary DOM changes.

**Interview Line**

When a parent re-renders, React normally evaluates its child tree again, but only the necessary DOM changes are committed.

### Q. Does a child component always re-render when parent re-renders?

**Answer:**

By default, a child component is usually rendered again when its parent renders.

However, React can skip the child render if memoization determines that its inputs have not changed.

**Example:**

```jsx
const Child = React.memo(function Child({ name }) {
  console.log("Child render");

  return <p>{name}</p>;
});
```

If the parent re-renders but:

```js
name;
```

has the same value, React may skip rendering `Child`.

However, memoization can fail if props receive new references.

**Example:**

```jsx
<Child
  config={{
    theme: "dark",
  }}
/>
```

A new object is created on every parent render.

**Interview Line**

A child usually renders when its parent renders, but memoization can skip it when props and relevant inputs remain unchanged.

### Q. How do you identify unnecessary re-renders?

**Answer:**

Unnecessary re-renders should be identified through profiling rather than guessing.

Useful tools include:

- React DevTools Profiler
- Browser Performance panel
- Temporary render logs
- Highlight updates feature

**Example:**

```jsx
function UserCard() {
  console.log("UserCard rendered");

  return <div>User</div>;
}
```

If the component renders repeatedly without meaningful input changes, investigate:

- Parent re-renders
- Context updates
- New object references
- New function references
- State stored too high
- Expensive derived calculations

The React Profiler can show which components rendered and why.

**Interview Line**

Use React DevTools Profiler and render tracing to find components that render frequently without meaningful prop, state, or context changes.

### Q. What is render phase in React?

**Answer:**

The render phase is the phase where React calculates what the UI should look like.

During this phase, React:

- Executes component functions
- Reads props and state
- Creates React elements
- Compares the new tree with the previous tree
- Determines required changes

The render phase should remain pure.

Code should not perform side effects such as:

```js
document.title = "Dashboard";
```

directly during render.

React may interrupt, restart, or repeat render work.

**Interview Line**

The render phase is where React computes the next UI tree and determines what changes may be required.

### Q. What is commit phase in React?

**Answer:**

The commit phase happens after React finishes determining the required changes.

During commit, React applies those changes to the actual environment.

For DOM applications, React may:

- Add DOM nodes
- Remove DOM nodes
- Update attributes
- Update text
- Attach refs

After the DOM is updated, effect-related work may also run according to the type of effect.

Unlike render, the commit phase is not simply discarded and retried.

**Interview Line**

The commit phase is where React applies the calculated changes to the real DOM and finalizes the update.

### Q. What is the difference between render phase and commit phase?

**Answer:**

The render phase calculates what should change.

The commit phase applies those changes.

**Flow:**

```text
State update
↓
Render Phase
Calculate new UI
↓
Commit Phase
Update DOM
```

Comparison:

| Render Phase        | Commit Phase              |
| ------------------- | ------------------------- |
| Calculates UI       | Applies changes           |
| Executes components | Updates DOM               |
| Should be pure      | Performs actual mutation  |
| Can be restarted    | Represents committed work |

This distinction is important because side effects during render can behave unpredictably if React renders more than once.

**Interview Line**

Render determines what the next UI should be, while commit applies those calculated changes to the real DOM.

### Q. What are render props?

**Answer:**

Render props are a pattern where a component receives a function as a prop and calls that function to decide what UI to render.

**Example:**

```jsx
function Mouse({ render }) {
  const [position, setPosition] = useState({
    x: 0,
    y: 0,
  });

  return render(position);
}
```

Usage:

```jsx
<Mouse
  render={(position) => (
    <p>
      {position.x},{position.y}
    </p>
  )}
/>
```

The component owns reusable behavior, while the caller decides how the result should be displayed.

Before hooks, render props were commonly used to share stateful logic.

**Interview Line**

Render props share reusable behavior by passing a function that receives internal state and returns the UI to render.

### Q. When would you use render props in modern React?

**Answer:**

Hooks have replaced many traditional render-prop use cases because custom hooks provide a simpler way to reuse stateful logic.

Instead of:

```jsx
<DataLoader render={(data) => <List data={data} />} />
```

we can often write:

```jsx
const data = useDataLoader();

return <List data={data} />;
```

Render props are still useful when a component intentionally exposes control over rendering.

Examples include:

- Headless component libraries
- Complex reusable widgets
- Legacy APIs
- Cases where JSX customization is central to the component API

**Interview Line**

Modern React usually prefers custom hooks for logic reuse, but render props remain useful when a component needs to delegate rendering decisions to its consumer.

### Q. What are Higher Order Components?

**Answer:**

A Higher Order Component, or HOC, is a function that takes a component and returns a new enhanced component.

**Example:**

```jsx
function withLoading(Component) {
  return function Wrapped({ isLoading, ...props }) {
    if (isLoading) {
      return <Loader />;
    }

    return <Component {...props} />;
  };
}
```

Usage:

```jsx
const UserListWithLoading = withLoading(UserList);
```

HOCs were commonly used for:

- Authentication
- Permissions
- Data loading
- Logging
- Shared behavior

**Interview Line**

A Higher Order Component is a function that receives a component and returns another component with additional behavior or props.

### Q. Are Higher Order Components still useful after hooks?

**Answer:**

Yes, but they are used less often for logic reuse.

Hooks usually provide a simpler alternative.

Instead of:

```jsx
withAuth(withTheme(withData(Component)));
```

modern React often uses:

```jsx
const user = useAuth();

const theme = useTheme();

const data = useData();
```

HOCs are still useful for:

- Legacy codebases
- Library APIs
- Cross-cutting wrappers
- Route or permission wrappers
- Cases where the component itself must be transformed

A common downside of HOCs is deeply nested wrapper hierarchies.

**Interview Line**

Hooks replaced many HOC use cases, but HOCs are still useful for wrappers, legacy patterns, and APIs that need to enhance entire components.

### Q. What problems can occur with deeply nested component trees?

**Answer:**

Deep component trees are not automatically bad, but they can create architectural problems.

Common issues include:

- Prop drilling
- Difficult state ownership
- Hard-to-follow data flow
- Excessive coupling
- Difficult debugging
- More complex context usage

**Example:**

```text
App
↓
Layout
↓
Dashboard
↓
Panel
↓
Card
↓
Button
```

If `App` must pass the same user data through every level only for `Button`, this is prop drilling.

Possible solutions include:

- Component composition
- Context
- State colocation
- Custom hooks
- Better component boundaries

**Interview Line**

Deep component trees become problematic when they create prop drilling, unclear ownership, and tightly coupled dependencies rather than simply because they are deep.

### Q. What is component colocation?

**Answer:**

Component colocation means keeping code, state, tests, styles, and related logic close to the feature that uses them.

For example:

```text
UserProfile/
  UserProfile.jsx
  UserProfile.css
  UserProfile.test.js
  useUserProfile.js
```

State should also be colocated.

If only one component needs a value:

```jsx
function SearchBox() {
  const [query, setQuery] = useState("");
}
```

there is usually no need to move that state to a global store.

Colocation reduces unnecessary dependencies and makes features easier to understand.

**Interview Line**

Component colocation keeps related UI, state, styles, tests, and logic near the feature that owns them.

### Q. How do you decide whether to split a component?

**Answer:**

A component should usually be split when it has multiple responsibilities or when part of it can be reused or understood independently.

Useful signals include:

- Very large JSX
- Multiple unrelated responsibilities
- Repeated UI
- Complex state logic
- Difficult testing
- A clear reusable child section

**Example:**

Instead of one large:

```text
CheckoutPage
```

we might split:

```text
CheckoutPage
├── AddressForm
├── PaymentForm
├── OrderSummary
└── SubmitButton
```

Avoid splitting every small piece unnecessarily because too many tiny components can also make code harder to follow.

**Interview Line**

Split a component when it has multiple responsibilities, reusable sections, or complexity that becomes easier to manage through clear boundaries.

### Q. What is a reusable component API?

**Answer:**

A reusable component API is the set of props and behaviors through which other components use a reusable component.

A good API should be:

- Clear
- Predictable
- Flexible
- Difficult to misuse
- Small enough to understand

**Example:**

```jsx
<Button variant="primary" size="medium" disabled={false} onClick={handleClick}>
  Save
</Button>
```

This is easier to understand than many unclear boolean props such as:

```jsx
<Button blue large rounded special />
```

A component API should expose necessary customization without exposing internal implementation details.

**Interview Line**

A reusable component API is the public props and composition model that let consumers configure a component without depending on its internal implementation.

### Q. How do you design flexible reusable components?

**Answer:**

Flexible reusable components should provide sensible defaults while allowing controlled customization.

Useful principles include:

1. Prefer composition.
2. Keep props focused.
3. Support `children` where appropriate.
4. Allow controlled callbacks.
5. Avoid too many boolean props.
6. Keep business logic separate from generic UI.
7. Expose semantic options instead of implementation details.

**Example:**

```jsx
<Modal title="Delete User" footer={<DeleteActions />}>
  <p>Are you sure?</p>
</Modal>
```

This is often more flexible than creating many props such as:

```jsx
showDeleteButton;
showCancelButton;
showWarningText;
```

For advanced reusable libraries, patterns such as compound components or headless components can provide additional flexibility.

**Interview Line**

Flexible reusable components use composition, focused props, sensible defaults, and semantic customization without exposing unnecessary internal details.

## Props

### Q. What is prop spreading in React?

**Answer:**

Prop spreading means passing all properties of an object to a component using the spread operator.

**Example:**

```jsx
const userProps = {
  name: "John",
  age: 25,
  role: "admin",
};

<UserCard {...userProps} />;
```

This is equivalent to:

```jsx
<UserCard name="John" age={25} role="admin" />
```

Prop spreading is useful when:

- An object already contains all required props
- Wrapping or forwarding props
- Building reusable components

It can make code shorter, but it should be used carefully because it can hide which props are actually being passed.

**Interview Line**

Prop spreading uses `{...object}` to pass multiple props at once from an object to a React component.

### Q. When should you avoid prop spreading?

**Answer:**

Prop spreading should be avoided when it makes the component API unclear or passes unnecessary props.

**Example:**

```jsx
<UserCard {...user} />
```

This may pass many values that `UserCard` does not need.

A clearer version is:

```jsx
<UserCard name={user.name} role={user.role} />
```

Problems with excessive prop spreading include:

- Harder readability
- Accidental prop forwarding
- Passing invalid DOM attributes
- Tighter coupling between objects and components
- Harder refactoring

It is still useful for wrapper components where forwarding props is intentional.

**Interview Line**

Avoid prop spreading when it hides the component contract or forwards unnecessary values; prefer explicit props when clarity matters.

### Q. What are default props?

**Answer:**

Default props are fallback values used when a prop is not provided.

In modern functional components, default values are usually handled through JavaScript default parameters or destructuring.

**Example:**

```jsx
function Button({ text = "Click" }) {
  return <button>{text}</button>;
}
```

Usage:

```jsx
<Button />
```

Output:

```text
Click
```

If a value is provided:

```jsx
<Button text="Save" />
```

the provided value is used.

Default values help make components easier to use without requiring every prop to be passed explicitly.

**Interview Line**

Default props provide fallback values when a prop is `undefined` or not supplied.

### Q. How do you set default values for props in functional components?

**Answer:**

The most common approach is using default values during destructuring.

**Example:**

```jsx
function Avatar({ size = 40, shape = "circle" }) {
  return (
    <div>
      Size: {size}
      Shape: {shape}
    </div>
  );
}
```

Usage:

```jsx
<Avatar />
```

The defaults are:

```text
size = 40
shape = circle
```

Another approach is:

```jsx
function Avatar(props) {
  const { size = 40 } = props;

  return <div>{size}</div>;
}
```

Default values apply when the prop is `undefined`.

They do not automatically replace `null`.

**Interview Line**

Functional components usually define default prop values using JavaScript default parameters or destructuring defaults.

### Q. What is prop validation?

**Answer:**

Prop validation means checking that a component receives props in the expected shape and type.

Without validation, a component may receive invalid data and fail at runtime.

**Example:**

Suppose a component expects:

```text
name -> string
age -> number
```

but receives:

```jsx
<User name={123} age="25" />
```

Validation tools can detect this mismatch.

Common approaches include:

- PropTypes
- TypeScript
- Runtime schema validation

TypeScript provides compile-time validation, while PropTypes and schema libraries can provide runtime validation.

**Interview Line**

Prop validation ensures components receive data in the expected type and structure, reducing runtime mistakes and unclear component contracts.

### Q. What are PropTypes?

**Answer:**

PropTypes is a runtime type-checking mechanism traditionally used in React applications.

It validates component props during development.

**Example:**

```jsx
import PropTypes from "prop-types";

function User({ name, age }) {
  return (
    <div>
      {name} - {age}
    </div>
  );
}

User.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number,
};
```

If invalid props are passed, React can show warnings in development.

PropTypes supports types such as:

```text
string
number
bool
array
object
func
node
element
```

**Interview Line**

PropTypes provides runtime prop validation and development warnings for incorrect React component props.

### Q. Is PropTypes still useful when using TypeScript?

**Answer:**

Usually, TypeScript makes PropTypes unnecessary for internal React components because TypeScript provides compile-time type checking.

**Example:**

```tsx
type UserProps = {
  name: string;
  age?: number;
};

function User({ name, age }: UserProps) {
  return (
    <div>
      {name} {age}
    </div>
  );
}
```

TypeScript can detect incorrect usage before runtime.

However, PropTypes may still be useful when:

- A library is consumed by plain JavaScript users
- Runtime validation is specifically required
- Data can come from untyped external sources

Even with TypeScript, external API data should still be validated at runtime when necessary.

**Interview Line**

TypeScript usually replaces PropTypes for compile-time checking, but runtime validation may still be useful for external or untrusted data.

### Q. What is children prop?

**Answer:**

`children` is a special prop that represents content placed between a component's opening and closing tags.

**Example:**

```jsx
function Card({ children }) {
  return <div className="card">{children}</div>;
}
```

Usage:

```jsx
<Card>
  <h2>Profile</h2>
  <p>User details</p>
</Card>
```

The nested JSX becomes the `children` prop.

It is useful for:

- Layout components
- Modals
- Cards
- Providers
- Wrapper components

**Interview Line**

`children` is the special prop React uses to pass nested content into a component.

### Q. How do you restrict children type in React?

**Answer:**

With TypeScript, the `children` prop can be typed depending on what the component should accept.

For general renderable React content:

```tsx
type Props = {
  children: React.ReactNode;
};
```

If exactly one React element is expected:

```tsx
type Props = {
  children: React.ReactElement;
};
```

For a specific component type, stricter typing can be attempted through `ReactElement` generics.

**Example:**

```tsx
type CardProps = {
  children: React.ReactNode;
};

function Card({ children }: CardProps) {
  return <div>{children}</div>;
}
```

`ReactNode` is the most common type because it supports:

- Strings
- Numbers
- Elements
- Fragments
- Arrays
- `null`

**Interview Line**

In TypeScript, use `ReactNode` for general children and narrower types such as `ReactElement` when the component requires stricter child content.

### Q. What is props drilling vs props composition?

**Answer:**

Prop drilling means passing data through multiple intermediate components only so a deeply nested child can receive it.

**Example:**

```text
App
↓ user
Layout
↓ user
Panel
↓ user
UserProfile
```

Even if `Layout` and `Panel` do not need `user`, they still receive and forward it.

Props composition avoids some drilling by passing already-composed UI.

**Example:**

```jsx
function App() {
  return <Layout content={<UserProfile />} />;
}
```

Another example is using `children`.

Composition can reduce unnecessary knowledge between intermediate components.

**Interview Line**

Prop drilling passes data through intermediate components, while composition passes UI or behavior in a way that can reduce unnecessary prop forwarding.

### Q. How do you avoid passing too many props?

**Answer:**

Too many props can make a component difficult to understand and maintain.

Ways to reduce this include:

1. Group related values into meaningful objects.
2. Use composition.
3. Move state closer to where it is used.
4. Use context for truly shared data.
5. Split large components.
6. Pass callbacks instead of low-level implementation details.

**Example:**

Instead of:

```jsx
<UserCard firstName={user.firstName} lastName={user.lastName} email={user.email} role={user.role} />
```

we may use:

```jsx
<UserCard user={user} />
```

if the component logically owns the whole user object.

The goal is not to minimize prop count at any cost, but to design a clear component API.

**Interview Line**

Avoid too many props by designing cohesive APIs, colocating state, using composition, and passing grouped domain data when appropriate.

### Q. What is the problem with passing objects directly as props?

**Answer:**

Passing objects is not inherently bad.

The main issue is creating a new object during every render.

**Example:**

```jsx
<Child
  config={{
    theme: "dark",
    size: "large",
  }}
/>
```

Every parent render creates a new object reference.

So even if the values are the same:

```js
previousConfig !== newConfig;
```

This can affect memoized components.

**Example:**

```jsx
const Child = React.memo(function Child({ config }) {
  return <div />;
});
```

`Child` may re-render because the `config` reference changes.

A stable object can be created outside the component or memoized when necessary.

**Interview Line**

Passing objects is fine, but creating new object literals on every render can break reference-based memoization and cause unnecessary child re-renders.

### Q. What is callback prop?

**Answer:**

A callback prop is a function passed from one component to another through props.

It is commonly used to let a child notify the parent about an event.

**Example:**

```jsx
function Parent() {
  function handleDelete(id) {
    console.log("Delete:", id);
  }

  return <Child onDelete={handleDelete} />;
}
```

Child:

```jsx
function Child({ onDelete }) {
  return <button onClick={() => onDelete(10)}>Delete</button>;
}
```

The parent owns the logic, while the child decides when to call it.

**Interview Line**

A callback prop is a function passed through props so a child can trigger behavior owned by its parent.

### Q. How do you communicate from child to parent component?

**Answer:**

React data flow is primarily top-down, so a child usually communicates upward by calling a callback function provided by the parent.

**Example:**

Parent:

```jsx
function Parent() {
  const [message, setMessage] = useState("");

  function handleMessage(value) {
    setMessage(value);
  }

  return (
    <>
      <Child onMessage={handleMessage} />

      <p>{message}</p>
    </>
  );
}
```

Child:

```jsx
function Child({ onMessage }) {
  return <button onClick={() => onMessage("Hello")}>Send</button>;
}
```

The parent passes behavior down, and the child invokes it with data.

**Interview Line**

Child-to-parent communication is usually implemented by passing a callback from the parent and invoking it from the child with the required data.

### Q. How do you pass data between sibling components?

**Answer:**

Sibling components do not usually communicate directly.

The common approach is to lift shared state to their nearest common parent.

**Example:**

```jsx
function Parent() {
  const [value, setValue] = useState("");

  return (
    <>
      <SiblingA onChange={setValue} />

      <SiblingB value={value} />
    </>
  );
}
```

`SiblingA` updates the parent:

```jsx
function SiblingA({ onChange }) {
  return <button onClick={() => onChange("Hello")}>Update</button>;
}
```

`SiblingB` receives the value:

```jsx
function SiblingB({ value }) {
  return <p>{value}</p>;
}
```

For deeply shared data, Context or an external state manager may be more appropriate.

**Interview Line**

Sibling components usually communicate by lifting shared state to their nearest common parent and passing data and callbacks through props.

## Styling in React

### Q. What are different ways to style React components?

**Answer:**

React supports multiple styling approaches, and the right choice depends on project size, team conventions, theming needs, and performance requirements.

Common options include:

1. Plain CSS
2. CSS Modules
3. Inline styles
4. CSS-in-JS
5. Tailwind CSS
6. Sass or SCSS
7. Component libraries with theming

**Example:**

```jsx
import "./button.css";

function Button() {
  return <button className="btn">Save</button>;
}
```

Inline styles can also be used:

```jsx
<button
  style={{
    padding: "8px 12px",
    borderRadius: "6px",
  }}
>
  Save
</button>
```

**Interview Line**

React supports plain CSS, CSS Modules, inline styles, CSS-in-JS, utility CSS, and component-library styling.

### Q. CSS Modules vs Styled Components

**Answer:**

CSS Modules keep styles in regular CSS files while scoping class names locally.

```css
.button {
  color: white;
  background: blue;
}
```

```jsx
import styles from "./Button.module.css";

<button className={styles.button}>Save</button>;
```

Styled Components defines styles in JavaScript:

```jsx
const Button = styled.button`
  color: white;
  background: blue;
`;
```

CSS Modules have low runtime overhead and keep CSS separate. Styled Components make dynamic styling and theming convenient.

**Interview Line**

CSS Modules provide locally scoped CSS files, while Styled Components use CSS-in-JS to attach styles directly to components.

### Q. Styled Components vs Emotion

**Answer:**

Both are CSS-in-JS libraries and support dynamic styling, theming, and styled component APIs.

Styled Components is centered around:

```jsx
const Button = styled.button`
  color: red;
`;
```

Emotion offers a similar `styled` API and also supports flexible styling through utilities such as the `css` prop.

The choice usually depends on team preference, ecosystem, SSR needs, and existing project architecture.

**Interview Line**

Styled Components and Emotion are similar CSS-in-JS solutions, while Emotion also offers flexible APIs such as the `css` prop.

### Q. CSS-in-JS vs traditional CSS

**Answer:**

Traditional CSS keeps styles in CSS files.

```css
.button {
  color: red;
}
```

CSS-in-JS defines styles from JavaScript.

```jsx
const Button = styled.button`
  color: red;
`;
```

Traditional CSS generally has lower runtime overhead and follows native browser styling patterns.

CSS-in-JS provides strong component scoping, dynamic styling, and theme integration.

**Interview Line**

Traditional CSS separates styling from JavaScript, while CSS-in-JS co-locates styles with components and makes dynamic styling easier.

### Q. What are advantages of Tailwind CSS in React?

**Answer:**

Tailwind provides utility classes directly in JSX.

```jsx
<button className="px-4 py-2 rounded bg-blue-600 text-white">Save</button>
```

Advantages include:

- Faster development
- Consistent spacing and sizing
- Built-in responsive utilities
- Easy hover/focus states
- Less custom CSS
- Fewer naming decisions
- Strong design consistency

**Interview Line**

Tailwind speeds development by providing reusable utility classes for layout, spacing, responsiveness, and UI states.

### Q. What are disadvantages of Tailwind CSS in React?

**Answer:**

The biggest drawback is that JSX can become visually noisy.

```jsx
<div className="flex items-center justify-between rounded-lg border p-4 shadow-sm">
```

Potential disadvantages include:

- Long class lists
- Repeated utility combinations
- Learning Tailwind conventions
- Reduced readability for unfamiliar developers

Large projects usually solve this through reusable components and shared variants.

**Interview Line**

Tailwind improves speed and consistency, but large class lists can reduce readability and create repetition.

### Q. How do you handle conditional class names?

**Answer:**

Conditional classes can be handled with ternaries, template literals, or helper libraries.

```jsx
<button className={active ? "btn btn-active" : "btn"}>Save</button>
```

For more complex conditions, helpers such as `clsx` improve readability.

**Interview Line**

Conditional classes can be built with JavaScript expressions, while `clsx` is useful when many conditions exist.

### Q. What is `clsx` or `classnames` library?

**Answer:**

`clsx` and `classnames` are utilities for conditionally combining CSS class names.

```jsx
import clsx from "clsx";

<button
  className={clsx("btn", {
    "btn-active": active,
    "btn-disabled": disabled,
  })}
>
  Save
</button>;
```

They are especially useful with Tailwind, CSS Modules, and reusable component variants.

**Interview Line**

`clsx` and `classnames` simplify conditional class-name composition.

### Q. How do you manage global styles?

**Answer:**

Global styles should be limited to application-wide concerns such as:

- CSS reset
- Body styles
- Typography
- CSS variables
- Theme tokens
- Base element styles

```css
:root {
  --color-primary: #2563eb;
}

body {
  margin: 0;
  font-family: system-ui, sans-serif;
}
```

Component-specific styles should usually stay locally scoped.

**Interview Line**

Use global CSS for application-wide defaults and tokens, while keeping component-specific styles scoped.

### Q. How do you avoid CSS conflicts in large React apps?

**Answer:**

CSS conflicts can be reduced using:

- CSS Modules
- CSS-in-JS
- Tailwind
- BEM
- Component libraries
- Scoped design-system styles

Avoid broad selectors:

```css
div {
  margin: 10px;
}
```

Prefer component-scoped selectors:

```css
.userCard {
  margin: 10px;
}
```

**Interview Line**

Avoid CSS conflicts by using scoped styles and predictable naming instead of broad global selectors.

### Q. What is design token?

**Answer:**

A design token is a named reusable value representing a design decision.

Examples include:

- Colors
- Spacing
- Font sizes
- Radius
- Shadows
- Breakpoints

```css
:root {
  --color-primary: #2563eb;
  --space-sm: 8px;
  --radius-md: 8px;
}
```

Tokens improve consistency and make design changes easier.

**Interview Line**

Design tokens are reusable named values for design decisions such as color, spacing, typography, and radius.

### Q. What is theme provider?

**Answer:**

A Theme Provider exposes shared theme values to components through a context-like mechanism.

```jsx
const theme = {
  colors: {
    primary: "#2563eb",
    background: "#ffffff",
  },
};
```

```jsx
<ThemeProvider theme={theme}>
  <App />
</ThemeProvider>
```

It is useful for dark mode, branding, multi-tenant apps, and design systems.

**Interview Line**

A Theme Provider supplies shared design values such as colors, spacing, and typography to descendant components.

### Q. How do you implement dark mode in React?

**Answer:**

Dark mode usually involves tracking the theme and applying a root class or data attribute.

```jsx
const [theme, setTheme] = useState("light");

useEffect(() => {
  document.documentElement.dataset.theme = theme;
}, [theme]);
```

```css
:root {
  --background: white;
  --text: black;
}

[data-theme="dark"] {
  --background: #111;
  --text: white;
}
```

The preference can be persisted with `localStorage` and system preference can be detected with `prefers-color-scheme`.

**Interview Line**

Dark mode is commonly implemented by switching a root class or attribute and changing shared CSS variables or design tokens.

### Q. How do you keep styling consistent across a large application?

**Answer:**

Large applications need shared styling rules rather than independent decisions by every developer.

Useful approaches include:

- Design tokens
- Shared component library
- Typography scale
- Spacing scale
- Color system
- Reusable variants
- Documentation
- Storybook
- Linting

Instead of styling buttons separately everywhere, use:

```jsx
<Button variant="primary" size="medium">
  Save
</Button>
```

**Interview Line**

Styling consistency comes from shared tokens, components, variants, and documented design rules.

### Q. What is a design system?

**Answer:**

A design system is a shared collection of design rules, reusable components, tokens, patterns, and documentation.

It may include:

- Colors
- Typography
- Spacing
- Buttons
- Forms
- Icons
- Modals
- Accessibility guidelines
- Interaction patterns

A design system is broader than a component library because it also defines how and when components should be used.

**Interview Line**

A design system is a shared source of design tokens, reusable components, patterns, and usage guidelines.

### Q. How do React component libraries help large teams?

**Answer:**

React component libraries provide reusable and standardized UI building blocks.

Examples include:

- Button
- Input
- Modal
- Table
- Dropdown
- Tooltip

Benefits include:

- Faster development
- Consistent UI
- Shared accessibility behavior
- Less duplicate code
- Easier maintenance
- Centralized bug fixes

```jsx
<Button variant="primary">Save</Button>
```

If the button design or accessibility behavior changes, it can be updated in one place.

**Interview Line**

React component libraries help large teams by standardizing reusable UI, behavior, accessibility, and visual design.

## Hooks

### Q. What are hooks?

**Answer:**

Hooks are functions that let you use state and other React features inside functional components.

Examples:

- `useState` → state
- `useEffect` → side effects
- `useContext` → context

Interview one-liner:

“Hooks allow functional components to manage state and lifecycle behavior.”

### Q. Why were hooks introduced?

**Answer:**

Problems before hooks (class components):

- Complex lifecycle methods
- Hard to reuse logic
- this keyword confusion

Hooks solve:

- Logic reuse
- Cleaner, simpler components
- No classes needed

Interview phrase:

“Hooks were introduced to reuse logic and simplify component design.”

### Q. Rules of hooks

**Answer:**

📌 Two rules only:

- Call hooks only at the top level
- Call hooks only inside React functions

❌ Don’t use hooks:

- Inside loops
- Inside conditions
- Inside nested functions

Interview tip:

“Rules ensure hooks run in the same order every render.”

### Q. What is `useState`?

**Answer:**

`useState` lets you add state to a functional component.

```jsx
const [count, setCount] = useState(0);
```

- Returns state value
- Returns state updater function
- Triggers re-render

### Q. How does `useState` work internally?

**Answer:**

Conceptually:

- React stores state in an internal array
- Each hook is tracked by call order
- setState schedules a re-render

Key idea:

“Hooks rely on call order, not names.”

### Q. What is `useEffect`?

**Answer:**

`useEffect` handles side effects in functional components.

Examples:

- API calls
- Subscriptions
- Timers
- DOM updates

```jsx
useEffect(() => {
  fetchData();
}, []);
```

**Interview Line**

“`useEffect` replaces lifecycle methods in functional components.”

### Q. Explain `useEffect` dependency array

**Answer:**

| Dependency | Behavior                     |
| ---------- | ---------------------------- |
| `[]`       | Runs once (on mount)         |
| `[a, b]`   | Runs when `a` or `b` changes |
| No array   | Runs on every render         |

Important:

- Missing dependencies → bugs
- ESLint helps enforce correctness

### Q. Explain in detail `useEffect`, `useLayoutEffect`, and `useInsertionEffect`

**Answer:**

All three are side-effect hooks, but they run at different times in React’s rendering process.

🧠 First: React render flow (important)

- React renders JSX (virtual DOM)
- React updates the real DOM
- Browser paints the screen
- Effects run

The difference between these hooks is WHEN they run.

#### 1️⃣ `useEffect` (most common)

📌 When does it run?

👉 After the browser paints the screen

🧩 What it’s used for

- API calls
- Subscriptions
- Timers
- Logging
- Side effects that don’t affect layout

```jsx
useEffect(() => {
  fetchData();
}, []);
```

👍 Why it’s preferred

- Non-blocking
- Better performance
- Doesn’t delay UI rendering

⚠️ Downside

If it updates layout → user may see a flicker

##### 2️⃣ `useLayoutEffect`

📌 When does it run?

👉 After DOM updates but BEFORE the browser paints

So:

DOM is ready

Screen is not shown yet

Browser is paused until effect finishes

```jsx
useLayoutEffect(() => {
  const width = ref.current.offsetWidth;
  setWidth(width);
}, []);
```

🧩 What it’s used for

- Measuring DOM size/position
- Reading layout values
- Synchronous DOM updates
- Preventing visual flicker

⚠️ Downside

- Blocks painting
- Can hurt performance if overused

#### 3️⃣ `useInsertionEffect` (advanced / rare)

📌 When does it run?

👉 Before DOM mutations happen

Order:

→ `useInsertionEffect`

→ DOM updates

→ `useLayoutEffect`

→ Paint

→ `useEffect`

🧩 Why it exists

Created mainly for:

- CSS-in-JS libraries
- Injecting styles before elements appear

```jsx
useInsertionEffect(() => {
  insertStyles();
}, []);
```

⚠️ Very important

❌ Don’t read layout

❌ Don’t update state

✔ Only for style insertion

Used by:

- styled-components
- UI libraries

🧠 Visual Timeline (easy to remember)

Render

↓

useInsertionEffect

↓

DOM update

↓

useLayoutEffect

↓

Paint (screen shown)

↓

useEffect

🆚 Comparison Table (Interview Gold ⭐)

| Feature      | useEffect          | useLayoutEffect | useInsertionEffect |
| ------------ | ------------------ | --------------- | ------------------ |
| Runs         | After paint        | Before paint    | Before DOM update  |
| Blocks paint | ❌ No              | ✅ Yes          | ✅ Yes             |
| Use case     | Data, side effects | DOM measurement | Inject styles      |
| Performance  | Best               | Slower          | Very limited       |
| Common use   | ✅ Yes             | ⚠️ Sometimes    | ❌ Rare            |

🎯 When to use what?

90% of the time → `useEffect`

Need DOM measurements / no flicker → useLayoutEffect

Building CSS-in-JS library → useInsertionEffect

⭐ Interview One-Line Answers

`useEffect`

Runs after paint and is used for non-blocking side effects.

`useLayoutEffect`

Runs before paint and is used for synchronous DOM measurements.

`useInsertionEffect`

Runs before DOM mutations and is used to inject styles safely.

### Q. Difference between `useEffect`, `useLayoutEffect`, and `useInsertionEffect`

**Answer:**

| Hook                 | When it runs        | Use case         |
| -------------------- | ------------------- | ---------------- |
| `useEffect`          | After paint         | API calls        |
| `useLayoutEffect`    | Before paint        | DOM measurements |
| `useInsertionEffect` | Before DOM mutation | CSS-in-JS        |

**Interview Line**

“useLayoutEffect blocks paint; useEffect doesn’t.”

### Q. How to mimic lifecycle methods using hooks?

**Answer:**

| Class Lifecycle      | Hook Equivalent               |
| -------------------- | ----------------------------- |
| componentDidMount    | `useEffect(() => {}, [])`     |
| componentDidUpdate   | `useEffect(() => {}, [deps])` |
| componentWillUnmount | cleanup function              |

```jsx
useEffect(() => {
  return () => cleanup();
}, []);
```

### Q. What is `useRef`?

**Answer:**

`useRef` creates a mutable reference that persists across renders without causing re-render.

```jsx
const inputRef = useRef(null);
```

Uses:

- Access DOM elements
- Store previous values
- Timers & intervals

### Q. Difference between `useRef` and `useState`

**Answer:**

| useRef       | useState         |
| ------------ | ---------------- |
| No re-render | Causes re-render |
| Mutable      | Immutable        |
| DOM access   | UI data          |

Interview one-liner:

“useRef stores values without affecting rendering.”

### Q. What is `useMemo`?

**Answer:**

`useMemo` memoizes expensive calculations.

```jsx
const value = useMemo(() => heavyCalc(a), [a]);
```

- Improves performance
- Avoids recomputation

### Q. When should you use `useMemo`?

**Answer:**

Use it when:

- Expensive calculation
- Large lists
- Value used as dependency
- Performance bottleneck

❌ Don’t overuse it.

Interview tip:

“`useMemo` is an optimization, not a default.”

### Q. What is `useCallback`?

**Answer:**

`useCallback` memoizes functions.

```jsx
const handleClick = useCallback(() => {
  setCount((c) => c + 1);
}, []);
```

Why needed:

- Prevents unnecessary re-renders
- Useful with React.memo

### Q. Difference between `useCallback` and `useMemo`

**Answer:**

| useCallback       | useMemo              |
| ----------------- | -------------------- |
| Memoizes function | Memoizes value       |
| Returns function  | Returns result       |
| Used in props     | Used in calculations |

**Interview Line**

“`useCallback` is `useMemo` for functions.”

### Q. What is `useContext`?

**Answer:**

`useContext` lets components consume context directly, without passing props.

```jsx
const theme = useContext(ThemeContext);
```

Use case:

- Theme
- Auth
- Language

### Q. What is prop drilling and how do hooks solve it?

**Answer:**

Prop drilling:
Passing props through multiple intermediate components.

Problems:

- Messy code
- Hard to maintain

Solution:

- `useContext`
- Global state hooks

**Interview Line**

“Context eliminates unnecessary prop passing.”

### Q. Custom hooks – what and why?

**Answer:**

Custom hooks are reusable functions that use hooks internally.

```jsx
function useFetch(url) {
  const [data, setData] = useState(null);
  return data;
}
```

Why:

- Reuse logic
- Cleaner components
- Separation of concerns

### Q. How do you share logic between components?

**Answer:**

Best approaches:

- Custom hooks ✅
- Context
- Higher-order components (older)
- Render props (older)

Interview conclusion:

“Custom hooks are the modern way to share logic.”

### Q. What is `useReducer`?

**Answer:**

`useReducer` is a React hook used for managing complex state logic using a reducer function and dispatching actions — similar to how Redux works.

Why `useReducer` Exists

When:

- State is complex (multiple related values)
- Next state depends on previous state
- Many state transitions exist
- Logic becomes messy with multiple useState

👉 `useReducer` provides a structured, predictable state flow.

Basic Syntax

```jsx
const [state, dispatch] = useReducer(reducer, initialState);
```

Core Concepts
| Concept | Meaning |
| -------- | --------------------------------------- |
| reducer | Function that decides how state changes |
| state | Current state |
| dispatch | Function to send actions |
| action | Object describing what happened |

1️⃣ Simple Counter Example

```jsx
import React, { useReducer } from "react";

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <>
      <p>{state.count}</p>
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
    </>
  );
}
```

How It Works (Flow)

```
User clicks →
dispatch(action) →
reducer runs →
new state returned →
component re-renders
```

2️⃣ Real-World Example (Form Handling)

```jsx
const initialState = {
  name: "",
  email: "",
};

function reducer(state, action) {
  return {
    ...state,
    [action.field]: action.value,
  };
}

<input
  onChange={(e) =>
    dispatch({
      field: "name",
      value: e.target.value,
    })
  }
/>;
```

👉 Cleaner than multiple `useState`.

### `useReducer` vs `useState`

**Answer:**

| Feature          | useState | useReducer  |
| ---------------- | -------- | ----------- |
| Simple state     | ✅       | ❌ Overkill |
| Complex logic    | ❌       | ✅          |
| Multiple updates | ❌       | ✅          |
| Predictability   | Medium   | High        |

📌 Interview Line

“`useReducer` is preferred when state logic becomes complex or depends heavily on previous state.”

### When Should You Use `useReducer`?

**Answer:**

✅ Complex forms
✅ State transitions
✅ Multiple sub-values
✅ Business logic separation

❌ Simple counter
❌ Single boolean toggle

Important Interview Points

- Reducer must return new state object
- Reducer must be pure function
- Similar pattern to Redux
- Can combine with useContext for global state

One-Line Interview Summary

“useReducer is a hook for managing complex state logic using a reducer function and dispatching actions, similar to Redux but built into React.”

### 🔥 30-Second Interview Summary (Hooks)

“Hooks allow functional components to manage state, side effects, and shared logic. They simplify code, improve reusability, and replace class-based lifecycle methods.”

### Q. Explain `useId`

**Answer:**

`useId` is a React Hook used to generate a unique ID inside a component.

It is mainly used for accessibility attributes, such as connecting a `<label>` with an `<input>` using `htmlFor` and `id`. React officially describes `useId` as a Hook for generating unique IDs that can be passed to accessibility attributes.

Syntax

```js
const id = useId();
```

Example

```jsx
import { useId } from "react";

function InputField() {
  const id = useId();

  return (
    <div>
      <label htmlFor={id}>Username</label>
      <input id={id} type="text" />
    </div>
  );
}
```

In this example, `useId()` creates a unique ID. The same ID is used in both `label` and `input`, so clicking the label focuses the input.

Why not use random values?

You should not use `Math.random()` or manually generated random IDs for this because they can cause mismatch problems during server-side rendering and hydration.

`useId` is safe for server rendering because React can keep the generated IDs consistent between server and client, as long as the component tree is the same.

Important Points

- useId generates a unique ID for a component.
- It is useful for accessibility.
- It helps connect elements like labels, inputs, hints, and error messages.
- It should not be used to generate keys in a list.
- For list keys, use stable IDs from your data instead.

Example with multiple IDs

```jsx
import { useId } from "react";

function SignupForm() {
  const id = useId();

  return (
    <form>
      <label htmlFor={`${id}-email`}>Email</label>
      <input id={`${id}-email`} type="email" />

      <label htmlFor={`${id}-password`}>Password</label>
      <input id={`${id}-password`} type="password" />
    </form>
  );
}
```

Here, one generated ID is reused to create multiple related unique IDs.

Final Answer

`useId` is a React Hook that generates unique IDs. It is mostly used for accessibility, such as linking labels with inputs. It is safe for server-side rendering and should not be used for list keys.

### Q. Explain `useDeferredValue`

**Answer:**

`useDeferredValue` is a React Hook that lets you delay updating a non-urgent part of the UI.

React describes `useDeferredValue` as a Hook that lets you defer updating a part of the UI.

It is useful when one part of the UI should update immediately, but another expensive part can update slightly later.

Syntax

```jsx
const deferredValue = useDeferredValue(value);
```

Simple Explanation

Suppose a user is typing in a search box.

The input value should update immediately while typing. But filtering or rendering a large list based on that input may be expensive.

In that case, we can use `useDeferredValue` so that:

- The input stays fast.
- The expensive list update can happen later.
- React keeps the UI responsive.

Example

```jsx
import { useState, useDeferredValue } from "react";

function SearchPage({ products }) {
  const [search, setSearch] = useState("");

  const deferredSearch = useDeferredValue(search);

  const filteredProducts = products.filter((product) => product.name.toLowerCase().includes(deferredSearch.toLowerCase()));

  return (
    <div>
      <input value={search} onChange={(e) => setSearch(e.target.value)} placeholder="Search products" />

      <ul>
        {filteredProducts.map((product) => (
          <li key={product.id}>{product.name}</li>
        ))}
      </ul>
    </div>
  );
}
```

Here, `search` updates immediately when the user types. But `deferredSearch` may update slightly later, allowing React to keep the input responsive.

Important Points

- `useDeferredValue` does not stop the original value from updating.
- It creates a deferred version of that value.
- It is useful for expensive rendering.
- It does not add a fixed delay like `setTimeout`.
- React starts the deferred update after finishing the urgent update.
- It does not automatically reduce network requests.

Showing stale UI

Sometimes, the UI may show old results while new results are being prepared. You can show this using comparison:

```jsx
const isStale = search !== deferredSearch;
```

Example:

```jsx
<div style={{ opacity: isStale ? 0.5 : 1 }}>
  <ProductList search={deferredSearch} />
</div>
```

This tells the user that the displayed result is slightly behind the typed value.

Final Answer

`useDeferredValue` is used to defer a value so that expensive UI updates can happen later. It helps keep the interface responsive, especially during typing, searching, filtering, or rendering large lists.

### Q. Explain `useTransition`

**Answer:**

`useTransition` is a React Hook used to mark some state updates as non-urgent.

React describes `useTransition` as a Hook that lets you render a part of the UI in the background.

It helps keep the UI responsive when a state update may cause expensive rendering.

Syntax

```jsx
const [isPending, startTransition] = useTransition();
```

It returns two values:

| Value             | Meaning                                                      |
| ----------------- | ------------------------------------------------------------ |
| `isPending`       | A boolean that tells whether the transition is still running |
| `startTransition` | A function used to mark state updates as non-urgent          |

Simple Explanation

Some updates are urgent. For example:

- Typing in an input
- Clicking a button
- Opening a menu

Some updates are less urgent. For example:

- Rendering a large list
- Changing a tab with heavy content
- Updating a complex chart

`useTransition` allows React to handle urgent updates first and process non-urgent updates in the background.

Example

```jsx
import { useState, useTransition } from "react";

function SearchPage({ products }) {
  const [input, setInput] = useState("");
  const [query, setQuery] = useState("");

  const [isPending, startTransition] = useTransition();

  function handleChange(e) {
    const value = e.target.value;

    setInput(value);

    startTransition(() => {
      setQuery(value);
    });
  }

  const filteredProducts = products.filter((product) => product.name.toLowerCase().includes(query.toLowerCase()));

  return (
    <div>
      <input value={input} onChange={handleChange} />

      {isPending && <p>Updating results...</p>}

      <ul>
        {filteredProducts.map((product) => (
          <li key={product.id}>{product.name}</li>
        ))}
      </ul>
    </div>
  );
}
```

In this example:

- `setInput(value)` is urgent because the input should update immediately.
- `setQuery(value)` is wrapped inside `startTransition`, so React treats it as non-urgent.
- `isPending` can be used to show a loading or pending message.

Important Points

- `useTransition` helps prevent slow UI during expensive updates.
- It is useful when state updates trigger heavy rendering.
- `startTransition` marks state updates as low priority.
- `isPending` helps show a pending state.
- The function passed to `startTransition` runs immediately, but the state updates inside it are marked as transitions.
- `useTransition` must be called inside a component or custom Hook.

Final Answer

`useTransition` is used to mark some state updates as non-urgent so React can keep the UI responsive. It is helpful when an update causes expensive rendering. It returns isPending and startTransition.

### Q. Difference Between `useDeferredValue` and `useTransition`

**Answer:**

| Feature       | `useDeferredValue`                    | `useTransition`                   |
| ------------- | ------------------------------------- | --------------------------------- |
| Main purpose  | Defers a value                        | Defers a state update             |
| Works with    | Existing value                        | State setter function             |
| Returns       | Deferred value                        | `[isPending, startTransition]`    |
| Useful for    | Search input, filtering, large lists  | Tabs, routes, heavy state updates |
| Pending state | Does not directly provide `isPending` | Provides `isPending`              |
| Control level | Less control                          | More control                      |

Simple Difference

Use `useDeferredValue` when you already have a value and want to use a delayed version of it.

Use `useTransition` when you are updating state and want to mark that update as non-urgent.

Example Summary

```jsx
// useDeferredValue
const deferredSearch = useDeferredValue(search);
```

Here, React creates a deferred version of `search`.

```jsx
// useTransition
startTransition(() => {
  setQuery(value);
});
```

Here, React treats `setQuery(value)` as a non-urgent update.

### Q. What is a stale closure in React hooks?

**Answer:**

A stale closure happens when a callback captures values from an older render and later keeps using those outdated values.

This commonly happens with:

- `setTimeout`
- `setInterval`
- Event listeners
- Async callbacks
- Effects with missing dependencies

**Example:**

```jsx
function Counter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    const timer = setInterval(() => {
      console.log(count);
    }, 1000);

    return () => clearInterval(timer);
  }, []);

  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

Because the effect runs only once, the callback closes over the initial `count`.

**Interview Line**

A stale closure occurs when a callback captures state or props from an older render and later uses those outdated values.

### Q. How do you fix stale closure issues?

**Answer:**

Common solutions are:

1. Add the correct dependencies.
2. Use functional state updates.
3. Use refs when a stable callback must read the latest value.
4. Recreate subscriptions when dependencies change.

**Example:**

```jsx
setCount((prevCount) => prevCount + 1);
```

This avoids depending on an old captured `count`.

Another fix is:

```jsx
useEffect(() => {
  console.log(count);
}, [count]);
```

**Interview Line**

Fix stale closures with correct dependencies, functional updates, or refs when stable callbacks need access to the latest value.

### Q. Why should hooks not be called conditionally?

**Answer:**

React relies on hooks being called in the same order on every render.

**Bad Example:**

```jsx
function Component({ enabled }) {
  if (enabled) {
    const [count, setCount] = useState(0);
  }

  return <div />;
}
```

If `enabled` changes, the hook call order changes too.

A safer approach is:

```jsx
function Component({ enabled }) {
  const [count, setCount] = useState(0);

  if (!enabled) {
    return null;
  }

  return <div>{count}</div>;
}
```

**Interview Line**

Hooks must not be called conditionally because React depends on a consistent hook call order across renders.

### Q. Why does hook order matter?

**Answer:**

React associates hook state by call position.

Conceptually:

```text
Hook 1 -> first useState
Hook 2 -> second useState
Hook 3 -> useEffect
```

If the order changes on a later render, React could associate stored state with the wrong hook.

**Interview Line**

Hook order matters because React tracks hooks by their call position, so the order must remain stable on every render.

### Q. What is dependency array mistake in `useEffect`?

**Answer:**

A dependency array mistake happens when the listed dependencies do not correctly represent the reactive values used inside the effect.

**Example:**

```jsx
useEffect(() => {
  fetchUser(userId);
}, []);
```

If `userId` changes, the effect will not run again.

Correct version:

```jsx
useEffect(() => {
  fetchUser(userId);
}, [userId]);
```

**Interview Line**

A dependency array mistake occurs when the effect's dependency list does not match the changing state, props, or functions it uses.

### Q. What happens if a dependency is missing in `useEffect`?

**Answer:**

The effect may use stale state or props and fail to synchronize when values change.

**Example:**

```jsx
useEffect(() => {
  console.log(userId);
}, []);
```

If `userId` changes later, the effect still reflects the value from the render where it was created.

This can cause:

- Stale data
- Wrong API requests
- Incorrect subscriptions
- Missed updates

**Interview Line**

A missing dependency can cause stale closures and prevent the effect from responding to required changes.

### Q. What happens if unnecessary dependencies are added in `useEffect`?

**Answer:**

The effect may run more often than needed.

**Example:**

```jsx
const options = {
  page: 1,
};

useEffect(() => {
  fetchData(options);
}, [options]);
```

A new `options` object is created every render, so the effect runs again every time.

Possible results include:

- Duplicate API calls
- Extra cleanup
- Repeated subscriptions
- Infinite loops

**Interview Line**

Unnecessary dependencies can cause repeated effect execution, especially when objects or functions get new references every render.

### Q. How do you safely call APIs inside `useEffect`?

**Answer:**

A safe API effect should handle errors and stale requests.

**Example:**

```jsx
useEffect(() => {
  const controller = new AbortController();

  async function loadUser() {
    try {
      const response = await fetch(`/api/users/${userId}`, {
        signal: controller.signal,
      });

      if (!response.ok) {
        throw new Error("Request failed");
      }

      const data = await response.json();

      setUser(data);
    } catch (error) {
      if (error.name !== "AbortError") {
        setError(error);
      }
    }
  }

  loadUser();

  return () => {
    controller.abort();
  };
}, [userId]);
```

**Interview Line**

API calls inside `useEffect` should handle errors and cancel stale requests during cleanup, usually with `AbortController`.

### Q. How do you avoid infinite loops in `useEffect`?

**Answer:**

Infinite loops often happen when an effect updates a value that is also one of its dependencies.

**Bad Example:**

```jsx
useEffect(() => {
  setCount(count + 1);
}, [count]);
```

This creates:

```text
count changes
↓
effect runs
↓
setCount changes count
↓
effect runs again
```

Also avoid unstable dependencies such as freshly created objects or functions unless they are required.

**Interview Line**

Infinite loops happen when an effect repeatedly changes one of its own dependencies or depends on unstable values.

### Q. How do you clean up subscriptions in `useEffect`?

**Answer:**

Return a cleanup function from the effect.

**Example:**

```jsx
useEffect(() => {
  const unsubscribe = store.subscribe(handleUpdate);

  return () => {
    unsubscribe();
  };
}, []);
```

Cleanup runs when the component unmounts or before the effect reruns because dependencies changed.

**Interview Line**

Subscriptions should be removed in the function returned from `useEffect` to prevent leaks and duplicate listeners.

### Q. How do you clean up timers in `useEffect`?

**Answer:**

Clear timers in the cleanup function.

**Example:**

```jsx
useEffect(() => {
  const timer = setTimeout(() => {
    console.log("Done");
  }, 1000);

  return () => {
    clearTimeout(timer);
  };
}, []);
```

For intervals:

```jsx
return () => {
  clearInterval(interval);
};
```

**Interview Line**

Timers created inside effects should be cleared during cleanup using `clearTimeout()` or `clearInterval()`.

### Q. How do you handle race conditions inside `useEffect`?

**Answer:**

Race conditions happen when older requests finish after newer ones and overwrite the latest state.

A common solution is to cancel the previous request.

**Example:**

```jsx
useEffect(() => {
  const controller = new AbortController();

  fetch(`/api/users/${userId}`, {
    signal: controller.signal,
  })
    .then((res) => res.json())
    .then(setUser)
    .catch((error) => {
      if (error.name !== "AbortError") {
        console.error(error);
      }
    });

  return () => {
    controller.abort();
  };
}, [userId]);
```

**Interview Line**

Prevent effect race conditions by cancelling stale requests or ignoring responses that are no longer current.

### Q. How do you skip the first execution of `useEffect`?

**Answer:**

A ref can track whether the first execution has already happened.

**Example:**

```jsx
const isFirstRender = useRef(true);

useEffect(() => {
  if (isFirstRender.current) {
    isFirstRender.current = false;
    return;
  }

  console.log("Value changed");
}, [value]);
```

This pattern should be used only when skipping the initial run is truly required.

**Interview Line**

Use a ref to detect the initial render when an effect intentionally needs to skip its first execution.

### Q. How do you compare previous and current props using hooks?

**Answer:**

Store the previous value inside a ref.

**Example:**

```jsx
const previousUserId = useRef();

useEffect(() => {
  console.log("Previous:", previousUserId.current);
  console.log("Current:", userId);

  previousUserId.current = userId;
}, [userId]);
```

Because refs persist between renders, the previous value is available on the next update.

**Interview Line**

Use a ref to store the previous prop so it can be compared with the current value on the next render.

### Q. How do you create a `usePrevious` hook?

**Answer:**

A simple implementation stores the current value after render.

**Example:**

```jsx
function usePrevious(value) {
  const ref = useRef();

  useEffect(() => {
    ref.current = value;
  }, [value]);

  return ref.current;
}
```

Usage:

```jsx
const previousCount = usePrevious(count);
```

On the first render, the previous value is usually `undefined`.

**Interview Line**

`usePrevious` stores a value in a ref after render and returns the value from the previous render.

### Q. What is the difference between `useRef` and a normal variable?

**Answer:**

A normal variable is recreated whenever the component function runs.

A ref persists across renders.

**Example:**

```jsx
let count = 0;
```

is recreated each render.

But:

```jsx
const countRef = useRef(0);
```

keeps the same ref object between renders.

Comparison:

| Normal Variable                | `useRef`                           |
| ------------------------------ | ---------------------------------- |
| Recreated on render            | Persists across renders            |
| Does not trigger render        | Does not trigger render            |
| Good for temporary calculation | Good for persistent mutable values |

**Interview Line**

Normal variables are recreated on each render, while `useRef` persists across renders without triggering re-renders.

### Q. Why does changing `useRef.current` not trigger re-render?

**Answer:**

React does not treat `ref.current` as reactive state.

A ref is intentionally a mutable container.

**Example:**

```jsx
const countRef = useRef(0);

function handleClick() {
  countRef.current++;
}
```

This updates the stored value but does not schedule a render.

If a value should appear in the UI and update it, use state instead.

**Interview Line**

Changing `ref.current` does not trigger rendering because refs are mutable storage outside React's reactive state system.

### Q. When can `useMemo` hurt performance?

**Answer:**

`useMemo` has its own cost because React must store the value and compare dependencies.

**Bad Example:**

```jsx
const total = useMemo(() => {
  return a + b;
}, [a, b]);
```

For a cheap calculation, memoization may cost more than recalculating.

Use it when:

- The calculation is expensive
- Stable reference identity matters
- Profiling shows a real benefit

**Interview Line**

`useMemo` can hurt performance when used for cheap work because dependency tracking and memoization also have overhead.

### Q. When can `useCallback` be unnecessary?

**Answer:**

`useCallback` is unnecessary when stable function identity does not provide any real benefit.

**Example:**

```jsx
const handleClick = useCallback(() => {
  setCount((count) => count + 1);
}, []);
```

If this callback is only used by a normal button, memoization may not improve anything.

It is more useful when:

- Passing callbacks to memoized children
- Another hook requires stable identity
- Function identity affects behavior

**Interview Line**

`useCallback` is unnecessary when function identity does not matter and no meaningful render work is being avoided.

### Q. What is the difference between memoizing value and memoizing component?

**Answer:**

`useMemo` memoizes a computed value.

```jsx
const filteredUsers = useMemo(() => {
  return users.filter(filterUser);
}, [users]);
```

`React.memo` memoizes a component based on its props.

```jsx
const UserCard = React.memo(function UserCard({ user }) {
  return <div>{user.name}</div>;
});
```

Comparison:

| `useMemo`             | `React.memo`                 |
| --------------------- | ---------------------------- |
| Memoizes a value      | Memoizes component rendering |
| Used inside component | Wraps component              |
| Uses dependency array | Compares props               |

**Interview Line**

`useMemo` caches a computed value, while `React.memo` can skip rendering a component when its props are unchanged.

### Q. How do you create a custom hook for API fetching?

**Answer:**

A custom hook can encapsulate data, loading, error, and cleanup.

**Example:**

```jsx
function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const controller = new AbortController();

    async function load() {
      try {
        setLoading(true);

        const response = await fetch(url, {
          signal: controller.signal,
        });

        if (!response.ok) {
          throw new Error("Request failed");
        }

        setData(await response.json());
      } catch (error) {
        if (error.name !== "AbortError") {
          setError(error);
        }
      } finally {
        setLoading(false);
      }
    }

    load();

    return () => controller.abort();
  }, [url]);

  return { data, loading, error };
}
```

For complex server state, a library such as TanStack Query is usually more capable.

**Interview Line**

A custom API hook can encapsulate fetching, loading, error, and cleanup, while complex server state is often better handled by a query library.

### Q. How do you create a custom hook for debounce?

**Answer:**

A debounce hook delays exposing the latest value until it stops changing for a configured duration.

**Example:**

```jsx
function useDebounce(value, delay) {
  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {
    const timer = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);

    return () => clearTimeout(timer);
  }, [value, delay]);

  return debouncedValue;
}
```

**Interview Line**

A debounce hook waits until a value remains unchanged for a given delay before updating the debounced value.

### Q. How do you create a custom hook for localStorage?

**Answer:**

A custom hook can synchronize React state with browser storage.

**Example:**

```jsx
function useLocalStorage(key, initialValue) {
  const [value, setValue] = useState(() => {
    const stored = localStorage.getItem(key);

    return stored !== null ? JSON.parse(stored) : initialValue;
  });

  useEffect(() => {
    localStorage.setItem(key, JSON.stringify(value));
  }, [key, value]);

  return [value, setValue];
}
```

In server-rendered environments, `localStorage` should only be accessed on the client.

**Interview Line**

A `useLocalStorage` hook keeps React state synchronized with persistent browser storage.

### Q. What are best practices for writing custom hooks?

**Answer:**

Good custom hooks should:

1. Start with `use`.
2. Have one clear responsibility.
3. Follow the Rules of Hooks.
4. Handle cleanup correctly.
5. Expose a predictable API.
6. Avoid unnecessary hidden side effects.
7. Keep dependencies correct.
8. Share logic rather than UI.

**Example:**

Good:

```jsx
useDebounce(value, 500);
```

Less clear:

```jsx
useEverything();
```

which may manage unrelated concerns.

**Interview Line**

Good custom hooks have a focused responsibility, correct cleanup and dependencies, and a clear reusable API.

### Q. How do you test custom hooks?

**Answer:**

Custom hooks should be tested through their observable behavior.

Typical checks include:

- Initial value
- State updates
- Async behavior
- Cleanup
- Errors
- Dependency changes

For timer-based hooks, fake timers are useful.

For API hooks, mock the network boundary instead of depending on real external services.

**Example:**

```jsx
function TestComponent() {
  const value = useDebounce("hello", 500);

  return <div>{value}</div>;
}
```

The test can render the component, advance timers, and verify the displayed value.

**Interview Line**

Test custom hooks by verifying their public behavior, including state changes, async results, cleanup, and dependency reactions.

## Forms & Events

### Q. What are controlled components?

**Answer:**

Controlled components are form elements whose value is controlled by React state.

```jsx
const [name, setName] = useState("");

<input value={name} onChange={(e) => setName(e.target.value)} />;
```

Key points:

- Single source of truth = React state
- Easy validation & control
- Re-renders on every change

**Interview Line**

“In controlled components, React controls the form data.”

### Q. What are uncontrolled components?

**Answer:**

Uncontrolled components store their form data in the DOM itself, not in React state.

```jsx
const inputRef = useRef();

<input ref={inputRef} />;
```

Key points:

- Uses ref to access values
- Fewer re-renders
- Less control

**Interview Line**

“Uncontrolled components rely on the DOM for form state.”

### Q. Difference between controlled and uncontrolled components

**Answer:**

| Controlled        | Uncontrolled       |
| ----------------- | ------------------ |
| State-driven      | DOM-driven         |
| More control      | Less control       |
| Easier validation | Harder validation  |
| More re-renders   | Better performance |

One-liner:

“Controlled = React state, Uncontrolled = DOM state.”

### Q. How does React handle events?

**Answer:**

React handles events using camelCase syntax and passes a function as the handler.

```jsx
<button onClick={handleClick}>Click</button>
```

Differences from HTML:

- onClick instead of onclick
- Uses synthetic events

Interview tip:

“Event handlers are passed as functions, not strings.”

### Q. Why does React use synthetic events?

**Answer:**

React wraps native browser events into Synthetic Events.

Benefits:

- Cross-browser compatibility
- Consistent behavior
- Better performance via event delegation

**Interview Line**

“Synthetic events normalize event behavior across browsers.”

### Q. How do you handle form validation?

**Answer:**

Common approaches:

1️⃣ Manual validation

```jsx
if (!email) setError("Email required");
```

2️⃣ On submit validation

- Validate before API call

3️⃣ Library-based

- Yup + Formik
- React Hook Form

Interview phrase:

“Validation can be handled manually or using form libraries.”

### Q. How do you handle multiple inputs in a form?

**Answer:**

By using a single state object and dynamic keys.

```jsx
const [formData, setFormData] = useState({ name: "", email: "" });

const handleChange = (e) => {
  setFormData({
    ...formData,
    [e.target.name]: e.target.value,
  });
};
```

```jsx
<input name="email" onChange={handleChange} />
```

Interview tip:

“One handler can manage multiple inputs using the name attribute.”

### Q. How do you optimize large forms?

**Answer:**

Techniques interviewers expect:

✅ Reduce re-renders

- Use useCallback
- Split into smaller components
- React.memo

✅ Use uncontrolled inputs where possible

- Especially for non-critical fields

✅ Use form libraries

- React Hook Form (uncontrolled by default)

✅ Lazy load form sections

- Step-based forms

**Interview Line**

“Optimizing large forms is about minimizing re-renders and splitting responsibilities.”

### Q. How do you handle checkbox inputs in React?

**Answer:**

Checkboxes are usually handled as controlled inputs using the `checked` prop and an `onChange` handler.

**Example:**

```jsx
function TermsForm() {
  const [accepted, setAccepted] = useState(false);

  return (
    <label>
      <input type="checkbox" checked={accepted} onChange={(event) => setAccepted(event.target.checked)} />
      Accept terms
    </label>
  );
}
```

For checkboxes, the current value comes from:

```js
event.target.checked;
```

not:

```js
event.target.value;
```

For multiple checkbox values, state can be stored in an array or object.

**Interview Line**

React checkboxes are commonly controlled using `checked` and `onChange`, with the current boolean value read from `event.target.checked`.

### Q. How do you handle radio buttons in React?

**Answer:**

Radio buttons are usually controlled using one shared state value for the entire group.

Each radio button has the same `name` but a different `value`.

**Example:**

```jsx
function PaymentForm() {
  const [method, setMethod] = useState("card");

  return (
    <>
      <label>
        <input type="radio" name="payment" value="card" checked={method === "card"} onChange={(event) => setMethod(event.target.value)} />
        Card
      </label>

      <label>
        <input type="radio" name="payment" value="upi" checked={method === "upi"} onChange={(event) => setMethod(event.target.value)} />
        UPI
      </label>
    </>
  );
}
```

Only one option in the group should match the current state.

**Interview Line**

Radio buttons are controlled with one shared state value, and each option checks whether its own value matches that state.

### Q. How do you handle select dropdowns in React?

**Answer:**

A select dropdown is usually controlled through the `value` prop and `onChange`.

**Example:**

```jsx
function CountrySelect() {
  const [country, setCountry] = useState("");

  return (
    <select value={country} onChange={(event) => setCountry(event.target.value)}>
      <option value="">Select country</option>

      <option value="india">India</option>

      <option value="japan">Japan</option>
    </select>
  );
}
```

For multi-select:

```jsx
<select multiple>
```

the selected options can be collected from:

```js
event.target.selectedOptions;
```

**Interview Line**

Select elements are usually controlled using `value` and `onChange`, with the selected option read from `event.target.value`.

### Q. How do you handle file upload input in React?

**Answer:**

File inputs are usually accessed through the `files` property of the input element.

**Example:**

```jsx
function FileUpload() {
  const [file, setFile] = useState(null);

  function handleChange(event) {
    const selectedFile = event.target.files?.[0];

    setFile(selectedFile ?? null);
  }

  return <input type="file" onChange={handleChange} />;
}
```

To upload the file, `FormData` is commonly used.

```js
const formData = new FormData();

formData.append("file", file);

await fetch("/api/upload", {
  method: "POST",
  body: formData,
});
```

**Interview Line**

File inputs are handled through `event.target.files`, and uploads are commonly sent using `FormData`.

### Q. Why is file input usually uncontrolled?

**Answer:**

Browsers do not allow JavaScript to programmatically set the selected file path for security reasons.

Because of that, file inputs cannot be controlled in the same way as text inputs.

For example, this is not a normal controlled pattern:

```jsx
<input type="file" value={file} />
```

Instead, React reads the selected files from the DOM input.

**Example:**

```jsx
<input
  type="file"
  onChange={(event) => {
    const file = event.target.files?.[0];
  }}
/>
```

Refs are also commonly used when direct access to the input is needed.

**Interview Line**

File inputs are usually uncontrolled because browsers do not allow applications to programmatically control the selected file value for security reasons.

### Q. How do you handle dynamic form fields?

**Answer:**

Dynamic form fields are usually stored in an array of objects in state.

**Example:**

```jsx
const [skills, setSkills] = useState([
  {
    id: 1,
    name: "",
  },
]);
```

Adding a field:

```jsx
function addSkill() {
  setSkills((prev) => [
    ...prev,
    {
      id: Date.now(),
      name: "",
    },
  ]);
}
```

Updating a field:

```jsx
function updateSkill(id, value) {
  setSkills((prev) =>
    prev.map((skill) =>
      skill.id === id
        ? {
            ...skill,
            name: value,
          }
        : skill,
    ),
  );
}
```

Stable IDs are important so React can correctly track each input.

**Interview Line**

Dynamic form fields are usually modeled as arrays in state and updated immutably using stable IDs.

### Q. How do you handle dependent dropdowns?

**Answer:**

A dependent dropdown changes its available options based on another selected value.

**Example:**

```jsx
const [country, setCountry] = useState("");

const [city, setCity] = useState("");
```

If the country changes, the city list changes.

```jsx
const cities = {
  india: ["Mumbai", "Pune"],
  japan: ["Tokyo", "Osaka"],
};
```

Rendering:

```jsx
<select
  value={country}
  onChange={(event) => {
    setCountry(
      event.target.value
    );

    setCity("");
  }}
>
  {/* country options */}
</select>

<select
  value={city}
  onChange={(event) =>
    setCity(
      event.target.value
    )
  }
>
  {(cities[country] || [])
    .map((city) => (
      <option
        key={city}
        value={city}
      >
        {city}
      </option>
    ))}
</select>
```

If options come from an API, fetch them when the parent selection changes.

**Interview Line**

Dependent dropdowns derive or fetch child options from the selected parent value and should reset invalid child selections when the parent changes.

### Q. How do you handle form reset?

**Answer:**

For controlled forms, reset state back to its initial values.

**Example:**

```jsx
const initialForm = {
  name: "",
  email: "",
};

const [form, setForm] = useState(initialForm);
```

Reset:

```jsx
function resetForm() {
  setForm(initialForm);
}
```

If the form is uncontrolled, the native form reset API can be used.

```jsx
<form ref={formRef}>
```

```js
formRef.current?.reset();
```

For file inputs, resetting the DOM input may also be necessary.

**Interview Line**

Controlled forms reset by restoring initial state, while uncontrolled forms can use the native form reset behavior.

### Q. How do you show field-level validation errors?

**Answer:**

Field-level errors are usually stored by field name.

**Example:**

```jsx
const [errors, setErrors] = useState({});
```

Validation:

```js
const nextErrors = {};

if (!form.email) {
  nextErrors.email = "Email is required";
}
```

Rendering:

```jsx
<input value={form.email} onChange={handleChange} />;

{
  errors.email && <p className="error">{errors.email}</p>;
}
```

This gives users feedback close to the field that needs correction.

**Interview Line**

Field-level validation errors are usually stored by field key and displayed next to the corresponding input.

### Q. How do you handle server-side validation errors in forms?

**Answer:**

Server-side validation errors should be mapped back to the correct fields when possible.

Suppose the API returns:

```json
{
  "errors": {
    "email": "Email already exists",
    "password": "Password is too weak"
  }
}
```

The frontend can store them directly:

```js
setErrors(responseData.errors);
```

Then render:

```jsx
{
  errors.email && <p>{errors.email}</p>;
}
```

General errors that do not belong to one field can be displayed at form level.

Client-side validation improves UX, but server-side validation is still required for security and correctness.

**Interview Line**

Server validation errors should be mapped to individual fields when possible, while general failures should be shown at form level.

### Q. What is touched state in forms?

**Answer:**

Touched state tracks whether the user has interacted with a field, usually by focusing and then leaving it.

**Example:**

```js
const [touched, setTouched] = useState({});
```

On blur:

```jsx
<input
  onBlur={() =>
    setTouched((prev) => ({
      ...prev,
      email: true,
    }))
  }
/>
```

Validation can then be shown only when:

```js
touched.email && errors.email;
```

This prevents displaying errors before the user has had a chance to interact with the field.

**Interview Line**

Touched state tells whether a field has been interacted with and is commonly used to decide when validation messages should appear.

### Q. What is dirty state in forms?

**Answer:**

Dirty state indicates whether a form field or form value has changed from its initial value.

**Example:**

Initial:

```js
const initialEmail = "";
```

Current:

```js
email !== initialEmail;
```

means the field is dirty.

Form libraries often expose:

```text
isDirty
dirtyFields
```

Dirty state is useful for:

- Enabling save buttons
- Showing unsaved-change warnings
- Avoiding unnecessary updates
- Tracking modified fields

**Interview Line**

Dirty state indicates whether the current form value differs from its initial value.

### Q. How do you prevent multiple form submissions?

**Answer:**

The submit action should be disabled while a request is already in progress.

**Example:**

```jsx
const [isSubmitting, setIsSubmitting] = useState(false);

async function handleSubmit(event) {
  event.preventDefault();

  if (isSubmitting) {
    return;
  }

  try {
    setIsSubmitting(true);

    await saveForm();
  } finally {
    setIsSubmitting(false);
  }
}
```

Button:

```jsx
<button disabled={isSubmitting}>Submit</button>
```

The backend should also be designed to handle duplicate requests safely for important operations.

**Interview Line**

Prevent duplicate submissions by tracking submission state, disabling repeated actions, and making critical backend operations idempotent where appropriate.

### Q. How do you handle form submission loading state?

**Answer:**

Loading state should reflect whether the form submission is currently in progress.

**Example:**

```jsx
const [isSubmitting, setIsSubmitting] = useState(false);
```

During submission:

```js
try {
  setIsSubmitting(true);

  await submitForm();
} finally {
  setIsSubmitting(false);
}
```

UI:

```jsx
<button disabled={isSubmitting}>{isSubmitting ? "Saving..." : "Save"}</button>
```

The form can also show a spinner or loading indicator.

The user should still receive clear success or error feedback after submission completes.

**Interview Line**

Track submission state explicitly so the UI can disable duplicate actions and show meaningful loading feedback.

### Q. How do you improve performance in forms with many fields?

**Answer:**

Large forms can become slow when every keystroke causes a large component tree to re-render.

Common optimizations include:

- Split large forms into smaller components
- Keep state close to the field that needs it
- Avoid unnecessary global state
- Memoize expensive components only when useful
- Debounce expensive validation
- Use uncontrolled inputs where appropriate
- Use form libraries optimized for large forms

**Example:**

Instead of one large component controlling 100 fields, divide it into sections:

```text
ProfileForm
├── PersonalDetails
├── AddressFields
├── Preferences
└── PaymentDetails
```

Measure before adding memoization everywhere.

**Interview Line**

Large-form performance improves by reducing the scope of re-renders, colocating state, splitting sections, and avoiding expensive validation on every keystroke.

### Q. What is event pooling in React?

**Answer:**

Event pooling was an optimization used by older versions of React's SyntheticEvent system.

React reused event objects after the event handler finished.

Because of that, accessing an event asynchronously could return cleared values.

**Older Example:**

```jsx
function handleChange(event) {
  setTimeout(() => {
    console.log(event.target.value);
  }, 1000);
}
```

In older React versions, developers sometimes needed:

```js
event.persist();
```

to keep the event object available.

This behavior is mainly relevant when discussing older React code.

**Interview Line**

Event pooling was an older React optimization where SyntheticEvent objects were reused after handlers completed.

### Q. Is event pooling still an issue in modern React?

**Answer:**

No, event pooling is no longer a normal concern in modern React on the web.

Modern React no longer clears SyntheticEvent objects in the old pooled-event way.

So code like:

```jsx
function handleClick(event) {
  setTimeout(() => {
    console.log(event.target);
  }, 100);
}
```

does not require:

```js
event.persist();
```

for the old pooling reason.

You may still copy values early when it makes the code clearer or when the DOM element itself may change.

**Interview Line**

Event pooling is primarily an older React concern; modern React web applications generally do not need `event.persist()`.

### Q. How do you pass parameters to event handlers?

**Answer:**

The most common approach is to use an arrow function.

**Example:**

```jsx
function UserList() {
  function handleDelete(id) {
    console.log("Delete:", id);
  }

  return <button onClick={() => handleDelete(10)}>Delete</button>;
}
```

Another option is `bind()`:

```jsx
<button
  onClick={
    handleDelete.bind(
      null,
      10
    )
  }
>
```

Arrow functions are generally easier to read.

**Interview Line**

Pass parameters to event handlers by wrapping the handler in an arrow function or by using `bind()`.

### Q. Why should event handlers not be called directly in JSX?

**Answer:**

React expects an event handler prop to receive a function, not the result of calling that function.

**Wrong:**

```jsx
<button onClick={handleClick()}>Click</button>
```

This executes `handleClick()` during rendering.

If it updates state, it can cause repeated renders or loops.

Correct:

```jsx
<button onClick={handleClick}>Click</button>
```

With parameters:

```jsx
<button onClick={() => handleClick(10)}>Click</button>
```

**Interview Line**

Event handlers should be passed as functions, not executed during render, otherwise the handler runs immediately instead of waiting for the event.

### Q. What is the difference between `onChange` in React and native JavaScript?

**Answer:**

React's `onChange` behavior is normalized so form inputs usually notify the component as their value changes.

**React Example:**

```jsx
<input value={name} onChange={(event) => setName(event.target.value)} />
```

For text inputs, React's `onChange` behaves similarly to the browser's `input` event and updates on each user edit.

Historically, native DOM `change` behavior for some form elements could fire after the value was committed, such as when focus changed.

React provides one consistent abstraction across supported form elements.

**Interview Line**

React's `onChange` is a normalized event that usually fires on each value change for controlled form inputs, unlike the historically different native `change` behavior for some elements.

## State Management

### Q. What is lifting state up?

**Answer:**

Lifting state up means moving state to the closest common parent component so that multiple child components can share and sync the same data.

Why it’s needed:

React data flows top → down. If two siblings need the same state, it must live in their parent.

Example:

A parent holds selectedItem, and two child components read/update it.

Interview one-liner:

“Lifting state up is the process of moving shared state to a common ancestor so multiple components can access and modify it consistently.”

### Q. What is global state?

**Answer:**

Global state is application-wide state that is shared across many unrelated components.

Examples:

- Logged-in user info
- Theme (dark/light)
- Language
- Cart data

Why not local state?

Passing props through many levels causes prop drilling.

Interview one-liner:

“Global state stores data that needs to be accessed by many components across the app, regardless of their position in the component tree.”

### Q. When should you use Context API?

**Answer:**

Use Context API when:

- State is global or semi-global
- Data changes infrequently
- You want to avoid prop drilling
- App is small to medium

Common use cases:

Theme

- Auth user
- Language
- Feature flags

Interview one-liner:

“Context API is best for sharing global data like theme or auth where updates are not very frequent.”

### Q. Limitations of Context API

**Answer:**

Key limitations:

1. Performance issues
   - Any context change re-renders all consumers

2. Not designed for complex logic
   - No middleware
   - No async handling pattern

3. Harder to debug
   - No time-travel or devtools like Redux

4. Scalability issues
   - Large apps become messy

Interview tip:

Say Context is not a replacement for Redux.

One-liner:

“Context API is great for simple global state but not suitable for complex, frequently changing data.”

### Q. What is Redux?

**Answer:**

Redux is a predictable state management library that centralizes application state in a single store.

Key idea:

State changes happen in a controlled, predictable way.

Interview one-liner:

“Redux is a state management library that helps manage complex global state using a single source of truth.”

### Q. Core principles of Redux

**Answer:**

There are 3 core principles 👇

1. Single source of truth

   → Entire state is stored in one store

2. State is read-only

   → State can only be changed by dispatching actions

3. Changes via pure functions

   → Reducers are pure functions that return new state

Interview one-liner:

“Redux follows single source of truth, immutable state updates, and pure reducers.”

### Q. Redux vs Context API

**Answer:**

| Feature     | Context API          | Redux               |
| ----------- | -------------------- | ------------------- |
| Purpose     | Data sharing         | State management    |
| Performance | Can cause re-renders | Optimized           |
| Async logic | ❌ No                | ✅ Yes              |
| Middleware  | ❌ No                | ✅ Yes              |
| DevTools    | ❌ Limited           | ✅ Powerful         |
| Best for    | Simple global state  | Large, complex apps |

Interview conclusion:

“Context API solves prop drilling, Redux solves complex state management.”

### Q. What is a store in Redux?

**Answer:**

The store is an object that:

- Holds the entire app state
- Allows state access via `getState()`
- Updates state via `dispatch()`
- Registers listeners via `subscribe()`

One store per app.

Interview one-liner:

“The Redux store holds the complete application state and manages updates through actions and reducers.”

### Q. What are actions?

**Answer:**

Actions are plain JavaScript objects that describe what happened.

Structure:

```js
{ type: "ADD_TODO", payload: data }
```

Key point:

Actions do not change state, they just describe intent.

One-liner:

“Actions are objects that describe events that trigger state changes.”

### Q. What are reducers?

**Answer:**

Reducers are pure functions that:

- Take state and action
- Return new state

```js
(state, action) => newState;
```

Rules:

- No mutation
- No async code
- No side effects

Interview one-liner:

“Reducers specify how the state changes in response to actions.”

### Q. What is dispatch?

**Answer:**

`dispatch()` is used to send an action to the Redux store.

Flow:
UI → dispatch(action) → reducer → store update

One-liner:

“Dispatch sends an action to the store to trigger a state update.”

### Q. What are middleware in Redux?

**Answer:**

Middleware sits between dispatch and reducer.

Used for:

- Async logic
- API calls
- Logging
- Error handling

Flow:

dispatch → middleware → reducer

One-liner:

“Middleware extends Redux to handle side effects like async operations.”

### Q. What is Redux Thunk?

**Answer:**

Redux Thunk allows dispatching functions instead of objects.

Used for:

- Async API calls
- Delayed dispatch

```jsx
dispatch((dispatch) => {
  fetchData().then((res) => dispatch({ type: "SUCCESS", payload: res }));
});
```

One-liner:

“Redux Thunk enables async logic by allowing functions to be dispatched.”

### Q. What is Redux Saga?

**Answer:**

Redux Saga uses generator functions to manage async flows.

Best for:

- Complex async workflows
- Background tasks
- Cancellation, retry, debounce

Compared to Thunk:

- More powerful
- Steeper learning curve

One-liner:

“Redux Saga handles complex async logic using generator functions.”

### Q. What is RTK (Redux Toolkit)?

**Answer:**

Redux Toolkit is the official, recommended way to write Redux.

It provides:

- configureStore
- createSlice
- Built-in thunk
- Less boilerplate

Key benefit:

You write less code, safer code.

One-liner:

“Redux Toolkit simplifies Redux development with less boilerplate and better defaults.”

### Q. Why is Redux Toolkit recommended?

**Answer:**

Reasons:

- Reduces boilerplate
- Prevents common mistakes
- Built-in DevTools
- Uses Immer (safe mutation)
- Better performance defaults

Interview closing statement (important):

“Redux Toolkit is recommended because it makes Redux easier, safer, and more maintainable.”

### 🔥 Interview Tip (Very Important)

If asked “Do we still need Redux?”, say:

“For small apps, Context API is enough. For large apps with complex state and async logic, Redux Toolkit is still very relevant.”

### Q. What is local component state?

**Answer:**

Local component state is state that belongs to a specific component and is only needed by that component or its close children.

It is commonly managed with hooks such as:

```jsx
useState();
useReducer();
```

**Example:**

```jsx
function Modal() {
  const [isOpen, setIsOpen] = useState(false);

  return (
    <>
      <button onClick={() => setIsOpen(true)}>Open</button>

      {isOpen && <Dialog />}
    </>
  );
}
```

Here, `isOpen` is local because only the `Modal` component needs it.

Local state is useful for:

- Form inputs
- Toggle states
- Modal visibility
- Selected tabs
- UI interactions

**Interview Line**

Local state is state owned by a component and should remain local when no wider part of the application needs it.

### Q. What is derived state?

**Answer:**

Derived state is a value that can be calculated from existing state or props instead of being stored separately.

**Example:**

```jsx
const [firstName, setFirstName] = useState("John");

const [lastName, setLastName] = useState("Doe");
```

Instead of storing:

```jsx
const [fullName, setFullName] = useState("");
```

we can derive it:

```jsx
const fullName = `${firstName} ${lastName}`;
```

`fullName` does not need its own state because it can always be calculated from `firstName` and `lastName`.

**Interview Line**

Derived state is data calculated from existing props or state and usually does not need to be stored separately.

### Q. Why should derived state be avoided when possible?

**Answer:**

Stored derived state creates multiple sources of truth.

**Bad Example:**

```jsx
const [price, setPrice] = useState(100);

const [quantity, setQuantity] = useState(2);

const [total, setTotal] = useState(200);
```

Now every update must keep `total` synchronized.

If `price` changes but `total` is not updated, state becomes inconsistent.

Better:

```jsx
const total = price * quantity;
```

If the calculation is expensive, memoization may be considered:

```jsx
const total = useMemo(() => calculateTotal(items), [items]);
```

**Interview Line**

Avoid storing derived state because it creates duplicate sources of truth and can easily become inconsistent with the original state.

### Q. What is duplicated state?

**Answer:**

Duplicated state means storing the same logical information in multiple places.

**Example:**

```jsx
const [users, setUsers] = useState([
  {
    id: 1,
    name: "John",
  },
]);

const [selectedUser, setSelectedUser] = useState({
  id: 1,
  name: "John",
});
```

The selected user object duplicates information already stored in `users`.

A safer approach is:

```jsx
const [selectedUserId, setSelectedUserId] = useState(1);

const selectedUser = users.find((user) => user.id === selectedUserId);
```

Now the user data exists in one source of truth.

**Interview Line**

Duplicated state stores the same logical data in multiple places, increasing synchronization problems and inconsistency risk.

### Q. Why is duplicated state dangerous?

**Answer:**

Duplicated state is dangerous because one copy can change while another remains outdated.

**Example:**

```text
users[0].name = "Mike"
```

but:

```text
selectedUser.name = "John"
```

Now different parts of the UI may display different values for the same user.

Problems include:

- Inconsistent UI
- Difficult updates
- More synchronization logic
- More bugs
- Harder debugging

The safer design is to store one source of truth and derive related values from it.

**Interview Line**

Duplicated state is dangerous because multiple copies of the same data can become inconsistent and create synchronization bugs.

### Q. What is normalized state?

**Answer:**

Normalized state stores entities by ID instead of deeply nesting repeated objects.

**Example:**

Instead of:

```js
const posts = [
  {
    id: 1,
    title: "Post",
    author: {
      id: 10,
      name: "John",
    },
  },
];
```

normalized state may look like:

```js
const state = {
  users: {
    10: {
      id: 10,
      name: "John",
    },
  },

  posts: {
    1: {
      id: 1,
      title: "Post",
      authorId: 10,
    },
  },
};
```

Each entity exists in one place and relationships are represented using IDs.

**Interview Line**

Normalized state stores entities separately by ID and represents relationships with references instead of duplicating nested objects.

### Q. Why is normalized state useful in large applications?

**Answer:**

Normalized state reduces duplication and makes updates easier.

Suppose the same user appears in:

```text
posts
comments
messages
notifications
```

If the user object is copied everywhere, updating the name requires changing many locations.

With normalized state:

```js
users[10].name = "Mike";
```

all features can reference the same user entity.

Benefits include:

- Single source of truth
- Easier updates
- Reduced duplication
- Faster entity lookup
- Cleaner state relationships

**Interview Line**

Normalized state improves large applications by keeping each entity in one place and simplifying updates across related features.

### Q. What is state colocation?

**Answer:**

State colocation means keeping state as close as possible to the components that actually use it.

**Example:**

If only `SearchBox` needs the search text:

```jsx
function SearchBox() {
  const [query, setQuery] = useState("");
}
```

there is no reason to move `query` into:

```text
App
Context
Redux
```

unless other components need it.

State should move upward only when multiple components need to share it.

**Interview Line**

State colocation means keeping state near the components that use it instead of making it global unnecessarily.

### Q. Why should state be kept close to where it is used?

**Answer:**

Keeping state close to its consumers reduces unnecessary complexity and re-renders.

Benefits include:

- Easier reasoning
- Smaller dependency scope
- Less prop drilling
- Fewer global updates
- Easier testing
- Better component isolation

**Example:**

If a dropdown's open state is used only inside the dropdown:

```jsx
const [isOpen, setIsOpen] = useState(false);
```

it should remain inside that component.

Moving it to global state would create unnecessary coupling.

**Interview Line**

State should stay close to where it is used because local ownership reduces coupling, complexity, and unnecessary application-wide updates.

### Q. What is stale state in React?

**Answer:**

Stale state occurs when code uses an old state value from a previous render instead of the latest value.

**Example:**

```jsx
setTimeout(() => {
  console.log(count);
}, 1000);
```

The callback may capture the `count` value from the render in which it was created.

Another common example:

```jsx
setCount(count + 1);
setCount(count + 1);
```

Both calls may use the same old `count`.

If:

```js
count === 0;
```

both may effectively request:

```js
setCount(1);
```

instead of producing `2`.

**Interview Line**

Stale state happens when an update or callback uses a state value captured from an older render.

### Q. How do you avoid stale state updates?

**Answer:**

When the next value depends on the previous value, use the functional updater form.

**Example:**

Instead of:

```jsx
setCount(count + 1);
```

use:

```jsx
setCount((prevCount) => prevCount + 1);
```

For multiple updates:

```jsx
setCount((prev) => prev + 1);

setCount((prev) => prev + 1);
```

If the initial count is `0`, the final result becomes:

```text
2
```

Functional updates avoid depending on a potentially stale closure.

**Interview Line**

Avoid stale state updates by using functional setters whenever the next state depends on the previous state.

### Q. What is functional state update?

**Answer:**

A functional state update passes a function to the state setter instead of passing the new value directly.

**Example:**

```jsx
setCount((previousCount) => previousCount + 1);
```

React provides the latest pending state value to the updater function.

This is safer than:

```jsx
setCount(count + 1);
```

when the new value depends on the previous one.

Functional updates are especially useful with:

- Multiple updates
- Async callbacks
- Timers
- Event handlers with queued updates

**Interview Line**

A functional state update calculates the next state from the latest previous state provided by React.

### Q. When should you use functional updates with `setState`?

**Answer:**

Use functional updates whenever the next state depends on the previous state.

**Example:**

```jsx
setCount((prev) => prev + 1);
```

For object state:

```jsx
setForm((prev) => ({
  ...prev,
  name: "John",
}));
```

This is especially important when:

- Multiple updates happen together
- Updates occur asynchronously
- State is modified from callbacks
- Previous state is required for calculation

If the new value does not depend on previous state:

```jsx
setTheme("dark");
```

a functional update is not necessary.

**Interview Line**

Use functional updates when the next state is calculated from the previous state rather than replacing it with an independent value.

### Q. Why is state update asynchronous in React?

**Answer:**

React state setters schedule updates instead of immediately changing the state variable in the current render.

**Example:**

```jsx
console.log(count);

setCount(count + 1);

console.log(count);
```

Both logs may show the same value.

Why?

Because `count` belongs to the current render snapshot.

Calling:

```jsx
setCount();
```

requests another render with the new value.

This lets React:

- Batch updates
- Avoid unnecessary renders
- Schedule work efficiently
- Maintain consistent render snapshots

It is more accurate to say state updates are **scheduled** rather than simply asynchronous.

**Interview Line**

React state setters schedule a future render instead of mutating the current render's state value immediately.

### Q. Can multiple state updates be merged?

**Answer:**

React can batch multiple state updates so they produce fewer renders.

**Example:**

```jsx
function handleClick() {
  setName("John");
  setAge(25);
  setActive(true);
}
```

React can process these updates together before rendering.

For updates to the same state:

```jsx
setCount(count + 1);
setCount(count + 1);
```

both may use the same render snapshot.

To increment twice correctly:

```jsx
setCount((prev) => prev + 1);

setCount((prev) => prev + 1);
```

React processes the queued updater functions in order.

**Interview Line**

React batches multiple state updates, and functional updaters should be used when several queued updates depend on previous state.

### Q. How do you reset component state?

**Answer:**

State can be reset by assigning its original value again.

**Example:**

```jsx
const initialForm = {
  name: "",
  email: "",
};

const [form, setForm] = useState(initialForm);
```

Reset:

```jsx
setForm(initialForm);
```

Another React technique is changing a component's `key`.

**Example:**

```jsx
<UserForm key={userId} />
```

When `userId` changes, React treats it as a different component instance and resets its local state.

**Interview Line**

Reset state by restoring its initial value, or use a different `key` when you intentionally want React to recreate the component state.

### Q. How do you preserve state between renders?

**Answer:**

React preserves state automatically as long as the same component remains in the same position in the rendered tree.

**Example:**

```jsx
function Counter() {
  const [count, setCount] = useState(0);

  return <button onClick={() => setCount((prev) => prev + 1)}>{count}</button>;
}
```

When `Counter` re-renders, React keeps the existing state.

State may reset when:

- The component is unmounted
- Its `key` changes
- A different component type appears in that position

For mutable values that should persist without re-rendering, `useRef` can be used.

**Interview Line**

React preserves component state across renders when the same component identity remains at the same position in the tree.

### Q. How do you share state between unrelated components?

**Answer:**

If components do not have a convenient parent-child relationship, shared state can be moved to a common external source.

Common options include:

- React Context
- Redux
- Zustand
- External stores
- Server-state libraries for remote data

**Example with Context:**

```jsx
const ThemeContext = createContext(null);
```

Then components anywhere under the provider can consume the shared value.

The right solution depends on what kind of state is being shared.

For example:

```text
Theme -> Context
Large application workflow state -> Redux/Zustand
API cache -> React Query
```

**Interview Line**

Unrelated components can share state through Context, an external state manager, or a server-state library depending on the type of data.

### Q. How do you decide between local state, Context, Redux, and React Query?

**Answer:**

The correct tool depends on what kind of state you are managing.

### Local State

Use for state owned by one component or a small subtree.

Examples:

```text
modal open
input value
selected tab
```

### Context

Use for relatively stable values needed across many components.

Examples:

```text
theme
current locale
authentication context
```

### Redux

Use when complex client-side application state needs:

- Predictable updates
- Centralized logic
- DevTools
- Middleware
- Cross-feature coordination

### React Query

Use for server state.

Examples:

```text
users
products
orders
API caching
refetching
mutations
```

A common architecture can use all of them together.

**Interview Line**

Use local state for local UI, Context for shared app-level values, Redux for complex client state, and React Query for remote server state.

### Q. What type of data should not be stored in Redux?

**Answer:**

Redux should not become a storage location for every value in the application.

Usually avoid storing:

- Temporary local UI state used by one component
- Derived values that can be calculated
- Duplicated data
- DOM elements
- Functions
- Promises
- Class instances
- Non-serializable values without a strong reason
- Server cache that is better handled by a dedicated query library

**Example:**

A modal used only inside one component should usually remain:

```jsx
const [isOpen, setIsOpen] = useState(false);
```

instead of being added to Redux.

Similarly, API data with caching and refetch requirements is often better managed by tools such as React Query or RTK Query.

**Interview Line**

Do not put purely local UI state, duplicated or derived values, or unnecessary non-serializable data into Redux; keep state in the smallest appropriate layer.

## Context API

### Q. How does Context API work internally?

**Answer:**

Context lets a value be available to descendant components without manually passing it through every intermediate component.

A Context setup usually has three parts:

1. Create the context.
2. Provide a value.
3. Read the value from descendant components.

**Example:**

```jsx
const ThemeContext = createContext("light");

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Page />
    </ThemeContext.Provider>
  );
}
```

A child can read it with:

```jsx
const theme = useContext(ThemeContext);
```

React resolves the nearest matching provider above the consumer in the tree.

When the provider value changes, consumers that read that context are scheduled to update.

**Interview Line**

Context works by letting consumers read the nearest provider value, and React updates those consumers when that value changes.

### Q. Why can Context cause unnecessary re-renders?

**Answer:**

A Context consumer re-renders when the provider value changes.

A common problem is passing a new object reference on every provider render.

**Example:**

```jsx
<AuthContext.Provider
  value={{
    user,
    login,
    logout,
  }}
>
  {children}
</AuthContext.Provider>
```

The object is recreated on every render.

So even if `user` did not change, the provider still receives a new `value` reference.

Another issue is putting too many unrelated values into one large context.

If only one field changes, all consumers of that context may be affected.

**Interview Line**

Context can cause unnecessary re-renders when provider values change reference frequently or unrelated state is grouped into one large context.

### Q. How do you optimize Context API performance?

**Answer:**

Common optimization strategies include:

1. Split large contexts into smaller focused contexts.
2. Keep state close to where it is used.
3. Memoize provider values when it helps.
4. Separate state from dispatch functions.
5. Avoid storing frequently changing high-volume data in one global context.

**Example:**

```jsx
const value = useMemo(() => {
  return {
    user,
    logout,
  };
}, [user, logout]);
```

Then:

```jsx
<AuthContext.Provider value={value}>{children}</AuthContext.Provider>
```

The most important optimization is usually better state structure, not adding memoization everywhere.

**Interview Line**

Optimize Context by keeping contexts focused, stabilizing provider values where useful, and avoiding one large frequently changing global context.

### Q. How do you split context for better performance?

**Answer:**

Instead of putting unrelated values into one context, create separate contexts based on responsibility.

**Bad Example:**

```jsx
<AppContext.Provider
  value={{
    theme,
    user,
    cart,
    notifications,
  }}
>
```

A better structure is:

```jsx
<ThemeProvider>
  <AuthProvider>
    <CartProvider>
      <App />
    </CartProvider>
  </AuthProvider>
</ThemeProvider>
```

Now a component that only consumes theme does not need to subscribe to cart state.

You can also split by update frequency, for example:

```text
AuthStateContext
AuthDispatchContext
```

**Interview Line**

Split Context by responsibility or update frequency so components subscribe only to the data they actually need.

### Q. What is the difference between state context and dispatch context?

**Answer:**

A state context exposes current state.

A dispatch context exposes the function used to update that state.

**Example:**

```jsx
const TodoStateContext = createContext(null);
const TodoDispatchContext = createContext(null);
```

Provider:

```jsx
function TodoProvider({ children }) {
  const [state, dispatch] = useReducer(todoReducer, initialState);

  return (
    <TodoStateContext.Provider value={state}>
      <TodoDispatchContext.Provider value={dispatch}>{children}</TodoDispatchContext.Provider>
    </TodoStateContext.Provider>
  );
}
```

A component that only dispatches actions can subscribe only to `TodoDispatchContext`.

Since `dispatch` is stable, that component does not need to re-render for every state update.

**Interview Line**

State context exposes changing data, while dispatch context exposes update actions and can reduce re-renders for components that only trigger updates.

### Q. How do you combine `useReducer` with Context API?

**Answer:**

`useReducer` handles predictable state transitions, while Context makes the reducer state and dispatch function available to descendants.

**Example:**

```jsx
const CounterContext = createContext(null);

function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return {
        count: state.count + 1,
      };

    case "decrement":
      return {
        count: state.count - 1,
      };

    default:
      return state;
  }
}
```

Provider:

```jsx
function CounterProvider({ children }) {
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <CounterContext.Provider
      value={{
        state,
        dispatch,
      }}
    >
      {children}
    </CounterContext.Provider>
  );
}
```

Consumer:

```jsx
const { state, dispatch } = useContext(CounterContext);
```

This pattern works well for medium-complexity shared client state.

**Interview Line**

`useReducer` handles state transitions, while Context distributes the reducer state and dispatch function to the components that need them.

### Q. When should you not use Context API?

**Answer:**

Context is not always the best solution.

Avoid it when:

- State is only needed by one component.
- Data changes extremely frequently.
- You need fine-grained subscriptions.
- The state has complex cross-feature logic.
- Server-state caching and synchronization are required.
- You need advanced middleware or DevTools.

For example, a local modal state should usually stay local:

```jsx
const [isOpen, setIsOpen] = useState(false);
```

Server data such as caching, retries, refetching, and pagination is often better handled by React Query.

**Interview Line**

Do not use Context for simple local state, complex server state, or highly dynamic global state that needs fine-grained subscriptions.

### Q. Can Context replace all state management libraries?

**Answer:**

No.

Context mainly solves this problem:

```text
Make a value available to distant descendants
```

It does not automatically provide:

- Server-state caching
- Request deduplication
- Middleware
- Fine-grained selectors
- Persistence
- Time-travel debugging
- Complex async workflows

Context may be enough for:

```text
theme
locale
current user
feature flags
```

For complex client state, tools such as Redux or Zustand may be more suitable.

For remote server state, React Query or RTK Query is often a better fit.

**Interview Line**

Context is a dependency-sharing mechanism, not a full replacement for dedicated client-state or server-state management libraries.

### Q. How do you provide multiple contexts?

**Answer:**

Multiple providers can be nested around the part of the application that needs them.

**Example:**

```jsx
function App() {
  return (
    <ThemeProvider>
      <AuthProvider>
        <CartProvider>
          <Router />
        </CartProvider>
      </AuthProvider>
    </ThemeProvider>
  );
}
```

A component can consume multiple contexts:

```jsx
const theme = useContext(ThemeContext);
const user = useContext(AuthContext);
```

This is usually cleaner than combining unrelated state into one giant context.

**Interview Line**

Multiple contexts are provided by nesting focused providers and consuming only the contexts each component actually needs.

### Q. How do you avoid deeply nested context providers?

**Answer:**

Deep provider nesting can make the root component difficult to read.

**Example:**

```jsx
<AuthProvider>
  <ThemeProvider>
    <CartProvider>
      <ToastProvider>
        <SettingsProvider>
          <App />
        </SettingsProvider>
      </ToastProvider>
    </CartProvider>
  </ThemeProvider>
</AuthProvider>
```

A common solution is a provider composition component.

**Example:**

```jsx
function AppProviders({ children }) {
  return (
    <AuthProvider>
      <ThemeProvider>
        <CartProvider>
          <ToastProvider>{children}</ToastProvider>
        </CartProvider>
      </ThemeProvider>
    </AuthProvider>
  );
}
```

Then:

```jsx
<AppProviders>
  <App />
</AppProviders>
```

Feature-specific providers can also be moved closer to the feature that needs them.

**Interview Line**

Avoid deeply nested providers by composing them into a shared provider component and colocating feature-specific providers lower in the tree.

### Q. What is provider composition?

**Answer:**

Provider composition is the practice of combining multiple Context providers into one reusable wrapper.

**Example:**

```jsx
function AppProviders({ children }) {
  return (
    <ThemeProvider>
      <AuthProvider>
        <QueryProvider>{children}</QueryProvider>
      </AuthProvider>
    </ThemeProvider>
  );
}
```

Usage:

```jsx
<AppProviders>
  <App />
</AppProviders>
```

This improves:

- Root component readability
- Provider organization
- Reusability
- Test setup

It does not remove the actual nesting internally; it simply organizes it in one place.

**Interview Line**

Provider composition groups multiple Context providers into one reusable wrapper to keep application setup cleaner.

### Q. How do you test components that use Context?

**Answer:**

A component that depends on Context should be rendered with the required provider in the test.

**Example:**

```jsx
function UserName() {
  const user = useContext(AuthContext);

  return <p>{user.name}</p>;
}
```

Test:

```jsx
render(
  <AuthContext.Provider
    value={{
      name: "John",
    }}
  >
    <UserName />
  </AuthContext.Provider>,
);
```

Then assert the visible behavior:

```js
expect(screen.getByText("John")).toBeInTheDocument();
```

For many tests, create a reusable helper:

```jsx
function renderWithProviders(ui) {
  return render(<AppProviders>{ui}</AppProviders>);
}
```

Tests should focus on observable behavior rather than Context implementation details.

**Interview Line**

Test Context consumers by wrapping them with the required provider values and asserting their observable behavior.

## Redux & Redux Toolkit

### Q. What is `createSlice` in Redux Toolkit?

**Answer:**

`createSlice` is a Redux Toolkit utility that creates a slice of Redux state along with its reducers and action creators.

A slice usually represents one feature of the application.

**Example:**

```js
import { createSlice } from "@reduxjs/toolkit";

const counterSlice = createSlice({
  name: "counter",

  initialState: {
    value: 0,
  },

  reducers: {
    increment(state) {
      state.value++;
    },

    decrement(state) {
      state.value--;
    },
  },
});
```

Redux Toolkit automatically creates action creators:

```js
counterSlice.actions.increment();
counterSlice.actions.decrement();
```

And the reducer is available as:

```js
counterSlice.reducer;
```

`createSlice` reduces boilerplate because you no longer need to manually write:

- Action type constants
- Action creators
- Switch statements

**Interview Line**

`createSlice` creates a feature reducer and automatically generates matching Redux action creators from reducer definitions.

### Q. What is `configureStore` in Redux Toolkit?

**Answer:**

`configureStore` is the recommended way to create a Redux store with Redux Toolkit.

It automatically configures several useful defaults.

**Example:**

```js
import { configureStore } from "@reduxjs/toolkit";

import counterReducer from "./counterSlice";

export const store = configureStore({
  reducer: {
    counter: counterReducer,
  },
});
```

It automatically provides:

- Redux DevTools support
- Thunk middleware
- Development checks
- Better default configuration

Without Redux Toolkit, developers traditionally had to configure much of this manually.

**Interview Line**

`configureStore` creates a Redux store with sensible defaults such as thunk middleware, DevTools support, and development checks.

### Q. What is Immer in Redux Toolkit?

**Answer:**

Immer is a library used internally by Redux Toolkit to simplify immutable state updates.

Redux requires state updates to be immutable.

Traditionally:

```js
return {
  ...state,
  user: {
    ...state.user,
    name: "John",
  },
};
```

With Immer, Redux Toolkit allows code that looks mutable:

```js
state.user.name = "John";
```

Immer tracks those changes and creates a new immutable state object internally.

The original state is not actually mutated.

**Interview Line**

Immer lets Redux Toolkit reducers use mutation-like syntax while internally producing safe immutable state updates.

### Q. How does Redux Toolkit allow writing mutable-looking code?

**Answer:**

Redux Toolkit uses Immer inside `createSlice` and `createReducer`.

When you write:

```js
state.count++;
```

Immer gives the reducer a proxy-based draft state.

Changes are recorded against that draft.

After the reducer finishes, Immer produces a new immutable state based on those changes.

**Example:**

```js
reducers: {
  addTodo(
    state,
    action
  ) {
    state.todos.push(
      action.payload
    );
  },
}
```

This looks like direct mutation, but the actual Redux state remains immutable.

This only works inside Immer-enabled reducers.

You should not directly mutate Redux state outside reducers.

**Interview Line**

Redux Toolkit uses Immer drafts so reducer code can look mutable while the final Redux state is still updated immutably.

### Q. What is `createAsyncThunk`?

**Answer:**

`createAsyncThunk` is a Redux Toolkit utility for handling asynchronous logic such as API requests.

It automatically creates three lifecycle actions:

```text
pending
fulfilled
rejected
```

**Example:**

```js
import { createAsyncThunk } from "@reduxjs/toolkit";

export const fetchUsers = createAsyncThunk("users/fetchUsers", async () => {
  const response = await fetch("/api/users");

  if (!response.ok) {
    throw new Error("Request failed");
  }

  return response.json();
});
```

Redux Toolkit automatically creates actions such as:

```text
users/fetchUsers/pending
users/fetchUsers/fulfilled
users/fetchUsers/rejected
```

These can be handled in `extraReducers`.

**Interview Line**

`createAsyncThunk` standardizes async Redux logic by generating pending, fulfilled, and rejected actions around a Promise-based operation.

### Q. How do you handle loading, success, and error states in Redux Toolkit?

**Answer:**

For async requests created with `createAsyncThunk`, loading, success, and error states are usually handled through lifecycle actions.

**Example:**

```js
const usersSlice = createSlice({
  name: "users",

  initialState: {
    data: [],
    loading: false,
    error: null,
  },

  reducers: {},

  extraReducers: (builder) => {
    builder
      .addCase(fetchUsers.pending, (state) => {
        state.loading = true;

        state.error = null;
      })

      .addCase(fetchUsers.fulfilled, (state, action) => {
        state.loading = false;

        state.data = action.payload;
      })

      .addCase(fetchUsers.rejected, (state, action) => {
        state.loading = false;

        state.error = action.error.message;
      });
  },
});
```

The UI can then select:

```text
loading
data
error
```

from Redux state.

**Interview Line**

Async Redux state is commonly modeled with loading, data, and error fields updated by `pending`, `fulfilled`, and `rejected` actions.

### Q. What is extraReducers in Redux Toolkit?

**Answer:**

`extraReducers` allows a slice to respond to actions that were not defined inside its own `reducers` field.

This is especially useful for:

- `createAsyncThunk`
- Actions from other slices
- Global reset actions
- Cross-feature coordination

**Example:**

```js
extraReducers: (builder) => {
  builder.addCase(fetchUsers.fulfilled, (state, action) => {
    state.data = action.payload;
  });
};
```

Unlike `reducers`, `extraReducers` does not generate action creators.

It only handles existing actions.

**Interview Line**

`extraReducers` lets a slice respond to external actions such as async thunk lifecycle actions without creating new action creators.

### Q. What is Redux selector?

**Answer:**

A selector is a function that reads or derives data from Redux state.

**Example:**

```js
const selectUsers = (state) => state.users.data;
```

Usage:

```js
const users = useSelector(selectUsers);
```

Selectors can also derive values:

```js
const selectActiveUsers = (state) => state.users.data.filter((user) => user.active);
```

Selectors help separate state structure from UI components.

**Interview Line**

A Redux selector is a function that reads or derives specific data from the Redux store.

### Q. Why should selectors be used?

**Answer:**

Selectors improve maintainability by hiding the internal shape of Redux state from components.

Instead of:

```js
useSelector((state) => state.users.data);
```

you can define:

```js
const selectUsers = (state) => state.users.data;
```

Then components use:

```js
useSelector(selectUsers);
```

Benefits include:

- Reusability
- Centralized state access
- Easier refactoring
- Derived data logic
- Better testing
- Memoization opportunities

If the Redux state structure changes later, selectors can be updated without changing every component.

**Interview Line**

Selectors centralize state access and derived logic so components are less coupled to the exact Redux store structure.

### Q. What is memoized selector?

**Answer:**

A memoized selector caches its previous result and avoids recalculating when its inputs have not changed.

**Example:**

Suppose this filtering is expensive:

```js
const activeUsers = state.users.data.filter((user) => user.active);
```

A memoized selector can return the previously calculated result if the relevant input reference is unchanged.

This is useful for:

- Expensive derived data
- Stable object references
- Avoiding unnecessary component re-renders

Memoized selectors are commonly created with Reselect.

**Interview Line**

A memoized selector caches derived Redux data and recomputes it only when its input values change.

### Q. What is Reselect?

**Answer:**

Reselect is a selector library commonly used with Redux for memoized derived data.

Redux Toolkit exports `createSelector`, which comes from Reselect.

**Example:**

```js
import { createSelector } from "@reduxjs/toolkit";

const selectUsers = (state) => state.users.data;

const selectActiveUsers = createSelector([selectUsers], (users) => users.filter((user) => user.active));
```

If `users` has the same reference, the filtering function does not need to run again.

It also preserves the previous result reference.

**Interview Line**

Reselect provides memoized selectors that efficiently compute derived Redux state only when their inputs change.

### Q. How do you avoid unnecessary re-renders with Redux?

**Answer:**

Common strategies include:

1. Select only the data a component needs.
2. Avoid returning new objects from selectors unnecessarily.
3. Use memoized selectors for derived data.
4. Normalize state where appropriate.
5. Use `shallowEqual` when selecting grouped values.
6. Split large components.
7. Avoid updating unrelated state.

**Bad Example:**

```js
const data = useSelector((state) => ({
  user: state.user,
  theme: state.theme,
}));
```

A new object is returned every time the selector runs.

Better:

```js
const user = useSelector((state) => state.user);

const theme = useSelector((state) => state.theme);
```

Or use a memoized selector or `shallowEqual` where appropriate.

**Interview Line**

Avoid Redux re-renders by selecting narrowly, preserving references, and memoizing derived data instead of returning new objects unnecessarily.

### Q. What is `useSelector`?

**Answer:**

`useSelector` is a React Redux hook that reads data from the Redux store.

**Example:**

```jsx
import { useSelector } from "react-redux";

function Counter() {
  const count = useSelector((state) => state.counter.value);

  return <p>{count}</p>;
}
```

When the selected value changes, React Redux re-renders the component.

`useSelector` also subscribes the component to the Redux store.

**Interview Line**

`useSelector` subscribes a React component to Redux and returns the selected portion of store state.

### Q. What is `useDispatch`?

**Answer:**

`useDispatch` returns the Redux store's `dispatch` function.

Components use it to send actions to Redux.

**Example:**

```jsx
import { useDispatch } from "react-redux";

import { increment } from "./counterSlice";

function CounterButton() {
  const dispatch = useDispatch();

  return <button onClick={() => dispatch(increment())}>Increment</button>;
}
```

For async thunks:

```js
dispatch(fetchUsers());
```

**Interview Line**

`useDispatch` gives React components access to Redux's dispatch function so they can send actions or async thunks.

### Q. How does `useSelector` compare values?

**Answer:**

By default, `useSelector` uses strict reference equality:

```js
previous === next;
```

If the selected result is a primitive:

```js
10 === 10;
```

React Redux sees no change.

But if the selector returns a new object:

```js
{ count: 1 } !==
{ count: 1 }
```

because the references are different.

That can cause re-renders even when the contents are logically equal.

This is why selectors should avoid creating new object or array references unnecessarily.

**Interview Line**

`useSelector` uses strict `===` reference equality by default to determine whether the selected result changed.

### Q. What is shallow equality in Redux?

**Answer:**

Shallow equality compares the top-level properties of two objects rather than only comparing the object references.

React Redux provides:

```js
shallowEqual;
```

**Example:**

```jsx
import { shallowEqual, useSelector } from "react-redux";

const data = useSelector(
  (state) => ({
    name: state.user.name,
    age: state.user.age,
  }),
  shallowEqual,
);
```

If `name` and `age` remain the same, the component can avoid re-rendering even though the selector returns a new object.

Shallow equality does not deeply compare nested objects.

**Interview Line**

Shallow equality compares top-level property values and can prevent re-renders when a selector returns a new object with unchanged top-level values.

### Q. How do you structure Redux slices in a large app?

**Answer:**

Large applications should usually organize Redux by feature rather than by Redux concept.

**Example:**

```text
features/
  auth/
    authSlice.js
    authSelectors.js

  cart/
    cartSlice.js
    cartSelectors.js

  products/
    productsSlice.js
    productsSelectors.js
```

Each feature can contain:

- Slice
- Selectors
- Async thunks
- Types
- Tests
- Related API logic

Avoid creating one giant global slice.

Each slice should represent a coherent domain or feature.

**Interview Line**

Large Redux applications are best organized by feature, with each slice owning related state, reducers, selectors, and async logic.

### Q. What is RTK Query?

**Answer:**

RTK Query is Redux Toolkit's built-in data-fetching and server-state management solution.

It handles common API concerns such as:

- Fetching
- Caching
- Request deduplication
- Loading state
- Error state
- Refetching
- Cache invalidation

**Example:**

```js
import { createApi, fetchBaseQuery } from "@reduxjs/toolkit/query/react";

export const usersApi = createApi({
  reducerPath: "usersApi",

  baseQuery: fetchBaseQuery({
    baseUrl: "/api",
  }),

  endpoints: (builder) => ({
    getUsers: builder.query({
      query: () => "/users",
    }),
  }),
});
```

Generated hook:

```jsx
const { data, isLoading, error } = useGetUsersQuery();
```

**Interview Line**

RTK Query is Redux Toolkit's server-state solution for fetching, caching, deduplicating, and synchronizing API data.

### Q. How is RTK Query different from Redux Thunk?

**Answer:**

Redux Thunk is a general middleware for writing async Redux logic.

RTK Query is a specialized server-state and data-fetching solution.

With Redux Thunk, you usually manage manually:

- Loading state
- Error state
- API calls
- Caching
- Deduplication
- Refetching
- Invalidation

With RTK Query, most of these are built in.

**Example with thunk:**

```text
dispatch pending
↓
fetch
↓
dispatch success/error
↓
manually cache
```

With RTK Query:

```jsx
useGetUsersQuery();
```

handles most of that automatically.

**Interview Line**

Redux Thunk is a general async middleware, while RTK Query is a higher-level server-state system with built-in caching, deduplication, and invalidation.

### Q. When should you use RTK Query?

**Answer:**

Use RTK Query when the application already uses Redux Toolkit and needs structured server-state management.

It is useful for:

- REST APIs
- Cached API data
- Mutations
- Refetching
- Request deduplication
- Pagination
- Cache invalidation
- Loading/error state

Example use cases:

```text
users
products
orders
comments
dashboard data
```

If your application already uses Redux Toolkit, RTK Query integrates naturally with the same store.

**Interview Line**

Use RTK Query when a Redux Toolkit application needs reliable API fetching, caching, mutation handling, and server-state synchronization.

### Q. How does RTK Query handle caching?

**Answer:**

RTK Query caches data based on the endpoint and serialized query arguments.

For example:

```jsx
useGetUserQuery(10);
```

and:

```jsx
useGetUserQuery(10);
```

refer to the same cached query.

RTK Query tracks:

- Query arguments
- Cached data
- Active subscribers
- Fetch status
- Cache lifetime

If multiple components request the same data, RTK Query can reuse the same cached result instead of sending duplicate requests.

Cached data can remain for a configured period after the final subscriber unsubscribes.

**Interview Line**

RTK Query caches responses by endpoint plus query arguments and reuses the same cached data across subscribers.

### Q. How do you invalidate cache in RTK Query?

**Answer:**

RTK Query commonly invalidates cached queries through tags.

A query declares which tags it provides.

A mutation declares which tags it invalidates.

**Example:**

```js
getUsers:
  builder.query({
    query: () =>
      "/users",

    providesTags:
      ["Users"],
  }),
```

Mutation:

```js
addUser:
  builder.mutation({
    query: (user) => ({
      url: "/users",
      method: "POST",
      body: user,
    }),

    invalidatesTags:
      ["Users"],
  }),
```

After `addUser` succeeds, RTK Query marks the `Users` cache as invalid and can refetch active queries that provide that tag.

**Interview Line**

RTK Query invalidates cached data by connecting mutation `invalidatesTags` with query `providesTags`.

### Q. What are tags in RTK Query?

**Answer:**

Tags are labels used by RTK Query to connect cached queries with mutations that may make that data stale.

**Example:**

```js
providesTags: ["Users"];
```

means:

```text
This query provides Users data
```

A mutation can declare:

```js
invalidatesTags: ["Users"];
```

meaning:

```text
This mutation may make Users data stale
```

Tags can also be more specific.

**Example:**

```js
providesTags: (result, error, id) => [
  {
    type: "User",
    id,
  },
];
```

This allows invalidating one user instead of every user query.

**Interview Line**

RTK Query tags label cached data so mutations can invalidate specific queries and trigger targeted refetching.

## React Query / TanStack Query

### Q. What is React Query?

**Answer:**

React Query, now known as **TanStack Query**, is a library for managing asynchronous server state in React applications.

It helps handle tasks such as:

- Fetching API data
- Caching responses
- Refetching
- Loading and error states
- Request deduplication
- Pagination
- Infinite scrolling
- Mutations
- Cache invalidation

**Example:**

```jsx
const { data, isLoading, error } = useQuery({
  queryKey: ["users"],
  queryFn: fetchUsers,
});
```

Instead of manually managing:

```jsx
useState();
useEffect();
loading;
error;
cache;
```

React Query handles much of that lifecycle automatically.

**Interview Line**

React Query is a server-state management library that simplifies fetching, caching, synchronization, and mutation of remote data.

### Q. Why is React Query used?

**Answer:**

React Query is used because server data has different concerns from normal local UI state.

Server state often needs:

- Fetching
- Caching
- Refetching
- Stale-data handling
- Synchronization
- Error handling
- Request deduplication
- Background updates

Without React Query, developers often write repeated logic with:

```jsx
useEffect();
useState();
fetch();
```

for every API request.

React Query centralizes these patterns and provides a consistent data-fetching model.

**Interview Line**

React Query is used to reduce repeated API-state boilerplate and provide built-in caching, refetching, and synchronization for server data.

### Q. What problem does React Query solve?

**Answer:**

React Query solves the problem of managing **server state** on the client.

A normal API request is not just:

```text
fetch data
```

It also involves:

```text
loading
error
cache
stale state
refetch
deduplication
retry
mutation
synchronization
```

React Query manages these concerns around remote data.

For example, if two components request:

```js
["users"];
```

React Query can reuse the cached result instead of every component independently implementing API logic.

**Interview Line**

React Query solves server-state synchronization by managing fetching, caching, retries, refetching, and mutations around remote data.

### Q. What is server state?

**Answer:**

Server state is data that originates from an external server and is not fully owned by the frontend application.

Examples include:

- Users
- Products
- Orders
- Blog posts
- Notifications
- Account details

Server state can change without the current browser changing it.

For example, another user or backend process may update the same data.

Because of this, server state has concepts such as:

- Freshness
- Staleness
- Refetching
- Cache invalidation

**Interview Line**

Server state is remote data owned outside the frontend and must be fetched, cached, synchronized, and refreshed over time.

### Q. How is server state different from client state?

**Answer:**

Client state is owned by the frontend application.

Examples:

```text
modal open
selected tab
theme
form input
```

Server state comes from a backend.

Examples:

```text
products
users
orders
posts
```

Comparison:

| Client State             | Server State               |
| ------------------------ | -------------------------- |
| Owned locally            | Owned remotely             |
| Usually synchronous      | Requires async fetching    |
| No staleness concept     | Can become stale           |
| Often `useState`/Context | Often React Query          |
| No refetching needed     | Refetching may be required |

**Interview Line**

Client state controls local UI behavior, while server state represents remote data that needs fetching, caching, and synchronization.

### Q. What is `useQuery`?

**Answer:**

`useQuery` is the main React Query hook for fetching and reading server data.

**Example:**

```jsx
const { data, isLoading, isError, error } = useQuery({
  queryKey: ["users"],
  queryFn: fetchUsers,
});
```

`useQuery` manages:

- Request execution
- Loading state
- Error state
- Cached data
- Refetching
- Stale-state behavior

The `queryKey` identifies the cached query.

The `queryFn` defines how the data is fetched.

**Interview Line**

`useQuery` fetches and subscribes a component to cached server data identified by a query key.

### Q. What is `useMutation`?

**Answer:**

`useMutation` is used for operations that change server data.

Common examples include:

- POST
- PUT
- PATCH
- DELETE

**Example:**

```jsx
const mutation = useMutation({
  mutationFn: createUser,
});
```

Usage:

```jsx
mutation.mutate({
  name: "John",
});
```

It provides states such as:

```text
isPending
isError
isSuccess
```

Unlike queries, mutations are usually triggered manually.

**Interview Line**

`useMutation` handles server-changing operations and provides mutation lifecycle states such as pending, success, and error.

### Q. What is query key?

**Answer:**

A query key uniquely identifies cached data in React Query.

**Example:**

```js
queryKey: ["users"];
```

For a specific user:

```js
queryKey: ["users", userId];
```

React Query uses the key for:

- Cache lookup
- Deduplication
- Refetching
- Invalidation
- Sharing data between components

Query keys should describe all values used to fetch the data.

**Interview Line**

A query key uniquely identifies a cached query and should include every parameter that affects the fetched result.

### Q. Why should query keys be stable?

**Answer:**

Stable query keys ensure that logically identical requests map to the same cache entry.

**Example:**

Good:

```js
["users", userId];
```

If `userId` stays the same, React Query recognizes the same query.

Keys should be serializable and deterministic.

If relevant parameters are missing:

```js
queryKey: ["users"];
```

while fetching different users by ID, unrelated responses may incorrectly share the same cache entry.

**Interview Line**

Query keys must be stable and complete so React Query can correctly identify, cache, deduplicate, and invalidate data.

### Q. What is stale time in React Query?

**Answer:**

`staleTime` defines how long cached data is considered fresh.

**Example:**

```jsx
useQuery({
  queryKey: ["users"],
  queryFn: fetchUsers,
  staleTime: 5 * 60 * 1000,
});
```

This means the data remains fresh for:

```text
5 minutes
```

While data is fresh, React Query generally does not need to refetch merely because another component mounts.

After `staleTime` expires, the data becomes stale.

Stale does not mean deleted.

It means React Query is allowed to refetch it based on configured triggers.

**Interview Line**

`staleTime` controls how long cached data is considered fresh before React Query treats it as eligible for refetching.

### Q. What is cache time / garbage collection time?

**Answer:**

In modern TanStack Query, the option is called:

```js
gcTime;
```

Older versions commonly called it:

```js
cacheTime;
```

It controls how long unused query data remains in memory after there are no active subscribers.

**Example:**

```jsx
useQuery({
  queryKey: ["users"],
  queryFn: fetchUsers,
  gcTime: 10 * 60 * 1000,
});
```

If no component is using the query, the cached data can remain for 10 minutes before being garbage-collected.

Important distinction:

```text
staleTime -> freshness
gcTime -> unused cache lifetime
```

**Interview Line**

`staleTime` controls freshness, while `gcTime` controls how long inactive cached data remains before garbage collection.

### Q. What is refetching in React Query?

**Answer:**

Refetching means executing the query function again to obtain newer server data.

React Query can refetch automatically in situations such as:

- Component remount
- Window focus
- Network reconnect
- Query invalidation
- Polling interval

Depending on configuration, stale queries are often eligible for these automatic refetches.

**Example:**

```jsx
useQuery({
  queryKey: ["users"],
  queryFn: fetchUsers,
  refetchOnWindowFocus: true,
});
```

Refetching updates the existing cache instead of creating unrelated state.

**Interview Line**

Refetching means rerunning the query function to synchronize cached data with the latest server state.

### Q. How do you refetch data manually?

**Answer:**

`useQuery` returns a `refetch` function.

**Example:**

```jsx
const { data, refetch } = useQuery({
  queryKey: ["users"],
  queryFn: fetchUsers,
});
```

Usage:

```jsx
<button onClick={() => refetch()}>Refresh</button>
```

Another approach is using the `QueryClient`.

**Example:**

```js
queryClient.invalidateQueries({
  queryKey: ["users"],
});
```

Invalidation is often preferred after a mutation because it marks related data stale and lets React Query refetch active queries.

**Interview Line**

Manually refetch with the query's `refetch()` function or invalidate matching queries through `QueryClient`.

### Q. How do you disable automatic query execution?

**Answer:**

Use the `enabled` option.

**Example:**

```jsx
const query = useQuery({
  queryKey: ["user", userId],
  queryFn: () => fetchUser(userId),
  enabled: false,
});
```

The query does not automatically run.

It can later be triggered manually:

```js
query.refetch();
```

A common pattern is conditionally enabling a query:

```js
enabled: Boolean(userId);
```

**Interview Line**

Use `enabled: false` to prevent automatic query execution, or derive `enabled` from prerequisites such as an ID.

### Q. How do you handle dependent queries?

**Answer:**

Dependent queries should run only after the data required by the next query is available.

**Example:**

First query:

```jsx
const { data: user } = useQuery({
  queryKey: ["user", email],
  queryFn: () => fetchUser(email),
});
```

Second query:

```jsx
const userId = user?.id;

const projectsQuery = useQuery({
  queryKey: ["projects", userId],
  queryFn: () => fetchProjects(userId),
  enabled: Boolean(userId),
});
```

The second query remains disabled until `userId` exists.

**Interview Line**

Dependent queries use `enabled` so a query runs only after the data required by it becomes available.

### Q. How do you handle pagination with React Query?

**Answer:**

Pagination usually includes the current page or cursor in the query key.

**Example:**

```jsx
const [page, setPage] = useState(1);

const query = useQuery({
  queryKey: ["users", page],
  queryFn: () => fetchUsers(page),
});
```

Each page receives its own cache entry.

React Query can also preserve previous data while the next page loads using placeholder strategies.

A typical page-based flow is:

```text
page 1 -> cache
page 2 -> separate cache
page 3 -> separate cache
```

**Interview Line**

Pagination includes the page or cursor in the query key so each result set is cached independently.

### Q. How do you handle infinite scrolling with React Query?

**Answer:**

Infinite scrolling is usually handled with:

```jsx
useInfiniteQuery();
```

**Example:**

```jsx
const { data, fetchNextPage, hasNextPage, isFetchingNextPage } = useInfiniteQuery({
  queryKey: ["users"],

  queryFn: ({ pageParam }) => fetchUsers(pageParam),

  initialPageParam: 1,

  getNextPageParam: (lastPage) => lastPage.nextPage,
});
```

The returned data is stored as pages:

```js
data.pages;
```

When the user reaches the bottom:

```js
fetchNextPage();
```

can load the next batch.

**Interview Line**

Infinite scrolling uses `useInfiniteQuery` to cache multiple pages and load the next page with `fetchNextPage()`.

### Q. How do you update cache after mutation?

**Answer:**

There are two common approaches:

1. Invalidate the related query.
2. Update the cache directly.

**Invalidate Example:**

```jsx
const queryClient = useQueryClient();

const mutation = useMutation({
  mutationFn: createUser,

  onSuccess: () => {
    queryClient.invalidateQueries({
      queryKey: ["users"],
    });
  },
});
```

Direct cache update:

```js
queryClient.setQueryData(["users"], (oldUsers) => [...oldUsers, newUser]);
```

Invalidation is simpler when the server is the source of truth.

Direct updates can provide faster UI updates when the response contains enough data.

**Interview Line**

After a mutation, either invalidate related queries for refetching or update cached data directly with `setQueryData()`.

### Q. What is optimistic update?

**Answer:**

An optimistic update changes the UI immediately before the server confirms the mutation.

The application assumes the request will succeed.

**Example flow:**

```text
User clicks like
↓
UI immediately shows liked
↓
API request sent
↓
Server confirms
```

This improves perceived responsiveness.

React Query supports optimistic updates through mutation lifecycle callbacks.

A common pattern is:

1. Cancel related queries.
2. Store previous cache data.
3. Update cache optimistically.
4. Perform mutation.
5. Roll back if it fails.
6. Invalidate after completion.

**Interview Line**

An optimistic update updates the UI before server confirmation and rolls back if the mutation fails.

### Q. How do you rollback optimistic updates?

**Answer:**

Before changing the cache, save the previous data.

**Example:**

```jsx
const mutation = useMutation({
  mutationFn: updateUser,

  onMutate: async (newUser) => {
    await queryClient.cancelQueries({
      queryKey: ["users"],
    });

    const previousUsers = queryClient.getQueryData(["users"]);

    queryClient.setQueryData(["users"], (old) => old.map((user) => (user.id === newUser.id ? newUser : user)));

    return {
      previousUsers,
    };
  },

  onError: (error, variables, context) => {
    queryClient.setQueryData(["users"], context.previousUsers);
  },

  onSettled: () => {
    queryClient.invalidateQueries({
      queryKey: ["users"],
    });
  },
});
```

The context returned from `onMutate` stores the rollback snapshot.

**Interview Line**

Rollback optimistic updates by saving the previous cache in `onMutate` and restoring it in `onError`.

### Q. React Query vs Redux: when would you use each?

**Answer:**

React Query and Redux solve different primary problems.

#### React Query

Best for server state:

```text
API data
caching
refetching
pagination
mutations
stale data
```

#### Redux

Best for complex client-side application state:

```text
multi-step workflows
global client state
cross-feature coordination
predictable reducers
middleware
```

Comparison:

| React Query         | Redux                 |
| ------------------- | --------------------- |
| Server state        | Client state          |
| Built-in caching    | Manual state modeling |
| Refetching          | Reducer-based updates |
| API synchronization | Global app workflows  |

They can be used together.

A common architecture is:

```text
React Query -> server data
Redux -> complex client state
useState -> local UI state
```

**Interview Line**

Use React Query for remote server state and Redux for complex shared client state; they solve different problems and can coexist.

## Performance Optimization

### Q. How do you optimize performance in React?

**Answer:**

High-level answer (start with this):

“React performance optimization mainly focuses on reducing unnecessary re-renders, optimizing rendering of large components, and loading only what is needed.”

Key techniques (mention 4–5):

- Memoization (React.memo, useMemo, useCallback)
- Code splitting & lazy loading
- Debouncing & throttling
- Virtualization for large lists
- Avoiding unnecessary state updates
- Proper key usage in lists

Interview tip:

Always say “measure first using React DevTools Profiler”.

### Q. What is memoization?

**Answer:**

Memoization is a technique where the result of an expensive computation is cached and reused if inputs don’t change.

Why it helps:
Prevents re-calculating values and re-rendering components unnecessarily.

In React:

- `React.memo` → memoize components
- `useMemo` → memoize values
- `useCallback` → memoize functions

One-liner:

“Memoization avoids repeating expensive calculations by caching results.”

### Q. What is `React.memo`?

**Answer:**

`React.memo` is a higher-order component that prevents re-rendering if props have not changed.

```jsx
const MyComponent = React.memo(Component);
```

How it works:

- Uses shallow comparison of props
- Re-renders only if props change

When to use:

- Functional components
- Pure presentational components
- Components that re-render often with same props

Interview one-liner:

“React.memo prevents unnecessary re-renders by memoizing functional components.”

### Q. How does PureComponent work?

**Answer:**

PureComponent is a class component that implements shouldComponentUpdate with a shallow comparison of props and state.

Effect:

- Prevents re-render if props/state are unchanged

```jsx
class MyComponent extends React.PureComponent {}
```

`React.memo` vs PureComponent:

- PureComponent → class components
- `React.memo` → functional components

One-liner:

“PureComponent avoids re-renders by performing shallow comparison of props and state.”

### Q. What is code splitting in React?

**Answer:**

Code splitting means breaking the JavaScript bundle into smaller chunks that are loaded on demand.

Why it matters:

- Faster initial load
- Less JS sent to browser

How:

- Dynamic `import()`
- `React.lazy`

One-liner:

“Code splitting improves performance by loading only the required code.”

### Q. How does lazy loading improve performance?

**Answer:**

Lazy loading loads components only when they are actually needed.

```jsx
const Dashboard = React.lazy(() => import("./Dashboard"));
```

Benefits:

- Smaller initial bundle
- Faster first paint

Common usage:

- Routes
- Heavy components
- Modals

One-liner:

“Lazy loading improves performance by deferring loading of non-critical components.”

### Q. What is debouncing and throttling?

**Answer:**

Debouncing

- Executes function after user stops triggering
- Example: search input

```jsx
debounce(search, 300);
```

Throttling

- Executes function at fixed intervals
- Example: scroll, resize

```jsx
throttle(onScroll, 200);
```

Why important in React:

Prevents excessive state updates and re-renders.

One-liner:

“Debouncing delays execution, throttling limits execution frequency.”

### Q. How do you optimize large lists?

**Answer:**

Techniques:

- List virtualization
- Pagination / infinite scroll
- Memoized list items
- Proper key usage

Never render thousands of DOM nodes at once.

One-liner:

“Large lists are optimized by rendering only visible items and reducing DOM nodes.”

### Q. What is virtualization?

**Answer:**

Virtualization renders only the visible items in a list instead of the entire dataset.

How it works:

- As you scroll, items are added/removed dynamically

Benefits:

- Huge performance improvement
- Less memory usage

Common libraries:

- react-window
- react-virtualized

One-liner:

“Virtualization improves performance by rendering only visible list items.”

### Q. What are common React performance mistakes?

**Answer:**

Mention these (very important):

- Unnecessary state updates
- Inline functions & objects in JSX
- Missing key in lists
- Overusing Context API
- Not memoizing expensive calculations
- Large component trees
- Rendering large lists without virtualization
- Not using code splitting

Strong closing line:

“Most React performance issues come from unnecessary re-renders.”

#### ⭐ Final Interview Cheat Answer (30 seconds)

“React performance is optimized by reducing unnecessary re-renders using memoization, optimizing large lists with virtualization, loading code lazily, and controlling frequent updates using debouncing or throttling. Measuring performance with React Profiler is essential before optimizing.”

### Q. What is React Profiler?

**Answer:**

React Profiler is a tool used to measure how often React components render and how much time those renders take.

It helps identify:

- Expensive components
- Repeated renders
- Slow render paths
- Components affected by parent updates
- Performance bottlenecks

React provides profiling support through React DevTools and the `Profiler` component.

**Example:**

```jsx
import { Profiler } from "react";

function onRender(id, phase, actualDuration) {
  console.log({
    id,
    phase,
    actualDuration,
  });
}

<Profiler id="Dashboard" onRender={onRender}>
  <Dashboard />
</Profiler>;
```

The callback receives information about rendering performance.

**Interview Line**

React Profiler measures component render frequency and render duration so performance bottlenecks can be identified.

### Q. How do you use React DevTools Profiler?

**Answer:**

React DevTools includes a Profiler tab that records component rendering activity.

A common workflow is:

1. Open React DevTools.
2. Select the **Profiler** tab.
3. Start recording.
4. Perform the slow user interaction.
5. Stop recording.
6. Inspect which components rendered.
7. Check render duration and render reasons.

Useful views include:

- Flame graph
- Ranked view
- Component render details

You should profile a real interaction instead of guessing where the problem is.

Examples:

```text
Opening modal
Typing into form
Changing filters
Rendering table
Switching tabs
```

**Interview Line**

Use React DevTools Profiler by recording a real interaction and inspecting which components rendered, how long they took, and why they updated.

### Q. What is wasted render?

**Answer:**

A wasted render is a render that performs work but does not produce a meaningful UI change.

**Example:**

```jsx
function Parent() {
  const [count, setCount] = useState(0);

  return (
    <>
      <button onClick={() => setCount((prev) => prev + 1)}>{count}</button>

      <ExpensiveChild />
    </>
  );
}
```

If `ExpensiveChild` does not depend on `count`, rendering it every time the count changes may be unnecessary.

Not every extra render is a performance problem.

Optimization matters when the render is:

- Frequent
- Expensive
- Affecting user experience

**Interview Line**

A wasted render is a render that performs unnecessary work without producing a meaningful UI change.

### Q. How do you detect wasted renders?

**Answer:**

The best way is profiling.

Useful techniques include:

- React DevTools Profiler
- Render highlighting
- Temporary render logs
- Measuring expensive calculations
- Checking why components rendered

**Example:**

```jsx
function UserCard() {
  console.log("UserCard rendered");

  return <div>User</div>;
}
```

If the component renders frequently even when its meaningful inputs are unchanged, investigate:

- Parent renders
- Context changes
- New object props
- New function props
- Unstable selectors

**Interview Line**

Detect wasted renders with the React Profiler and verify whether components are re-rendering without meaningful input changes.

### Q. What is referential equality?

**Answer:**

Referential equality checks whether two references point to the same object in memory.

For primitives:

```js
10 === 10; // true
```

For objects:

```js
{} === {}; // false
```

Even though both objects look identical, they are different references.

**Example:**

```js
const a = {};
const b = a;

console.log(a === b);
```

Output:

```text
true
```

Referential equality matters in React because optimization tools such as:

- `React.memo`
- `useMemo`
- `useCallback`
- `useSelector`

often depend on stable references.

**Interview Line**

Referential equality checks object identity, and React memoization often depends on whether references remain the same between renders.

### Q. Why do inline objects break memoization?

**Answer:**

An inline object creates a new reference on every render.

**Example:**

```jsx
<Child
  config={{
    theme: "dark",
  }}
/>
```

Even if the content is unchanged:

```js
previousConfig !== nextConfig;
```

because a new object was created.

If `Child` is memoized:

```jsx
const Child = React.memo(function Child({ config }) {
  return <div />;
});
```

the new object reference can cause the memoization check to fail.

**Interview Line**

Inline objects can break memoization because a new object reference is created on every render.

### Q. Why do inline functions break memoization?

**Answer:**

Inline functions also create a new function reference on every render.

**Example:**

```jsx
<Child onClick={() => handleClick(id)} />
```

On every parent render:

```js
previousFunction !== newFunction;
```

If `Child` is memoized, the changed callback reference may cause it to render again.

This only matters when function identity is actually relevant.

Creating inline functions is not automatically a performance problem.

**Interview Line**

Inline functions can break prop-based memoization because each render creates a new function reference.

### Q. How do you stabilize object references?

**Answer:**

Objects can be stabilized with `useMemo` when stable identity provides a real benefit.

**Example:**

```jsx
const config = useMemo(() => {
  return {
    theme,
    size: "large",
  };
}, [theme]);
```

Then:

```jsx
<Child config={config} />
```

Other options include:

- Define static objects outside the component.
- Pass primitive props instead.
- Avoid creating unnecessary wrapper objects.

**Example:**

Instead of:

```jsx
<Child
  config={{
    theme,
  }}
/>
```

you may simply pass:

```jsx
<Child theme={theme} />
```

**Interview Line**

Stabilize object references with `useMemo`, module-level constants, or simpler primitive props when reference identity affects performance.

### Q. How do you stabilize function references?

**Answer:**

`useCallback` can preserve a function reference across renders until its dependencies change.

**Example:**

```jsx
const handleDelete = useCallback(
  (id) => {
    deleteUser(id);
  },
  [deleteUser],
);
```

Then:

```jsx
<MemoizedChild onDelete={handleDelete} />
```

Use `useCallback` when:

- Passing callbacks to memoized children
- Function identity is a dependency
- Profiling shows avoidable renders

Do not wrap every function automatically.

**Interview Line**

Use `useCallback` when a stable function reference prevents meaningful work or is required by another dependency-sensitive API.

### Q. What is bundle analysis?

**Answer:**

Bundle analysis is the process of inspecting the JavaScript and assets included in a production build.

It helps answer questions such as:

- Which dependency is largest?
- Is the same library included twice?
- Which chunks are too large?
- Is unused code being bundled?
- Are route-specific modules split correctly?

A bundle analyzer typically displays bundle contents visually.

**Example:**

```text
main.js
├── react
├── chart-library
├── date-library
└── application code
```

If a chart library occupies most of the bundle, it may be a candidate for lazy loading or replacement.

**Interview Line**

Bundle analysis shows what code is included in production bundles so oversized dependencies and optimization opportunities can be identified.

### Q. How do you analyze React bundle size?

**Answer:**

A typical process is:

1. Create a production build.
2. Use the bundler's analyzer or reporting plugin.
3. Inspect large chunks.
4. Identify heavy dependencies.
5. Check duplicated packages.
6. Verify code splitting.
7. Compare before and after optimization.

Depending on the toolchain, common approaches include:

```text
Webpack Bundle Analyzer
Rollup visualizer
Vite bundle visualization plugins
Framework-specific analyzers
```

Also inspect the browser Network panel to see actual downloaded chunk sizes.

**Interview Line**

Analyze React bundle size by building for production, inspecting bundle composition, and targeting oversized or duplicated dependencies.

### Q. How do you reduce third-party library bundle size?

**Answer:**

Common strategies include:

- Import only required functions
- Prefer tree-shakeable libraries
- Remove unused dependencies
- Lazy load heavy features
- Replace oversized libraries
- Avoid duplicate package versions
- Use native browser APIs when practical

**Example:**

Instead of importing an entire utility library:

```js
import _ from "some-library";
```

prefer a tree-shakeable or direct import when supported:

```js
import debounce from "some-library/debounce";
```

A large chart or editor library can also be dynamically loaded only when needed.

**Interview Line**

Reduce third-party bundle size through selective imports, tree shaking, lazy loading, dependency cleanup, and smaller alternatives.

### Q. What is dynamic import?

**Answer:**

Dynamic import loads a JavaScript module at runtime instead of including it in the initial execution path.

It uses:

```js
import()
```

and returns a Promise.

**Example:**

```js
async function loadEditor() {
  const module = await import("./editor.js");

  module.openEditor();
}
```

Bundlers can use dynamic imports as code-splitting boundaries.

This is useful for:

- Large components
- Optional features
- Route-specific code
- Admin tools

**Interview Line**

Dynamic import uses `import()` to load modules at runtime and commonly creates a code-splitting boundary.

### Q. What is preloading?

**Answer:**

Preloading tells the browser that a resource is important for the current navigation and should be fetched early.

Examples include:

- Critical fonts
- Hero images
- Important scripts

Conceptually:

```html
<link rel="preload" href="/font.woff2" as="font" />
```

Preloading should be used carefully because it gives the resource high priority.

Preloading too many assets can compete with genuinely critical resources.

**Interview Line**

Preloading fetches important resources early for the current page because they are expected to be needed soon.

### Q. What is prefetching?

**Answer:**

Prefetching tells the browser that a resource may be useful for a future navigation or interaction.

It is lower priority than preload.

**Example:**

```html
<link rel="prefetch" href="/next-page.js" />
```

Typical use cases include:

- Likely next route
- Future chunk
- Data expected soon

Prefetching improves future responsiveness without making the resource critical for the current screen.

**Interview Line**

Prefetching downloads likely future resources at low priority so later navigation or interaction can be faster.

### Q. Difference between preload and prefetch

**Answer:**

The main difference is urgency.

| Preload                   | Prefetch                     |
| ------------------------- | ---------------------------- |
| Current navigation        | Future navigation            |
| Higher priority           | Lower priority               |
| Resource needed soon      | Resource may be needed later |
| Critical performance path | Predictive optimization      |

**Example:**

Use preload for:

```text
hero image
critical font
important current-page asset
```

Use prefetch for:

```text
next route chunk
future page data
optional later resource
```

**Interview Line**

Preload is for important current-page resources, while prefetch is for likely future resources.

### Q. What is image lazy loading in React?

**Answer:**

Image lazy loading delays loading images until they are near the viewport.

Native HTML supports:

```jsx
<img src="/photo.jpg" loading="lazy" alt="Photo" />
```

This helps pages with many below-the-fold images by reducing:

- Initial network usage
- Initial page weight
- Competing requests

Images visible immediately above the fold should generally not be lazy loaded if they are important for initial rendering.

**Interview Line**

Image lazy loading delays non-critical image downloads until they are near the viewport, reducing initial page load work.

### Q. How do you optimize images in React apps?

**Answer:**

Useful techniques include:

- Use correct dimensions
- Serve responsive images
- Compress images
- Prefer modern formats where suitable
- Lazy load below-the-fold images
- Preload important hero images
- Avoid shipping images much larger than rendered size
- Use CDN image optimization when available

**Example:**

```jsx
<img src="/photo.webp" width="600" height="400" loading="lazy" alt="Product" />
```

Providing dimensions also reduces layout shift.

Frameworks such as Next.js can automate several image optimizations.

**Interview Line**

Optimize images through correct sizing, compression, responsive variants, modern formats, lazy loading, and explicit dimensions.

### Q. How do you optimize expensive child components?

**Answer:**

First verify that the child is actually expensive through profiling.

Common optimizations include:

- `React.memo`
- Stable props
- `useMemo` for expensive calculations
- `useCallback` for callback identity
- Move unrelated state away from the parent
- Split large components
- Virtualize large lists

**Example:**

```jsx
const ExpensiveChart = React.memo(function ExpensiveChart({ data }) {
  return <Chart data={data} />;
});
```

Memoization helps only when props remain stable often enough to avoid useful work.

**Interview Line**

Optimize expensive children by profiling first, then reducing re-renders with stable props, memoization, and better component boundaries.

### Q. How do you optimize context-heavy components?

**Answer:**

Context-heavy applications can cause broad re-rendering when large provider values change.

Useful strategies include:

- Split contexts by responsibility
- Separate state and dispatch context
- Keep providers closer to consumers
- Avoid huge provider value objects
- Memoize provider values when appropriate
- Use external stores for highly dynamic shared state

**Example:**

Instead of:

```jsx
<AppContext.Provider
  value={{
    user,
    theme,
    cart,
    notifications,
  }}
>
```

split into focused providers:

```jsx
<AuthProvider>
  <ThemeProvider>
    <CartProvider>{children}</CartProvider>
  </ThemeProvider>
</AuthProvider>
```

**Interview Line**

Optimize context-heavy components by splitting contexts and ensuring consumers subscribe only to the data they actually need.

### Q. What is windowing in React?

**Answer:**

Windowing, also called virtualization, renders only the visible portion of a large list.

Instead of rendering:

```text
10,000 rows
```

the application may render only:

```text
20-50 visible rows
```

as the user scrolls.

Libraries commonly used for this pattern include virtual-list libraries.

Benefits include:

- Fewer DOM nodes
- Faster rendering
- Lower memory usage
- Better scrolling performance

**Interview Line**

Windowing improves large-list performance by rendering only the items currently visible in the viewport.

### Q. How do you optimize table rendering?

**Answer:**

Large tables can be expensive because many rows and cells create large DOM trees.

Common optimizations include:

- Pagination
- Virtualization
- Memoized rows
- Stable row keys
- Avoid expensive cell calculations
- Avoid re-rendering all rows for one cell update
- Server-side sorting/filtering for huge datasets

**Example:**

Instead of rendering:

```text
50,000 rows
```

use:

```text
pagination
or
virtualized rows
```

For interactive tables, keep frequently changing cell state as local as possible.

**Interview Line**

Optimize tables with pagination or virtualization, stable row identity, localized updates, and reduced per-cell computation.

### Q. How do you optimize charts in React?

**Answer:**

Charts can be expensive because they may process large datasets and perform heavy SVG or canvas rendering.

Useful strategies include:

- Memoize transformed chart data
- Avoid recreating configuration objects
- Lazy load chart libraries
- Reduce unnecessary data points
- Avoid re-rendering the chart for unrelated state
- Use canvas/WebGL for very large datasets when supported
- Debounce resize handling

**Example:**

```jsx
const chartData = useMemo(() => transformData(rawData), [rawData]);
```

Then pass stable data to the chart.

**Interview Line**

Optimize charts by reducing data processing, stabilizing inputs, lazy loading heavy libraries, and avoiding unrelated re-renders.

### Q. How do you prevent unnecessary API calls?

**Answer:**

Common techniques include:

- Debounce search requests
- Cache server data
- Deduplicate in-flight requests
- Cancel stale requests
- Use stable query keys
- Avoid incorrect `useEffect` dependencies
- Disable duplicate submit actions
- Use server-state libraries

**Example with debounce:**

```jsx
const debouncedQuery = useDebounce(query, 400);
```

**Example with React Query:**

```jsx
useQuery({
  queryKey: ["users", userId],
  queryFn: () => fetchUser(userId),
});
```

The library can reuse the same cached query instead of repeatedly fetching identical data.

**Interview Line**

Prevent unnecessary API calls with caching, deduplication, debounce, correct dependencies, and stale-request cancellation.

### Q. How do you handle expensive calculations in render?

**Answer:**

Avoid repeating expensive calculations on every render when the inputs have not changed.

**Example:**

Without memoization:

```jsx
const filteredItems = expensiveFilter(items, query);
```

If profiling shows this calculation is expensive:

```jsx
const filteredItems = useMemo(() => {
  return expensiveFilter(items, query);
}, [items, query]);
```

Other options include:

- Precompute data earlier
- Move work to the server
- Split work into smaller tasks
- Use Web Workers for CPU-heavy calculations
- Reduce dataset size

Do not use `useMemo` for every small expression.

**Interview Line**

Handle expensive render calculations by profiling first, then memoizing, precomputing, reducing work, or moving CPU-heavy tasks off the main thread.

## Security

### Q. How can XSS happen in React?

**Answer:**

React escapes values rendered inside JSX by default, which protects against many common Cross-Site Scripting attacks.

**Example:**

```jsx
const input = "<img src=x onerror=alert(1)>";

return <div>{input}</div>;
```

React renders the value as text instead of interpreting it as executable HTML.

However, XSS can still happen when an application bypasses React's normal escaping.

Common examples include:

- Using `dangerouslySetInnerHTML`
- Writing directly to `innerHTML`
- Using untrusted values in unsafe third-party libraries
- Creating unsafe URLs
- Rendering unsanitized HTML from APIs or CMS systems

**Interview Line**

React escapes JSX values by default, but XSS is still possible when untrusted content bypasses normal escaping.

### Q. Does React fully prevent XSS?

**Answer:**

No.

React protects normal JSX interpolation by escaping values, but developers can still introduce XSS by using unsafe APIs or rendering untrusted HTML.

Risky areas include:

- `dangerouslySetInnerHTML`
- `innerHTML`
- Unsafe third-party DOM libraries
- Unsanitized HTML
- Unsafe redirect URLs
- Dangerous URL schemes

Security also depends on backend validation, CSP, secure cookies, authorization, and other controls outside React.

**Interview Line**

React reduces XSS risk through automatic escaping, but it does not fully prevent XSS if developers render or execute untrusted content unsafely.

### Q. What is `dangerouslySetInnerHTML`?

**Answer:**

`dangerouslySetInnerHTML` is a React API that inserts raw HTML directly into the DOM.

It is similar to:

```js
element.innerHTML;
```

**Example:**

```jsx
const content = "<strong>Hello</strong>";

return (
  <div
    dangerouslySetInnerHTML={{
      __html: content,
    }}
  />
);
```

React uses the word `dangerously` to highlight that this bypasses normal escaping.

It is sometimes used for:

- CMS content
- Rich-text editors
- Trusted HTML
- Markdown converted to HTML

**Interview Line**

`dangerouslySetInnerHTML` inserts raw HTML into the DOM and bypasses React's normal escaping.

### Q. When is `dangerouslySetInnerHTML` risky?

**Answer:**

It is risky when the HTML comes from an untrusted or insufficiently sanitized source.

**Bad Example:**

```jsx
<div
  dangerouslySetInnerHTML={{
    __html: commentFromUser,
  }}
/>
```

Sources requiring caution include:

- User comments
- Rich text
- CMS content
- External APIs
- URL parameters
- Stored database content

If the content can be controlled by an attacker, sanitize it before rendering.

**Interview Line**

`dangerouslySetInnerHTML` is risky whenever attacker-controlled HTML can reach it without proper sanitization.

### Q. How do you safely render HTML from API?

**Answer:**

Treat API HTML as untrusted unless there is a strong security guarantee.

A common flow is:

```text
API HTML
↓
Sanitize
↓
Render
```

**Example:**

```jsx
import DOMPurify from "dompurify";

function Article({ html }) {
  const safeHtml = DOMPurify.sanitize(html);

  return (
    <div
      dangerouslySetInnerHTML={{
        __html: safeHtml,
      }}
    />
  );
}
```

Whenever possible, prefer structured data that React can render normally.

**Interview Line**

Safely render API HTML by sanitizing it first and prefer structured data over raw HTML whenever possible.

### Q. How do you sanitize user-generated content?

**Answer:**

Sanitization removes or neutralizes unsafe HTML while preserving allowed markup.

Use a well-maintained HTML sanitizer instead of trying to parse dangerous HTML with regular expressions.

**Example:**

```jsx
import DOMPurify from "dompurify";

const sanitized = DOMPurify.sanitize(userHtml);
```

Then:

```jsx
<div
  dangerouslySetInnerHTML={{
    __html: sanitized,
  }}
/>
```

Sanitization should also be combined with server-side controls when user content is stored.

**Interview Line**

Sanitize user-generated HTML with a trusted sanitizer instead of custom regex-based filtering.

### Q. What is DOMPurify?

**Answer:**

DOMPurify is a popular HTML sanitization library used to clean untrusted HTML before it is inserted into the DOM.

**Example:**

```jsx
import DOMPurify from "dompurify";

const clean = DOMPurify.sanitize(apiResponse.content);
```

Then:

```jsx
<div
  dangerouslySetInnerHTML={{
    __html: clean,
  }}
/>
```

It is useful when applications need to render HTML from:

- CMS systems
- Rich-text editors
- User-generated content
- External services

**Interview Line**

DOMPurify sanitizes untrusted HTML before rendering and helps reduce DOM-based XSS risk.

### Q. How do you secure forms in React?

**Answer:**

React form security requires both frontend and backend protection.

Frontend validation improves user experience but must not be treated as the final security boundary.

Important practices include:

- Validate input
- Escape output
- Use HTTPS
- Protect authenticated requests against CSRF where relevant
- Avoid exposing sensitive values
- Disable duplicate submissions
- Validate file uploads
- Enforce authorization on the server

**Example:**

```jsx
if (!email.includes("@")) {
  setError("Invalid email");
}
```

The server must still validate the same value.

**Interview Line**

React forms should validate for UX, while the server must enforce validation, authorization, and all security-sensitive rules.

### Q. How do you prevent sensitive data exposure in frontend?

**Answer:**

Anything delivered to the browser should be considered accessible to the user.

Do not place secrets in:

- JavaScript bundles
- Public environment variables
- LocalStorage
- SessionStorage
- HTML
- Unnecessary API responses

Examples of secrets that should remain server-side include:

```text
database passwords
private API keys
JWT signing secrets
cloud credentials
payment-provider secret keys
```

The frontend should receive only the minimum data needed for the current user and action.

**Interview Line**

Assume all frontend code and data can be inspected, so true secrets must remain on trusted server-side systems.

### Q. Why should secrets not be stored in React environment variables?

**Answer:**

Frontend environment variables can be bundled into JavaScript delivered to the browser.

So values exposed to client code can usually be inspected.

Unsafe example:

```env
API_SECRET=super-secret-value
```

Frontend environment variables are appropriate only for public configuration such as:

```text
API base URL
analytics ID
public feature configuration
```

Secret operations should happen on the backend.

**Interview Line**

React environment variables are not secret once included in client-side bundles, so private credentials must remain server-side.

### Q. How do you handle secure redirects?

**Answer:**

Redirect destinations should never be trusted blindly when they come from user input.

**Bad Example:**

```js
const params = new URLSearchParams(location.search);

window.location.href = params.get("redirect");
```

A safer design is to allow only known internal paths or approved origins.

**Example:**

```js
const allowedPaths = ["/dashboard", "/profile"];

const redirect = params.get("redirect");

if (allowedPaths.includes(redirect)) {
  window.location.href = redirect;
}
```

Also reject unsafe schemes such as:

```text
javascript:
data:
```

**Interview Line**

Secure redirects validate user-controlled destinations against an allowlist and reject unexpected paths, origins, and URL schemes.

### Q. What is open redirect?

**Answer:**

An open redirect vulnerability occurs when an application accepts a user-controlled redirect destination without strict validation.

**Example:**

```text
https://example.com/login?redirect=https://evil.example
```

If the application directly redirects to that value, an attacker can abuse the trusted domain to send users to a malicious site.

Open redirects are commonly used in:

- Phishing
- Fake login pages
- Trust abuse
- Authentication-flow attacks

The safest approach is to allow only approved destinations.

**Interview Line**

An open redirect allows attacker-controlled redirect targets and is prevented with strict validation or allowlisting.

### Q. How do you protect against clickjacking?

**Answer:**

Clickjacking happens when an attacker embeds your application inside another page and tricks users into clicking hidden or misleading UI.

The main protection should be HTTP response headers.

**Example:**

```http
Content-Security-Policy: frame-ancestors 'none';
```

Or:

```http
Content-Security-Policy: frame-ancestors 'self';
```

Older protection:

```http
X-Frame-Options: DENY
```

or:

```http
X-Frame-Options: SAMEORIGIN
```

**Interview Line**

Protect against clickjacking with CSP `frame-ancestors` and, where appropriate, `X-Frame-Options`.

### Q. What security headers are useful for React apps?

**Answer:**

Security headers are configured by the server, CDN, reverse proxy, or framework serving the React app.

Useful headers include:

- `Content-Security-Policy`
- `Strict-Transport-Security`
- `X-Content-Type-Options`
- `Referrer-Policy`
- `Permissions-Policy`
- `X-Frame-Options`

For example:

```http
X-Content-Type-Options: nosniff
```

and:

```http
Referrer-Policy: strict-origin-when-cross-origin
```

The exact policy should match the application's architecture.

**Interview Line**

Useful security headers include CSP, HSTS, `X-Content-Type-Options`, `Referrer-Policy`, `Permissions-Policy`, and frame restrictions.

### Q. How do you handle dependency vulnerabilities?

**Answer:**

Frontend applications rely heavily on third-party packages, so dependency security should be managed continuously.

Useful practices include:

- Keep dependencies updated
- Remove unused packages
- Review security advisories
- Run vulnerability scanners
- Lock dependency versions
- Prefer maintained libraries
- Avoid unnecessary dependencies
- Monitor transitive dependencies

**Example:**

```bash
npm audit
```

Audit results should be evaluated based on whether the vulnerable code path actually affects the application.

For serious issues, upgrade, patch, replace, or remove the affected dependency.

**Interview Line**

Manage dependency vulnerabilities through continuous auditing, timely upgrades, dependency minimization, and review of direct and transitive packages.

## Lifecycle & Error Handling

### Q. What are lifecycle methods?

**Answer:**

Lifecycle methods are special methods in class components that let you run code at specific stages of a component’s life—from creation to removal.

Why they exist:

They allow you to:

- Fetch data
- Update DOM
- Clean up resources
- Handle errors

Interview one-liner:

“Lifecycle methods allow developers to hook into different stages of a React component’s life.”

### Q. Phases of component lifecycle

**Answer:**

React lifecycle has three main phases 👇

1️⃣ Mounting (component is created)

- `constructor()`
- `render()`
- `componentDidMount()`

2️⃣ Updating (state/props change)

- `render()`
- `componentDidUpdate()`

3️⃣ Unmounting (component removed)

- `componentWillUnmount()`

Interview one-liner:

“React components go through mounting, updating, and unmounting phases.”

### Q. What is componentDidMount used for?

**Answer:**

`componentDidMount()` runs once after the component is rendered to the DOM.

Common use cases:

- API calls
- Subscriptions
- Timers
- DOM manipulation

```jsx
componentDidMount() {
  fetchData();
}
```

Why not in constructor?

DOM is not ready in constructor.

Interview one-liner:

“componentDidMount is used for side effects like API calls after the component is rendered.”

### Q. What are error boundaries?

**Answer:**

Error boundaries are special class components that catch JavaScript errors in:

- Child component rendering
- Lifecycle methods
- Constructors

…and show a fallback UI instead of crashing the app.

Important:

They do not catch errors in:

- Event handlers
- Async code
- Server-side rendering

Interview one-liner:

“Error boundaries prevent the entire app from crashing by handling render-time errors.”

### Q. How do error boundaries work?

**Answer:**

They rely on two lifecycle methods:

1. static getDerivedStateFromError(error)
   → Updates state to show fallback UI

2. componentDidCatch(error, info)
   → Logs error (e.g., to monitoring services)

```jsx
class ErrorBoundary extends React.Component {
  state = { hasError: false };

  static getDerivedStateFromError() {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    logError(error, info);
  }

  render() {
    return this.state.hasError ? <Fallback /> : this.props.children;
  }
}
```

Interview one-liner:

“Error boundaries catch errors during rendering and display a fallback UI.”

### Q. Can hooks catch errors?

**Answer:**

Short answer: ❌ No

Explanation:

- Hooks cannot act as error boundaries
- There is no hook equivalent of componentDidCatch

What you can do instead:

- Use error boundary class components
- Wrap functional components inside them

Interview one-liner:

“Hooks cannot catch render errors; error boundaries must be class components.”

### Q. Difference between error boundaries and try–catch

**Answer:**

| Feature                  | Error Boundary | try–catch |
| ------------------------ | -------------- | --------- |
| Catches render errors    | ✅ Yes         | ❌ No     |
| Catches lifecycle errors | ✅ Yes         | ❌ No     |
| Catches async errors     | ❌ No          | ✅ Yes    |
| UI fallback              | ✅ Yes         | ❌ No     |
| React-specific           | ✅ Yes         | ❌ No     |

Key takeaway (say this):

“Error boundaries handle rendering errors, while try–catch handles synchronous code errors.”

### Q. Why are Error Boundaries only class components?

**Answer:**

Error boundaries are only class components because they rely on lifecycle methods like componentDidCatch and getDerivedStateFromError, which are not available in function components.

Explanation

React introduced error boundaries before hooks existed.

Class components support:

```js
static getDerivedStateFromError(error)
componentDidCatch(error, info)
```

Function components:

- Don’t have lifecycle methods
- Hooks don’t provide direct error boundary capability (yet)

**Interview Line**

“Error boundaries depend on lifecycle methods, which is why they are implemented only in class components.”

### Q. Can one error boundary catch errors in itself?

**Answer:**

❌ Short Answer

No.

Explanation

Error boundaries cannot catch errors within themselves.

They only catch errors in:

- Child components
- Their subtree

Example

```js
<ErrorBoundary>
  <Child />
</ErrorBoundary>
```

✅ Catches errors in Child

❌ Cannot catch its own errors

**Interview Line**

“Error boundaries only catch errors in their children, not in themselves.”

### Q. Where should error boundaries be placed?

**Answer:**

Error boundaries should be placed around critical parts of the UI to prevent the entire app from crashing.

Best Practices

- Wrap route-level components
- Wrap independent UI sections
- Avoid wrapping entire app

Example

```js
<App>
  <ErrorBoundary>
    <Navbar />
  </ErrorBoundary>

  <ErrorBoundary>
    <Routes />
  </ErrorBoundary>
</App>
```

🔥 Strategy

| Placement       | Purpose             |
| --------------- | ------------------- |
| Global          | Catch major crashes |
| Component-level | Isolate failures    |

**Interview Line**

“Error boundaries should be placed strategically to isolate failures and prevent full app crashes.”

### Q. Do error boundaries catch errors in event handlers?

**Answer:**

❌ Short Answer

No.

Explanation

Error boundaries only catch errors during:

- Rendering
- Lifecycle methods
- Constructors

They do NOT catch:

- Event handlers
- Async code (setTimeout, promises)
- Server-side errors

Example

```jsx
<button
  onClick={() => {
    throw new Error("Error");
  }}
>
  Click
</button>
```

❌ Not caught by Error Boundary

How to Handle Instead

```js
try {
  // logic
} catch (e) {
  // handle error
}
```

**Interview Line**

“Error boundaries do not catch errors in event handlers; those must be handled manually using try-catch.”

🔥 Final Summary (Strong Answer)

“Error boundaries are class components that catch rendering errors in their child components using lifecycle methods. They cannot catch errors in themselves or in event handlers, so they should be placed strategically around critical UI sections.”

#### ⭐ 30-Second Interview Summary

“Lifecycle methods allow us to run logic during mounting, updating, and unmounting of class components. componentDidMount is commonly used for API calls. Error boundaries are special class components that catch rendering errors using getDerivedStateFromError and componentDidCatch. Hooks cannot catch such errors, and error boundaries are different from try–catch, which only handles synchronous code.”

### Q. What is `getDerivedStateFromProps`?

**Answer:**

`getDerivedStateFromProps` is a static lifecycle method used in React class components to update state based on changes in props.

It runs during mounting and updating.

**Example:**

```jsx
class UserProfile extends React.Component {
  state = {
    selectedUserId: this.props.userId,
  };

  static getDerivedStateFromProps(nextProps, prevState) {
    if (nextProps.userId !== prevState.selectedUserId) {
      return {
        selectedUserId: nextProps.userId,
      };
    }

    return null;
  }

  render() {
    return <p>{this.state.selectedUserId}</p>;
  }
}
```

The method returns a partial state object or `null`.

Because it is static, it cannot access the component instance through `this`.

**Interview Line**

`getDerivedStateFromProps` is a static class lifecycle method used to synchronize state with props before rendering.

### Q. Why is `getDerivedStateFromProps` rarely used?

**Answer:**

It is rarely needed because copying props into state often creates duplicated state and synchronization problems.

**Problematic Example:**

```jsx
state = {
  name: this.props.name,
};
```

Now both:

```text
props.name
state.name
```

represent the same information.

If they become out of sync, the component can behave incorrectly.

In many cases, the better solution is simply to use the prop directly:

```jsx
render() {
  return <p>{this.props.name}</p>;
}
```

**Interview Line**

`getDerivedStateFromProps` is rarely used because derived state often duplicates props and creates unnecessary synchronization complexity.

### Q. What is `shouldComponentUpdate`?

**Answer:**

`shouldComponentUpdate` is a class lifecycle method used to decide whether React should continue rendering a component after props or state change.

**Example:**

```jsx
class Counter extends React.Component {
  shouldComponentUpdate(nextProps) {
    return nextProps.count !== this.props.count;
  }

  render() {
    return <p>{this.props.count}</p>;
  }
}
```

If it returns:

```js
false;
```

React can skip rendering that component for that update.

It is mainly a performance optimization.

Modern function components usually use `React.memo` instead.

**Interview Line**

`shouldComponentUpdate` lets class components skip unnecessary renders by returning `false` when relevant props and state have not changed.

### Q. What is `getSnapshotBeforeUpdate`?

**Answer:**

`getSnapshotBeforeUpdate` is a class lifecycle method that runs after render but before React commits DOM changes.

It lets the component capture information from the DOM before the update is applied.

**Example:**

```jsx
class MessageList extends React.Component {
  getSnapshotBeforeUpdate() {
    return this.listRef.scrollHeight;
  }

  componentDidUpdate(prevProps, prevState, snapshot) {
    console.log(snapshot);
  }

  render() {
    return (
      <div
        ref={(node) => {
          this.listRef = node;
        }}
      />
    );
  }
}
```

The value returned from `getSnapshotBeforeUpdate` is passed to `componentDidUpdate`.

**Interview Line**

`getSnapshotBeforeUpdate` captures DOM information immediately before React applies an update and passes it to `componentDidUpdate`.

### Q. When is `getSnapshotBeforeUpdate` useful?

**Answer:**

It is useful when you need to read DOM measurements before React changes the DOM.

A common example is preserving scroll position in a chat or message list.

**Example Flow:**

```text
Render new messages
↓
getSnapshotBeforeUpdate
Read old DOM measurement
↓
Commit DOM changes
↓
componentDidUpdate
Use snapshot to restore position
```

This method is uncommon because most components do not need pre-commit DOM measurements.

**Interview Line**

`getSnapshotBeforeUpdate` is useful for preserving DOM-related information such as scroll position before an update changes the layout.

### Q. What is the order of lifecycle methods during mounting?

**Answer:**

For a React class component, the common mounting lifecycle order is:

```text
constructor
↓
static getDerivedStateFromProps
↓
render
↓
componentDidMount
```

#### 1. `constructor`

Used for initial state and method binding.

#### 2. `getDerivedStateFromProps`

Runs before render when defined.

#### 3. `render`

Returns the React elements.

#### 4. `componentDidMount`

Runs after the component has been committed to the DOM.

**Interview Line**

The class mounting order is `constructor` → `getDerivedStateFromProps` → `render` → `componentDidMount`.

### Q. What is the order of lifecycle methods during updating?

**Answer:**

For a class component update, the common order is:

```text
static getDerivedStateFromProps
↓
shouldComponentUpdate
↓
render
↓
getSnapshotBeforeUpdate
↓
componentDidUpdate
```

If `shouldComponentUpdate()` returns `false`, React skips the later render work for that update.

**Interview Line**

The class update order is `getDerivedStateFromProps` → `shouldComponentUpdate` → `render` → `getSnapshotBeforeUpdate` → `componentDidUpdate`.

### Q. How do you handle errors in event handlers?

**Answer:**

Errors thrown inside event handlers are not caught by React Error Boundaries.

Handle them with normal JavaScript error handling.

**Example:**

```jsx
function DeleteButton() {
  async function handleDelete() {
    try {
      await deleteUser();
    } catch (error) {
      console.error(error);
    }
  }

  return <button onClick={handleDelete}>Delete</button>;
}
```

You can also store an error message in state and show it to the user.

**Interview Line**

Handle event-handler errors with `try...catch` because React Error Boundaries do not catch errors thrown from event handlers.

### Q. How do you handle errors in async API calls?

**Answer:**

Async API calls should handle both HTTP failures and rejected promises.

**Example:**

```jsx
async function loadUser() {
  try {
    const response = await fetch("/api/user");

    if (!response.ok) {
      throw new Error(`HTTP ${response.status}`);
    }

    const data = await response.json();

    setUser(data);
  } catch (error) {
    console.error(error);

    setError("Unable to load user");
  }
}
```

Also consider loading state, retry strategy, stale request cancellation, and user-facing fallback UI.

**Interview Line**

Handle async API errors with `try...catch`, explicitly check HTTP status, and expose useful loading and error states.

### Q. How do you handle errors in custom hooks?

**Answer:**

A custom hook should expose errors through a clear public API or intentionally throw them when that is part of the design.

**Example:**

```jsx
function useUser(userId) {
  const [user, setUser] = useState(null);

  const [error, setError] = useState(null);

  useEffect(() => {
    async function load() {
      try {
        const response = await fetch(`/api/users/${userId}`);

        if (!response.ok) {
          throw new Error("Request failed");
        }

        setUser(await response.json());
      } catch (error) {
        setError(error);
      }
    }

    load();
  }, [userId]);

  return {
    user,
    error,
  };
}
```

The consuming component then decides how to present the error.

**Interview Line**

Custom hooks should handle failures predictably and expose error state or thrown errors through a clear contract.

### Q. How do you create reusable error fallback UI?

**Answer:**

Create a shared component that receives error information and optional recovery actions through props.

**Example:**

```jsx
function ErrorFallback({ message, onRetry }) {
  return (
    <div role="alert">
      <h2>Something went wrong</h2>

      <p>{message}</p>

      {onRetry && <button onClick={onRetry}>Try again</button>}
    </div>
  );
}
```

A good fallback should be accessible, clear, and actionable.

**Interview Line**

Reusable error fallback UI should show a clear message and optional recovery action through a shared component API.

### Q. How do you reset an error boundary?

**Answer:**

An Error Boundary can be reset by clearing its internal error state or by remounting it with a new `key`.

**Class Example:**

```jsx
class ErrorBoundary extends React.Component {
  state = {
    hasError: false,
  };

  static getDerivedStateFromError() {
    return {
      hasError: true,
    };
  }

  reset = () => {
    this.setState({
      hasError: false,
    });
  };

  render() {
    if (this.state.hasError) {
      return <button onClick={this.reset}>Retry</button>;
    }

    return this.props.children;
  }
}
```

Changing a boundary key is another reset mechanism:

```jsx
<ErrorBoundary key={resetKey}>
  <Feature />
</ErrorBoundary>
```

**Interview Line**

Reset an Error Boundary by clearing its error state or remounting it with a different `key`.

### Q. How do you log errors from error boundaries?

**Answer:**

Class Error Boundaries can report rendering errors from `componentDidCatch()`.

**Example:**

```jsx
class ErrorBoundary extends React.Component {
  componentDidCatch(error, info) {
    logError({
      error,
      componentStack: info.componentStack,
    });
  }

  render() {
    return this.props.children;
  }
}
```

Useful context includes:

- Error message
- Stack trace
- Component stack
- Route
- App version
- Browser details

Avoid logging sensitive user information unnecessarily.

**Interview Line**

Use `componentDidCatch` to send rendering errors and component-stack context to an error-monitoring service.

### Q. How do you integrate Sentry with React error boundaries?

**Answer:**

Sentry can capture errors reported from an Error Boundary and attach useful component context.

A manual integration looks conceptually like:

```jsx
componentDidCatch(
  error,
  info
) {
  Sentry.captureException(
    error,
    {
      extra: {
        componentStack:
          info.componentStack,
      },
    }
  );
}
```

A production setup typically includes:

1. Initialize Sentry once.
2. Wrap important UI with an Error Boundary.
3. Capture exceptions.
4. Add release/version metadata.
5. Upload source maps so stack traces are readable.

**Interview Line**

Sentry integrates with React Error Boundaries by capturing exceptions and component-stack details for production monitoring.

### Q. What is graceful degradation in React UI?

**Answer:**

Graceful degradation means the application remains useful even when one feature fails.

Instead of:

```text
One widget fails
→ whole page becomes unusable
```

prefer:

```text
Dashboard
├── Navigation works
├── Profile works
└── Analytics widget shows fallback
```

Examples include:

- Placeholder for failed images
- Retry UI for failed requests
- Cached data during network failure
- Simpler fallback for optional widgets
- Disabling only the failed feature

**Interview Line**

Graceful degradation keeps the application usable by providing simpler fallback behavior when a non-critical feature fails.

### Q. How do you show fallback UI for failed components?

**Answer:**

For rendering failures, use an Error Boundary around the smallest useful feature boundary.

**Example:**

```jsx
<ErrorBoundary>
  <AnalyticsWidget />
</ErrorBoundary>
```

For async data failures, render fallback UI from request state.

**Example:**

```jsx
if (isError) {
  return <ErrorFallback message="Unable to load data" onRetry={refetch} />;
}
```

The goal is to isolate failure so the rest of the page can continue working.

**Interview Line**

Use Error Boundaries for rendering failures and explicit error states for async failures, ideally isolating the fallback to the affected feature.

## Routing

### Q. What is React Router?

**Answer:**

React Router is a client-side routing library for React that enables navigation between views without reloading the page.

Why it’s needed:

- React is a Single Page Application
- URLs must change without full page refresh
- Different components render for different routes

Interview one-liner:

“React Router enables declarative routing in React applications without page reloads.”

### Q. Difference between BrowserRouter and HashRouter

**Answer:**

| Feature        | BrowserRouter     | HashRouter       |
| -------------- | ----------------- | ---------------- |
| URL type       | `/users/1`        | `/#/users/1`     |
| Uses           | HTML5 History API | URL hash         |
| Server support | Required          | Not required     |
| SEO friendly   | ✅ Yes            | ❌ No            |
| Production use | Preferred         | Limited / legacy |

When to use:

- BrowserRouter → modern apps with server config
- HashRouter → static hosting (GitHub Pages)

Interview one-liner:

“BrowserRouter uses clean URLs but needs server support, while HashRouter works without server configuration.”

### Q. What is dynamic routing?

**Answer:**

Dynamic routing means routes are created using parameters that change based on data.

Example:

```jsx
<Route path="/users/:id" element={<User />} />
```

/users/101 and /users/202 use the same route.

Why useful:

- Profile pages
- Product pages
- Detail views

Interview one-liner:

“Dynamic routing allows rendering the same component for different URLs using route parameters.”

### Q. How do you pass params in routes?

**Answer:**

1️⃣ Path params

```jsx
<Route path="/product/:id" element={<Product />} />
```

```jsx
const { id } = useParams();
```

2️⃣ Query params

```jsx
/products?category=mobile
```

```jsx
const params = new URLSearchParams(location.search);
```

3️⃣ State (navigation state)

```jsx
navigate("/profile", { state: user });
```

Interview one-liner:

“Route params can be passed using path params, query strings, or navigation state.”

### Q. How do you handle protected routes?

**Answer:**

Protected routes restrict access based on authentication or authorization.

Common approach:

- Create a wrapper component
- Check auth status
- Redirect if not allowed

```jsx
function ProtectedRoute({ children }) {
  return isAuth ? children : <Navigate to="/login" />;
}
```

Used for:

- Dashboard
- Admin pages
- Profile pages

Interview one-liner:

“Protected routes use conditional rendering to restrict access based on authentication.”

### Q. What is `useNavigate`?

**Answer:**

`useNavigate` is a hook used for programmatic navigation.

Example:

```jsx
const navigate = useNavigate();
navigate("/dashboard");
```

Common use cases:

- After login
- After form submit
- On button click

Interview one-liner:

“`useNavigate` allows navigation programmatically instead of using links.”

### Q. Difference between `Link` and `NavLink`

| Feature              | Link         | NavLink         |
| -------------------- | ------------ | --------------- |
| Navigation           | ✅ Yes       | ✅ Yes          |
| Active state         | ❌ No        | ✅ Yes          |
| Styling active route | ❌ No        | ✅ Yes          |
| Common use           | Normal links | Menus / navbars |

Example:

```jsx
<NavLink to="/home" className={({ isActive }) => (isActive ? "active" : "")} />
```

Interview one-liner:

“`NavLink` provides active route styling, while `Link` is used for simple navigation.”

### Q. Difference between `Navigate` and `useNavigate`

Short Answer

`Navigate` → component-based navigation

`useNavigate` → programmatic navigation (hook)

Explanation

Both are part of React Router, but used in different situations.

Comparison

| Feature    | `Navigate`  | `useNavigate`        |
| ---------- | ----------- | -------------------- |
| Type       | Component   | Hook                 |
| Used in    | JSX         | Functions / events   |
| Navigation | Declarative | Imperative           |
| Common use | Auth guards | Button click, submit |

Examples

Navigate

```jsx
return isLoggedIn ? <Dashboard /> : <Navigate to="/login" />;
```

useNavigate

```jsx
const navigate = useNavigate();

<button onClick={() => navigate("/profile")}>Go to Profile</button>;
```

📌 Interview Tip

Use `Navigate` when rendering conditionally, `useNavigate` when reacting to events.

### Q. How Routing Works in an SPA

Short Answer

In an SPA, routing changes the URL without reloading the page, and renders different components dynamically.

Explanation

- Browser loads one HTML file
- Route changes are handled by JavaScript
- Uses History API (pushState)
- Only components change, not the whole page

Flow

URL change → Router matches route → Component renders → No reload

Example

```jsx
<Routes>
  <Route path="/login" element={<Login />} />
  <Route path="/dashboard" element={<Dashboard />} />
</Routes>
```

📌 Why SPAs are fast

- No full-page reload
- Less network usage
- Smooth UX

### Q. How to Handle 404 Routes

Short Answer

Use a catch-all route (\*) to handle unmatched paths.

Explanation

If no route matches the URL, React Router renders the fallback route.

Example

```jsx
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about" element={<About />} />
  <Route path="\*" element={<NotFound />} />
</Routes>
```

Real-world Use

- Show “Page Not Found”
- Redirect to home
- Track invalid URLs

### Q. Nested Routing – Use Cases

Short Answer

Nested routing is used when a page has sub-sections that share layout or context.

Common Use Cases

- Dashboard pages
- Admin panels
- Settings pages
- Tabs with URLs

Example

```jsx
<Route path="/dashboard" element={<Dashboard />}>
  <Route path="profile" element={<Profile />} />
  <Route path="settings" element={<Settings />} />
</Route>
```

```jsx
// Dashboard.jsx
<>
  <Sidebar />
  <Outlet />
</>
```

Why It’s Useful

- Shared layout
- Clean URL structure
- Better scalability

### Q. Route-Based Code Splitting

Short Answer

Route-based code splitting loads only the code needed for the current route, improving performance.

Explanation

- Uses React.lazy + Suspense
- Reduces initial bundle size
- Faster page load

Example

```jsx
const Dashboard = React.lazy(() => import("./Dashboard"));

<Suspense fallback={<Loader />}>
  <Routes>
    <Route path="/dashboard" element={<Dashboard />} />
  </Routes>
</Suspense>;
```

When to Use

- Large applications
- Rarely visited pages
- Admin or analytics sections

📌 Interview Line

“Route-based code splitting improves performance by loading components only when their route is accessed.”

### Q. What is History API and how does it work in React routing?

**Answer:**

The History API is a browser API that allows JavaScript to manipulate the browser’s session history (URL and navigation) without reloading the page.

React Router uses it to implement client-side routing in SPAs.

It’s part of modern browsers (HTML5) and provides methods like:

- `history.pushState()`
- `history.replaceState()`
- `popstate` event
- `history.back()`
- `history.forward()`

It allows changing the URL without refreshing the page.

Key Methods Explained

1️⃣ `pushState()`

Adds a new entry to browser history.

```js
history.pushState({ page: 1 }, "", "/dashboard");
```

✅ Changes URL

✅ Does NOT reload page

2️⃣ `replaceState()`

Replaces the current history entry.

```js
history.replaceState({}, "", "/login");
```

Used when you don’t want the user to go back.

3️⃣ `popstate` Event

Triggered when:

User clicks back/forward button

```js
window.addEventListener("popstate", (event) => {
  console.log("URL changed");
});
```

How It Works in React Routing

React Router (from React Router) internally uses the History API.

Flow in SPA:

1. User clicks `<Link to="/dashboard" />`
2. React Router calls `history.pushState()`
3. URL changes
4. No page reload
5. Router matches new route
6. Corresponding component renders

```
Click → pushState → URL change → Component render → No reload
```

Example in React

```jsx
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";

<BrowserRouter>
  <Link to="/about">About</Link>

  <Routes>
    <Route path="/about" element={<About />} />
  </Routes>
</BrowserRouter>;
```

BrowserRouter uses the History API under the hood.

What Happens on Page Refresh?

Since it’s client-side routing:

- Browser requests /dashboard
- Server must return index.html
- React takes over routing

If server is not configured properly → 404 error

👉 That’s why SPA deployments need fallback routing.

Why History API is Important for SPAs

Without History API:

- URL would not change
- No back/forward support
- Bad SEO

With History API:

- Real URLs
- Browser navigation works
- Better user experience

History API vs Hash Routing

| Feature              | History API   | Hash Router |
| -------------------- | ------------- | ----------- |
| URL format           | `/about`      | `/#/about`  |
| SEO friendly         | ✅ Yes        | ❌ Less     |
| Server config needed | ✅ Yes        | ❌ No       |
| Used by              | BrowserRouter | HashRouter  |

One-Line Interview Summary

“The History API allows React Router to change URLs and manage navigation without reloading the page, enabling client-side routing in SPAs.”

### ⭐ 30-Second Interview Summary

“React Router enables client-side routing in SPAs. BrowserRouter uses the history API with clean URLs, while HashRouter uses URL hashes. Dynamic routing allows parameters in routes. Route params can be passed via path, query, or state. Protected routes restrict access using authentication checks. useNavigate enables programmatic navigation, and NavLink is used when active route styling is required.”

### Q. What is route layout?

**Answer:**

A route layout is a parent route element that renders shared UI for a group of nested routes.

Common layout content includes:

- Header
- Sidebar
- Navigation
- Footer
- Shared route context

The nested child route is usually rendered through:

```jsx
<Outlet />
```

**Example:**

```jsx
import { Outlet } from "react-router-dom";

function DashboardLayout() {
  return (
    <div>
      <Sidebar />

      <main>
        <Outlet />
      </main>
    </div>
  );
}
```

Route configuration:

```jsx
{
  path: "/dashboard",
  element:
    <DashboardLayout />,
  children: [
    {
      index: true,
      element:
        <DashboardHome />,
    },
    {
      path: "settings",
      element:
        <Settings />,
    },
  ],
}
```

Both child routes reuse the same dashboard layout.

**Interview Line**

A route layout is a parent route that provides shared UI and renders nested child routes through `<Outlet />`.

### Q. What is outlet context in React Router?

**Answer:**

Outlet context lets a parent route pass data directly to nested route components rendered through `<Outlet />`.

**Parent Example:**

```jsx
import { Outlet } from "react-router-dom";

function DashboardLayout() {
  const user = {
    name: "John",
  };

  return (
    <Outlet
      context={{
        user,
      }}
    />
  );
}
```

Child route:

```jsx
import { useOutletContext } from "react-router-dom";

function Profile() {
  const { user } = useOutletContext();

  return <h1>{user.name}</h1>;
}
```

This is useful when shared data belongs specifically to a route subtree and does not need a global Context provider.

**Interview Line**

Outlet context passes data from a parent route directly to its nested route components through `<Outlet context={...}>`.

### Q. What is index route?

**Answer:**

An index route is the default child route rendered when the parent route matches exactly.

It has:

```js
index: true;
```

instead of a path.

**Example:**

```jsx
{
  path: "/dashboard",
  element:
    <DashboardLayout />,
  children: [
    {
      index: true,
      element:
        <DashboardHome />,
    },
    {
      path: "settings",
      element:
        <Settings />,
    },
  ],
}
```

When the user visits:

```text
/dashboard
```

React Router renders:

```jsx
<DashboardHome />
```

inside the parent outlet.

When visiting:

```text
/dashboard/settings
```

it renders `Settings`.

**Interview Line**

An index route is the default nested route shown when the parent URL matches without any additional child path.

### Q. What is relative routing?

**Answer:**

Relative routing means defining navigation relative to the current route instead of using a full absolute URL path.

**Example:**

If the current route is:

```text
/dashboard
```

you can write:

```jsx
<Link to="settings">Settings</Link>
```

instead of:

```jsx
<Link to="/dashboard/settings">Settings</Link>
```

Navigation APIs can also use relative paths:

```js
navigate("settings");
```

or:

```js
navigate("..");
```

Relative routing makes nested route structures easier to move and maintain.

**Interview Line**

Relative routing builds navigation from the current route hierarchy instead of hardcoding full absolute paths.

### Q. What is route ranking?

**Answer:**

Route ranking is the process React Router uses to decide which route is the best match when multiple routes could match the same URL.

More specific routes are ranked higher than less specific ones.

For example:

```text
/users/new
/users/:id
```

For:

```text
/users/new
```

React Router prefers the static route:

```text
/users/new
```

instead of treating `"new"` as an `id`.

Route specificity generally favors:

- Static segments
- Then dynamic segments
- Then wildcard or splat routes

This means route declaration order is less important than route specificity in modern React Router.

**Interview Line**

Route ranking lets React Router choose the most specific matching route rather than simply using declaration order.

### Q. How does React Router match routes?

**Answer:**

React Router compares the current location pathname against the configured route tree.

A route can contain:

- Static segments
- Dynamic parameters
- Nested segments
- Wildcards

**Example:**

```jsx
{
  path: "/users/:id",
  element:
    <UserDetails />,
}
```

For:

```text
/users/42
```

React Router matches:

```text
/users/:id
```

and extracts:

```js
id = "42";
```

With nested routes, React Router matches a branch of the route tree rather than only one standalone route.

**Interview Line**

React Router matches the current pathname against the route tree, ranks candidate branches, and renders the best matching nested route branch.

### Q. How do you handle query parameters using `useSearchParams`?

**Answer:**

`useSearchParams` provides access to the URL query string and a setter for updating it.

**Example URL:**

```text
/products?page=2&sort=price
```

Usage:

```jsx
import { useSearchParams } from "react-router-dom";

function Products() {
  const [searchParams, setSearchParams] = useSearchParams();

  const page = searchParams.get("page");

  const sort = searchParams.get("sort");

  return (
    <button
      onClick={() =>
        setSearchParams({
          page: "3",
          sort: sort ?? "price",
        })
      }
    >
      Next Page
    </button>
  );
}
```

Search params are useful for state that should be shareable through the URL.

**Interview Line**

`useSearchParams` reads and updates URL query parameters while keeping them synchronized with React Router navigation.

### Q. Difference between path params and search params

**Answer:**

Path params are part of the route structure.

**Example:**

```text
/users/42
```

Route:

```text
/users/:id
```

Access with:

```js
useParams();
```

Search params appear after `?`.

**Example:**

```text
/users?page=2&sort=name
```

Access with:

```js
useSearchParams();
```

Comparison:

| Path Params             | Search Params                      |
| ----------------------- | ---------------------------------- |
| Identify route resource | Represent optional filters/options |
| Part of pathname        | Part of query string               |
| `useParams()`           | `useSearchParams()`                |
| Often required          | Often optional                     |

**Interview Line**

Path params identify route resources, while search params represent optional URL state such as filters, sorting, or pagination.

### Q. How do you preserve query params during navigation?

**Answer:**

Read the current search string and include it in the new navigation destination.

**Example:**

```jsx
import { Link, useLocation } from "react-router-dom";

function ProductLink() {
  const location = useLocation();

  return (
    <Link
      to={{
        pathname: "/products/42",
        search: location.search,
      }}
    >
      Open Product
    </Link>
  );
}
```

With `navigate`:

```js
navigate({
  pathname: "/products/42",
  search: location.search,
});
```

This is useful for preserving:

```text
filters
sort
page
campaign params
```

**Interview Line**

Preserve query parameters by carrying the current `location.search` into the next route destination.

### Q. How do you lazy load route components?

**Answer:**

Route components can be lazy loaded so their JavaScript is downloaded only when the route is needed.

A common React approach is:

```jsx
import { lazy, Suspense } from "react";

const Dashboard = lazy(() => import("./Dashboard"));
```

Then:

```jsx
<Suspense fallback={<Loader />}>
  <Dashboard />
</Suspense>
```

With data-router APIs, routes can also define lazy route modules depending on the routing setup.

Lazy loading helps reduce the initial bundle size.

**Interview Line**

Lazy load route components with dynamic imports so route-specific code is downloaded only when that route is needed.

### Q. How do you handle route-level error UI?

**Answer:**

React Router data routers support route-level error boundaries through an `errorElement` or equivalent error boundary configuration.

**Example:**

```jsx
{
  path: "/products",
  element:
    <Products />,
  loader:
    productsLoader,
  errorElement:
    <RouteError />,
}
```

Inside the error UI:

```jsx
import { useRouteError } from "react-router-dom";

function RouteError() {
  const error = useRouteError();

  return <div>Something went wrong</div>;
}
```

Route-level error UI can isolate failures to one branch of the route tree.

**Interview Line**

Route-level error UI catches route rendering, loader, or action failures at the nearest configured route error boundary.

### Q. How do you handle unauthorized and forbidden routes separately?

**Answer:**

`401 Unauthorized` and `403 Forbidden` represent different situations.

#### Unauthorized

The user is not authenticated or their session is invalid.

Typical action:

```text
redirect to login
```

#### Forbidden

The user is authenticated but lacks permission.

Typical action:

```text
show access denied page
```

**Example:**

```jsx
if (!user) {
  return <Navigate to="/login" replace />;
}

if (!user.roles.includes("admin")) {
  return <ForbiddenPage />;
}
```

Do not treat every authorization failure as a login problem.

**Interview Line**

Handle unauthenticated users with login redirection, while authenticated users without permission should see a forbidden or access-denied state.

### Q. How do you redirect after login to the originally requested page?

**Answer:**

Store the requested location before redirecting the user to login.

**Example:**

```jsx
function ProtectedRoute({ children }) {
  const location = useLocation();

  if (!isAuthenticated) {
    return (
      <Navigate
        to="/login"
        replace
        state={{
          from: location,
        }}
      />
    );
  }

  return children;
}
```

After successful login:

```jsx
const location = useLocation();

const navigate = useNavigate();

const destination = location.state?.from?.pathname ?? "/dashboard";

navigate(destination, {
  replace: true,
});
```

You may also preserve the original search string and hash.

**Interview Line**

Store the originally requested location before redirecting to login, then navigate back to that location after authentication succeeds.

### Q. How do you handle breadcrumbs in React Router?

**Answer:**

Breadcrumbs should usually be derived from the matched route hierarchy instead of hardcoded independently on every page.

With modern React Router, matched routes can expose metadata that breadcrumb UI reads.

Conceptually:

```js
{
  path: "users",
  handle: {
    breadcrumb:
      "Users",
  },
}
```

A nested route:

```js
{
  path: ":id",
  handle: {
    breadcrumb:
      "User Details",
  },
}
```

Then the application can inspect the current matched route branch and render:

```text
Home > Users > User Details
```

This keeps breadcrumbs aligned with route structure.

**Interview Line**

Breadcrumbs are best derived from the current matched route hierarchy and route metadata rather than maintained separately.

### Q. How do you handle scroll restoration?

**Answer:**

Scroll restoration decides where the page should scroll after navigation.

For simple client routing, you can scroll to the top on pathname changes.

**Example:**

```jsx
function ScrollToTop() {
  const { pathname } = useLocation();

  useEffect(() => {
    window.scrollTo(0, 0);
  }, [pathname]);

  return null;
}
```

React Router data-router setups also provide built-in scroll restoration support.

This is useful for:

- Browser back/forward navigation
- Nested route transitions
- Preserving previous positions

**Interview Line**

Scroll restoration resets or restores scroll position during navigation, either manually or with React Router's built-in data-router support.

### Q. How do you block navigation when a form has unsaved changes?

**Answer:**

Track whether the form is dirty and intercept navigation while unsaved changes exist.

Conceptually:

```text
form changed
↓
dirty = true
↓
navigation attempted
↓
show confirmation
```

For browser refresh or tab close, the native `beforeunload` event may be used.

**Example:**

```jsx
useEffect(() => {
  function handleBeforeUnload(event) {
    if (!isDirty) {
      return;
    }

    event.preventDefault();
    event.returnValue = "";
  }

  window.addEventListener("beforeunload", handleBeforeUnload);

  return () => {
    window.removeEventListener("beforeunload", handleBeforeUnload);
  };
}, [isDirty]);
```

For in-app routing, use the routing API available in your React Router version for navigation blocking.

**Interview Line**

Prevent losing unsaved work by tracking dirty state and blocking or confirming both in-app navigation and browser unload events.

### Q. How do you handle nested protected routes?

**Answer:**

Wrap the protected route branch with one authentication or authorization layout instead of checking every child individually.

**Example:**

```jsx
function ProtectedLayout() {
  if (!isAuthenticated) {
    return <Navigate to="/login" replace />;
  }

  return <Outlet />;
}
```

Route configuration:

```jsx
{
  element:
    <ProtectedLayout />,
  children: [
    {
      path:
        "/dashboard",
      element:
        <Dashboard />,
    },
    {
      path:
        "/profile",
      element:
        <Profile />,
    },
  ],
}
```

Role-based protection can be added at another nested route level.

**Interview Line**

Nested protected routes are best handled by protecting a parent route layout so all child routes inherit the same access rule.

### Q. How do you organize routes in a large app?

**Answer:**

Large applications should organize routes by feature or domain instead of keeping one massive route file.

A typical structure might be:

```text
routes/
  rootRoutes.js

features/
  auth/
    authRoutes.js

  users/
    userRoutes.js

  products/
    productRoutes.js
```

Each feature can own:

- Route definitions
- Loaders
- Actions
- Error UI
- Lazy imports
- Route metadata

Shared layouts can sit at higher route levels.

A scalable route tree often looks like:

```text
Root Layout
├── Public Routes
├── Auth Routes
└── Protected App Layout
    ├── Users
    ├── Products
    └── Settings
```

**Interview Line**

Organize large React Router applications by feature, with each feature owning its route configuration and shared layouts defining common route boundaries.

## API Handling

### Q. How do you design an API service layer in React?

**Answer:**

An API service layer separates HTTP request logic from React components.

Instead of calling `fetch()` or Axios directly inside every component, create reusable modules for API communication.

**Example structure:**

```text
src/
  api/
    client.js
    userService.js
    orderService.js
```

A shared API client can handle common concerns:

```js
// client.js
import axios from "axios";

export const apiClient = axios.create({
  baseURL: "/api",
  timeout: 10000,
});
```

A feature service can focus on domain-specific endpoints:

```js
// userService.js
import { apiClient } from "./client";

export function getUsers() {
  return apiClient.get("/users");
}

export function getUser(id) {
  return apiClient.get(`/users/${id}`);
}
```

Components or query hooks then consume these services.

This keeps transport logic separate from presentation and makes the code easier to test and maintain.

**Interview Line**

An API service layer centralizes HTTP communication and keeps components focused on UI instead of request implementation details.

### Q. Why should API logic be separated from components?

**Answer:**

API logic should be separated because React components should primarily focus on rendering and user interaction.

If every component contains request logic, concerns become tightly coupled.

**Problems include:**

- Repeated request code
- Harder testing
- Inconsistent error handling
- Difficult token management
- Harder migration from `fetch` to Axios or another client

**Bad Example:**

```jsx
function Users() {
  useEffect(() => {
    fetch("/api/users")
      .then((res) => res.json())
      .then(setUsers);
  }, []);
}
```

A cleaner approach is:

```js
const users = await userService.getUsers();
```

Then components can focus on:

```text
loading
data
error
UI
```

**Interview Line**

Separating API logic improves reusability, consistency, testability, and keeps React components focused on presentation.

### Q. How do you handle request cancellation?

**Answer:**

With `fetch`, request cancellation is commonly handled using `AbortController`.

**Example:**

```jsx
useEffect(() => {
  const controller = new AbortController();

  async function load() {
    try {
      const response = await fetch("/api/users", {
        signal: controller.signal,
      });

      const data = await response.json();

      setUsers(data);
    } catch (error) {
      if (error.name !== "AbortError") {
        console.error(error);
      }
    }
  }

  load();

  return () => {
    controller.abort();
  };
}, []);
```

Cancellation is especially useful for:

- Search requests
- Route changes
- Component unmounting
- Rapid filter changes

Axios also supports the standard `AbortController` signal in modern versions.

**Interview Line**

Handle request cancellation with `AbortController` so obsolete requests do not continue consuming resources or update stale UI.

### Q. How do you handle stale API responses?

**Answer:**

A stale response is an old request result that arrives after a newer request has already completed.

**Example:**

```text
Search "r" starts
Search "react" starts
"react" finishes first
"r" finishes later
```

If both update state, the UI may incorrectly show results for `"r"`.

Solutions include:

- Cancel previous requests
- Track a request ID
- Compare the request input before updating state
- Use a query library that handles stale data

**Example with request ID:**

```js
let latestRequest = 0;

async function search(query) {
  const requestId = ++latestRequest;

  const data = await fetchSearch(query);

  if (requestId !== latestRequest) {
    return;
  }

  setResults(data);
}
```

**Interview Line**

Prevent stale responses from updating state by cancelling older requests or verifying that the response still belongs to the latest request.

### Q. How do you handle API race conditions?

**Answer:**

API race conditions happen when multiple requests run concurrently and complete in an unexpected order.

The most common strategies are:

1. Abort previous requests.
2. Track sequence IDs.
3. Ignore outdated responses.
4. Use server-state libraries with stale-response handling.

**Example:**

```js
let controller;

async function loadUser(id) {
  controller?.abort();

  controller = new AbortController();

  const response = await fetch(`/api/users/${id}`, {
    signal: controller.signal,
  });

  return response.json();
}
```

This ensures that when a newer request starts, the older one is cancelled.

**Interview Line**

Handle API race conditions by ensuring only the latest valid request is allowed to update application state.

### Q. How do you implement retry logic?

**Answer:**

Retry logic reruns a failed request a limited number of times.

Retries should normally be used only for transient failures such as:

- Network errors
- Temporary `5xx` responses
- Rate limits with proper delay

Avoid blindly retrying:

```text
400
401
403
```

because those usually require a different action.

**Example:**

```js
async function retry(fn, attempts = 3) {
  let lastError;

  for (let attempt = 0; attempt < attempts; attempt++) {
    try {
      return await fn();
    } catch (error) {
      lastError = error;
    }
  }

  throw lastError;
}
```

Production implementations should also consider delay and backoff.

**Interview Line**

Retry logic should be bounded and used only for transient failures, not permanent client or authorization errors.

### Q. How do you implement exponential backoff?

**Answer:**

Exponential backoff increases the wait time after each failed retry.

A common formula is:

```text
delay = baseDelay * 2^attempt
```

**Example:**

```js
function delay(ms) {
  return new Promise((resolve) => setTimeout(resolve, ms));
}

async function retryWithBackoff(fn, maxRetries = 3, baseDelay = 500) {
  let attempt = 0;

  while (attempt <= maxRetries) {
    try {
      return await fn();
    } catch (error) {
      if (attempt === maxRetries) {
        throw error;
      }

      const wait = baseDelay * 2 ** attempt;

      await delay(wait);

      attempt++;
    }
  }
}
```

In production, jitter is often added to avoid many clients retrying at exactly the same time.

**Interview Line**

Exponential backoff increases retry delay after each failure and often combines with jitter to reduce retry storms.

### Q. How do you handle optimistic UI updates?

**Answer:**

Optimistic updates change the UI immediately before the server confirms success.

**Example flow:**

```text
User clicks Like
↓
UI immediately increments count
↓
API request starts
↓
Success -> keep change
Failure -> rollback
```

**Example:**

```js
const previous = likes;

setLikes((count) => count + 1);

try {
  await likePost();
} catch {
  setLikes(previous);
}
```

This improves perceived responsiveness.

It works best when:

- Success is likely
- Rollback is easy
- Operation is reversible

**Interview Line**

Optimistic UI updates assume success and update the interface immediately, then rollback if the server request fails.

### Q. How do you handle pessimistic UI updates?

**Answer:**

A pessimistic update waits for the server to confirm success before changing the UI.

**Example flow:**

```text
User clicks Save
↓
Show loading state
↓
Send request
↓
Server succeeds
↓
Update UI
```

**Example:**

```js
setIsSaving(true);

try {
  const updated = await updateUser(formData);

  setUser(updated);
} finally {
  setIsSaving(false);
}
```

This approach is safer for operations where showing incorrect temporary state would be confusing or risky.

Examples include:

- Payment confirmation
- Permission changes
- Sensitive account updates

**Interview Line**

Pessimistic updates wait for server confirmation before changing UI state, prioritizing correctness over immediate feedback.

### Q. How do you handle API loading skeletons?

**Answer:**

A skeleton loader displays a placeholder shaped like the expected content while data is loading.

**Example:**

```jsx
if (isLoading) {
  return <UserCardSkeleton />;
}
```

A skeleton is often better than a generic spinner when the final layout is predictable.

Benefits include:

- Reduced perceived waiting time
- Better layout stability
- Clear visual expectation

The skeleton should roughly match the final component dimensions to avoid layout shift.

**Interview Line**

Use skeleton loaders to preserve layout and communicate expected content while API data is loading.

### Q. How do you handle empty API response?

**Answer:**

An empty response should be treated differently from an error.

**Example:**

```jsx
if (!isLoading && users.length === 0) {
  return <EmptyState message="No users found" />;
}
```

A good empty state may include:

- Explanation
- Suggested next action
- Create button
- Clear filters action

**Example:**

```text
No results found
Try changing your filters
```

Do not show an error when the request succeeded but returned no records.

**Interview Line**

Handle empty responses with a dedicated empty state, not an error state, because the request itself succeeded.

### Q. How do you handle partial API failure?

**Answer:**

Partial failure happens when part of the page loads successfully but one or more requests fail.

**Example:**

```text
Dashboard
├── Profile -> success
├── Orders -> success
└── Analytics -> failed
```

Instead of failing the entire page, isolate each section.

**Example:**

```jsx
<ProfileSection />

<OrdersSection />

<ErrorBoundary>
  <AnalyticsSection />
</ErrorBoundary>
```

For multiple API requests, each section can maintain its own:

```text
loading
success
error
```

state.

**Interview Line**

Handle partial API failure by isolating independent sections so one failed request does not break the entire screen.

### Q. How do you handle multiple parallel API calls?

**Answer:**

Independent requests can run in parallel using `Promise.all`.

**Example:**

```js
const [user, orders, notifications] = await Promise.all([fetchUser(), fetchOrders(), fetchNotifications()]);
```

This is faster than awaiting each request sequentially when they do not depend on each other.

However, `Promise.all` rejects if any request rejects.

If partial success is acceptable, use:

```js
Promise.allSettled();
```

**Example:**

```js
const results = await Promise.allSettled([fetchUser(), fetchOrders(), fetchNotifications()]);
```

**Interview Line**

Use `Promise.all` for independent requests that must all succeed, and `Promise.allSettled` when partial success is acceptable.

### Q. How do you handle dependent API calls?

**Answer:**

Dependent calls must run sequentially because the second request requires data from the first.

**Example:**

```js
const user = await fetchUserByEmail(email);

const orders = await fetchOrders(user.id);
```

The second call cannot start until:

```js
user.id;
```

is available.

With React Query, dependent queries often use:

```js
enabled: Boolean(userId);
```

Avoid unnecessary sequential requests when the backend can provide the required data in one endpoint.

**Interview Line**

Dependent API calls run sequentially because later requests require data produced by earlier requests.

### Q. How do you centralize API error handling?

**Answer:**

Centralize transport-level error handling in the shared API client.

**Example with Axios:**

```js
apiClient.interceptors.response.use(
  (response) => response,

  (error) => {
    const status = error.response?.status;

    if (status === 500) {
      logServerError(error);
    }

    return Promise.reject(normalizeError(error));
  },
);
```

Central handling is useful for:

- Normalizing errors
- Logging
- Token expiry
- Network failures
- Shared status handling

Feature-specific messages should still be handled near the UI.

For example:

```text
"Email already exists"
```

belongs to the form, not a generic interceptor.

**Interview Line**

Centralize common transport errors in the API client while keeping feature-specific error messages close to the feature UI.

### Q. How do you add auth token to every API request?

**Answer:**

With Axios, a request interceptor can attach an access token automatically.

**Example:**

```js
apiClient.interceptors.request.use((config) => {
  const token = authStore.getAccessToken();

  if (token) {
    config.headers.Authorization = `Bearer ${token}`;
  }

  return config;
});
```

With `fetch`, create a wrapper:

```js
async function apiFetch(url, options = {}) {
  return fetch(url, {
    ...options,

    headers: {
      ...options.headers,
      Authorization: `Bearer ${token}`,
    },
  });
}
```

For cookie-based authentication, the browser may send cookies automatically depending on origin and credentials configuration.

**Interview Line**

Attach access tokens centrally through an API client interceptor or request wrapper instead of repeating auth logic in every component.

### Q. How do you handle token refresh using Axios interceptor?

**Answer:**

A common pattern is to intercept `401` responses, refresh the access token once, then retry the original request.

**Example:**

```js
apiClient.interceptors.response.use(
  (response) => response,

  async (error) => {
    const originalRequest = error.config;

    if (error.response?.status === 401 && !originalRequest._retry) {
      originalRequest._retry = true;

      const response = await refreshToken();

      const newToken = response.data.accessToken;

      setAccessToken(newToken);

      originalRequest.headers.Authorization = `Bearer ${newToken}`;

      return apiClient(originalRequest);
    }

    return Promise.reject(error);
  },
);
```

In production, multiple simultaneous `401` responses should usually share one refresh request rather than each starting its own refresh.

**Interview Line**

Axios token refresh usually intercepts `401`, refreshes credentials once, updates the token, and retries the original request.

### Q. How do you prevent infinite token refresh loops?

**Answer:**

The refresh request itself can also fail with `401`.

If every `401` automatically triggers another refresh, the application can loop forever.

Common protections include:

1. Mark retried requests.
2. Do not intercept the refresh endpoint as a normal protected request.
3. Limit refresh attempts.
4. Log the user out when refresh fails.
5. Share one refresh promise across concurrent requests.

**Example:**

```js
if (error.response?.status === 401 && !originalRequest._retry) {
  originalRequest._retry = true;

  // refresh once
}
```

If refresh fails:

```js
clearAuth();
redirectToLogin();
```

Also ensure:

```text
/auth/refresh
```

does not recursively trigger the same refresh interceptor logic.

**Interview Line**

Prevent infinite refresh loops by marking retried requests, excluding the refresh endpoint, limiting retries, and logging out when refresh fails.

## Authentication & Authorization

### Q. Difference between authentication and authorization

**Answer:**

Authentication and authorization solve different security problems.

#### Authentication

Authentication answers:

```text
Who are you?
```

It verifies the identity of the user.

Examples include:

- Username and password
- OTP
- Social login
- Passkeys
- SSO

#### Authorization

Authorization answers:

```text
What are you allowed to do?
```

It determines which resources or actions the authenticated user can access.

**Example:**

A user may be authenticated successfully but still not be allowed to open:

```text
/admin
```

because they do not have the required role.

**Interview Line**

Authentication verifies identity, while authorization determines what an authenticated user is allowed to access or perform.

### Q. How do you persist login state in React?

**Answer:**

Login state should be restored from a durable authentication mechanism instead of relying only on in-memory React state.

A common architecture is:

```text
User logs in
↓
Server creates session or issues token
↓
Browser stores secure auth credential
↓
React stores current user in memory
```

For secure browser applications, authentication is often persisted using:

- Secure `HttpOnly` cookies
- Server-side sessions
- Short-lived access tokens with a secure refresh mechanism

React state can store the current user for UI rendering, but it should not be the only source of persistence.

**Example:**

```jsx
const [user, setUser] = useState(null);
```

The browser credential survives refresh, while React restores `user` from the server.

**Interview Line**

Persist login with a durable server-backed credential, then keep the current user in React state for UI purposes.

### Q. How do you restore auth state after page refresh?

**Answer:**

React state is lost after a full page refresh, so the application must restore authentication from persistent credentials.

A common flow is:

```text
App starts
↓
Check existing session/token
↓
Call /me or /session
↓
Server validates credential
↓
Restore current user
```

**Example:**

```jsx
useEffect(() => {
  async function restoreSession() {
    try {
      const response = await fetch("/api/me", {
        credentials: "include",
      });

      if (!response.ok) {
        setUser(null);
        return;
      }

      const user = await response.json();

      setUser(user);
    } finally {
      setAuthLoading(false);
    }
  }

  restoreSession();
}, []);
```

The app should usually show an auth-loading state until the check completes.

**Interview Line**

Restore auth after refresh by validating the persisted credential with the server and rebuilding the current-user state before rendering protected UI.

### Q. How do you handle private and public routes?

**Answer:**

Public routes are accessible without authentication.

Private routes require an authenticated user.

**Example:**

```jsx
function ProtectedRoute({ children }) {
  const { user, isLoading } = useAuth();

  if (isLoading) {
    return <Loader />;
  }

  if (!user) {
    return <Navigate to="/login" replace />;
  }

  return children;
}
```

Public routes can render normally:

```text
/login
/register
/about
```

Private routes may include:

```text
/dashboard
/profile
/settings
```

**Interview Line**

Public routes are always accessible, while private routes check authentication before rendering protected content.

### Q. How do you handle guest-only routes?

**Answer:**

Guest-only routes are routes that should be available only when the user is not authenticated.

Examples include:

```text
/login
/register
forgot-password
```

If an authenticated user visits them, redirect to the application.

**Example:**

```jsx
function GuestRoute({ children }) {
  const { user, isLoading } = useAuth();

  if (isLoading) {
    return <Loader />;
  }

  if (user) {
    return <Navigate to="/dashboard" replace />;
  }

  return children;
}
```

This prevents already logged-in users from repeatedly seeing login or signup screens.

**Interview Line**

Guest-only routes allow unauthenticated users but redirect authenticated users away from pages such as login or registration.

### Q. How do you handle role-based UI rendering?

**Answer:**

Role-based UI rendering hides or shows interface elements based on the current user's permissions or roles.

**Example:**

```jsx
function AdminActions({ user }) {
  if (!user.roles.includes("admin")) {
    return null;
  }

  return <button>Delete User</button>;
}
```

For more complex systems, permission checks are usually better than checking raw role names everywhere.

**Example:**

```js
can(user, "delete", "user");
```

UI checks improve usability by hiding unavailable actions.

They are not a security boundary.

**Interview Line**

Role-based UI rendering controls what the user sees, but real authorization must still be enforced by the backend.

### Q. Why should role checks also happen on the backend?

**Answer:**

Frontend code can be modified or bypassed by the user.

Even if a React button is hidden:

```jsx
{
  isAdmin && <DeleteButton />;
}
```

an attacker can still manually send:

```http
DELETE /api/users/10
```

using DevTools, scripts, Postman, or another client.

Therefore, the backend must validate:

- User identity
- Role
- Permission
- Resource ownership

before performing the action.

Frontend role checks are only for UX.

**Interview Line**

Backend authorization is mandatory because frontend role checks can be bypassed and do not protect server resources.

### Q. Where should access tokens be stored?

**Answer:**

There is no single answer for every architecture, but for browser applications, the safest design often minimizes JavaScript access to long-lived sensitive credentials.

Common options include:

- In-memory access token
- Secure `HttpOnly` cookie
- Short-lived token plus secure refresh cookie

A common pattern is:

```text
refresh credential -> HttpOnly cookie
access token -> short-lived, sometimes in memory
```

This reduces exposure of long-lived credentials to XSS.

The correct design depends on:

- Same-origin vs cross-origin architecture
- CSRF protections
- Backend capabilities
- Token lifetime

**Interview Line**

Prefer short-lived credentials and minimize JavaScript access to sensitive tokens; secure `HttpOnly` cookies are commonly used for long-lived session or refresh credentials.

### Q. What are the risks of storing tokens in localStorage?

**Answer:**

The main risk is XSS.

Any JavaScript running on the page can access:

```js
localStorage;
```

So if an attacker achieves script execution, they may read and exfiltrate stored tokens.

**Example:**

```js
const token = localStorage.getItem("accessToken");
```

Advantages of localStorage include:

- Easy persistence
- Easy access from JavaScript

But it is not appropriate for highly sensitive long-lived credentials.

Another issue is that tokens remain until explicitly removed.

**Interview Line**

The biggest localStorage token risk is XSS because injected JavaScript can read and steal stored credentials.

### Q. What are the risks of storing tokens in cookies?

**Answer:**

Cookies can reduce XSS exposure when configured with:

```text
HttpOnly
Secure
SameSite
```

However, cookies are automatically attached to matching requests, which can introduce CSRF risk depending on the authentication architecture.

Useful protections include:

- `SameSite`
- CSRF tokens
- Origin checks
- HTTPS
- Narrow cookie scope

**Example:**

```http
Set-Cookie:
session=abc;
HttpOnly;
Secure;
SameSite=Lax
```

Cookies are not automatically safer in every design; their security depends on correct configuration and server-side protections.

**Interview Line**

Cookies reduce direct token access from JavaScript with `HttpOnly`, but require careful CSRF protection and secure cookie configuration.

### Q. How do you handle logout securely?

**Answer:**

Logout should invalidate the user's authenticated session, not just hide the UI.

A secure flow is:

```text
User clicks logout
↓
Call logout endpoint
↓
Server invalidates session/refresh token
↓
Client clears local auth state
↓
Redirect to login
```

**Example:**

```js
await fetch("/api/logout", {
  method: "POST",
  credentials: "include",
});

clearAuthState();

navigate("/login", {
  replace: true,
});
```

If refresh tokens are used, they should be revoked or rotated appropriately on logout.

**Interview Line**

Secure logout invalidates the server-side session or refresh credential and then clears all client-side authentication state.

### Q. How do you clear user data after logout?

**Answer:**

Logout should remove user-specific state so the next user cannot see stale private data.

Clear or reset:

- Auth context
- Redux auth state
- User profile
- Query caches
- Sensitive local storage
- Session storage
- Feature-specific private state

**Example with React Query:**

```js
queryClient.clear();
```

Or selectively remove private queries.

With Redux:

```js
dispatch(resetAppState());
```

Be careful not to leave cached private API data visible after logout.

**Interview Line**

After logout, clear auth state and all user-specific cached or global data to prevent stale private information from leaking into the next session.

### Q. How do you handle session timeout?

**Answer:**

Session timeout should be enforced by the server, while the frontend reacts to it.

Common flow:

```text
Session expires
↓
API returns 401
↓
Try refresh if supported
↓
Refresh fails
↓
Clear auth
↓
Redirect to login
```

The UI may also warn the user before timeout in applications with strict session policies.

Avoid relying only on a client-side timer because users can manipulate frontend code and browser clocks.

**Interview Line**

The server should enforce session timeout, while the frontend handles expiry by refreshing when possible or logging the user out when the session is no longer valid.

### Q. How do you handle refresh token expiration?

**Answer:**

If the refresh token has expired, the application can no longer obtain a new access token.

The correct action is usually:

```text
Refresh request fails
↓
Clear authentication state
↓
Clear private caches
↓
Redirect to login
```

**Example:**

```js
try {
  await refreshToken();
} catch {
  clearAuth();
  queryClient.clear();

  navigate("/login", {
    replace: true,
  });
}
```

Do not keep retrying indefinitely.

**Interview Line**

When the refresh token expires, stop retrying, clear the authenticated session, and require the user to log in again.

### Q. How do you protect routes during auth loading state?

**Answer:**

Do not redirect immediately before authentication restoration finishes.

Otherwise, an already authenticated user may briefly be sent to login during app startup.

Use three states:

```text
loading
authenticated
unauthenticated
```

**Example:**

```jsx
function ProtectedRoute({ children }) {
  const { user, isLoading } = useAuth();

  if (isLoading) {
    return <FullPageLoader />;
  }

  if (!user) {
    return <Navigate to="/login" replace />;
  }

  return children;
}
```

This prevents redirect flicker and incorrect route decisions before the session check completes.

**Interview Line**

Protected routes should wait for auth restoration to finish before deciding whether to render content or redirect to login.

## Advanced React

### Q. What is reconciliation?

**Answer:**

Reconciliation is the process React uses to compare the previous Virtual DOM with the new Virtual DOM and determine the minimum changes needed to update the real DOM.

Why it matters:

- DOM updates are expensive
- React updates only what changed

Key idea:

React uses diffing + keys to optimize updates.

Interview one-liner:

“Reconciliation is how React efficiently updates the DOM by comparing virtual DOM trees.”

### Q. What is reconciliation overhead?

**Answer:**

Reconciliation overhead is the extra work React does to compare the new Virtual DOM with the previous Virtual DOM and decide what needs to change in the real DOM.

In React, whenever a component’s state or props change, React does not immediately replace the whole UI. Instead, it creates a new Virtual DOM tree and compares it with the old one. This comparison process is called reconciliation.

The time and resources spent during this comparison process are called reconciliation overhead.

Simple Explanation

React follows this process:

1. State or props change.
2. React re-renders the component.
3. React creates a new Virtual DOM.
4. React compares the new Virtual DOM with the old Virtual DOM.
5. React finds the minimum required changes.
6. React updates only the necessary parts of the real DOM.

The work done in steps 3 and 4 is reconciliation work. When this work becomes expensive, it is called reconciliation overhead.

Example

```jsx
function ProductList({ products }) {
  return (
    <ul>
      {products.map((product) => (
        <li key={product.id}>{product.name}</li>
      ))}
    </ul>
  );
}
```

If `products` changes, React will compare the previous list with the new list. It checks which items were added, removed, or updated.

For a small list, this is fast. But for a very large list, this comparison can take more time.

That extra comparison cost is reconciliation overhead.

Why Reconciliation Overhead Happens

Reconciliation overhead can increase when:

1. Too Many Components Re-render

```jsx
function App() {
  const [count, setCount] = useState(0);

  return (
    <>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <Header />
      <Sidebar />
      <ProductList />
      <Footer />
    </>
  );
}
```

When `count` changes, `App` re-renders. Child components may also re-render even if their data did not change.

This increases reconciliation work.

2. Large Lists Are Rendered

```jsx
{
  items.map((item) => <Item key={item.id} item={item} />);
}
```

If the list contains thousands of items, React has to compare many elements during reconciliation.

3. Incorrect Keys Are Used

```jsx
{
  items.map((item, index) => <li key={index}>{item.name}</li>);
}
```

Using array index as a key can confuse React when items are inserted, removed, or reordered.

React may do more work than necessary, increasing reconciliation overhead.

Better:

```jsx
{
  items.map((item) => <li key={item.id}>{item.name}</li>);
}
```

Stable keys help React identify which items actually changed.

4. New Object or Function References Are Created Every Render

```jsx
<Child data={{ name: "John" }} onClick={() => console.log("Clicked")} />
```

Every render creates a new object and a new function. React may treat them as changed props.

This can cause unnecessary child re-renders.

How to Reduce Reconciliation Overhead

1. Use Stable Keys

```jsx
{
  users.map((user) => <UserCard key={user.id} user={user} />);
}
```

Use unique and stable IDs instead of array indexes.

2. Use `React.memo`

```jsx
const UserCard = React.memo(function UserCard({ user }) {
  return <div>{user.name}</div>;
});
```

`React.memo` prevents a component from re-rendering when its props have not changed.

3. Use `useMemo`

```jsx
const filteredUsers = useMemo(() => {
  return users.filter((user) => user.active);
}, [users]);
```

`useMemo` helps avoid recalculating expensive values on every render.

4. Use `useCallback`

```jsx
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
```

`useCallback` helps keep function references stable between renders.

5. Split Components Properly

Instead of keeping too much state in a parent component, move state closer to where it is needed.

This prevents unrelated components from re-rendering.

6. Virtualize Large Lists

For very large lists, use libraries like `react-window` or `react-virtualized`.

Instead of rendering thousands of items, virtualization renders only the visible items.

Difference Between Rendering and Reconciliation

| Concept        | Meaning                                             |
| -------------- | --------------------------------------------------- |
| Rendering      | Creating the new UI description or Virtual DOM      |
| Reconciliation | Comparing the new Virtual DOM with the previous one |
| Commit phase   | Applying the actual changes to the real DOM         |

Final Answer

Reconciliation overhead is the performance cost React spends comparing the new Virtual DOM with the old Virtual DOM to find what changed.

It happens during React updates when state or props change. It can become expensive when many components re-render, large lists are used, unstable keys are given, or unnecessary new props are created.

To reduce reconciliation overhead, use stable keys, memoization, component splitting, and list virtualization.

### Q. What is Fiber architecture?

**Answer:**

Fiber is React’s new reconciliation engine introduced to make rendering interruptible and incremental.

What it solves:

- Long blocking renders
- Poor UI responsiveness

What Fiber enables:

- Pausing work
- Resuming work
- Prioritizing updates

Interview one-liner:

“Fiber is React’s internal architecture that enables incremental rendering and better responsiveness.”

### Q. What is concurrent rendering?

**Answer:**

Concurrent rendering allows React to work on multiple rendering tasks at the same time, pause them, and resume later.

Benefits:

- UI stays responsive
- High-priority updates (clicks, typing) are handled first

Important:

- It is opt-in
- Does NOT mean multi-threading

Interview one-liner:

“Concurrent rendering allows React to interrupt rendering to keep the UI responsive.”

### Q. What is hydration?

**Answer:**

Hydration is the process where React attaches event listeners to server-rendered HTML.

Used in:

- Server-Side Rendering (SSR)

Flow:

- Server sends HTML
- Browser shows content
- React hydrates it to make it interactive

Interview one-liner:

“Hydration makes server-rendered HTML interactive by attaching React logic on the client.”

### Q. Difference between CSR, SSR, and SSG

**Answer:**

| Feature        | CSR        | SSR           | SSG          |
| -------------- | ---------- | ------------- | ------------ |
| Rendering      | Browser    | Server        | Build time   |
| Initial load   | Slower     | Faster        | Fastest      |
| SEO            | ❌ Weak    | ✅ Good       | ✅ Excellent |
| Data freshness | Live       | Live          | Static       |
| Example use    | Dashboards | Content sites | Blogs        |

Interview summary line:

“CSR renders in the browser, SSR renders per request on the server, and SSG generates pages at build time.”

### Q. What is React Suspense?

**Answer:**

`Suspense` lets you wait for async operations (like lazy-loaded components or data) and show a fallback UI.

```jsx
<Suspense fallback={<Loader />}>
  <LazyComponent />
</Suspense>
```

Used for:

- Code splitting
- Data fetching (with frameworks)

Interview one-liner:

“`Suspense` improves UX by handling loading states declaratively.”

### Q. What are portals?

**Answer:**

Portals allow rendering a component outside its parent DOM hierarchy, while still being part of the React tree.

Common use cases:

- Modals
- Tooltips
- Dropdowns

Why needed:

Avoids CSS issues like overflow and z-index.

Interview one-liner:

“Portals render components outside the DOM hierarchy without breaking React’s event system.”

### Q. What is `forwardRef`?

**Answer:**

`forwardRef` allows a parent component to pass a ref to a child component.

Why needed:

Refs don’t pass automatically through components.

```jsx
const Input = React.forwardRef((props, ref) => <input ref={ref} />);
```

Interview one-liner:

“`forwardRef` allows refs to be forwarded to child components.”

### Q. What is controlled re-render?

**Answer:**

Controlled re-rendering means intentionally limiting when a component re-renders.

How it’s achieved:

- Memoization
- Splitting components
- Avoiding unnecessary state updates

Why important:

Reduces wasted renders → better performance.

Interview one-liner:

“Controlled re-rendering minimizes unnecessary updates to improve performance.”

### Q. What is batching in React?

**Answer:**

Batching is when React groups multiple state updates into a single re-render.

Before:

Multiple setState calls → multiple renders

Now (automatic batching):

- One render for multiple updates
- Works in async code too

Interview one-liner:

“Batching improves performance by reducing the number of re-renders.”

### Q. What are server components?

**Answer:**

Server Components run only on the server and send rendered output to the client.

Key benefits:

- Smaller JS bundle
- Secure access to server data
- Better performance

Restrictions:

- No hooks like useState
- No browser APIs

Interview one-liner:

“Server components run on the server to reduce client-side JavaScript and improve performance.”

### Q. What is React Strict Mode?

**Answer:**

Strict Mode is a development-only tool that helps identify potential problems.

What it does:

- Detects unsafe lifecycle usage
- Double-invokes effects
- Warns about deprecated APIs

Important:

- Does NOT affect production

Interview one-liner:

“Strict Mode helps detect bugs early by highlighting unsafe patterns in development.”

### What is React Fiber ?

**Answer:**

React Fiber is the reconciliation engine introduced in React 16 that improves rendering performance by breaking rendering work into small units and allowing it to be paused, prioritized, and resumed.

Why React Fiber Was Introduced

Before Fiber:

- Rendering was synchronous
- Large updates could block the UI
- No prioritization of updates

Fiber solves:

- UI lag
- Long blocking renders
- Poor animation performance

What Problem Does Fiber Solve?

Imagine:

- Large dashboard
- Many components updating
- User clicks a button

Old React:

👉 Entire update blocks UI until finished

With Fiber:

👉 Work is split into small tasks

👉 Can pause and continue later

👉 High-priority updates (like typing) run first

How React Fiber Works

Fiber divides rendering into two phases:

1️⃣ Render Phase (Reconciliation Phase)

- Calculates changes
- Can be paused
- Can be interrupted
- Creates Fiber tree

2️⃣ Commit Phase

- Applies changes to DOM
- Runs synchronously
- Cannot be interrupted

Key Concepts in Fiber

| Concept               | Meaning                   |
| --------------------- | ------------------------- |
| Fiber Node            | A unit of work            |
| Reconciliation        | Comparing old vs new tree |
| Incremental Rendering | Breaking work into chunks |
| Priority Scheduling   | Important updates first   |
| Time Slicing          | Pause & resume rendering  |

What is a Fiber Node?

Each component becomes a Fiber object.

It stores:

- Component type
- State
- Props
- Parent/child/sibling references
- Effect tags

Think of it as:

A lightweight virtual stack frame for each component.

Real-World Example

Typing in an input inside a heavy dashboard:

Without Fiber:

❌ UI freezes

With Fiber:

✅ Input stays responsive

✅ Background rendering continues

Important Interview Points

- Introduced in React 16
- Enables Concurrent features
- Makes rendering interruptible
- Improves animations and UX
- Not a feature you use directly — it's internal

Fiber vs Old Stack Reconciler

| Feature       | Old React   | Fiber       |
| ------------- | ----------- | ----------- |
| Rendering     | Synchronous | Incremental |
| Interruptible | ❌ No       | ✅ Yes      |
| Priority      | ❌ No       | ✅ Yes      |
| Performance   | Limited     | Better      |

One-Line Interview Summary

“React Fiber is the internal reconciliation algorithm that enables incremental, prioritized, and interruptible rendering to improve performance and responsiveness.”

### Q. What is React Helmet and React Helmet Async, and why are they used?

**Answer:**

```
React Helmet is a library used to dynamically manage changes to the document head in React applications (like <title>, <meta>, <link>, etc.).
```

It is mainly used for:

- SEO
- Dynamic page titles
- Social media meta tags

Why We Need It

In a React SPA:

- There is only one index.html
- Head content doesn’t automatically change per route

Without Helmet:

```html
<title>React App</title>
```

With Helmet:

Each route can have its own:

- Page title
- Description
- Open Graph tags
- Canonical URL

Basic Example (React Helmet)

```jsx
import { Helmet } from "react-helmet";

function Home() {
  return (
    <>
      <Helmet>
        <title>Home Page</title>
        <meta name="description" content="Welcome to home page" />
      </Helmet>

      <h1>Home</h1>
    </>
  );
}
```

When route changes → title updates automatically.

2️⃣ What is React Helmet Async?

Short Interview Answer

react-helmet-async is an improved version of React Helmet that supports server-side rendering (SSR) and avoids memory leaks in async environments.

Why Helmet Async Was Introduced

Regular react-helmet:

- Not fully safe for concurrent/async rendering
- Issues in SSR apps
- Not ideal for React 18 concurrent features

react-helmet-async:

- Thread-safe
- Supports SSR properly
- Recommended for modern apps

Example (Helmet Async Setup)

```jsx
import { Helmet, HelmetProvider } from "react-helmet-async";

function App() {
  return (
    <HelmetProvider>
      <Home />
    </HelmetProvider>
  );
}
```

Then inside component:

```jsx
<Helmet>
  <title>Dashboard</title>
</Helmet>
```

React Helmet vs Helmet Async

| Feature             | react-helmet | react-helmet-async |
| ------------------- | ------------ | ------------------ |
| SPA Support         | ✅ Yes       | ✅ Yes             |
| SSR Safe            | ⚠️ Limited   | ✅ Yes             |
| React 18 Compatible | ❌ Not ideal | ✅ Yes             |
| Recommended Today   | ❌ No        | ✅ Yes             |

Why It Is Used (Very Important for Interviews)

SEO Optimization

- Dynamic meta tags per route
- Google reads correct title/description

Social Sharing

```html
<meta property="og:title" content="Product Page" />
```

Dynamic Titles

Better UX:

```
Home → Dashboard → Profile
```

Title changes automatically.

Real-World Use Case

For example:

- /products/1
- /products/2

Each product page needs:

- Unique title
- Unique description
- Unique canonical link

Helmet solves this.

Important Interview Points

- Helmet only changes head tags
- It does not improve SEO fully in pure SPA (SSR needed for full SEO)
- For best SEO → use SSR frameworks (Next.js, Remix)
- Helmet Async is recommended for modern apps

One-Line Interview Summary

“React Helmet is used to dynamically manage document head tags like title and meta for SEO and better user experience, and Helmet Async is its improved SSR-safe version.”

#### ⭐ 30-Second Senior-Level Summary

“Reconciliation is how React updates the DOM efficiently. Fiber enables interruptible rendering, which powers concurrent rendering. Hydration makes server-rendered HTML interactive. CSR, SSR, and SSG differ in where and when rendering happens. Suspense handles async UI states, portals render outside the DOM tree, and forwardRef passes refs through components. Batching reduces re-renders, server components reduce client JS, and Strict Mode helps catch bugs during development.”

### Q. What is `useSyncExternalStore`?

**Answer:**

`useSyncExternalStore` is a React hook for safely subscribing to external stores that are managed outside React.

Examples include:

- Redux-like stores
- Browser APIs
- Custom event-based stores
- External mutable state containers

It takes:

```jsx
useSyncExternalStore(subscribe, getSnapshot, getServerSnapshot);
```

**Example:**

```jsx
function subscribe(callback) {
  window.addEventListener("online", callback);

  return () => {
    window.removeEventListener("online", callback);
  };
}

function getSnapshot() {
  return navigator.onLine;
}

function getServerSnapshot() {
  return true;
}

function Status() {
  const isOnline = useSyncExternalStore(subscribe, getSnapshot, getServerSnapshot);

  return <p>{isOnline ? "Online" : "Offline"}</p>;
}
```

**Interview Line**

`useSyncExternalStore` safely connects React to external mutable stores while preserving consistent snapshots during concurrent rendering.

### Q. When would you use `useSyncExternalStore`?

**Answer:**

Use it when React needs to subscribe to state that lives outside React's own state system.

Typical examples include:

- Custom global stores
- Browser event-based state
- External subscriptions
- Libraries exposing mutable stores
- SSR-compatible external state

For normal React-owned state, prefer:

```jsx
useState();
useReducer();
Context;
```

**Interview Line**

Use `useSyncExternalStore` when the source of truth lives outside React and components must subscribe to it safely.

### Q. What is `useImperativeHandle`?

**Answer:**

`useImperativeHandle` lets a component control which methods or values are exposed through a ref.

**Example:**

```jsx
const Input = forwardRef(function Input(props, ref) {
  const inputRef = useRef(null);

  useImperativeHandle(
    ref,
    () => ({
      focus() {
        inputRef.current?.focus();
      },
    }),
    [],
  );

  return <input ref={inputRef} />;
});
```

Parent:

```jsx
const inputRef = useRef(null);

inputRef.current?.focus();
```

**Interview Line**

`useImperativeHandle` lets a component expose a controlled imperative API through a ref instead of exposing internals directly.

### Q. When should you avoid `useImperativeHandle`?

**Answer:**

Avoid it when the same behavior can be represented declaratively with props and state.

Prefer:

```jsx
<Modal isOpen={isOpen} />
```

instead of:

```jsx
modalRef.current.open();
```

Imperative APIs increase coupling.

They are best reserved for:

- Focus
- Scroll
- Selection
- Media control
- Third-party imperative libraries

**Interview Line**

Avoid `useImperativeHandle` when declarative props and state can express the behavior more clearly.

### Q. What is imperative handle in React?

**Answer:**

An imperative handle is the object exposed to a parent through a ref.

For example:

```js
{
  (focus, reset, scrollToTop);
}
```

The child decides which operations are publicly available.

**Example:**

```jsx
useImperativeHandle(
  ref,
  () => ({
    reset() {
      setValue("");
    },

    focus() {
      inputRef.current?.focus();
    },
  }),
  [],
);
```

**Interview Line**

An imperative handle is the controlled object a child exposes through a ref for specific imperative operations.

### Q. What is controlled imperative behavior?

**Answer:**

Controlled imperative behavior means exposing only a small, intentional set of imperative commands instead of unrestricted access to component internals.

For example, a custom input may expose:

```text
focus()
reset()
select()
```

but not its internal state implementation.

**Example:**

```jsx
useImperativeHandle(
  ref,
  () => ({
    focus: () => inputRef.current?.focus(),
  }),
  [],
);
```

**Interview Line**

Controlled imperative behavior exposes a small intentional command API while keeping the component implementation encapsulated.

### Q. What is `flushSync`?

**Answer:**

`flushSync` forces React to synchronously process and commit state updates to the DOM.

It is imported from:

```js
react - dom;
```

**Example:**

```jsx
import { flushSync } from "react-dom";

flushSync(() => {
  setCount((prev) => prev + 1);
});
```

This bypasses normal scheduling and batching behavior.

**Interview Line**

`flushSync` forces React to synchronously commit updates instead of letting React schedule them normally.

### Q. When would you use `flushSync`?

**Answer:**

Use it only when imperative code must interact with the DOM immediately after a React update.

**Example:**

```jsx
flushSync(() => {
  setItems((prev) => [...prev, newItem]);
});

lastItemRef.current?.scrollIntoView();
```

The newly rendered DOM exists before the imperative call runs.

**Interview Line**

Use `flushSync` only when external imperative code requires the DOM to reflect a React update immediately.

### Q. Why should `flushSync` be avoided in normal cases?

**Answer:**

`flushSync` reduces React's ability to optimize scheduling.

It can:

- Break batching opportunities
- Increase synchronous work
- Block the main thread
- Reduce concurrent rendering benefits
- Hurt performance

Most code should let React schedule updates normally.

**Interview Line**

Avoid `flushSync` in normal code because it bypasses React's scheduling and can hurt performance.

### Q. What is automatic batching in React 18?

**Answer:**

Automatic batching means React groups multiple state updates into fewer renders.

In React 18+, batching also applies to more async contexts.

**Example:**

```jsx
setCount((prev) => prev + 1);

setName("John");
```

React can combine these into one render.

Batching can also happen inside:

```text
Promises
timeouts
native event handlers
async callbacks
```

when using a modern React root.

**Interview Line**

Automatic batching in React 18 groups multiple state updates from more async contexts into fewer renders.

### Q. How does React prioritize updates?

**Answer:**

React can assign different priorities to updates.

Urgent work includes:

```text
typing
clicking
input updates
```

Lower-priority work may include:

```text
large filtering
heavy list rendering
non-critical UI refresh
```

React can interrupt lower-priority rendering to handle urgent updates.

APIs such as:

```jsx
startTransition();
useTransition();
```

let developers mark updates as non-urgent.

**Interview Line**

React prioritizes updates so urgent interactions stay responsive while lower-priority rendering can be delayed or interrupted.

### Q. What are urgent and non-urgent updates?

**Answer:**

Urgent updates should appear immediately because they directly reflect user interaction.

Examples:

- Typing
- Checkbox changes
- Focus changes

Non-urgent updates can wait slightly.

Examples:

- Large filtering
- Search result rendering
- Expensive panel updates

**Example:**

```jsx
setInputValue(value);

startTransition(() => {
  setSearchQuery(value);
});
```

Here:

```text
inputValue -> urgent
searchQuery -> non-urgent
```

**Interview Line**

Urgent updates reflect immediate user input, while non-urgent updates can be deferred to preserve responsiveness.

### Q. What is tearing in concurrent rendering?

**Answer:**

Tearing happens when different parts of the UI read different versions of the same external state during one logical render.

**Example:**

```text
Component A reads value = 10
Store changes
Component B reads value = 11
```

The UI may temporarily become inconsistent.

`useSyncExternalStore` helps React avoid this problem with external stores.

**Interview Line**

Tearing is an inconsistent UI state where components render different versions of the same external data during concurrent rendering.

### Q. How does React avoid inconsistent UI during concurrent rendering?

**Answer:**

React renders from consistent state snapshots and commits completed trees atomically.

For React-owned state, one render sees a consistent snapshot.

For external stores, React can use:

```jsx
useSyncExternalStore;
```

to verify that the external snapshot remains valid.

React can also discard incomplete work and restart rendering if necessary.

**Interview Line**

React avoids inconsistent UI by using consistent snapshots, atomic commits, and coordinated external-store subscriptions.

### Q. What is Suspense boundary?

**Answer:**

A Suspense boundary defines fallback UI that React can display while part of the component tree is waiting.

**Example:**

```jsx
<Suspense fallback={<Loader />}>
  <Dashboard />
</Suspense>
```

Suspense is commonly used with:

- Lazy-loaded components
- Framework-integrated data loading
- Streaming server rendering

**Interview Line**

A Suspense boundary defines where React can temporarily show fallback UI while descendant content is waiting.

### Q. Can Suspense catch errors?

**Answer:**

No.

Suspense handles waiting or suspended rendering, not normal runtime failures.

Use an Error Boundary for errors.

**Example:**

```jsx
<ErrorBoundary>
  <Suspense fallback={<Loader />}>
    <Profile />
  </Suspense>
</ErrorBoundary>
```

**Interview Line**

Suspense handles pending work, while Error Boundaries handle rendering errors.

### Q. Difference between Suspense and Error Boundary

**Answer:**

They handle different states.

| Suspense                | Error Boundary              |
| ----------------------- | --------------------------- |
| Handles waiting         | Handles failure             |
| Shows loading fallback  | Shows error fallback        |
| Used for suspended work | Used for rendering errors   |
| Usually temporary       | Represents failure/recovery |

**Interview Line**

Suspense handles pending work, while Error Boundaries handle failed rendering.

### Q. What is streaming SSR?

**Answer:**

Streaming Server-Side Rendering sends HTML to the browser progressively instead of waiting for the whole page to finish rendering.

Traditional SSR:

```text
Render entire page
↓
Send complete HTML
```

Streaming SSR:

```text
Send page shell
↓
Send ready sections
↓
Stream slower sections later
```

It works well with Suspense boundaries and improves perceived load performance.

**Interview Line**

Streaming SSR sends server-rendered HTML progressively so ready sections can appear before slower parts finish.

### Q. What is selective hydration?

**Answer:**

Selective hydration means React can hydrate different areas of server-rendered HTML independently.

If a user interacts with one section, React can prioritize hydrating that area.

**Conceptually:**

```text
HTML arrives
↓
User clicks navbar
↓
Navbar hydration prioritized
↓
Other sections hydrate later
```

**Interview Line**

Selective hydration lets React prioritize hydration of important or interacted-with areas of a server-rendered page.

### Q. What are hydration mismatches?

**Answer:**

A hydration mismatch happens when the HTML generated on the server differs from what React renders on the client during the first hydration render.

**Example:**

Server:

```html
<p>10:00</p>
```

Client:

```html
<p>10:01</p>
```

React detects that the markup does not match.

**Interview Line**

A hydration mismatch occurs when server-rendered HTML differs from the client's first React render.

### Q. What causes hydration mismatch?

**Answer:**

Common causes include:

- `Date.now()`
- `Math.random()`
- Different locale formatting
- Browser-only APIs during render
- Conditional rendering based on `window`
- Client-only data unavailable on the server
- Invalid HTML nesting
- Third-party scripts modifying the DOM

**Example:**

```jsx
<p>{Math.random()}</p>
```

The server and browser usually produce different values.

**Interview Line**

Hydration mismatches are usually caused by non-deterministic or environment-specific differences between server and client rendering.

### Q. How do you fix hydration mismatch?

**Answer:**

Ensure the server and first client render produce the same markup.

Common fixes include:

- Move browser-only logic into effects
- Avoid random or time-based values during SSR render
- Use consistent server-provided data
- Use deterministic formatting
- Fix invalid HTML structure
- Delay client-only UI until after mount

**Example:**

```jsx
const [width, setWidth] = useState(null);

useEffect(() => {
  setWidth(window.innerWidth);
}, []);
```

**Interview Line**

Fix hydration mismatches by making the first client render deterministic and identical to the server output.

### Q. What are client components and server components?

**Answer:**

Server Components render on the server and do not send their component JavaScript to the browser by default.

Client Components run in the browser and support interactivity.

In frameworks such as Next.js App Router, Client Components are marked with:

```js
"use client";
```

Server Components can commonly:

- Fetch server data
- Access server-only resources
- Reduce client JavaScript

Client Components can use:

- `useState`
- `useEffect`
- Event handlers
- Browser APIs
- Interactive hooks

**Interview Line**

Server Components execute on the server for data and rendering, while Client Components provide browser-side interactivity.

### Q. Difference between client component and server component

**Answer:**

| Server Component                    | Client Component                |
| ----------------------------------- | ------------------------------- |
| Runs on server                      | Runs in browser                 |
| Can access server resources         | Can access browser APIs         |
| Cannot use interactive client hooks | Can use `useState`, `useEffect` |
| Less client JavaScript              | Ships JS for interaction        |
| Good for data fetching              | Good for interactive UI         |

A Server Component can render Client Components as part of its tree.

**Interview Line**

Server Components optimize server-side data and rendering, while Client Components handle stateful and interactive browser behavior.

### Q. When should you use a server component?

**Answer:**

Use a Server Component when the component mainly:

- Fetches server data
- Reads databases or server APIs
- Uses secrets
- Renders non-interactive content
- Does not need browser APIs
- Does not need client state or effects

**Examples:**

```text
product details
blog article
database-driven page
server-rendered dashboard data
```

**Interview Line**

Use Server Components for data-heavy, non-interactive UI that can run entirely on the server.

### Q. When should you use a client component?

**Answer:**

Use a Client Component when browser-side interactivity is required.

Typical reasons include:

- `useState`
- `useEffect`
- Event handlers
- Browser APIs
- DOM refs
- Interactive forms
- Client-side libraries

**Example:**

```js
"use client";

function Counter() {
  const [count, setCount] = useState(0);

  return <button onClick={() => setCount((prev) => prev + 1)}>{count}</button>;
}
```

**Interview Line**

Use Client Components only where browser interactivity, client state, effects, or browser APIs are required.

## Testing

### Q. How do you test React components?

**Answer:**

React components are usually tested by rendering them in a test environment, simulating user interactions, and asserting the visible behavior.

A common stack is:

```text
Jest or Vitest
+
React Testing Library
+
userEvent
+
MSW for API mocking
```

**Example:**

```jsx
render(<Counter />);

await user.click(
  screen.getByRole("button", {
    name: /increment/i,
  }),
);

expect(screen.getByText("1")).toBeInTheDocument();
```

The goal is to test what the user can observe rather than internal component implementation.

**Interview Line**

Test React components by rendering them, simulating realistic user behavior, and asserting visible outcomes.

### Q. What is Jest?

**Answer:**

Jest is a JavaScript testing framework commonly used for unit and integration testing.

It provides:

- Test runner
- Assertions
- Mocking
- Spies
- Fake timers
- Snapshot testing

**Example:**

```js
test("adds two numbers", () => {
  expect(2 + 2).toBe(4);
});
```

In React projects, Jest is often combined with React Testing Library.

**Interview Line**

Jest is a JavaScript testing framework that provides test execution, assertions, mocking, and utility APIs.

### Q. What is React Testing Library?

**Answer:**

React Testing Library is a library for testing React components from the user's perspective.

It encourages developers to query the UI by accessible elements such as:

- Role
- Label
- Text
- Placeholder

**Example:**

```jsx
render(<LoginForm />);

expect(
  screen.getByRole("button", {
    name: /login/i,
  }),
).toBeInTheDocument();
```

It discourages testing private component internals such as state variables or implementation-specific methods.

**Interview Line**

React Testing Library tests React UI through user-visible behavior instead of internal implementation details.

### Q. Unit testing vs Integration testing

**Answer:**

Unit testing checks a small isolated piece of logic.

Examples:

```text
utility function
reducer
custom validation function
small component
```

Integration testing checks multiple parts working together.

Examples:

```text
form + validation + API
router + protected route
Redux + component
```

Comparison:

| Unit Test       | Integration Test    |
| --------------- | ------------------- |
| Small scope     | Multiple modules    |
| Highly isolated | Tests collaboration |
| Usually faster  | More realistic      |
| More mocks      | Fewer mocks ideally |

React applications often benefit strongly from integration-style component tests.

**Interview Line**

Unit tests verify isolated logic, while integration tests verify that multiple parts work correctly together.

### Q. How do you mock API calls?

**Answer:**

API calls can be mocked at different levels.

Common options include:

- Mocking `fetch`
- Mocking Axios
- Mocking the API service layer
- Using MSW

A direct `fetch` mock:

```js
global.fetch = jest.fn(() =>
  Promise.resolve({
    ok: true,

    json: () =>
      Promise.resolve([
        {
          id: 1,
          name: "John",
        },
      ]),
  }),
);
```

For more realistic tests, MSW is often preferred because it intercepts network requests instead of replacing implementation functions.

**Interview Line**

API calls can be mocked directly, but MSW is often preferred because it mocks the network layer more realistically.

### Q. What is snapshot testing?

**Answer:**

Snapshot testing stores a serialized representation of rendered output and compares future test runs against it.

**Example:**

```jsx
const { asFragment } = render(<Button>Save</Button>);

expect(asFragment()).toMatchSnapshot();
```

If the rendered output changes, the snapshot test fails.

Snapshot tests can be useful for stable, predictable output, but they should not replace behavioral testing.

**Interview Line**

Snapshot testing compares current rendered output with a previously saved reference snapshot.

### Q. What should be tested in React components?

**Answer:**

Focus on behavior that matters to users and application requirements.

Useful things to test include:

- Visible content
- User interactions
- Form validation
- Conditional UI
- Loading states
- Error states
- Navigation
- API-driven behavior
- Accessibility behavior
- Permission-based rendering

**Example:**

```text
User enters invalid email
↓
Submits form
↓
Validation error appears
```

That is more useful than checking an internal state variable.

**Interview Line**

Test observable behavior, important user flows, and business rules rather than internal component implementation.

### Q. What should not be tested in React components?

**Answer:**

Avoid testing implementation details that users do not care about.

Examples include:

- Internal state variables
- Private functions
- Exact hook call counts
- Internal component structure
- React library internals
- Third-party library internals

**Bad Example:**

```text
Expect internal state "count" to equal 2
```

Better:

```text
Expect the UI to display "2"
```

Testing implementation details makes tests fragile during refactoring.

**Interview Line**

Do not test private implementation details; test the behavior those implementation details produce.

### Q. What is user-centric testing?

**Answer:**

User-centric testing verifies the application the way a real user interacts with it.

Instead of querying implementation details:

```js
container.querySelector(".submit-btn");
```

prefer:

```js
screen.getByRole("button", {
  name: /submit/i,
});
```

Then interact with it using realistic user events.

This makes tests more closely reflect actual usage.

**Interview Line**

User-centric testing focuses on what users can see, access, and interact with rather than how the component is implemented internally.

### Q. Why does React Testing Library encourage testing behavior?

**Answer:**

Behavior-based tests are more resilient to refactoring.

A component may change from:

```text
useState
```

to:

```text
useReducer
```

without changing what users experience.

If the test checks visible behavior, it continues to pass.

If it tests implementation details, it may fail even though the feature still works correctly.

**Interview Line**

React Testing Library encourages behavioral testing because user-visible behavior stays stable even when internal implementation changes.

### Q. Difference between `getBy`, `queryBy`, and `findBy`

**Answer:**

These query families behave differently.

#### `getBy`

Returns the element immediately.

Throws if it is not found.

```js
screen.getByText("Welcome");
```

Use when the element should already exist.

#### `queryBy`

Returns:

```js
null;
```

if the element is absent.

```js
screen.queryByText("Error");
```

Useful when asserting something does not exist.

#### `findBy`

Returns a Promise and waits for an element to appear.

```js
await screen.findByText("Loaded");
```

Useful for asynchronous UI.

**Interview Line**

Use `getBy` for present elements, `queryBy` for absence checks, and `findBy` for asynchronously appearing elements.

### Q. Difference between `fireEvent` and `userEvent`

**Answer:**

`fireEvent` dispatches a low-level DOM event directly.

**Example:**

```js
fireEvent.click(button);
```

`userEvent` simulates interactions closer to how a real user behaves.

**Example:**

```js
await user.click(button);
```

Typing with `userEvent` may trigger multiple realistic events such as:

```text
keydown
input
keyup
```

For most user interaction tests, `userEvent` is preferred.

**Interview Line**

`fireEvent` triggers individual DOM events, while `userEvent` simulates more realistic user interactions.

### Q. How do you test conditional rendering?

**Answer:**

Render the component in different states and assert whether expected UI appears or disappears.

**Example:**

```jsx
render(<UserPanel isLoggedIn={false} />);

expect(screen.getByText(/please login/i)).toBeInTheDocument();
```

Then test the authenticated case:

```jsx
render(<UserPanel isLoggedIn={true} />);

expect(screen.getByText(/welcome/i)).toBeInTheDocument();
```

For absence:

```js
expect(screen.queryByText(/please login/i)).not.toBeInTheDocument();
```

**Interview Line**

Test conditional rendering by providing different inputs and asserting which UI is present or absent.

### Q. How do you test form input changes?

**Answer:**

Use `userEvent` to type into form fields and assert the input value.

**Example:**

```jsx
const user = userEvent.setup();

render(<LoginForm />);

const emailInput = screen.getByLabelText(/email/i);

await user.type(emailInput, "john@example.com");

expect(emailInput).toHaveValue("john@example.com");
```

This tests the behavior from the user's perspective.

**Interview Line**

Test form input changes by typing with `userEvent` and asserting the resulting visible field value or validation behavior.

### Q. How do you test form submission?

**Answer:**

Fill the form, submit it through the same interaction a user would perform, then assert the result.

**Example:**

```jsx
const user = userEvent.setup();

render(<LoginForm onSubmit={handleSubmit} />);

await user.type(screen.getByLabelText(/email/i), "john@example.com");

await user.click(
  screen.getByRole("button", {
    name: /submit/i,
  }),
);

expect(handleSubmit).toHaveBeenCalled();
```

In integration tests, it is often better to assert API behavior or UI changes instead of only checking callback invocation.

**Interview Line**

Test form submission by interacting with the form naturally and asserting the resulting application behavior.

### Q. How do you test API loading state?

**Answer:**

Mock a request that remains pending long enough for the loading UI to appear.

**Example concept:**

```text
Render component
↓
API request starts
↓
Assert skeleton/spinner
↓
API resolves
↓
Assert final content
```

With MSW, you can delay the response.

Then assert:

```js
expect(screen.getByTestId("loading")).toBeInTheDocument();
```

Prefer accessible loading indicators when possible.

**Interview Line**

Test API loading state by delaying the mocked response and asserting the loading UI before the request completes.

### Q. How do you test API error state?

**Answer:**

Mock the API to return an error and assert that the component shows appropriate fallback UI.

**Example:**

```text
API returns 500
↓
Component catches error
↓
Error message appears
```

With MSW, configure the handler to return an error response.

Then:

```js
expect(await screen.findByText(/unable to load/i)).toBeInTheDocument();
```

Also test recovery behavior such as a retry button when relevant.

**Interview Line**

Test API error state by mocking a failed request and asserting the user-facing error or retry UI.

### Q. How do you test components using React Router?

**Answer:**

Render the component inside a router.

For tests, `MemoryRouter` is commonly used because it keeps navigation in memory.

**Example:**

```jsx
render(
  <MemoryRouter initialEntries={["/users/10"]}>
    <Routes>
      <Route path="/users/:id" element={<UserPage />} />
    </Routes>
  </MemoryRouter>,
);
```

This lets you test:

- Path params
- Links
- Navigation
- Route rendering
- Protected routes

**Interview Line**

Test router-dependent components inside a `MemoryRouter` or test router configured with the required route entries.

### Q. How do you test protected routes?

**Answer:**

Test both authenticated and unauthenticated states.

**Example scenarios:**

```text
Unauthenticated
→ navigate to /dashboard
→ redirected to /login
```

and:

```text
Authenticated
→ navigate to /dashboard
→ dashboard rendered
```

Provide the required auth context or mocked auth state in the test.

**Interview Line**

Protected-route tests should verify both access for authenticated users and redirection or denial for unauthenticated users.

### Q. How do you test components using Redux?

**Answer:**

Render the component with a real Redux store configured for the test.

**Example:**

```jsx
render(
  <Provider store={store}>
    <Counter />
  </Provider>,
);
```

For reusable setup, create a helper such as:

```js
renderWithProviders();
```

It is usually better to use the real slice reducer than to mock Redux itself.

This gives more realistic integration coverage.

**Interview Line**

Test Redux-connected components by rendering them with a test store and asserting user-visible behavior.

### Q. How do you test components using Context?

**Answer:**

Wrap the component with the required Context provider.

**Example:**

<!-- {% raw %} -->

```jsx
render(
  <AuthContext.Provider
    value={{
      user: {
        name: "John",
      },
    }}
  >
    <Profile />
  </AuthContext.Provider>,
);
```

<!-- {% endraw %} -->

Then assert the visible behavior.

For repeated tests, create a reusable provider wrapper.

**Interview Line**

Test Context consumers by wrapping them with the required provider values and asserting their rendered behavior.

### Q. How do you test custom hooks with React Testing Library?

**Answer:**

React Testing Library provides `renderHook` for testing hooks in isolation when needed.

**Example:**

```jsx
const { result } = renderHook(() => useCounter());

act(() => {
  result.current.increment();
});

expect(result.current.count).toBe(1);
```

For hooks that depend on providers, pass a wrapper.

**Example:**

```jsx
renderHook(() => useAuth(), {
  wrapper: AuthProvider,
});
```

**Interview Line**

Use `renderHook` for isolated hook tests and provide wrappers when the hook depends on Context or other providers.

### Q. How do you mock custom hooks?

**Answer:**

A custom hook can be mocked by mocking the module that exports it.

**Example:**

```js
jest.mock("./useAuth");
```

Then:

```js
useAuth.mockReturnValue({
  user: {
    name: "John",
  },
});
```

This is useful when you want to isolate a component from complex hook behavior.

However, over-mocking hooks can make tests less realistic.

Prefer testing with the real hook when the setup is simple and valuable.

**Interview Line**

Mock custom hooks through their module when isolation is necessary, but prefer real behavior when practical.

### Q. How do you mock child components?

**Answer:**

A child component can be mocked by replacing its module with a simple test component.

**Example:**

```js
jest.mock("./HeavyChart", () => () => <div>Chart Mock</div>);
```

This is useful when the child:

- Is very expensive
- Depends on browser APIs
- Uses third-party libraries
- Is unrelated to the behavior being tested

Avoid mocking every child because that can hide integration problems.

**Interview Line**

Mock child components only when their implementation is irrelevant or difficult to run in the test environment.

### Q. What is MSW?

**Answer:**

MSW stands for Mock Service Worker.

It is a library for mocking network requests at the request layer.

Instead of mocking:

```js
fetch();
```

directly, MSW intercepts requests and returns mocked responses.

**Example concept:**

```text
Component
↓
fetch("/api/users")
↓
MSW intercepts request
↓
Mock response returned
```

This makes tests more realistic because application request code does not need to change.

**Interview Line**

MSW mocks API behavior at the network layer, allowing components to use their real request code during tests.

### Q. Why is MSW useful for API mocking?

**Answer:**

MSW provides more realistic and maintainable API tests.

Benefits include:

- Same request code as production
- Mock success and failure states
- Mock delays
- Mock different status codes
- Reuse handlers across tests
- Works with `fetch` and Axios

It reduces coupling between tests and the implementation details of the HTTP client.

**Interview Line**

MSW is useful because it mocks network behavior instead of mocking specific HTTP client functions.

### Q. What are accessibility queries in React Testing Library?

**Answer:**

Accessibility-oriented queries select elements using information users and assistive technologies rely on.

Common examples include:

```js
getByRole();
getByLabelText();
getByPlaceholderText();
getByText();
```

The preferred query is often:

```js
getByRole();
```

**Example:**

```js
screen.getByRole("button", {
  name: /save/i,
});
```

This encourages semantic HTML and accessible UI design.

**Interview Line**

Accessibility queries locate elements through semantic roles, labels, and accessible names instead of implementation-specific selectors.

### Q. Why should snapshot testing not be overused?

**Answer:**

Large snapshots are difficult to review and can become noisy.

Common problems include:

- Developers update snapshots without understanding changes
- Tests fail for harmless markup changes
- Behavior is not clearly tested
- Large diffs hide important regressions

Behavior-based assertions are often more meaningful.

Instead of snapshotting an entire page:

```text
Assert button exists
Assert form submits
Assert error appears
```

These tests communicate intent more clearly.

**Interview Line**

Do not overuse snapshots because large snapshots are fragile and often provide less meaningful behavioral coverage.

### Q. How do you test accessibility in React?

**Answer:**

Accessibility testing combines semantic queries, behavioral checks, and automated accessibility tools.

Useful techniques include:

- Query by role
- Query by accessible name
- Test keyboard navigation
- Test focus behavior
- Check labels
- Check error announcements
- Use tools such as `jest-axe`

**Example:**

```js
expect(
  screen.getByRole("button", {
    name: /submit/i,
  }),
).toBeEnabled();
```

Automated tools help catch many issues, but they do not replace manual accessibility testing.

**Interview Line**

Test accessibility through semantic queries, keyboard and focus behavior, and automated tools while remembering that automation cannot catch every accessibility issue.

## Real-World / Scenario-Based

### Q. How would you optimize a slow React application?

**Answer:**

I optimize React apps by reducing unnecessary re-renders, improving bundle size, and optimizing data handling.

Key Techniques

- Use `React.memo`, `useMemo`, `useCallback`
- Code splitting (`React.lazy`)
- Avoid unnecessary state updates
- Virtualize large lists (e.g., react-window)
- Optimize API calls (debounce, cache)
- Use production build

🔥 One-liner

“I focus on minimizing re-renders, optimizing bundle size, and improving data fetching strategies.”

### Q. How do you handle API failures?

**Answer:**

I handle API failures using proper error handling, fallback UI, and retry strategies.

Approach

- `try/catch` or `.catch()`
- Show user-friendly error message
- Retry logic (exponential backoff)
- Use global error handling (interceptors)

Example

```js
try {
  const res = await fetch(url);
} catch (err) {
  setError("Something went wrong");
}
```

### Q. How do you manage authentication in React?

**Answer:**

Authentication is managed using tokens (JWT), stored securely, and protected routes.

Flow

1. Login → get token
2. Store token (cookie/localStorage)
3. Attach token in API headers
4. Protect routes

Tools

- Context API / Redux
- Axios interceptors

### Q. How do you handle role-based access?

**Answer:**

Role-based access is implemented by checking user roles and conditionally rendering routes/components.

Example

```jsx
if (user.role !== "admin") {
  return <Navigate to="/unauthorized" />;
}
```

Best Practice

- Centralized role config
- Backend validation (important!)

### Q. How do you improve SEO in React apps?

**Answer:**

For SEO, I use SSR or SSG and manage meta tags dynamically.

Techniques

- Use Next.js
- Use react-helmet-async
- Add meta tags (title, description)
- Use semantic HTML

### Q. How do you structure a large React project?

**Answer:**

I follow a modular and scalable folder structure.

Example Structure

```css
src/
  components/
  features/
  hooks/
  services/
  utils/
  pages/
  routes/
```

Best Practices

- Feature-based structure
- Reusable components
- Separate business logic

### Q. How do you handle environment variables?

**Answer:**

Environment variables are used for configuration and managed using `.env` files.

Example

```env
REACT_APP_API_URL=https://api.com
```

```js
process.env.REACT_APP_API_URL;
```

Best Practices

- Never expose secrets
- Use different env for dev/prod

### Q. How do you deploy a React app?

**Answer:**

React apps are deployed by building optimized static files and hosting them on a server/CDN.

Steps

```bash
npm run build
```

Platforms

- Vercel
- Netlify
- AWS S3 + CloudFront

### Q. How do you manage feature flags?

**Answer:**

Feature flags allow enabling/disabling features without redeploying.

Approaches

- Config-based flags
- Remote config (API)
- Tools like LaunchDarkly

```jsx
if (featureFlags.newUI) {
  return <NewUI />;
}
```

### Q. How do you debug a React app in production?

**Answer:**

I use logging, monitoring tools, and error tracking to debug production issues.

Tools

- Console logs (controlled)
- Error tracking:
  - Sentry
  - LogRocket

Techniques

- Source maps
- Network inspection
- Reproduce issues locally

🔥 Final Interview Summary (Power Answer)

“In production React apps, I focus on performance optimization, robust error handling, secure authentication, scalable architecture, and monitoring tools to ensure reliability and maintainability.”

### Q. How does crawling happens in SPA like ReactJS ?

**Answer:**

In a pure SPA, the server often sends a minimal HTML file and JavaScript renders content later. Search engine crawlers may need to execute JavaScript to see the page content.

Modern crawlers can execute JavaScript, but crawling can be slower and less reliable than SSR/SSG. For SEO-heavy pages, use SSR, SSG, pre-rendering, semantic HTML, meta tags, sitemap, and proper routing.

**Interview Line**

Crawling SPAs depends on JavaScript rendering, so SSR/SSG is preferred for SEO-critical pages.

### Q. A React page is slow while typing in search. How will you debug and fix it ?

**Answer:**

First reproduce and profile the issue using React DevTools Profiler. Common causes are filtering a large list on every keystroke, rendering too many rows, expensive calculations, and unnecessary child re-renders.

Fix it with debouncing, `useDeferredValue`, `useMemo`, list virtualization, moving state closer, and avoiding inline props.

### Q. A component keeps re-rendering unnecessarily. How will you find the cause ?

**Answer:**

Use React DevTools Profiler to check why the component rendered. Look for parent re-renders, context updates, changing object/function props, state updates inside effects, or missing memoization.

### Q. A list input loses focus after every keystroke. What could be the reason ?

**Answer:**

Input losing focus after every keystroke is often caused by changing the component `key`, defining components inside another component, recreating the input tree, or conditionally remounting the input.

### Q. A modal is hidden behind another element. How would you fix it ?

**Answer:**

A modal hidden behind another element is usually caused by stacking context, `z-index`, `overflow: hidden`, or DOM placement. Render modals using React Portal near `document.body` and manage z-index consistently.

### Q. A route works locally but shows 404 after deployment. Why ?

**Answer:**

Client-side routes work locally because the dev server falls back to `index.html`. In production, the server may look for a real file at that path and return 404.

Fix by configuring fallback/rewrite rules to serve `index.html` for SPA routes.

### Q. An API response updates old search results after a new search. How do you fix it?

**Answer:**

Old API responses can overwrite newer search results due to race conditions. Fix by canceling stale requests with `AbortController`, tracking request IDs, or using React Query with query keys.

### Q. A user clicks submit multiple times and duplicate records are created. How do you prevent it?

**Answer:**

Prevent duplicate submissions by disabling the button while submitting, guarding the submit handler, debouncing clicks, and ensuring backend idempotency where needed.

### Q. A protected route flashes before redirecting to login. How do you fix it?

**Answer:**

Protected route flashing happens when auth state is unknown initially. Show an auth loading state until session restore finishes, then render either protected content or redirect.

### Q. A context update re-renders the whole application. How do you optimize it?

**Answer:**

Optimize broad context updates by splitting context, memoizing provider values, separating state and dispatch, and moving frequently changing state into a more suitable store.

### Q. A React app has a very large bundle size. How do you reduce it?

**Answer:**

Reduce bundle size by analyzing the bundle, code splitting routes, lazy loading heavy components, replacing large libraries, tree shaking, removing unused dependencies, and loading charts/editors only when needed.

### Q. A large table freezes the browser. How do you optimize it?

**Answer:**

Optimize large tables with virtualization/windowing, pagination, memoized rows/cells, server-side sorting/filtering, and avoiding rendering thousands of DOM nodes at once.

### Q. A component works in development but fails in production. How do you debug it?

**Answer:**

Check minification issues, environment variables, API URLs, build-only warnings, source maps, browser compatibility, and differences between dev server and production hosting.

### Q. A hydration error appears in an SSR app. What are possible reasons?

**Answer:**

Hydration errors are often caused by server/client markup differences: dates, random IDs, browser-only APIs, conditional rendering, invalid HTML, different data, or locale/timezone differences.

### Q. A component fetches data twice in development. Why can this happen?

**Answer:**

In React Strict Mode development, effects may run twice to detect unsafe side effects. This does not happen the same way in production. Use proper cleanup, idempotent requests, or data-fetching libraries.

### Q. A child component does not update even after props change. What could be wrong?

**Answer:**

### Q. A memoized component still re-renders. What could be the reason?

**Answer:**

A memoized component still re-renders if props change by reference, context changes, internal state changes, or the custom comparison returns false.

### Q. A form with many fields feels slow. How would you improve it?

**Answer:**

Improve large form performance by using uncontrolled inputs, React Hook Form, splitting fields, memoizing field components, debouncing validation, and avoiding global state updates for every keystroke.

### Q. A dropdown is not keyboard accessible. How would you fix it?

**Answer:**

Make dropdowns keyboard accessible with proper roles, focus management, arrow-key navigation, Escape close, Enter/Space selection, labels, and ARIA attributes only where needed.

### Q. A React app needs offline support. What approach would you use?

**Answer:**

Offline support can be added with a Service Worker, caching static assets, background sync, IndexedDB for local data, and clear offline UI states.

### Q. A third-party script breaks the React page. How would you isolate the issue?

**Answer:**

Isolate third-party script issues by lazy loading it, wrapping dependent UI in error boundaries, loading it in a sandboxed iframe if possible, monitoring errors, and providing fallbacks.

## Design Pattern

### Q. Explain in detail about Design Pattern

📌 Definition

Design patterns are reusable solutions to commonly occurring problems in software design.

They are templates or best practices, not exact code.

🧩 Key Idea

“Don’t reinvent the wheel — use proven solutions.”

Design patterns help you write:

- Cleaner code
- Maintainable systems
- Scalable architecture

🏗️ Types of Design Patterns

1. 🏭 Creational Patterns (Object Creation)

Focus on how objects are created

- Singleton → Only one instance exists
- Factory → Creates objects without exposing logic
- Builder → Step-by-step object creation

```js
// Singleton Example
const Singleton = (function () {
  let instance;

  function createInstance() {
    return { name: "I am single" };
  }

  return {
    getInstance: function () {
      if (!instance) {
        instance = createInstance();
      }
      return instance;
    },
  };
})();
```

2. 🧱 Structural Patterns (Composition)

Focus on how objects are structured

- Adapter → Makes incompatible interfaces work together
- Decorator → Adds behavior without modifying code
- Facade → Simplifies complex systems

```js
// Decorator Example
function addLogging(fn) {
  return function (...args) {
    console.log("Calling function");
    return fn(...args);
  };
}
```

3. 🔄 Behavioral Patterns (Communication)

Focus on how objects interact

- Observer → Subscribing to changes (very common in JS)
- Strategy → Switch algorithms dynamically
- Command → Encapsulate actions

```js
// Observer Example
const observers = [];

function subscribe(fn) {
  observers.push(fn);
}

function notify(data) {
  observers.forEach((fn) => fn(data));
}
```

⚙️ Why Use Design Patterns?

- Solve recurring problems efficiently
- Improve code readability
- Enable scalability
- Promote best practices

📦 Real-World Examples

- React
  - Component pattern (composition)
  - Hooks → Observer-like behavior
- Redux
  - Uses Observer pattern
- JavaScript
  - Event listeners → Observer pattern

⚠️ Important Notes

- ❌ Not mandatory — use only when needed
- ❌ Overusing patterns = overengineering
- ❌ Not language-specific

💡 Best Practices

- Start simple → apply patterns when needed
- Understand the problem first, then choose pattern
- Don’t force patterns into small/simple code

### Q. Layout Components

**Answer:**

📌 Definition

Layout components are reusable UI components responsible for structuring and organizing the overall layout of an application. They define where content appears rather than what the content is.

🧠 Key Idea

Layout components control structure (positioning, spacing, alignment), not business logic or data.

🏗️ Common Types of Layout Components

1. Container / Wrapper

- Centers content and applies max width
- Adds padding/margin

```jsx
const Container = ({ children }) => <div className="max-w-7xl mx-auto px-4">{children}</div>;
```

2. Grid Layout

- Used for 2D layouts (rows + columns)

```html
<div className="grid grid-cols-3 gap-4">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>
```

3. Flex Layout

- Used for 1D layouts (row or column)

```html
<div className="flex justify-between items-center">
  <div>Left</div>
  <div>Right</div>
</div>
```

4. Page Layout

- Defines full page structure (header, footer, sidebar)

```jsx
const Layout = ({ children }) => {
  return (
    <>
      <Header />
      <main>{children}</main>
      <Footer />
    </>
  );
};
```

5. Sidebar Layout

- Used in dashboards or admin panels

```jsx
<div className="flex">
  <Sidebar />
  <main className="flex-1">Content</main>
</div>
```

6. Stack / Spacer Components

- Used for consistent spacing

```jsx
const Stack = ({ children }) => <div className="flex flex-col gap-4">{children}</div>;
```

⚙️ How Layout Components Work

1. Wrap content
2. Apply CSS (Flexbox, Grid, spacing)
3. Ensure consistency across pages
4. Promote reusability

📦 Real-World Example (React App Structure)

```jsx
<App>
  <Layout>
    <HomePage />
  </Layout>
</App>
```

```jsx
const Layout = ({ children }) => (
  <div className="min-h-screen flex flex-col">
    <Header />
    <div className="flex flex-1">
      <Sidebar />
      <main className="flex-1 p-4">{children}</main>
    </div>
    <Footer />
  </div>
);
```

🎯 Key Principles

- Separation of Concerns

  Layout ≠ Business logic

- Reusability

  Same layout across multiple pages

- Consistency

  Uniform spacing, alignment

- Responsiveness

  Works across screen sizes

⚠️ Common Mistakes

- Mixing layout + business logic
- Hardcoding spacing instead of reusable components
- Not making layouts responsive
- Deep nesting → hard to maintain

💡 Best Practices

- Use utility-first CSS (Tailwind) or design systems
- Create generic layout components (Container, Grid, Stack)
- Keep layouts dumb (presentational)
- Use props for flexibility

```jsx
const Container = ({ children, className = "" }) => <div className={`max-w-7xl mx-auto ${className}`}>{children}</div>;
```

### Q. Container Components

**Answer:**

Container components manage data, state, and business logic, then pass prepared props to presentational components.

```jsx
function UserContainer() {
  const { data } = useUser();
  return <UserProfile user={data} />;
}
```

### Q. Recursive Components

**Answer:**

Recursive components render themselves for nested data structures like comments, menus, folders, and tree views.

```jsx
function TreeNode({ node }) {
  return (
    <li>
      {node.name}
      <ul>
        {node.children?.map((child) => (
          <TreeNode key={child.id} node={child} />
        ))}
      </ul>
    </li>
  );
}
```

### Q. Composition Components

**Answer:**

Composition means building larger components by combining smaller components instead of creating one large component with many configuration props.

**Example:**

```jsx
function Card({ children }) {
  return <div className="card">{children}</div>;
}
```

Usage:

```jsx
<Card>
  <CardHeader />
  <CardBody />
  <CardFooter />
</Card>
```

This keeps components flexible because consumers decide what content is placed inside them.

Composition is generally preferred over inheritance in React.

**Interview Line**

Composition builds complex UI by combining smaller components through props and `children`, producing flexible and reusable APIs.

### Q. Partial Components

**Answer:**

A partial component is a preconfigured version of a reusable component where some props are already fixed.

This concept is similar to partial application.

**Example:**

Suppose we have:

```jsx
function Button({ variant, children, ...props }) {
  return (
    <button className={variant} {...props}>
      {children}
    </button>
  );
}
```

We can create specialized partial components:

```jsx
function PrimaryButton(props) {
  return <Button variant="primary" {...props} />;
}
```

Usage:

```jsx
<PrimaryButton>Save</PrimaryButton>
```

This reduces repeated configuration while preserving reuse.

**Interview Line**

A partial component is a preconfigured reusable component that fixes some props while leaving the remaining API customizable.

### Q. Compound Components

**Answer:**

Compound components are multiple related components that work together and share implicit state.

They provide an API similar to native HTML elements such as:

```html
<select>
  <option />
</select>
```

**Example:**

```jsx
<Tabs>
  <Tabs.List>
    <Tabs.Tab id="one">One</Tabs.Tab>

    <Tabs.Tab id="two">Two</Tabs.Tab>
  </Tabs.List>

  <Tabs.Panel id="one">First panel</Tabs.Panel>

  <Tabs.Panel id="two">Second panel</Tabs.Panel>
</Tabs>
```

The parent `Tabs` component manages shared state, while child components consume it through Context.

**Interview Line**

Compound components are related components that coordinate through shared internal state while exposing a flexible declarative API.

### Q. Error Handling

**Answer:**

Error handling in reusable React components should separate rendering failures from operational failures.

Typical categories include:

- Render errors
- API errors
- Validation errors
- Event-handler errors
- Async errors

Rendering failures can be isolated with Error Boundaries.

**Example:**

```jsx
<ErrorBoundary fallback={<ErrorFallback />}>
  <Dashboard />
</ErrorBoundary>
```

Async errors should normally be handled explicitly:

```jsx
try {
  await saveUser();
} catch (error) {
  setError("Unable to save");
}
```

Reusable components should expose clear error states instead of swallowing errors silently.

**Interview Line**

React error handling should isolate render failures with Error Boundaries and handle async or interaction errors explicitly near the affected feature.

### Q. Explain `as` props

**Answer:**

An `as` prop lets a reusable component change the underlying HTML element or component it renders.

**Example:**

```jsx
function Text({ as: Component = "span", children, ...props }) {
  return <Component {...props}>{children}</Component>;
}
```

Usage:

```jsx
<Text>
  Default span
</Text>

<Text as="h1">
  Heading
</Text>
```

This pattern improves flexibility while keeping shared styling or behavior.

**Interview Line**

The `as` prop lets one reusable component render as different underlying elements while preserving shared styling and behavior.

### Q. What is compound component pattern?

**Answer:**

The compound component pattern creates a family of components designed to be used together.

The parent usually owns shared state, while child components read or modify that state.

**Example:**

```jsx
<Accordion>
  <Accordion.Item id="one">
    <Accordion.Trigger>Question</Accordion.Trigger>

    <Accordion.Content>Answer</Accordion.Content>
  </Accordion.Item>
</Accordion>
```

Internally, Context is often used:

```jsx
const AccordionContext = createContext(null);
```

This avoids passing large numbers of props between related components.

**Interview Line**

The compound component pattern exposes coordinated subcomponents that share state internally but remain flexible in how they are composed.

### Q. When would you use compound components?

**Answer:**

Use compound components when several pieces of UI:

- Belong to one logical widget
- Need shared state
- Should be freely composed
- Would otherwise require many configuration props

Good use cases include:

```text
Tabs
Accordion
Menu
Select
Modal
Stepper
Dropdown
```

Compound components are less suitable when the API is extremely simple and one component with a few props is sufficient.

**Interview Line**

Use compound components for complex widgets whose related parts need shared state and flexible composition.

### Q. What is controlled component pattern?

**Answer:**

A controlled component receives its important state from the parent through props.

The parent owns the source of truth.

**Example:**

```jsx
function Input({ value, onChange }) {
  return <input value={value} onChange={onChange} />;
}
```

Parent:

```jsx
const [name, setName] = useState("");

<Input value={name} onChange={(event) => setName(event.target.value)} />;
```

This gives the parent full control over the value.

**Interview Line**

A controlled component receives state through props and reports changes through callbacks, making the parent the source of truth.

### Q. What is uncontrolled component pattern?

**Answer:**

An uncontrolled component manages its own internal state instead of receiving the current value from the parent.

**Example:**

```jsx
function Toggle({ defaultOpen = false }) {
  const [isOpen, setIsOpen] = useState(defaultOpen);

  return <button onClick={() => setIsOpen((prev) => !prev)}>{isOpen ? "Open" : "Closed"}</button>;
}
```

Native form inputs can also be uncontrolled using refs.

Uncontrolled components are simpler when the parent does not need to own every state change.

**Interview Line**

An uncontrolled component owns its internal state and optionally accepts initial values rather than requiring the parent to control every update.

### Q. What is state reducer pattern?

**Answer:**

The state reducer pattern lets consumers customize how a reusable component updates its internal state.

The component provides default behavior but allows the parent to intercept or modify transitions.

**Example concept:**

```jsx
function useToggle({ reducer = defaultReducer } = {}) {
  const [state, dispatch] = useReducer(reducer, {
    on: false,
  });

  return {
    state,
    dispatch,
  };
}
```

A consumer can provide a custom reducer to prevent or change specific transitions.

This pattern is useful for highly reusable components that need customizable behavior without exposing all internals.

**Interview Line**

The state reducer pattern lets consumers customize internal state transitions while the reusable component keeps its default state model.

### Q. What is provider pattern?

**Answer:**

The provider pattern uses React Context to make shared data or behavior available to descendant components.

**Example:**

```jsx
const ThemeContext = createContext(null);

function ThemeProvider({ children }) {
  const value = {
    theme: "dark",
  };

  return <ThemeContext.Provider value={value}>{children}</ThemeContext.Provider>;
}
```

Consumers can then use:

```jsx
const theme = useContext(ThemeContext);
```

This is useful for:

```text
theme
auth
feature settings
component families
```

**Interview Line**

The provider pattern uses Context to share state or services across a component subtree without prop drilling.

### Q. What is custom hook pattern?

**Answer:**

The custom hook pattern extracts reusable stateful logic into a function whose name starts with `use`.

**Example:**

```jsx
function useToggle(initial = false) {
  const [value, setValue] = useState(initial);

  const toggle = () => setValue((prev) => !prev);

  return {
    value,
    toggle,
  };
}
```

Usage:

```jsx
const { value, toggle } = useToggle();
```

Custom hooks reuse logic without reusing markup.

**Interview Line**

The custom hook pattern extracts reusable stateful behavior while allowing each component to control its own rendering.

### Q. What is prop getter pattern?

**Answer:**

The prop getter pattern provides functions that return the props consumers should spread onto specific elements.

It is common in headless component libraries.

**Example:**

```jsx
function useToggle() {
  const [on, setOn] = useState(false);

  function getButtonProps(props = {}) {
    return {
      ...props,

      "aria-pressed": on,

      onClick: (event) => {
        props.onClick?.(event);

        setOn((prev) => !prev);
      },
    };
  }

  return {
    on,
    getButtonProps,
  };
}
```

Usage:

```jsx
const { getButtonProps } = useToggle();

<button {...getButtonProps()}>Toggle</button>;
```

This allows reusable behavior while giving consumers control over markup.

**Interview Line**

The prop getter pattern returns merged element props so reusable behavior and consumer-provided props can work together safely.

### Q. What is slot pattern in React?

**Answer:**

The slot pattern lets a reusable component expose named areas where consumers provide specific content.

**Example:**

```jsx
function Card({ header, body, footer }) {
  return (
    <section>
      <header>{header}</header>

      <div>{body}</div>

      <footer>{footer}</footer>
    </section>
  );
}
```

Usage:

```jsx
<Card header={<Title />} body={<Content />} footer={<Actions />} />
```

Slots can also be implemented through compound components.

**Interview Line**

The slot pattern provides named composition areas so consumers can inject custom content into specific regions of a reusable component.

### Q. What is polymorphic component pattern?

**Answer:**

A polymorphic component can render different underlying element types while keeping a common API.

**Example:**

```jsx
function Box({ as: Component = "div", ...props }) {
  return <Component {...props} />;
}
```

Usage:

```jsx
<Box>
  Div
</Box>

<Box as="section">
  Section
</Box>

<Box
  as="button"
  type="button"
>
  Click
</Box>
```

This pattern is common in design systems.

**Interview Line**

A polymorphic component can render as different HTML elements or components while sharing the same abstraction and styling API.

### Q. What is the `as` prop pattern?

**Answer:**

The `as` prop pattern is a common implementation of polymorphic components.

The component receives the element type through:

```jsx
as;
```

**Example:**

```jsx
function Button({ as: Component = "button", children, ...props }) {
  return <Component {...props}>{children}</Component>;
}
```

Usage:

```jsx
<Button>
  Save
</Button>

<Button
  as="a"
  href="/docs"
>
  Docs
</Button>
```

When using TypeScript, the prop types should usually adapt based on the selected element.

**Interview Line**

The `as` prop pattern lets a reusable component change its rendered element while preserving shared component behavior.

### Q. How do you build reusable modal components?

**Answer:**

A reusable modal should separate:

- State
- Accessibility
- Overlay
- Dialog container
- Trigger
- Close behavior
- Content

A compound API is often a good fit.

**Example:**

```jsx
<Modal>
  <Modal.Trigger>Open</Modal.Trigger>

  <Modal.Content>
    <Modal.Title>Delete item?</Modal.Title>

    <Modal.Close>Cancel</Modal.Close>
  </Modal.Content>
</Modal>
```

Important behaviors include:

- Focus trapping
- Escape key handling
- Restoring focus
- `aria-modal`
- Backdrop click handling
- Portal rendering

For production applications, accessibility behavior is complex enough that established headless libraries are often preferable.

**Interview Line**

A reusable modal should separate structure from state and correctly handle focus, keyboard behavior, accessibility, and composition.

### Q. How do you build reusable table components?

**Answer:**

Reusable tables should separate data, column definitions, and rendering behavior.

**Example:**

```jsx
const columns = [
  {
    key: "name",
    header: "Name",
  },
  {
    key: "email",
    header: "Email",
  },
];
```

Then:

```jsx
<Table data={users} columns={columns} />
```

For advanced tables, keep optional concerns separate:

```text
sorting
filtering
pagination
selection
virtualization
```

Avoid creating one huge component with dozens of unrelated props.

Headless table logic can also expose state and handlers while leaving markup to the consumer.

**Interview Line**

Reusable tables should separate data and behavior from presentation and add features such as sorting or pagination through composable APIs.

### Q. How do you build reusable form input components?

**Answer:**

A reusable input should support normal form semantics while adding shared styling and validation UI.

**Example:**

```jsx
function FormInput({ label, error, id, ...inputProps }) {
  return (
    <div>
      <label htmlFor={id}>{label}</label>

      <input id={id} aria-invalid={Boolean(error)} {...inputProps} />

      {error && <p role="alert">{error}</p>}
    </div>
  );
}
```

It should still allow consumers to pass:

```text
value
onChange
name
type
placeholder
disabled
```

**Interview Line**

A reusable form input wraps shared labeling, styling, and error behavior while preserving standard input props and accessibility.

### Q. How do you build reusable dropdown components?

**Answer:**

A reusable dropdown should separate trigger, menu state, item behavior, and rendering.

A compound API works well.

**Example:**

```jsx
<Dropdown>
  <Dropdown.Trigger>Actions</Dropdown.Trigger>

  <Dropdown.Menu>
    <Dropdown.Item>Edit</Dropdown.Item>

    <Dropdown.Item>Delete</Dropdown.Item>
  </Dropdown.Menu>
</Dropdown>
```

Important concerns include:

- Keyboard navigation
- Focus management
- Escape behavior
- Outside click
- ARIA roles
- Positioning

For complex accessible dropdowns, headless libraries can reduce implementation risk.

**Interview Line**

A reusable dropdown should provide composable trigger and menu parts while correctly handling focus, keyboard interaction, and accessibility.

### Q. How do you build headless components?

**Answer:**

A headless component provides behavior and state without deciding visual styling.

It may expose:

- State
- Event handlers
- Prop getters
- Context
- Render props
- Custom hooks

**Example:**

```jsx
function useDisclosure() {
  const [isOpen, setIsOpen] = useState(false);

  return {
    isOpen,

    open: () => setIsOpen(true),

    close: () => setIsOpen(false),

    toggle: () => setIsOpen((prev) => !prev),
  };
}
```

Consumers decide the markup:

```jsx
const disclosure = useDisclosure();
```

This provides maximum styling freedom.

**Interview Line**

Headless components encapsulate behavior and accessibility while leaving visual rendering and styling to the consumer.

### Q. What is headless UI pattern?

**Answer:**

The headless UI pattern separates component behavior from presentation.

A headless abstraction may manage:

```text
state
keyboard behavior
focus
accessibility
events
```

while the application decides:

```text
HTML
CSS
layout
visual design
```

This is common in design systems where teams need consistent behavior but different visual styles.

Examples include:

```text
headless dropdown
headless tabs
headless modal
headless table
```

**Interview Line**

The headless UI pattern provides reusable behavior without imposing visual markup or styling.

### Q. What is separation of concerns in React components?

**Answer:**

Separation of concerns means organizing code so each part has a clear responsibility.

For example:

```text
Component -> rendering
Custom hook -> stateful logic
Service -> API communication
Utility -> pure transformation
Context/store -> shared state
```

**Example structure:**

```text
features/users/
  UserList.jsx
  useUsers.js
  userService.js
  userUtils.js
```

This does not mean every function must live in a separate file.

The goal is to avoid one component handling:

```text
UI
API calls
validation
routing
state logic
formatting
```

all at once.

**Interview Line**

Separation of concerns keeps rendering, business logic, data access, and shared state responsibilities independent so components remain easier to maintain and test.

## Accessibility

### Q. Why is accessibility important in React applications?

**Answer:**

Accessibility ensures people using keyboards, screen readers, or assistive technologies can use the application. It also improves usability, SEO, and legal compliance.

### Q. What are semantic HTML elements?

**Answer:**

Semantic HTML elements clearly describe meaning, such as `<button>`, `<nav>`, `<main>`, `<header>`, `<form>`, and `<label>`. They provide built-in accessibility.

### Q. How do you make a button accessible?

**Answer:**

Use a real `<button>`, provide clear text or `aria-label`, support keyboard interaction, avoid disabled-only hidden meaning, and show visible focus.

### Q. How do you make a modal accessible?

**Answer:**

An accessible modal should use `role="dialog"`, `aria-modal="true"`, a label, focus trap, Escape close, focus restoration, and should prevent background interaction.

### Q. How do you trap focus inside a modal?

**Answer:**

An accessible modal should use `role="dialog"`, `aria-modal="true"`, a label, focus trap, Escape close, focus restoration, and should prevent background interaction.

### Q. How do you restore focus after closing a modal?

**Answer:**

An accessible modal should use `role="dialog"`, `aria-modal="true"`, a label, focus trap, Escape close, focus restoration, and should prevent background interaction.

### Q. What are ARIA attributes?

**Answer:**

ARIA attributes add accessibility information when native HTML is not enough. `aria-label` gives an accessible name, `aria-labelledby` references an element as the label, and `aria-describedby` references extra descriptive text.

### Q. When should ARIA be avoided?

**Answer:**

ARIA should be avoided when semantic HTML can do the job. Native elements usually provide better accessibility with less code.

### Q. What is `aria-label`?

**Answer:**

ARIA attributes add accessibility information when native HTML is not enough. `aria-label` gives an accessible name, `aria-labelledby` references an element as the label, and `aria-describedby` references extra descriptive text.

### Q. What is `aria-labelledby`?

**Answer:**

ARIA attributes add accessibility information when native HTML is not enough. `aria-label` gives an accessible name, `aria-labelledby` references an element as the label, and `aria-describedby` references extra descriptive text.

### Q. What is `aria-describedby`?

**Answer:**

ARIA attributes add accessibility information when native HTML is not enough. `aria-label` gives an accessible name, `aria-labelledby` references an element as the label, and `aria-describedby` references extra descriptive text.

### Q. How do you make form errors accessible?

**Answer:**

Make form errors accessible by linking error text with inputs using `aria-describedby`, marking invalid fields with `aria-invalid`, and using `role="alert"` for important messages.

### Q. How do you make custom dropdowns accessible?

**Answer:**

Custom dropdowns need keyboard navigation, focus management, correct roles, active option indication, Escape close, and screen reader labels.

### Q. How do you handle keyboard navigation?

**Answer:**

Custom dropdowns need keyboard navigation, focus management, correct roles, active option indication, Escape close, and screen reader labels.

### Q. What is focus management?

**Answer:**

Focus management means intentionally moving and restoring focus during UI changes such as modals, route changes, dropdowns, and validation errors.

### Q. How do you test accessibility in React?

**Answer:**

Test accessibility with keyboard-only navigation, screen readers, React Testing Library accessibility queries, axe DevTools, Lighthouse, and jest-axe.

### Q. What tools can be used for accessibility testing?

**Answer:**

Test accessibility with keyboard-only navigation, screen readers, React Testing Library accessibility queries, axe DevTools, Lighthouse, and jest-axe.

## Build, Deployment & Environment

### Q. Difference between development build and production build

**Answer:**

Development build includes debugging support, warnings, source maps, and hot reloading. Production build is optimized, minified, and removes development-only checks.

### Q. Why is production build faster?

**Answer:**

Production build is faster because code is minified, dead code is removed, assets are optimized, and React development warnings are stripped.

### Q. What happens during `npm run build`?

**Answer:**

`npm run build` runs the configured build tool to compile JSX/TypeScript, bundle modules, optimize assets, minify code, and output static files for deployment.

### Q. What is source map?

**Answer:**

A source map maps minified production code back to original source code for debugging. In production, enable it carefully because it can expose source code.

### Q. Should source maps be enabled in production?

**Answer:**

A source map maps minified production code back to original source code for debugging. In production, enable it carefully because it can expose source code.

### Q. How do you configure environment variables in Vite?

**Answer:**

In Vite, public environment variables must start with `VITE_` and are accessed through `import.meta.env`.

```js
const apiUrl = import.meta.env.VITE_API_URL;
```

### Q. Difference between CRA and Vite

**Answer:**

Create React App and Vite are both tools used to start and build React applications, but they use different development architectures.

#### Create React App

CRA historically used Webpack under the hood.

It provides:

- Preconfigured React setup
- Webpack-based development server
- Babel-based transformation
- Production bundling

CRA is now considered legacy for starting new React applications.

#### Vite

Vite uses native ES modules during development and a modern bundling pipeline for production.

It provides:

- Very fast dev-server startup
- Fast Hot Module Replacement
- Modern plugin ecosystem
- Smaller configuration overhead

| CRA                              | Vite                          |
| -------------------------------- | ----------------------------- |
| Webpack-based                    | Native ESM during development |
| Slower startup on large projects | Very fast startup             |
| Legacy React starter             | Modern tooling                |
| Heavier dev bundling             | On-demand module serving      |

**Interview Line**

CRA is an older Webpack-based React starter, while Vite uses native ES modules and a modern build pipeline for much faster development.

### Q. Why is Vite faster than Create React App?

**Answer:**

Vite is faster mainly because it does not bundle the entire application before starting the development server.

Traditional bundlers often do:

```text
Read project
↓
Bundle dependencies and modules
↓
Start dev server
```

Vite instead serves application modules on demand through native ES modules.

```text
Start dev server
↓
Browser requests module
↓
Vite transforms only what is needed
```

Vite also pre-bundles dependencies efficiently and updates only changed modules during development.

**Interview Line**

Vite is faster because it serves source modules on demand during development instead of bundling the whole application before startup.

### Q. What is hot module replacement?

**Answer:**

Hot Module Replacement, or HMR, updates changed modules in a running application without performing a full browser reload.

**Example:**

You edit:

```jsx
function Button() {
  return <button>Save</button>;
}
```

The dev server detects the change and replaces only the affected module.

Benefits include:

- Faster feedback
- Preserved application state where possible
- No full-page refresh
- Better developer experience

React tooling often combines HMR with Fast Refresh.

**Interview Line**

HMR replaces changed modules in the running application without reloading the entire page.

### Q. What is tree shaking in React build?

**Answer:**

Tree shaking removes unused exports from the final production bundle.

It works best with statically analyzable ES modules.

**Example:**

```js
export function add() {}
export function subtract() {}
export function multiply() {}
```

If the application imports only:

```js
import { add } from "./utils";
```

the bundler may exclude the unused exports from the final production bundle.

**Interview Line**

Tree shaking removes unused module exports from production bundles, especially when code uses statically analyzable ES modules.

### Q. What is dead code elimination?

**Answer:**

Dead code elimination removes code that can never affect the final program.

Examples include:

- Unused functions
- Unreachable branches
- Development-only code
- Unused imports after optimization

**Example:**

```js
if (false) {
  console.log("Never runs");
}
```

A production optimizer can remove this branch.

Tree shaking is one form of dead-code removal focused on unused module exports.

**Interview Line**

Dead code elimination removes code that cannot affect the final program, reducing production bundle size.

### Q. How do you deploy React with client-side routing?

**Answer:**

A React Single Page Application usually uses client-side routing.

For example:

```text
/
/about
/products
/products/42
```

The server should usually return the application's main HTML file for these frontend routes.

```text
Request /products/42
↓
Server returns index.html
↓
React app starts
↓
React Router matches /products/42
↓
Product page renders
```

**Interview Line**

Deploy a React SPA by configuring the server to return `index.html` for client-side routes so React Router can handle the URL.

### Q. Why does page refresh show 404 after React deployment?

**Answer:**

This happens because client-side routing and server-side routing are different.

Suppose React Router supports:

```text
/products/42
```

During client navigation, React handles the route.

After a browser refresh, the server receives:

```http
GET /products/42
```

If the server looks for a real file or backend route at that path and cannot find one, it returns `404`.

The fix is to configure an SPA fallback to:

```text
index.html
```

**Interview Line**

A refresh returns 404 when the web server does not know about React's client-side routes and lacks an `index.html` fallback.

### Q. How do you fix routing issues on Netlify, Vercel, or Nginx?

**Answer:**

The usual fix is to configure SPA route rewrites so frontend paths resolve to `index.html`.

#### Netlify

A typical `_redirects` rule is:

```text
/*    /index.html   200
```

#### Vercel

For a static SPA, configure a rewrite so frontend routes resolve to:

```text
/index.html
```

For frameworks such as Next.js, routing is handled differently and you normally should not add a generic SPA fallback.

#### Nginx

A common configuration is:

```nginx
location / {
  try_files $uri $uri/ /index.html;
}
```

**Interview Line**

Fix SPA refresh 404s by configuring the hosting server to rewrite frontend routes to `index.html`.

### Q. What is CDN caching?

**Answer:**

CDN caching stores static files on geographically distributed edge servers.

Instead of every request reaching the origin:

```text
User
↓
Origin server
```

the request can be served from a nearby edge:

```text
User
↓
CDN edge
```

Common cached assets include:

- JavaScript
- CSS
- Images
- Fonts
- Static HTML in some architectures

Benefits include lower latency, reduced origin load, and faster global delivery.

**Interview Line**

CDN caching stores static assets at edge locations so users can download them from servers closer to them.

### Q. How do you cache static assets safely?

**Answer:**

Static assets should usually use long cache lifetimes only when their URLs change whenever their content changes.

For example:

```text
main.a8f72c.js
styles.91db2a.css
```

A typical policy for hashed assets is conceptually:

```http
Cache-Control: public, max-age=31536000, immutable
```

For `index.html`, use shorter caching or revalidation because it references the latest asset filenames.

A common strategy is:

```text
HTML -> short cache or revalidation
Hashed assets -> very long cache
```

**Interview Line**

Cache content-hashed assets for a long time, while keeping HTML short-lived so users can discover new build versions.

### Q. What is cache busting?

**Answer:**

Cache busting forces browsers or CDNs to download a new version of a file after it changes.

A common approach is adding a content hash to the filename.

**Example:**

Old build:

```text
app.abc123.js
```

New build:

```text
app.def456.js
```

Because the URL changes, the browser treats it as a different resource.

Another older technique is:

```text
app.js?v=2
```

Content-hashed filenames are usually more reliable in modern build systems.

**Interview Line**

Cache busting changes a resource URL when its content changes so browsers and CDNs fetch the new version instead of stale cache.

### Q. What is versioned build asset?

**Answer:**

A versioned build asset is a generated file whose filename or URL contains a version identifier.

Modern bundlers commonly use content hashes.

**Example:**

```text
assets/
  index-8f3a21.js
  vendor-a17c92.js
  style-09bf11.css
```

When file content changes, the hash changes.

This gives two major benefits:

1. New code gets a new URL.
2. Unchanged old assets can remain cached.

**Interview Line**

A versioned build asset includes a version or content hash in its URL so changed files invalidate cache while unchanged files remain cacheable.

## TypeScript with React

### Q. Why use TypeScript with React?

**Answer:**

TypeScript adds static type checking to React applications.

It helps catch mistakes before runtime and improves developer tooling.

Benefits include:

- Safer props
- Better autocomplete
- Easier refactoring
- Clearer component APIs
- Better handling of API data
- Safer hooks and state
- Better team collaboration

**Example:**

```tsx
type UserProps = {
  name: string;
  age: number;
};

function User({ name, age }: UserProps) {
  return (
    <p>
      {name} - {age}
    </p>
  );
}
```

Passing the wrong type is caught during development.

```tsx
<User name="John" age="25" />
```

Here `age` should be a number.

**Interview Line**

TypeScript improves React reliability by catching type errors early and making component contracts explicit.

### Q. How do you type props in React?

**Answer:**

Define a `type` or `interface` describing the component props.

**Example:**

```tsx
type ButtonProps = {
  label: string;
  disabled: boolean;
};

function Button({ label, disabled }: ButtonProps) {
  return <button disabled={disabled}>{label}</button>;
}
```

You can also type the props parameter directly, but a named type is usually easier to reuse and maintain.

**Interview Line**

Type React props by defining a `type` or `interface` and applying it to the component's props parameter.

### Q. Difference between `type` and `interface` for props

**Answer:**

Both can describe React props.

**Using `type`:**

```tsx
type UserProps = {
  name: string;
  age: number;
};
```

**Using `interface`:**

```tsx
interface UserProps {
  name: string;
  age: number;
}
```

Main differences:

- `interface` supports declaration merging.
- `type` supports unions, intersections, tuples, and more flexible compositions.
- Both support extension.

**Example with interface:**

```tsx
interface BaseProps {
  id: string;
}

interface UserProps extends BaseProps {
  name: string;
}
```

**Example with type:**

```tsx
type UserProps = BaseProps & {
  name: string;
};
```

For normal props, either is fine.

**Interview Line**

Both `type` and `interface` work for props; `interface` is strong for object extension, while `type` is more flexible for unions and composition.

### Q. How do you type optional props?

**Answer:**

Use the `?` operator.

**Example:**

```tsx
type CardProps = {
  title: string;
  subtitle?: string;
};
```

Now `subtitle` is optional.

Usage:

```tsx
<Card title="Profile" />
```

Inside the component:

```tsx
function Card({ title, subtitle }: CardProps) {
  return (
    <div>
      <h2>{title}</h2>

      {subtitle && <p>{subtitle}</p>}
    </div>
  );
}
```

**Interview Line**

Optional props are typed with `?`, making the property possibly `undefined`.

### Q. How do you type children prop?

**Answer:**

The common type is:

```tsx
React.ReactNode;
```

**Example:**

```tsx
type CardProps = {
  children: React.ReactNode;
};
```

Then:

```tsx
function Card({ children }: CardProps) {
  return <div>{children}</div>;
}
```

`React.ReactNode` allows values React can render, including:

- JSX
- Strings
- Numbers
- Arrays
- `null`
- `undefined`

**Interview Line**

Use `React.ReactNode` for children when a component should accept normal renderable React content.

### Q. How do you type event handlers?

**Answer:**

React provides event types for different elements and events.

**Example:**

```tsx
function handleClick(event: React.MouseEvent<HTMLButtonElement>) {
  console.log(event.currentTarget);
}
```

Usage:

```tsx
<button onClick={handleClick}>Save</button>
```

You can also type a handler directly:

```tsx
const handleClick: React.MouseEventHandler<HTMLButtonElement> = (event) => {
  console.log(event);
};
```

**Interview Line**

Type event handlers with React event types such as `React.MouseEvent` or handler aliases such as `React.MouseEventHandler`.

### Q. How do you type form events?

**Answer:**

The exact type depends on the form element and event.

For input change:

```tsx
function handleChange(event: React.ChangeEvent<HTMLInputElement>) {
  console.log(event.target.value);
}
```

For form submission:

```tsx
function handleSubmit(event: React.FormEvent<HTMLFormElement>) {
  event.preventDefault();
}
```

For a select:

```tsx
React.ChangeEvent<HTMLSelectElement>;
```

For textarea:

```tsx
React.ChangeEvent<HTMLTextAreaElement>;
```

**Interview Line**

Use the specific React event type matching both the event and DOM element, such as `ChangeEvent<HTMLInputElement>`.

### Q. How do you type `useState`?

**Answer:**

TypeScript can often infer the state type automatically.

**Example:**

```tsx
const [count, setCount] = useState(0);
```

Here `count` is inferred as:

```ts
number;
```

When the initial value is `null`, provide the type explicitly.

```tsx
type User = {
  id: number;
  name: string;
};

const [user, setUser] = useState<User | null>(null);
```

For union state:

```tsx
const [status, setStatus] = useState<"idle" | "loading" | "success">("idle");
```

**Interview Line**

Let TypeScript infer simple `useState` types, but provide explicit generics for nullable, union, or complex state.

### Q. How do you type `useRef`?

**Answer:**

For DOM references, pass the element type as a generic.

**Example:**

```tsx
const inputRef = useRef<HTMLInputElement>(null);
```

Then:

```tsx
inputRef.current?.focus();
```

For mutable non-DOM values:

```tsx
const timerRef = useRef<number | null>(null);
```

The type should represent the value stored in `current`.

**Interview Line**

Type `useRef` with the DOM element or mutable value type stored in `ref.current`.

### Q. How do you type custom hooks?

**Answer:**

Type the hook's inputs and return value like a normal TypeScript function.

**Example:**

```tsx
type UseToggleReturn = {
  value: boolean;
  toggle: () => void;
};

function useToggle(initial: boolean): UseToggleReturn {
  const [value, setValue] = useState(initial);

  const toggle = () => {
    setValue((prev) => !prev);
  };

  return {
    value,
    toggle,
  };
}
```

TypeScript can also infer return types, but explicit types can be useful for public hooks.

**Interview Line**

Type custom hooks like normal functions by defining their parameters and returned state, values, and callbacks.

### Q. How do you type API responses?

**Answer:**

Define a TypeScript type that represents the expected API response.

**Example:**

```tsx
type User = {
  id: number;
  name: string;
  email: string;
};
```

Then:

```tsx
async function fetchUser(id: number): Promise<User> {
  const response = await fetch(`/api/users/${id}`);

  if (!response.ok) {
    throw new Error("Request failed");
  }

  return response.json();
}
```

Important: TypeScript does not validate API data at runtime.

If the API is untrusted or external, runtime validation may still be needed.

**Interview Line**

Type API responses with interfaces or types, but use runtime validation when you cannot fully trust the server response.

### Q. How do you type generic components?

**Answer:**

Generic components allow the component to work with multiple data types while preserving type safety.

**Example:**

```tsx
type ListProps<T> = {
  items: T[];
  renderItem: (item: T) => React.ReactNode;
};
```

Component:

```tsx
function List<T>({ items, renderItem }: ListProps<T>) {
  return (
    <div>
      {items.map((item, index) => (
        <div key={index}>{renderItem(item)}</div>
      ))}
    </div>
  );
}
```

Usage:

```tsx
<List items={["A", "B"]} renderItem={(item) => <span>{item}</span>} />
```

TypeScript infers `T` as `string`.

**Interview Line**

Generic components use type parameters to remain reusable while preserving the exact type of their data and callbacks.

### Q. What is `React.FC`?

**Answer:**

`React.FC` means:

```ts
React.FunctionComponent;
```

It is a type used to describe a function component.

**Example:**

```tsx
type Props = {
  title: string;
};

const Header: React.FC<Props> = ({ title }) => {
  return <h1>{title}</h1>;
};
```

It types the component function and props.

However, it is optional.

**Interview Line**

`React.FC` is a TypeScript helper type for function components, but React components do not require it.

### Q. Should you use `React.FC`?

**Answer:**

You can use it, but it is not necessary.

Many teams prefer typing the props parameter directly.

**Preferred by many teams:**

```tsx
type Props = {
  title: string;
};

function Header({ title }: Props) {
  return <h1>{title}</h1>;
}
```

Advantages of avoiding `React.FC` include:

- Simpler function typing
- More explicit return behavior
- Less abstraction
- Easier generic components

`React.FC` is still valid and may fit a team's conventions.

**Interview Line**

`React.FC` is optional; directly typing props is often simpler and works better with generics and explicit component APIs.

### Q. How do you type component props with default values?

**Answer:**

Use optional props and assign defaults during destructuring.

**Example:**

```tsx
type ButtonProps = {
  label: string;
  variant?: "primary" | "secondary";
};
```

Then:

```tsx
function Button({ label, variant = "primary" }: ButtonProps) {
  return <button className={variant}>{label}</button>;
}
```

After destructuring, `variant` is treated as a defined value.

**Interview Line**

Type defaulted props as optional and assign their default values during parameter destructuring.

### Q. How do you type polymorphic components with `as` prop?

**Answer:**

Polymorphic components need generic types so props change based on the element passed through `as`.

**Example:**

```tsx
type BoxProps<T extends React.ElementType> = {
  as?: T;
  children?: React.ReactNode;
} & Omit<React.ComponentPropsWithoutRef<T>, "as" | "children">;
```

Component:

```tsx
function Box<T extends React.ElementType = "div">({ as, children, ...props }: BoxProps<T>) {
  const Component = as || "div";

  return <Component {...props}>{children}</Component>;
}
```

Usage:

```tsx
<Box as="a" href="/docs">
  Docs
</Box>
```

TypeScript knows that `href` is valid because `as="a"`.

**Interview Line**

Type polymorphic components with a generic `ElementType` and derive valid props from the selected `as` element.

### Q. How do you type Redux state and dispatch?

**Answer:**

In Redux Toolkit, infer the store types directly from the configured store.

**Example:**

```tsx
export const store = configureStore({
  reducer: {
    users: usersReducer,
  },
});
```

Create types:

```tsx
export type RootState = ReturnType<typeof store.getState>;

export type AppDispatch = typeof store.dispatch;
```

Then define typed hooks:

```tsx
export const useAppDispatch = useDispatch.withTypes<AppDispatch>();

export const useAppSelector = useSelector.withTypes<RootState>();
```

This prevents repeating generic types throughout the application.

**Interview Line**

Infer `RootState` and `AppDispatch` from the Redux store and expose typed selector and dispatch hooks.

### Q. How do you type Context API?

**Answer:**

Define the shape of the context value and use it as the generic for `createContext`.

**Example:**

```tsx
type AuthContextValue = {
  user: User | null;
  login: () => void;
  logout: () => void;
};
```

Create context:

```tsx
const AuthContext = createContext<AuthContextValue | undefined>(undefined);
```

Then create a custom hook:

```tsx
function useAuth() {
  const context = useContext(AuthContext);

  if (!context) {
    throw new Error("useAuth must be used inside AuthProvider");
  }

  return context;
}
```

This avoids unsafe default values and gives consumers a strongly typed API.

**Interview Line**

Type Context by defining the value shape, passing it to `createContext`, and using a custom hook to ensure safe consumption.
