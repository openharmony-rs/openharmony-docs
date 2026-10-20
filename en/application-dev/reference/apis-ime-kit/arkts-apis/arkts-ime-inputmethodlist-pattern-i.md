# Pattern

```TypeScript
export interface Pattern
```

Represents the definition of the icon resources for input method mode options, used to configure the visual representation of keyboard modes in the dialog. Available only to the current input method (that is, the preset system input method).

**Since:** 11

<!--Device-unnamed-export interface Pattern--><!--Device-unnamed-export interface Pattern-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { InputMethodListDialog, PatternOptions, Pattern } from '@kit.IMEKit';
```

## icon

```TypeScript
icon: Resource
```

Icon resource for the default (unselected) state of the input method mode option. <br> <br>Usage scenarios: Identify the visual representation of each keyboard mode when it is unselected, allowing users to recognize different mode options in the dialog. <br> <br>Use effect: After setting, this icon is displayed for the mode option in the dialog when it is in the unselected state. <br> <br>Note: A Resource type reference such as **$r('app.media.xxx')** must be used, and the corresponding icon resource file must be added to the project's resource directory. Image resources of the string and PixelMap types are not supported.

**Type:** [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-i.md)

**Since:** 11

<!--Device-Pattern-icon: Resource--><!--Device-Pattern-icon: Resource-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## selectedIcon

```TypeScript
selectedIcon: Resource
```

Icon resource for the selected state of the input method mode option. <br> <br>Usage scenarios: Identify the visual representation of each keyboard mode when it is selected, forming a selected/unselected visual distinction with **icon** to help users recognize the currently selected mode. <br> <br>Use effect: After setting, this icon is displayed for the mode option in the dialog when it is in the selected state. <br> <br>Usage with related parameters: **selectedIcon** should remain visually consistent with **icon**, differing only by the selected state indicator (such as adding highlighting or a border), so users can recognize the currently selected mode. The **icon** and **selectedIcon** in each **Pattern** must be set at the same time; neither can be omitted.

**Type:** [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-i.md)

**Since:** 11

<!--Device-Pattern-selectedIcon: Resource--><!--Device-Pattern-selectedIcon: Resource-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
