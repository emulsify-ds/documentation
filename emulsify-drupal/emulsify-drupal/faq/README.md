---
description: Frequently asked questions about Emulsify Drupal
---

# FAQ

### Do I need to run `npm install` in the original Emulsify if I create my own custom clone?

No. Your new custom theme is not a subtheme of Emulsify and has no references to the original Emulsify contributed theme. You should do all development on the new cloned theme, including running any npm/yarn tasks. Also, do not enable Emulsify **and** your cloned them, only your cloned theme.

### Do I have to use the php command or can I just use Emulsify as-is?

You can use Emulsify as your theme. However, any changes you make to the components will be overwritten if you ever update Emulsify. So, it's recommended that you run the php command to create a clone, and make your customizations there.
