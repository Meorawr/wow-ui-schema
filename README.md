# World of Warcraft UI Schema Definitions

This repository contains the UI XML schema definitions for the World of Warcraft user interface system with a few tweaks that allows them be used for validating XML used by addons.

```xml
<Ui xmlns="http://www.blizzard.com/wow/ui/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.blizzard.com/wow/ui/
https://raw.githubusercontent.com/Meorawr/wow-ui-schema/main/UI.xsd">
</Ui>
```

The UI.xsd file within this repository is aimed at tracking the Retail version of the game. Classic may lack certain functionality, but should be largely similar.

PRs are welcome to provide adjustments for any missing attributes, elements, or intrinsic types that are known to exist. PRs that make the XSDs less strict *may* be rejected however; the XSDs are intentionally a little stricter than what the game actually accepts so as to provide some linting capabilities - for example an empty `<Frames>` element will not validate as having no child frames defined is likely not intentional.

## Modifications

These files may not be precisely identical to the ones shipped by Blizzard in their interface code. Any changes will be listed below.

* No modifications as of build 10.0.2.45969.
