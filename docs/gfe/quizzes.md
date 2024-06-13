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