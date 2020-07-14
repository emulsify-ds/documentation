---
description: 'Powered by Gatsby, MDX and Theme UI'
---

# Style Guide

### Summary

Emulsify Design System contains a fully customizable/theme-able style guide _generator_ built with Gatsby. It reads your documentation and component library and builds a style guide for you. Using MDX you can author custom documentation for your components as well as any other pages for your design system audience.

### Setup

#### Installation

As per Gatsby theme best practices, this repo is a Yarn workspace containing the Gatsby theme as well as an `example` directory to see how to use it in a project.

To install just the Gatsby theme in your project, run:

`npm i gatsby gatsby-theme-emulsify`

#### Setting up Basic Site Information

Create a local `gatsby-config.js` file \(see [the example one](https://github.com/emulsify-ds/gatsby-theme-emulsify-workspace/blob/master/example/gatsby-config.js) for documented options\) and enter your basic site information in the `siteMetadata` fields.

#### Documenting Pages

Writing MDX/Markdown is supported out of the box. By default, if you create a `styleguide` directory in the root of your starter and start adding directories and pages \(you have to at least create index.md and 404.md\), they will automatically populate to the style guide. You can also set this path to something different in the `docPagesPath` field of your local `gatsby-config.js` file. Note that a directory named `Components` behaves differently in that any subpages added won't be indexed. This is because your project component documentation can live anywhere you like including a separate repo/package. So, you will likely want to create that directory, but just leave it empty in your `/styleguide` directory.

#### Documenting Components

By default, the style guide will look for component documentation in your `components` directory, but this path is also configurable via a local `gatsby-config.js` using the `componentLibPath` field. Once you have that set, create an MDX \(or Markdown\) file alongside any component in that directory to document it and the Gatsby theme will automatically consume them and add them to the reserved `Components` directory \(again, see the `example` theme components\).

**Displaying Components using Storybook**

If you'd like to display isolated components in your style guide, there is built-in support for [Storybook](https://storybook.js.org/). Set your Storybook iframe build path in the `UILibPath` field in `gatsby-config.js` \(this can be a local or remote path\).

**Displaying Components - MDX**

To show your Storybook components, you can now go to the MDX file where you'd like to display it and use the following MDX shortcode:

`<StorybookComponent id="button--emoji" />`

The `id` for your component is the ID that Storybook uses to identify the component in their iframe, which follows this convention: `COMPONENT_DIRECTORY--COMPONTENT_NAME` \(you can find this in the Storybook URL of your component\). Put in the correct ID and you will see your live component show in your documentation! See the `example` components directory for usage ideas. Also, there is a height prop that you can configure to increase the height of the iframe depending on the nature of the component \(e.g., `<StorybookComponent id="button--emoji" height="100px" />`\).

**Displaying Components - Component Code**

You can also show component code in your MDX files using the traditional backtick syntax \(uses [PRISMJS](https://github.com/PrismJS/prism) and [Prism React Rendered](https://github.com/FormidableLabs/prism-react-renderer)\) like so:

```text
```html
<div class="cta">
  <h2>This is a call to action</h2>
  <Button>Click here</Button>
</div>
```

**Other MDX shortcodes available:**

`<ContrastWrapper>` : Wraps any contents in this section in a contrasted background wrapper \(opposite of background color\). Usage:

```text
<ContrastWrapper>
Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.
</ContrastWrapper>
```

### Theming

The style guide should match your organization's identity, so it is important that this project is fully customizable.

#### Theme UI

We use [Theme UI](https://theme-ui.com/) to manage the styling of the theme. This API-based method of building allows you to easily update/extend/override via config for quickly changing the look/feel. See their [documentation](https://theme-ui.com/getting-started) for details, and the `example` theme for an example override file \(`example/src/gatsby-plugin-theme-ui/index.js`\). Also, this allows us to quickly implement a dark mode, which is enabled by default \(also to add new modes\). Theme UI alone can be used to a great extent to change the look/feel of your style guide.

#### Gatsby Shadowing

For complete control, Gatsby themes also allow you to fully override components via [shadowing](https://www.gatsbyjs.org/docs/themes/shadowing/). From the layout to specific components, this allows you full customization over the look/feel and even functionality of the project.

### Contributing

#### Workspace Installation

* Clone this workspace and run `yarn` from root to install dependencies
* Also helpful: `yarn develop` at root will actually run `yarn workspace example develop`.



