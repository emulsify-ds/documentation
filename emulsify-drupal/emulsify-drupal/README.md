---
description: >-
  Install the component library (Storybook/Webpack) for prototyping and/or as a
  Drupal theme
---

# Emulsify Drupal

## Installation

### Requirements

1. [PHP 7.1](http://www.php.net)
2. [Node (we recommend NVM)](https://github.com/nvm-sh/nvm)
3. [Composer](https://getcomposer.org)

### Picking a version:

* **2.x** - Drupal 8.x compatible
* **3.x** - Drupal 9.x compatible

## Inside a Composer-Based Drupal Instance

1. Require emulsify in your project. `composer require emulsify-ds/emulsify-drupal`
2. Move into the contrib Emulsify theme directory.`cd web/themes/contrib/emulsify-drupal`
3. Create your new custom theme by cloning emulsify `php emulsify.php "THEME NAME"` (Run `php emulsify.php -h` for other available options)
4. Move into your new custom theme directory `cd ../../custom/THEME_NAME/`
5. Install the theme dependencies `npm install`
6. Build theme `npm run build`
7. Enable your theme and its dependencies\*`drush then THEME_NAME -y && drush en components emulsify_twig -y`
8. Set your custom theme as the default `drush config-set system.theme default THEME_NAME -y`

\* `drush then` is the correct command for Drush versions >= 9. `drush en` is the command to use for Drush versions <= 8.

Troubleshooting Installation: See [Drupal Installation FAQ](broken-reference).

_Note: Once you've created your custom theme, you can remove Emulsify as a dependency of your project. If you'd like to get updates as we push them, solely for educational/best-practice information, feel free to leave it in and receive the updates. Updating Emulsify will not affect your custom theme in any way. You should not however enable both projects - only your custom theme._

_If you do decide to remove the Emulsify Drupal dependency, make sure to move the two requires from its composer.json into your project-root composer.json. (The components, and emulsify\_twig modules are required for your custom theme to function, and need to be required somewhere in the composer chain.)_

## Standalone (for prototyping outside of a Drupal install)

1. Clone [Emulsify Drupal](https://github.com/emulsify-ds/emulsify-drupal) to your preferred location.
2. `cd` into that directory and run `php emulsify.php "New Theme" --machine-name new_theme --path none`. This will create your custom instance next to the one you cloned (you can now delete the git cloned version).
3. `cd` into your `new_theme` and run `npm install`
4. Now you can run `npm run develop` to start working on the components in isolation.
