# 🔹 1. `useReducer` — State management for complex logic

## 🧠 Concept

`useReducer` is an alternative to `useState`, useful when:

* State logic is **complex**
* Multiple state values depend on each other
* You want **predictable state transitions**

It follows the **reducer pattern** (like Redux):

```
(state, action) → newState
```

---

## 📌 Syntax

```js
const [state, dispatch] = useReducer(reducer, initialState);
```

---

## ✅ Example: Counter with actions

```js
import React, { useReducer } from "react";

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    case "reset":
      return initialState;
    default:
      return state;
  }
}

export default function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <h2>{state.count}</h2>
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
      <button onClick={() => dispatch({ type: "reset" })}>Reset</button>
    </div>
  );
}
```

---

## 🧩 When to use

* Forms with many fields
* Complex state transitions
* When `useState` becomes messy

---

# 🔹 2. `useMemo` — Memoizing values

## 🧠 Concept

`useMemo` **caches the result of a computation** so it doesn’t re-run unnecessarily.

👉 It runs only when dependencies change.

---

## 📌 Syntax

```js
const memoizedValue = useMemo(() => computeValue(), [dependencies]);
```

---

## ✅ Example: Expensive calculation

```js
import React, { useState, useMemo } from "react";

function expensiveCalculation(num) {
  console.log("Calculating...");
  return num * 2;
}

export default function App() {
  const [count, setCount] = useState(0);
  const [text, setText] = useState("");

  const result = useMemo(() => {
    return expensiveCalculation(count);
  }, [count]);

  return (
    <div>
      <h2>Result: {result}</h2>
      <button onClick={() => setCount(count + 1)}>Increment</button>

      <input
        value={text}
        onChange={(e) => setText(e.target.value)}
        placeholder="Typing won't trigger calculation"
      />
    </div>
  );
}
```

---

## ⚡ Why it matters

Without `useMemo`, the function runs on **every render**
With it, it runs **only when needed**

---

## 🧩 When to use

* Expensive calculations
* Derived data (filtering, sorting)
* Performance optimization

---

# 🔹 3. `useCallback` — Memoizing functions

## 🧠 Concept

`useCallback` returns a **memoized version of a function**.

👉 Prevents unnecessary re-creation of functions on every render.

---

## 📌 Syntax

```js
const memoizedFn = useCallback(() => {}, [dependencies]);
```

---

## ✅ Example: Prevent child re-renders

```js
import React, { useState, useCallback } from "react";

const Child = React.memo(({ onClick }) => {
  console.log("Child rendered");
  return <button onClick={onClick}>Click me</button>;
});

export default function Parent() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    console.log("Clicked");
  }, []);

  return (
    <div>
      <Child onClick={handleClick} />
      <button onClick={() => setCount(count + 1)}>
        Re-render Parent ({count})
      </button>
    </div>
  );
}
```

---

## ⚡ Why it matters

Without `useCallback`:

* New function created every render
* Child components may re-render unnecessarily

---

## 🧩 When to use

* Passing functions to **memoized children (`React.memo`)**
* Avoid unnecessary renders
* Performance tuning

---

# 🔹 4. `useRef` — Mutable values & DOM access

## 🧠 Concept

`useRef` stores a **mutable value that does NOT trigger re-renders**.

It has two major uses:

1. Access DOM elements
2. Store persistent values

---

## 📌 Syntax

```js
const ref = useRef(initialValue);
```

---

## ✅ Example 1: Access DOM

```js
import React, { useRef } from "react";

export default function InputFocus() {
  const inputRef = useRef();

  const focusInput = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input ref={inputRef} />
      <button onClick={focusInput}>Focus Input</button>
    </div>
  );
}
```

---

## ✅ Example 2: Store previous value

```js
import React, { useState, useRef, useEffect } from "react";

export default function PreviousValue() {
  const [count, setCount] = useState(0);
  const prevCount = useRef();

  useEffect(() => {
    prevCount.current = count;
  }, [count]);

  return (
    <div>
      <h2>Current: {count}</h2>
      <h3>Previous: {prevCount.current}</h3>
      <button onClick={() => setCount(count + 1)}>+</button>
    </div>
  );
}
```

---

## ⚡ Why it matters

* Doesn’t cause re-renders
* Persists across renders
* Useful for timers, DOM, previous state

---

# 🔥 Key Differences Summary

| Hook        | Purpose                         | Causes Re-render? |
| ----------- | ------------------------------- | ----------------- |
| useReducer  | Complex state management        | ✅ Yes             |
| useMemo     | Memoize computed values         | ❌ No              |
| useCallback | Memoize functions               | ❌ No              |
| useRef      | Store mutable values / DOM refs | ❌ No              |

---

# 🧠 Quick Mental Model

* `useReducer` → **"Manage complex state cleanly"**
* `useMemo` → **"Cache results"**
* `useCallback` → **"Cache functions"**
* `useRef` → **"Store without re-render"**
