---
description: >-
  Install the component library (Storybook/Webpack) for prototyping and/or as a
  Drupal theme
---

# Emulsify Drupal

## Installation

### Requirements

1. [Node (we recommend NVM)](https://github.com/nvm-sh/nvm)
2. [Emulsify CLI](https://docs.emulsify.info/supporting-projects/emulsify-cli) (Not strictly recommended, but all docs will assume its use)

### Picking a version

* **4.x** - Drupal 9.x compatible
* **2.x** - Drupal 8.x compatible (No longer supported)

## Inside a Composer-Based Drupal Instance

The recommended method of installing the Drupal Starter is via the Emulsify CLI. Before you follow the steps below, verify you have the CLI installed `npm install -g @emulsify/cli`.

Here's a [video walkthrough](https://modulesunraveled.wistia.com/medias/7cdtb3k40h) that quickly shows these steps, plus a little more about the CLI

1. In your project root, initialize a theme based on the Drupal starter `emulsify init "My Awesome Theme"` (Using your preferred theme name)
2. Move into your new theme `cd web/themes/custom/my_awesome_theme`
3. Install the Compound system with the default components `emulsify system install compound`
4. Build theme `npm run build`
5. Enable your theme and its dependencies\* \*\*`drush then THEME_NAME -y && drush en components emulsify_twig -y`
6. Set your custom theme as the default `drush config-set system.theme default THEME_NAME -y`
7. See [the FAQ](faq/) for the final step to avoid the `.git can't be found` error

\* `drush then` is the correct command for Drush versions >= 9. `drush en` is the command to use for Drush versions <= 8.\
\*\* if it's not already a part of your project, run `composer require drupal/components drupal/emulsify_twig` to get the required Drupal modules.

## Standalone (for prototyping outside of a Drupal install)

1. Install the starter at your preferred location, and pass a starter\* (like Drupal) `emulsify init "My Awesome Theme" --platform drupal .` (The preceding snippet uses `.` to indicate "the current location")
2. `cd` into that directory and install your system. `emulsify system install --repository https://github.com/emulsify-ds/compound.git --checkout main` for the latest version or `emulsify system install --repository https://github.com/emulsify-ds/compound.git --checkout [branch/tag/commit]` if you would like to use a specific version.
3. Now you can run `npm run build` to simply compile things, or `npm run develop` to start working on the components in isolation.
4. See [the FAQ](faq/) for the final step to avoid the `.git can't be found` error

\* If you don't pass a starter, the CLI will try to figure out your environment, but if it can't it'll fail. By passing one explicitly the CLI skips the "try to figure it out" step, and just uses what you pass.
