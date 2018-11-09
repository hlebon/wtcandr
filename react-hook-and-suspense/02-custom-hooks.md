# 02 - Custom Hooks

1. It is easy to share login across multiple components.
2. Can be an implementation detail, that allows us to abstract logic of an app.

## Example: Abstract Logic

```javascript
import React, { useState } from "react";

function UseCounter() {
  const [counter, setCount] = useState(0);
  return {
    IncrementCount: function() {
      setCount(currentCount => currentCount + 1);
    },
    counter
  };
}

function Counter() {
  const { counter, IncrementCount } = UseCounter();
  return <button onClick={IncrementCount}>{counter}</button>;
}

export default Counter;
```

### Example: Custom Hook

```javascript
function UseCounter(initialState, step) {
  const [counter, setCount] = useState(initialState);
  const IncrementCount = () => setCount(currentCount => currentCount + step);
  return {
    IncrementCount,
    counter
  };
}

function Counter() {
  const { counter, IncrementCount } = UseCounter(0, 2);
  return <button onClick={IncrementCount}>{counter}</button>;
}
```
