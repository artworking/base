# Artworking project base

This is a starting point for all frontend builds at [Artworking](http://artworking.uk/). This repository serves to standardise and document our frontend development process somewhat. We figured other developers may get a kick out of seeing how we do things and decided to make it public.

## Downloading

For now, just grab a copy of the [latest version (zip)](https://github.com/artworking/base/archive/master.zip) – in the future, we’ll be creating [releases](https://github.com/artworking/base/releases) instead.

## Updating base files

Spotted a bug? Want to add a new feature? Don’t fix it just on the project you’re working on.

1. [Raise an issue.](https://github.com/artworking/base/issues/new)
2. Clone a copy of this repository, fix and test thoroughly.
3. Commit and push your changes to GitHub, and [close the issue](https://help.github.com/articles/closing-issues-via-commit-messages/).

## Coding guidelines

Please start at the [coding guidelines introduction](https://github.com/artworking/base/blob/master/doc/intro.md).

Please do not commit this readme file or the `doc/` directory to your projects.

## Changelog

### 2015-06-18

- Added the [stretch object](https://github.com/artworking/base/blob/master/css/sass/generic/_stretch.scss).
- Added the [ratio object](https://github.com/artworking/base/blob/master/css/sass/generic/_ratio.scss).

### 2015-06-15

- Removed Modernizr by default (it’s still in `js/vendor/` if needed) and replaced it with [HTML5 Shiv](https://github.com/afarkas/html5shiv) and a small inline script to change the `no-js` class on the `html` element to `js` (if you decide to use Modernizr, remove these other two bits of code).
