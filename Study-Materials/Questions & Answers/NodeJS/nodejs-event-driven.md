# 🟢 Node.js Interview Q&A

## 🔹 1. What is Node.js?

**Answer:**
Node.js is a JavaScript runtime built on Chrome’s V8 engine that allows running JavaScript on the server-side. It is designed for building scalable, fast, and non-blocking applications.

---

## 🔹 2. Is Node.js single-threaded?

**Answer:**
Yes, Node.js uses a single-threaded event loop, but it can handle multiple concurrent operations using asynchronous, non-blocking I/O.

---

## 🔹 3. What is non-blocking I/O?

**Answer:**
Non-blocking I/O allows Node.js to execute other tasks while waiting for operations like file reading or API calls to complete.

---

## 🔹 4. What is the event loop?

**Answer:**
The event loop is the core mechanism that handles asynchronous operations in Node.js by executing callbacks from the queue.

---

## 🔹 5. What is event-driven architecture?

**Answer:**
Event-driven architecture is a design pattern where actions are triggered by events. Node.js uses events and listeners to handle asynchronous operations.

---

## 🔹 6. What are events in Node.js?

**Answer:**
Events are signals that something has happened (e.g., request received, file read completed).

---

## 🔹 7. What is EventEmitter?

**Answer:**
EventEmitter is a core module in Node.js used to create and handle custom events.

---

## 🔹 8. Difference between synchronous and asynchronous code?

**Answer:**

* Synchronous → executes line by line (blocking)
* Asynchronous → executes without blocking

---

## 🔹 9. Why Node.js is fast?

**Answer:**

* Uses V8 engine
* Non-blocking I/O
* Event-driven architecture

---

## 🔹 10. Where is Node.js used?

**Answer:**

* APIs
* Real-time apps (chat apps)
* Streaming apps
* Microservices

---

# 💻 Coding Questions

---

## 🧩 Coding Question 1: Basic HTTP Server

### Problem:

Create a simple Node.js server that returns "Hello World".

### Solution:

```js id="n1srv1"
const http = require("http");

const server = http.createServer((req, res) => {
  res.write("Hello World");
  res.end();
});

server.listen(3000, () => {
  console.log("Server running on port 3000");
});
```

---

## 🧩 Coding Question 2: Custom Event with EventEmitter

### Problem:

Create a custom event called `greet` and trigger it.

### Solution:

```js id="n2evt2"
const EventEmitter = require("events");

const emitter = new EventEmitter();

// listener
emitter.on("greet", (name) => {
  console.log(`Hello, ${name}`);
});

// trigger event
emitter.emit("greet", "John");
```

---

# ⚡ Bonus Interview Questions

### Q: What is callback hell?

**Answer:**
Nested callbacks that make code hard to read and maintain.

---

### Q: How to avoid callback hell?

**Answer:**
Use Promises or async/await.

---

### Q: What is a stream?

**Answer:**
A way to handle data piece by piece instead of loading all at once.

---

# 🎯 Quick Summary

* Node.js = server-side JS runtime
* Event loop = handles async tasks
* Event-driven = actions triggered by events
* EventEmitter = create custom events

* **Advanced Node.js interview Q&A (event loop deep, streams, clustering)**
* OR **Top real interview questions asked in companies** 🚀
