# the Box Model

every element in an HTML page is a box, there’s essentially two kinds of boxes depending on whether the element is an inline element or a block element. every element is one of those by default: `<span> <a> <img>` are all inline elements `<div> <h1> <p>` are all block elements. but these defaults (like all defaults) can be overridden via CSS, in this case w/the `display` property, for ex: `img { display: block }`. the basic difference between the two is that block elements have default widths of 100% (so they stretch from the far left to the far right of their parent element) whereas inline elements are only ever as wide as their content. additionally, block elements always force a line-break (so they appear one on top of the other like a column), whereas inline elements line up next to each other (like a row).

### [example 1](...)

in this first example i've got 3 divs && 3 spans with only a little CSS to change their background color (so that we can see the actual boxes). the divs are "block" elements by default so those will be stacked vertically as well as expand the full width of their parent element (in this case the `<body>` element). the spans are "inline" elements by default so those will be lined up horizontally && only be as wide as the content inside of them.

use ur browser's "Inspector" tool (like we did in class) to edit the CSS of these elements. see what happens when u change a div from block to inline by adding `display: inline` to its CSS, or vice-versa: change a span from inline to block by adding `display: block` to its CSS. 
