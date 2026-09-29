# OperateItemV2

```TypeScript
export declare class OperateItemV2
```

Defines the element types for the right element of list items.

**Since:** 26.0.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class OperateItemV2--><!--Device-unnamed-export declare class OperateItemV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ComposeListItemV2, ContentItemV2, ContentItemV2Options, IconTypeV2, OperateButtonV2, OperateButtonV2Options, OperateCheckV2, OperateCheckV2Options, OperateIconV2, OperateIconV2Options, OperateItemV2, OperateItemV2Options } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: OperateItemV2Options)
```

A constructor used to create an **OperateItemV2** object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2-constructor(options?: OperateItemV2Options)--><!--Device-OperateItemV2-constructor(options?: OperateItemV2Options)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [OperateItemV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operateitemv2options-i.md) | No | Configuration of the right element of the list item.<br>If not set or set to undefined, an object is created based on the default effect of each attribute. |

## arrow

```TypeScript
public arrow?: OperateIconV2
```

Arrow, sized 12 × 24 vp.

By default, this attribute is not set or set to **undefined**, and the arrow is not displayed.

**Type:** [OperateIconV2](arkts-arkui-arkui-advanced-composelistitemv2-operateiconv2-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2-public arrow?: OperateIconV2--><!--Device-OperateItemV2-public arrow?: OperateIconV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## button

```TypeScript
public button?: OperateButtonV2
```

Button.

By default, this attribute is not set or set to **undefined**, and the button is not displayed.

**Type:** [OperateButtonV2](arkts-arkui-arkui-advanced-composelistitemv2-operatebuttonv2-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2-public button?: OperateButtonV2--><!--Device-OperateItemV2-public button?: OperateButtonV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## checkbox

```TypeScript
public checkbox?: OperateCheckV2
```

Checkbox, sized 24 × 24 vp.

By default, this attribute is not set or set to **undefined**, and the checkbox is not displayed.

**Type:** [OperateCheckV2](arkts-arkui-arkui-advanced-composelistitemv2-operatecheckv2-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2-public checkbox?: OperateCheckV2--><!--Device-OperateItemV2-public checkbox?: OperateCheckV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
public icon?: OperateIconV2
```

First icon, sized 24 × 24 vp.

By default, this attribute is not set or set to **undefined**, and the icon is not displayed.

**Type:** [OperateIconV2](arkts-arkui-arkui-advanced-composelistitemv2-operateiconv2-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2-public icon?: OperateIconV2--><!--Device-OperateItemV2-public icon?: OperateIconV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## image

```TypeScript
public image?: ResourceStr
```

Image resource, sized 48 × 48 vp.

By default, this attribute is not set or set to **undefined**, and the image is not displayed.

If symbolStyle is also set, only the symbol icon is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2-public image?: ResourceStr--><!--Device-OperateItemV2-public image?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radio

```TypeScript
public radio?: OperateCheckV2
```

Radio button, sized 24 × 24 vp.

By default, this attribute is not set or set to **undefined**, and the radio button is not displayed.

**Type:** [OperateCheckV2](arkts-arkui-arkui-advanced-composelistitemv2-operatecheckv2-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2-public radio?: OperateCheckV2--><!--Device-OperateItemV2-public radio?: OperateCheckV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## subIcon

```TypeScript
public subIcon?: OperateIconV2
```

Second icon, sized 24 × 24 vp.

By default, this attribute is not set or set to **undefined**, and the second icon is not displayed.

**Type:** [OperateIconV2](arkts-arkui-arkui-advanced-composelistitemv2-operateiconv2-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2-public subIcon?: OperateIconV2--><!--Device-OperateItemV2-public subIcon?: OperateIconV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
public symbolStyle?: SymbolGlyphModifier
```

Symbol icon resource, sized 48 × 48 vp. It has a higher priority than image, and only the symbol icon is displayed when both are set.

By default, this attribute is not set or set to **undefined**, and the symbol icon is not displayed.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2-public symbolStyle?: SymbolGlyphModifier--><!--Device-OperateItemV2-public symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
public text?: ResourceStr
```

Text.

By default, this attribute is not set or set to **undefined**, and the text is not displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2-public text?: ResourceStr--><!--Device-OperateItemV2-public text?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## toggle

```TypeScript
public toggle?: OperateCheckV2
```

Toggle.

By default, this attribute is not set or set to **undefined**, and the toggle is not displayed.

**Type:** [OperateCheckV2](arkts-arkui-arkui-advanced-composelistitemv2-operatecheckv2-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2-public toggle?: OperateCheckV2--><!--Device-OperateItemV2-public toggle?: OperateCheckV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
