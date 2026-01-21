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

```js
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

```js
<Welcome name="Tanmay" />
```

```js
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

```js
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

What is component re-rendering?
What causes a component to re-render?
How do you prevent unnecessary re-renders?
What is key in React and why is it important?
What happens if keys are not unique?
Can we use index as a key?
What is conditional rendering?
How do you render lists in React?
What is React.Fragment?
Difference between div and Fragment
What is lazy loading in React?

## Hooks (Very Important ⭐)

What are hooks?
Why were hooks introduced?
Rules of hooks
What is useState?
How does useState work internally?
What is useEffect?
Explain useEffect dependency array
Difference between useEffect, useLayoutEffect, and useInsertionEffect
How to mimic lifecycle methods using hooks?
What is useRef?
Difference between useRef and useState
What is useMemo?
When should you use useMemo?
What is useCallback?
Difference between useCallback and useMemo
What is useContext?
What is prop drilling and how do hooks solve it?
Custom hooks – what and why?
How do you share logic between components?

## Forms & Events

What are controlled components?
What are uncontrolled components?
Difference between controlled and uncontrolled components
How does React handle events?
Why does React use synthetic events?
How do you handle form validation?
How do you handle multiple inputs in a form?
How do you optimize large forms?

## State Management

What is lifting state up?
What is global state?
When should you use Context API?
Limitations of Context API
What is Redux?
Core principles of Redux
Redux vs Context API
What is a store in Redux?
What are actions?
What are reducers?
What is dispatch?
What are middleware in Redux?
What is Redux Thunk?
What is Redux Saga?
What is RTK (Redux Toolkit)?
Why Redux Toolkit is recommended?

## Performance Optimization

How do you optimize performance in React?
What is memoization?
What is React.memo?
How does PureComponent work?
Code splitting in React
How does lazy loading improve performance?
What is debouncing and throttling?
How do you optimize large lists?
What is virtualization?
What are common React performance mistakes?

## Lifecycle & Error Handling

What are lifecycle methods?
Phases of component lifecycle
What is componentDidMount used for?
What are error boundaries?
How do error boundaries work?
Can hooks catch errors?
Difference between error boundaries and try-catch

## Routing

What is React Router?
Difference between BrowserRouter and HashRouter
What is dynamic routing?
How do you pass params in routes?
How do you handle protected routes?
What is useNavigate?
Difference between Link and NavLink

## Advanced React

What is reconciliation?
What is Fiber architecture?
What is concurrent rendering?
What is hydration?
Difference between CSR, SSR, and SSG
What is React Suspense?
What are portals?
What is forwardRef?
What is controlled re-render?
What is batching in React?
What are server components?
What is React Strict Mode?

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
