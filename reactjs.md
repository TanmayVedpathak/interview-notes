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

### Q. How does React differ from Angular or Vue?

**Answer:**
| Feature | React | Angular | Vue |
| -------------- | ---------- | -------------- | ---------- |
| Type | Library | Full framework | Framework |
| Language | JavaScript | TypeScript | JavaScript |
| Learning Curve | Moderate | Steep | Easy |
| Data Binding | One-way | Two-way | Two-way |

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

### Q. What is a single-page application (SPA)?

**Answer:**

An SPA loads one HTML page and updates content dynamically without full page reloads.

How React helps:

- Uses client-side routing
- Faster navigation
- Better user experience

Examples:
Gmail, Facebook, Twitter

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

- eact.memo() → memoize components
- seCallback() → memoize functions
- seMemo() → memoize values
- void inline functions in JSX
- eep state minimal

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
{items.map(item => (
  <li key={item.id}>{item.name}</li>
))}
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
{isLoggedIn && <Dashboard />}

{isAdmin ? <Admin /> : <User />}
```

Interview line:

“React uses JavaScript conditions to control rendering.”

### Q. How do you render lists in React?

**Answer:**

Using the map() method.

```jsx
{users.map(user => (
  <User key={user.id} name={user.name} />
))}
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
const Dashboard = React.lazy(() => import('./Dashboard'));

<Suspense fallback={<Loader />}>
  <Dashboard />
</Suspense>
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
  setCount(c => c + 1);
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

### 🔥 30-Second Interview Summary (Hooks)

“Hooks allow functional components to manage state, side effects, and shared logic. They simplify code, improve reusability, and replace class-based lifecycle methods.”

## Forms & Events

### Q. What are controlled components?

**Answer:**

Controlled components are form elements whose value is controlled by React state.

```jsx
const [name, setName] = useState("");

<input value={name} onChange={e => setName(e.target.value)} />
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

<input ref={inputRef} />
```

Key points:

- Uses ref to access values
- Fewer re-renders
- Less control

Interview line:

“Uncontrolled components rely on the DOM for form state.”

### Q.  between controlled and uncontrolled components

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

const handleChange = e => {
  setFormData({
    ...formData,
    [e.target.name]: e.target.value
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
| Async logic | ❌ No                 | ✅ Yes               |
| Middleware  | ❌ No                 | ✅ Yes               |
| DevTools    | ❌ Limited            | ✅ Powerful          |
| Best for    | Simple global state  | Large, complex apps |

Interview conclusion:

“Context API solves prop drilling, Redux solves complex state management.”

### Q. What is a store in Redux?

**Answer:**

- The store is an object that:
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
(state, action) => newState
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
  fetchData().then(res =>
    dispatch({ type: "SUCCESS", payload: res })
  );
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
debounce(search, 300)
```

Throttling

- Executes function at fixed intervals
- Example: scroll, resize

```jsx
throttle(onScroll, 200)
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
    return this.state.hasError
      ? <Fallback />
      : this.props.children;
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
| Catches render errors    | ✅ Yes          | ❌ No      |
| Catches lifecycle errors | ✅ Yes          | ❌ No      |
| Catches async errors     | ❌ No           | ✅ Yes     |
| UI fallback              | ✅ Yes          | ❌ No      |
| React-specific           | ✅ Yes          | ❌ No      |

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
| SEO friendly   | ✅ Yes             | ❌ No             |
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
| Navigation           | ✅ Yes        | ✅ Yes           |
| Active state         | ❌ No         | ✅ Yes           |
| Styling active route | ❌ No         | ✅ Yes           |
| Common use           | Normal links | Menus / navbars |

Example:

```jsx
<NavLink to="/home" className={({isActive}) => isActive ? "active" : ""} />
```

Interview one-liner:

“NavLink provides active route styling, while Link is used for simple navigation.”

### ⭐ 30-Second Interview Summary

“React Router enables client-side routing in SPAs. BrowserRouter uses the history API with clean URLs, while HashRouter uses URL hashes. Dynamic routing allows parameters in routes. Route params can be passed via path, query, or state. Protected routes restrict access using authentication checks. useNavigate enables programmatic navigation, and NavLink is used when active route styling is required.”

### 🔥 Common Follow-ups Interviewers Ask

Difference between Navigate and useNavigate

How routing works in SPA

How to handle 404 routes

Nested routing use cases

Route-based code splitting

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

| Feature        | CSR        | SSR           | SSG         |
| -------------- | ---------- | ------------- | ----------- |
| Rendering      | Browser    | Server        | Build time  |
| Initial load   | Slower     | Faster        | Fastest     |
| SEO            | ❌ Weak     | ✅ Good        | ✅ Excellent |
| Data freshness | Live       | Live          | Static      |
| Example use    | Dashboards | Content sites | Blogs       |

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
const Input = React.forwardRef((props, ref) => (
  <input ref={ref} />
));
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

How would you optimize a slow React application?
How do you handle API failures?
How do you manage authentication in React?
How do you handle role-based access?
How do you improve SEO in React apps?
How do you structure a large React project?
How do you handle environment variables?
How do you deploy a React app?
How do you manage feature flags?
How do you debug a React app in production?

## Coding / Practical Questions

Build a counter using hooks
Implement debounce in React
Optimize a component with unnecessary re-renders
Create a custom hook
Implement infinite scrolling
Build a reusable modal component

## Extra

React fibre
React query
