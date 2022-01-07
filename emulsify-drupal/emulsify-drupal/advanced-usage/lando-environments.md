---
description: Use Lando to make your development environment portable
---

# Lando Environments

### Why use Lando?

1. Standardizing local environments is simple and effective.
2. Your development environment is portable, so you only need Docker and Lando to develop.
3. Complicated infrastructure can be stood up quickly.
4. Versions of services can be changed with simple line updates.
5. Local environments can be extended with automation easily.
6. You can ensure specific versions of your tools are set, so they do not vary from machine-to-machine.

### Dependencies

* [Docker](https://docs.docker.com/get-docker/)
* [Lando](https://lando.dev/download/)

### Basic Lando stack

1. The `drupal9` recipe can handle most the work for us

    ```yaml
    recipe: drupal9
    ```
2. Both NodeJS and NPM needs to be available at a project level. Using npm the emulsify cli command can also be installed. This and npm can both be made available via Lando tooling.

    ```yaml
    services:
      appserver:
        build_as_root:
           - apt update -y && apt install -y apt-transport-https build-essential unzip
           - curl -sL https://deb.nodesource.com/setup_16.x | bash -
           - apt-get install -y nodejs
           - chown -R www-data /usr/lib/node_modules
           - chown -R www-data /usr/bin
           - npm install -g npm
           - npm install -g @emulsify/cli
    ...
    tooling:
      node:
        service: appserver
      npm:
        service: appserver
      emulsify:
        service: appserver
    ```
3. Emulsify needs port `6006` to be available for StorybookJS and port `32778` to be available for [Hot Reload](./hot-reload-drupal.md).

   By adding proxy address for browsersync.example.lndo.site and storybook.example.lndo.site that point to the ports needed, those applications can be accessible by navigating to the addresses (without the ports, like this: `http://storybook.example.lndo.site`) from outside the container services.

   Since we are using proxies instead of forwarding ports directly, multiple projects can make use of these ports simultaneously.
   ```yaml
   proxy:
      appserver:
         - example.lndo.site
         - browsersync.example.lndo.site:32778
         - storybook.example.lndo.site:6006 
   ```

## Full example

### .lando.yml

This example includes a full setup for Emulsify Drupal with Drupal 9 in a Lando environment.

```yaml
name: example
recipe: drupal9
config:
  php: '7.4'
  via: apache
  webroot: ./web
  database: mysql
services:
  appserver:
    overrides:
      environment:
        DRUSH_OPTIONS_URI: "https://example.lndo.site"
    build:
      - composer install
    build_as_root:
      - apt update -y && apt install -y apt-transport-https build-essential unzip
      - curl -sL https://deb.nodesource.com/setup_16.x | bash -
      - apt-get install -y nodejs
      - chown -R www-data /usr/lib/node_modules
      - chown -R www-data /usr/bin
      - npm install -g npm
      - npm install -g @emulsify/cli
proxy:
  appserver:
    - example.lndo.site
    - browsersync.example.lndo.site:32778
    - storybook.example.lndo.site:6006
tooling:
  drush:
    service: appserver
    cmd: /app/vendor/bin/drush --root=/app/web
  node:
    service: appserver
  npm:
    service: appserver
  emulsify:
    service: appserver
```

### Setup

1. Run `composer create-project drupal/recommended-project my-project` See [Starting a Site Using Drupal Composer Project Templates](https://www.drupal.org/docs/develop/using-composer/starting-a-site-using-drupal-composer-project-templates) for more information on setting up a Drupal project with Composer.
2. Add the above lando.yml file to the project
3. Run `lando start`
4. After it builds you can then run these commands:

* `lando node`
* `lando npm`
* `lando emulsify`
* `lando drush`

1. Follow the [Inside a Composer-Based Drupal Instance](emulsify-drupal/emulsify-drupal#inside-a-composer-based-drupal-instance) steps to complete setting up Emulsify Drupal.
