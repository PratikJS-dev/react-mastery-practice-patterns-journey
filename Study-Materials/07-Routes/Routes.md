# 🔷 1. What is React Router?

## 🧠 Simple Idea

👉 React Router is used to **navigate between pages in a React app without reloading the page**.

Think:

> 🔗 “It makes your React app behave like a multi-page website”

---

# 🔷 2. Basic Routing (Step-by-Step)

---

## ✅ Step 1: Install React Router

```bash
npm install react-router-dom
```

---

## ✅ Step 2: Wrap App with Router

```js
import { BrowserRouter } from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <h1>My App</h1>
    </BrowserRouter>
  );
}
```

---

## ✅ Step 3: Define Routes

```js
import { Routes, Route } from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

## ✅ Step 4: Navigation (Links)

```js
import { Link } from "react-router-dom";

function Navbar() {
  return (
    <div>
      <Link to="/">Home</Link>
      <Link to="/about">About</Link>
    </div>
  );
}
```

---

## 💻 Basic Example

```js
function Home() {
  return <h2>Home Page</h2>;
}

function About() {
  return <h2>About Page</h2>;
}
```

---

# 🔷 3. Lazy Loading (Code Splitting)

## 🧠 Simple Idea

👉 Load components **only when needed**, not all at once.

> ⚡ Improves performance

---

## ✅ Step-by-Step

### Step 1: Use React.lazy

```js
import { lazy } from "react";

const Home = lazy(() => import("./Home"));
const About = lazy(() => import("./About"));
```

---

### Step 2: Wrap with Suspense

```js
import { Suspense } from "react";

<Suspense fallback={<h2>Loading...</h2>}>
  <Routes>
    <Route path="/" element={<Home />} />
    <Route path="/about" element={<About />} />
  </Routes>
</Suspense>
```

---

## 💡 Result

* Component loads **only when route is visited**
* Faster initial load 🚀

---

# 🔷 4. Conditional Routing (Protected Routes)

## 🧠 Simple Idea

👉 Show a route **only if a condition is true** (like user logged in)

---

## 💻 Example: Protected Route

```js
import { Navigate } from "react-router-dom";

function ProtectedRoute({ children }) {
  const isAuth = true; // fake auth

  return isAuth ? children : <Navigate to="/login" />;
}
```

---

### 🔹 Use it

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

## 💡 If not logged in:

👉 Redirects to `/login`

---

# 🔷 5. Nested / Parent-Child Routing

## 🧠 Simple Idea

👉 Routes inside routes (like layout + sub-pages)

---

## 💻 Example

```js
<Route path="/dashboard" element={<Dashboard />}>
  <Route path="profile" element={<Profile />} />
  <Route path="settings" element={<Settings />} />
</Route>
```

---

### 🔹 Dashboard Component

```js
import { Outlet } from "react-router-dom";

function Dashboard() {
  return (
    <div>
      <h2>Dashboard</h2>
      <Outlet /> {/* Child routes render here */}
    </div>
  );
}
```

---

## 💡 URL

* `/dashboard/profile`
* `/dashboard/settings`

---

# 🔷 6. Role-Based Routing (Permissions)

## 🧠 Simple Idea

👉 Show routes based on **user role (admin, user, etc.)**

---

## 💻 Example

```js
function RoleRoute({ children, role }) {
  const userRole = "user"; // or "admin"

  if (userRole !== role) {
    return <h2>Access Denied</h2>;
  }

  return children;
}
```

---

### 🔹 Use it

```js
<Route
  path="/admin"
  element={
    <RoleRoute role="admin">
      <AdminPanel />
    </RoleRoute>
  }
/>
```

---

## 💡 Behavior

* Admin → allowed ✅
* Normal user → blocked ❌

---

# 🔥 Combine Everything (Real World Example)

```js
<Suspense fallback={<h2>Loading...</h2>}>
  <Routes>

    <Route path="/" element={<Home />} />

    <Route path="/login" element={<Login />} />

    <Route
      path="/dashboard"
      element={
        <ProtectedRoute>
          <Dashboard />
        </ProtectedRoute>
      }
    >
      <Route path="profile" element={<Profile />} />

      <Route
        path="admin"
        element={
          <RoleRoute role="admin">
            <AdminPanel />
          </RoleRoute>
        }
      />
    </Route>

  </Routes>
</Suspense>
```

---

# 🧠 Final Mental Model

* Basic Routing → 🛣️ Navigate pages
* Lazy Loading → ⚡ Load only when needed
* Protected Route → 🔐 Auth-based access
* Nested Routes → 🌳 Parent-child pages
* Role-based → 👮 Permission control

---

# 🚀 Interview Tips

* Always mention:

  * `BrowserRouter`, `Routes`, `Route`
  * `Suspense` for lazy loading
  * `Navigate` for redirects
  * `Outlet` for nested routes

