## 1. Use React memoization (avoid unnecessary re-renders)

### ✅ `React.memo`

Wrap components so they only re-render when props change.

```js
export default React.memo(MyComponent);
```

Use it for:

* Pure functional components
* Components that re-render often without prop changes

---

### ✅ `useMemo`

Memoize expensive calculations.

```js
const filteredList = useMemo(() => {
  return items.filter(i => i.active);
}, [items]);
```

---

### ✅ `useCallback`

Memoize functions so they don’t get recreated every render.

```js
const handleClick = useCallback(() => {
  console.log("clicked");
}, []);
```

---

## 2. Avoid unnecessary state updates

* Don’t store derived values in state
* Don’t update state with same value
* Keep state as local as possible

Bad:

```js
setCount(count); // same value = unnecessary render
```

---

## 3. Split large components

Break big components into smaller ones so only parts re-render.

---

## 4. Code splitting (lazy loading)

Load components only when needed.

```js
const Dashboard = React.lazy(() => import("./Dashboard"));

<Suspense fallback={<div>Loading...</div>}>
  <Dashboard />
</Suspense>
```

---

## 5. Optimize lists with virtualization

For large lists, render only visible items.

Use libraries like:

* `react-window`
* `react-virtualized`

This avoids rendering thousands of DOM nodes.

---

## 6. Avoid inline functions and objects in JSX (when possible)

Bad:

```js
<Button onClick={() => doSomething()} />
```

Better:

```js
const handleClick = useCallback(() => doSomething(), []);
<Button onClick={handleClick} />
```

---

## 7. Use key properly in lists

Bad:

```js
key={index}
```

Good:

```js
key={item.id}
```

Prevents incorrect re-renders.

---

## 8. Reduce unnecessary context re-renders

* Split contexts (don’t put everything in one context)
* Memoize context values

```js
const value = useMemo(() => ({ user, setUser }), [user]);
```

---

## 9. Debounce / throttle expensive operations

Useful for:

* search input
* resize events
* scroll events

---

## 10. Profile before optimizing

Use:

* React DevTools Profiler
* Chrome Performance tab

👉 Don’t optimize blindly—find actual bottlenecks first.

---

## 11. Use production build

Always ensure:

* `npm run build`
* production mode enabled

Development builds are much slower.

---

## 12. Server-side rendering (advanced)

Frameworks like Next.js improve initial load performance by rendering HTML on server.

---

## Summary

React performance optimization is mainly about:

* preventing unnecessary renders
* reducing DOM work
* loading only what is needed
* profiling before fixing

