# Emulsify Design System

![](.gitbook/assets/logo.png)

Emulsify is an open-source tool for creating design systems with reusable components and clear guidelines for teams. Emulsify helps organizations scale their design while reducing cost, streamlining workflows, and improving accessibility.

Emulsify Design System contains multiple packages, which can be used individually to solve small problems or together to solve big ones. See below for some of the popular packages.

## Starters

Starters contain application-specific configuration and files. For example, the Drupal starter contains the `.info.yml` file that defines the Drupal theme's name and other metadata as well as other Drupal-specific files.

### [**Drupal**](https://github.com/emulsify-ds/emulsify-drupal)

Emulsify Drupal is a full prototyping development environment using [Storybook](https://storybook.js.org) as a component library and [Webpack](https://webpack.js.org) as a build engine. It is also a [Drupal](https://www.drupal.org) theme. It can be used as a standalone prototyping tool or inside a Drupal installation.

### [**Wordpress**](https://github.com/emulsify-ds/emulsify-wordpress-theme)

In progress. Not ready for active use.

## Systems

Systems are used to define components and assets. Emulsify projects opt into using systems via the Emulsify CLI. Once a system has been selected for a project, the system mandates how components are organized and how required components/assets are installed. It also gives developers the ability to find and install non-required components.

### [Compound](https://github.com/emulsify-ds/compound)

Compound is the default Emulsify system, and currently includes a variant for Drupal.

## Supporting Projects

### [Emulsify Cli](https://github.com/emulsify-ds/emulsify-cli)

This is a command line interface for Emulsify. With it, you can initialize a project, and identify a "system" (like Compound) for your project. Once initialized you can install individual components from that system into your project as "boiler-plate" code.

### Emulsify Twig

The Emulsify Twig repositories includes two functions "BEM" and "Add Attributes".

The BEM function provides a simple way to programmatically generate BEM classes on elements in your components.

The Add Attributes function provides a way to programmatically add any html attribute (including classes) to elements of your components.

#### [Emulsify Twig Extensions](https://github.com/emulsify-ds/emulsify-twig-extensions)

This repo contains the Javascript version of the BEM and Add Attributes extensions for compatibility with Twig.js (which makes the work in Storybook.)

#### [Emulsify Twig](https://github.com/emulsify-ds/emulsify\_twig)

This repo is a Drupal module that contains the PHP version of the BEM and Add Attributes extensions for support in a Drupal project.

## Style Guide

### [Gatsby Theme Emulsify](https://github.com/emulsify-ds/gatsby-theme-emulsify-workspace)

A fully customizable style guide powered by [GatsbyJS](https://www.gatsbyjs.org). The style guide is a Gatsby theme, and instructions for installation and usage can be found [here](https://github.com/emulsify-ds/gatsby-theme-emulsify-workspace).

## **Example Websites/Repos**

The examples below were created to demonstrate how multiple properties under the same organization could create properties that implement varied languages (Twig and React, in this case) and share things that make sense.

We created a Twig repository for the Drupal sites, a React repository for the Gatsby/React site, and then a separate SCSS repository that is shared between all of them - this means the organizations styles are defined in one place, and each language just needs to ensure their markup meets the organizations expectations. No duplicating styles across languages!

The Western Arts site is also unique because it uses some of the components from the shared repository, but also contains custom components used only by that property! This demonstrates how individual properties can utilize the "organizational" components off-the-shelf, without any custom development, but expand their component library to fulfill unique business needs.

### Websites

#### [**Western University**](https://github.com/emulsify-ds/westernuni)

The Western University site is a Drupal site which implements the Western UP Twig and Western UP SCSS repos off-the-shelf.

#### [**Western Arts**](https://github.com/emulsify-ds/westernarts)

The Western Arts site is a Drupal site with implements some of the Western UP Twig/SCSS components off-the-shelf, but also contains custom components not a part of the Western U "organizational" components.

#### [**Western Law**](https://github.com/emulsify-ds/western-law)

The Western Law site is a Gatsby and React site which uses the Western UP React/SCSS repos for its components.

#### [**Western Identity**](https://github.com/emulsify-ds/western-identity)

The Western Identity site is a Gatsby powered "guidelines" site that contains information on branding, components, and other related documentation.

### **Component Repositories**

#### [**Western UP SCSS**](https://github.com/emulsify-ds/western-up-scss)

The Western UP SCSS repository contains all of the styles used by Western U properties. Since both the Twig and React repos below are configured to consume scss, we only write the styles once, and let each language focus on creating high-quality markup in their respective languages.

#### [**Western UP Twig**](https://github.com/emulsify-ds/western-up-twig)

The Western UP Twig repo contains the Twig components available to all Western U Twig-based properties.

#### [**Western UP React**](https://github.com/emulsify-ds/western-up-react)

The Western UP **React** repo contains the React components available to all Western U React-based properties.

### Contributors

<table>
<tr>
    <td align="center" style="word-wrap: break-word; width: 150.0; height: 150.0">
        <a href=https://github.com/ModulesUnraveled>
            <img src=https://avatars.githubusercontent.com/u/1663810?v=4 width="100;"  style="border-radius:50%;align-items:center;justify-content:center;overflow:hidden;padding-top:10px" alt=Brian Lewis/>
            <br />
            <sub style="font-size:14px"><b>Brian Lewis</b></sub>
        </a>
    </td>
    <td align="center" style="word-wrap: break-word; width: 150.0; height: 150.0">
        <a href=https://github.com/amazingrando>
            <img src=https://avatars.githubusercontent.com/u/409903?v=4 width="100;"  style="border-radius:50%;align-items:center;justify-content:center;overflow:hidden;padding-top:10px" alt=Randy Oest/>
            <br />
            <sub style="font-size:14px"><b>Randy Oest</b></sub>
        </a>
    </td>
    <td align="center" style="word-wrap: break-word; width: 150.0; height: 150.0">
        <a href=https://github.com/cruno91>
            <img src=https://avatars.githubusercontent.com/u/1760366?v=4 width="100;"  style="border-radius:50%;align-items:center;justify-content:center;overflow:hidden;padding-top:10px" alt=Chris Runo/>
            <br />
            <sub style="font-size:14px"><b>Chris Runo</b></sub>
        </a>
    </td>
    <td align="center" style="word-wrap: break-word; width: 150.0; height: 150.0">
        <a href=https://github.com/acouch>
            <img src=https://avatars.githubusercontent.com/u/512243?v=4 width="100;"  style="border-radius:50%;align-items:center;justify-content:center;overflow:hidden;padding-top:10px" alt=Aaron Couch/>
            <br />
            <sub style="font-size:14px"><b>Aaron Couch</b></sub>
        </a>
    </td>
    <td align="center" style="word-wrap: break-word; width: 150.0; height: 150.0">
        <a href=https://github.com/thejimbirch>
            <img src=https://avatars.githubusercontent.com/u/5177009?v=4 width="100;"  style="border-radius:50%;align-items:center;justify-content:center;overflow:hidden;padding-top:10px" alt=Jim Birch/>
            <br />
            <sub style="font-size:14px"><b>Jim Birch</b></sub>
        </a>
    </td>
    <td align="center" style="word-wrap: break-word; width: 150.0; height: 150.0">
        <a href=https://github.com/stephencapellic>
            <img src=https://avatars.githubusercontent.com/u/13124872?v=4 width="100;"  style="border-radius:50%;align-items:center;justify-content:center;overflow:hidden;padding-top:10px" alt=Stephen Musgrave/>
            <br />
            <sub style="font-size:14px"><b>Stephen Musgrave</b></sub>
        </a>
    </td>
</tr>
<tr>
    <td align="center" style="word-wrap: break-word; width: 150.0; height: 150.0">
        <a href=https://github.com/acrollet>
            <img src=https://avatars.githubusercontent.com/u/101649?v=4 width="100;"  style="border-radius:50%;align-items:center;justify-content:center;overflow:hidden;padding-top:10px" alt=Adrian Rollett/>
            <br />
            <sub style="font-size:14px"><b>Adrian Rollett</b></sub>
        </a>
    </td>
    <td align="center" style="word-wrap: break-word; width: 150.0; height: 150.0">
        <a href=https://github.com/hanoii>
            <img src=https://avatars.githubusercontent.com/u/677879?v=4 width="100;"  style="border-radius:50%;align-items:center;justify-content:center;overflow:hidden;padding-top:10px" alt=Ariel Barreiro/>
            <br />
            <sub style="font-size:14px"><b>Ariel Barreiro</b></sub>
        </a>
    </td>
    <td align="center" style="word-wrap: break-word; width: 150.0; height: 150.0">
        <a href=https://github.com/ccjjmartin>
            <img src=https://avatars.githubusercontent.com/u/12279982?v=4 width="100;"  style="border-radius:50%;align-items:center;justify-content:center;overflow:hidden;padding-top:10px" alt=Chris Martin/>
            <br />
            <sub style="font-size:14px"><b>Chris Martin</b></sub>
        </a>
    </td>
    <td align="center" style="word-wrap: break-word; width: 150.0; height: 150.0">
        <a href=https://github.com/jfitzsimmons2>
            <img src=https://avatars.githubusercontent.com/u/1531748?v=4 width="100;"  style="border-radius:50%;align-items:center;justify-content:center;overflow:hidden;padding-top:10px" alt=Joe Fitzsimmons/>
            <br />
            <sub style="font-size:14px"><b>Joe Fitzsimmons</b></sub>
        </a>
    </td>
    <td align="center" style="word-wrap: break-word; width: 150.0; height: 150.0">
        <a href=https://github.com/KurtTrowbridge>
            <img src=https://avatars.githubusercontent.com/u/848721?v=4 width="100;"  style="border-radius:50%;align-items:center;justify-content:center;overflow:hidden;padding-top:10px" alt=Kurt Trowbridge/>
            <br />
            <sub style="font-size:14px"><b>Kurt Trowbridge</b></sub>
        </a>
    </td>
    <td align="center" style="word-wrap: break-word; width: 150.0; height: 150.0">
        <a href=https://github.com/gitbook-bot>
            <img src=https://avatars.githubusercontent.com/u/31919211?v=4 width="100;"  style="border-radius:50%;align-items:center;justify-content:center;overflow:hidden;padding-top:10px" alt=GitBook Bot/>
            <br />
            <sub style="font-size:14px"><b>GitBook Bot</b></sub>
        </a>
    </td>
</tr>
</table>
