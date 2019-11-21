# Commands

### Storybook

Develop: `yarn develop` or `npm run develop`

This combines 3 tasks:

1. `yarn webpack` \(Sass/CSS compiling/minifying/linting, SVG Spriting\)
2. `yarn babel` \(ES6 transpiling, minification\)
3. `yarn storybook` \(Storybook dev watch task\)

**Deploy Storybook**

`yarn deploy-storybook`

### Linting

`yarn lint`

### Build

`yarn build` or `npm run build`

This combines 3 tasks:

1. `yarn build-webpack` \(same as `yarn webpack`  but without watch task and using [production](../details/webpack-and-build.md#project) webpack file\)
2. `yarn build-babel` \(same as `yarn babel` but without watch task\)
3. \(Coming soon\) `yarn build-styleguide`

### Styleguide \(coming soon\)

`yarn styleguide` or `npm run styleguide`

