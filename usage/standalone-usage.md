# Standalone Usage

### Storybook

Develop: `yarn develop` or `npm run develop`

This combines 3 tasks:

1. `yarn webpack` \(Sass/CSS compiling/minifying/linting, SVG Spriting\)
2. `yarn babel` \(ES6 transpiling, minification\)
3. `yarn storybook` \(Storybook dev watch task\)

**Deploy Storybook**

`yarn deploy-storybook`

#### Generate Design System

`yarn styleguide` or `npm run styleguide`

#### Build Tasks

`yarn build` or `npm run build`

This combines 3 tasks:

1. `yarn build-webpack` \(same as `yarn webpack`  but without watch task and using [production](https://fourkitchens.gitbook.io/emulsify-design-system/help/webpack-and-build#project) webpack file\)
2. `yarn build-babel` \(same as `yarn babel` but without watch task\)
3. \(Coming soon\) `yarn build-styleguide`

#### Linting

`yarn lint`

