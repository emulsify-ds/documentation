# Twig Extensions

Emulsify Design System uses a variety of plugins for Twig extensions:

1. [Twig Drupal Filters](https://www.npmjs.com/package/twig-drupal-filters): Adds Drupal Twig extensions for Storybook \(Twig.js\)
2. [Emulsify Twig Extensions](https://github.com/emulsify-ds/emulsify-twig-extensions): Adds BEM and Add Attributes custom Twig extensions for Storybook \(Twig.js\)
3. [Emulsify Twig](https://www.drupal.org/project/emulsify_twig): Adds BEM and Add Attributes custom Twig extensions for Drupal \(Drupal module\)

_Note: The `attach_library` Twig extension was deprecated in the latest version as Storybook has a better method for handling JavaScript. That function won't throw errors in Storybook, but it will not add your JavaScript. See `components/02-molecules/tabs/tabs.stories.js` for an example of how to add JavaScript for a component in Storybook._



