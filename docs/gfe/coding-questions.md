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

## [Contact Form](https://www.greatfrontend.com/questions/user-interface/contact-form)

```jsx
import './styles.css';
import submitForm from './submitForm';

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