# ⚠️ Error Handling in JavaScript

---

# 📌 What is Error Handling?

- Error handling helps manage **runtime errors**  
- Prevents application crashes  
- Improves user experience  



# ❗ Types of Errors

- Syntax Errors → Mistakes in code structure  
- Runtime Errors → Errors during execution  
- Logical Errors → Incorrect logic, no crash  


# ⚙️ Error Handling in JavaScript

JavaScript provides:
- try  
- catch  
- finally  



# 🎯 Error Handling – Interview Questions & Answers

**Q1. What is error handling?**  
A: Error handling is the process of managing errors that occur during program execution.

**Q2. What are the types of errors in JavaScript?**  
A: Syntax errors, runtime errors, and logical errors.

**Q3. Can JavaScript handle runtime errors?**  
A: Yes, runtime errors can be handled using try...catch.

---

# 🧩 TRY...CATCH

## 📌 What is try...catch?

- `try` block contains code that may throw an error  
- `catch` block handles the error  
- `finally` block executes whether an error occurs or not  


## 💻 Example

```js id="k2p9as"
try {
  let result = x + 10;
} catch (error) {
  console.log(error.message);
} finally {
  console.log("Execution completed");
}
```


## 🎯 Try...Catch – Interview Questions & Answers

**Q1. What is the purpose of try...catch?**  
A: It allows handling runtime errors without stopping program execution.

**Q2. Can we use try without catch?**  
A: Yes, try can be used with finally only.

**Q3. What does finally do?**  
A: finally executes regardless of whether an error occurs or not.

**Q4. Can try...catch handle asynchronous errors?**  
A: No, it cannot handle asynchronous errors directly.

---
### ⚠️ Common Mistakes
 - Not handling errors properly
 - Ignoring error messages
 - Using try...catch for all logic (not recommended)
 - Expecting it to handle async errors

### 🧠 Quick Revision
 - Error handling improves app stability
 - try → risky code
 - catch → handles error
 - finally → always runs
 - Does not handle async errors directly
