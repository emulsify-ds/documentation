---
description: Upgrading from the deprecated Emulsify Pattern Lab
---

# Upgrading

### Required Steps

1. Rename old theme directory.
2. Follow [Drupal installation instructions](design-system.md#drupal-installation) \(be sure and use your old name and machine name in the php script, e.g., `php emulsify.php "THEME NAME" --machine-name THEME_NAME`
3. Replace contents of the new theme's `components` directory with your old theme's `components/_patterns` contents. Be sure and change any library paths in style.scss, like so:

```text
// Old
@import "normalize";
@import "breakpoint-sass/stylesheets/breakpoint"

// New
@import "~normalize.css/normalize";
@import "~breakpoint-sass/stylesheets/breakpoint";
```

     4. Move any static contents \(e.g., `images` directory\) into the new theme.  
     5. Copy over Drupal files \(you may need to fix paths later\):

```text
*.theme
*.breakpoints.yml
*.info.yml
*.libraries.yml
```

     6. Uninstall/remove the unified\_twig\_extensions module, and enable            
           [emulsify\_twig](https://www.drupal.org/project/emulsify_twig).  
     7. Remove `node_modules` directory and run `yarn` or `npm install`.  
     8. Run `yarn develop` or `npm develop`.

### Optional Steps \(depending on your installation\)

1. Move any custom references inside `custom/nyusteinhardt_old/components/_meta/_00-head|_01-foot.twig` into `.storybook/preview-head.html` \(see [Storybook docs](https://storybook.js.org/docs/configurations/add-custom-head-tags/) for details\) and fix any reference paths. An example of this might be as follows:

```text
<!-- Old _00-head.twig -->
<link rel="stylesheet" href="../../js/slick/slick.css?{{ cacheBuster }}" media="all" />
<script src="../../js/slick/slick.min.js"></script>

<!-- New preview-head.html -->
<link rel="stylesheet" href="../js/slick/slick.css?{{ cacheBuster }}" media="all" />
<script src="../js/slick/slick.min.js"></script>
```

To complete the step above, you would add this `js` directory to the Storybook command in package.json like:

```text
"storybook": "start-storybook -s ./dist, ./images, ./js -p 6006",
"build-storybook": "build-storybook -s ./dist, ./images, ./js -o .out",
```

     2. You may need to copy over new Emulsify styles, e.g. for [the colors](https://github.com/emulsify-ds/emulsify-drupal/blob/develop/components/00-base/01-colors/_color-vars.scss).

### Writing Stories

Storybook only loads the stories you tell it to, so you will need to create \*.stories.js files. We have multiple examples in the new starter including ones using complex Twig includes, sharing data across components and using JavaScript \(see [usage](../usage/writing-stories.md) details\).

### Data

Data can still be handled via YML \(preferred\) or JSON files. However, you will need to handle any global data files differently \(see [usage](../usage/writing-stories.md) instructions\) as the new setup pays no attention automatically to the old `/components/_data` directory.

