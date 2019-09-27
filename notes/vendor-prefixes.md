# Browser Wars
### support, prefixes && quirks

there were a few proposals for style languages in the early days of the web, Håkon W Lie [debuted CHSS](http://www.w3.org/People/howcome/p/cascade.html) (Cascading HTML Style Sheets, later renamed CSS) at a Web conference in Chicago in 1994. but proposals don't become a reality that web-developers can use until browser companies implement the recommendations in their software. the first to implement CSS was Microsoft Internet Explorer 3 in 1996 (Netscape, the other top browser of the time, followed shortly after).

*(side note: if u want to learn more about CSS history check out this amazing blog post [The Languages Which Almost Became CSS](https://eager.io/blog/the-languages-which-almost-were-css/) by Zack Bloom, or [ch 20](http://www.w3.org/Style/LieBos2e/history/) of Håkon Wium Lie && Bert Bos (the original inventors of CSS) book Cascading Style Sheets: Designing for the Web as well as the [history sections](https://books.google.com/books?id=jAGSAwAAQBAJ&lpg=PA1927&dq=Sfetcu%2C%20Nicolae.%20Web%20Design%20%26%20Development%3A%20Nicolae%20Sfetcu%2C%202014&pg=PT75#v=onepage&q&f=false) in Web Design & Development By Nicolae Sfetcu)*

CSS has been evolving ever since. everyone/anyone interested in the future of CSS is subscribed to the [www-style](http://lists.w3.org/Archives/Public/www-style/) mailing list where discussions about the CSS specification (the design that browser makers follow) take place. included in this email group are the members of [the CSS Working Group](http://www.w3.org/Style/CSS/members) (some of whom work at companies who make browsers), they have the final say on what should/shouldn't be a part of CSS.2 when they release recommendations or changes to the spec it's up to the browser vendors (companies) to update their software to properly render the new CSS. sometimes that takes a bit, which is why when new CSS properties are decided on by the working group, it might be a while before they work in all browsers. a great website to check whether or not a particular browser has implemented a particular CSS feature is [caniuse.com](http://caniuse.com/)

*(other side note: u can check out the latest CSS happenings at the working group's [current work](http://www.w3.org/Style/CSS/current-work) page && even if u don't subscribe to the mailing list, the email discussion is all public && accessible [here](http://lists.w3.org/Archives/Public/www-style/) && if one day u decide u are interested in participating in the development of the CSS spec, [start here](http://www.w3.org/Style/CSS/current-work#contribute))*


## experimenting w/the new stuff

every browser has something called a [rendering engine](https://en.wikipedia.org/wiki/Web_browser_engine) built into it: this is the part of the browser that handles drawing the HTML/CSS onto the screen. Safari, Kindle, Blackberry && others use a popular open-source engine called [WebKit](https://en.wikipedia.org/wiki/WebKit) (Chrome made their own version of WebKit known called [Blink](https://en.wikipedia.org/wiki/Blink_%28web_engine%29)), Mozilla has their own open-source engine (which they use in Firefox && other apps) called [Gecko](https://en.wikipedia.org/wiki/Gecko_%28software%29) (now there's [Servo](https://en.wikipedia.org/wiki/Servo_(software))). Microsoft uses their own proprietary engine called [Trident](https://en.wikipedia.org/wiki/Trident_%28layout_engine%29) for Internet Explorer, but for Edge they use the same stuff Chrome uses. && there are more! when the CSS WG is working on a new CSS feature && the browser vendors want to be early adopters (or when vendors want to experiment w/their own new CSS ideas) these properties usually have to be "prefixed" w/the vendor name. eventually the CSS property may become part of the official spec, at which point all browsers will be expected to implement it && web-developers no longer need to include the prefix.

- `-webkit-` for Wekbit browsers (Safari, Chrome, Edge etc.)
- `-moz-` for Gecko browsers (Firefox)
- `-o-` for Opera (which uses [Presto](https://en.wikipedia.org/wiki/Presto_%28layout_engine%29))
- `-ms-` for Microsoft (ie. Trident in Internet Explorer)

for example:
```css
div {
-webkit-border-radius: 5px;
-moz-border-radius: 5px;
-o-border-radius: 5px;
-ms-border-radius: 5px;
border-radius: 5px;
}
```
(*though now all u need is just `border-radius: 5px;`*)

## cross-browser testing

b/c every browser implements new updates at their own pace && b/c not every vendor implements the CSS standard the same way in the rendering engine CSS code doesn't always get rendered the same way on every browser. for this reason it's very important to test ur page on all the major browsers. u might not have access to every browser (b/c u might not be running Windows, Apple && Linux simultaneously), for this reason there are services u can use to see what ur page looks like in different browsers using tools like [browserstack](https://www.browserstack.com/), [browsershots](http://browsershots.org/) + [others](http://mashable.com/2014/02/26/browser-testing-tools/#y.nHh6rZdGqP) (they come && go)

## normalize.css, a “browser reset”

one way to get around the fact that different render engines (&&thus browsers) display CSS differently is to use [normalize.css](http://necolas.github.io/normalize.css/), a stylesheet u can add to ur page which changes some CSS defaults to, “makes browsers render all elements more consistently and in line with modern standards. It precisely targets only the styles that need normalizing.” the stylesheet itself has lots of helpful comments which explain exactly what's going on && why.  
