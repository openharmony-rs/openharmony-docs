# PanelInfo

```TypeScript
export interface PanelInfo
```

Attribute information of the input method panel. It is used to describe the type and display state of the input method panel and is passed as a configuration parameter when you create an input method panel. <br> <br>- Meaning/Function: Defines the type (soft keyboard or status bar) and display state (fixed, floating, or candidate state) of the input method panel, and serves as the configuration parameter of **InputMethodAbility.createPanel()** to determine the form of the created panel. <br>- Usage scenarios: Used when an input method app needs to create an input method panel through **createPanel()** and specify its type and state. Examples include creating a default fixed-state soft keyboard panel, creating a freely draggable floating-state soft keyboard panel, and creating a candidate-state panel that displays candidate words in an independent window. <br>- Use effect: The set **type** and **flag** determine the type and display form of the created panel. After the settings are complete, the system creates the panel according to the specified type and state. The visibility behavior of the panel is determined by **flag**. The fixed state and floating state are controlled by the system, while the candidate state is controlled by you. <br> <br>Suggestions for the **PanelInfo** parameter: <br> <br>- **type** parameter: <br>- Value range: [PanelType](arkts-ime-inputmethod-panel-paneltype-e.md) enum values, that is, **SOFT_KEYBOARD** (**0**) or **STATUS_BAR** (**1**). <br>- Default value: **SOFT_KEYBOARD** (**0**). A soft keyboard panel is created by default if this parameter is not specified. <br>- Usage with related parameters: The **flag** property is currently used only to describe the state of a **SOFT_KEYBOARD** panel. Setting **flag** takes no effect when **type** is set to **STATUS_BAR**. <br>- **flag** parameter: <br>- Value range: [PanelFlag](arkts-ime-inputmethod-panel-panelflag-e.md) enum values, that is, **FLAG_FIXED** (**0**), **FLAG_FLOATING** (**1**), or **FLAG_CANDIDATE** (**2**). <br>- Default value: **FLAG_FIXED** (**0**). A fixed‑state panel is used by default if this parameter is not specified. <br>- Usage scenarios: Select different **flag** values for different scenarios: <br>- **FLAG_FIXED** (**0**): Applies to most default input scenarios. The panel is anchored at the bottom of the screen, and its visibility is managed by the system. <br>- **FLAG_FLOATING** (**1**): Applies to scenarios where the panel position needs to be adjusted freely (for example, landscape‑mode input or multi‑window environments). The panel is draggable, and its visibility is managed by the system. <br>- **FLAG_CANDIDATE** (**2**): Applies to scenarios that require candidate words to be displayed independently. The panel serves as a candidate word window, and the timing for showing and hiding it shall be managed by you. <br>- Use effect: <br>- When **FLAG_FIXED** is set: The panel is anchored at the bottom of the screen, and the system manages its visibility behaviors. <br>- When **FLAG_FLOATING** is set: The panel acts as a floating window that can be dragged freely, and the system manages its visibility behaviors. <br>- When **FLAG_CANDIDATE** is set: The panel acts as a candidate word window. The system does not actively manage its visibility. You must control the timing for showing and hiding the panel by calling **Panel.show()** and **Panel.hide()**. <br>- Specification limits: This parameter applies only to **SOFT_KEYBOARD** panels. Setting **flag** for a **STATUS_BAR** panel takes no effect. <br>- Precautions: When **FLAG_CANDIDATE** is selected, you must manage the visibility of the candidate word panel. This includes calling **Panel.show()** to display the panel when the user starts input, and calling **Panel.hide()** to hide the panel after input ends or the user selects a candidate word.

**Since:** 11

<!--Device-unnamed-export interface PanelInfo--><!--Device-unnamed-export interface PanelInfo-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { PanelInfo, PanelType, PanelFlag } from '@kit.IMEKit';
```

## flag

```TypeScript
flag?: PanelFlag
```

State type of the input method panel. <br> <br>- The default value is `FLAG_FIXED`(0), indicating a fixed state panel type. <br>- Currently used only to describe the state of a soft keyboard type panel. Setting it for a `STATUS_BAR` type panel has no actual effect. <br>- The show/hide behavior of the panel differs under different state types: `FLAG_FIXED` and `FLAG_FLOATING` are controlled by the system, while `FLAG_CANDIDATE` is controlled by you.

**Type:** [PanelFlag](arkts-ime-inputmethod-panel-panelflag-e.md)

**Default:** FLG_FIXED

**Since:** 11

<!--Device-PanelInfo-flag?: PanelFlag--><!--Device-PanelInfo-flag?: PanelFlag-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## type

```TypeScript
type: PanelType
```

Type of the input method panel. Determines whether the panel is a soft keyboard or a status bar. When the parameter is not specified, the default value is `SOFT_KEYBOARD`(0).

**Type:** [PanelType](arkts-ime-inputmethod-panel-paneltype-e.md)

**Since:** 11

<!--Device-PanelInfo-type: PanelType--><!--Device-PanelInfo-type: PanelType-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
