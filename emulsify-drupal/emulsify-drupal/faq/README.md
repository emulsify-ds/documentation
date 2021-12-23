---
description: Frequently asked questions about Emulsify Drupal
---

# FAQ

## .git can't be found

Are you getting this error?

```
> emulsify-drupal@1.0.0 prepare
> husky install

.git can't be found (see https://git.io/Jc3F9)
```

If so, remove the script `"prepare": "husky install",` from your package.json, and you should be good to go.

This is a known issue. Since `emulsify-drupal` is a standalone project, it has its own linting setup, and husky is the tool that runs linting/formatting scripts automatically. However, once you install the Drupal starter into a project, you don't want a git submodule, so we delete the `.git` directory that comes with `emulsify-drupal` ... which causes husky to throw a fit.

We're working on a long-term solution, and if you have any ideas, please share in [the related issue queue!](https://github.com/emulsify-ds/emulsify-cli/issues/82)
