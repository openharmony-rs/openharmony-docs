# PopupOptions

```TypeScript
export interface PopupOptions
```

Defines the style parameters of the popup.

**Since:** 11

<!--Device-unnamed-export interface PopupOptions--><!--Device-unnamed-export interface PopupOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Popup, PopupButtonOptions, PopupIconOptions, PopupOptions, PopupTextOptions } from '@kit.ArkUI';
```

## onClose

```TypeScript
onClose?: () => void
```

Popup close button callback.

No close button callback is set by default.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupOptions-onClose?: () => void--><!--Device-PopupOptions-onClose?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttons

```TypeScript
buttons?: [PopupButtonOptions?, PopupButtonOptions?]
```

Popup action buttons. A maximum of two buttons can be set.

Hidden by default.

**Type:** [PopupButtonOptions?, PopupButtonOptions?]

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupOptions-buttons?: [PopupButtonOptions?, PopupButtonOptions?]--><!--Device-PopupOptions-buttons?: [PopupButtonOptions?, PopupButtonOptions?]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

Layout direction of the Popup content. For available enum values, see Direction.

Default value: **Direction.Auto**

**Type:** [Direction](arkts-arkui-direction-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupOptions-direction?: Direction--><!--Device-PopupOptions-direction?: Direction-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: PopupIconOptions
```

Popup icon.

**NOTE:** 

The icon is not displayed when width and height are set to abnormal values or 0.

Hidden by default.

**Type:** [PopupIconOptions](arkts-arkui-arkui-advanced-popup-popupiconoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupOptions-icon?: PopupIconOptions--><!--Device-PopupOptions-icon?: PopupIconOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxWidth

```TypeScript
maxWidth?: Dimension
```

Maximum width of the Popup. Custom width display is supported.

**NOTE:** 

1. When a referenced resource type is used, its parameter type must be consistent with the type of the **maxWidth** attribute itself.
2. **maxWidth** is of the [Dimension](arkts-arkui-dimension-t.md) type, which supports numeric and percentage string types. Numeric types support float and integer, for example, `$r('app.float.maxWidth')` and `$r('app.integer.maxWidth')`; percentage strings, for example, '50%'.
3. When the type is Resource, if no unit is set, the default unit is px.

Default value: **400vp**

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-PopupOptions-maxWidth?: Dimension--><!--Device-PopupOptions-maxWidth?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: PopupTextOptions
```

Popup content text.

**NOTE:** 

**fontWeight** setting is not supported for message.

Hidden by default.

**Type:** [PopupTextOptions](arkts-arkui-arkui-advanced-popup-popuptextoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupOptions-message: PopupTextOptions--><!--Device-PopupOptions-message: PopupTextOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showClose

```TypeScript
showClose?: boolean | Resource
```

Popup close button.

The value **true** indicates to show the close button, and **false** indicates to hide the close button.

**Resource**: displays the corresponding icon.

Default value: **true**

**Type:** boolean &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupOptions-showClose?: boolean | Resource--><!--Device-PopupOptions-showClose?: boolean | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: PopupTextOptions
```

Popup title text.

Hidden by default.

**Type:** [PopupTextOptions](arkts-arkui-arkui-advanced-popup-popuptextoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupOptions-title?: PopupTextOptions--><!--Device-PopupOptions-title?: PopupTextOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
