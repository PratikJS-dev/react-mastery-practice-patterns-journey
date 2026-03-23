# React Basics & JSX 🚀

---

# 📌 What is React?

React is an open-source JavaScript library developed by Facebook for building fast, interactive user interfaces, especially Single Page Applications (SPAs). It follows a component-based architecture.

---

# ⭐ Key Features

- Component-based architecture  
- Declarative UI  
- Virtual DOM for better performance  
- One-way data binding  
- Reusable components  
- Strong community support  

---

# ✅ Advantages of React

- High performance  
- Reusable UI components  
- Easy to learn  
- SEO-friendly (with SSR)  
- Backed by Meta (Facebook)  

---

# ⚠️ Limitations

- Learning curve for beginners  
- Frequent updates  
- JSX may feel unusual initially  

---

# 🎯 React Interview Questions & Answers

**Q1. What is React?**  
A: React is a JavaScript library used to build user interfaces using reusable components and a virtual DOM.

**Q2. Is React a framework or a library?**  
A: React is a library because it focuses only on the view layer.

**Q3. What are components in React?**  
A: Components are reusable, independent pieces of UI.

**Q4. What is SPA?**  
A: A Single Page Application loads a single HTML page and updates content dynamically without page reloads.

**Q5. Why use React?**  
A: For better performance, reusable components, and maintainable UI code.

---

# 🌳 Virtual DOM

## 📌 What is Virtual DOM?

The Virtual DOM is a lightweight JavaScript representation of the real DOM. React updates the Virtual DOM first and then efficiently updates only the changed parts of the real DOM.

---

## ⚙️ How Virtual DOM Works

- State changes  
- New Virtual DOM is created  
- Diffing algorithm compares old and new VDOM  
- React updates only changed nodes in real DOM  

---

## ✅ Benefits

- Improved performance  
- Faster UI updates  
- Reduced direct DOM manipulation  

---

## 🎯 Virtual DOM Interview Questions

**Q1. What is Virtual DOM?**  
A: A virtual copy of the real DOM used to optimize updates.

**Q2. How is Virtual DOM faster?**  
A: It updates only changed elements instead of reloading the entire DOM.

**Q3. What is diffing?**  
A: The process of comparing old and new Virtual DOM trees.

**Q4. Does React update the real DOM directly?**  
A: No, React first updates the Virtual DOM.

**Q5. Is Virtual DOM unique to React?**  
A: No, other libraries also use similar concepts.

---

# 🧩 JSX

## 📌 What is JSX?

JSX stands for JavaScript XML. It allows writing HTML-like syntax inside JavaScript.

```js
const element = <h1>Hello React</h1>;
```
## ⭐ Why JSX?
- Improves readability
- Easier UI creation
- Prevents XSS attacks by escaping values
## 📏 JSX Rules
- Must return a single parent element
- Use className instead of class
- JavaScript expressions use {}

# 🎯 JSX Interview Questions

**Q1. What is JSX?**
A: JSX is a syntax extension that allows HTML in JavaScript.

**Q2. Is JSX mandatory?**
A: No, but it is recommended for readability.

**Q3. Why use className instead of class?**
A: Because class is a reserved keyword in JavaScript.

**Q4. Can we write JavaScript inside JSX?**
A: Yes, using curly braces {}.

**Q5. What happens to JSX in the browser?**
A: It is compiled to JavaScript using Babel.


# ⚙️ React Project Setup

---

# 📌 Introduction

Project setup is the process of creating and configuring a React application environment so you can start building UI components efficiently.

---

# 🚀 Ways to Create React App

## 1. Using Create React App (CRA)

Create React App is a tool that sets up a React project with pre-configured settings.

```bash
npx create-react-app my-app
cd my-app
npm start       
```
## 📌 Important Files
- index.js
- Entry point of the application
- Renders the root component
- App.js
- Root component
- Main UI logic starts here
- package.json
- Stores dependencies
- Contains scripts and metadata

## ▶️ Running the Application
Start Development Server
`npm start`

or

`npm run dev`
Build for Production
`npm run build`
## 📦 Installing Dependencies
`npm install package-name`


# 🎯 Project Setup – Interview Questions

**Q1. What is Create React App?**
A: A tool to quickly set up a React project with default configuration.

**Q2. Why is Vite preferred over CRA?**
A: It is faster and uses modern build tools.

**Q3. What is npm?**
A: Node Package Manager used to manage dependencies.

**Q4. What is package.json?**
A: It contains project metadata, dependencies, and scripts.

**Q5. What command starts a React app?**
A: npm start or npm run dev