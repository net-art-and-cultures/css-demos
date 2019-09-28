# the Cascade

often times u will have more than one CSS rule applying to the same element, understanding how CSS "cascades" helps clarify confusion over which takes precedence as well as enables u to write cleaner/simpler stylesheets w/less code that takes advantage of the cascade.


### [ex 1: what takes precedence?](https://net-art-and-cultures.github.io/css-demos/demos/the-cascade-ex1.html)

this first example can be confusing b/c there are multiple lines of seemingly conflicting CSS, it's hard to know which takes precedence, but here are a few basic rules for figuring that out...

#### Last One
when u have two identical selectors, the last of the two takes priority. see the two `p { }` selectors in the example above, the first sets the color to red, the second sets the color to gray. sense the second one is listed lass in the stylesheet it will override the former && take precedence.

#### Specificity
the most specific selector takes precedence over the less specific. in the example above `h1 { }` is more specific than `* { }` && `#main { }` is more specific than `h1 { }`. this is b/c the wildcard `*` selector means any/all elements (*NOTE: the asterisk symbol is used this way in other coding languages as well*) but the `h1` selector only targets `<h1>` elements (that's more specific) && the `#main` selector only targets elements with that particular id assigned to them (that's even more specific). NOTE: the Specificity is more important that the order, so even though `h1 { }` is written after `#main` in the style sheet, the later takes precedence b/c it's a more specific selector.

#### !important
when u want to force precedence on something, u can add override both of the previous rules by placing `!important` after any value in a CSS statement. consider the first `<h1>`, it has the `#main { }` rules applied to it, which is why it's colored purple instead of orange as specified in the `h1 { }` rules. the `#main { }` rules also includes `font-size: 28px;` && though `#main` is more specific, the font-size in `h1 { }` is set with importance `font-size: 18px !important;` && so the `<h1>` ends up being 18px in size.

inspect these elements with ur Web Inspector && edit the CSS to see how it effects the elements. for example, try removing `!important` && see what happens.

### [ex 2: more than one class](https://net-art-and-cultures.github.io/css-demos/demos/the-cascade-ex2.html)

in class (&& in [the CSS intro notes](https://github.com/net-art-and-cultures/syllabus-and-notes/tree/master/notes/css)) we discussed the different ways to include CSS on the page including inline-style using the HTML `style` attribute. so what happens when u have both a style attribute && a class attribute w/conflicting rules? like:

```html
<div style="color: purple;" class="red-text"> hello there! </div>
```

in this situation the text will be purple, b/c the inline styling always takes precedence over rules in an attached stylesheet or between `<style>` tags.

u can also apply more than one class to the same element, for example:

```html
<div class="red green"> hello there! </div>
```

notice that there's a space between "red" && "green", this means they are two different classes in the stylesheet`.red { }` && `.green { }`. both list of properties will be combined && applied to the `<div>`, but if there is a conflict, then the general "Last One" rule applies, whichever one of these two classes is defined last in the stylesheet takes precedence.

### [ex 3: Inheritance](https://net-art-and-cultures.github.io/css-demos/demos/the-cascade-ex3.html)

a child of another element will inherit many of it's CSS properties from it's parent element (like `font-size`, `font-family` && `color`) but it won’t inherit others (like `background-image`, `border` && `padding`). that said, u can force an element to inherit a property from it's parent which it would otherwise ignore by using the `inherit` value. in the example above, the `<h1>` tag is forced to inherit the border && padding values from it's parent (the `<div class="content">`). use ur Web Inspector to remove these && play w/the values to see how it works.
