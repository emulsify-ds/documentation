# Webpack & Babel

Emulsify Design System uses [Webpack](https://webpack.js.org/) and [Babel](https://babeljs.io/) across all projects. See below for instructions on adding/editing specific Webpack and/or Babel configuration:

### Webpack

#### Storybook

Storybook's configuration, including its Webpack configuration, can be found in the `/.storybook` directory. You can easily extend this configuration beyond the defaults, which for Emulsify Drupal includes loading twig, sass, YAML, and linting styles.

#### Project

The Webpack build for the project found in the `/webpack` directory can be extended as well. By default it includes the following:

1. **SVG Spriting:** Any SVG added into the `images/icons` directory will be added to the sprite and is delivered via the icon component (see `components/01-atoms/images/icons` for details)
2. **Image minification**: Any images added into the `images` directory will be minified
3. **Sass/Stylelint/Minification**: By default, all sass files will be compiled and minified into a single CSS file with stylelint feedback for errors.

There are other niceties for feedback (progress plugin) and cleanup (to keep the `dist` directory clean). Also, by default, there is a separate webpack configuration for development (`webpack/webpack.dev.js`) and production (`webpack/webpack.prod.js`). The development file is used when running `yarn develop` and the production task is meant to be used by the `yarn build-webpack` command for deployments.

**Create separate CSS files per component**

As of version 4.2.0, Emulsify's webpack config compiles multiple SCSS files into multiple CSS files while keeping the default `style.css`. Any SASS file that is not a partial (its filename is not prefixed with an underscore) will have a file created in `dist/css`.

Prior to 4.2.0, Emulsify compiles all SASS files into one `style.scss` file. If you'd like to generate separate component-based css files to use in Drupal libraries, do the following:

1. In `webpack/plugins.js` change

```
const MiniCssExtractPlugin = new _MiniCssExtractPlugin({
  filename: 'style.css',
  chunkFilename: '[id].css',
});
```

To:

```
const MiniCssExtractPlugin = new _MiniCssExtractPlugin({
  filename: '[name].css',
  chunkFilename: '[id].css'
});
```

1. In the webpack directory create a css directory with the following structure. (Each js file should import its own `<component>.scss` file. Look at `webpack/css.js` for an example.)

```
.
└──webpack
│  └──css
│     │   component-1.js
│     │   component-2.js
```

1. In webpack.common.js replace

```
entries.css = path.resolve(webpackDir, 'css.js');
```

with

```
// CSS Files.
glob.sync(`${webpackDir}/css/*js`).forEach((file) => {
  const baseFileName = path.basename(file);
  const newfilePath = `css/${baseFileName.replace('.js', '')}`;
  entries[newfilePath] = file;
});
```

1. Now you can define CSS files in your Drupal libraries only where you need them, just like you do with js.
2. Finally, Storybook only loads the main `styles.scss` file, by default. So make sure you add anything not globbed into that file to `.storybook/preview.js`.

### Babel

The project leverages Babel for the transpiling and minifying of JavaScript files for the Drupal project. The options for this are controlled by the following files:

1. **Babel config**: `./babel.config.js` (Main config file)
2. **Browser Support**: `./.browserslistrc` (used by Babel env)
