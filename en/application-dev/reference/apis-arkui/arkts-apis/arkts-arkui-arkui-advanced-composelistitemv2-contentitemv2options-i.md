# ContentItemV2Options

```TypeScript
export interface ContentItemV2Options
```

Defines the options for the **ContentItemV2** constructor.

**Since:** 26.0.0

<!--Device-unnamed-export interface ContentItemV2Options--><!--Device-unnamed-export interface ContentItemV2Options-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ComposeListItemV2, ContentItemV2, ContentItemV2Options, IconTypeV2, OperateButtonV2, OperateButtonV2Options, OperateCheckV2, OperateCheckV2Options, OperateIconV2, OperateIconV2Options, OperateItemV2, OperateItemV2Options } from '@kit.ArkUI';
```

## description

```TypeScript
description?: ResourceStr
```

Description content of the middle element. Not set by default or set to **undefined**, the description content is not displayed. The text is displayed with unlimited line wrapping when it overflows.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ContentItemV2Options-description?: ResourceStr--><!--Device-ContentItemV2Options-description?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Icon resource of the left element. Not set by default or set to **undefined**, the icon resource is not displayed. When **symbolStyle** is also set, only the Symbol icon is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ContentItemV2Options-icon?: ResourceStr--><!--Device-ContentItemV2Options-icon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconStyle

```TypeScript
iconStyle?: IconTypeV2
```

Icon type of the left element. Not set by default or set to **undefined**, the leading icon resource is not displayed.

**Type:** [IconTypeV2](arkts-arkui-arkui-advanced-composelistitemv2-icontypev2-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ContentItemV2Options-iconStyle?: IconTypeV2--><!--Device-ContentItemV2Options-iconStyle?: IconTypeV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryText

```TypeScript
primaryText?: ResourceStr
```

Title content of the middle element.

Not set by default or set to **undefined**, the title content is not displayed.

The text is displayed with unlimited line wrapping when it overflows.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ContentItemV2Options-primaryText?: ResourceStr--><!--Device-ContentItemV2Options-primaryText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryText

```TypeScript
secondaryText?: ResourceStr
```

Subtitle content of the middle element. Not set by default or set to **undefined**, the subtitle content is not displayed. The text is displayed with unlimited line wrapping when it overflows.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ContentItemV2Options-secondaryText?: ResourceStr--><!--Device-ContentItemV2Options-secondaryText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Symbol icon resource of the left element, which takes priority over **icon**. When both are set, only the Symbol icon is displayed. Not set by default or set to **undefined**, the Symbol icon is not displayed.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ContentItemV2Options-symbolStyle?: SymbolGlyphModifier--><!--Device-ContentItemV2Options-symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
