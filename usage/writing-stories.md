# Writing Stories

Writing components is still the same as it has always been in Emulsify \(Create your component Twig/React, .scss and/or .js files. However, for Storybook you will now want to create "stories" to add your components to the Storybook UI. See below for some examples:

### Simple annotated example

\(From `components/01-atoms/buttons/buttons.stories.js` with added comments\)

```text
// We use the React version of Storybook (more on that later)
import React from 'react';

// Import your Twig file
import button from './twig/button.twig';

// Import your Data file
import buttonData from './twig/button.yml';

/**
 * Create your Storybook Definition and components
 */

// This is the definition and defines the navigation in Storybook
export default { title: 'Atoms/Button' }; 

// Will create a story called "Twig" in the above navigation
// using your button component and buttonData.
export const twig = () => <div dangerouslySetInnerHTML={{ __html: button(buttonData) }} />;
```

### Sharing Data Between Components

\(From `components/02-molecules/card/cards.stories.js` with added comments\)

```text
import React from 'react';

import card from './card.twig';

// Original Data for all cards
import cardData from './card.yml';
// Only data specific to the 'bg' card variation
import cardBgData from './card-bg.yml';

export default { title: 'Molecules/Cards' };

export const cardExample = () => <div dangerouslySetInnerHTML={{ __html: card(cardData) }} />;
// Below contains all data including 'bg' variation data.
export const cardWithBackground = () => (
  <div dangerouslySetInnerHTML={{ __html: card({ ...cardData, ...cardBgData }) }} />);

```

### Using JavaScript

\(From `components/02-molecules/tabs/tabs.stories.js` with added comments\)

```text
import React from 'react';

import tabs from './tabs.twig';

import tabData from './tabs.yml';

// Import your JavaScript file as you normally would in Node.js
// Assuming you use Drupal behaviors it will automatically be loaded.
import './tabs';

export default { title: 'Molecules/Tabs' };

// Apply the Storybook hook with your JS function inside of it
// before returning your component.
export const JSTabs = () => (
  <div dangerouslySetInnerHTML={{ __html: tabs(tabData) }} />;
);

```

### React and Twig Side-by-side

\(From `components/01-atoms/buttons/buttons.stories.js` with added comments\)

```text
import React from 'react';

import button from './twig/button.twig';

import buttonData from './twig/button.yml';

// Import React button
import Button from './react/Button.component';

// Add component to your Storybook definition
export default {
  component: Button,
  title: 'Atoms/Button',
};

export const twig = () => <div dangerouslySetInnerHTML={{ __html: button(buttonData) }} />;

// Export React button
export const react = () => <Button>React Button</Button>;
```

### Using Storybook "Controls"

Storybook [Controls](https://storybook.js.org/docs/react/essentials/controls) offers the ability to tweak stories via the Storybook UI for demoing different variations, etc. Here is a simple example below:

```text
import React from 'react';

import button from './button.twig';

import buttonData from './button.yml';

/**
 * Storybook Definition.
 */
export default {
  title: 'Atoms/Button',
  argTypes: {
    color: {
      control: {
        type: 'select',
        name: 'Color',
        options: ['red', 'yellow', 'blue'],
      },
    },
  },
};

export const Button = (args) => (
  <div
    dangerouslySetInnerHTML={{
      __html: button({
        ...buttonData,
        button_modifiers: [
          // By default, it contains an array of all colors.
          Array.isArray(args.color) ? 'red' : args.color,
        ],
      }),
    }}
  />
);

Button.args = {
  color: ['red', 'yellow', 'blue'],
};

```

