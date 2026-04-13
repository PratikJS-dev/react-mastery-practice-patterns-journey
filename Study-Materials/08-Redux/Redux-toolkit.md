# 🧠 Redux Toolkit (RTK) — Simple Explanation

Redux Toolkit is the **modern and recommended way to use Redux**.

👉 It removes most of Redux’s complex boilerplate and makes Redux **easy, fast, and clean**.

# 💡 First: Why Redux Toolkit?

Old Redux problems:

* Too much code (actions, reducers, constants)
* Confusing setup
* Repetitive patterns
* Hard for beginners

👉 Redux Toolkit solves this.

# ⚡ Simple Meaning

👉 Redux Toolkit = “Redux made easy with shortcuts built-in”

You don’t manually write:

* action types
* switch-case reducers
* long setup code

RTK does it for you.

---

# 🧩 Main Concepts in Redux Toolkit

## 1. `configureStore`

👉 Creates store easily

## 2. `createSlice`

👉 Combines:

* state
* reducers
* actions (auto-generated!)

## 3. `useSelector`

👉 Read data from store

## 4. `useDispatch`

👉 Update data

---

# 🚀 Simple Example: Counter App

## 📦 Step 1: Install

```bash
npm install @reduxjs/toolkit react-redux
```

---

# 🏪 Step 2: Create Slice

```js id="slice1"
import { createSlice } from "@reduxjs/toolkit";

const counterSlice = createSlice({
  name: "counter",

  initialState: {
    count: 0,
  },

  reducers: {
    increment: (state) => {
      state.count += 1;
    },

    decrement: (state) => {
      state.count -= 1;
    },

    addByValue: (state, action) => {
      state.count += action.payload;
    },
  },
});

export const { increment, decrement, addByValue } = counterSlice.actions;
export default counterSlice.reducer;
```

---

# 🏪 Step 3: Create Store

```js id="store1"
import { configureStore } from "@reduxjs/toolkit";
import counterReducer from "./counterSlice";

const store = configureStore({
  reducer: {
    counter: counterReducer,
  },
});

export default store;
```

---

# 🧠 Step 4: Provide Store

```js id="provider1"
import { Provider } from "react-redux";
import store from "./store";

root.render(
  <Provider store={store}>
    <App />
  </Provider>
);
```

---

# 🧾 Step 5: Use in Component

```js id="component1"
import { useSelector, useDispatch } from "react-redux";
import { increment, decrement, addByValue } from "./counterSlice";

function Counter() {
  const count = useSelector((state) => state.counter.count);
  const dispatch = useDispatch();

  return (
    <div>
      <h1>{count}</h1>

      <button onClick={() => dispatch(increment())}>+</button>

      <button onClick={() => dispatch(decrement())}>-</button>

      <button onClick={() => dispatch(addByValue(5))}>
        Add 5
      </button>
    </div>
  );
}
```

---

# 🧠 What’s happening (super simple)

### Old Redux:

You had to manually:

* define action types
* create actions
* write switch-case reducer

---

### Redux Toolkit:

👉 You just write “features”

Example:

```js
increment: (state) => {
  state.count += 1;
}
```

RTK automatically:

* creates action
* handles immutability safely
* wires everything

---

# ⚡ Key Feature: “Mutating state is allowed”

This looks wrong but is correct:

```js
state.count += 1;
```

👉 RTK uses a library called **Immer** internally
So it safely converts it into immutable updates.

---

# 🎯 Why Redux Toolkit is better

| Feature       | Old Redux | Redux Toolkit |
| ------------- | --------- | ------------- |
| Code length   | Long      | Short         |
| Setup         | Complex   | Easy          |
| Boilerplate   | High      | Very low      |
| Best practice | Manual    | Built-in      |

---

# 🧠 Real-world idea

Think like this:

### 🧱 Old Redux:

You build a house brick by brick manually

### 🧰 Redux Toolkit:

You get a pre-built smart construction kit

---

# 🚀 When to use Redux Toolkit?

Use RTK when:

* app has shared state (auth, cart, user data)
* medium to large applications
* multiple components need same data

---

# 🔥 Summary

👉 Redux Toolkit is:

* modern Redux
* easier Redux
* recommended official way
* reduces 70% of Redux code
* safer and cleaner

