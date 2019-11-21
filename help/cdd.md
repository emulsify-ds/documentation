---
description: Helpful information for those new to component-driven design
---

# Component-Driven Design

Component-driven design is a way to systematize and share designs as functional prototypes. Emulsify uses the [Atomic Design](http://bradfrost.com/blog/post/atomic-web-design/) system for organization.

* **Atoms** are the basic building blocks of matter. Applied to web interfaces, atoms are our HTML tags, such as a form label, an input or a button.
* **Molecules** are where things start to get more tangible as we start combining atoms together. Example, a search form comprised of a label, input and submit button.
* **Organisms** allow us to combine molecules into something relatively complex, such as a distinct section of the interface. Example, the header or footer of a site.
* **Templates** consist mostly of groups of organisms stitched together to form pages. It’s here where we start to see the design coming together and start seeing things like layout in action. Example, article node page.
* **Pages** are specific instances of templates. Here, placeholder content is replaced with real representative content to give an accurate depiction of what a user will ultimately see.

We accomplish this by using [Storybook](https://storybook.js.org/) and [Twig](https://twig.symfony.com/). Because both Storybook and Drupal 8 can use Twig for templates, this means that the design components that get built can be used directly by systems such as Drupal! 🎉

### How to use Storybook

Organizing components using the [Atomic Design](http://bradfrost.com/blog/post/atomic-web-design/) system and seeing those components come to life in Storybook is extremely rewarding. It's worth taking a few moments to read the [Storybook documentation](https://storybook.js.org/docs/basics/introduction/), particularly the section on [Writing Stories](https://storybook.js.org/docs/basics/writing-stories/). Below are a few basic principles.

1. **Structure:** All components \(all HTML, CSS, JS\) are housed in the `components` directory.
2. **Global mixins, code:** Code that is global belongs in `components/00-base`. By default, there are files for mixins, variables, breakpoints, layout, and more.
3. **Building a component:** A component is commonly comprised of an HTML file \(using Twig in our case\), a CSS file \(using Sass in our case\) and possibly a Javascript file. `components/01-atoms/links/link/link.twig` is a good example of a simple link component. Please store all code for a component together inside the component's directory.
4. **Storybook Specific:** Storybook allows you to use YAML or JSON files to insert data in your components \(we use YAML by default\). It also allows you to easily add variations for a component. See `components/01-atoms/buttons/buttons.stories.js` for a an example.
5. **Drupal-related:** There are other files in the prototyping system specific to Drupal, which you can ignore while prototyping as they have no effect on building the components in Storybook \(e.g., the `/templates` directory\).

