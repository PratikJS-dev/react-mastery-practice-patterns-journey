# 🔷 1. Context API (Global State in React)

## 🧠 Simple Idea

👉 Context API lets you **share data across components without passing props manually at every level**.

Think of it like:

> 📡 “A global storage that any component can access directly”

---

## ❌ Problem (Without Context)

Passing props through many layers (called **prop drilling**):

```js
<App>
  <Parent user={user}>
    <Child user={user}>
      <DeepChild user={user} />
    </Child>
  </Parent>
</App>
```

😩 Messy and hard to maintain

---

## ✅ Solution (With Context)

Now you can directly access data anywhere:

```js
<DeepChild /> // gets user without props
```

---

## 📌 Steps to Use Context API

### 1. Create Context

```js
const UserContext = React.createContext();
```

---

### 2. Provide Context

```js
<UserContext.Provider value={user}>
  <App />
</UserContext.Provider>
```

---

### 3. Consume Context

```js
const user = useContext(UserContext);
```

---

## 💻 Example: User Login Context

```js
import React, { createContext, useContext, useState } from "react";

const UserContext = createContext();

function App() {
  const [user, setUser] = useState("John");

  return (
    <UserContext.Provider value={user}>
      <Child />
    </UserContext.Provider>
  );
}

function Child() {
  return <DeepChild />;
}

function DeepChild() {
  const user = useContext(UserContext);
  return <h2>Hello {user}</h2>;
}

export default App;
```

---

## ⚡ When to Use Context API

* Authentication (user data)
* Theme (dark/light mode)
* Language settings
* Global app data

---

## ⚠️ Important Notes

* Avoid overusing it (can cause re-renders)
* Best for **global/shared state**, not everything

---

# 🔷 2. Custom Hooks (Reusable Logic)

## 🧠 Simple Idea

👉 A custom hook is just a **function that uses React hooks and lets you reuse logic**.

Think:

> 🔁 “Write logic once, reuse everywhere”

---

## 📌 Rule

* Must start with **`use`**
* Can use other hooks inside

---

## ❌ Problem (Without Custom Hook)

You repeat the same logic:

```js
useEffect(() => {
  window.addEventListener("resize", handleResize);
  return () => window.removeEventListener("resize", handleResize);
}, []);
```

Used in many components 😩

---

## ✅ Solution: Custom Hook

---

## 💻 Example 1: Window Width Hook

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
```

---

### 🔹 Use it anywhere

```js
function App() {
  const width = useWindowWidth();

  return <h2>Width: {width}</h2>;
}
```

---

## 💻 Example 2: Fetch Data Hook

```js
import { useState, useEffect } from "react";

function useFetch(url) {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch(url)
      .then(res => res.json())
      .then(data => setData(data));
  }, [url]);

  return data;
}
```

---

### 🔹 Use it

```js
function App() {
  const data = useFetch("https://jsonplaceholder.typicode.com/posts");

  return <pre>{JSON.stringify(data, null, 2)}</pre>;
}
```

---

# 🔥 Context API vs Custom Hooks

| Feature     | Context API        | Custom Hooks  |
| ----------- | ------------------ | ------------- |
| Purpose     | Share global state | Reuse logic   |
| Scope       | App-wide           | Anywhere      |
| Reusability | Limited            | High          |
| Example     | Auth, Theme        | Fetch, Resize |

---

# 🧠 Combine Both (Real Interview Insight)

👉 Best practice: **Use Context + Custom Hook together**

---

## 💻 Example

```js
const UserContext = createContext();

export function useUser() {
  return useContext(UserContext);
}
```

Now instead of:

```js
const user = useContext(UserContext);
```

You use:

```js
const user = useUser();
```

✅ Cleaner
✅ Reusable
✅ Industry standard

---

# 🚀 Final Mental Model

* Context API → 📡 “Share data globally”
* Custom Hooks → 🔁 “Reuse logic easily”
