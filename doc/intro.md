# Intro

## Project layout

All projects must use Codekit. The directory which must be added to Codekit is the parent directory of the project’s CSS directory, which may not always be the website’s root directory. For example, a WordPress project may have the following path to its CSS directory:

    ~/sites/website-name/wp-content/themes/theme-name/css

In this case, the following directory is imported into Codekit:

    ~/sites/website-name/wp-content/themes/theme-name

In your Codekit project, enable Sass and Autoprefixer. Compass is optional – enable it only when you think it will be useful. Never use Compass’s CSS3 mixins that do nothing more than add vendor prefixes (eg `border-radius()` or `box-shadow()`) – Autoprefixer takes care of this already.

The `config.codekit`, `config.rb` (when using Compass) and `.scss-lint.yml` must be committed to version control along with the rest of the project’s files. Do not add these to `.gitignore`. This allows all of us to use the exact same project settings when collaborating on a project.

## SCSS Lint

We use a linter tool called SCSS Lint to pick up any obvious stylistic mistakes in SCSS files. In our project layout template, there file in the `css/sass` directory called `.scss-lint.yml`.

The warnings emitted by SCSS Lint should always be corrected prior to committing code. However, often there is not enough time to fix all issues when working toward a tight deadline, and a temporary quick fix is favourable. In such situations, add your quick fixes into the file `_hacks.scss` which is automatically ignored by the linter. These hacks should be refactored as soon as possible.

To run SCSS Lint, open a terminal window, browse to the Sass directory and run the following command:

    $ scss-lint .

Note: on most of our older completed projects, SCSS Lint is not enabled and probably won’t ever be as our practices have changed considerably over the years. Linting is only something we’re concerned with for future (and ongoing) projects.

## General coding style

- Use 4 spaces for indentation.
- Use appropriate documentation comments for custom functions, mixins, etc in any language.