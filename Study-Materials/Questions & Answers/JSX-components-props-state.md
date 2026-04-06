# ⚛️ React Interview Q&A

## 🔹 JSX

### 1. What is JSX?

**Answer:**
JSX (JavaScript XML) is a syntax extension that allows writing HTML-like code inside JavaScript. It gets compiled into `React.createElement()`.

### 2. Can browsers understand JSX directly?

**Answer:**
No. JSX must be transpiled (e.g., using Babel) into regular JavaScript.

### 3. Difference between HTML and JSX?

**Answer:**

* `class` → `className`
* `for` → `htmlFor`
* Inline styles use objects
* Must return a single parent element

### 4. Can we write JavaScript inside JSX?

**Answer:**
Yes, using `{}`
Example:

```js
<h1>{name}</h1>
```

---

## 🔹 Components

### 5. What are components?

**Answer:**
Reusable, independent pieces of UI in React.

### 6. Types of components?

**Answer:**

* Functional components (modern)
* Class components (older)

### 7. What is a functional component?

**Answer:**
A JavaScript function that returns JSX.

### 8. What is component reusability?

**Answer:**
Using the same component multiple times with different data.

---

## 🔹 Props

### 9. What are props?

**Answer:**
Props (properties) are read-only inputs passed from parent to child components.


### 10. Can props be modified?

**Answer:**
No, props are immutable.

### 11. How to pass props?

**Answer:**

```js
<Child name="John" />
```

### 12. Props vs State?

**Answer:**

* Props → passed from parent, read-only
* State → managed inside component, mutable

---

## 🔹 State

### 13. What is state?

**Answer:**
State is a built-in object used to store data that can change over time.

### 14. How to create state in functional components?

**Answer:**

```js
const [count, setCount] = useState(0);
```

### 15. Why use state?

**Answer:**
To make components dynamic and interactive.


### 16. What happens when state changes?

**Answer:**
Component re-renders.

### 17. Can we update state directly?

**Answer:**
No. Must use setter function.

### 18. Is state async?

**Answer:**
Yes, updates may be asynchronous.

---

# 💻 Coding Questions

---

## 🧩 Coding Question 1: Counter App

### Problem:

Create a counter with increment & decrement buttons.

### Solution:

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h2>{count}</h2>
      <button onClick={() => setCount(count + 1)}>+</button>
      <button onClick={() => setCount(count - 1)}>-</button>
    </div>
  );
}

export default Counter;
```

---

## 🧩 Coding Question 2: Pass Props & Display

### Problem:

Create a parent component that passes a name to child and display it.

### Solution:

```jsx
function Child(props) {
  return <h2>Hello, {props.name}</h2>;
}

function Parent() {
  return <Child name="Alice" />;
}

export default Parent;
```

---

# ⚡ Bonus (Common Follow-up)

### Q: Why React uses components?

**Answer:**
To break UI into reusable, manageable pieces.

### Q: What is re-render?

**Answer:**
Updating UI when state/props change.


* **Advanced React interview Q&A (hooks, lifecycle, performance)**
* OR **Real company-level coding questions (React + JS combined)** 🚀
