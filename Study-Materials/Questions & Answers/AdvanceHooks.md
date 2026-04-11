# 🔷 1. `useReducer`

## ✅ Basic Interview Questions

### ❓ What is `useReducer`?

👉 A hook used for **complex state logic**, based on the reducer pattern:

```js
(state, action) => newState
```

---

### ❓ Difference between `useState` and `useReducer`?

| useState         | useReducer            |
| ---------------- | --------------------- |
| Simple state     | Complex state         |
| Direct updates   | Uses reducer function |
| Less boilerplate | More structured       |

---

### ❓ What is `dispatch`?

👉 A function used to send actions to the reducer:

```js
dispatch({ type: "increment" });
```

---

## 🚀 Advanced Questions

### ❓ When should you prefer `useReducer`?

* Multiple related states
* Complex updates
* State depends on previous state

---

### ❓ Can you use async logic inside reducer?

❌ No (reducers must be pure)

👉 Use async logic **before dispatch**

```js
const fetchData = async () => {
  const data = await fetch(...);
  dispatch({ type: "success", payload: data });
};
```

---

## 💻 Coding Question

### 🔹 Build a Todo App using `useReducer`

```js
import React, { useReducer, useState } from "react";

const reducer = (state, action) => {
  switch (action.type) {
    case "add":
      return [...state, action.payload];
    case "delete":
      return state.filter((_, i) => i !== action.index);
    default:
      return state;
  }
};

export default function TodoApp() {
  const [todos, dispatch] = useReducer(reducer, []);
  const [input, setInput] = useState("");

  return (
    <div>
      <input value={input} onChange={(e) => setInput(e.target.value)} />
      <button onClick={() => dispatch({ type: "add", payload: input })}>
        Add
      </button>

      {todos.map((todo, i) => (
        <div key={i}>
          {todo}
          <button onClick={() => dispatch({ type: "delete", index: i })}>
            ❌
          </button>
        </div>
      ))}
    </div>
  );
}
```

---

# 🔷 2. `useMemo`

## ✅ Basic Interview Questions

### ❓ What is `useMemo`?

👉 Memoizes a **computed value** to avoid recomputation.

---

### ❓ Why use it?

👉 Performance optimization (avoids expensive recalculations)

---

## 🚀 Advanced Questions

### ❓ When NOT to use `useMemo`?

* Cheap calculations
* Over-optimization can hurt readability

---

### ❓ Difference between `useMemo` and `useCallback`?

| useMemo                | useCallback             |
| ---------------------- | ----------------------- |
| Returns value          | Returns function        |
| `useMemo(() => value)` | `useCallback(() => fn)` |

---

## 💻 Coding Question

### 🔹 Optimize filtering list

```js
import React, { useState, useMemo } from "react";

export default function SearchList() {
  const [query, setQuery] = useState("");

  const items = ["apple", "banana", "grape", "orange"];

  const filtered = useMemo(() => {
    console.log("Filtering...");
    return items.filter((item) => item.includes(query));
  }, [query]);

  return (
    <div>
      <input onChange={(e) => setQuery(e.target.value)} />
      {filtered.map((item) => (
        <p key={item}>{item}</p>
      ))}
    </div>
  );
}
```

---

# 🔷 3. `useCallback`

## ✅ Basic Interview Questions

### ❓ What is `useCallback`?

👉 Memoizes a **function reference**

---

### ❓ Why is it needed?

👉 Prevent unnecessary re-renders in child components

---

## 🚀 Advanced Questions

### ❓ What problem does it solve?

👉 Referential equality issue:

* Functions are recreated every render
* Causes child re-renders

---

### ❓ When is it useless?

👉 If child is NOT memoized (`React.memo`)

---

## 💻 Coding Question

### 🔹 Prevent child re-render

```js
import React, { useState, useCallback } from "react";

const Child = React.memo(({ handleClick }) => {
  console.log("Child rendered");
  return <button onClick={handleClick}>Click</button>;
});

export default function App() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    console.log("Clicked");
  }, []);

  return (
    <div>
      <Child handleClick={handleClick} />
      <button onClick={() => setCount(count + 1)}>Parent {count}</button>
    </div>
  );
}
```

---

# 🔷 4. `useRef`

## ✅ Basic Interview Questions

### ❓ What is `useRef`?

👉 Stores a **mutable value that doesn’t trigger re-render**

---

### ❓ What is `.current`?

👉 The actual stored value

---

## 🚀 Advanced Questions

### ❓ Difference between `useRef` and `useState`?

| useRef       | useState           |
| ------------ | ------------------ |
| No re-render | Triggers re-render |
| Mutable      | Immutable updates  |

---

### ❓ Common use cases?

* DOM access
* Store previous value
* Timers / intervals

---

## 💻 Coding Questions

### 🔹 Focus input on button click

```js
import React, { useRef } from "react";

export default function FocusInput() {
  const inputRef = useRef();

  return (
    <div>
      <input ref={inputRef} />
      <button onClick={() => inputRef.current.focus()}>
        Focus
      </button>
    </div>
  );
}
```

---

### 🔹 Track previous value

```js
import React, { useRef, useEffect, useState } from "react";

export default function PrevValue() {
  const [count, setCount] = useState(0);
  const prev = useRef();

  useEffect(() => {
    prev.current = count;
  }, [count]);

  return (
    <div>
      <h2>Now: {count}</h2>
      <h3>Prev: {prev.current}</h3>
      <button onClick={() => setCount(count + 1)}>+</button>
    </div>
  );
}
```

---

# 🔥 Mixed Advanced Interview Questions

### ❓ Combine all hooks in one scenario

👉 Example:

* `useReducer` → manage state
* `useMemo` → derived data
* `useCallback` → stable handlers
* `useRef` → store previous state

---

### ❓ What are common mistakes?

* Overusing `useMemo` / `useCallback`
* Wrong dependency arrays
* Mutating state inside reducer
* Using `useRef` instead of state incorrectly

---

# 🧠 Pro Interview Tips

* Always explain **"why"**, not just "what"
* Mention **performance optimization carefully**
* Use terms like:

  * “referential equality”
  * “pure function”
  * “memoization”
