# ⚛️ Hooks in React (Overview + Advanced)

---

# 📌 What are Hooks?

Hooks are special functions introduced in React 16.8 that allow **functional components to use state and lifecycle features** without using class components.

---

# 🎯 Why Hooks?

- Avoid class components  
- Reuse logic easily  
- Cleaner and readable code  
- Better separation of concerns  

---

# 📏 Rules of Hooks

- Call hooks only at the **top level**  
- Call hooks only inside **React functions**  
- Do not call hooks inside **loops, conditions, or nested functions**  

---

# 🎯 Hooks Overview – Interview Questions & Answers

**Q1. What are hooks in React?**  
A: Functions that allow functional components to use state and lifecycle features.

**Q2. Why were hooks introduced?**  
A: To simplify state and lifecycle management.

**Q3. Can hooks be used in class components?**  
A: No.

**Q4. What are the rules of hooks?**  
A: Call at top level and only inside React functions.

---

# 🚀 MOST IMPORTANT HOOKS

## 1. useState

Used to manage state in functional components.

```js
const [count, setCount] = useState(0);
```

## 2. useEffect

Used to handle side effects (API calls, subscriptions, etc.)
```js
useEffect(() => {
  console.log("Component mounted");
}, []);
```
