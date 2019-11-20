---
description: >-
  Instructions from
  https://github.com/emulsify-ds/gatsby-starter-emulsify-drupal#-develop
---

# Standalone Usage

### Storybook

Develop: `yarn develop` or `npm develop`

This combines 3 tasks:

1. `yarn webpack` \(CSS compiling/minifying/linting, SVG Sprite generation\)
2. `yarn babel` \(ES6 transpiling, minification\)
3. `yarn storybook` \(Storybook dev watch task\)

**Deploy Storybook**

`yarn deploy-storybook`

#### Generate Design System

`yarn styleguide` or `npm styleguide`

#### Build Tasks

Styleguide: `build-styleguide` Storybook: `build-storybook` Babel: `build-babel` Webpack: `build-webpack`

#### Linting

`yarn lint`

