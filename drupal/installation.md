---
description: Instructions for installing Emulsify as your Drupal theme
---

# Drupal Installation

### Requirements

1. [PHP 7.1](http://www.php.net/)
2. [Node \(we recommend NVM\)](https://github.com/creationix/nvm)
3. [Composer](https://getcomposer.org/)

### Composer \(recommended\)

1. Require emulsify in your project `composer require fourkitchens/gatsby-starter-emulsify-drupal`
2. Move into the Emulsify theme `cd web/themes/contrib/gatsby-starter-emulsify-drupal/`
3. Create your new theme by cloning emulsify `php emulsify.php "THEME NAME"` \(Run `php emulsify.php -h` for other available options\)
4. Move into your theme directory `cd web/themes/custom/THEME_NAME/`
5. Install the theme dependencies `yarn` or `npm install`
6. Enable your theme and its dependencies `drush then THEME_NAME -y && drush en components emulsify_twig -y`

Troubleshooting Installation: See [Drupal Installation FAQ](https://github.com/fourkitchens/emulsify/wiki/Installation#drupal-installation-faq).

_Note: Once you've created your custom theme, you can remove Emulsify as a dependency of your project. If you'd like to get updates as we push them, solely for educational/best-practice information, feel free to leave it in and receive the updates. Updating Emulsify will not affect your custom theme in any way._

### Not Composer \(e.g. tarball download from drupal.org\)

1. `cd themes/contrib` \(You may need to create this directory\)
2. `composer create-project fourkitchens/emulsify --stability dev --no-interaction emulsify`
3. Move into the emulsify theme `cd emulsify`
4. Create your new theme by cloning emulsify `php emulsify.php "THEME NAME"` \(Run `php emulsify.php -h` for other available options\)
5. Move into your cloned theme directory `cd web/themes/custom/THEME_NAME/`
6. Install the theme dependencies `yarn` or `npm install`
7. Move the Emulsify Twig module from `themes/custom/emulsify/vendor/drupal/emulsify_twig/` to `modules/contrib/emulsify_twig`. \(You can do this from the Drupal root with `cp -r themes/contrib/emulsify/vendor/drupal/emulsify_twig/ modules/contrib/emulsify_twig`\)
8. Enable Emulsify and its dependencies `drush then THEME_NAME -y && drush en components emulsify_twig -y`

#### Drupal installation FAQ

**Do I need to run `npm install` or `yarn` in the original Emulsify if I use the drush command to create my own custom clone?**

No. Your new custom theme is not a subtheme of Emulsify, and has no references to the original Emulsify contributed theme. You should do all development on the new cloned theme, including running any npm/yarn tasks. Also, do not enable Emulsify **and** your cloned them, only your cloned theme.

**Do I have to use the drush command or can I just use Emulsify as-is?**

You can use Emulsify as your theme!

However, any changes you make to the components will be overwritten if you ever update Emulsify. So, it's recommended that you run the drush command to create a clone, and make your customizations there.

