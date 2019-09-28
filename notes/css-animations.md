# CSS Animations

in the beginning the web was pretty static. then in 1996 the Netscape 2.0 browser was released w/support for GIF animations! that same browser also shipped w/an API that enabled programmers to make plugins. this opened the door for FutureSplash (later renamed Flash), which folks at Microsoft loved so much they packaged it into Internet Explorer 3.0 by default. this ushered in a whole age of Flash dominated web animations. today there are lots of different browsers (&& devices) accessing the web + most don’t come w/the Flash plugin by default (some devices don’t support it at all) which has ushered in a new age of web animations. these days Flash is used for banner ads but not much else. lots has sprung up in it’s place: JavaScript driven DOM animations (w/libraries 2 like jQuery, D3.js && GASP), HTML5 canvas (also JavaScript), webGL && ... CSS Animations.

(*NOTE: there are also libraries for CSS animations, i like Daniel Eden's [animate.css](https://daneden.github.io/animate.css/), it's simple && nice*)

which route to go depends on what u’re trying to accomplish. generally u’ll end up using JavaScript for animations, but there are some situations where CSS transitions && animations can do the trick. a good rule of thumb might be: if it’s a tiny/simple thing like a fading background-color or a tiny image bounce than CSS transitions/animations might be the best solution, but if it’s much more complicated than that (like 100 bouncing images or a series of complex animations) than one of the other JavaScript routes is likely the way to go (to learn a bit more on CSS vs JS animations[ check out the post](https://css-tricks.com/myth-busting-css-animations-vs-javascript/) Jack Doyle of GASP wrote for CSS-Tricks)


the CSS "animation" system is similar to the "transition" system (see notes on [hover && transition](hover-transitions.md)) && consists of a set of properties which could be defined individually:


| property | description |
|:--------:|:------------|
| animation-name | the name of the animation u want to apply. |
| animation-duration | the time it takes for the animation to do one cycle. |
| animation-timing-function | easing (same as transition). |
| animation-delay | time before starting (same as transition). |
| animation-direction | 'normal' (resets itself after a cycle) or 'alternate' (reverses animation each cycle). |
| animation-iteration-count | number of cycles (how many times should the animation loop). |
| animation-fill-mode | the values applied before/after the animation (either forwards, backwards, both or none). |
| animation-play-state | pause/play the animation (paused, running, running) |

or, like transitions, they can be defined in a single line using the "animation" property, for example: `animation: drop 1s infinite;` is the same as `animation-name: drop; animation-duration: 1s; animation-iteration-count: infinite;`

before we can set an element to animate, we need to make an CSS animation rule w/the `@keyframes name { }`, w/in that rule we create keyframe sub-rules which contain where the CSS properties should be at a given point in the animation cycle. below is an example of what that looks like:


### [ex 1: bounce animation](https://net-art-and-cultures.github.io/css-demos/demos/animation-ex1.html)

```css
.ball {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  /* here are the animation settings for this element */
  animation-name: drop;
  animation-duration: 1s;
  animation-iteration-count: infinite;
  /* could also be written in one line like this... */
  animation: drop 1s infinite;
}

/* && here is the actual animation */
@keyframes drop {
  0% {
    transform: translateY(0px);
    background-color: #00BEE3;
  }
  100% {
    transform: translateY(100px);
  	background-color: #D71855;
  }
}
```

the `%` blocks specify what the CSS should look like (for any element with their animation property set to "drop") at that given point in the sequence (this is the percentage of the specified animation-duration), so 0% = the beginning of the cycle, 50% = half way, 100% = the end of the animation cycle. u can set up as many of these as u like.

below is a slightly more complicated animation called "bounce" (w/more keyframes)
```css
.ball {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background-color: #D71855;
  animation: bounce 0.8s infinite;
}

@keyframes bounce {
  0% {
    transform: translateY(0px);
    background-color: #D71855;
  }
  15% {
    transform: translateY(-100px);
    background-color: #900E37;
  }
  30% {
    transform: translateY(0px);
    background-color: #D71855;
  }
  45% {
    transform: translateY(-60px);
    background-color: #B01244;
  }
  60% {
    transform: translateY(0px);
    background-color: #D71855;
  }
  75% {
    transform: translateY(-20px);
    background-color: #C5164E;
  }
  100% {
    transform: translateY(0px);
    background-color: #D71855;
  }
}
```

### [ex 2: blinking CSS emoji](https://net-art-and-cultures.github.io/css-demos/demos/animation-ex2.html)

In the beginning HTML had elements && attributes like `<font>` && `<center>` which effected the style + layout of a page. When CSS was first introduced the idea was to "separate concerns", let HTML handle structure && CSS handle the style + layout. Over the years CSS has evolved to be able to do much more than just change the font color && center things. It's now an incredibly expresive animation tool, as the curated pens in this [CSS Art Gallery](https://github.com/net-art-and-cultures/syllabus-and-notes/blob/master/notes/css-gallery/README.md) can attest to. those are very advanced examples, but to get a taste for what it's like to use CSS to create + animate drawings (rather than simply layout content) below are (more or less) the same steps I took in class to create the blinking emoji.

we start w/the HTML. b/c our elements won't be containing any semantic content (no headers, by-lines or paragraphs here), the CSS itself is the content, we can create our whole design using the general purpose `<div>` element. first a parent div to contain the entire emoji (the "emoji-head"), inside of that we'll create 2 child divs, one for the "mouth" && another for the "eyes". the "eyes" div will itself contain two more child divs (one for each "eye")

```html
<div class="emoji-head">
  <div class="eyes">
    <div class="eye"></div>
    <div class="eye"></div>
  </div>
  <div class="mouth"></div>
</div>
```

we'll start w/the "emoji-head" class. we'll give it the width && height that we want && some background-color. rather than giving it a solid color, i wanted to give it a radial gradient. u can do this in CSS but it can be tricky to remember how, in these sorts of situations there's often "online CSS generators" that help u create specific lines of CSS like background gradients, [i used this one](https://cssgradient.io/). as u know from the [box model](the-box-model.md) notes, all elements are squares by default. but we can give them a border-radius of `50%` which will round out the corners enough to make it look like a circle.

```css
.emoji-head {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(254, 239, 0, 1) 0%, rgba(254, 166, 0, 1) 100%);
}
```
next we'll work on the "eye" class (which is shared by both the left && right eyes). these are also circles so we'll do what we did w/the head, give it a width && height, as well as a background-color (in this case a solid shade of gray) && a 50% border-radius.

```css
.eye {
  width: 10px;
  height: 10px;
  background-color: #2c302d;
  border-radius: 50%;
}
```

at this point our eyes will be stacked on on top of the other (which is the default layout of divs) && they will definitely not be in the right place (ie. centered in our emoji-head), so we'll handle placement in the "eyes" class assigned to the parent div of the two eye divs.

```css
.eyes {
  width: 100px;
  display: flex;
  justify-content: space-around;
  transform: translate(0px, 31px);
}
```

as i covered in the [modern CSS layout](layout-modern.md) notes, a quick way to get items to line up horizontally like a row is to use flexbox `display: flex;`, which unlocks all the other flexbox properties, including properties for how to space out the items in the row, in this case i'll use `justify-content: space-around;`. by default this div is as wide as it can be (not the way we want it), so we'll also want to give it a constraied width until the two eyes seem to be where we want them. lastly we'll want to use the `transform: translate()` property (covered in the [CSS transform](transform.md) notes) to adjust the y (top) offset until they are vertically positioned where we want them.

with the eyes finished we can move on to the "mouth". these sorts of curved shapes are best produced w/JavaScript or `<svg>` but b/c we're trying to push CSS to it's limits (like the examples in the [CSS Art Gallery](https://github.com/net-art-and-cultures/syllabus-and-notes/blob/master/notes/css-gallery/README.md)) we've got to think creatively about how we might make a curved smile shape. we know how to make circles already, so we'll do the same here, giving our "mouth" class a specific width, height && border-radius. except this time, rather than being the same size, the width will be a little longer than the height (to create more of an oval shape) && we won't give it any background-color. we'll leave it invisible, this is b/c we don't want to see the full oval, we only want it's shape in order to take advantage of the curve. what we'll do instead is give it a [box-shadow](https://developer.mozilla.org/en-US/docs/Web/CSS/box-shadow). like the name implies, the "box-shadow" property is how u apply shadows to elements in CSS. this one can be a little tricky to remember how to use, so naturally there are [box-shadow generators](https://www.cssmatic.com/box-shadow). i have it a solid 10px shadow on the bottom which (b/c the div itself is invisible) looks like a smile :)

```css
.mouth {
  width: 70px;
  height: 50px;
  border-radius: 50%;
  box-shadow: 0 10px 0 0 #2c302d;
  transform: translate(15px, 9px);
}
```

lastly i add another `transform: translate()` here to nudge it into the right position && we've got our emoji!

next it's time to animate it. i want the eyes to look like they're blinking, which can be easily done by adjusting the height from `10px` (the height value) down to `0px` && back again. i want the eyes to be open most of the time && only blink momentarily, so i'll set my animation to start w/the eyes closed, then a mere `5%` later i'll open them && leave them open for the majority of the animation (until `95%`), then i'll close them back at the end.

```css
@keyframes blink {
  0% { height: 0px; }
  5% { height: 10px; }
  95% { height: 10px; }
  100% { height: 0px; }
}
```

then we need to return to our "eye" class && actually apply this new "blink" animation used the "animation-name" property. we'll also adjust some of the default settings, i'll make the "animation-duration" 2 seconds && the "animation-iteration-count" "infinite" (this could also be a specific number if i only wanted the animation to play a certain number of times).

```css
.eye {
  width: 10px;
  height: 10px;
  background-color: #2c302d;
  border-radius: 50%;
  animation-name: blink;
  animation-duration: 2s;
  animation-iteration-count: infinite;
}
```

this isn't a bad place to stop, but there's still some more polishing we could do. u might notice that everytime the eyes blink the mouth moves up. this is b/c the mouth element is stacked below the "eyes" div && the eyes div has no predefined height, it's height is determined by the height of it's content (the inner "eye" divs) && so when they reduce to 0, so does the "eyes" div which essentially pulls the "mouth" div below it upwards. there's a couple things we can do here, we could create an animation for the mouth which nudges it down by 10px (the height of the eyes) at the same time that the eye blinks, something like this:

```css
.mouth {
  width: 70px;
  height: 50px;
  border-radius: 50%;
  transform: translate(15px, 9px);
  box-shadow: 0 10px 0 0 #2c302d;
  animation-name: shift-mouth;
  animation-duration: 2s;
  animation-iteration-count: infinite;
}

@keyframes shift-mouth {
  0% { transform: translate(15px, 19px); }
  5% { transform: translate(15px, 9px); }
  95% { transform: translate(15px, 9px); }
  100% { transform: translate(15px, 19px); }
}
```

but there's an even simpler hack. like i said, the issue is that "mouth" is below "eyes" && "eyes" has no height (it's only as tall as it's inner child "eye" divs), but if we give the parent "eyes" div a specific height (say 10px like the child divs when they're open), then it won't change height when the inner "eye" divs close && thus the "mouth" div won't get pull back up. that's how i solved the nudge in the example linked above.

beyond that i made a couple more polishes. i put the "emoji-head" inside of a `<section>` element (which is another general purpose element like the `<div>`) && used some of the techniques covered in the [modern CSS layout](layout-modern.md) notes to center the emoji on the page (i also gave it a radial gradient to give it a backdrop similar to the examples in the CSS Art Gallery). just for fun, i also gave the "emoji-head" a `transition` property && alternate `:hover` properties s othat the emoji spins around when i hover over it (see the [CSS hover && transition](hover-transitions) notes for how that works as well as the [CSS transform](css-transform.md) notes for how to rotate things)
