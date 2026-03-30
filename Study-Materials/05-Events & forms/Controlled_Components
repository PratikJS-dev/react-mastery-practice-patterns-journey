# 🧩 Controlled Components in React

---

## 📌 What is a Controlled Component?

A controlled component is a **form element whose value is controlled by React state**.

### 💻 Example

```js
import { useState } from "react";

function App() {
  const [name, setName] = useState("");

  return (
    <input
      value={name}
      onChange={(e) => setName(e.target.value)}
    />
  );
}
```
## ⭐ Benefits
- Single source of truth
- Easy validation
- Better control over form data

## 🔄 Controlled vs Uncontrolled Components
| Feature       | Controlled Component | Uncontrolled Component |
| ------------- | -------------------- | ---------------------- |
| Control       | React State          | DOM                    |
| Data Handling | Managed by React     | Managed by browser     |
| Validation    | Easy                 | Difficult              |
| Usage         | Recommended          | Less preferred         |

### 🎯 Controlled Components – Interview Questions & Answers

**Q1. What is a controlled component?**  
A: A form element managed by React state.

**Q2. Why use controlled components?**  
A: For validation and predictable form behavior.

**Q3. What is an uncontrolled component?**  
A: A form element controlled by the DOM using refs.

**Q4. Which approach is recommended?**  
A: Controlled components.

### 🎯 Common Interview Scenario Questions

**Q1. How do you handle multiple inputs in a form?**  
A: Use a single state object and update using the name attribute.

**Q2. What is the role of the name attribute in forms?**  
A: It helps identify inputs when handling multiple fields.

**Q3. Can controlled components cause performance issues?**  
A: Yes, in very large forms, but it is manageable.

### ⚠️ Common Mistakes
- Forgetting to bind value with state
- Not handling onChange properly
- Using uncontrolled inputs unintentionally
- Not using name attribute for multiple inputs
