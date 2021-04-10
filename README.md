# World of Warcraft UI Schema Definitions

This repository contains the UI XML schema definitions for the World of Warcraft user interface system with a few tweaks that allows them be used for validating XML used by addons.

Each client branch is represented as a seprate file at the root of this repository and can be referenced through the following `<Ui>` tag at the root of an addons' XML document.

```xml
<Ui xmlns="http://www.blizzard.com/wow/ui/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.blizzard.com/wow/ui/ https://raw.githubusercontent.com/Meorawr/wow-ui-schema/main/UI-Retail.xsd">

    <!-- Your stuff goes here! -->

</Ui>
```

## Modifications

These files are not precisely identical to the ones shipped by Blizzard in their interface code and have the following changes made.

* Removed an `xs:assert` node from the ColorType definition as this caused validation issues.
* Added `ScopedModifier` element support to the root `Ui` tag.
* Added the following intrinsic frame types:
  * ContainedAlertFrame
  * ItemButton (Retail-only)
  * DropDownToggleButton (Retail-only)
  * EventButton (Retail-only)
