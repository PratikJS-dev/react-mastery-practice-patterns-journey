# 🔹 Functional vs Class Components (React)

### 🧠 Core Difference

| Feature     | Functional Components          | Class Components  |
| ----------- | ------------------------------ | ----------------- |
| Syntax      | Simple functions               | ES6 classes       |
| State       | Uses Hooks (`useState`)        | Uses `this.state` |
| Lifecycle   | Hooks (`useEffect`)            | Lifecycle methods |
| Boilerplate | Minimal                        | More verbose      |
| Performance | Slightly better (modern React) | Slightly heavier  |
| Recommended | ✅ Yes (modern React)           | ❌ Mostly legacy   |

---

## 🔹 Example

### Functional Component

```jsx
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>{count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

export default Counter;
```

---

### Class Component

```jsx
import React, { Component } from "react";

class Counter extends Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  render() {
    return (
      <div>
        <p>{this.state.count}</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Increment
        </button>
      </div>
    );
  }
}

export default Counter;
```

---

# 🔹 Interview Questions & Answers

## 1. What is the difference between functional and class components?

**Answer:**
Functional components are plain JavaScript functions that use Hooks for state and lifecycle, while class components use ES6 classes with lifecycle methods like `componentDidMount`.

---

## 2. What are React Hooks?

**Answer:**
Hooks are functions (like `useState`, `useEffect`) that let you use state and lifecycle features inside functional components.

---

## 3. Why are functional components preferred now?

**Answer:**

* Less boilerplate
* Easier to read and test
* Hooks simplify logic reuse
* Better performance optimizations

---

## 4. What replaces lifecycle methods in functional components?

**Answer:**
`useEffect` replaces lifecycle methods like:

* `componentDidMount`
* `componentDidUpdate`
* `componentWillUnmount`

---

## 5. What is `this` in class components?

**Answer:**
`this` refers to the component instance and is used to access state and props (`this.state`, `this.props`).

---

## 6. Can functional components have state?

**Answer:**
Yes, using `useState`.

---

## 7. Difference between `setState` and `useState`?

**Answer:**

* `setState` merges state (class)
* `useState` replaces state (functional)

---

## 8. Are class components deprecated?

**Answer:**
No, but they are rarely used in modern development.

---

# 🔹 Coding Interview Questions

## 🧩 1. Convert Class → Functional

### Given:

```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello {this.props.name}</h1>;
  }
}
```

### Solution:

```jsx
function Welcome({ name }) {
  return <h1>Hello {name}</h1>;
}
```

---

## 🧩 2. Counter with Hooks

```jsx
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <>
      <h2>{count}</h2>
      <button onClick={() => setCount(count + 1)}>+</button>
      <button onClick={() => setCount(count - 1)}>-</button>
    </>
  );
}
```

---

## 🧩 3. useEffect Example (Lifecycle Replacement)

```jsx
import React, { useEffect } from "react";

function Example() {
  useEffect(() => {
    console.log("Mounted");

    return () => {
      console.log("Unmounted");
    };
  }, []);

  return <h1>Hello</h1>;
}
```

---

## 🧩 4. Fetch API Data (Common Interview Task)

```jsx
import React, { useState, useEffect } from "react";

function Users() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then(res => res.json())
      .then(data => setUsers(data));
  }, []);

  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

---

## 🧩 5. Toggle Component

```jsx
import React, { useState } from "react";

function Toggle() {
  const [isOn, setIsOn] = useState(false);

  return (
    <button onClick={() => setIsOn(!isOn)}>
      {isOn ? "ON" : "OFF"}
    </button>
  );
}
```

---

# 🔹 Bonus Advanced Questions

### 🔸 What is useCallback?

Used to memoize functions to avoid unnecessary re-renders.

### 🔸 What is useMemo?

Used to memoize computed values.

### 🔸 What is prop drilling?

Passing props through multiple levels → solved using Context API.

---

# 🔥 3. Functional vs Class Components

## ❓ Q8: Why are functional components faster?

**Answer:**

* Less overhead (no class instance)
* Simpler memory usage
* Better optimization with hooks


## ❓ Q9: Can functional components replace all class features?

**Answer:**
Yes, using hooks:

* State → `useState`
* Lifecycle → `useEffect`
* Context → `useContext`


## ❓ Q10: What are the drawbacks of class components?

**Answer:**

* Verbose syntax
* `this` confusion
* Harder to reuse logic
* Lifecycle duplication

---

# 🔹 Pro Interview Tip 💡

If interviewer asks:
👉 *“Which one should we use?”*

**Best Answer:**

> “Functional components with Hooks are the modern standard in React and should be preferred unless maintaining legacy class-based code.”
