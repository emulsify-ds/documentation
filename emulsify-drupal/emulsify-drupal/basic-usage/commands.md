---
description: Commands available in Emulsify Drupal
---

# Commands

### Storybook

Develop: `npm run develop`

This combines 2 tasks, which can be run separately as needed:

1. `npm run webpack` (Sass/CSS compiling/minifying/linting, SVG Spriting)
2. `npm run storybook` (Storybook dev watch task)

**Deploy Storybook**

`npm run storybook-deploy`

[Here is a demo](https://emulsify-ds.github.io/compound/) of the default Storybook Github deployment

### Linting JavaScript/Styles

`npm run lint`

### Testing Accessibility

`npm run a11y`: Will test the components specified in your a11y config file ([default](https://github.com/emulsify-ds/emulsify-drupal/blob/2.x/a11y.config.js#L17)). Note: this will also be run on commit via husky

### Build

`npm run build`

This runs the production webpack script and is intended for Drupal builds (e.g., in a CI environment.)
