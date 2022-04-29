---
description: >-
  How to use package management in Emulsify to share components and styles
  across multiple projects
---

# Packaging For Multiple Properties

## Sharing Across Multiple Projects

Emulsify allows you to use shared packages across multiple projects. If you are a large organization, this is an excellent way to provide consistency, reuse and save time/money across all properties. The first step is to make some decisions around how you want to organize your organization and projects. Emulsify is not opinionated on this, as organizations will operate in a multitude of ways. We will use one common way as an example to show how it can be set up.&#x20;

One common way to package components and styles is to have one package for components (for a given language) and one package for shared styling. That way, you can share styling across multiple languages and components per language to any relevant project. So, here's an imaginary set of packages:

* Styles (Sass) `global-sass`
* Components (Twig) `global-twig`
* Drupal Project A (Organization)
* Drupal Project B (Property)

The organization's Drupal project (A) and one of the properties of the organization (B) can both share the components and styling across their projects. Once those packages have been set up, installing them in each project using Emulsify Drupal is as follows:

#### Install Packages

```
$ npm i global-sass global-twig
```

#### Styling

In Emulsify Drupal,  you will want to tell Webpack where to compile your new files. Let's start with the styles. We already have a Sass pipeline in place, so importing styling from a package is as simple as putting this into `components/style.scss`:

```
@import '~global-sass/style';
```

Assuming you have a Sass stylesheet named `style.css` that compiles all the styles from your global-sass directory, this import will automatically pull in all of those styles. See our Western University [project](https://github.com/emulsify-ds/westernuni/blob/master/web/themes/custom/western-up/components/style.scss) and [sass project's style.css](https://github.com/emulsify-ds/western-up-scss/blob/master/style.scss) for an example of this.&#x20;

#### Twig/Markup - Storybook

Next, we need to tell Storybook and Drupal where to find the component Twig files. First let's start with Storybook. Storybook uses Webpack to load files, and since our Twig components are Node packages, we need to tell Webpack a few things (see links for Western University examples of how to do this): 1. [How to watch/compile for changes in these files](https://github.com/emulsify-ds/westernuni/blob/master/web/themes/custom/western-up/.storybook/webpack.config.js#L7-L18), 2. [Where to look for these files](https://github.com/emulsify-ds/westernuni/blob/master/web/themes/custom/western-up/.storybook/webpack.config.js#L29-L43), and 3. [To include those in our linting](https://github.com/emulsify-ds/westernuni/blob/master/web/themes/custom/western-up/.storybook/webpack.config.js#L94-L95). Let's walk through a couple of places in this file that may be confusing - see comments in file for clarification:

```javascript
// In the case of using yarn/npm link to link and develop your packages locally, this will help.
config.resolve = { symlinks: false }

// For hot reloading (watch), ignore node_modules except the western-up-scss/twig directories. 
config.watchOptions = {
  ignored: [
    /node_modules\/(?!(western-up-scss|western-up-twig)\/)/,
    /\(?!(western-up-scss|western-up-twig)([\\]+|\/)node_modules/
  ]
}

// Transpile western-up-twig because it includes un-transpiled ES6 code.
config.module.rules[0].exclude = [/node_modules\/(?!(western-up-twig)\/)/];
config.module.rules[0].use[0].loader = require.resolve('babel-loader');
```

#### Organization vs. Property (Global vs. local)

Also, you may have noticed we're only using global components in this project (the atoms/molecules/etc. in the `twig-loader` namespaces are all from our global package). This is helpful when working on a global project like a main organization project. If you need some global and local, like on a property, you can use something like in the [Western School of Arts project](https://github.com/emulsify-ds/westernarts/blob/master/web/themes/custom/western\_arts/.storybook/webpack.config.js#L43-L77). Notice there are now namespaces for both global (e.g., `atoms`) and local (e.g., `wa_atoms`). Now you can use things like this in your Twig:

```
{% raw %}
{% include "@atoms/global/button.twig" %}
{% include "@wa_atoms/local/button.twig %}
{% endraw %}
```

#### Organization Workflow

If you are working on a property like this, you should be good to go. Changes to your local files will hot reload automatically and you will be able to leverage global components/styles. One last note is needed here when you are working on the organization (parent or global) project. You will want to work on the global components and styles within their respective packages while also gaining hot reloading. There are a number of approaches for this, but we have had great success with the simple usage of `npm/yarn link`. We use `yarn` so I will show an example using that. You will clone down your projects separately (`global-sass` ,`global-twig`). In each, you will want to run:

```
yarn link
```

Once you've done that, you need to now link them in your Drupal project. Go to your theme, and run:

```
yarn link global-sass
yarn link global-twig
```

Now, your project will use your local versions of those packages, and with the changes in place above, your Storybook will also hot reload when editing those files!

#### Drupal Twig

One last note on the Drupal side: you will also want your theme's `*.info.yml` file to mimic any namespaces you have in Webpack for Storybook. Here's [the example from Western University](https://github.com/emulsify-ds/westernuni/blob/master/web/themes/custom/western-up/western\_up.info.yml#L46-L58). And of course, for these paths to work, you will have to make sure your continuous integration process produces the `node_modules` directory with your packages.



