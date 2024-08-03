---
title: Quizzes
description: A set of answers to the quiz questions from GFE
---

# Quizzes

## [Explain how prototypal inheritance works](https://www.greatfrontend.com/questions/quiz/explain-how-prototypal-inheritance-works)

- Prototypical inheritance is a way for objects to inherit properties and methods from other objects

- Every object in JavaScript has a property called prototype enclosed in double brackets, which references the object’s prototype. It can be accessed with underbar underbar proto, or with object-dot-get-prototype-of method.

- If an object’s property is accessed, and if it doesn’t exist, the engine looks at the prototype object, and its prototype again until it finds the property.

- When an object is created, the new object’s prototype can be the constructor function’s prototype or object-dot-prototype.

- Inherited objects can be made by using the object-dot-create method. If there is a need to change the prototype of an existing object, you can use the object-dot-set-prototype-of method.

## [Describe the difference between `<script>`, `<script async>` and `<script defer>`](https://www.greatfrontend.com/questions/quiz/describe-the-difference-between-script-async-and-script-defer?list=one-week)

**`<script>`**

- The script tag is used to load and execute a JavaScript file in the HTML file.

- So when the browser reads the HTML file, it starts to parse it, but when it encounters the script tag, it processes the loading and execution.

- But while this is being taken care of, the parsing of the rest of the HTML file is stopped. After the process is done, it continues the parsing.

- The potential problem here is that when the JavaScript file that the script tag is referring to is too big or takes too much time, it'll block the page loading for too long.

- Users will see a blank page, be unable to interact with it, and the loading spinner will keep spinning. Users may consider that the page is too slow and possibly leave the page.

- To prevent this, it's a good idea to put the script tag right before the end of the body tag, ensuring that the blocking happens after the page is fully rendered.

**with async attribute**

- When an 'async' attribute is given to the tag, the browser starts downloading when the parser faces the tag, but the parsing continues right away. This means that the script tag doesn't block the HTML parsing.

- Meanwhile, when the JavaScript download is finished, it gets executed.

- As it doesn't block the parsing, the page gets rendered earlier, which can be perceived as a performance gain.

- Using the 'async' attribute is recommended when the script is not dependent on any other scripts in the HTML, as the execution could happen before the HTML parsing is finished.

**with defer attribute**

- When the defer attribute is added, the browser downloads the script asynchronously in parallel to the HTML parsing, just like the async option.

- But the defer option executes the script after the HTML parsing is done and before the DOMContentLoaded event fires.

- It’s good to use the defer option when the script depends on other scripts on the page or manipulates DOM elements.

## [Explain how `this` works in JavaScript](https://www.greatfrontend.com/questions/quiz/explain-how-this-works-in-javascript)

- A hand-wavey explanation is that the value of this depends on how the function is called.

The following rules are applied to this:

1. If the `new` keyword is used when calling the function, `this` inside the function is a brand new object.
   ```js
   function ConstructorExample() {
     console.log(this);
     this.value = 10;
     console.log(this);
   }
   new ConstructorExample();
   // -> {}
   // -> { value: 10 }
   ```
2. If `apply`, `call`, or `bind` are used to call/create a function, this inside the function is the object that is passed in as the argument.

   ```js
   function fn() {
     console.log(this);
   }

   var obj = {
     value: 5,
   };

   var boundFn = fn.bind(obj);

   boundFn(); // -> { value: 5 }
   fn.call(obj); // -> { value: 5 }
   fn.apply(obj); // -> { value: 5 }
   ```

3. If a function is called as a method, such as `obj.method()` — this is the object that the function is a property of.

   ```js
   var obj = {
     value: 5,
     printThis: function () {
       console.log(this);
     },
   };

   obj.printThis(); // -> { value: 5, printThis: ƒ }
   ```

4. If a function is invoked as a free function invocation, meaning it was invoked without any of the conditions present above, this is the global object. In a browser, it is the window object. If in strict mode ('use strict'), this will be undefined instead of the global object.

   ```js
   function fn() {
     console.log(this);
   }
   // If called in browser:
   fn(); // -> Window {stop: ƒ, open: ƒ, alert: ƒ, ...}
   ```

5. If multiple of the above rules apply, the rule that is higher wins and will set the this value.

6. If the function is an ES2015 arrow function, it ignores all the rules above and receives the `this` value of its surrounding scope at the time it is created.

   ```js
   const obj = {
     value: "abc",
     createArrowFn: function () {
       return () => console.log(this);
     },
   };

   const arrowFn = obj.createArrowFn();
   arrowFn(); // -> { value: 'abc', createArrowFn: ƒ }
   ```

## [Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models](https://www.greatfrontend.com/questions/quiz/explain-your-understanding-of-the-box-model-and-how-you-would-tell-the-browser-in-css-to-render-your-layout-in-different-box-models)

The CSS box model describes how elements are rendered as rectangular boxes, consisting of content, padding, border, and margin.

The CSS box model is responsible for calculating:

- How much space a block element takes up.
- Whether or not borders and/or margins overlap, or collapse.
- A box's dimensions.

Key box model rules:

- Block element dimensions include width, height, padding, and borders
- Without specified height, elements expand to fit content plus padding
- Without specified width, non-floated blocks expand to parent width minus padding
- Some elements have default widths (e.g., table, figure, input)
- By default (box-sizing: content-box), paddings and borders are not part of the width and height of an element.

There are two main box models:

1. Content-box (default):

   - Width/height only includes content
   - Padding and border add to total size
   - `box-sizing: content-box;`

2. Border-box:
   - Width/height includes content, padding, and border
   - `box-sizing: border-box;`
   - Border-box is often preferred as it makes sizing more intuitive.

- To specify the box model, use the `box-sizing` property:
- Margins always remain outside the box in both models.

## [What are the differences between variables created using `let`, `var` or `const`?](https://www.greatfrontend.com/questions/quiz/what-are-the-differences-between-variables-created-using-let-var-or-const)

In JavaScript, let, var, and const are all keywords used to declare variables, but they differ significantly in various aspects.

| Behavior                     | `let`            | `var`              | `const`          |
| ---------------------------- | ---------------- | ------------------ | ---------------- |
| Scope                        | Block            | Function or Global | Block            |
| Initialization               | Optional         | Optional           | Required         |
| Redeclaration                | No               | Yes                | No               |
| Reassignment                 | Yes              | Yes                | No               |
| Accessing before declaration | `ReferenceError` | `undefined`        | `ReferenceError` |

- When a JavaScript execution context is created, it goes through a creation phase before code execution. During this phase, for var declarations: 1. Memory is allocated for the variable, 2. The variable is initialized with undefined, 3. This happens before any code in that context is executed. As a result, when you try to access a var variable before its declaration in the code, it already exists in memory with the value undefined. This is part of the variable hoisting mechanism in JavaScript.

- Hoisting with execution context:

  1. Creation Phase:

     - The JavaScript engine scans the code for variable and function declarations.
     - For `var` declarations, it creates a property in the Variable Environment of the current execution context, which is automatically initialized to `undefined`.
     - For `let` and `const`, it registers their existence in the lexical environment without creating a property or initializing them (putting them in the Temporal Dead Zone).
     - Function declarations are fully hoisted (both declaration and definition).

  2. Execution Phase:
     - The code is executed line by line.
     - This is when `console.log()` and other statements are actually run.

  - For `var`:

    ```javascript
    console.log(x);
    var x = 5;
    ```

    1. Creation Phase:

    - A property `x` is created in the Variable Environment and automatically initialized to `undefined`.

    2. Execution Phase:

    - `console.log(x)` is executed, printing `undefined` (the current value of `x` in the Variable Environment).
    - `x = 5` is executed, assigning 5 to the `x` property in the Variable Environment.

  - For `let` and `const`:

    ```javascript
    console.log(y);
    let y = 10;
    ```

    1. Creation Phase:

    - `y` is registered in the lexical environment of its scope, entering the TDZ. No property is created or initialized.

    2. Execution Phase:

    - `console.log(y)` is executed. Since `y` is in the TDZ and no property exists for it yet in the lexical environment, this throws a ReferenceError.
    - The declaration and initialization `let y = 10` is never reached due to the error. If it were reached, this is where a property would be created in the lexical environment and initialized with the value 10.

## [What does `* { box-sizing: border-box; }` do?](https://www.greatfrontend.com/questions/quiz/what-does-box-sizing-border-box-do-what-are-its-advantages)

- By default, elements have `box-sizing: content-box` applied, and only the content size is being accounted for if an element has height and width specified. `box-sizing: border-box` changes how the width and height of elements are being calculated, border and padding are also being included in the calculation.
- Taking into account paddings and borders as part of the box model resonates better with how designers actually imagine content in grids. This is a much more intuitive way to think about boxes and hence many CSS frameworks set `* { box-sizing: border-box; }` globally, so that all elements use such a box model by default.

## [What is CSS selector specificity and how does it work?](<[asdf](https://www.greatfrontend.com/questions/quiz/what-is-css-selector-specificity-and-how-does-it-work)>)

- According to the CSS specification, specificity is calculated as a three-part value: A, B, C. Each part represents:

  - A: Number of ID selectors. `#header` (1,0,0)
  - B: Number of class selectors, attribute selectors, and pseudo-classes. `.button`, `[type="text"]`, `:hover` (0,1,0)
  - C: Number of type selectors and pseudo-elements. `div`, `::before` (0,0,1)

- The first rule wins because its specificity (1,1,0) is higher than the second (0,2,0).

  ```
  #sidebar .widget { background: blue; }
  .widget-area .my-widget { background: red; }
  ```

- It's important to note that inline styles, while not part of this calculation, always override external stylesheets. They're considered separately in the cascade.
- `!important` can override specificity, it's generally considered a last resort.
- When writing CSS UI component library code, it is important that they have low specificities so that users of the library can override them

## [What is the CSS `display` property and can you give a few examples of its use?](https://www.greatfrontend.com/questions/quiz/what-is-the-css-display-property-and-can-you-give-a-few-examples-of-its-use)

| `display` Value | Description                                                                                                                                                                                                            |
| :-------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `none`          | Does not display an element (the element no longer affects the layout of the document). All child element are also no longer displayed. The document is rendered as if the element did not exist in the document tree. |
| `block`         | The element consumes the whole line in the block direction (which is usually horizontal).                                                                                                                              |
| `inline`        | Elements can be laid out beside each other.                                                                                                                                                                            |
| `inline-block`  | Similar to `inline`, but allows some `block` properties like setting `width` and `height`.                                                                                                                             |
| `flex`          | Behaves as a block-level `flex` container, which can be manipulated using flexbox model.                                                                                                                               |
| `grid`          | Behaves as a block-level `grid` container using grid layout.                                                                                                                                                           |
| `table`         | Behaves like the `<table>` element.                                                                                                                                                                                    |
| `table-row`     | Behaves like the `<tr>` element.                                                                                                                                                                                       |
| `table-cell`    | Behaves like the `<td>` element.                                                                                                                                                                                       |
| `list-item`     | Behaves like a `<li>` element which allows it to define `list-style-type` and `list-style-position`.                                                                                                                   |

## [What is the difference between `==` and `===` in JavaScript?](https://www.greatfrontend.com/questions/quiz/what-is-the-difference-between-double-equal-and-triple-equal)

- The `==` operator will compare for equality after doing any necessary type conversions.

  - ```js
    42 == "42"; // true
    0 == false; // true
    null == undefined; // true
    [] == false; // true
    "" == false; // true

    // However, when using ==, unintuitive results can happen:
    1 == [1]; // true
    0 == ""; // true
    0 == "0"; // true
    "" == "0"; // false
    ```

  - Use `==` when you want to compare values with type coercion (and understand the implications of it). Practically, the only valid use case for the equality operator is when against null and undefined for convenience.

- The `===` operator will not do type conversion, so if two values are not the same type `===` will simply return false.
  - ```js
    console.log(42 === "42"); // false
    console.log(0 === false); // false
    console.log(null === undefined); // false
    console.log([] === false); // false
    console.log("" === false); // false
    ```
  - Use `===` when you want to ensure both the value and the type are the same, which is the safer and more predictable choice in most cases.
- Using `===` (strict equality) is generally recommended to avoid the pitfalls of type coercion, which can lead to unexpected behavior and bugs in your code. It makes the intent of your comparisons clearer and ensures that you are comparing both the value and the type.

## [What's the difference between a variable that is: `null`, `undefined` or undeclared?](https://www.greatfrontend.com/questions/quiz/whats-the-difference-between-a-variable-that-is-null-undefined-or-undeclared-how-would-you-go-about-checking-for-any-of-these-states?list=one-week)

- Undeclared variables are created when you assign a value to an identifier that is not previously created using `var`, `let` or `const`. In strict mode, a `ReferenceError` will be thrown when you try to assign to an undeclared variable. Undeclared variables will be defined globally, outside of the current scope.

  - ```js
    function foo() {
      x = 1; // Throws a ReferenceError in strict mode
    }

    foo();
    console.log(x); // 1
    ```

- A variable that is `undefined` is a variable that has been declared, but not assigned a value. It is of type `undefined`. If a function does not return any value as the result of executing it is assigned to a variable, the variable also has the value of `undefined`.

  - ```js
    let foo;
    console.log(foo); // undefined
    console.log(foo === undefined); // true
    console.log(typeof foo === "undefined"); // true

    function bar() {} // Returns undefined if there is nothing returned.
    let baz = bar();
    console.log(baz); // undefined
    ```

- A variable that is `null` will have been explicitly assigned to the `null` value. It represents no value and is different from undefined in the sense that it has been explicitly assigned.
  - ```js
    const foo = null;
    console.log(foo === null); // true
    console.log(typeof foo === "object"); // true
    ```

## [What's the difference between `.call` and `.apply`?](https://www.greatfrontend.com/questions/quiz/whats-the-difference-between-call-and-apply?list=one-week)

`.call` and `.apply` are both used to invoke functions with a specific this context and arguments. The primary difference lies in how they accept arguments:

- `.call(thisArg, arg1, arg2, ...)`: Takes arguments individually.
- `.apply(thisArg, [argsArray])`: Takes arguments as an array.

```js
function add(a, b) {
  return a + b;
}

console.log(add.call(null, 1, 2)); // 3
console.log(add.apply(null, [1, 2])); // 3
```

## [Describe the difference between a cookie, `sessionStorage` and `localStorage`.](https://www.greatfrontend.com/questions/quiz/describe-the-difference-between-a-cookie-sessionstorage-and-localstorage?list=one-week)

All of the following are mechanisms of storing data on the client, the user's browser in this case. localStorage and sessionStorage both implement the Web Storage API interface.

- Cookies: Suitable for server-client communication, small storage capacity, can be persistent or session-based, domain-specific. Sent to the server on every request.
- `localStorage`: Suitable for long-term storage, data persists even after the browser is closed, accessible across all tabs and windows of the same origin, highest storage capacity among the three.
- `sessionStorage`: Suitable for temporary data within a single page session, data is cleared when the tab or window is closed, has a higher storage capacity compared to cookies.

More:

- Common properties of these storage types:
  - The clients can read and modify the values (except for HttpOnly cookies).
  - Key-value based storage.
  - They are only able to store values as strings. Non-strings will have to be serialized into a string (e.g. `JSON.stringify()`) in order to be stored.
- Cookies are sent to the server on every HTTP request so the low maximum size is a feature that prevents your HTTP requests from being too large due to cookies

## [What's the difference between a `relative`, `fixed`, `absolute`, `sticky` and `static`-ally positioned element?](https://www.greatfrontend.com/questions/quiz/whats-the-difference-between-a-relative-fixed-absolute-and-statically-positioned-element?list=one-week)

A positioned element is an element whose computed `position` property is either `relative`, `absolute`, `fixed` or `sticky`.

- `static`: The default position; the element will flow into the page as it normally would. The `top`, `right`, `bottom`, `left` and `z-index` properties do not apply.
- `relative`: The element's position is adjusted relative to itself, without changing layout (and thus leaving a gap for the element where it would have been had it not been positioned).
- `absolute`: The element is removed from the flow of the page and positioned at a specified position relative to its closest positioned ancestor if any, or otherwise relative to the initial containing block. Absolutely-positioned boxes can have margins, and they do not collapse with any other margins. These elements do not affect the position of other elements.
- `fixed`: The element is removed from the flow of the page and positioned at a specified position relative to the viewport and doesn't move when scrolled.
- `sticky`: Sticky positioning is a hybrid of relative and fixed positioning. The element is treated as `relative` positioned until it crosses a specified threshold, at which point it is treated as `fixed`-positioned.

## [What's the difference between `inline` and `inline-block`?](https://www.greatfrontend.com/questions/quiz/whats-the-difference-between-inline-and-inline-block?list=one-week)

| Property                             | `block`                                                                                     | `inline-block`                                                      | `inline`                                                                                                                                                                                                             |
| ------------------------------------ | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Size                                 | Fills up the width of its parent container.                                                 | Depends on content.                                                 | Depends on content.                                                                                                                                                                                                  |
| Positioning                          | Start on a new line and tolerates no HTML elements next to it (except when you add `float`) | Flows along with other content and allows other elements beside it. | Flows along with other content and allows other elements beside it.                                                                                                                                                  |
| Can specify `width` and `height`     | Yes                                                                                         | Yes                                                                 | No. Will ignore if being set.                                                                                                                                                                                        |
| Can be aligned with `vertical-align` | No                                                                                          | Yes                                                                 | Yes                                                                                                                                                                                                                  |
| Margins and paddings                 | All sides respected.                                                                        | All sides respected.                                                | Only horizontal sides respected. Vertical sides, if specified, do not affect layout. Vertical space it takes up depends on `line-height`, even though the `border` and `padding` appear visually around the content. |
| Float                                | -                                                                                           | -                                                                   | Becomes like a `block` element where you can set vertical margins and paddings.                                                                                                                                      |

## [Can you offer a use case for the new arrow => function syntax?](https://www.greatfrontend.com/questions/quiz/can-you-offer-a-use-case-for-the-new-arrow-function-syntax-how-does-this-new-syntax-differ-from-other-functions?list=one-week)

Advantages of arrow functions

- `this` Behavior: Arrow functions do not have their own `this`. Instead, they inherit `this` from the parent scope at the time they are defined. This is particularly useful in scenarios where you are dealing with callbacks and want to retain the context of `this`.
- Implicit Return: If the function body consists of a single expression, arrow functions allow you to omit the return keyword and the curly braces.

When to use arrow functions

- In callback functions where you want to preserve the lexical scope of `this`.

When not to use arrow functions

- Methods in objects: Arrow functions do not have their own `this` context, which can lead to unexpected behavior in object methods.
- As constructors: Arrow functions cannot be used as constructors and will throw an error if used with the new keyword.
- When you need to use function hoisting: Arrow functions are not hoisted, unlike traditional function declarations.


## [Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`?](https://www.greatfrontend.com/questions/quiz/css-link-between-head-and-js-script-just-before-body?list=one-week)

Placing `<link>`s in `<head>`:

- Placing CSS `<link>`s in the `<head>` ensures that the stylesheets are loaded and ready for use when the browser starts rendering the page.
- When a page first loads, HTML creates the DOM (Document Object Model) and CSS creates the CSSOM (CSS Object Model). Both are needed to create the visuals in a website, allowing for a quick "first meaningful paint" timing. 
- Putting stylesheets near the bottom of the document is what prohibits progressive rendering in many browsers.

Placing `<script>`s just before `</body>`:

- `<script>` tags block HTML parsing while they are being downloaded and executed which can slow down the display of your page. Placing the `<script>`s at the bottom will allow the HTML to be parsed and displayed to the user first.
  