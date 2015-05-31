# CSS

## Naming conventions

### Class names

Typically we follow Bem naming conventions.

```css
.block {}
.block__element {}
.block--modifier {}
```

Please follow this style unless there is a compelling reason not to do so.

### Mixins & functions

Custom mixins and functions should follow the official Sass style of hyphen-separated lowercase names.

```scss
@mixin full-screen-overlay() {
	// styles
}

@function px-to-rem($px) {
	// code
}
```

## Reusability

CSS should always be written with reusability in mind. Here are the golden rules for writing reusable CSS:

### 1. Never use IDs in selectors

IDs by definition cannot be reused, and their high specificity causes too many issues. Always use a class selector instead.

### 2. Use nested selectors only when completely necessary

Remember that nesting can tightly couple styling to a specific HTML structure, which is usually undesirable. Always write selectors which are as portable as possible, ie those which can be applied to any element on the page.

    .sidebar .menu h2 {
        font-size: 2rem;
        color: #fc0;
    }

The above selector prevents reuse of the heading’s styles elsewhere. Refactor as follows:

    .widget-title {
        font-size: 2rem;
        color: #fc0;
    }

There are circumstances where nesting can be used effectively.

    .avatar {
        border: 2px solid #333;
        border-radius: 50%;
    }

    .header--dark .avatar {
        border-color: #fff;
    }

In the above example, a default `.avatar` ruleset is defined and then additional styles are applied when it appears in a certain parent element.

### 3. Selectors should rarely be qualified with tag names

Consider:

```css
h2.heading {
    /* styles */
}
```

The above styles can now only be applied to `h2` tags. This isn’t ideal when we want to use the same styles on a different tag – maybe an `h3`, for example. Omit the tag from this kind of selector as it brings no benefit.

Sometimes tag qualification is necessary.

```css
.button {
    display: block;
    padding: 6px 12px;
}

button.button {
    box-sizing: border-box;
    width: 100%;
}
```

In the above example, simply setting a `button` element to `display: block` won’t make it fill its container, hence the need for the additional instructions just for `button` elements.

### 4. Try and avoid undoing styles

If you find yourself undoing (not overriding) styles, it’s possible that the original styles were set too early and were too generic. Consider refactoring the undone styles into a separate ruleset.

```css
.widget {
    float: left;
    clear: left;
    margin-left: 25px;
}

.widget--full-width {
    float: none;
    clear: none;
    margin-left: 0;
}
```

The above should be refactored as follows:

```css
.widget--floated {
    float: left;
    clear: left;
    margin-left: 25px;
}
```

Now the additional `.widget--full-width` ruleset is not needed, and the floated styles can still be applied as and when needed.

### 5. Try and keep layout rules separate

```css
.logo {
    position: absolute;
    top: 25px;
    left: 50px;
    width: 250px;
    height: 75px;
    background-image: url('../images/logo.png');
}
```

Introducing a logo elsewhere on the site will result in odd behaviour unless we undo a bunch of positioning rules first.

Instead, add two classes to the element and style them separately.

```css
.logo {
    width: 250px;
    height: 75px;
    background-image: url('../images/logo.png');
}

.header__logo {
    position: absolute;
    top: 25px;
    left: 50px;
}
```

### 6. Override styles sensibly

Overriding previous styles is often needed. Be careful what you override, however – for example, it’s wise to avoid shorthand styles when overriding.

```css
.header {
    background-color: #eee;
    background-image: url(logo.png);
    background-position: 25px 50%;
}

.header--dark {
    background: #000;
}
```

In the above example, all `background-*` properties set originally will be undone, which is probably not desirable behaviour.

## CSS formatting

```scss
/**
 * Use docblock style comments to document rulesets. There is a hard
 * 80-character width limit for comment blocks.
 *
 * Use footnote-style annotations on properties whose purpose may not be
 * immediately clear, for example:
 *
 * 1. Stop child elements from overlapping rounded corners.
 */
.block {
    box-sizing: border-box;
    display: inline-block;
    overflow: hidden; /* [1] */
    border-radius: 5px;
}

.block--modifier {
    color: #f00;
}

    /**
     * Child elements' styles should be indented to match the DOM
     * structure.
     *
     * Comma-separated selectors should be separated onto multiple
     * lines.
     */
    .block__element,
    .block__other-element {
        margin-bottom: 15px;
    }



/**
 * Similar grouped rulesets can be condensed into single lines to
 * aid readability.
 */
.icon--facebook { background-image: url(facebook.png); }
.icon--twitter  { background-image: url(twitter.png);  }
.icon--linkedin { background-image: url(linkedin.png); }



/**
 * Four line breaks between blocks/sections.
 */
.other-block {
    /* styles */
}



/**
 * Sass-specific formatting rules.
 *
 * 1. @extend directives must appear first.
 * 2. Generic mixins come immediately after.
 * 3. Mixins with narrow scope (eg those that output only one or two
 *    styles) should appear in roughly the same order their raw CSS
 *    would.
 */
.widget {
    @extend .clearfix; /* [1] */
    @include fill-screen(); /* [2] */
    position: relative;
    @include font-size(20px); /* [3] */

    @media screen and (min-width: 600px) {
        /* styles */
    }

    &:pseudo-class {
        /* styles */
    }

    &:pseudo-element {
        /* styles */
    }

    .nested-element {
        /* styles */
    }
}
```

## Property order

CSS properties must appear in the order defined in .scss-lint.yml. This ordering standard groups related properties.

Any missing properties (eg browser specific or otherwise rarely used properties) should go at the end of the style declaration in no particular order, and should probably be annotated with a brief explanation.

