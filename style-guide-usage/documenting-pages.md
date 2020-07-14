---
description: Document anything in the form of a new page.
---

# Documenting Pages

#### Documenting Pages

Writing MDX/Markdown is supported out of the box. By default, if you create a `styleguide` directory in the root of your starter and start adding directories and pages \(you have to at least create index.md and 404.md\), they will automatically populate to the style guide. You can also set this path to something different in the `docPagesPath` field of your local `gatsby-config.js` file. Note that a directory named `Components` behaves differently in that any subpages added won't be indexed. This is because your project component documentation can live anywhere you like including a separate repo/package. So, you will likely want to create that directory, but just leave it empty in your `/styleguide` directory.

