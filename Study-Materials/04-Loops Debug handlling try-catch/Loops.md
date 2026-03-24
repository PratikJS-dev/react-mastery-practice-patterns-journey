# 🔁 Loops & Iterations (JavaScript)

---

## 📌 What are Loops?

- Loops are used to **execute a block of code multiple times**  
- Iteration means **repeating a set of instructions**  
- Loops help **reduce repetitive code**

---

## 🔄 Types of Loops in JavaScript

- for loop  
- while loop  
- do...while loop  
- for...in loop  
- for...of loop  

---

## 💻 Examples

### 1. for loop

```js
for (let i = 1; i <= 3; i++) {
  console.log(i);
}

```

### 2. While loop
```js
let i = 1;
while (i <= 3) {
  console.log(i);
  i++;
}
```
### 3. for-of loop

```js
let arr = [10, 20, 30];

for (let value of arr) {
  console.log(value);
}

```

### 4. for-in loop
```js
let obj = { a: 1, b: 2 };

for (let key in obj) {
  console.log(key);
}
```
---
## 📊 for...in vs for...of
| Feature       | for...in       | for...of                   |
| ------------- | -------------- | -------------------------- |
| Iterates over | Keys / Indexes | Values                     |
| Used for      | Objects        | Arrays, Strings, Iterables |
| Output        | Key names      | Actual values              |

---

## 🎯 Interview Questions & Answers

**Q1. Difference between for...in and for...of?**
A: for...in iterates over keys/indexes, while for...of iterates over values.

**Q2. When should you use a while loop?**
A: When the number of iterations is not known in advance.

**Q3. Does for...of work with objects?**
A: No, it works with iterable objects like arrays and strings.

**Q4. What is an infinite loop?**
A: A loop that never terminates because its condition always remains true.