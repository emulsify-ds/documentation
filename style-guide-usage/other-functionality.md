# Other Functionality

**Other MDX shortcodes available:**

`<ContrastWrapper>` : Wraps any contents in this section in a contrasted background wrapper \(opposite of background color\). Usage:

```text
<ContrastWrapper>
Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.
</ContrastWrapper>
```

`<TabLinks>`: Wrap a set of links as "tabs" that will automatically open in new windows - ideal for creating tabs for code languages. Usage:

```text
<TabLinks defaultTab="React">
  <a href="http://example.com/vanillajs" target="_blank">Vanilla JS</a>
  <a href="http://example.com/angular" target="_blank">Angular</a>
</TabLinks>
```

### Theming

The style guide should match your organization's identity, so it is important that this project is fully customizable.

#### Theme UI

We use [Theme UI](https://theme-ui.com/) to manage the styling of the theme. This API-based method of building allows you to easily update/extend/override via config for quickly changing the look/feel. See their [documentation](https://theme-ui.com/getting-started) for details, and the `example` theme for an example override file \(`example/src/gatsby-plugin-theme-ui/index.js`\). Also, this allows us to quickly implement a dark mode, which is enabled by default \(also to add new modes\). Theme UI alone can be used to a great extent to change the look/feel of your style guide.

#### Gatsby Shadowing

For complete control, Gatsby themes also allow you to fully override components via [shadowing](https://www.gatsbyjs.org/docs/themes/shadowing/). From the layout to specific components, this allows you full customization over the look/feel and even functionality of the project.

