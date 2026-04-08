# 🔹 1. `useState` Hook

## 🧠 What it does

`useState` lets you **add state to functional components**.


## ✅ Syntax

```jsx
const [state, setState] = useState(initialValue);
```


## 📌 Example: Counter

```jsx
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <>
      <h2>{count}</h2>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </>
  );
}
```

## 💡 Key Points

* `useState` returns **array → [value, setter]**
* Updating state **re-renders component**
* State updates are **asynchronous**



## ⚠️ Common Mistake

```jsx
setCount(count + 1);
setCount(count + 1); // ❌ wrong (same value used)
```

✔ Fix:

```jsx
setCount(prev => prev + 1);
setCount(prev => prev + 1);
```

---

# 🔹 2. `useEffect` Hook

## 🧠 What it does

Handles **side effects** like:

* API calls
* Timers
* DOM updates


## ✅ Syntax

```jsx
useEffect(() => {
  // side effect

  return () => {
    // cleanup (optional)
  };
}, [dependencies]);
```

## 📌 Example: Run Once (like `componentDidMount`)

```jsx
useEffect(() => {
  console.log("Component Mounted");
}, []);
```
## 📌 Example: Run on State Change

```jsx
useEffect(() => {
  console.log("Count changed:", count);
}, [count]);
```

## 📌 Example: Cleanup (important for interviews)

```jsx
useEffect(() => {
  const timer = setInterval(() => {
    console.log("Running...");
  }, 1000);

  return () => {
    clearInterval(timer); // cleanup
  };
}, []);
```

---

# 🔹 Dependency Array Explained

| Dependency | Behavior               |
| ---------- | ---------------------- |
| `[]`       | Run once (mount)       |
| `[count]`  | Run when count changes |
| No array   | Run on every render    |

---

# 🔹 Interview Questions & Answers

## 1. What is `useState`?

**Answer:**
A Hook used to manage state in functional components.


## 2. What is `useEffect`?

**Answer:**
A Hook used to handle side effects like API calls, subscriptions, and timers.

## 3. What happens if dependency array is empty?

**Answer:**
Effect runs only once after initial render.


## 4. What is cleanup function?

**Answer:**
A function returned from `useEffect` to clean resources (e.g., timers, listeners).

## 5. Difference between `useEffect` and lifecycle methods?

**Answer:**
`useEffect` replaces:

* `componentDidMount`
* `componentDidUpdate`
* `componentWillUnmount`


## 6. Can we use multiple `useEffect`?

**Answer:**
Yes, and it's recommended to separate concerns.


# 🔹 Coding Interview Questions

## 🧩 1. Auto Increment Counter

```jsx
import React, { useState, useEffect } from "react";

function AutoCounter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    const id = setInterval(() => {
      setCount(prev => prev + 1);
    }, 1000);

    return () => clearInterval(id);
  }, []);

  return <h2>{count}</h2>;
}
```


## 🧩 2. Fetch Data from API

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
      {users.map(u => <li key={u.id}>{u.name}</li>)}
    </ul>
  );
}
```


## 🧩 3. Toggle Title (DOM Side Effect)

```jsx
import React, { useState, useEffect } from "react";

function TitleToggle() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Clicked ${count} times`;
  }, [count]);

  return <button onClick={() => setCount(count + 1)}>Click</button>;
}
```
---

# 🔥 4. Hooks – Advanced (`useState`, `useEffect`)

## ❓ Q1: Why is `useState` asynchronous?

**Answer:**
React batches state updates for performance optimization.



## ❓ Q2: What is stale state in `useState`?

**Answer:**
When state updates use an outdated value.

❌ Problem:

```js
setCount(count + 1);
```

✔ Fix:

```js
setCount(prev => prev + 1);
```



## ❓ Q3: How does React decide when to re-run `useEffect`?

**Answer:**
It compares dependency array values using **shallow comparison**.

---

## ❓ Q4: What happens if dependency array is missing?

**Answer:**
`useEffect` runs on **every render**, which may cause performance issues.



## ❓ Q5: Can `useEffect` cause infinite loops?

**Answer:**
Yes.

❌ Example:

```js
useEffect(() => {
  setCount(count + 1);
}, [count]);
```

👉 This keeps updating forever.


## ❓ Q6: What is cleanup in `useEffect` and why important?

**Answer:**
Used to prevent memory leaks.

✔ Example:

```js
useEffect(() => {
  const id = setInterval(() => {}, 1000);

  return () => clearInterval(id);
}, []);
```



## ❓ Q7: Difference between `useEffect` and `useLayoutEffect`?

**Answer:**

| useEffect        | useLayoutEffect   |
| ---------------- | ----------------- |
| Runs after paint | Runs before paint |
| Non-blocking     | Blocking          |
| Preferred        | Rare use cases    |


## ❓ Q8: Why shouldn’t we use `useEffect` for everything?

**Answer:**
It can:

* Reduce performance
* Create unnecessary re-renders
* Make logic harder to follow

👉 Use only for **side effects**


# 🔥 5. Coding-Based Advanced Questions

## 🧩 Q9: Build a custom counter with safe updates

```jsx
function Counter() {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(prev => prev + 1);
  };

  return <button onClick={increment}>{count}</button>;
}
```

---

## 🧩 Q10: Prevent API call on every render

```jsx
useEffect(() => {
  fetchData();
}, []); // only once
```

---

## 🧩 Q11: Debounced Search (Important)

```jsx
import { useState, useEffect } from "react";

function Search() {
  const [query, setQuery] = useState("");
  const [debounced, setDebounced] = useState(query);

  useEffect(() => {
    const timer = setTimeout(() => {
      setDebounced(query);
    }, 500);

    return () => clearTimeout(timer);
  }, [query]);

  return <input onChange={e => setQuery(e.target.value)} />;
}
```

---

# 🔥 Pro-Level Interview Tip

If interviewer asks:
👉 *“What are common mistakes with hooks?”*

✔ Strong Answer:

* Missing dependencies in `useEffect`
* Infinite loops
* Mutating state
* Overusing `useEffect`
* Not using functional updates


---

# 🔹 Real Interview Tip 💡

👉 If interviewer asks:
**“When should you use useEffect?”**

✔ Best Answer:

> “Whenever we need to perform side effects like API calls, subscriptions, timers, or manually updating the DOM after rendering.”

---

# 🔹 Quick Summary

* `useState` → manage state
* `useEffect` → handle side effects
* Together → replace most class component features
