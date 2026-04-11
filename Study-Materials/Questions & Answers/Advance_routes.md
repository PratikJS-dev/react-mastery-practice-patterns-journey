# 🔷 PART 1: BASIC ROUTING Q&A

---

## ✅ ❓ What is React Router?

👉 A library to **navigate between pages without reloading the browser**.


## ✅ ❓ What are main components?

| Component       | Purpose                  |
| --------------- | ------------------------ |
| `BrowserRouter` | Wraps the app            |
| `Routes`        | Group of routes          |
| `Route`         | Defines path + component |
| `Link`          | Navigation               |

---

## ✅ ❓ Basic Example

```js
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <Link to="/">Home</Link>
      <Link to="/about">About</Link>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

## ✅ ❓ Difference: `Link` vs `<a>` tag?

| Link      | `<a>`        |
| --------- | ------------ |
| No reload | Reloads page |
| Fast      | Slow         |

---

## ✅ ❓ What is `useNavigate`?

👉 Used to navigate programmatically

```js
import { useNavigate } from "react-router-dom";

const navigate = useNavigate();

navigate("/dashboard");
```

---

---

# 🔷 PART 2: INTERMEDIATE QUESTIONS

---

## 🚀 ❓ What is Dynamic Routing?

👉 URL with parameters

```js
<Route path="/user/:id" element={<User />} />
```

---

### 🔹 Access param

```js
import { useParams } from "react-router-dom";

const { id } = useParams();
```

---

## 💻 Coding Question

### 🔹 Show user ID from URL

```js
function User() {
  const { id } = useParams();
  return <h2>User ID: {id}</h2>;
}
```

---

---

## 🚀 ❓ What is Nested Routing?

👉 Routes inside routes

```js
<Route path="/dashboard" element={<Dashboard />}>
  <Route path="profile" element={<Profile />} />
</Route>
```

---

### 🔹 Why use `Outlet`?

👉 To render child routes

```js
import { Outlet } from "react-router-dom";

function Dashboard() {
  return (
    <div>
      <h2>Dashboard</h2>
      <Outlet />
    </div>
  );
}
```

---

---

# 🔷 PART 3: ADVANCED QUESTIONS

---

## 🚀 ❓ What is Lazy Loading in routing?

👉 Load components only when needed

---

### 💻 Example

```js
import { lazy, Suspense } from "react";

const Home = lazy(() => import("./Home"));

<Suspense fallback={<h2>Loading...</h2>}>
  <Route path="/" element={<Home />} />
</Suspense>
```

---

---

## 🚀 ❓ What is Protected Route?

👉 Restrict access if user not logged in

---

### 💻 Example

```js
import { Navigate } from "react-router-dom";

function ProtectedRoute({ children }) {
  const isAuth = false;

  return isAuth ? children : <Navigate to="/login" />;
}
```

---

---

## 🚀 ❓ What is Role-Based Routing?

👉 Access based on user role

---

### 💻 Example

```js
function RoleRoute({ children, role }) {
  const userRole = "user";

  return userRole === role ? children : <h2>Access Denied</h2>;
}
```

---

---

## 🚀 ❓ What is `useLocation`?

👉 Gives current URL info

```js
import { useLocation } from "react-router-dom";

const location = useLocation();
console.log(location.pathname);
```

---

---

## 🚀 ❓ What is `Navigate`?

👉 Used to redirect

```js
<Navigate to="/login" />
```

---

---

# 🔷 PART 4: CODING PROBLEMS

---

## 💻 Problem 1: Protected Dashboard

👉 Redirect if not logged in

```js
<Route
  path="/dashboard"
  element={
    <ProtectedRoute>
      <Dashboard />
    </ProtectedRoute>
  }
/>
```

---

---

## 💻 Problem 2: Dynamic Product Page

👉 URL: `/product/101`

```js
<Route path="/product/:id" element={<Product />} />
```

```js
function Product() {
  const { id } = useParams();
  return <h2>Product {id}</h2>;
}
```

---

---

## 💻 Problem 3: Nested Routing

```js
<Route path="/settings" element={<Settings />}>
  <Route path="profile" element={<Profile />} />
  <Route path="account" element={<Account />} />
</Route>
```

---

---

## 💻 Problem 4: Redirect After Login

```js
const navigate = useNavigate();

function login() {
  navigate("/dashboard");
}
```

---

---

## 💻 Problem 5: Lazy Loaded Routes

```js
const Dashboard = lazy(() => import("./Dashboard"));

<Suspense fallback={<h2>Loading...</h2>}>
  <Route path="/dashboard" element={<Dashboard />} />
</Suspense>
```

---

---

# 🔷 PART 5: COMMON MISTAKES

---

## ❌ Missing `BrowserRouter`

👉 App won’t work

---

## ❌ Using `<a>` instead of `Link`

👉 Causes reload

---

## ❌ Wrong path in nested routes

👉 Use relative paths (`profile`, not `/profile`)

---

## ❌ Forgetting `Outlet`

👉 Child routes won’t render

---

## ❌ Infinite redirects

👉 Wrong auth logic

---

---

# 🔥 ADVANCED INTERVIEW QUESTIONS

---

### ❓ How to optimize routing performance?

* Lazy loading
* Code splitting
* Avoid unnecessary renders

---

### ❓ Difference: `useNavigate` vs `Navigate`?

| useNavigate       | Navigate    |
| ----------------- | ----------- |
| Hook              | Component   |
| Used in functions | Used in JSX |

---

### ❓ How to handle 404 page?

```js
<Route path="*" element={<h2>Page Not Found</h2>} />
```

---

---

# 🧠 FINAL SUMMARY

---

## 🔹 Core Concepts

* Routing → navigation
* Dynamic → params
* Nested → layout
* Lazy → performance
* Protected → auth
* Role-based → permissions

---

## 🔹 Golden Line (for interviews)

👉 “React Router enables client-side navigation with support for dynamic, nested, and protected routes while optimizing performance using lazy loading.”
