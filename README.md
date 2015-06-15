# Artworking project base

This is a starting point for all frontend builds at [Artworking](http://artworking.uk/).

## Downloading

For now, download a copy of the [latest version](https://github.com/artworking/base/archive/master.zip) – in the future, we’ll be creating [releases](https://github.com/artworking/base/releases) instead.

## Directory structure

Please read through the `README.md` file in each directory to get an idea of what’s expected there. As a general rule, `lib/` and `generic/` directories (and their files) should remain unchanged – see “updating base files” below.

## Codekit

All projects must use Codekit. The directory to add to Codekit is the parent directory of the project’s CSS directory, which may not always be the website’s root directory. For example, a WordPress project may have the following path to its CSS directory:

    ~/sites/website-name/wp-content/themes/theme-name/css

In this case, the following directory is imported into Codekit:

    ~/sites/website-name/wp-content/themes/theme-name

In your Codekit project, enable Sass and Autoprefixer. Compass is optional – enable it only when you think it will be useful. Never use Compass’s CSS3 mixins that do nothing more than add vendor prefixes (eg `border-radius()` or `box-shadow()`) – Autoprefixer takes care of this already.

The `config.codekit`, `config.rb` (when using Compass) and `.scss-lint.yml` must be committed to version control along with the rest of the project’s files. Do not add these to `.gitignore`. This allows all of us to use the exact same project settings when collaborating on a project.

## Updating base files

Spotted a bug? Want to add a new feature? Don’t just fix it on the project you’re working on.

1. [Raise an issue.](https://github.com/artworking/base/issues/new)
2. Clone a copy of this repository, fix and test thoroughly.
3. Commit and push your changes to GitHub, and [close the issue](https://help.github.com/articles/closing-issues-via-commit-messages/).

## Coding style

- Use 4 spaces for indentation.
- Use appropriate documentation comments for custom functions, mixins, etc in any language.

Language-specific coding guidelines can be found in the `doc/` directory, or below.

- [HTML](https://github.com/artworking/base/blob/master/doc/html.md)
- [CSS](https://github.com/artworking/base/blob/master/doc/css.md)
- [JavaScript](https://github.com/artworking/base/blob/master/doc/javascript.md)

## Documentation

Please do not commit this or the `doc/` directory to your projects.
