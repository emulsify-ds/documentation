---
description: Document your project components with live Storybook examples
---

# Documenting Components

## Documenting Components

By default, the style guide will look for component documentation in your `components` directory, but this path is also configurable via a local `gatsby-config.js` using the `componentLibPath` field. Once you have that set, create an MDX (or Markdown) file alongside any component in that directory to document it and the Gatsby theme will automatically consume them and add them to the reserved `Components` directory (again, see the `example` theme components).

**Displaying Components using Storybook**

If you'd like to display isolated components in your style guide, there is built-in support for [Storybook](https://storybook.js.org). Set your Storybook iframe build path in the `UILibPath` field in `gatsby-config.js` (this can be a local or remote path).

**Displaying Components - MDX**

To show your Storybook components, you can now go to the MDX file where you'd like to display it and use the following MDX shortcode:

`<StorybookComponent id="button--emoji" />`

The `id` for your component is the ID that Storybook uses to identify the component in their iframe, which follows this convention: `COMPONENT_DIRECTORY--COMPONENT_NAME` (you can find this in the Storybook URL of your component). Put in the correct ID and you will see your live component show in your documentation! See the `example` components directory for usage ideas. Also, there is a height prop that you can configure to increase the height of the iframe depending on the nature of the component (e.g., `<StorybookComponent id="button--emoji" height="100px" />`).

**Displaying Components - Component Code**

You can also show component code in your MDX files using the traditional backtick syntax (uses [PRISMJS](https://github.com/PrismJS/prism) and [Prism React Rendered](https://github.com/FormidableLabs/prism-react-renderer)) like so:

````
```html
<div class="cta">
  <h2>This is a call to action</h2>
  <Button>Click here</Button>
</div>
````
