# PopupOptions

Defines the style parameters of the popup.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Popup, PopupButtonOptions, PopupIconOptions, PopupOptions, PopupTextOptions } from '@kit.ArkUI';
```

## onClose

```TypeScript
onClose?: () => void
```

Callback for the popup close button.

By default, the callback for the close button is not set.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttons

```TypeScript
buttons?: [PopupButtonOptions?, PopupButtonOptions?]
```

Buttons of the popup. A maximum of two buttons can be set.

By default, no buttons are displayed.

**Type:** [PopupButtonOptions?, PopupButtonOptions?]

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

Layout direction.

Default value: **Direction.Auto**

**Type:** [Direction](arkts-arkui-direction-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: PopupIconOptions
```

Icon of the popup.

**NOTE:** 

The icon is not displayed when **width** and **height** are set to an invalid value or **0**.

By default, no icon is displayed.

**Type:** [PopupIconOptions](arkts-arkui-arkui-advanced-popup-popupiconoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxWidth

```TypeScript
maxWidth?: Dimension
```

Maximum width of the popup. This API allows the popup to display with a custom width.

**NOTE:** 

1. When using resource references, ensure that the parameter type matches the attribute method type.
2. **maxWidth** accepts numeric values (both floating-point and integer values), such as **&#36;r('app.float.maxWidth')** and **&#36;r('app.integer.maxWidth')**.
3. When the type is Resource, values default to px units if no unit is explicitly specified.

Default value: **400vp**

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: PopupTextOptions
```

Message of the popup.

**NOTE:** 

**fontWeight** is not available for messages.

By default, no message is displayed.

**Type:** [PopupTextOptions](arkts-arkui-arkui-advanced-popup-popuptextoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showClose

```TypeScript
showClose?: boolean | Resource
```

Whether to show the close button.

**true**: Show the close button. **false**: Do not show the close button.

**Resource**: Show the corresponding icon.

Default value: **true**

**Type:** boolean &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: PopupTextOptions
```

Title of the popup.

By default, no title is displayed.

**Type:** [PopupTextOptions](arkts-arkui-arkui-advanced-popup-popuptextoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
