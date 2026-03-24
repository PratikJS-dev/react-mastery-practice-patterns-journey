# 🧩 Components & Types of Components

---

# 📌 COMPONENTS

## What is a Component?

A component is a **reusable, independent piece of UI** in React.  
Every React application is built using components.

---

## 🔹 Types of Components

- Functional Components  
- Class Components  

---

## ⭐ Benefits of Components

- Reusability  
- Better code organization  
- Easy maintenance  
- Faster development  

---

#@ 🎯 Components – Interview Questions & Answers

**Q1. What is a component in React?**   
A: A reusable UI block that returns JSX.

**Q2. Why are components important?**  
A: They improve reusability and maintainability.

**Q3. Can a component return multiple elements?**  
A: No, it must return a single parent element (or Fragment).

**Q4. What is a reusable component?**  
A: A component that can be used multiple times with different data.

---
---

# ⚛️ FUNCTIONAL COMPONENTS

## 📌 What is a Functional Component?

A functional component is a **JavaScript function** that returns JSX.

---

## 💻 Example

```js
function Welcome() {
  return <h1>Hello React</h1>;
}
```
---
## 🎯 Functional Components – Interview Questions & Answers

**Q1. What is a functional component?**  
A: A JavaScript function that returns JSX.

**Q2. Why functional components are preferred?**  
A: They are simpler and support hooks.

**Q3. Can functional components use state?**  
A: Yes, using hooks like useState.

**Q4. Do functional components have lifecycle methods?**  
A: No, but hooks like useEffect handle lifecycle behavior.

---
---
# 🧩 Class Components

# ⚛️ CLASS COMPONENTS

## 📌 What is a Class Component?

A class component is a **JavaScript class** that extends `React.Component`.

---

## 💻 Example

```js
class Welcome extends React.Component {
  render() {
    return <h1>Hello React</h1>;
  }
}
``` 
# 🎯 Class Components – Interview Questions & Answers

**Q1. What is a class component?**  
A: A component created using ES6 class syntax.

**Q2. Why are class components less used now?**  
A: Functional components with hooks provide the same features with less complexity.

**Q3. What is render() method?**  
A: It returns JSX for the component UI.

**Q4. Can class components use hooks?**  
A: No, hooks are only for functional components.

---
---

## 📦 PROPS
# 📌 What are Props?

Props (properties) are read-only inputs passed from parent to child components.

💻 Example
```js
function Welcome(props) {
  return <h1>Hello {props.name}</h1>;
}
```
# ⭐ Props Characteristics
- Immutable (read-only)
- Passed from parent to child
- Help make components dynamic

# 🎯 Props – Interview Questions & Answers

**Q1. What are props?**  
A: Inputs passed to components to customize behavior.

**Q2. Can props be modified?**  
A: No, props are read-only.

**Q3. How do you pass props?**  
A: Using attributes in JSX.

**Q4. What is props drilling?**  
A: Passing props through multiple components.

**Q5. Difference between props and state?**  
A: Props are external and read-only, state is internal and mutable.
