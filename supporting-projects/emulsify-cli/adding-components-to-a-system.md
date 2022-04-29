# Adding Components to a System

When you're building out your system, you'll need to add new components to your `system.emulsify.json` file in order for the CLI to know they exists, and what to do with them.

The process is really pretty straight-forward. Let's take a look at a few sections in the [system.emulsify.json for Compound](https://github.com/emulsify-ds/compound/blob/main/system.emulsify.json). Below are the "structure" and "variants" sections - which are where your updates are most likely to be made:

```
"structure": [
  {
    "name": "base",
    "description": "Base-level components used in virtually every higher-level component"
  },
  {
    "name": "atoms",
    "description": "Small components commonly used in higher-level components"
  },
  {
    "name": "molecules",
    "description": "Medium-sized components used as building blocks within a larger component"
  },
  {
    "name": "organisms",
    "description": "Large components that compose smaller components into a cohesive UI"
  },
  {
    "name": "templates",
    "description": "Collection of layout templates."
  },
  {
    "name": "pages",
    "description": "Entire pages built using smaller components"
  }
],
"variants": [
  {
    "platform": "drupal",
    "structureImplementations": [
      {
        "name": "base",
        "directory": "./components/00-base"
      },
      {
        "name": "atoms",
        "directory": "./components/01-atoms"
      },
      {
        "name": "molecules",
        "directory": "./components/02-molecules"
      },
      {
        "name": "organisms",
        "directory": "./components/03-organisms"
      },
      {
        "name": "templates",
        "directory": "./components/04-templates"
      },
      {
        "name": "pages",
        "directory": "./components/05-pages"
      }
    ],
    "directories": [
      {
        "name": "template-components",
        "path": "./components/04-templates",
        "destinationPath": "./components/04-templates",
        "description": "Contains default templates and layouts that are required"
      },
      {
        // other directories
      }
    ],
    "files": [
      {
        "name": "style",
        "path": "./components/style.scss",
        "destinationPath": "./components/style.scss",
        "description": "Primary style scss file"
      }
    ],
    "components": [
      {
        "name": "01-colors",
        "structure": "base",
        "required": true
      },
      {
        // other "base" components
      },
      {
        "name": "buttons",
        "structure": "atoms",
        "required": true
      },
      {
        // other "atoms"
      },
      {
        "name": "card",
        "structure": "molecules"
      },
      {
        // other "molecules"
      },
      {
        "name": "grid",
        "structure": "organisms"
      },
      {
        // other "organisms"
      }
    ]
  }
]
```

### Structure

The structure section is where you define the "structure" (or categories) of your components. In this example, the system follows an atomic methodology, so components can be identified as "base", "atoms", "molecules", "organisms", or "pages". Each with a description of the term.

```
"structure": [
  {
    "name": "base",
    "description": "Base-level components used in virtually every higher-level component"
  },
  {
    "name": "atoms",
    "description": "Small components commonly used in higher-level components"
  },
  {
    "name": "molecules",
    "description": "Medium-sized components used as building blocks within a larger component"
  },
  {
    "name": "organisms",
    "description": "Large components that compose smaller components into a cohesive UI"
  },
  {
    "name": "templates",
    "description": "Collection of layout templates."
  },
  {
    "name": "pages",
    "description": "Entire pages built using smaller components"
  }
],
```

### Structure Implementation

In the "variants" array, there's a "drupal" variant, and in that variant, you'll see the "structureImplementations" array. This tells the CLI where, in the directory structure of a project, components of each type should be installed.

So when you run a command like `emulsify component install card` from within your project, this example would install the card (molecule) component at the location `<project>/molecules/02-molecules/card`

```
    "structureImplementations": [
      {
        "name": "base",
        "directory": "./components/00-base"
      },
      {
        "name": "atoms",
        "directory": "./components/01-atoms"
      },
      {
        "name": "molecules",
        "directory": "./components/02-molecules"
      },
      {
        "name": "organisms",
        "directory": "./components/03-organisms"
      },
      {
        "name": "templates",
        "directory": "./components/04-templates"
      },
      {
        "name": "pages",
        "directory": "./components/05-pages"
      }
    ],
```

### Directories

Sometimes, you know that any time you install your system, you'll always want a set of components, files, etc. that all live in a specific directory. This is very common for "base-level" components, styles, mixins, etc. that may not even necessarily qualify as components, but are considered required for every project.

The "directories" array lets you specify one or more directories that should be copied, in whole, any time the system is installed.

In the example below, we're brining over the templates directory which includes all of the "page-level" layouts.

```
    "directories": [
      {
        "name": "template-components",
        "path": "./components/04-templates",
        "destinationPath": "./components/04-templates",
        "description": "Contains default templates and layouts that are required"
      },
      {
        // other directories
      }
    ],
```

### Files

Like directories, there may be specific files that are required that don't necessarily relate to any other grouping of files. The "files" array let's you choose specific files to copy over on install.

This example shows how the main `style.scss` file (that globs component scss files) is copied as a required file.

```
    "files": [
      {
        "name": "style",
        "path": "./components/style.scss",
        "destinationPath": "./components/style.scss",
        "description": "Primary style scss file"
      }
    ],
```

### Components

Finally, individual components can be identified to the system so that projects can install them individually, as needed.

In this example, you'll see that each component has a "structure" key that evaluates to one of the options in the "structureImplementations" section. This tells the CLI where the component should be installed.

Then, each component also requires a "name", which identifies the directory that contains the component files.

_Note: if you have multiple components nested in a common directory like "molecules/cards/news-card" and "molecules/cards/event-card" you can specify them individually by giving them the names "cards/news-card" and "cards/event-card", respectively. And/or you can support installing them both at the same time by creating a "components" entry simply named "cards", and that will install everything in the "cards" directory, recursively._

Finally, you'll notice some of the components additional have `"required": true` . This will tell the CLI to install that component upon initial install as a required component.

```
    "components": [
      {
        "name": "01-colors",
        "structure": "base",
        "required": true
      },
      {
        // other "base" components
      },
      {
        "name": "buttons",
        "structure": "atoms",
        "required": true
      },
      {
        // other "atoms"
      },
      {
        "name": "card",
        "structure": "molecules"
      },
      {
        // other "molecules"
      },
      {
        "name": "grid",
        "structure": "organisms"
      },
      {
        // other "organisms"
      }
    ]
```
