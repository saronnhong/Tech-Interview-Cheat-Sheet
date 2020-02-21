# Tech-Interview-Cheat-Sheet
## HTML
1. What does a doctype do?
    - Doctype stands for Document Type Declaration. It informs the web browser about the type and version of HTML used in building the web document.
2. How do you serve a page with content in multiple languages?
    - Use the HTTP Accept-Language header to infer the user's language/region but also allow the user to change the language as needed in case it is wrong.
3. What kind of things must you be wary of when designing or developing for multilingual sites?
    - Who will translate your content? Google Translate is not always very accurate with meaning. You may have to hire a native speaker in order to translate content correctly.
    - Writing content in different languages, you have to be wary of different vocabulary and cultural systems.
    - Might need different content for each language. Some of your content might not apply to their culture.
    - Display content in user's locale. Correct time zone, measurements (miles vs km), 
    - Use Lang attribute to make language of content
4. What are data- attributes good for?
    - Used to store custom data private to the page or application. Gives us the ability to embed cust data attributes to HTML elements. The stored data can then be used in the page's JavaScript to create a more engaging experience.
5. Consider HTML5 as an open web platform. What are the building blocks of HTML5?
    - More semantic text markup
    - Video and audio
    - New JavaScript API
    - Canvas and SVG
    - New communication API
    - Geolocation API
    - Web Worker API
    - New Data Storage
6. Describe the difference between a cookie, sessionStorage and localStorage.
    - localStorage:
        - 5MB size
        - Data not sent back to the server on every HTTP request - reduces the amount of traffic between server and client
        - Data persists until explicitly deleted. Changes made are save and available for current and future visits to the site.
    - sessionStorage:
        - Similar to localStorage (5mb size, Not sent back to server on every HTTP request)
        - Changes are only available per window/tab. Once the window is closed, the storage is deleted
    - Cookie:
        - We can set the expiration time for each cookie
        - 4k size limit for the entire cookie
        - Data is sent back to the server for every HTTP request - increasing the amount of traffic between the client and server
7. Describe the difference between ```<script>, <script async>, and <script defer>.```
    - ```<script>```: Used to define a client-side script
    - ```<script async>```: The script is executed asynchronously with the rest of the page (the script will be executed while the page continues the parsing)
    - ```<script defer>```: The defer attribute tells the browser to only execute the script file once the HTML document has been fully parsed
8. Why is it generally a good idea to position CSS ```<link>```s between ```<head></head>``` and JS ```<script>```s just before ```</body>```? Do you know any exceptions?
    - CSS is linked in the Head because they are applied regardless if the DOM is rendered or not. That way the page will be rendered immediately with the CSS as the page loads. If it were on the bottom, it would load the page with plain HTML and then load the CSS afterwards which could show an ugly page if the load time is long.
    - JavaScript is linked at the bottom because whenever the browser encounters any JS, it will parse it and render it immediately. This can lead to slow load times. If the DOM isn't fully rendered, it wouldn't be able to manipulate the elements on the page anyways.
9. What is progressive rendering?
    - Progressive Rendering is the technique of sequentially rendering portions of a webpage in the server and streaming it to the client in parts without waiting for the whole page to rendered.
    - You render the critical content on the server, you start streaming it to the client without waiting for non-critical content.
10. Why you would use a srcset attribute in an image tag? Explain the process the browser uses when evaluating the content of this attribute.
    - You would use the srcset attribute when you want to serve different images to users depending on their device display width - serve higher quality images to devices with retina display enhances the user experience while serving lower resolution images to low-end devices increase performance and decrease data wastage (because serving a larger image will not have any visible difference). 
11. Have you used different HTML templating languages before?
    - Yes, I have used Handlebars.js in one of my projects. It allows you to seperate the HTML from the JavaScript to make it easier to manage. 

## CSS
1. What is CSS selector specificity and how does it work?
    - CSS Specificity is the set of the rules applied to CSS selectors in order to determine which style is applied to an element. The more specific a CSS style is, the higher point value it accrues, and the likelier it is to be present on the element's style.
    
    **Order of Importance**
    1. Inline styles
    2. ID selectors
    3. Classes, attributes and pseudo-classes selectors (ie a:hover)
    4. Tags and pseudo-elements selectors (ie p::firstline)
2. What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?
    - Resetting is meant to strip all default browser styling on elements.
    - Normalize CSS aims to make built-in browser styling consistent across browsers. Normalizing preserves useful default styles rather than "unstyling" everything. It also corrects bugs for common browser dependencies.
3. Describe Floats and how they work.
    - Float is a CSS positioning property. Floated elements remain a part of the flow of the page, and will affect the positioning of other elements
    - Use clear property or .clearfix hack to work around it
4. Describe z-index and how stacking context is formed.
    - The z-index property in CSS controls the vertical stacking order of elements that overlap. z-index only affects elements that have a position value which is not static.
5. Describe BFC (Block Formatting Context) and how it works.
    - ??? A Block Formatting Context (BFC) is part of the visual CSS rendering of a web page in which block boxes are laid out.
6. What are the various clearing techniques and which is appropriate for what context?
    - Empty div method - `<div style="clear:both;"></div>.`
    - Clearfix method
    - overflow: auto or overflow: hidden method - Parent will establish a new block formatting context and expand to contains its floated children.
    -In large projects, I would write a utility .clearfix class and use them in places where I need it. overflow: hidden might clip children if the children is taller than the parent and is not very ideal.
7. How would you approach fixing browser-specific styling issues?
    - Use Reset CSS or Normalize.css
8. How do you serve your pages for feature-constrained browsers? What techniques/processes do you use?
    - Graceful degradation - The practice of building an application for modern browsers while ensuring it remains functional in older browsers.
    - Progressive enhancement - The practice of building an application for a base level of user experience, but adding functional enhancements when a browser supports it.
9. What are the different ways to visually hide content (and make it available only for screen readers)?
    - `visibility: hidden`. However, the element is still in the flow of the page, and still takes up space.
    - `width: 0; height: 0`. Make the element not take up any space on the screen at all, resulting in not showing it.
    - `position: absolute; left: -99999px`. Position it outside of the screen.
    - `text-indent: -9999px`. This only works on text within the block elements.
10. Have you ever used a grid system, and if so, what do you prefer?
    - I use the Bootstrap grid system. It uses a series of containers, rows, and columns to layout and align content.
11. Have you used or implemented media queries or mobile specific layouts/CSS?
    - Yes, used it to change CSS on any smaller screen sizes
12. Can you give an example of an @media property other than screen?
    - `all` - for all media type devices
    - `print` - for printers
    - `speech` - for screenreaders that "reads" the page out loud
    - `screen` - for computer screens, tablets, smart-phones etc.
13. Explain how a browser determines what elements match a CSS selector.
    - Browsers match selectors from rightmost (key selector) to left. Browsers filter out elements in the DOM according to the key selector and traverse up its parent elements to determine matches. The shorter the length of the selector chain, the faster the browser can determine if that element matches the selector.
14. Describe pseudo-elements and discuss what they are used for.
    - A CSS pseudo-element is a keyword added to a selector that lets you style a specific part of the selected element(s). They can be used for decoration (`:first-line`, `:first-letter`) or adding elements to the markup (combined with `content: ...`) without having to modify the markup (`:before`, `:after`).
15. Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models.
    - The CSS box model describes the rectangular boxes that are generated for elements in the document tree and laid out according to the visual formatting model. Each box has a content area (e.g. text, an image, etc.) and optional surrounding padding, border, and margin areas.
16. What does * { box-sizing: border-box; } do? What are its advantages?
    - By default, elements have box-sizing: content-box applied, and only the content size is being accounted for.
box-sizing: border-box changes how the width and height of elements are being calculated, border and padding are also being included in the calculation.
    - The height of an element is now calculated by the content's height + vertical padding + vertical border width.
    - The width of an element is now calculated by the content's width + horizontal padding + horizontal border width.
17. What is the CSS display property and can you give a few examples of its use?
    - `none`: Does not display an element (the elementv no longer affects the layout of the document). All child element are also no longer displayed. The document is rendered as if the element did not exist in the document tree
    - `block`: The element consumes the whole line in the block direction (which is usually horizontal)
    - `inline`: Elements can be laid out beside each other
    - `inline-block`: Similar to inline, but allows some block properties like setting width and height
    - `table`: Behaves like the <table> element
    - `table-row` `table-cell` `list-item`: Behaves like its corresponding element
18. What's the difference between inline and inline-block?
    - Inline block can set width and height
    - Inline block can set margin and paddings on all sides. Inline can only set on horizontal sides.
19. What's the difference between the "nth-of-type()" and "nth-child()" selectors?
    - `p:n-th-child(2)` selector means in a `p` element, select the second child
    - `p:n-th-of-type(2)` selector means select the second paragraph child of a parent. It is less conditional
20. What's the difference between a relative, fixed, absolute and statically positioned element?
    - `static` - The default position; the element will flow into the page as it normally would. The top, right, bottom, left and z-index properties do not apply.
    - `relative` - The element's position is adjusted relative to itself, without changing layout (and thus leaving a gap for the element where it would have been had it not been positioned).
    - `absolute` - The element is removed from the flow of the page and positioned at a specified position relative to its closest positioned ancestor if any, or otherwise relative to the initial containing block. Absolutely positioned boxes can have margins, and they do not collapse with any other margins. These elements do not affect the position of other elements.
    - `fixed` - The element is removed from the flow of the page and positioned at a specified position relative to the viewport and doesn't move when scrolled.
    - `sticky` - Sticky positioning is a hybrid of relative and fixed positioning. The element is treated as relative positioned until it crosses a specified threshold, at which point it is treated as fixed positioned.
21. What existing CSS frameworks have you used locally, or in production? How would you change/improve them?
    - Bootstrap
    - Material UI
22. Have you played around with the new CSS Flexbox or Grid specs?
    - Flexbox is mainly meant for 1-dimensional layouts while Grid is meant for 2-dimensional layouts.
    - Flexbox solves many common problems in CSS, such as vertical centering of elements within a container, sticky footer, etc. Bootstrap and Bulma are based on Flexbox, and it is probably the recommended way to create layouts these days. Have tried Flexbox before but ran into some browser incompatibility issues (Safari) in using flex-grow, and I had to rewrite my code using inline-blocks and math to calculate the widths in percentages, it wasn't a nice experience.
    - Grid is by far the most intuitive approach for creating grid-based layouts (it better be!) but browser support is not wide at the moment.
## JavaScript
1. Explain event delegation
    - Event delegation is a technique involving adding event listeners to a parent element instead of adding them to the descendant elements. The listener will fire whenever the event is triggered on the descendant elements due to event bubbling up the DOM.
2. Explain how this works in JavaScript
    - The value of this depends on how the function is called.
        - If the new keyword is used when calling the function, this inside the function is a brand new object.
        - If apply, call, or bind are used to call/create a function, this inside the function is the object that is passed in as the argument.
        - If a function is called as a method, such as obj.method() — this is the object that the function is a property of.
        - If a function is invoked as a free function invocation, meaning it was invoked without any of the conditions present above, this is the global object. In a browser, it is the window object. If in strict mode ('use strict'), this will be undefined instead of the global object.
        - If multiple of the above rules apply, the rule that is higher wins and will set the this value.
        - If the function is an ES2015 arrow function, it ignores all the rules above and receives the this value of its surrounding scope at the time it is created.
3. Explain how prototypal inheritance works
    - All JavaScript objects have a prototype property, that is a reference to another object. When a property is accessed on an object and if the property is not found on that object, the JavaScript engine looks at the object's prototype, and the prototype's prototype and so on, until it finds the property defined on one of the prototypes or until it reaches the end of the prototype chain. 
4. What's the difference between a variable that is: null, undefined or undeclared? How would you go about checking for any of these states?
    - `Undeclared` variables are created when you assign a value to an identifier that is not previously created using var, let or const.
    - `Undefined` is a variable that has been declared, but not assigned a value
    - `null` will have been explicitly assigned to the null value. It represents no value and is different from undefined in the sense that it has been explicitly assigned. 
5. What is a closure, and how/why would you use one?
    - A closure gives you access to an outer function's scope from an inner function
    - You would use it for Data Privacy
6. Can you describe the main difference between a .forEach loop and a .map() loop and why you would pick one versus the other?
    - `.forEach` - iterates through the array and executes a callback on each element
    - `.map` - iterates through an array and returns a new array without mutating the original
7. What's a typical use case for anonymous functions?
    - They can be used in IIFEs to encapsulate some code within a local scope so that variables declared in it do not leak to the global scope.
    - As a callback that is used once and does not need to be used anywhere else. The code will seem more self-contained and readable when handlers are defined right inside the code calling them, rather than having to search elsewhere to find the function body.
8. What's the difference between host objects and native objects?
    - Native objects are objects that are part of the JavaScript language defined by the ECMAScript specification, such as String, Math, RegExp, Object, Function, etc.
    - Host objects are provided by the runtime environment (browser or Node), such as window, XMLHTTPRequest, etc.
9. Explain Ajax in as much detail as possible.
    - Ajax (asynchronous JavaScript and XML) is a set of web development techniques using many web technologies on the client side to create asynchronous web applications. With Ajax, web applications can send data to and retrieve from a server asynchronously (in the background) without interfering with the display and behavior of the existing page. By decoupling the data interchange layer from the presentation layer, Ajax allows for web pages, and by extension web applications, to change content dynamically without the need to reload the entire page.
10. Explain `"hoisting"`
    - Hoisting is a term used to explain the behavior of variable declarations in your code. Variables declared or initialized with the var keyword will have their declaration "moved" up to the top of their module/function-level scope, which we refer to as hoisting. However, only the declaration is hoisted, the assignment (if there is one), will stay where it is.
    - Note that the declaration is not actually moved - the JavaScript engine parses the declarations during compilation and becomes aware of declarations and their scopes. It is just easier to understand this behavior by visualizing the declarations as being hoisted to the top of their scope. Let's explain with a few examples.
    - Function declarations have the body hoisted while the function expressions (written in the form of variable declarations) only has the variable declaration hoisted.
    - Variables declared via let and const are hoisted as well. However, unlike var and function, they are not initialized and accessing them before the declaration will result in a ReferenceError exception. The variable is in a "temporal dead zone" from the start of the block until the declaration is processed.
11. Describe `event bubbling`
    - When an event triggers on a DOM element, it will attempt to handle the event if there is a listener attached, then the event is bubbled up to its parent and the same thing happens. This bubbling occurs up the element's ancestors all the way to the document. Event bubbling is the mechanism behind event delegation.
12. Describe event capturing
    - Event capturing is the event starts from top element to the target element. It is the opposite of Event bubbling, which starts from target element to the top element
13. What's the difference between an "attribute" and a "property"?
    - Attributes are defined on the HTML markup but properties are defined on the DOM.
14. Why is extending built-in JavaScript objects not a good idea?
    - Extending a built-in/native JavaScript object means adding properties/functions to its prototype. While this may seem like a good idea at first, it is dangerous in practice. Imagine your code uses a few libraries that both extend the Array.prototype by adding the same contains method, the implementations will overwrite each other and your code will break if the behavior of these two methods is not the same.
    - The only time you may want to extend a native object is when you want to create a polyfill, essentially providing your own implementation for a method that is part of the JavaScript specification but might not exist in the user's browser due to it being an older browser.
15. What is the difference between == and ===?
    - == is the abstract equality operator while === is the strict equality operator. The == operator will compare for equality after doing any necessary type conversions. The === operator will not do type conversion, so if two values are not the same type === will simply return false.
16. Explain the same-origin policy with regards to JavaScript.
    - The same-origin policy prevents JavaScript from making requests across domain boundaries. An origin is defined as a combination of URI scheme, hostname, and port number. This policy prevents a malicious script on one page from obtaining access to sensitive data on another web page through that page's Document Object Model.
17. Why is it called a Ternary operator, what does the word "Ternary" indicate?
    - "Ternary" indicates three, and a ternary expression accepts three operands, the test condition, the "then" expression and the "else" expression. 
18. What is "use strict";? What are the advantages and disadvantages to using it?
    - 'use strict' is a statement used to enable strict mode to entire scripts or individual functions. Strict mode is a way to opt into a restricted variant of JavaScript.
        - Advantages
            - Makes it impossible to accidentally create global variables.
            - Makes assignments which would otherwise silently fail to throw an exception.
            - Makes attempts to delete undeletable properties throw (where before the attempt would simply have no effect).
            - Requires that function parameter names be unique.
            - this is undefined in the global context.
            - It catches some common coding bloopers, throwing exceptions.
            - It disables features that are confusing or poorly thought out.
        - Disadvantages
            - Many missing features that some developers might be used to.
            - No more access to function.caller and function.arguments.
            - Concatenation of scripts written in different strict modes might cause issues.
19. Explain the difference between mutable and immutable objects.
    - A mutable object is an object whose state can be modified after it is created. An immutable object is an object whose state cannot be modified after it is created.
20. Explain what a single page app is and how to make one SEO-friendly.
    - Web developers these days refer to the products they build as web apps, rather than websites. While there is no strict difference between the two terms, web apps tend to be highly interactive and dynamic, allowing the user to perform actions and receive a response to their action. Traditionally, the browser receives HTML from the server and renders it. When the user navigates to another URL, a full-page refresh is required and the server sends fresh new HTML to the new page. This is called server-side rendering.
    - However, in modern SPAs, client-side rendering is used instead. The browser loads the initial page from the server, along with the scripts (frameworks, libraries, app code) and stylesheets required for the whole app. When the user navigates to other pages, a page refresh is not triggered. The URL of the page is updated via the HTML5 History API. New data required for the new page, usually in JSON format, is retrieved by the browser via AJAX requests to the server. The SPA then dynamically updates the page with the data via JavaScript, which it has already downloaded in the initial page load. This model is similar to how native mobile apps work.
    - The benefits:
        - The app feels more responsive and users do not see the flash between page navigations due to full-page refreshes.
        - Fewer HTTP requests are made to the server, as the same assets do not have to be downloaded again for each page load.
        - Clear separation of the concerns between the client and the server; you can easily build new clients for different platforms (e.g. mobile, chatbots, smart watches) without having to modify the server code. You can also modify the technology stack on the client and server independently, as long as the API contract is not broken.
    - The downsides:
        - Heavier initial page load due to the loading of framework, app code, and assets required for multiple pages.
        - There's an additional step to be done on your server which is to configure it to route all requests to a single entry point and allow client-side routing to take over from there.
        - SPAs are reliant on JavaScript to render content, but not all search engines execute JavaScript during crawling, and they may see empty content on your page. This inadvertently hurts the Search Engine Optimization (SEO) of your app. However, most of the time, when you are building apps, SEO is not the most important factor, as not all the content needs to be indexable by search engines. To overcome this, you can either server-side render your app or use services such as Prerender to "render your javascript in a browser, save the static HTML, and return that to the crawlers".
21. Explain the difference between synchronous and asynchronous functions.
    - Synchronous functions are blocking while asynchronous functions are not. In synchronous functions, statements complete before the next statement is run. In this case, the program is evaluated exactly in order of the statements and execution of the program is paused if one of the statements take a very long time.
    - Asynchronous functions usually accept a callback as a parameter and execution continue on the next line immediately after the asynchronous function is invoked. The callback is only invoked when the asynchronous operation is complete and the call stack is empty. Heavy duty operations such as loading data from a web server or querying a database should be done asynchronously so that the main thread can continue executing other operations instead of blocking until that long operation to complete (in the case of browsers, the UI will freeze).
22. What is event loop? What is the difference between call stack and task queue?
    - The event loop is a single-threaded loop that monitors the call stack and checks if there is any work to be done in the task queue. If the call stack is empty and there are callback functions in the task queue, a function is dequeued and pushed onto the call stack to be executed.
23. Explain the differences on the usage of foo between function foo() {} and var foo = function() {}
    - The former is a function declaration while the latter is a function expression. The key difference is that function declarations have its body hoisted but the bodies of function expressions are not (they have the same hoisting behavior as variables). If you try to invoke a function expression before it is defined, you will get an Uncaught TypeError: XXX is not a function error.
24. What are the differences between variables created using let, var or const?
    - Variables declared using the var keyword are scoped to the function in which they are created, or if created outside of any function, to the global object. let and const are block scoped, meaning they are only accessible within the nearest set of curly braces (function, if-else block, or for-loop).
25. Can you offer a use case for the new arrow => function syntax? How does this new syntax differ from other functions?
    - One obvious benefit of arrow functions is to simplify the syntax needed to create functions, without a need for the function keyword. The this within arrow functions is also bound to the enclosing scope which is different compared to regular functions where the this is determined by the object calling it. Lexically-scoped this is useful when invoking callbacks especially in React components.
26. What advantage is there for using the arrow syntax for a method in a constructor?
    - The main advantage of using an arrow function as a method inside a constructor is that the value of this gets set at the time of the function creation and can't change after that. So, when the constructor is used to create a new object, this will always refer to that object.
    - The main takeaway here is that this can be changed for a normal function, but the context always stays the same for an arrow function. So even if you are passing around your arrow function to different parts of your application, you wouldn't have to worry about the context changing.
    - This can be particularly helpful in React class components. If you define a class method for something such as a click handler using a normal function, and then you pass that click handler down into a child component as a prop, you will need to also bind this in the constructor of the parent component. If you instead use an arrow function, there is no need to also bind "this", as the method will automatically get its "this" value from its enclosing lexical context.
27. What is the definition of a higher-order function?
    - A higher-order function is any function that takes one or more functions as arguments, which it uses to operate on some data, and/or returns a function as a result. Higher-order functions are meant to abstract some operation that is performed repeatedly. The classic example of this is `map`, which takes an array and a function as arguments. map then uses this function to transform each item in the array, returning a new array with the transformed data. Other popular examples in JavaScript are `forEach`, `filter`, and `reduce`. 
28. Destructuring is an expression available in ES6 which enables a succinct and convenient way to extract values of Objects or Arrays and place them into distinct variables.
    - Array Destructuring - 
    
    `const foo = ["one", "two", "three"];`

    `const [one, two, three] = foo;`

    - Object Destructuring - 

    `const o = { p: 42, q: true };`

    `const { p, q } = o;`
29. ES6 Template Literals offer a lot of flexibility in generating strings, can you give an example?
    - ```console.log(`Hi, my name is ${person.name} and I am ${person.age} years old!`);```
30. Can you give an example of a curry function and why this syntax offers an advantage?
    - Currying is a pattern where a function with more than one parameter is broken into multiple functions that, when called in series, will accumulate all of the required parameters one at a time. This technique can be useful for making code written in a functional style easier to read and compose. It's important to note that for a function to be curried, it needs to start out as one function, then broken out into a sequence of functions that each accepts one parameter.
31. What are the benefits of using spread syntax and how is it different from rest syntax?
    - ES6's spread syntax is very useful when coding in a functional paradigm as we can easily create copies of arrays or objects without resorting to Object.create, slice, or a library function.
    - ES6's rest syntax offers a shorthand for including an arbitrary number of arguments to be passed to a function. It is like an inverse of the spread syntax, taking data and stuffing it into an array rather than unpacking an array of data, and it works in function arguments, as well as in array and object destructuring assignments.
32. How can you share code between files?
    - On the client (browser environment), as long as the variables/functions are declared in the global scope (window), all scripts can refer to them. Alternatively, adopt the Asynchronous Module Definition (AMD) via RequireJS for a more modular approach.
    - On the server (Node.js), the common way has been to use CommonJS. Each file is treated as a module and it can export variables and functions by attaching them to the `module.exports` object.
33. Why you might want to create static class members?
    - Static class members (properties/methods) are not tied to a specific instance of a class and have the same value regardless of which instance is referring to it. Static properties are typically configuration variables and static methods are usually pure utility functions which do not depend on the state of the instance.