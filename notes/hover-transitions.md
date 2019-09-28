# Changing on `:hover` && CSS Transitions

In the class notes reviewing the basics of [CSS](https://github.com/net-art-and-cultures/syllabus-and-notes/tree/master/notes/css) i mention that CSS selector's can also be followed by [pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes), which specify a particular "state" the element can be in. the example below shows a very common use of the `:hover` pseudo-class.

### [ex 1: hovering over links](https://net-art-and-cultures.github.io/css-demos/demos/hover-transitions-ex1.html)

```css
a {
  color: #0366d6;
  text-decoration: none;
}

a:hover {
  color: #418be0;
}
```

in this example i've chanted the default link color to a more pleasent blue (in my subjective opinion) && i've also removed the default underline that shows up in HTML links using `text-decoration: none;`. by creating a second CSS block for the `a` w/the pseudo-class `:hover` i can define another set of CSS properties which will conditionally render only in that case (ie. when u hover over an `<a>`). in this case i'm changing the color to a slightly lighter blue.


## Transitions

an element's style can change during the user's interaction w/the page (either via JavaScript or via pseudo-classes/elements like :hover, :visited, etc) && when they do it happens immediately. the CSS transition property[s] is a way to do just that: transition between one style && another (in the event that they change), we'll use :hover in this tutorial (+other pseudo-classes in the example link) but don't forget there are other ways to change an element's style (&&thus other ways to leverage the transition property[s]), like w/JavaScript for example.

### [ex 2: CSS Transitions](https://net-art-and-cultures.github.io/css-demos/demos/hover-transitions-ex2.html)

u need to two properties to get things to started "transition-property" which takes as its value the property (or list of properties separated by commas) u want to transition for ex `transition-property: color;`, && "transition-duration" which is the time u want it to take to transition (written in either seconds like 1.5s or milliseconds like 1500ms) like this `transition-duration: 0.5s;`

```css
h1 {
  color: #000000;
  font-size: 20px;
  transition-property: color, font-size; /* transition any changes to these properties */
  transition-duration: 1s; /* ...over the course of 1 second */
}

h1:hover {
  /* change the color && font-size on hover && thus trigger the transition */
  color: #ff00ff;
  font-size: 30px;
}
```

u can set a delay in seconds or milliseconds to trigger the transition a short while after the event (in this case hover) w/the `transition-delay: 0.5s;`

u can also control the speed-curve (easeing) of the transition w/the "transition-timing" property, values can be either ease (slow start, then fast, then end slowly - this is default) linear (consistent speed from start to end) ease-in (slow start) ease-out (slow end) ease-in-out (slow start and end) cubic-bezier(n,n,n,n) (lets you define ur own values in a cubic-bezier function), for example `transition-timing-function: ease-in;`

```css
h1 {
  color: #000000;
  font-size: 20px;
  transition-property: color, font-size;
  transition-duration: 1s;
  transition-delay: 0.5s; /* wait half a second after hover before transitioning */
  transition-timing-function: ease-in; /* start slow then speed up */
}

h1:hover {
  color: #ff00ff;
  font-size: 30px;
}
```

while u can also combine transition multiple properties by including other values in a comma separated list (like above). u can also apply the same transition to any/all properties that change like this: using "all"

```css
{
  transition-property: all;
}
```

it's also worth noting that u can combine them all in a single line using the "transition" property (it can be a useful shorthand that keeps ur code cleaner)

```css
{
  transition: color 0.5s eas-in-out;
}
```
