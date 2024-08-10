# Coding questions

### [Counter](https://www.greatfrontend.com/questions/user-interface/counter)

```jsx
import { useState } from "react";

import "./styles.css";

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
        }}
      >
        Clicks: {count}
      </button>
    </div>
  );
}
```

- It's the simplest and easiest coding question.
- Just chaning the method to `count + 1` was enough.

### [Contact Form](https://www.greatfrontend.com/questions/user-interface/contact-form)

```jsx
import "./styles.css";
import submitForm from "./submitForm";

export default function App() {
  return (
    <form
      // Ignore the onSubmit prop, it's used by GFE to
      // intercept the form submit event to check your solution.
      onSubmit={submitForm}
      action="https://www.greatfrontend.com/api/questions/contact-form"
      method="post"
    >
      <div>
        <label for="name">Name</label>
        <br />
        <input id="name" name="name" type="text" />
      </div>

      <br />

      <div>
        <label for="email">Email</label>
        <br />
        <input id="email" name="email" type="email" />
      </div>

      <br />

      <div>
        <label for="message">Message</label>
        <br />
        <textarea id="message" name="message" />
      </div>

      <br />

      <input type="submit" value="Send" />
    </form>
  );
}
```

- This is the simplest way to write a form.
- For the form element, you have to put action and method attributes to ensure the data is properly submitted. The value for the action attribute is the URL where the data is submitted to. And the value for the method is the HTTP request method.
- The for attribute in the label element points to the id of the input so when a user clicks a label, the input element is focused.
- The name attribute in input or textarea becomes the key of the form data that is submitted to the server. So we set name, email and message as the corresponding name attributes.
- The submit type input renders a submit button inside the form. We can use a button with type="submit" instead of it.

### [Holy Grail](https://www.greatfrontend.com/questions/user-interface/holy-grail)

```jsx
import "./styles.css";

export default function App() {
  return (
    <div class="container">
      <header>Header</header>
      <div class="content-container">
        <nav>Navigation</nav>
        <main>Main Main Main Main Main Main Main Main Main</main>
        <aside>Sidebar</aside>
      </div>
      <footer>Footer</footer>
    </div>
  );
}
```

```css
body {
  font-family: sans-serif;
  font-size: 12px;
  font-weight: bold;
  margin: 0;
}

* {
  box-sizing: border-box;
}

header,
nav,
main,
aside,
footer {
  padding: 12px;
}

div.container {
  display: flex;
  flex-direction: column;
  height: 100vh;
}

header {
  background-color: tomato;
  height: 60px;
}

div.content-container {
  display: flex;
  flex: 1;
}

nav {
  background-color: coral;
  width: 100px;
  flex-shrink: 0;
}

main {
  background-color: moccasin;
  flex-grow: 1;
}

aside {
  background-color: sandybrown;
  width: 100px;
  flex-shrink: 0;
}

footer {
  background-color: slategray;
  height: 100px;
}
```

### [Array.prototype.filter](https://www.greatfrontend.com/questions/javascript/array-filter?list=one-week)

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs>
  <TabItem value="try-a" label="Try A" default>
    ```ts
    interface Array<T> {
      myFilter(
        callbackFn: (value: T, index: number, array: Array<T>) => boolean,
        thisArg?: any
      ): Array<T>;
    }

    Array.prototype.myFilter = function (callbackFn, thisArg) {
      return this.reduce((pv, cv, index, array) => {
        if (callbackFn.apply(thisArg, [cv, index, array])) {
          return [...pv, cv];
        } else {
          return pv;
        }
      }, []);
    };
    ```

  </TabItem>
  <TabItem value="try-b" label="Try B">
    ```ts
    interface Array<T> {
      myFilter(
        callbackFn: (value: T, index: number, array: Array<T>) => boolean,
        thisArg?: any,
      ): Array<T>;
    }

    Array.prototype.myFilter = function (callbackFn, thisArg) {
      const results = [];

      for (let i = 0; i < this.length; i += 1) {
        const value = this[i];

        if (callbackFn.apply(thisArg, [value, i, this])) {
          results.push(value);
        } else {
        }
      }

      return results;
    };
    ```

  </TabItem>
</Tabs>

### [jQuery.css](https://www.greatfrontend.com/questions/javascript/jquery-css?list=one-week)

<Tabs>
  <TabItem value="try-a" label="Try A" default>
  ```ts
    interface JQuery {
      css: (
        prop: string,
        value?: boolean | string | number
      ) => JQuery | string | undefined;
    }

    export default function $(selector: string): JQuery {
    const targetEl = document.querySelector(selector);
      return {
        css: function (prop, value) {
          if (value !== undefined) {
            targetEl?.style[prop] = value;
            return this;
          }

          const styleValue = targetEl?.style[prop];
          return styleValue === "" ? undefined : styleValue;
        },
      };
    }
    ```

  </TabItem>
  <TabItem value="try-b" label="Try B">
    ```ts
    interface JQuery {
        css: (
          prop: string,
          value?: boolean | string | number,
        ) => JQuery | string | undefined;
      }

    class JQuery {
      constructor(selector: string) {
        this.targetEl = document.querySelector(selector);
      }

      css(prop, value) {
        if (value !== undefined) {
          this.targetEl?.style[prop] = value;
          return this;
        }

        const styleValue = this.targetEl?.style[prop];
        return styleValue === "" ? undefined : styleValue;
      }

    }

      export default function $(selector: string): JQuery {
      return new JQuery(selector);
    }
    ```

  </TabItem>
</Tabs>

### [Debounce](https://www.greatfrontend.com/questions/javascript/debounce?list=one-week)

```js
export default function debounce(func: Function, wait: number): Function {
  let timeoutId = null;
  return function (...args) {
    clearTimeout(timeoutId);
    timeoutId = setTimeout(() => {
      func.call(this, ...args);
    }, wait);
  };
}
```

### [Curry](https://www.greatfrontend.com/questions/javascript/curry?list=one-week)

```ts
export default function curry(func: Function): Function {
  return function recursive(this: any, ...args: any[]) {
    if (args.length === func.length) {
      return func.call(this, ...args);
    }

    return (arg: any) => {
      if (arg === undefined) {
        return recursive.call(this, ...args);
      }
      return recursive.call(this, ...[...args, arg]);
    };
  };
}
```

### [Classnames](https://www.greatfrontend.com/questions/javascript/classnames?list=one-week)

```ts
export type ClassValue =
  | ClassArray
  | ClassDictionary
  | string
  | number
  | null
  | boolean
  | undefined;
export type ClassDictionary = Record<string, any>;
export type ClassArray = Array<ClassValue>;

export default function classNames(...args: Array<ClassValue>): string {
  const classes: Array<string> = [];

  function handle(value: any) {
    if (!Boolean(value)) {
      return;
    }

    if (Array.isArray(value)) {
      value.forEach((v) => {
        handle(v);
      });
      return;
    }

    if (typeof value === "object") {
      const validClasses = Object.entries(value).reduce<string[]>((acc, cv) => {
        const [key, value] = cv;
        if (value) {
          return [...acc, key];
        }
        return acc;
      }, []);
      classes.push(...validClasses);
      return;
    }

    if (typeof value === "string") {
      classes.push(value);
      return;
    }

    if (typeof value === "number") {
      classes.push(value.toString());
      return;
    }
  }

  handle(args);

  return classes.join(" ");
}

```

### [Flatten](https://www.greatfrontend.com/questions/javascript/flatten?list=one-week)

<Tabs>
  <TabItem value="try-a" label="Try A" default>
  ```ts
  type ArrayValue = any | Array<ArrayValue>;

  export default function flatten(value: Array<ArrayValue>): Array<any> {
    const result: any[] = [];

    const handler = (val: any[]) => {
      if (Array.isArray(val)) {
        val.forEach(v => handler(v));
        return;
      }

      result.push(val);
    }

    handler(value);

    return result;
  }
  ```
  </TabItem>
  <TabItem value="try-b" label="Try B">
  ```ts
  type ArrayValue = any | Array<ArrayValue>;

  export default function flatten(value: Array<ArrayValue>): Array<any> {
    const result: any[] = [];
    const temp = [...value];

    while (temp.length > 0) {
      const value = temp.shift();

      if (Array.isArray(value)) {
        temp.unshift(...value);
        continue;
      }

      result.push(value);
    }
    
    return result;
  }
  ```
  </TabItem>
  <TabItem value="try-c" label="Try C">
  ```ts
  export default function flatten(value: Array<ArrayValue>): Array<any> {
    return value.reduce((acc, cv) => {
      if (Array.isArray(cv)) {
        return [
          ...acc,
          ...flatten(cv)
        ]
      }

      return [
        ...acc,
        cv
      ]
    }, [])
  }
  ```
  </TabItem>
</Tabs>


### [Promise.all](https://www.greatfrontend.com/questions/javascript/promise-all?list=one-week)

```ts
export default function promiseAll<T extends readonly unknown[] | []>(
  iterable: T,
): Promise<{ -readonly [P in keyof T]: Awaited<T[P]> }> {
  
  return new Promise((resolve, reject) => {
    if (iterable.length === 0) {
      resolve([] as { -readonly [P in keyof T]: Awaited<T[P]> });
      return;
    }

    let count = 0;
    const results = [];

    for (let i = 0; i < iterable.length; i += 1) {
      const item = iterable[i];

      (async () => {
        try {
          const result = await item;
          count += 1;
          results[i] = result;

          if (count === iterable.length) {
            resolve(results as { -readonly [P in keyof T]: Awaited<T[P]> });
            return;
          }
        } catch (error) {
          reject(error);
        }
      })();
    }
  })
}
```

### [Todo List](https://www.greatfrontend.com/questions/user-interface/todo-list/vanilla)

```js
import "./styles.css";

const DEFAULT_TASKS = ["Walk the dog", "Water the plants", "Wash the dishes"];

function createTaskEl(task) {
  const templateEl = document.createElement("template");
  templateEl.innerHTML = `
        <li>
            <span>${task}</span>
            <button>Delete</button>
        </li>
    `;

  const el = templateEl.content.firstElementChild;

  const buttonEl = el.querySelector("button");

  buttonEl.addEventListener("click", (event) => {
    el.remove();
  });

  return el;
}

const ulEl = document.querySelector("ul");

const formEl = document.querySelector("form");

formEl.addEventListener("submit", (event) => {
  event.preventDefault();
  const inputEl = formEl.querySelector("input");
  if (inputEl.value === "") {
    return;
  }

  ulEl.appendChild(createTaskEl(inputEl.value));
  formEl.reset();
  inputEl.focus();
});

(() => {
  DEFAULT_TASKS.forEach((task) => {
    ulEl.appendChild(createTaskEl(task));
  });
})();

```

### [getElementsByTagName](https://www.greatfrontend.com/questions/javascript/get-elements-by-tag-name?list=one-week)

```ts
export default function getElementsByTagName(
  el: Element,
  tagName: string
): Array<Element> {
  const results: Array<Element> = [];

  function traverse(element: Element) {
    if (element.tagName === tagName.toUpperCase()) {
      if (el !== element) {
        results.push(element);
      }
    }

    if (element.children.length === 0) {
      return;
    }

    [...element.children].forEach((el) => {
      traverse(el);
    });
  }

  traverse(el);

  return results;
}
```