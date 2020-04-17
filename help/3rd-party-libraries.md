---

description: Helpful information for those new to component-driven design
---

# Adding 3rd Party Libraries 

## Global Libraries (ie jQuery)

There are some instances in which a library should be available to all components, i.e. "global."

### jQuery

Use the following steps to make jQuery available to your component javascript files and to use additional libraries that require jQuery.

#### Add jQuery Library

```
yarn add jquery
```

### Add jQuery to Storybook Config

Create a ``./storybook/jquery-global.js`` file and add the following:

```javascript
import jquery from 'jquery';
global.jQuery = jquery;
global.$ = jquery;
```

Import this file in ``./storybook/config.js``:

```javascript
 import { action } from '@storybook/addon-actions';
+import './jquery-global.js';

```

This ensures that jQuery is loaded before other libraries. [See this explanation for details](https://stackoverflow.com/a/39820703). 

### Add jQuery as a Global in Webpack

Add the following to ``./storybook/webpack.config.js``:

```json
     loader: 'eslint-loader',
     options: {
       cache: true,
+      globals: [
+        'jQuery'
+      ],
     },
   });
```

### Example: Use jQuery in a Component

The following example will cause the error status message to blink.

#### Create JS file

Create ``components/02-molecules/status/status.js`` and add the following:

```javascript
($ => {
  Drupal.behaviors.status = {
    attach() {
      setInterval(() => {
        $('.status--error').fadeToggle();
      }, 500);
    },
  };
})(jQuery);
```

#### Update the Status Story

Add the new JS file to the ``components/02-molecules/status/status.stories.js`` and include the DrupalBehaviors effect:

```javascript
 import React from 'react';
+import { useEffect } from '@storybook/client-api';
 
 import status from './status.twig';
 
 import statusData from './status.yml';
 
+import './status';
+
 /**
  * Storybook Definition.
  */
 export default { title: 'Molecules/Status' };
 
-export const statusExamples = () => (
-  <div dangerouslySetInnerHTML={{ __html: status(statusData) }} />
-);
+export const statusExamples = () => {
+  useEffect(() => Drupal.attachBehaviors(), []);
+  return <div dangerouslySetInnerHTML={{ __html: status(statusData) }} />;
+};
```

Now if you run the storybook ``yarn develop`` you should see a blinking error message in the status molecule.

#### Add JS File to Theme Library and Load in the Template

Add the JS file to the theme library by editing ``MY_THEME.libraries.yml``:

```yml
     - core/drupal
+
+status:
+  js:
+    dist/js/02-molecules/status/status.js: {}
+  dependencies:
+    - core/drupal
+    - core/jquery
```

Make sure to include the drupal and jquery core libraries as dependencies. They will both be loaded before your JS file in Drupal.

The library then needs to be loaded in the component twig template. In this case edit ``components/02-molecules/status/status.stories.js`` and add:

```php
+{{ attach_library('THEME_NAME/status') }}
```

## Libraries for Individual Components

There are a couple of strategies for loading individual libraries.

### Add with Yarn

Add an external library using yarn by adding it to your project ``yarn add LIBRARY`` and then importing where needed.

### Load Library from an External URL

External libraries, for example from a CDN, can be loaded with [Storybook External Links](https://github.com/jhta/storybook-external-links). Install, ``yarn add storybook-external-links`` and add to the  ``./storybook/config.js`` or an individual story file:

```javascript
+import withExternalLinks from 'storybook-external-links';
+const url = '//[URL TO LIBRARY]';
+const externalLinkDecorator = withExternalLinks(url);
+addDecorator(externalLinkDecorator);
```


