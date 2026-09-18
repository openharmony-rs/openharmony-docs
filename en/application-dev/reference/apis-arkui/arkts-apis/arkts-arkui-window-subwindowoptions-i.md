# SubWindowOptions

Describes the parameters used for creating a child window.

**Since:** 11

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## decorEnabled

```TypeScript
decorEnabled: boolean
```

Whether decorations are displayed in the child window. **true** if displayed, **false** otherwise.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## isModal

```TypeScript
isModal?: boolean
```

Whether the modal property is enabled for the child window. **true** if enabled, **false** otherwise. The default value is **false**.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## maximizeSupported

```TypeScript
maximizeSupported?: boolean
```

Whether the child window supports maximization. **true** if supported, **false** otherwise. The default value is **false**.

This parameter can be used properly on devices that support the [freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode and are currently in that mode. On devices that do not support the freeform window mode, the API call will neither take effect nor report an error when this parameter is used as an input. On devices that support the freeform window mode but are not currently in that mode, the API call will neither take effect nor report an error when this parameter is used as an input. The setting will take effect after the devices switch to that mode.

**Type:** boolean

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Window.SessionManager

## modalityType

```TypeScript
modalityType?: ModalityType
```

Modality type of the child window. This parameter takes effect only when the modal property is enabled for the child window. **WINDOW_MODALITY** means window-modal, and **APPLICATION_MODALITY** means application-modal. The default value is **WINDOW_MODALITY**.

**Type:** [ModalityType](arkts-arkui-window-modalitytype-e.md)

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Window.SessionManager

## outlineEnabled

```TypeScript
outlineEnabled?: boolean
```

Whether the child window displays an outline. **true** if displayed, **false** otherwise. The default value is **false**.

This parameter can be properly used on 2-in-1 devices. If it is used as an input parameter on other device types, the corresponding API has no effect and does not report errors.

**Type:** boolean

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

## title

```TypeScript
title: string
```

Title of the child window. The title display area should not go past the left side of the three-button area of the system. Any part that goes beyond will show as an ellipsis.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## windowRect

```TypeScript
windowRect?: Rect
```

Rectangle of the child window, and the size of the child window is limited. For details, see [resize()](arkts-arkui-window-window-i.md#resize). If this parameter is not set and [showWindow()](arkts-arkui-window-window-i.md#showwindow) is not called, the default value {left: 0, top: 0, width: 0, height: 0} is used. For details, see [Setting a Child Window of an Application](../../../windowmanager/application-window-stage.md#setting-a-child-window-of-an-application).

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Window.SessionManager

## zLevel

```TypeScript
zLevel?: number
```

Z-level of the child window. This parameter is valid only when the modal property is not enabled for the child window, that is, **isModal** is not set. The value is an integer in the range [-10000, 10000]. Floating-point numbers will be rounded down. The default value is **0**.

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Window.SessionManager

## zLevelAboveParentLoosened

```TypeScript
zLevelAboveParentLoosened?: boolean
```

Indicates whether loose the restriction of sub window z-level above parent.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Window.SessionManager
