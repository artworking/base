# HTML

Our preferred doctype is HTML5. Please do not use XHTML-style self-closing tags:

```html
<!-- bad -->
<img src="logo.jpg" alt="" />

<!-- good -->
<img src="logo.jpg" alt="">
```

HTML tags and attribute names must be written in lower case. Attribute values must be enclosed by double quotes (unless the value itself contains double quotes).

```html
<a href="..." title='This is when "single quotes" may be used'>...</a>
```

Multiple class names in HTML elements must be separated by two spaces.

```html
<p class="intro  gamma">...</p>
```

Each block-level element must start on a new line. Its contents must be indented by exactly one additional indentation level:

```html
<div class="grid">
    <div class="grid__item  one-half">
        <h3 class="section-heading">...</h3>
    </div>
</div>
```

An inline element’s contents may appear on the same line as its parent:

```html
<a href="..." class="twitter"><strong>Follow us on Twitter</strong></a>
```

Please use the above with caution – break and indent as necessary when readability starts to suffer.

```html
<a href="http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/">
    <span class="favourite" aria-label="Favourite">❤</span>
    MindBEMding – getting your head ’round BEM syntax
</a>
```

In general, there should be no empty lines between HTML elements. However, in areas dominated by lengthy copy, it may be preferable to break up sections of text with a single empty line to ease scanning.
