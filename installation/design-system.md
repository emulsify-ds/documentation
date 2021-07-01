---
description: >-
  Install the component library (Storybook/Webpack) for prototyping and/or as a
  Drupal theme
---

# Emulsify Drupal

1. [Drupal Installation](design-system.md#drupal-installation)
2. [Standalone Installation](design-system.md#standalone-installation-prototyping-and-or-contribution)

### Drupal Installation

#### Requirements

1. [PHP 7.1](http://www.php.net/)
2. [Node \(we recommend NVM\)](https://github.com/creationix/nvm)
3. [Composer](https://getcomposer.org/)
4. [Yarn](https://yarnpkg.com/) \(optional\)

#### Picking a version:
- **2.x** - Drupal 8.x compatible
- **3.x** - Drupal 9.x compatible

#### Composer \(recommended\)

1. Require emulsify in your project `composer require emulsify-ds/emulsify-drupal`
2. Move into the contrib Emulsify theme directory`cd web/themes/contrib/emulsify-drupal`
3. Create your new custom theme by cloning emulsify `php emulsify.php "THEME NAME"` \(Run `php emulsify.php -h` for other available options\)
4. Move into your new custom theme directory `cd ../../custom/THEME_NAME/`
5. Install the theme dependencies `yarn` or `npm install`
6. Build theme `yarn build`
7. Enable your theme and its dependencies\*`drush then THEME_NAME -y && drush en components emulsify_twig -y`
8. Set your custom theme to be the default `drush config-set system.theme default THEME_NAME -y`

\* `drush then` is the correct command for Drush versions &gt;= 9. `drush en` is the command to use for Drush versions &lt;= 8.

Troubleshooting Installation: See [Drupal Installation FAQ](../help/styleguide-vs.-pattern-library/drupal-faq.md).

_Note: Once you've created your custom theme, you can remove Emulsify as a dependency of your project. If you'd like to get updates as we push them, solely for educational/best-practice information, feel free to leave it in and receive the updates. Updating Emulsify will not affect your custom theme in any way. You should not however enable both projects - only your custom theme._

_If you do decide to remove the Emulsify Drupal dependency, make sure to move the two requires from its composer.json into your project-root composer.json. \(The components, and emulsify\_twig modules are required for your custom theme to function, and need to be required somewhere in the composer chain.\)_

#### Non-Composer \(e.g. tarball download from drupal.org\)

1. `cd themes/contrib` \(You may need to create this directory\)
2. `composer create-project emulsify-ds/emulsify-drupal --stability dev --no-interaction emulsify`
3. Move into the emulsify theme `cd emulsify`
4. Create your new theme by cloning emulsify `php emulsify.php "THEME NAME"` \(Run `php emulsify.php -h` for other available options\)
5. Move into your cloned theme directory `cd web/themes/custom/THEME_NAME/`
6. Install the theme dependencies `yarn` or `npm install`
7. Build Theme `yarn build`
8. Move the Emulsify Twig module from `themes/custom/emulsify/vendor/drupal/emulsify_twig/` to `modules/contrib/emulsify_twig`. \(You can do this from the Drupal root with `cp -r themes/contrib/emulsify/vendor/drupal/emulsify_twig/ modules/contrib/emulsify_twig`\)
9. Enable Emulsify and its dependencies `drush then THEME_NAME -y && drush en components emulsify_twig -y`
10. Log in and set your custom theme to be the default

Troubleshooting Installation: See [Drupal Installation FAQ](../help/styleguide-vs.-pattern-library/drupal-faq.md).

### Standalone Installation \(prototyping and/or contribution\)

`yarn` or `npm install`

To create a custom clone with your project's name, you can run `php emulsify.php "New Theme" --machine-name new_theme --path none`. This will create a custom version alongside your original \(which can now be deleted\).

