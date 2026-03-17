# Style Stage Source Sass

> A minimal starter for Style Stage submissions that includes the source Sass used to create the base Style Stage theme, and the source HTML.

[Read the full guidelines](https://stylestage.dev/guidelines/) to ensure your final styles will be ready for inclusion in the showcase!

## To Use

1. Fork or select "Use this Template"
2. Once cloned to your computer, run `npm i` to install dependencies needed to compile the Sass
3. Run `npm start` to launch a hot-reload server that watches for Sass changes.

## Sass Architecture Guide

This project follows a layered Sass architecture:

- `sass/global/` — global tokens and base element rules only (theme variables, reset, typography).
- `sass/composition/` — layout/structure rules (page regions, wrappers, panel placement).
- `sass/block/` — component/section-specific styles (`header`, `nav`, `features`, etc.).
- `sass/utility/` — reusable mixins/helpers shared across blocks.

### Authoring Rules

- Keep styles in the narrowest layer possible:
	- If it applies site-wide, place it in `global`.
	- If it controls layout flow, place it in `composition`.
	- If it styles one section/component, place it in `block`.
	- If it is reused in multiple places, create/use a `utility` mixin.
- Use nested selectors within each block file for readability, but avoid unnecessary depth.
- Prefer shared utility mixins for repeated interaction patterns (links, pill actions).

### Sass Module Usage

- This codebase uses `@use`/`@forward` (not `@import`).
- Layer entrypoints:
	- `sass/global/_index.scss`
	- `sass/composition/_index.scss`
	- `sass/block/_index.scss`
- Main entry file: `sass/style.scss`.
- Each partial should explicitly declare its own dependencies (`@use "../global/theme" as *;`, utility mixins, etc.) rather than relying on global scope.

The final stylesheet will be placed in `public/style.css`.

You may alter anything and everything, but keep in mind that the final stylesheet should be unminified and ideally non-prefixed. All Style Stage submissions are parsed with `autoprefixer` during the publish build process, and unminified stylesheets are easier for visitors to learn from.

> If you change the output stylesheet name, be sure to update the link to it in `index.html`

### Publish to Github Pages
This starter uses github actions to auto deploy `public` directory to `gh-pages` branch whenever there is a push to `main` branch.
1. Go to repo settings, under Github Pages, select `gh-pages` as source.
2. Go to https://username.github.io/stylestage-sass to see your published site.

## Submitting Your Stylesheet

Once you've created your stylesheet with this starter, publish this as a public repo and then you can use the GitHub link to the "raw" version of the `public/style.css` file for your final submission.

If you choose to publish to github pages, you can use:
https://username.github.io/stylestage-sass/style.css

You will need to fork [the main Style Stage repo](https://github.com/5t3ph/stylestage) to add your stylesheet, as [explained in the FAQ](https://stylestage.dev/guidelines/#how-do-i-create-a-pull-request-pr).
