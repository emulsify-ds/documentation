---
description: Compound is the default Emulsify system.
---

# Compound

## Components

The components in [Compound](https://github.com/emulsify-ds/compound) are intentionally bland and sparsely styled. These components are intended to be used as "boiler-plate" code that can easily be customized to fit a specific project's needs. PRs to add new components are always welcome, as long as they are coded to follow that methodology.

## Live Component Library

You can view the current state of the [Compound component library](https://emulsify-ds.github.io/compound/) at any time. It is automatically updated and published any time something is merged into the main branch.

If you'd like to automate your component library deployment, here's the [GitHub Workflow file](https://github.com/emulsify-ds/compound/blob/main/.github/workflows/deploy-component-library.yml) we're using.

## Visual Regression Testing

Visual regression testing is also performed against Compound any time a PR is changed from "Draft" to "Ready for Review". You can see the results of that [in Percy](https://percy.io/333ca28a/Compound).

If you'd like to automate visual regression testing for your component library, [this GitHub Workflow config](https://github.com/emulsify-ds/compound/blob/main/.github/workflows/tests.yml#L6-L34) may help point you in the right direction.
