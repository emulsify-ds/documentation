# Emulsify CLI Usage



This project is a command line interface for working with Emulsify. It has a few primary responsibilities:

* Make initializing Emulsify projects very simple.
* Allow developers to select an Emulsify system (such as [Compound](https://github.com/emulsify-ds/compound)).
* Give developers the ability to pull in components from the system they're using, when/if they need them.

### Projects, Systems and Variants

You will see the terms "Projects", "Systems" and "Variants" used throughout this documentation, so it's important for you to understand what they mean.

* **Project**: an implementation of an Emulsify starter, such as [emulsify-drupal](https://github.com/emulsify-ds/emulsify-drupal).
* **System**: a design system that defines components, and assets. Emulsify projects opt into using systems using cli commands. Once a system has been selected for a project, the system will mandate how components are organized and how required components/assets are installed. It also gives developers the ability to find and install non-required components.
* **Variant**: a system might have a Drupal variant, a WordPress variant, and a React variant. The system is the same (imagine Material-UI is a system), but each variant may define different types of components, or have different organization patterns that are compatible with different platforms. Systems may have as many variants as they want.

### Using the CLI

#### Init

#### The cli exposes an init command that allows developers to easily create an Emulsify project.

When the init command is run, it will attempt to detect the platform you're using, and use that to choose a starter (such as [emulsify-drupal](https://github.com/emulsify-ds/emulsify-drupal)). However, you can use the command options to specify any platform, starter, and starter version/branch/tag. If the cli cannot determine the platform you're using, it will instruct you to provide those details yourself.

```
emulsify init --help
Usage: emulsify init [options] <name> [path]

Initialize an Emulsify project

Arguments:
  name                                  Name of the Emulsify project you are initializing. This should be a proper name, such as "Carmen Sandiego".
  path                                  Path to the folder in which you would like to to create your Emulsify project. For example, "./themes" will
                                        result in the Emulsify project being placed in ./themes/{name}

Options:
  -m --machineName <machineName>        Machine-friendly name of the project you are initializing. If not provided, this will be automatically
                                        generated.
  -s --starter <repository>             Git repository of the Emulsify starter you would like to use, such as the Emulsify Drupal theme:
                                        https://github.com/emulsify-ds/emulsify-drupal.git
  -c --checkout <commit/branch/tag>     Commit, branch or tag of the base repository that should be checked out
  -p --platform <drupal/wordpress/etc>  Name of the platform Emulsify is being within. In some cases, Emulsify is able to automatically detect this. If
                                        it is not, Emulsify will prompt you to specify.
  -h, --help                            display help for command
```

Example usage:

```
cd ~/projects/my-drupal-codebase
emulsify init "Theme Name"

# If you are not relying on the cli to detect the platform, and use a starter:
emulsify init "Theme Name" ./web/themes/custom/theme-name --starter https://github.com/emulsify-ds/emulsify-drupal.git --checkout 2.x --platform drupal
```

#### System

Once you have initialized a project, you can use system commands available within the cli to list the out-of-the-box systems, and install a system into your current project.

```
emulsify system --help
Usage: emulsify system [options] [command]

Parent command that contains sub-commands pertaining to systems

Options:
  -h, --help                display help for command

Commands:
  list|ls                   Lists all of the available systems that Emulsify supports out-of-the-box
  install [options] [name]  Install a system within an Emulsify project. You must specify either the name of an out-of-the-box system (such as
                            compound), or a link to a git repository containing the system you want to install
  help [command]            display help for command
```

The `emulsify system list|ls` command lists all of the out-of-the-box systems Emulsify supports at the moment.

Example usage:

```
emulsify system list
compound - https://github.com/emulsify-ds/compound.git
```

The `emulsify system install` command, when run within an Emulsify project, will install a system within the given project. You can pass the name of an out-of-the-box system, like `compound`, or you can pass a repository, and commit/branch/tag of any system you'd like to use.

```
emulsify system install --help
Usage: emulsify system install [options] [name]

Install a system within an Emulsify project. You must specify either the name of an out-of-the-box system (such as compound), or a link to a git repository containing the system you want to install

Arguments:
  name                               Name of the out-of-the-box system you would like to install

Options:
  -r --repository <repository>       Git repository containing the system you would like to install
  -c --checkout <commit/branch/tag>  Commit, branch or tag of the base repository that should be checked out. MUST be provided if you are passing along
                                     a repository (-r or --repository). Tags or commit hashes are strongly preferable, because you want to ensure that
                                     you are using the same version of the system every time you install components, etc
  -a --all                           Use this to install all available components within the specified system. Without this flag, only the required system components will be installed.
  -h, --help                         display help for command
```

Example usage:

```
cd ~/projects/my-drupal-codebase/web/themes/custom/my-theme
emulsify system install compound
 > Successfully installed the compound system using the drupal variant.


# If you are pasing in your own repo/checkout
emulsify system install --repository https://github.com/your-org/your-custom-system.git --checkout 3.x
```

#### Components

In your project, once you have selected a system, you may use the `components` commands within the cli to find, and install components that are available within your system.

```
emulsify component --help
Usage: emulsify component [options] [command]

Parent command that contains sub-commands pertaining to components

Options:
  -h, --help        display help for command

Commands:
  list|ls           Lists all of the components that are available for installation within your project based on the system and variant you selected
  install|i [name] [options] Install a component from within the current project's system and variant
  help [command]    display help for command
```

**Listing components**

The `emulsify component list|ls` will return a list of components available within the system you selected for your project.

Example usage:

```
cd ~/projects/my-drupal-codebase/web/themes/custom/my-theme
emulsify component list

base -> 01-colors
base -> 02-motion
base -> 03-site
atoms -> buttons
atoms -> forms
atoms -> images
atoms -> links
atoms -> lists
atoms -> tables
atoms -> text
atoms -> video
molecules -> card
molecules -> cta
molecules -> menus
molecules -> pager
molecules -> status
molecules -> tabs
organisms -> grid
organisms -> site
templates -> placeholder
pages -> content-types
pages -> landing-pages
```

**Installing components**

Once you've found a component you want to install, you can use the `emulsify component install` command to fetch it into your project.

Example usage:

```
cd ~/projects/my-drupal-codebase/web/themes/custom/my-theme
emulsify component install card
 > Success! The card component has been added to your project.
```

**Force installing components**

If you attempt to install a component that already exists within your project, you the installation process will throw an error. However, if you wish to overwrite the existing component, pass the `--force` flag.

Example usage:

```
emulsify component install card
 > Error: The component "card" already exists, and force was not passed (--force).

emulsify component install card --force
 > Success! The card component has been added to your project.
```

**Installing all available components**

If you would like to simply install all components available within the system you've selected, use the `--all` flag.

Example usage:

```
emulsify component install --all
 > Success! The 01-colors component has been added to your project.
 > ...
```

That's pretty much it. Have fun, and please feel free to open issues if you discover a bug, or have an improvement to suggest!
