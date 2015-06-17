# CSS

## Sass directory structure

Please read through the `README.md` file in each directory under `css/sass/` to get an idea of what’s expected there. As a general rule, `lib/` and `generic/` directories (and their files) should remain unchanged (see “updating base files” on the [main project README](https://github.com/artworking/base/blob/master/README.md)).

## Linting

Please run [SCSS Lint](https://github.com/brigade/scss-lint) regularly to check for inconsistent CSS. The linter output should be error-free before committing – see “hacks” below for when this isn’t possible.

You’ll notice by default the linter throws `EmptyRule` warnings when run on a freshly downloaded project base – this is known behaviour and intentional. Either fill in the gaps or remove the empty declarations, whatever the project dictates.

### Installing the Linter

```bash
sudo gem install scss_lint
```

### Running the Linter

```bash
cd /path/to/your/project/css/sass
scss-lint
```

### Linter errors

If you’re using a version of SCSS Lint older than 0.39.0, please run the following commands to remove it and install the newer version (note the name of the package has changed hence the need to remove and install from scratch):

```bash
sudo gem uninstall scss-lint
sudo gem install scss_lint
```

To find out which version you’re running:

```bash
scss-lint -v
```

## Vendor prefixes

Please avoid vendor prefixes – Autoprefixer adds them for you.

## Reset or normalize?

In all honesty we don’t mind which is used, which is why both can be found in the `vendor/` directory. Make sure only one is imported, naturally.

## Grids

Our standard grid system is [CSS Wizardry grids](https://github.com/csswizardry/csswizardry-grids) and is bundled with the project base. Please ensure it is configured correctly and only outputs the grid declarations that are needed for the website.

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

CSS should always be written with reusability in mind. Please read the [golden rules for writing reusable CSS](http://samhastings.com/guides/reusable-css/).

## Hacks

We’ve all been there: it’s 10 to 5 on a Friday afternoon and the _only_ way you can get that button’s link colour to behave is by sticking `!important` at the end of the CSS declaration. It’s quick and dirty and will do for now.

Put this declaration on its own in `_hacks.scss` (which is ignored by the linter) and refactor it as soon as possible.

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
.icon--facebook { background-image: url('facebook.png'); }
.icon--twitter  { background-image: url('twitter.png');  }
.icon--linkedin { background-image: url('linkedin.png'); }



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

    &::pseudo-element {
        /* styles */
    }

    .nested-element {
        /* styles */
    }
}



/**
 * Mixin declaration
 */
@mixin mixin-name($foo, $bar: false) {
	// rules
}
```

## Property order

CSS properties must appear in the order defined in `.scss-lint.yml`. This ordering standard groups related properties.

Any missing properties (eg browser specific or otherwise rarely used properties) should go at the end of the style declaration in no particular order, and should probably be annotated with a brief explanation. It may also be worth [opening an issue](https://github.com/artworking/base/issues/new) so the property can be added into `.scss-lint.yml` for future projects.

## Shorthand properties

Avoid the `background` shorthand property which can appear messy. Use the `background-` properties individually instead.
