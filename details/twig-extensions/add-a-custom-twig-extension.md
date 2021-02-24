# Add a Custom Twig Extension

### Storybook

**Step 1**: Create your extension. You can create a separate package like we have done with [Emulsify Twig Extensions](https://github.com/emulsify-ds/emulsify-twig-extensions), but you could also just put the extension directly into your project. For example, if you wanted to just add a simple Twig function that would just return the content passed in, you could create a file called `simple-function.js`. You can place it anywhere, but let's put it in the theme's `.storybook` directory. Here are the contents of our `.storybook/simple-function.js` file:

```
'use strict';

module.exports = simpleTwigExtension;

function simpleTwigExtension(Twig) {
  Twig.extendFunction("simple", function(content) {
    return content;
  });
}
```

You can see inside `Twig.extendFunction` that we are simply returning content, but you can write your extension functionality in here using JavaScript. 

**Step 2**: Import your extension into Twig.js. In `.storybook/setupTwig.js`, require your extension at top:

```bash
const twigSimple = require('./simple-function.js');
```

Below that inside of the `module.exports.setupTwig` function,  add your new function like so:

```bash
module.exports.setupTwig = function setupTwig(twig) {
  // Other stuff
  twigSimple(twig);
  return twig;
};
```

Now, Storybook and Twig.js will recognize your new function, so you can use it in any twig file!

```bash
{{ simple('test') }}
```

### Drupal

There are many excellent articles around the web on how to add a new twig extension. For an example of it done within a module, see our own [Emulsify Twig](https://www.drupal.org/project/emulsify_twig) module.

