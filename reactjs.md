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

🔹 How It Works

1. Browser loads index.html
2. JavaScript loads
3. Routing and rendering happen on the client
4. Only components update — not full page

🔹 Example

React apps created with CRA or Vite are SPAs.

🔹 Benefits

- Fast navigation
- Smooth UX
- Less server load

🔹 Drawbacks

- SEO challenges (without SSR)
- Slower first load (large JS bundle)

Examples:
Gmail, Facebook, Twitter

### Q. What is CSR (Client Side Rendering)?

**Answer:**

CSR means the browser downloads a minimal HTML file and uses JavaScript to render the page content on the client side.

🔹 Flow

```
Request → Empty HTML → JS loads → React renders UI
```

🔹 Used In

- React SPA
- Vue SPA
- Angular apps

🔹 Pros

- Fast navigation after first load
- Good for dashboards & web apps

🔹 Cons

- SEO not ideal
- Slow initial load
- JS-heavy

### Q. What is SSR (Server Side Rendering)?

**Answer:**

SSR means the server generates the complete HTML for each request and sends it to the browser.

🔹 Flow

```
Request → Server builds HTML → Send full page → Browser displays immediately
```

🔹 Example Framework

- Next.js
- Remix

🔹 Pros

- Better SEO
- Faster first paint
- Better performance on slow devices

🔹 Cons

- Higher server load
- Slightly slower navigation

### Q. What is SSG (Static Site Generation)?

**Answer:**

SSG generates HTML pages at build time and serves them as static files.

🔹 Flow

```
Build Time → HTML generated → CDN serves static file
```

🔹 Example

Blog site built using Next.js getStaticProps

🔹 Pros

- Very fast
- Excellent SEO
- CDN friendly

🔹 Cons

- Content not real-time
- Requires rebuild for updates

### Q. What is ISR (Incremental Static Regeneration)?

**Answer:**

ISR is a hybrid approach that allows static pages to be regenerated after deployment, without rebuilding the entire site.

🔹 Flow

```
Build → Serve static page → After interval → Regenerate in background
```

🔹 Example (Next.js)

```jsx
export async function getStaticProps() {
  return {
    props: { data },
    revalidate: 10, // regenerate after 10 seconds
  };
}
```

🔹 Pros

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

## Components & Rendering

### Q. What is component re-rendering?

**Answer:**

Component re-rendering means React re-executes a component function to calculate a new UI output when data changes.

👉 It does not always mean DOM updates—only changed parts are updated.

Interview line:

“Re-rendering is React recalculating the UI, not necessarily updating the DOM.”

### Q. What causes a component to re-render?

**Answer:**

- State change (setState, useState)
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

- React.memo() → memoize components
- useCallback() → memoize functions
- useMemo() → memoize values
- Avoid inline functions in JSX
- Keep state minimal

Example:

```jsx
export default React.memo(MyComponent);
```

Interview phrase:

“Memoization helps React skip unnecessary renders.”

### Q. What is key in React and why is it important?

**Answer:**

A key is a unique identifier used when rendering lists to help React track elements efficiently.

```jsx
{
  items.map((item) => <li key={item.id}>{item.name}</li>);
}
```

Why important:

- Improves performance
- Helps React correctly update elements

Interview line:

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

### Q. Can we use index as a key?

**Answer:**

⚠️ Not recommended, except for static lists.

Why index is bad:

- Order changes → wrong mapping
- Causes UI bugs

When it’s okay:

- List never changes
- No add/remove/reorder

Interview answer:

“Index as a key should be a last resort.”

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

Interview line:

“React uses JavaScript conditions to control rendering.”

### Q. How do you render lists in React?

**Answer:**

Using the map() method.

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

## Hooks (Very Important ⭐)

### Q. What are hooks?

**Answer:**

Hooks are functions that let you use state and other React features inside functional components.

Examples:

- useState → state
- useEffect → side effects
- useContext → context

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

### Q. What is useState?

**Answer:**

useState lets you add state to a functional component.

```jsx
const [count, setCount] = useState(0);
```

- Returns state value
- Returns state updater function
- Triggers re-render

### Q. How does useState work internally?

**Answer:**

Conceptually:

- React stores state in an internal array
- Each hook is tracked by call order
- setState schedules a re-render

Key idea:

“Hooks rely on call order, not names.”

### Q. What is useEffect?

**Answer:**

Answer:
useEffect handles side effects in functional components.

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

Interview line:

“useEffect replaces lifecycle methods in functional components.”

### Q. Explain useEffect dependency array

**Answer:**

| Dependency | Behavior                     |
| ---------- | ---------------------------- |
| `[]`       | Runs once (on mount)         |
| `[a, b]`   | Runs when `a` or `b` changes |
| No array   | Runs on every render         |

Important:

- Missing dependencies → bugs
- ESLint helps enforce correctness

### Q. Explain in detail useEffect, useLayoutEffect, and useInsertionEffect

**Answer:**

All three are side-effect hooks, but they run at different times in React’s rendering process.

🧠 First: React render flow (important)

- React renders JSX (virtual DOM)
- React updates the real DOM
- Browser paints the screen
- Effects run

The difference between these hooks is WHEN they run.

#### 1️⃣ useEffect (most common)

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
  fetchata();
}, []);
```

👍 Why it’s preferred

- Non-blocking
- Better performance
- Doesn’t delay UI rendering

⚠️ Downside

If it updates layout → user may see a flicker

##### 2️⃣ useLayoutEffect

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

#### 3️⃣ useInsertionEffect (advanced / rare)

📌 When does it run?

👉 Before DOM mutations happen

Order:

useInsertionEffect

→ DOM updates

→ useLayoutEffect

→ Paint

→ useEffect

🧩 Why it exists

- Created mainly for:
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

90% of the time → useEffect

Need DOM measurements / no flicker → useLayoutEffect

Building CSS-in-JS library → useInsertionEffect

⭐ Interview One-Line Answers

useEffect

Runs after paint and is used for non-blocking side effects.

useLayoutEffect

Runs before paint and is used for synchronous DOM measurements.

useInsertionEffect

Runs before DOM mutations and is used to inject styles safely.

### Q. Difference between useEffect, useLayoutEffect, and useInsertionEffect

**Answer:**

| Hook                 | When it runs        | Use case         |
| -------------------- | ------------------- | ---------------- |
| `useEffect`          | After paint         | API calls        |
| `useLayoutEffect`    | Before paint        | DOM measurements |
| `useInsertionEffect` | Before DOM mutation | CSS-in-JS        |

Interview line:

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

### Q. What is useRef?

**Answer:**

useRef creates a mutable reference that persists across renders without causing re-render.

```jsx
const inputRef = useRef(null);
```

Uses:

- Access DOM elements
- Store previous values
- Timers & intervals

### Q. Difference between useRef and useState

**Answer:**

| useRef       | useState         |
| ------------ | ---------------- |
| No re-render | Causes re-render |
| Mutable      | Immutable        |
| DOM access   | UI data          |

Interview one-liner:

“useRef stores values without affecting rendering.”

### Q. What is useMemo?

**Answer:**

useMemo memoizes expensive calculations.

```jsx
const value = useMemo(() => heavyCalc(a), [a]);
```

- Improves performance
- Avoids recomputation

### Q. When should you use useMemo?

**Answer:**

Use it when:

- Expensive calculation
- Large lists
- Value used as dependency
- Performance bottleneck

❌ Don’t overuse it.

Interview tip:

“useMemo is an optimization, not a default.”

### Q. What is useCallback?

**Answer:**

useCallback memoizes functions.

```jsx
const handleClick = useCallback(() => {
  setCount((c) => c + 1);
}, []);
```

Why needed:

- Prevents unnecessary re-renders
- Useful with React.memo

### Q. Difference between useCallback and useMemo

**Answer:**

| useCallback       | useMemo              |
| ----------------- | -------------------- |
| Memoizes function | Memoizes value       |
| Returns function  | Returns result       |
| Used in props     | Used in calculations |

Interview line:

“useCallback is useMemo for functions.”

### Q. What is useContext?

**Answer:**

useContext lets components consume context directly, without passing props.

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

- useContext
- Global state hooks

Interview line:

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

### What is useReducer ?

**Answer:**

useReducer is a React hook used for managing complex state logic using a reducer function and dispatching actions — similar to how Redux works.

Why useReducer Exists

When:

- State is complex (multiple related values)
- Next state depends on previous state
- Many state transitions exist
- Logic becomes messy with multiple useState

👉 useReducer provides a structured, predictable state flow.

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

👉 Cleaner than multiple useState.

### useReducer vs useState

**Answer:**

| Feature          | useState | useReducer  |
| ---------------- | -------- | ----------- |
| Simple state     | ✅       | ❌ Overkill |
| Complex logic    | ❌       | ✅          |
| Multiple updates | ❌       | ✅          |
| Predictability   | Medium   | High        |

📌 Interview Line

“useReducer is preferred when state logic becomes complex or depends heavily on previous state.”

### When Should You Use useReducer?

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

Interview line:

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

Interview line:

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

Interview line:

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

Interview line:

“Optimizing large forms is about minimizing re-renders and splitting responsibilities.”

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
- Allows state access via getState()
- Updates state via dispatch()
- Registers listeners via subscribe()

One store per app.

Interview one-liner:

“The Redux store holds the complete application state and manages updates through actions and reducers.”

### Q. Whar are actions?

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

dispatch() is used to send an action to the Redux store.

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

- React.memo → memoize components
- useMemo → memoize values
- useCallback → memoize functions

One-liner:

“Memoization avoids repeating expensive calculations by caching results.”

### Q. What is React.memo?

**Answer:**

React.memo is a higher-order component that prevents re-rendering if props have not changed.

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

React.memo vs PureComponent:

- PureComponent → class components
- React.memo → functional components

One-liner:

“PureComponent avoids re-renders by performing shallow comparison of props and state.”

### Q. What is code splitting in React?

**Answer:**

Code splitting means breaking the JavaScript bundle into smaller chunks that are loaded on demand.

Why it matters:

- Faster initial load
- Less JS sent to browser

How:

- Dynamic import()
- React.lazy

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

### ⭐ Final Interview Cheat Answer (30 seconds)

“React performance is optimized by reducing unnecessary re-renders using memoization, optimizing large lists with virtualization, loading code lazily, and controlling frequent updates using debouncing or throttling. Measuring performance with React Profiler is essential before optimizing.”

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

- constructor()
- render()
- componentDidMount()

2️⃣ Updating (state/props change)

- render()
- componentDidUpdate()

3️⃣ Unmounting (component removed)

- componentWillUnmount()

Interview one-liner:

“React components go through mounting, updating, and unmounting phases.”

### Q. What is componentDidMount used for?

**Answer:**

componentDidMount() runs once after the component is rendered to the DOM.

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

### 🔥 Common Interview Follow-ups (be ready)

❓ Why are error boundaries only class components?

❓ Can one error boundary catch errors in itself? (No)

❓ Where should error boundaries be placed? (Around risky components)

❓ Do error boundaries catch errors in event handlers? (No)

### ⭐ 30-Second Interview Summary

“Lifecycle methods allow us to run logic during mounting, updating, and unmounting of class components. componentDidMount is commonly used for API calls. Error boundaries are special class components that catch rendering errors using getDerivedStateFromError and componentDidCatch. Hooks cannot catch such errors, and error boundaries are different from try–catch, which only handles synchronous code.”

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

### Q. What is useNavigate?

**Answer:**

useNavigate is a hook used for programmatic navigation.

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

“useNavigate allows navigation programmatically instead of using links.”

### Q. Difference between Link and NavLink

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

“NavLink provides active route styling, while Link is used for simple navigation.”

### Q. Difference between Navigate and useNavigate

Short Answer

Navigate → component-based navigation

useNavigate → programmatic navigation (hook)

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

Use Navigate when rendering conditionally, useNavigate when reacting to events.

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

### What is history api and how it works in react routing ?

**Answer:**

The History API is a browser API that allows JavaScript to manipulate the browser’s session history (URL and navigation) without reloading the page.

React Router uses it to implement client-side routing in SPAs.

It’s part of modern browsers (HTML5) and provides methods like:

- history.pushState()
- history.replaceState()
- popstate event
- history.back()
- history.forward()

It allows changing the URL without refreshing the page.

Key Methods Explained

1️⃣ pushState()

Adds a new entry to browser history.

```js
history.pushState({ page: 1 }, "", "/dashboard");
```

✅ Changes URL

✅ Does NOT reload page

2️⃣ replaceState()

Replaces the current history entry.

```js
history.replaceState({}, "", "/login");
```

Used when you don’t want the user to go back.

3️⃣ popstate Event

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

1. User clicks <Link to="/dashboard" />
2. React Router calls history.pushState()
3. URL changes
4. No page reload
5. Router matches new route
6. Corresponding component renders

```
Click → pushState → URL change → Component render → No reload
Example in React
```

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

Suspense lets you wait for async operations (like lazy-loaded components or data) and show a fallback UI.

```jsx
<Suspense fallback={<Loader />}>
  <LazyComponent />
</Suspense>
```

Used for:

- Code splitting
- Data fetching (with frameworks)

Interview one-liner:

“Suspense improves UX by handling loading states declaratively.”

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

### Q. What is forwardRef?

**Answer:**

forwardRef allows a parent component to pass a ref to a child component.

Why needed:

Refs don’t pass automatically through components.

```jsx
const Input = React.forwardRef((props, ref) => <input ref={ref} />);
```

Interview one-liner:

“forwardRef allows refs to be forwarded to child components.”

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

### What is react helmet and helmet async and why it is use ?

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

🔹 Short Interview Answer

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

🔹 SEO Optimization

- Dynamic meta tags per route
- Google reads correct title/description

🔹 Social Sharing

```html
<meta property="og:title" content="Product Page" />
```

🔹 Dynamic Titles

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

### ⭐ 30-Second Senior-Level Summary

“Reconciliation is how React updates the DOM efficiently. Fiber enables interruptible rendering, which powers concurrent rendering. Hydration makes server-rendered HTML interactive. CSR, SSR, and SSG differ in where and when rendering happens. Suspense handles async UI states, portals render outside the DOM tree, and forwardRef passes refs through components. Batching reduces re-renders, server components reduce client JS, and Strict Mode helps catch bugs during development.”

## Testing

How do you test React components?
What is Jest?
What is React Testing Library?
Unit testing vs Integration testing
How do you mock API calls?
What is snapshot testing?

## Real-World / Scenario-Based

### Q. How would you optimize a slow React application?

**Answer:**

I optimize React apps by reducing unnecessary re-renders, improving bundle size, and optimizing data handling.

🔹 Key Techniques

- Use React.memo, useMemo, useCallback
- Code splitting (React.lazy)
- Avoid unnecessary state updates
- Virtualize large lists (e.g., react-window)
- Optimize API calls (debounce, cache)
- Use production build

🔥 One-liner

“I focus on minimizing re-renders, optimizing bundle size, and improving data fetching strategies.”

### Q. How do you handle API failures?

**Answer:**

I handle API failures using proper error handling, fallback UI, and retry strategies.

🔹 Approach

- try/catch or .catch()
- Show user-friendly error message
- Retry logic (exponential backoff)
- Use global error handling (interceptors)

🔹 Example

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

🔹 Flow

1. Login → get token
2. Store token (cookie/localStorage)
3. Attach token in API headers
4. Protect routes

🔹 Tools

- Context API / Redux
- Axios interceptors

### Q. How do you handle role-based access?

**Answer:**

Role-based access is implemented by checking user roles and conditionally rendering routes/components.

🔹 Example

```jsx
if (user.role !== "admin") {
  return <Navigate to="/unauthorized" />;
}
```

🔹 Best Practice

- Centralized role config
- Backend validation (important!)

### Q. How do you improve SEO in React apps?

**Answer:**

For SEO, I use SSR or SSG and manage meta tags dynamically.

🔹 Techniques

- Use Next.js
- Use react-helmet-async
- Add meta tags (title, description)
- Use semantic HTML

### Q. How do you structure a large React project?

**Answer:**

I follow a modular and scalable folder structure.

🔹 Example Structure

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

🔹 Best Practices

- Feature-based structure
- Reusable components
- Separate business logic

### Q. How do you handle environment variables?

**Answer:**

Environment variables are used for configuration and managed using .env files.

🔹 Example

```env
REACT_APP_API_URL=https://api.com
```

```jsz
process.env.REACT_APP_API_URL
```

🔹 Best Practices

- Never expose secrets
- Use different env for dev/prod

### Q. How do you deploy a React app?

**Answer:**

React apps are deployed by building optimized static files and hosting them on a server/CDN.

🔹 Steps

```bash
npm run build
```

🔹 Platforms

- Vercel
- Netlify
- AWS S3 + CloudFront

### Q. How do you manage feature flags?

**Answer:**

Feature flags allow enabling/disabling features without redeploying.

🔹 Approaches

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

🔹 Tools

- Console logs (controlled)
- Error tracking:
  - Sentry
  - LogRocket

🔹 Techniques

- Source maps
- Network inspection
- Reproduce issues locally

🔥 Final Interview Summary (Power Answer)

“In production React apps, I focus on performance optimization, robust error handling, secure authentication, scalable architecture, and monitoring tools to ensure reliability and maintainability.”

## Extra

### Q. React query

**Answer:**

## Design Pattern

### Layout Components

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
