# Artworking project base

## Downloading

For now, download a copy of the [latest version](https://github.com/artworking/base/archive/master.zip) – in the future, we’ll be creating [releases](https://github.com/artworking/base/releases) instead.

## Linter

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

## Directory structure

Please read through the `README.md` file in each directory to get an idea of what’s expected there. As a general rule, `lib/` and `generic/` directories (and their files) should remain unchanged – see “updating base files” below.

## Grids

Our standard grid system is [CSS Wizardry grids](https://github.com/csswizardry/csswizardry-grids) and is bundled with the project base. Please ensure it is configured correctly and only outputs the grid declarations that are needed for the website.

## Reset or normalize.css?

In all honesty we don’t mind which is used, which is why both can be found in the `vendor/` directory. Make sure only one is imported, naturally.

## Hacks

We’ve all been there: it’s 10 to 5 on a Friday afternoon and the _only_ way you can get that button’s link colour to behave is by sticking `!important` at the end of the CSS declaration. It’s quick and dirty and will do for now.

Put this declaration on its own in `_hacks.scss` (which is ignored by the linter) and refactor it as soon as possible.

## Updating base files

Spotted a bug? Want to add a new feature? Don’t just fix it on the project you’re working on.

1. [Raise an issue.](https://github.com/artworking/base/issues/new)
2. Clone a copy of this repository, fix and test thoroughly.
3. Commit and push your changes to GitHub, and [close the issue](https://help.github.com/articles/closing-issues-via-commit-messages/).
