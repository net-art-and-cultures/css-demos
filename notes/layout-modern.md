# Grids

![grids](../images/grid.jpg)

as i mentioned in the oldschool layout notes, web-designers think layout in terms of grids. there was a time when we used `<table>` to create grid-type layouts, this however wasn’t what the table element was designed for && as is often the case w/these sorts of hacks, using tables this way comes w/a few issues. && so eventually developers started creating their own table-like grid using divs && CSS, but this tricky + required lots of CSS classes. but now in the era of CSS3 we have two different systems specifically designed for modern day grid layouts.

### [ex 1: Flexbox](https://net-art-and-cultures.github.io/css-demos/demos/layout-ex1.html)

Flexbox is a series of newer (CSS3) properties for evenly distributing content across rows &&/or columns. it's great for laying things out in responsive ways. Flexbox is a system, to enable it u set a parent element's display to "flex" like `display: flex`. once u'v done that u can use a number of flexbox related properties that give u lots of control over the way the child elements are displayed. there are also properties u can apply directly to the child elements of a flexbox parent. there's SO MUCH u can do w/this, so for a full reference of all the parent && child properties in a flexbox system i highly recommend [this reference by css-tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/).

that said, here's a high level + basic flexbox setup, let's assume u've got the following HTML
```html
<div class="menu">
  <div>File</div>
  <div>Edit</div>
  <div>View</div>
  <div>Tools</div>
  <div>Help</div>
</div>
```

b/c these are all divs, they will stack up one on top of the other (ie. a column) by default. but if we make the parent div `display: flex` they will automatically be displayed next to each other (ie. a row)

```CSS
.menu {
  display: flex;
}
```

now we can use other properties to further define what this row looks like. for example, the "justify-content" property can be used to space out the children in different ways, for example w/"space-between" them or "space-around" each or "space-evenly". we can also "center" them all or "flex-start" to left align && "flex-end" to right align.

```CSS
.menu {
  display: flex;
  justify-content: space-around;
}
```

u could also control the direction using `flex-direction: row;` (which is the default) or `flex-direction: row-reverse;` to revers the order, `flex-direction: column;` to arrange them as a column as well as `flex-direction: column-reverse;`. u could also control the way items wrap back around using "flex-wrap".

in the [notes on how to center things](centering-things.md) i demonstrated a few different ways to center items horizontally, but i didn't really talk about how to center them vertically... this has always been a little tricky w/CSS. but now w/flexbox it's much simpler. first we need to give our parent element a specific height, we can declare this in pixels or if we want the full height of the page it's best to use the viewport units `height: 100vh`. then we can use the flexbox "align-items" property like this:

```CSS
.menu {
  height: 100vh;
  display: flex;
  justify-content: space-around;
  align-items: center;
}
```

checkout the [ex 1: Flexbox](https://net-art-and-cultures.github.io/css-demos/demos/layout-ex1.html) demo && use ur web inspector to adjust the values to see how quickly u can create otherwise complex layouts. again, refer to [this reference by css-tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) to know what other properties && values u can use w/flexbox.


### [ex 2: CSS Grid](https://net-art-and-cultures.github.io/css-demos/demos/layout-ex2.html)

while flexbox is great for things like menus && simple layouts, if u've got a complex grid design u want to implement in a responsive way via CSS then u're likely gonna want to use the CSS grid system. just like flexbox this can be activated by setting a parent element's display to "grid", for ex: `display: grid;` which similarly unlocks a whole set of grid related properties, which also includes a set of properties that can e applied to individual child elements of the grid parent. css-tricks also has a great [CSS grid reference](https://css-tricks.com/snippets/css/complete-guide-grid/) similar to the flexbox one.

there's so much u can do, just check out these [different grid examples](https://gridbyexample.com/examples/), but to get u started here's another high level + basic grid setup. say we have the following HTML:

```html
<div class="row">
  <div>first</div>
  <div>second</div>
  <div>third</div>
</div>
```

again, the default behavior would be for those 3 child divs to extend the full width of the page && stack up on on top the other, but we can turn this into a row using CSS grid like this:

```CSS
.row {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-column-gap: 10px;
}
```

let's break that down, the `display: grid;` is what unlocks the other grid properties, declaring "grid-template-columns" let's us decide how big each column (ie. div) in that row should be. we could specify these in traditional units but w/CSS grid we get access to the `fr` which stands for "fraction" of the free space. by setting each 3 of the divs to `1fr` they'll be evenly spaced && sized, but we could also do something like `grid-template-columns: 1fr 2fr 1fr;`, which would make the second div twice the size of the first && last div. the `grid-column-gap: 10px;` adds a big of a gap (think margin) between each column (ie. div) in or grid row. check out the [CSS Grid](https://net-art-and-cultures.github.io/css-demos/demos/layout-ex2.html) demo for a slightly more complex example where we've got 3 grids of rows inside another parent grid.

if u resize ur browser in either the flex or grid example u'll notice it's pretty responsive && adapts nicely to the various screen sizes. that said, if u squeeze the browser window too tightly it might start to collapse in strange ways, this will most definitely happen on mobile. this is where `@media` queries comes in, but that's [the next section](media-queries.md)
