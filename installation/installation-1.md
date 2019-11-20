---
description: 'Instructions from https://github.com/emulsify-ds/gatsby-theme-emulsify'
---

# Styleguide Installation \(Gatsby\)

### Quickstart

Using a Gatsby Starter is the fastest way to get up-and-running.

* [Twig Starter](https://github.com/fourkitchens/gatsby-starter-emulsify-twig)
* React Starter \(coming soon\)
* [Drupal Starter](https://github.com/fourkitchens/gatsby-starter-emulsify-drupal) \(Drupal 8 theme including Storybook and Webpack build\)

### **Manual Installation**

* Create a directory for your design system.

```text
mkdir my-design-system
cd my-design-system
```

* `yarn init`
* `yarn add react react-dom gatsby gatsby-theme-emulsify`
* Create a `gatsby-config.js`

```text
module.exports = {
  plugins: [
    {
      resolve: "gatsby-theme-emulsify",
      options: {
        componentLibPath: 'components', // Where your component library lives
        docPagesPath: 'styleguide', // Where your custom styleguide pages live
        basePath: __dirname, // Needed to make above paths relative to your project
        designSystems: [
          {
            name: "Acme Corporation", // Other design system you may want to link to in a parent/child situation
            link: "https://acme-design-system.netlify.com"
          },
        ],
        // Site Metadata for style guide
        siteMetadata: {
          title: "B&E Security",
          description: "Your favorite security company",
          author: "B&E Security",
        }
      },
    },
  ],
}
```

* In your project root, create a `components` directory and add a directory for each component.
* Add your component and an adjacent `.yml` file that will be used to populate the data needed to render the component.
* In your project root, create a `styleguide` directory and inside it create a `Components` directory with an empty `.md` file in it. This is needed for placing links to each component in the sidebar.

```text
---
title: "Components"
description: "This is the components section"
publishToStyleGuide: true
---
```

* You're now ready to start documenting your component library!

