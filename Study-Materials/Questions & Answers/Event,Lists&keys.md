# 🔹 1. Event Handling in React

## ✅ Basic Questions

**Q1. What is event handling in React?**
Event handling in React allows you to respond to user actions like clicks, input changes, form submissions, etc., using functions.

**Q2. How is event handling different in React vs HTML?**

* React uses **camelCase** (`onClick`) instead of lowercase (`onclick`)
* You pass a **function**, not a string

```jsx
<button onClick={handleClick}>Click</button>
```

**Q3. How do you pass arguments to event handlers?**

```jsx
<button onClick={() => handleClick("Hello")}>Click</button>
```

**Q4. What is Synthetic Event in React?**
React wraps native events in a **SyntheticEvent**, which provides consistent behavior across browsers.

---
## 🚀 Advanced Questions

**Q5. What is event delegation in React?**
React attaches a single event listener at the root (via its virtual DOM system) instead of adding listeners to each element → improves performance.


**Q6. Why do we need to bind event handlers in class components?**
Because `this` is undefined in regular functions.

```jsx
this.handleClick = this.handleClick.bind(this);
```

OR use arrow function:

```jsx
handleClick = () => {}
```


**Q7. How do you prevent default behavior?**

```jsx
function handleSubmit(e) {
  e.preventDefault();
}
```


**Q8. What are inline event handlers vs separate handlers?**

* Inline: `onClick={() => doSomething()}`
* Separate: `onClick={doSomething}`

Separate handlers are better for performance and readability.
---
# 🔹 2. Conditional Rendering

## ✅ Basic Questions

**Q1. What is conditional rendering?**
Rendering UI based on conditions (like `if`, `ternary`, etc.)

**Q2. What are common ways to do conditional rendering?**

1. **if statement**

```jsx
if (isLoggedIn) return <Dashboard />;
```

2. **Ternary operator**

```jsx
{isLoggedIn ? <Dashboard /> : <Login />}
```

3. **Logical AND (&&)**

```jsx
{isAdmin && <AdminPanel />}
```



**Q3. What happens if condition is false in `&&`?**
React renders nothing.

---

## 🚀 Advanced Questions

**Q4. Difference between ternary and &&?**

* `&&` → render only if true
* ternary → handles both true & false cases


**Q5. How do you conditionally apply styles/classes?**

```jsx
<div className={isActive ? "active" : "inactive"}></div>
```

**Q6. How to avoid nested ternary complexity?**

* Use helper functions
* Break UI into components


**Q7. Can you store JSX in variables?**
Yes:

```jsx
let content;
if (isLoggedIn) content = <Dashboard />;
else content = <Login />;
```
---

# 🔹 3. Lists & Keys

## ✅ Basic Questions

**Q1. How do you render lists in React?**
Using `.map()`:

```jsx
const items = [1,2,3];
items.map(item => <li>{item}</li>);
```

**Q2. What is a key in React?**
A key is a unique identifier used to track elements in a list.

---

**Q3. Why are keys important?**
They help React efficiently update the DOM (reconciliation process).
---

## 🚀 Advanced Questions

**Q4. Why should keys be unique?**
To correctly identify which item changed, added, or removed.


**Q5. Can we use index as key?**
Yes, but **not recommended** if:

* list can reorder
* items can be added/removed

Because it can cause UI bugs.


**Q6. What happens if keys are not used?**
React shows warning and performance decreases.

**Q7. What is reconciliation in React?**
React compares previous and current virtual DOM → updates only changed elements using keys.

---

**Q8. Best practices for keys?**

* Use unique IDs from data
* Avoid random values
* Avoid array index when possible

---

# 🔥 Bonus Interview Questions (Mixed Advanced)

**Q1. How does React optimize list rendering?**
Using keys + diffing algorithm (reconciliation).

---

**Q2. Can keys be reused across different lists?**
Yes, keys must be unique only among siblings.

---

**Q3. What is controlled event handling?**
Handling form inputs using state.

```jsx
<input value={name} onChange={(e) => setName(e.target.value)} />
```

---

**Q4. What is the difference between controlled and uncontrolled components?**

* Controlled → React manages state
* Uncontrolled → DOM manages state

---

# 🎯 Quick Revision Cheat Sheet

| Topic                 | Key Point                         |
| --------------------- | --------------------------------- |
| Event Handling        | Uses camelCase, Synthetic Events  |
| Conditional Rendering | if, ternary, &&                   |
| Lists                 | use `.map()`                      |
| Keys                  | unique, avoid index               |
| Performance           | event delegation + reconciliation |

