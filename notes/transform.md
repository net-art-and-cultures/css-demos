# CSS Transform

The CSS "transform" property can take a few different kinds (&& combinations) of values that let u reposition, rotate, scale && skew HTML elements. u can read more about it on [mdn](https://developer.mozilla.org/en-US/docs/Web/CSS/transform).

### [ex 1: translate](https://net-art-and-cultures.github.io/css-demos/demos/transform-ex1.html)

as we saw in the CSS [position](position.md) notes, the "position" property is one way to nudge things around, though this property is still actively used be developers, it's been around a while && has a few quirks. if/when u get frustrated w/positioning, the "transform" property with the "translate()" value could be the solve u're looking for. experiment with the example above in ur web inspector. note that in this exmaple i'm using `translate(25px, 25px);` to change both the "x" (left) && "y" (top) position, but u could also use `translateX(25px)` &&/or `translateY(25px)` as well as [translateZ()](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/translateZ) && [translate3d()](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/translate3d)

### [ex 2: scale](https://net-art-and-cultures.github.io/css-demos/demos/transform-ex2.html)

the [scale()](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/scale) value of the transform property can be used to change an element's size. u might ask, "isn't that what width && height are for?", while u can also change the size w/the width && height property sometimes u want to resize something proportionally, for example say u have lots of images on a page (all different sizes) && u want them to be half their original size, u can't do `width: 50%;` b/c as u might recall from the notes on [CSS units](css-units.md), `%` in this case is relative to the parent container, so u're saying make the image half the size of the parent element, not half the size of itself, for that u can do `transform: scale(0.5);` (u can also scale the width/height differently by passing two values `scale(0.5, 2)`)

### [ex 3: rotate](https://net-art-and-cultures.github.io/css-demos/demos/transform-ex3.html)

u can use the [rotate()](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/rotate) value of the transform property to rotate an element around. this can be specified in "degrees", ex `transform: rotate(180deg)` or in "turns" ex `transform: rotate(0.5turn)` or in "radians" `rotate(1.57rad)`. by default elements will rotate from there center, this is the default origin point, but u can change this with the "transform-origin" property. take a look at the example above with ur web inspector to see how i'm using these in combination. there is also a [rotate3d()](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/rotate3d) which can make things look 3 dimensional.

### [ex 4: skew](https://net-art-and-cultures.github.io/css-demos/demos/transform-ex4.html)

u can use the [skew()](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/skew) to warp an element, for example `transform: skew(50deg, 10deg);`. similar to the scale value, skew can take one value (applied to both x && y) or two separate values for x && y. similar to the rotate value, skew can take units of "turn" "deg" or "rad"


it's worth noting that u can mix && match these values, for example: `transform: translateX(25px) rotate(0.5turn)` will nudge the element 25 pixels to the right while also turning it upside down.
