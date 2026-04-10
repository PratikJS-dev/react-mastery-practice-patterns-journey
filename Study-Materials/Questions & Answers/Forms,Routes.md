# 🔹 1. Forms in React (Controlled vs Uncontrolled)

### ❓ What is a controlled component?

A **controlled component** is a form element whose value is controlled by React state.

```jsx
function ControlledInput() {
  const [value, setValue] = React.useState("");

  return (
    <input 
      value={value} 
      onChange={(e) => setValue(e.target.value)} 
    />
  );
}
```

👉 React is the **single source of truth**

---

### ❓ What is an uncontrolled component?

An **uncontrolled component** stores its own state internally using the DOM.

```jsx
function UncontrolledInput() {
  const inputRef = React.useRef();

  const handleSubmit = () => {
    alert(inputRef.current.value);
  };

  return <input ref={inputRef} />;
}
```

---

### ❓ Controlled vs Uncontrolled – Key Differences

| Feature     | Controlled      | Uncontrolled  |
| ----------- | --------------- | ------------- |
| Data source | React state     | DOM           |
| Validation  | Easy            | Harder        |
| Performance | Slightly slower | Faster        |
| Use case    | Complex forms   | Simple inputs |

---

### ❓ When should you use controlled components?

* Form validation
* Dynamic inputs
* Real-time UI updates

---

### ❓ What are common form handling techniques?

* `onChange` for updates
* `onSubmit` for form submission
* Prevent default behavior:

```js
e.preventDefault();
```

---

# 🔹 2. Lifting State Up

### ❓ What does "lifting state up" mean?

Moving shared state to the **closest common parent** so multiple components can access it.

---

### ❓ Example:

```jsx
function Parent() {
  const [data, setData] = React.useState("");

  return (
    <>
      <Child1 setData={setData} />
      <Child2 data={data} />
    </>
  );
}
```

---

### ❓ Why is lifting state important?

* Enables **data sharing between components**
* Maintains **single source of truth**
* Avoids duplication

---

### ❓ What are alternatives to lifting state up?

* Context API
* State management libraries (Redux, Zustand)

---

### ❓ Problem with excessive lifting?

👉 Leads to **prop drilling**

---

# 🔹 3. React Router (Basic to Advanced)

### ❓ What is React Router?

A library for **client-side routing** in React applications.

---

### ❓ Basic setup

```jsx
import { BrowserRouter, Routes, Route } from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

### ❓ What is the difference between `Link` and `a` tag?

| Link           | a tag                  |
| -------------- | ---------------------- |
| No page reload | Full reload            |
| SPA navigation | Traditional navigation |

---

### ❓ What is `useNavigate`?

```jsx
const navigate = useNavigate();
navigate("/home");
```

👉 Used for programmatic navigation

---

### ❓ What are route parameters?

```jsx
<Route path="/user/:id" element={<User />} />
```

```jsx
const { id } = useParams();
```

---

### ❓ What is nested routing?

```jsx
<Route path="/dashboard" element={<Dashboard />}>
  <Route path="settings" element={<Settings />} />
</Route>
```

---

### ❓ What is protected routing?

```jsx
function PrivateRoute({ children }) {
  return isAuth ? children : <Navigate to="/login" />;
}
```

---

### ❓ What is lazy loading in routing?

```jsx
const Home = React.lazy(() => import("./Home"));
```

👉 Improves performance

---

# 🔹 4. Common React Interview Questions

### ❓ What is Virtual DOM?

A lightweight copy of the real DOM used for efficient updates.

---

### ❓ What are hooks?

Functions that let you use state and lifecycle features in functional components.

Examples:

* `useState`
* `useEffect`
* `useRef`

---

### ❓ What is useEffect?

```jsx
useEffect(() => {
  // side effect
}, []);
```

👉 Runs after render

---

### ❓ What is the difference between useEffect and useLayoutEffect?

| useEffect   | useLayoutEffect |
| ----------- | --------------- |
| Async       | Sync            |
| After paint | Before paint    |

---

### ❓ What is memoization in React?

Optimizing performance by avoiding unnecessary re-renders.

* `React.memo`
* `useMemo`
* `useCallback`

---

# 🔹 5. Advanced React Interview Questions

### ❓ What is reconciliation?

The process React uses to update the DOM efficiently.

---

### ❓ What are keys in React?

Unique identifiers for list items.

```jsx
items.map(item => <li key={item.id}>{item.name}</li>)
```

---

### ❓ What is prop drilling?

Passing props through multiple layers unnecessarily.

---

### ❓ What is Context API?

A way to share global state without prop drilling.

---

### ❓ What are higher-order components (HOC)?

Functions that take a component and return a new component.

---

### ❓ What is suspense?

Used for handling lazy loading and async rendering.

---

### ❓ What are error boundaries?

Components that catch JavaScript errors in child components.

---

# 🔹 Pro Interview Tips

* Always explain with **real examples**
* Mention **performance optimization**
* Talk about **scalability**
* Compare alternatives (e.g., Context vs Redux)
