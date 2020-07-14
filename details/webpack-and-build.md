# Webpack & Babel

Emulsify Design System uses [Webpack](https://webpack.js.org/) and [Babel](https://babeljs.io/) across all projects. See below for instructions on adding/editing specific Webpack and/or Babel configuration:

### Webpack

#### Storybook

Storybook's configuration including its Webpack configuration can be found in the `/.storybook` directory.  You can easily extend this configuration beyond the defaults, which for Emulsify Drupal includes loading twig, sass, YAML and linting styles.

#### Project

The Webpack build for the project found in the `/webpack` directory can be extended as well. By default it includes the following:

1. **SVG Spriting:** Any SVG added into the `images/icons` directory will be added to the sprite and is delivered via the icon component \(see `components/01-atoms/images/icons` for details\)
2. **Image minification**: Any images added into the `images` directory will be minified
3. **Sass/Stylelint/Minification**: By default, all sass files will be compiled and minified into a single CSS file with stylelint feedback for errors.

There are also some other niceties for feedback \(progress plugin\) and cleanup \(to keep the `dist` directory clean\). Also, by default there is a separate webpack configuration for development \(`webpack/webpack.dev.js`\) and production \(`webpack/webpack.prod.js`\). The development file is used when running `yarn develop` and the production task is meant to be used by the `yarn build-webpack` command for deployments.

### Babel

The project leverages Babel for the transpiling and minifying of JavaScript files for the Drupal project. The options for this are controlled by the following files:

1. **Babel config**: `./babel.config.js` \(Main config file\)
2. **Browser Support**: `./.browserslistrc` \(used by Babel env\)

