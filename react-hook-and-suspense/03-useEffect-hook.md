# React Hooks and Suspense

## 03 - Store Values in LocalStorage with the React useEffect Hook

1. to perform side effect we can use `useEffect`
2. you can think of `useEffect` Hook as componentDidMount, componentDidUpdate, and componentWillUnmount combined.

```javascript
import React, { useState, useEffect } from "react";

function UseCounter(initialState, step) {
  const [counter, setCount] = useState(initialState);
  const IncrementCount = () => setCount(currentCount => currentCount + step);
  return {
    IncrementCount,
    counter
  };
}

function Counter() {
  const localState = Number(window.localStorage.getItem("count") || 0);
  const { counter, IncrementCount } = UseCounter(localState, 1);
  useEffect(() => {
    window.localStorage.setItem("count", counter);
  });
  return <button onClick={IncrementCount}>{counter}</button>;
}

export default Counter;
```

### Improvement

```javascript
function Counter() {
  // function are only call in the first render
  const localState = () => Number(window.localStorage.getItem("count") || 0);
  const { counter, IncrementCount } = UseCounter(localState, 1);
  useEffect(
    () => {
      window.localStorage.setItem("count", counter);
    },
    // array as an optional second argument to useEffect
    [counter] // Only re-run the effect if counter changes
  );
  return <button onClick={IncrementCount}>{counter}</button>;
}
```
