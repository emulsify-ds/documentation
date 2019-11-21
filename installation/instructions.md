---
description: Instructions for installing Emulsify as your Drupal theme
---

# Installation Instructions

1. [Drupal Installation](https://fourkitchens.gitbook.io/emulsify-design-system/installation/drupal-installation#drupal-installation)
2. [Standalone Installation](https://fourkitchens.gitbook.io/emulsify-design-system/installation/drupal-installation#standalone-installation-prototyping-and-or-contribution)

### Drupal Installation

#### Requirements

1. [PHP 7.1](http://www.php.net/)
2. [Node \(we recommend NVM\)](https://github.com/creationix/nvm)
3. [Composer](https://getcomposer.org/)

#### Composer \(recommended\)

1. Require emulsify in your project `composer require emulsify-ds/emulsify-design-system`
2. Move into the contrib Emulsify theme directory`cd web/themes/contrib/emulsify/`
3. Create your new custom theme by cloning emulsify `php emulsify.php "THEME NAME"` \(Run `php emulsify.php -h` for other available options\)
4. Move into your new custom theme directory `cd web/themes/custom/THEME_NAME/`
5. Install the theme dependencies `yarn` or `npm install`
6. Enable your theme and its dependencies `drush then THEME_NAME -y && drush en components emulsify_twig -y`

Troubleshooting Installation: See [Drupal Installation FAQ](https://fourkitchens.gitbook.io/emulsify-design-system/help/drupal-faq).

_Note: Once you've created your custom theme, you can remove Emulsify as a dependency of your project. If you'd like to get updates as we push them, solely for educational/best-practice information, feel free to leave it in and receive the updates. Updating Emulsify will not affect your custom theme in any way. You should not however enable both projects - only your custom theme._

#### Non-Composer \(e.g. tarball download from drupal.org\)

1. `cd themes/contrib` \(You may need to create this directory\)
2. `composer create-project emulsify-ds/emulsify-design-system --stability dev --no-interaction emulsify`
3. Move into the emulsify theme `cd emulsify`
4. Create your new theme by cloning emulsify `php emulsify.php "THEME NAME"` \(Run `php emulsify.php -h` for other available options\)
5. Move into your cloned theme directory `cd web/themes/custom/THEME_NAME/`
6. Install the theme dependencies `yarn` or `npm install`
7. Move the Emulsify Twig module from `themes/custom/emulsify/vendor/drupal/emulsify_twig/` to `modules/contrib/emulsify_twig`. \(You can do this from the Drupal root with `cp -r themes/contrib/emulsify/vendor/drupal/emulsify_twig/ modules/contrib/emulsify_twig`\)
8. Enable Emulsify and its dependencies `drush then THEME_NAME -y && drush en components emulsify_twig -y`

See [Drupal FAQ](https://fourkitchens.gitbook.io/emulsify-design-system/help/drupal-faq) for details

### Standalone Installation \(prototyping and/or contribution\)

`yarn` or `npm install`

