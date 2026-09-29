# PopupV2InitInfo

```TypeScript
export interface PopupV2InitInfo
```

Defines the specific style parameters of **PopupV2**.

**Since:** 26.0.0

<!--Device-unnamed-export interface PopupV2InitInfo--><!--Device-unnamed-export interface PopupV2InitInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { PopupV2, PopupV2InitInfo, PopupV2Button } from '@kit.ArkUI';
```

## buttons

```TypeScript
buttons?: [PopupV2Button?, PopupV2Button?]
```

PopupV2 action buttons. A maximum of two buttons can be set. No buttons are displayed by default.

Default value: **[{ text: '' }, { text: '' }]**

**Type:** [PopupV2Button?, PopupV2Button?]

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PopupV2InitInfo-buttons?: [PopupV2Button?, PopupV2Button?]--><!--Device-PopupV2InitInfo-buttons?: [PopupV2Button?, PopupV2Button?]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

Layout direction of **PopupV2**, which controls text arrangement and alignment. This is applicable to RTL (right- to-left) layout in internationalization scenarios. For details about the enum values, see Direction.

Default value: **Direction.Auto**

**Type:** [Direction](arkts-arkui-direction-e.md)

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PopupV2InitInfo-direction?: Direction--><!--Device-PopupV2InitInfo-direction?: Direction-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

PopupV2 icon.

**Note:** Default value: **''**, meaning no icon is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PopupV2InitInfo-icon?: ResourceStr--><!--Device-PopupV2InitInfo-icon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconModifier

```TypeScript
iconModifier?: ImageModifier
```

icon properties, such as the icon color, size, and border.

Default value: **undefined**, meaning the system icon properties are used.

**Type:** [ImageModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PopupV2InitInfo-iconModifier?: ImageModifier--><!--Device-PopupV2InitInfo-iconModifier?: ImageModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxWidth

```TypeScript
maxWidth?: Dimension
```

Maximum width of **PopupV2**, allowing **PopupV2** to be displayed with a custom width.

Default value: **400vp**

NOTE

1. When using a referenced resource type, the parameter type must be consistent with the attribute method type.
2. **maxWidth** is of the [Dimension](arkts-arkui-dimension-t.md) type, which supports numbers, percentages, or strings with units (such as 400, '50%', '400vp'). When using a referenced resource type, the resource type supports float and integer, for example, `$r('app.float.maxWidth')` and `$r('app.integer.maxWidth')`.
3. When the type is Resource, if no unit is set, the default unit is px.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PopupV2InitInfo-maxWidth?: Dimension--><!--Device-PopupV2InitInfo-maxWidth?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: ResourceStr
```

PopupV2 content text.

**Note:** Default value: **''**, meaning no content text is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PopupV2InitInfo-message: ResourceStr--><!--Device-PopupV2InitInfo-message: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## messageModifier

```TypeScript
messageModifier?: TextModifier
```

Content text properties, such as the content text color, font size, and font weight.

Default value: **undefined**, meaning the system content text properties are used.

**Type:** [TextModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PopupV2InitInfo-messageModifier?: TextModifier--><!--Device-PopupV2InitInfo-messageModifier?: TextModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onClose

```TypeScript
onClose?: Callback<void>
```

Callback for the **PopupV2** close button. No close button callback is set by default.

**Type:** Callback&lt;void&gt;

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PopupV2InitInfo-onClose?: Callback<void>--><!--Device-PopupV2InitInfo-onClose?: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showClose

```TypeScript
showClose?: boolean | Resource
```

PopupV2 close button. **true**: displays the close button; **false**: hides the close button. Resource type: displays the corresponding icon.

Default value: **true**

**Type:** boolean &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PopupV2InitInfo-showClose?: boolean | Resource--><!--Device-PopupV2InitInfo-showClose?: boolean | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: ResourceStr
```

PopupV2 title text.

**Note:** Default value: **''**, meaning no title text is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PopupV2InitInfo-title?: ResourceStr--><!--Device-PopupV2InitInfo-title?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## titleModifier

```TypeScript
titleModifier?: TextModifier
```

Title text properties, such as the title color, font size, and font weight.

Default value: **undefined**, meaning the system title text properties are used.

**Type:** [TextModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PopupV2InitInfo-titleModifier?: TextModifier--><!--Device-PopupV2InitInfo-titleModifier?: TextModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
