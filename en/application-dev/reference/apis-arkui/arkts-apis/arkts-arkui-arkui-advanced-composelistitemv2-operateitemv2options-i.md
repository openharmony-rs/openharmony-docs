# OperateItemV2Options

```TypeScript
export interface OperateItemV2Options
```

Defines the options for the **OperateItemV2** constructor.

**Since:** 26.0.0

<!--Device-unnamed-export interface OperateItemV2Options--><!--Device-unnamed-export interface OperateItemV2Options-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ComposeListItemV2, ContentItemV2, ContentItemV2Options, IconTypeV2, OperateButtonV2, OperateButtonV2Options, OperateCheckV2, OperateCheckV2Options, OperateIconV2, OperateIconV2Options, OperateItemV2, OperateItemV2Options } from '@kit.ArkUI';
```

## arrow

```TypeScript
arrow?: OperateIconV2
```

Right element of the list item is an arrow. Not set by default or set to **undefined**, the arrow is not displayed.

**Type:** [OperateIconV2](arkts-arkui-arkui-advanced-composelistitemv2-operateiconv2-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2Options-arrow?: OperateIconV2--><!--Device-OperateItemV2Options-arrow?: OperateIconV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## button

```TypeScript
button?: OperateButtonV2
```

Right element of the list item is a button. Not set by default or set to **undefined**, the button is not displayed.

**Type:** [OperateButtonV2](arkts-arkui-arkui-advanced-composelistitemv2-operatebuttonv2-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2Options-button?: OperateButtonV2--><!--Device-OperateItemV2Options-button?: OperateButtonV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## checkbox

```TypeScript
checkbox?: OperateCheckV2
```

Right element of the list item is a checkbox. Not set by default or set to **undefined**, the checkbox is not displayed.

**Type:** [OperateCheckV2](arkts-arkui-arkui-advanced-composelistitemv2-operatecheckv2-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2Options-checkbox?: OperateCheckV2--><!--Device-OperateItemV2Options-checkbox?: OperateCheckV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: OperateIconV2
```

First icon of the right element of the list item. Not set by default or set to **undefined**, the icon is not displayed.

**Type:** [OperateIconV2](arkts-arkui-arkui-advanced-composelistitemv2-operateiconv2-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2Options-icon?: OperateIconV2--><!--Device-OperateItemV2Options-icon?: OperateIconV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## image

```TypeScript
image?: ResourceStr
```

Right element of the list item is an image. Not set by default or set to **undefined**, the image is not displayed. When **symbolStyle** is also set, only the symbol icon is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2Options-image?: ResourceStr--><!--Device-OperateItemV2Options-image?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radio

```TypeScript
radio?: OperateCheckV2
```

Right element of the list item is a radio button. Not set by default or set to **undefined**, the radio button is not displayed.

**Type:** [OperateCheckV2](arkts-arkui-arkui-advanced-composelistitemv2-operatecheckv2-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2Options-radio?: OperateCheckV2--><!--Device-OperateItemV2Options-radio?: OperateCheckV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## subIcon

```TypeScript
subIcon?: OperateIconV2
```

Second icon of the right element of the list item. Not set by default or set to **undefined**, the second icon is not displayed.

**Type:** [OperateIconV2](arkts-arkui-arkui-advanced-composelistitemv2-operateiconv2-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2Options-subIcon?: OperateIconV2--><!--Device-OperateItemV2Options-subIcon?: OperateIconV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Right element of the list item is a symbol icon resource, which takes priority over **image**. When both are set, only the symbol icon is displayed. Not set by default or set to **undefined**, the symbol icon is not displayed.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2Options-symbolStyle?: SymbolGlyphModifier--><!--Device-OperateItemV2Options-symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr
```

Right element of the list item is text. Not set by default or set to **undefined**, the text is not displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2Options-text?: ResourceStr--><!--Device-OperateItemV2Options-text?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## toggle

```TypeScript
toggle?: OperateCheckV2
```

Right element of the list item is a toggle. Not set by default or set to **undefined**, the toggle is not displayed.

**Type:** [OperateCheckV2](arkts-arkui-arkui-advanced-composelistitemv2-operatecheckv2-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateItemV2Options-toggle?: OperateCheckV2--><!--Device-OperateItemV2Options-toggle?: OperateCheckV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
