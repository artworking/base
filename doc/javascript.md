# JavaScript

## Native JavaScript

Avoid jQuery unless it’s really necessary. Changing a single CSS property on an element with an `id` is as simple as:

```javascript
document.getElementById("foo").style.display = "none";
```

One day it will be nice to switch to [Zepto](http://zeptojs.com/) when we can safely stop supporting IE9 and below.

## jQuery

Currently our standard JavaScript library is jQuery. Using conditional comments in our HTML, we use the 2.x branch on more modern browsers with a fallback to 1.x for IE8 and below. 

```html
<!--[if lte IE 8]>
    <script src="/js/vendor/jquery-1.11.3.min.js"></script>
<![endif]-->
<!--[if !IE]> -->
    <script src="/js/vendor/jquery-2.1.4.min.js"></script>
<!-- <![endif]-->
```

Don’t include jQuery in a project unless you actually need it.

### Selectors

Never attach behaviour to classes which are also used for styling. For clarity, prefix your behavioural classes with `js-`.

```html
<a href="..." class="button">Click me</a>
```

```css
.button {
    color: #f00;
}
```

```javascript
$(".button").on("click", handler);
```

In the above scenario, the `.button` class cannot be applied to any HTML element without potentially unwanted side-effects.

```html
<a href="..." class="button  js-button">Click me</a>
```

```css
.button {
    color: #f00;
}
```

```javascript
$(".js-button").on("click", handler);
```

Please be mindful of selector performance. The ID selector is the fastest and should always be used when targetting a specific element where reuse is not a concern.

```javascript
$("#header").addClass("hidden");
```

The class selector should be used when targetting multiple elements – however, it should be qualified with a tag name when possible to speed up resolution.

```javascript
$("a.js-open-popup").on("click", handler);
```

Nesting jQuery selectors can cause performance issues.

```javascript
// instead of
$("#header a.nav-item");

// consider
$("#header").find("a.nav-item");
```

When a jQuery selector is to be used multiple times, please cache it in a local variable before its first use:

```javascript
var popupButtons = $("a.js-open-popup");

popupButtons.on("click", handler);

doSomethingElse(popupButtons);
```

### Manipulation

Many JavaScript animations can be achieved using CSS animations or transitions instead. Delegate the bulk of the work to CSS wherever possible.

Instead of:

```javascript
$("#logo").animate({
    top: 50,
    opacity: 0.5
}, 250);
```

Consider:

```css
.logo {
    transition: all ease 0.25s;
}

.logo--animated {
    top: 50px;
    opacity: 0.5;
}
```

```javascript
$("#logo").addClass("logo--animated");
```
