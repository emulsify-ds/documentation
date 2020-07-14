---
description: Commands available in Emulsify Drupal
---

# Commands

### Storybook

Develop: `yarn develop` or `npm run develop`

This combines 3 tasks, which can be run separately as needed:

1. `yarn webpack` \(Sass/CSS compiling/minifying/linting, SVG Spriting\)
2. `yarn babel` \(ES6 transpiling, minification\)
3. `yarn storybook` \(Storybook dev watch task\)

**Deploy Storybook**

`yarn deploy-storybook`

[Here is a demo](https://storybook.emulsify.info/) of the default Storybook Github deployment

### Linting JavaScript

`yarn lint`

### Testing Accessibility

`yarn a11y`: Will test the components specified in your a11y config file \([default](https://github.com/emulsify-ds/emulsify-drupal/blob/2.x/a11y.config.js#L17)\). Note: this will also be run on commit via husky

### Build

`yarn build` or `npm run build`

This combines 2 tasks and is intended for Drupal builds \(e.g., in a CI environment\):

1. `yarn build-webpack` \(same as `yarn webpack`  but without watch task and using [production](../details/webpack-and-build.md#project) webpack file\)
2. `yarn build-babel` \(same as `yarn babel` but without watch task\)

