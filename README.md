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