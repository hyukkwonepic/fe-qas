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
   ```
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

   ```
   function fn() {
    console.log(this);
   }

   var obj = {
    value: 5
   };

   var boundFn = fn.bind(obj);

   boundFn();     // -> { value: 5 }
   fn.call(obj);  // -> { value: 5 }
   fn.apply(obj); // -> { value: 5 }
   ```

3. If a function is called as a method, such as `obj.method()` — this is the object that the function is a property of.

   ```
   var obj = {
    value: 5,
    printThis: function() {
        console.log(this);
    }
   };

   obj.printThis(); // -> { value: 5, printThis: ƒ }
   ```

4. If a function is invoked as a free function invocation, meaning it was invoked without any of the conditions present above, this is the global object. In a browser, it is the window object. If in strict mode ('use strict'), this will be undefined instead of the global object.

   ```
   function fn() {
     console.log(this);
   }
   // If called in browser:
   fn(); // -> Window {stop: ƒ, open: ƒ, alert: ƒ, ...}
   ```

5. If multiple of the above rules apply, the rule that is higher wins and will set the this value.

6. If the function is an ES2015 arrow function, it ignores all the rules above and receives the `this` value of its surrounding scope at the time it is created.

   ```
   const obj = {
    value: 'abc',
    createArrowFn: function() {
        return () => console.log(this);
    }
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
