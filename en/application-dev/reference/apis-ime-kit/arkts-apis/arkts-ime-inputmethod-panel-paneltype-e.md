# PanelType

```TypeScript
export enum PanelType
```

Enumerates the input method panel types. Defines the panel category and determines whether the panel is a soft keyboard or a status bar. <br> <br>Suggestions for the **PanelType** parameter: <br> <br>- Selection principle: An input method app usually needs to create a **SOFT_KEYBOARD** panel as the main keyboard interface. The **STATUS_BAR** panel is optional and is created only when input method status information needs to be displayed. <br>- Specification limits: A single input method app can create only one panel of the **SOFT_KEYBOARD** type and one panel of the **STATUS_BAR** type. An error will be returned if panels of the same type are created repeatedly. <br>- Usage with related APIs: **PanelType** must be used together with **PanelFlag**. Currently, **PanelFlag** is only used to describe the state of a **SOFT_KEYBOARD** panel; for a **STATUS_BAR** panel, the setting of **PanelFlag** has no actual effect.

**Since:** 11

<!--Device-unnamed-export enum PanelType--><!--Device-unnamed-export enum PanelType-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## SOFT_KEYBOARD

```TypeScript
SOFT_KEYBOARD = 0
```

Soft keyboard.

**Since:** 11

<!--Device-PanelType-SOFT_KEYBOARD = 0--><!--Device-PanelType-SOFT_KEYBOARD = 0-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## STATUS_BAR

```TypeScript
STATUS_BAR
```

Status bar.

**Since:** 11

<!--Device-PanelType-STATUS_BAR--><!--Device-PanelType-STATUS_BAR-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
