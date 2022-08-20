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

These files are not precisely identical to the ones shipped by Blizzard in their interface code and have the following changes made.

* Added abstract `AnimationRef` element.
  * This is used as a substitution group target instead of `Animation` as non-abstract substitution groups used as references can have issues with completions provided by [some XML language servers](https://github.com/eclipse/lemminx).
* Added `jumpNavigateEnabled` (boolean) to `<Frame>` elements.
  * Behavior is unknown; no usages in UI source code.
  * Has no equivalent Widget script API.
* Added `jumpNavigateStart` (string?) to `<Frame>` elements.
  * Behavior is unknown; no usages in UI source code.
  * Has no equivalent Widget script API.
* Added `noanimalpha` (boolean) attribute to `<Texture>` elements.
  * Behavior is unknown; no usages in UI source code. May prevent alpha changes with `<Alpha>` animations?
  * Has no equivalent Widget script API.
* Added `nolazyload` (boolean) attribute to `<Texture>` elements.
  * (Untested) If set to true, any assigned texture asset will be loaded immediately regardless of object visibility.
  * Has no equivalent Widget script API.
* Added `nounload` (boolean) attribute to `<Texture>` elements.
  * If set to true, the assigned texture asset will not be unloaded when the texture object is no longer visible.
  * Has no equivalent Widget script API.
* Added `stepsPerPage` (float) attribute to `<Slider>` elements.
  * Equivalent to [Slider:SetStepsPerPage](https://wowpedia.fandom.com/wiki/API_Slider_SetStepsPerPage)().
* Changed `LayoutFrameRef` and `FrameRef` element definition to abstract.
  * As with AnimationRef, non-abstract substitution groups used as references can have issues with completions provided by [some XML language servers](https://github.com/eclipse/lemminx).
* Changed `<Origin>` subelement of `<Animation>` elements.
  * Removed from base `<Animation>` element type, as origin is only applicable to some subtypes.
  * Added `<Origin>` to `<Rotation>` and `<Scale>` elements (and derivations thereof).
* Removed `<TitleRegion>` element.
  * This was removed in [Patch 7.1.0](https://wowpedia.fandom.com/wiki/Patch_7.1.0/API_changes).
