# JavaScript & React Interview Questions and Answers (Detailed)

This guide covers essential JavaScript and React concepts, with detailed explanations, code examples, and extra topics often asked in interviews. Duplicates removed, concepts clarified, and practical examples included.

---

## JavaScript

### 1. What is Hoisting?
**Explanation:**  
Hoisting is JavaScript’s behavior of moving variable and function declarations to the top of their containing scope during the compilation phase. This means you can reference variables or functions before they are declared in code.

- **`var` declarations** are hoisted and initialized as `undefined`.
- **Function declarations** are hoisted with their definitions.
- **`let` and `const`** are hoisted but not initialized, leading to the Temporal Dead Zone (TDZ).

**Example:**
```js
console.log(foo); // undefined (hoisted, but not assigned)
var foo = 2;

bar(); // "Hello!" (function declaration is hoisted)
function bar() {
  console.log("Hello!");
};

console.log(baz); // ReferenceError (in TDZ)
let baz = 5;
```

---

### 2. What is the Temporal Dead Zone (TDZ)?
**Explanation:**  
TDZ is the period between entering a scope and the point at which a variable declared with `let` or `const` is initialized. Accessing the variable in this period results in a ReferenceError.

**Example:**
```js
{
  // TDZ starts here for 'x'
  // console.log(x); // ReferenceError
  let x = 10; // TDZ ends here
}
```

---

### 3. What is Event Bubbling?
**Explanation:**  
Event bubbling is the process where an event starts from the innermost (target) element and bubbles up to its parents in the DOM tree, triggering any event handlers on the way.

**Example:**
```html
<div id="parent">
  <button id="child">Click me</button>
</div>
<script>
document.getElementById('parent').addEventListener('click', () => {
  console.log('Parent clicked');
});
document.getElementById('child').addEventListener('click', () => {
  console.log('Child clicked');
});
</script>
```
*Clicking the button logs: "Child clicked" then "Parent clicked".*

---

### 4. `event.stopPropagation()` vs `event.preventDefault()`
- **`event.stopPropagation()`**: Prevents the event from bubbling up (or capturing down) the DOM tree.
- **`event.preventDefault()`**: Prevents the default action associated with the event (e.g., submitting a form).

**Example:**
```js
document.querySelector('form').addEventListener('submit', function(e) {
  e.preventDefault(); // Stops form from submitting
  alert('Form submit prevented!');
});

document.querySelector('button').addEventListener('click', function(e) {
  e.stopPropagation(); // Stops the event from bubbling up
  alert('Button click propagation stopped!');
});
```

---

### 5. What is the Event Loop?
**Explanation:**  
The event loop is a mechanism that allows JavaScript (single-threaded) to perform non-blocking operations by delegating tasks (like I/O, timers) to the browser or Node.js APIs. The event loop pulls tasks from the callback queue when the call stack is empty.

**Example:**
```js
console.log("Start");
setTimeout(() => console.log("Timeout"), 0);
Promise.resolve().then(() => console.log("Promise"));
console.log("End");

/* Output:
Start
End
Promise
Timeout
*/
```
*Promises are processed before `setTimeout` due to the microtask queue.*

---

### 6. What are Closures?
**Explanation:**  
A closure is a function that "remembers" its lexical scope even when executed outside that scope. Closures allow for private variables and function factories.

**Example:**
```js
function makeCounter() {
  let count = 0;
  return function() {
    count += 1;
    return count;
  }
}
const counter = makeCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```

---

### 7. What is Debounce?
**Explanation:**  
Debounce is a technique to limit how often a function is executed. A debounced function only runs after a specified time has elapsed since the last call. Useful for input fields, window resizing, etc.

**Example:**
```js
function debounce(func, delay) {
  let timeout;
  return function(...args) {
    clearTimeout(timeout);
    timeout = setTimeout(() => func.apply(this, args), delay);
  }
}

window.addEventListener('resize', debounce(() => {
  console.log('Resized!');
}, 500));
```

---

### 8. What are Arrow Functions?
**Explanation:**  
Arrow functions provide a shorter syntax for writing functions and do **not** have their own `this` context; they inherit `this` from their lexical scope.

**Example:**
```js
const add = (a, b) => a + b;

const obj = {
  value: 10,
  getValue: () => this.value // undefined, 'this' is not bound
};
```

---

### 9. Explain the `this` keyword and how to change its scope.
**Explanation:**  
`this` refers to the object that is executing the current function:
- In global scope: `this` is the global object (window in browsers)
- In a method: `this` is the object before the dot
- In a function: `this` is undefined in strict mode, otherwise the global object

**Changing `this`:**
- `call` and `apply` methods: invoke function with explicit `this`
- `bind`: create a new function with bound `this`
- Arrow functions: inherit `this` from parent scope

**Example:**
```js
function greet() { console.log(this.name); }
const user = { name: "Alice" };
greet.call(user); // "Alice"

const boundGreet = greet.bind(user);
boundGreet(); // "Alice"
```

---

### 10. Explain `Array.prototype.reduce`
**Explanation:**  
`reduce` executes a reducer function on each element of the array, accumulating a single result.

**Example:**
```js
const arr = [1, 2, 3, 4];
const sum = arr.reduce((acc, curr) => acc + curr, 0); // 10
```

---

### 11. What are Prototypes?
**Explanation:**  
Every JS object has a prototype, from which it inherits methods and properties. Prototypes enable inheritance.

**Example:**
```js
function Person(name) { this.name = name; }
Person.prototype.sayHello = function() {
  console.log(`Hello, ${this.name}!`);
};
const bob = new Person('Bob');
bob.sayHello(); // Hello, Bob!
```

---

### Additional Important JS Topics

#### 12. What is `async`/`await`?
**Explanation:**  
`async` and `await` are syntax for working with Promises in a readable, synchronous-like manner.

**Example:**
```js
async function fetchData() {
  const response = await fetch('https://api.github.com');
  const data = await response.json();
  return data;
}
```

#### 13. What is the difference between `==` and `===`?
- `==` checks for value equality with type coercion.
- `===` checks for both value and type equality.

#### 14. Explain the difference between `null` and `undefined`.
- `undefined`: Variable declared but not assigned a value.
- `null`: Explicitly set to "no value".

---

## React

### 1. What is the Virtual DOM?
**Explanation:**  
The Virtual DOM is an in-memory representation of the real DOM elements generated by React components. When a component state changes, a new Virtual DOM is created and compared (diffed) with the previous one. Only the changed parts are updated in the real DOM, making UI updates efficient.

**Example:**
- When you call `setState`, React updates the Virtual DOM first, then calculates the minimal DOM updates needed.

---

### 2. What are Hooks in React?
**Explanation:**  
Hooks are functions that let you use state and other React features in functional components. Common hooks include:
- `useState`: Add state
- `useEffect`: Side-effects (fetch data, subscriptions)
- `useContext`: Access context
- `useReducer`: Complex state logic
- `useCallback`, `useMemo`: Performance optimization
- `useRef`: Mutable values, DOM refs

**Example:**
```js
import { useState, useEffect } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  useEffect(() => {
    document.title = `Count: ${count}`;
  }, [count]);
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

---

### 3. What are Props in React?
**Explanation:**  
Props are inputs to a React component, passed from parent to child. They are read-only and used to make components reusable.

**Example:**
```js
function Welcome({ name }) {
  return <h1>Hello, {name}!</h1>;
}
// Usage: <Welcome name="Alice" />
```

---

### 4. Explain Context API
**Explanation:**  
Context API is a way to provide and consume values (like themes, user info) deeply in the component tree without passing props at every level.

**Example:**
```js
const ThemeContext = React.createContext('light');
function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}
function Toolbar() {
  const theme = React.useContext(ThemeContext);
  return <div>Current theme: {theme}</div>;
}
```

---

### 5. What is Code Splitting?
**Explanation:**  
Code splitting splits your code into smaller chunks, which are loaded on demand. This improves load time for large apps.

**Example:**
```js
import React, { Suspense } from 'react';
const LazyComponent = React.lazy(() => import('./LazyComponent'));
function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </Suspense>
  );
}
```

---

### 6. Explain the Flow of Redux
**Explanation:**  
Redux is a state management library. The flow is:
1. UI dispatches an action (plain object).
2. Middleware (like thunk) can handle async actions.
3. Reducers receive the action and update the store.
4. The UI subscribes to the store and updates as needed.

**Example:**
```js
// actions.js
export const increment = () => ({ type: 'INCREMENT' });

// reducer.js
const initialState = { count: 0 };
function counter(state = initialState, action) {
  switch(action.type) {
    case 'INCREMENT': return { count: state.count + 1 };
    default: return state;
  }
}
```

---

### 7. How to Share Data Between Components?
- **Parent to Child:** Props
- **Child to Parent:** Callback functions passed as props
- **Sibling to Sibling:** Lift state up to common ancestor or use Context/Redux

---

### 8. What is Server-side Rendering (SSR)?
**Explanation:**  
SSR renders React components on the server and sends fully rendered HTML to the client, improving performance and SEO. Next.js is a popular framework for SSR.

**Example:**
```js
// In Next.js's pages/index.js
export async function getServerSideProps() {
  // Fetch data here
  return { props: { /* data */ } }
}
```

---

### 9. How to Create a Custom Hook?
**Explanation:**  
Custom hooks let you extract and reuse component logic.

**Example:**
```js
function useCounter(initialValue = 0) {
  const [count, setCount] = useState(initialValue);
  const increment = () => setCount(c => c + 1);
  return [count, increment];
}
```

---

### 10. How to Optimize React Components?
- **Memoization:** Use `React.memo`, `useMemo`, `useCallback` to avoid unnecessary re-renders.
- **Code Splitting:** Load components on demand.
- **Avoid Anonymous Functions:** in props when possible.

---

### 11. Common React Design Patterns
- **Presentational and Container Components**
- **Hooks Pattern (custom hooks)**
- **Render Props**
- **Higher Order Components (HOCs)**

---

### 12. How to Make Async Calls Using Axios?
**Example:**
```js
import axios from 'axios';
useEffect(() => {
  axios.get('/api/data').then(res => setData(res.data));
}, []);
```

---

### 13. Redux Toolkit Basics
- **Slices:** Define actions and reducers together.
- **Async Thunks:** Handle async logic.
- **Selectors:** Get specific parts of state.

---

### 14. Testing With Jest & React Testing Library
- **Rendering:** `render(<Component />)`
- **Finding Elements:** `screen.getByText`, etc.
- **Mocking:** `jest.mock('axios')`
- **User Events:** `fireEvent.click(button)`

---

### 15. Semantic UI, AG Grid, CKEditor 4
- **Semantic UI:** Use components like `<Accordion>`, `<Table>`, etc.
- **AG Grid:** Powerful datagrid for large data sets.
- **CKEditor 4:** Rich text editor integration.

---

### 16. CSS Best Practices
- **Flexbox & Grid** for layouts
- **SASS** for maintainable styles
- **Responsive Design:** Media queries, mobile-first
- **UX Principles:** Accessibility, good contrast

---

## Additional React Topics for Interviews

#### 17. React Keys
Why are keys necessary in lists?  
**Answer:** Helps React identify which items have changed, are added, or are removed.

#### 18. Error Boundaries
What are error boundaries?  
**Answer:** Components that catch JavaScript errors anywhere in their child component tree.

#### 19. PropTypes and TypeScript
How do you enforce type safety?  
**Answer:** With PropTypes (runtime) or TypeScript (static).

#### 20. React Lifecycle Methods
What are common lifecycle methods in class components?  
**Answer:** `componentDidMount`, `componentDidUpdate`, `componentWillUnmount`.

---

# Summary Table

| Topic                         | JavaScript | React |
|-------------------------------|------------|-------|
| Hoisting                      | ✔️         |       |
| TDZ                           | ✔️         |       |
| Event Bubbling                | ✔️         |       |
| stopPropagation/preventDefault| ✔️         |       |
| Event Loop                    | ✔️         |       |
| Closures                      | ✔️         |       |
| Debounce                      | ✔️         |       |
| Arrow Functions               | ✔️         |       |
| this Keyword                  | ✔️         |       |
| Array.reduce                  | ✔️         |       |
| Prototypes                    | ✔️         |       |
| Async/Await                   | ✔️         |       |
| == vs ===                     | ✔️         |       |
| null vs undefined             | ✔️         |       |
| Virtual DOM                   |            | ✔️    |
| Hooks                         |            | ✔️    |
| Props                         |            | ✔️    |
| Context API                   |            | ✔️    |
| Code Splitting                |            | ✔️    |
| Redux Flow/Toolkit            |            | ✔️    |
| Data Sharing                  |            | ✔️    |
| SSR                           |            | ✔️    |
| Custom Hooks                  |            | ✔️    |
| Optimization                  |            | ✔️    |
| Design Patterns               |            | ✔️    |
| Async Calls (Axios)           |            | ✔️    |
| Testing                       |            | ✔️    |
| Semantic UI/AG Grid/CKEditor  |            | ✔️    |
| CSS/SASS/Responsive           | ✔️         | ✔️    |
| Keys in Lists                 |            | ✔️    |
| Error Boundaries              |            | ✔️    |
| PropTypes/TypeScript          | ✔️         | ✔️    |
| Lifecycle Methods             |            | ✔️    |

---

**Tip:** Practice writing code for these concepts and try building small projects or components using them!

# React Interview Questions and Answers (In-depth, with Examples)

This document provides detailed explanations, real-world context, and code examples for key React interview topics. It is designed for deeper understanding and practical application.

---

## 1. What is the Virtual DOM and how does React use it?

**In-depth Explanation:**  
The Virtual DOM (VDOM) is a lightweight JavaScript object representation of the real DOM. React uses the VDOM to optimize UI updates:

- When component state or props change, React creates a new Virtual DOM tree.
- React compares (diffs) the new tree with the previous tree using a reconciliation algorithm.
- React determines the minimal set of changes (the “diff”) and updates only those parts of the real DOM.
- This process is faster than updating the real DOM directly because changes are batched and unnecessary updates are avoided.

**Analogy:**  
Think of the VDOM as a blueprint. Instead of rebuilding an entire house for a small change, you update only the room that changed.

**Code Example:**
```js
function Counter() {
  const [count, setCount] = React.useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```
When `setCount` is called, React:
- Creates a new VDOM tree for `Counter`.
- Compares it with the previous tree.
- Updates only the text node that changed.

---

## 2. What are Hooks in React? Why were they introduced?

**In-depth Explanation:**  
Hooks are special functions that let you “hook into” React state and lifecycle features from function components. Before hooks, only class components had access to state and lifecycle methods; hooks enable these features in function components, leading to simpler and more reusable code.

**Main Hooks:**
- `useState`: Add local state to a function component.
- `useEffect`: Perform side effects (data fetching, subscriptions).
- `useContext`: Access global context.
- `useReducer`: For complex state logic.
- `useCallback` and `useMemo`: Optimize performance.
- `useRef`: Persist values or access DOM nodes.

**Example with `useState` and `useEffect`:**
```js
import React, { useState, useEffect } from 'react';

function Timer() {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => setSeconds(s => s + 1), 1000);
    return () => clearInterval(interval); // Cleanup
  }, []);

  return <div>Timer: {seconds}s</div>;
}
```

**Why Hooks?**
- Avoids “wrapper hell” (nesting HOCs, render props).
- Enables sharing logic via custom hooks.
- Simplifies component structure.

---

## 3. What are Props in React and how do they work?

**In-depth Explanation:**  
Props (short for “properties”) are read-only data passed from a parent component to a child component. They allow for dynamic and reusable components.

**Key Points:**
- Props are immutable in the child; only the parent can change them.
- Props can be any data type (primitive, object, function, element).
- Props enable communication from parent to child.

**Example:**
```js
function Profile({ name, avatarUrl }) {
  return (
    <div>
      <img src={avatarUrl} alt={name} />
      <h2>{name}</h2>
    </div>
  );
}

// Usage:
<Profile name="Alice" avatarUrl="/alice.png" />
```

---

## 4. Explain Context API. When should you use it?

**In-depth Explanation:**  
The Context API allows data to be shared across the component tree without passing props down manually at every level (avoids “prop drilling”).

**When to use:**
- When many components at different nesting levels need access to the same data (e.g., theme, user auth, locale).
- Avoid for “every state”; best for truly global data.

**How it works:**
1. Create a Context with `React.createContext`.
2. Wrap part of the tree with `Context.Provider` and pass a value.
3. Consume the context in any nested component with `useContext` or `Context.Consumer`.

**Example:**
```js
// Create context
const ThemeContext = React.createContext('light');

// Provider at the top level
function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}

// Consume context
function Toolbar() {
  const theme = React.useContext(ThemeContext);
  return <div>Current theme: {theme}</div>;
}
```

---

## 5. What is Code Splitting and how do you implement it in React?

**In-depth Explanation:**  
Code splitting breaks your app into smaller bundles (“chunks”) that can be loaded on demand, improving performance by reducing the initial load time.

**React Implementation:**
- `React.lazy()` allows you to dynamically import a component.
- `<Suspense>` lets you show a fallback UI while loading.

**Example:**
```js
import React, { Suspense } from 'react';

const HeavyComponent = React.lazy(() => import('./HeavyComponent'));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <HeavyComponent />
    </Suspense>
  );
}
```
For routes, libraries like React Router support code splitting per route.

---

## 6. Explain the Flow of Redux (with and without Redux Toolkit).

**In-depth Explanation:**  
Redux is a state management library for predictable state updates.

**Classic Redux Flow:**
1. **Action**: Plain JS object describing what happened.
2. **Dispatch**: Send action to the store.
3. **Reducer**: Pure function to determine how state changes.
4. **Store**: Holds the state tree.
5. **View**: Subscribes to store and re-renders on changes.

**Example:**
```js
// Action
const increment = () => ({ type: 'INCREMENT' });

// Reducer
function counter(state = 0, action) {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1;
    default:
      return state;
  }
}

// Dispatch
store.dispatch(increment());
```

**Redux Toolkit:**
- Reduces boilerplate with `createSlice` and `createAsyncThunk`.
- Provides “slices” for state + reducers + actions.

**Example:**
```js
import { createSlice } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter',
  initialState: 0,
  reducers: {
    increment: state => state + 1
  }
});

export const { increment } = counterSlice.actions;
export default counterSlice.reducer;
```

---

## 7. How do you share data between components in React?

**In-depth Explanation:**
- **Parent to Child:** Pass data as props.
- **Child to Parent:** Pass a function as a prop from parent, call it in child with data.
- **Sibling to Sibling:** Lift state up to their common parent.
- **Global Sharing:** Use Context, Redux, Zustand, or other state management.

**Example – Child to Parent:**
```js
function Parent() {
  const [value, setValue] = useState('');
  return <Child onChange={setValue} />;
}

function Child({ onChange }) {
  return <input onChange={e => onChange(e.target.value)} />;
}
```

---

## 8. What is Server-Side Rendering (SSR) in React? What are its benefits and trade-offs?

**In-depth Explanation:**  
SSR means rendering React components on the server, sending fully formed HTML to the client, then hydrating (attaching event listeners) on the client. Commonly used with Next.js.

**Benefits:**
- Faster initial page load (especially for slow networks).
- Better SEO (search engines see content immediately).
- Improved social sharing (meta tags rendered on server).

**Trade-offs:**
- More complex setup (node server needed).
- Slower time-to-interactive (JS still needs to hydrate).
- Some browser APIs not available during server render.

**Example (Next.js):**
```js
export async function getServerSideProps() {
  // fetch data on the server
  return { props: { /* data */ } };
}
```

---

## 9. How do you create a custom hook in React? Give a real-world example.

**In-depth Explanation:**  
A custom hook is a function named with a `use` prefix that can call other hooks and encapsulate logic for reuse across components.

**Benefits:**
- DRY code: Extract repeated logic.
- Share effects, state, and more between components.

**Example:**
```js
// useFetch.js
import { useState, useEffect } from 'react';

function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    setLoading(true);
    fetch(url)
      .then(res => res.json())
      .then(setData)
      .finally(() => setLoading(false));
  }, [url]);

  return { data, loading };
}

// Usage:
const { data, loading } = useFetch('/api/items');
```

---

## 10. How do you optimize React components for performance?

**In-depth Explanation:**
- **Memoization:**  
  - `React.memo` for functional components to prevent unnecessary re-renders.
  - `useMemo` for memoizing expensive calculations.
  - `useCallback` to memoize functions so they don’t trigger child re-renders.
- **Key prop in lists:** Helps React identify changed elements.
- **Code Splitting:** Load only the code needed for a specific route.
- **Avoid Anonymous Functions in JSX:** Can cause unnecessary re-renders.

**Example:**
```js
const ExpensiveComponent = React.memo(function ExpensiveComponent({ value }) {
  // Only re-renders if value changes
  // ...
});

const memoizedCallback = useCallback(() => {
  // Function body
}, [dependency]);
```

---

## 11. What are React Design Patterns?

**In-depth Explanation:**
- **Presentational and Container Components:**  
  Split UI (presentational, stateless) from logic (container, stateful).
- **Hooks Pattern:**  
  Encapsulate logic in custom hooks for reuse.
- **Render Prop Pattern:**  
  Pass a render function to a component for flexible UI composition.
- **Higher-Order Component (HOC):**  
  Function that takes a component and returns a new component with added props or logic.

**Example – Render Prop:**
```js
function DataProvider({ render }) {
  const [data, setData] = useState(null);
  // Fetch data...
  return render(data);
}

<DataProvider render={data => <div>{data}</div>} />;
```

---

## 12. How do you make async calls using Axios in React? Where should you put async logic?

**In-depth Explanation:**
- Use `useEffect` to perform side effects like data fetching.
- Always handle loading and error states.
- Clean up subscriptions (cancel requests) to avoid memory leaks.

**Example:**
```js
import axios from 'axios';
import { useEffect, useState } from 'react';

function UserList() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    let cancelled = false;
    axios.get('/api/users').then(res => {
      if (!cancelled) setUsers(res.data);
    }).finally(() => setLoading(false));
    return () => { cancelled = true; };
  }, []);

  if (loading) return <div>Loading...</div>;
  return <ul>{users.map(u => <li key={u.id}>{u.name}</li>)}</ul>;
}
```

---

## 13. What is Redux Toolkit and how do you fetch data using it?

**In-depth Explanation:**
- Redux Toolkit streamlines Redux by reducing boilerplate.
- `createSlice`: Defines state, reducers, and actions in one place.
- `createAsyncThunk`: Handles async logic (e.g., API calls) with pending/fulfilled/rejected actions.

**Example:**
```js
import { createSlice, createAsyncThunk } from '@reduxjs/toolkit';

export const fetchUsers = createAsyncThunk(
  'users/fetchUsers',
  async () => {
    const response = await axios.get('/api/users');
    return response.data;
  }
);

const usersSlice = createSlice({
  name: 'users',
  initialState: { data: [], status: 'idle' },
  extraReducers: builder => {
    builder
      .addCase(fetchUsers.pending, (state) => { state.status = 'loading'; })
      .addCase(fetchUsers.fulfilled, (state, action) => {
        state.data = action.payload;
        state.status = 'succeeded';
      });
  }
});
```
Use `useDispatch` to dispatch `fetchUsers`, and `useSelector` to read state.

---

## 14. How do you test React components using Jest and React Testing Library?

**In-depth Explanation:**
- **Jest** is the test runner and assertion library.
- **React Testing Library (RTL)** encourages testing components as users interact with them.

**Key practices:**
- Render components with `render()`.
- Query elements with `screen.getByText`, `getByRole`, etc.
- Simulate user events with `fireEvent` or `userEvent`.
- Mock APIs for async tests.

**Example:**
```js
import { render, screen, fireEvent } from '@testing-library/react';
import Counter from './Counter';

test('increments counter', () => {
  render(<Counter />);
  fireEvent.click(screen.getByText('Increment'));
  expect(screen.getByText(/Count:/)).toHaveTextContent('1');
});
```

---

## 15. What is Semantic UI and how is it used in React?

**In-depth Explanation:**
- **Semantic UI** is a CSS framework with React components (`semantic-ui-react`).
- Use prebuilt components (Accordion, Table, etc.) for rapid UI development.

**Example:**
```js
import { Table } from 'semantic-ui-react';

<Table celled>
  <Table.Header>
    <Table.Row>
      <Table.HeaderCell>Name</Table.HeaderCell>
      <Table.HeaderCell>Age</Table.HeaderCell>
    </Table.Row>
  </Table.Header>
  <Table.Body>
    <Table.Row>
      <Table.Cell>Alice</Table.Cell>
      <Table.Cell>24</Table.Cell>
    </Table.Row>
  </Table.Body>
</Table>
```

---

## 16. How do you use AG Grid in a React application?

**In-depth Explanation:**
- **AG Grid** is a feature-rich datagrid for React.
- Supports sorting, filtering, pagination, editing, and more.

**Example:**
```js
import { AgGridReact } from 'ag-grid-react';
import 'ag-grid-community/styles/ag-grid.css';

function MyGrid({ rowData }) {
  const columns = [{ field: 'name' }, { field: 'age' }];
  return (
    <div className="ag-theme-alpine" style={{ height: 400 }}>
      <AgGridReact rowData={rowData} columnDefs={columns} />
    </div>
  );
}
```

---

## 17. How do you use CKEditor 4 in React?

**In-depth Explanation:**
- CKEditor 4 is a rich text editor.
- Use the CKEditor React component to integrate it.

**Example:**
```js
import CKEditor from 'ckeditor4-react';

function Editor() {
  return (
    <CKEditor
      data="<p>Type here...</p>"
      onChange={event => console.log(event.editor.getData())}
    />
  );
}
```

---

## 18. CSS, Flexbox, Grid, SASS, Responsive Web Design in React

**In-depth Explanation:**
- **Flexbox/Grid:** Modern layouts.
- **SASS:** Nesting, variables, modular CSS.
- **Responsive Design:** Mobile-first, media queries.
- **Best Practices:** BEM naming, modular CSS, avoid inline styles.

**Example:**
```scss
// styles.module.scss
.container {
  display: flex;
  flex-direction: column;
  @media (max-width: 600px) {
    flex-direction: row;
  }
}
```
```js
import styles from './styles.module.scss';
<div className={styles.container}></div>
```

---

## 19. What are Error Boundaries in React?

**In-depth Explanation:**
Error boundaries are React components that catch JavaScript errors in their child component tree and display a fallback UI.

**Example:**
```js
class ErrorBoundary extends React.Component {
  state = { hasError: false };
  static getDerivedStateFromError() { return { hasError: true }; }
  componentDidCatch(error, info) { /* log error */ }
  render() {
    if (this.state.hasError) return <h1>Something went wrong.</h1>;
    return this.props.children;
  }
}
```
Use to wrap components that may throw errors.

---

## 20. Why are "keys" important in React lists?

**In-depth Explanation:**
Keys help React identify which items have changed, are added, or removed, for efficient list rendering. Keys should be stable, unique, and not rely on array indexes when possible.

**Example:**
```js
const items = ['a', 'b', 'c'];
items.map(item => <li key={item}>{item}</li>);
```

---

**Tip:**  
For each topic, try to build a small demo or code sandbox to see these concepts in action!
