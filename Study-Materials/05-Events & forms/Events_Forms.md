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


---

# ⚡ Handling Events in React

---

## 📌 What is Event Handling?

Event handling in React means **responding to user actions** (click, input, submit) using functions.

Event handlers are written as **functions and passed to JSX elements**.

---

### 💻 Example

```js
function handleClick() {
  console.log("Button clicked");
}

<button onClick={handleClick}>Click</button>
```

### 🎯 Passing Arguments to Event Handlers

You can pass arguments using arrow functions.
```js
<button onClick={() => handleClick(id)}>Click</button>
```
## ⭐ Common Events
- onClick
- onChange
- onSubmit
- onKeyDown
- onMouseOver

### 🎯 Handling Events – Interview Questions & Answers

**Q1. How do you handle events in React?**  
A: By passing a function to the event handler.

**Q2. Can you pass parameters to event handlers?**  
A: Yes, using arrow functions.

**Q3. What happens if you call function directly in JSX?**  
A: It executes immediately during render.

**Q4. Why are arrow functions commonly used?**
A: To avoid binding issues and pass parameters easily.

### ⚠️ Common Mistakes
- Calling function instead of passing it
``
❌ onClick={handleClick()}
✅ onClick={handleClick}
``
- Not using arrow function when passing parameters
- Using incorrect event names