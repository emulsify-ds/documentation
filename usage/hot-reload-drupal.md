---
description: Use BrowserSync to hot reload Drupal after changes
---

# Hot Reload Drupal

### Instructions

1. Install BrowserSync and BrowserSync Webpack plugin

```text
npm install --save-dev browser-sync browser-sync-webpack-plugin
```

    2.  In webpack/plugins.js, add the following \(this example uses a Lando url\):

```text
const _BrowserSyncPlugin = require('browser-sync-webpack-plugin');

const BrowserSyncPlugin = new _BrowserSyncPlugin({
  proxy: 'http://PROJECT.lndo.site',
  port: 32778,
});

module.exports = {
  ...
  BrowserSyncPlugin,
};

```

    3. In webpack/webpack.dev.js, add the following:

```text
const plugins = require('./plugins');

module.exports = merge(common, {
  ...
  plugins: [
    plugins.BrowserSyncPlugin,
  ],
});
```

This will add hot reloading for Drupal for a Lando project. Your local environment may require different settings \(proxy, port, etc.\). See [BrowserSync's docs](https://www.browsersync.io/docs/) for more info.

### Troubleshooting:

If you do not see your changes hot reloading when editing files, make sure your Drupal caching settings are [completely disabled](https://www.drupal.org/node/2598914). 

