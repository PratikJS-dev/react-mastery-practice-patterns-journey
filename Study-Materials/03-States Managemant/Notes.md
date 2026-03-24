# 🔄 State Management

---

## 📌 What is State?

State is a **built-in object** in React that stores **component-specific, mutable data**.

When the state changes, the component **re-renders automatically**.

---

## 🎯 Why State Management?

- Handle dynamic data  
- Control UI behavior  
- Manage user interactions  

---

## ⭐ Key Points

- State is local to a component  
- State changes trigger re-render  
- State should not be mutated directly  

---

## 🎯 State Management – Interview Questions & Answers

**Q1. What is state in React?**  
A: State is an object that holds dynamic data for a component.

**Q2. Why do we need state?**  
A: To manage data that changes over time.

**Q3. What happens when state updates?**    
A: React re-renders the component.

**Q4. Can state be shared between components?**  
A: Yes, by lifting state up or using global state.

---
# 🔄 useState Hook & setState

---

# ⚛️ useState HOOK

## 📌 What is useState?

`useState` is a **React Hook** that allows functional components to use state.

---

# 🧾 Syntax

```js
const [count, setCount] = useState(0);
```

---
# ⚙️ How useState Works
- Returns current state value
- Returns a function to update state
- Updating state triggers re-render

## 🎯 useState – Interview Questions & Answers

**Q1. What does useState return?**  
A: An array with state value and setter function.

**Q2. Can we use multiple useState hooks?**  
A: Yes, multiple times in the same component.

**Q3. Is useState synchronous?**  
A: No, state updates are asynchronous.

**Q4. Why use functional update in useState?**  
A: To safely update based on previous state.

## 💻 Example (Functional Update)
```js
setCount(prev => prev + 1);
```
# 🏛️ setState (Class Components)

## 📌 What is setState?

- setState is a method used in class components to update state.

##💻 Example
```js
this.setState({ count: this.state.count + 1 });
```
## ⚠️ Important Rules
- setState is asynchronous
- Do not mutate state directly
- Can accept a callback function

## 💻 Example (Functional setState)
```js
this.setState(
  prevState => ({ count: prevState.count + 1 }),
  () => console.log("Updated")
);
```

## 🎯 setState – Interview Questions & Answers

**Q1. Why is setState asynchronous?**  
A: To improve performance by batching updates.

**Q2. Can we update state directly?**  
A: No, it can cause unpredictable behavior.

**Q3. What is batching?**  
A: Grouping multiple state updates into one re-render.

**Q4. Difference between setState and useState?** 
A: setState is for class components, useState is for functional components.


---
# 🔄 State vs Props

---

## 📊 Differences Between State and Props

| Feature        | State                              | Props                              |
|----------------|-----------------------------------|------------------------------------|
| Nature         | Mutable                           | Immutable (read-only)              |
| Ownership      | Managed within component          | Passed from parent component       |
| Purpose        | Store dynamic data                | Configure component behavior       |
| Data Flow      | Internal                          | External (parent → child)          |
| Change         | Changes over time                 | Changes when parent updates        |

---

## 🎯 State vs Props – Interview Questions & Answers

**Q1. What is the main difference between state and props?**  
A: State is internal and mutable, while props are external and read-only.

**Q2. Can props change?** 
A: Yes, when the parent component updates.

**Q3. Can state be passed as props?**  
A: Yes, state can be passed to child components as props.

**Q4. Can child modify props?**  
A: No.

---

## 🎯 Common Interview Scenario Questions

**Q1. When should you lift state up?**  
A: When multiple components need shared state.

**Q2. What causes re-render in React?**  
A: Changes in state or props.

**Q3. How to prevent unnecessary re-renders?**  
A: Use memoization (React.memo, useMemo, useCallback) and proper state updates.

---

## 🧠 Quick Revision

- State = internal & mutable  
- Props = external & read-only  
- Props flow parent → child  
- State changes trigger re-render  
- Lift state when sharing is needed  

---
