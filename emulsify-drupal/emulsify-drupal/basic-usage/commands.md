---
description: Commands available in Emulsify Drupal
---

# Commands

### Storybook

Develop: `npm run develop`

This combines 3 tasks, which can be run separately as needed:

1. `npm run webpack` (Sass/CSS compiling/minifying/linting, SVG Spriting)
2. `npm run babel` (ES6 transpiling, minification)
3. `npm run storybook` (Storybook dev watch task)

**Deploy Storybook**

`npm run deploy-storybook`

[Here is a demo](https://emulsify-ds.github.io/compound/) of the default Storybook Github deployment

### Linting JavaScript

`npm run lint`

### Testing Accessibility

`npm run a11y`: Will test the components specified in your a11y config file ([default](https://github.com/emulsify-ds/emulsify-drupal/blob/2.x/a11y.config.js#L17)). Note: this will also be run on commit via husky

### Build

`npm run build`

This combines 2 tasks and is intended for Drupal builds (e.g., in a CI environment):

1. `npm run build-webpack` (same as `npm run webpack`  but without watch task and using [production](../../../supporting-projects/webpack-and-build.md#project) webpack file)
2. `npm run build-babel` (same as `npm run babel` but without watch task)
