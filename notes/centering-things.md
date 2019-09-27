# Centering Things

one of the first questions which often comes up when learning CSS is "how do I center my content?". like anything u might want to do in CSS there are lots of different ways. the old-school way to do this was to use the `<center>` element, but this is **NOT RECOMMENDED** b/c this is an old HTML element which has since been depreciated (so it migth not work in certain browsers, especially as time goes on && browsers update + new browsers come out). instead u should use CSS to center stuff.

### [CSS Centering Example](https://net-art-and-cultures.github.io/css-demos/demos/centering-things.html)

if u want to center text inside of an element, for example if u want ur headers like `<h1>` to always center their texts, u could us the `text-align: center;` property, like this:
```CSS
h1 {
  text-align: center;
}
```

but sometimes u want the entire element to be centered, for example if u have a `<p>` element u want centered on the page regardless the user's browser width. this requires two steps, first setting a specific `width` or `max-width` on ur element (NOTE: if ur element is an inline element by default, like `<img>`, `<span>`, etc u'll also need to make it a block element like `display: block;`). the difference between the two is that setting a `width` will maintain that size regardless of the browser's width whereas setting a `max-width` will let the element shrink to a small size (if for example the browser width is smaller then the specified width value) while preventing the element from expanding larger then the specified size (if for example the browser width is larger). once u've got a specific width value set u can use this trick: `margin: 0 auto;`. u might recall from [the box model](the-box-model.md) notes that when margin is passed 2 values, the first corresponds to the top && bottom margins (in this case 0, ie. no margin) && the second corresponds to the left && right margins. when u set these to "auto" instead of a specific number it will automatically add as much margin as it can given the size of the browser, in effect pushing the element to the center.
```css
p {
  max-width: 500px;
  margin: 0 auto;
}
```

another (more modern) approach to centering things is using the [flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) system. when u set an element's display to flex: `display: flex;` it unlocks a whole series of extra CSS properties u can use to control the way it's children (the elements inside of this element) get displayed. one of these extra properties is "justify-content" which can be set to "center" `justify-content: center;`. there's A LOT more u can do w/flexbox but we'll leave that for later (ie. the [flexbox](notes/modern-layouts.md) notes).

```css
  .center-child {
    display: flex;
    justify-content: center;
  }
```

there are LOTS of other ways to put things where u want (center or otherwise) including the [position](notes/css-position.md) property && the [transform](notes/css-transform.md) property, but we'll save those details for their own notes.
