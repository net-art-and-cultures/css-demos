# Typography
### fonts, sizes, styles && states

typography is an art form: typeface anatomy, font pairing, cogent, measure, pica, widows && orphans, etc. behind all that lingo is an entire design discipline beyond the scope of this class. what follows are simply the tools necessary for how to realize ur typographic vision w/CSS.

<div style="text-align:center;font-size:32px;font-family:serif;text-transform:uppercase;letter-spacing:5px;"> serif </div>

serif's are the small lines at the ends of the letters. serif typefaces are often used for long passages in print as they are easier to read

<div style="text-align:center;font-size:32px;font-family:sans-serif;text-transform:uppercase;letter-spacing:5px;">  sans-serif </div>

sans-serif ("sans" means without), is a typeface w/no serifs. easier to read tiny text (looks good on low resolution screens) oftentimes also used in headers/titles.

<div style="text-align:center;font-size:32px;font-family:monospace;text-transform:uppercase;letter-spacing:5px;">  monospace </div>

in a monospace typeface each character is of equal length (not the case w/most typefaces), often times used for code b/c they line up in a perfect grid.

## font stack

the `font-family` property is used to specify the typeface u want to use in a particular CSS rule. the default font-family is "serif" `font-family: serif;` but u can also make it `font-family: sans-serif;` or `font-family: monospace;` (see above). these will default to whatever generic serif (or sans-serif or monospace) typeface file the user has saved on their computer. u can specify a specific typeface by name but the browser can only display a typeface (or font-family) if the user visiting the page has that typeface installed on their computer. the font-family property allows u to set a comma separated list of typefaces as it's values, each typeface serving as a back-up for the next (in the event the user doesn't have it downloaded), this is called a font-stack && u can see a list of popular examples at [cssfontstack.com](http://www.cssfontstack.com/). below are a few common examples from [css-tricks.com](https://css-tricks.com/snippets/css/font-stacks/)

```css
/* Times New Roman-based stack */
font-family: Cambria, "Hoefler Text", Utopia, "Liberation Serif", "Nimbus Roman No9 L Regular", Times, "Times New Roman", serif;

/* Modern Georgia-based serif stack */
font-family: Constantia, "Lucida Bright", Lucidabright, "Lucida Serif", Lucida, "DejaVu Serif", "Bitstream Vera Serif", "Liberation Serif", Georgia, serif;

/* Traditional Garamond-based serif stack */
font-family: "Palatino Linotype", Palatino, Palladio, "URW Palladio L", "Book Antiqua", Baskerville, "Bookman Old Style", "Bitstream Charter", "Nimbus Roman No9 L", Garamond, "Apple Garamond", "ITC Garamond Narrow", "New Century Schoolbook", "Century Schoolbook", "Century Schoolbook L", Georgia, serif;

/* Helvetica/Arial-based sans serif stack */
font-family: Frutiger, "Frutiger Linotype", Univers, Calibri, "Gill Sans", "Gill Sans MT", "Myriad Pro", Myriad, "DejaVu Sans Condensed", "Liberation Sans", "Nimbus Sans L", Tahoma, Geneva, "Helvetica Neue", Helvetica, Arial, sans-serif;

/* Verdana-based sans serif stack */
font-family: Corbel, "Lucida Grande", "Lucida Sans Unicode", "Lucida Sans", "DejaVu Sans", "Bitstream Vera Sans", "Liberation Sans", Verdana, "Verdana Ref", sans-serif;

/* Trebuchet-based sans serif stack */
font-family: "Segoe UI", Candara, "Bitstream Vera Sans", "DejaVu Sans", "Bitstream Vera Sans", "Trebuchet MS", Verdana, "Verdana Ref", sans-serif;

/* Impact-based sans serif stack */
font-family: Impact, Haettenschweiler, "Franklin Gothic Bold", Charcoal, "Helvetica Inserat", "Bitstream Vera Sans Bold", "Arial Black", sans-serif;

/* Monospace stack */
font-family: Consolas, "Andale Mono WT", "Andale Mono", "Lucida Console", "Lucida Sans Typewriter", "DejaVu Sans Mono", "Bitstream Vera Sans Mono", "Liberation Mono", "Nimbus Mono L", Monaco, "Courier New", Courier, monospace;

```

## font-size

<pre style="width:100%;text-align:center;"> <code style="text-align:center;">font-size: 16px;</code> </pre>

if u want to be exact use pixels, setting ur size to 16px means the space between the top of an l && the bottom of a j is equal to 16px. pixels are relative to the resolution of the screen, so the same px value will look larger in an 1280x800 resolution screen than it will on a 1920x1080 resolution screen.

<pre style="width:100%;text-align:center;"> <code style="text-align:center;"> font-size: 16pt; </code> </pre>

points is specifically for [print layout](https://benfrain.com/create-print-styles-using-css3-media-queries/) (meaning: `@media print { }`). technically a pt is 1/72 of an inch on paper, on a screen it will vary depending on the monitors pixel density (dots-per-inch), so avoid using pt for web design (but keep it in ur print styles).

<pre style="width:100%;text-align:center;"> <code style="text-align:center;"> font-size: 100%; </code> </pre>

the default font-size in a browser is 16px (different for h1,h2,etc.), when u use percentage values, it's relative to the parent's font-size (if none is set, than it's relative to 16px), so `font-size:50%;` would be 8px

<pre style="width:100%;text-align:center;"> <code style="text-align:center;"> font-size: 1em; </code> </pre>

ems are kind of similar to percentages (in that they're relative to the parent or default). 1em = the default/parent size. 2em = 200%, 0.5em = 50%, etc. there's also [rem](https://css-tricks.com/theres-more-to-the-css-rem-unit-than-font-sizing/) but i'll let u read up on that on ur own

## a little more type style

- `font-weight: bold;`
[font-weight](https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight) value can be normal or bold, or 100, 200, 300, ...800, 900

- `font-style: italic;`
[font-style](https://developer.mozilla.org/en-US/docs/Web/CSS/font-style) value can be either normal, italic or oblique

- `text-transform: uppercase;`
[text-transform](https://developer.mozilla.org/en-US/docs/Web/CSS/text-transform) value can be none, capitalize, uppercase, lowercase or full-width


- `text-decoration: underline;`
[text-decoration](https://developer.mozilla.org/en-US/docs/Web/CSS/text-decoration) value can be none, line-through, underline, overline (or both underline overline). u could also change any of their color like `text-decoration: underline red` or make them wavy `text-decoration: underline wavy;` or combo all three `text-decoration: underline wavy blue;`

- `line-height: 1.5em;`
[line-height](https://developer.mozilla.org/en-US/docs/Web/CSS/line-height) controls what typographers call leading, which is the amount of space between the descender (the part of a letter like y or j that falls beneath the baseline) and the ascender (the highest point of a letter like l or h)

- `letter-spacing: 0.5em; ` && `word-spacing: 2em;`
[letter-spacing](https://developer.mozilla.org/en-US/docs/Web/CSS/letter-spacing) && [word-spacing](https://developer.mozilla.org/en-US/docs/Web/CSS/word-spacing) specifies the space between letters && words (or what typographers call kerning).

- `vertical-align: super;`
[vertical-align](https://developer.mozilla.org/en-US/docs/Web/CSS/vertical-align) won't vertically center ur div (common mistake), instead this has to do w/an inline elements vertical relation to it's neighbor inline elements. values include sub for this effect, or super for this effect. also helpful for aligning img (which are inline elements) w/neighboring text are middle, top && bottom values

- `text-indent: 10px;`
[text-indent](https://developer.mozilla.org/en-US/docs/Web/CSS/text-indent) the space before the first line of a body of text

- `text-shadow: 5px 5px #555;`
[text-shadow](https://developer.mozilla.org/en-US/docs/Web/CSS/text-shadow) can take different arrangement of values, it can be written either offset-x offset-y color (like the example to the left), or offset-x offset-y blur-radius color or color offset-x offset-y blur-radius or color offset-x offset-y or just offset-x offset-y

there are a few more (including some newer experimental properties) you can  
[check out here](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Text)

## the `font:` property shorthand

the `font: 12px sans-serif;` property is a shorthand that combines many of the above properties in a single line. there's a few ways to use it (see examples below via [mdn](https://developer.mozilla.org/en-US/docs/Web/CSS/font))

```css
/* size | family */
font: 2em "Open Sans", sans-serif;

/* style | size | family */
font: italic 2em "Open Sans", sans-serif;

/* style | variant | weight | size/line-height | family */
font: italic small-caps bolder 16px/3 cursive;

/* style | variant | weight | stretch | size/line-height | family */
font: italic small-caps bolder condensed 16px/3 cursive;
```

## pseudo-elements/classes

there are a few pseudo-elements && pseudo-classes particularly suited for typography. if u recall from the class [CSS overview](https://github.com/net-art-and-cultures/syllabus-and-notes/tree/master/notes/css) notes, pseudo-classes && pseudo-elements are tacked on the the CSS selector when defining a new rule, like so:` p::first-letter{ font-size:24px; }` or `a:hover { color:#ff55ff; }`. a full list of [pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes) is available on the mozilla developer network as well as a full list of [pseudo-elements](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements). u can also find a list of every CSS selector and property in CSS-Tricks.com's [almanac](https://css-tricks.com/almanac/).

- `::first-letter (or :first-letter)`
selects the first letter of the first line of an element (so long as it isn't preceded by anything, like another element)

- `:link`
used w/`<a>` elements, defines a rule for links that haven't been visited yet

- `:visited`
the opposite of *:link*, this applies to links that -
have` been visited

- `:hover`
not just for links, this defines styles to be applied the moment u hover over that particular element (the styles will return back to normal when u hover out)

- `:active`
can be specified for any element that the user interacts w/ (like links or buttons or input fields) && applies the styles the moment the user interacts (when clicking down on the link or button for example)

- `:focus`
defines styles to be applied when the elment has "focus", which means when u're currently engaged w/the element (ex: when ur cursor is inside the input field, that particular filed is "in focus")

## Custom Typefaces using @font-face

i mentioned before that the browser can only display a typeface (or font-family) if the user visiting the page has that typeface installed on their computer. one way around this is using the `@font-face { }` rule. this enables u to use ur own custom font-files which get downloaded by the user, the same way other media elements (images, video, audio) on a page do. it requires at least two properties, font-family, where the value is whatever u want to name the typeface && a src property (w/a url path to the font file)

*(**NOTE**: because this method downloads the font itself to the user's computers, as w/any media file, legally this requires that u have the "rights" to use/distribute the font file. in the next section there's a list of font-services that help ease the pain of dealing w/copyright issues)*

```css

/* create ur @font-face rule
  the code below assumes there's a file called myfont.woff
  in the same folder as this css file  */

@font-face {
  font-family: 'MyCoolFont';
  src: url('myfont.woff');
}

/* then u use it like this */
.title {
  font-family: 'MyCoolFont';
  color: #555;
  font-size: 24px;
}

```

there are many different font file formats, but they don't all work in every browser. for this reason u can have multiple src properties in an @font-face rule pointing to differnt file formats of the same font. bellow is a chart that illustrates which file types work in which browsers. for a more thorough look at which browsers support which formats visit [caniuse.com](http://caniuse.com/)

| browser | EOT | OTF / TIFF | WOFF | WOFF2 | SVG |
|:-------:|:---:|:----------:|:----:|:-----:|:---:|
| IE 8-11 | yes | -          | -    | -     | -   |
| IE 9-11 | yes | yes        | yes  | -     | -   |
| Edge 12-14 | -| yes        | yes  | -     | -   |
| Firefox 40-45 | -| yes     | yes  | yes   | -   |
| Chrome 43-49 | -| yes     | yes  | yes   | -   |
| Safari 8-9 | -| yes     | yes  | -   | yes   |
| Opera 32-35 | -| yes     | yes  | yes   | -   |
| iOS Safari 8.4-9.1 | -| yes     | yes  | -   | yes   |
| Android 4.4-44 | -| yes        | yes  | -     | -   |
| Chrome for Android 46 | -| yes     | yes  | yes   | -   |

## Font Services

maybe u're not a type designer && don't have folders full of custom typefaces u've produced (&& thus have the rights to) ready to go in all the right formats for distribution on the web. or maybe u do, but ur site has so many custom fonts + downloading all those from ur server every time someone visits ur page takes too long && thus u need a service that can serve them up faster known as a CDN (or content delivery network), below are a list of services that handle all that for u.


- [fontsquirrel.com](http://www.fontsquirrel.com/)
free, download fonts à la carte. they've also got a great [webfont generator](http://www.fontsquirrel.com/tools/webfont-generator) which converts font files to other formats && creates the @font-face css code for u. they've also got a new [matcherator](http://www.fontsquirrel.com/matcherator) which can identify
the typeface in an image.

- [Google Fonts](https://www.google.com/fonts)
"free" (like most things google), all fonts are
open-source && hosted on google (ie. they are ur CDN)

- [Adobe Typekit](https://typekit.com/)
free-$99 year subscription (w/monthly plans available as well), gives u access to a bundle of fonts, price effects the amount of page-views (250,000+) a month && the amount of fonts u have access to. fonts are served
from their CDN

- [fontspring.com](http://www.fontspring.com/)
$25+ per font. purchase fonts à la carte. no
subscription (unlimited use license)

- [fonts.com](http://www.fonts.com/)
free-$100 / year (monthy subscriptions also available) price effects the amount of page-views (250,000+) a month, the amount of fonts u have access to (free version comes w/watermark), access to special tools (
  including an online font editor) && other factors.

- [webtype.com](http://www.webtype.com/)
$40 per font. purchase fonts à la carte. price depends on page-views (250,000+) a month. year long license (free for 30 days, longer license available). they also have a free font swapper tool, which lets u preview
what a site would look like w/an alternative font

- [typography.com](http://www.typography.com/)
$99-$299 year subscription, price effects the amount of page-views (250,000+) a month. gives u access to a bundle of fonts. includes 5 font packages (additional
  come at a cost), fonts are served from their CDN

- [typotheque.com](https://www.typotheque.com/)
90€ per font. purchase fonts à la carte (subscription / CDN service also available)
