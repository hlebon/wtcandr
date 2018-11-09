# React Hooks and Suspense

## 01 - Using basic Hook State

1. I dont need classes to use state
2. I can import `{ useState }` to emulate `state` in classes
3. `useState` is a functions that recieve the state of the component
4. `useState` return an array with the state and a function to update the state. example: `[0, ƒ] = useState(0)`
5. The returned function it is like a setState

### Example

```javascript
import React, { useState } from "react";

function Counter() {
  const [counter, setCounter] = useState(0);
  const IncrementCount = () => {
    setCounter(currentCount => {
      return currentCount + 1;
    });
  };

  return <button onClick={IncrementCount}>{counter}</button>;
}

export default Counter;
```
