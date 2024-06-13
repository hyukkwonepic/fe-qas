# Coding questions

## [Counter](https://www.greatfrontend.com/questions/user-interface/counter)

```jsx
import { useState } from 'react';

import './styles.css';

// This is a warm up question to help you
// get familiar with the editor.
// Most of the code has been filled in for you.
export default function App() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <button
        onClick={() => {
          setCount(count + 1);
        }}>
        Clicks: {count}
      </button>
    </div>
  );
}

```

- It's the simplest and easiest coding question.
- Just chaning the method to `count + 1` was enough.