---
description: Create documentation in the form of pages.
---

# Documenting Pages

### Documenting Pages

Writing MDX/Markdown is supported out of the box. By default, if you create a `styleguide` directory in the root of your starter and start adding directories and pages \(you have to at least create index.md and 404.md\), they will automatically populate to the style guide. You can also set this path to something different in the `docPagesPath` field of your local `gatsby-config.js` file. Note that a directory named `Components` behaves differently in that any subpages added won't be indexed. This is because your project component documentation can live anywhere you like including a separate repo/package. So, you will likely want to create that directory, but just leave it empty in your `/styleguide` directory.

#### Images and Files

You can link to images and files as well. See below for syntax:

Image Markdown:

```text
![City](./city.jpg)
```

File Markdown:

```text
[Download the SVG here](logo.svg)[Download the PDF here](blank.pdf)
```

#### Linking Style Guides Together or linking to other systems

There is a `designSystems` configuration in `gatsby-config.js` that allows for links to other systems. This will open up in an offscreen menu by default. See below for an example:

```text
designSystems: [
  {
    name: "Style Guide 1",
    link: "http://emulsify.info"
  },
  {
    name: "Style Guide 2",
    link: "http://fourkitchens.com"
  }
],
```

