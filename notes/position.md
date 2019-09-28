# CSS Position

if u recall from the [CSS box model](the-box-model.md) notes, every element on the page is a box. the way these boxes stack up next to each other depends on whether they are inline elements or block elements. block elements will be the full width of their parent element by default && stack one on top of the other. inline elements will only be as wide as the content inside makes them && will line up one next to the other (until it reaches the end of the frame && then it wraps). there are a handful of ways to override this default layout, we discussd some of these in the box mode notes as well as the notes on [centering things](centering-things.md), another approach is using the "position" property, especially when u have a very *specific* spot on the page u want to place an element.

### [ex 1: `position: static;`](https://net-art-and-cultures.github.io/css-demos/demos/position-ex1.html)

the default or “normal flow” of block elements is `position: static;`, where block elements simply stack one on top of the other. u don’t need to specify `position: static;` block level elements have this by default.

### [ex 2: `position: relative;`](https://net-art-and-cultures.github.io/css-demos/demos/position-ex2.html)

by changing position to `position: relative;`, it allows u to use “offset” properties (top or bottom && left or right) which lets u “offset” the position of that element “relative” to where it would normally be, in the case of the example above: `top: 25px; left: 25px;`. note how this doesn't affect the position of any of the surrounding elements. Use ur web inspector to play with the top && left values in this example.

### [ex 3: `position: absolute;`](https://net-art-and-cultures.github.io/css-demos/demos/position-ex3.html)

with `position: absolute;` the element is taken out of normal flow, this means it no longer affects the position of the surrounding elements (which will now pretend that element was never there) && the offset properties `top: 25px; left: 25px;` are now relative to the parent element (in this case the body). change ur window size around && notice how the red element stays absolutely positioned in the spot (top/left) defined while the others remain centered.

### [ex 4: `position: fixed;`](https://net-art-and-cultures.github.io/css-demos/demos/position-ex4.html)

the `position: fixed;` is similar to the 'absolute' (in that it's taken out of normal flow) but the offset properties `top: 25px; left: 25px; `are now relative to the window itself (not the parent element) && so the element will not scroll with the rest of the page, rather it remain "fixed" where specified. resize ur window so that it's small enough that a vertical scroll bar appears, scroll up/down && compare the difference between ex4 && ex3.

the position doesn't have to be specified in "top" "left" (though that's more common), say u wanted somthing always anchored to the bottom right hand corner relative to the window not the page (ie. `position: fixed;`) u could use  `bottom: 25px; right: 25px;` instead.

when using position relative, absolute or fixed there’s a good chance that ur element will overlap with other elements. by default the stacking order (which is in front of which) will be the same as the order the elements appear in ur HTML. u can override this by specifying a "z-index" (this is not a measurement in px, it’s a number specifying the stacking order) for example `z-index: -1;` or `z-index: 10;` etc.
