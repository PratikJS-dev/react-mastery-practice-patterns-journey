# 🔷 PART 1: Context API

---

## ✅ BASIC INTERVIEW Q&A

### ❓ What is Context API?

👉 A way to **share data globally across components** without passing props manually at every level.

---

### ❓ Why do we need Context API?

👉 To avoid **prop drilling** (passing props through many layers).

---

### ❓ What is prop drilling?

👉 Passing data from parent → child → grandchild unnecessarily.

---

### ❓ What are main parts of Context API?

| Part          | Purpose        |
| ------------- | -------------- |
| createContext | Create context |
| Provider      | Provide data   |
| useContext    | Consume data   |

---

### ❓ Syntax of Context API?

```js
const MyContext = React.createContext();

<MyContext.Provider value={data}>
  <App />
</MyContext.Provider>

const value = useContext(MyContext);
```

---

## 🚀 ADVANCED INTERVIEW Q&A

### ❓ When should you use Context API?

* Global data like:

  * Auth (user)
  * Theme
  * Language
  * Settings

---

### ❓ When should you NOT use Context?

* Frequently changing data (can cause re-renders)
* Local component state

---

### ❓ What is the problem with Context API?

👉 **Performance issue**

* When value changes → ALL consuming components re-render

---

### ❓ How to optimize Context API?

* Split contexts (instead of one big context)
* Memoize values

```js
const value = useMemo(() => ({ user }), [user]);
```

---

### ❓ Context vs Redux?

| Context    | Redux            |
| ---------- | ---------------- |
| Built-in   | External library |
| Simple     | Powerful         |
| Small apps | Large apps       |

---

## 💻 CODING QUESTION

### 🔹 Create Theme Context

```js
import React, { createContext, useContext, useState } from "react";

const ThemeContext = createContext();

function App() {
  const [theme, setTheme] = useState("light");

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      <Child />
    </ThemeContext.Provider>
  );
}

function Child() {
  return <DeepChild />;
}

function DeepChild() {
  const { theme, setTheme } = useContext(ThemeContext);

  return (
    <div>
      <h2>Theme: {theme}</h2>
      <button onClick={() => setTheme("dark")}>Dark</button>
    </div>
  );
}

export default App;
```

---

## ⚠️ COMMON PROBLEMS

### ❌ Problem 1: Too many re-renders

👉 Solution: useMemo / split context

---

### ❌ Problem 2: Large context object

👉 Solution: create multiple contexts

---

### ❌ Problem 3: Using context for everything

👉 Solution: use local state where needed

---

---

# 🔷 PART 2: CUSTOM HOOKS

---

## ✅ BASIC INTERVIEW Q&A

### ❓ What is a custom hook?

👉 A **reusable function** that uses React hooks.

---

### ❓ Naming rule?

👉 Must start with **use**

```js
useFetch
useAuth
useWindowWidth
```

---

### ❓ Why use custom hooks?

* Reusability
* Clean code
* Separation of logic

---

## 🚀 ADVANCED INTERVIEW Q&A

### ❓ Can custom hooks share state?

👉 YES, but each call creates **separate instance**

---

### ❓ Can custom hooks use other hooks?

👉 YES

```js
useState
useEffect
useContext
```

---

### ❓ Difference between custom hook & normal function?

| Custom Hook                | Normal Function |
| -------------------------- | --------------- |
| Uses React hooks           | Doesn't         |
| Must follow rules of hooks | No restriction  |

---

### ❓ What are rules of hooks?

* Only call at top level
* Only call inside React function or custom hook

---

## 💻 CODING QUESTIONS

---

### 🔹 Question 1: Create useWindowWidth hook

```js
import { useState, useEffect } from "react";

function useWindowWidth() {
  const [width, setWidth] = useState(window.innerWidth);

  useEffect(() => {
    const handleResize = () => setWidth(window.innerWidth);

    window.addEventListener("resize", handleResize);

    return () => window.removeEventListener("resize", handleResize);
  }, []);

  return width;
}

export default useWindowWidth;
```

---

### 🔹 Use it

```js
function App() {
  const width = useWindowWidth();

  return <h2>Width: {width}</h2>;
}
```

---

### 🔹 Question 2: Create useFetch hook

```js
import { useState, useEffect } from "react";

function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch(url)
      .then(res => res.json())
      .then(data => {
        setData(data);
        setLoading(false);
      });
  }, [url]);

  return { data, loading };
}
```

---

### 🔹 Use it

```js
function App() {
  const { data, loading } = useFetch("https://jsonplaceholder.typicode.com/posts");

  if (loading) return <h2>Loading...</h2>;

  return <pre>{JSON.stringify(data, null, 2)}</pre>;
}
```

---

## ⚠️ COMMON PROBLEMS

---

### ❌ Problem 1: Breaking rules of hooks

👉 Calling inside conditions

```js
if (condition) {
  useEffect(); ❌
}
```

---

### ❌ Problem 2: Infinite loop in useEffect

👉 Wrong dependencies

```js
useEffect(() => {}, []); // correct
```

---

### ❌ Problem 3: Not handling cleanup

👉 Leads to memory leaks

```js
return () => window.removeEventListener();
```

---

---

# 🔥 COMBINED ADVANCED QUESTION

---

### ❓ Use Context + Custom Hook together

👉 Best practice in real projects

---

## 💻 Example

```js
import React, { createContext, useContext, useState } from "react";

const UserContext = createContext();

function useUser() {
  return useContext(UserContext);
}

function App() {
  const [user, setUser] = useState("John");

  return (
    <UserContext.Provider value={{ user, setUser }}>
      <Child />
    </UserContext.Provider>
  );
}

function Child() {
  const { user } = useUser();
  return <h2>Hello {user}</h2>;
}
```

---

# 🧠 FINAL INTERVIEW SUMMARY

---

## 🔹 Context API

👉 Share global data
👉 Avoid prop drilling
👉 Watch performance

---

## 🔹 Custom Hooks

👉 Reuse logic
👉 Cleaner code
👉 Must follow hook rules

---

## 🔹 Golden Tip

👉 **Context = data sharing**
👉 **Custom Hook = logic reuse**

