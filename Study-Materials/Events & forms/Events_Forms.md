# ⚡ Events in React

---

## 📌 What are Events in React?

Events are actions triggered by users such as:
- Clicking a button  
- Typing in an input  
- Submitting a form  

React events are called **Synthetic Events**, which wrap native browser events for better cross-browser compatibility.


## ⭐ Key Characteristics

- Event names use **camelCase** (e.g., onClick, onChange)  
- Event handlers are passed as **functions**  
- Default behavior can be prevented using `preventDefault()`  


### 💻 Example

```js
function handleClick() {
  console.log("Button clicked");
}

<button onClick={handleClick}>Click</button>

```
---
### 🎯 Events – Interview Questions & Answers

**Q1. What are events in React?**  
A: User interactions like clicks, inputs, and form submissions.

**Q2. How are React events different from HTML events?**  
A: React uses camelCase and passes functions instead of strings.

**Q3. What is a synthetic event?**  
A: A cross-browser wrapper around native events.

**Q4. How do you prevent page reload on form submit?**  
A: Using event.preventDefault().
