# ContentItemV2

```TypeScript
export declare class ContentItemV2
```

Defines the left icon, icon size, and middle element text content displayed in the list item.

**Since:** 26.0.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class ContentItemV2--><!--Device-unnamed-export declare class ContentItemV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ComposeListItemV2, ContentItemV2, ContentItemV2Options, IconTypeV2, OperateButtonV2, OperateButtonV2Options, OperateCheckV2, OperateCheckV2Options, OperateIconV2, OperateIconV2Options, OperateItemV2, OperateItemV2Options } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ContentItemV2Options)
```

A constructor used to create a **ContentItemV2** object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ContentItemV2-constructor(options?: ContentItemV2Options)--><!--Device-ContentItemV2-constructor(options?: ContentItemV2Options)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ContentItemV2Options](arkts-arkui-arkui-advanced-composelistitemv2-contentitemv2options-i.md) | No | Configuration of the left element of the list item.<br>If not set or set to **undefined**, an object is created based on the default effect of each attribute. |

## description

```TypeScript
public description?: ResourceStr
```

Description content of the middle element.

This attribute is not set or set to **undefined** by default, meaning the description is not displayed.

**Text processing rule:** Text is displayed with unlimited line wrap when it overflows.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ContentItemV2-public description?: ResourceStr--><!--Device-ContentItemV2-public description?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
public icon?: ResourceStr
```

Icon resource of the left element.

This attribute is not set or set to **undefined** by default, meaning the icon resource is not displayed.

When **symbolStyle** is also set, only the Symbol icon is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ContentItemV2-public icon?: ResourceStr--><!--Device-ContentItemV2-public icon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconStyle

```TypeScript
public iconStyle?: IconTypeV2
```

Icon type of the left element.

This attribute is not set or set to **undefined** by default, meaning the icon resource is not displayed.

**Type:** [IconTypeV2](arkts-arkui-arkui-advanced-composelistitemv2-icontypev2-e.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ContentItemV2-public iconStyle?: IconTypeV2--><!--Device-ContentItemV2-public iconStyle?: IconTypeV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryText

```TypeScript
public primaryText?: ResourceStr
```

Title content of the middle element.

This attribute is not set or set to **undefined** by default, meaning the title is not displayed.

**Text processing rule:** Text is displayed with unlimited line wrap when it overflows.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ContentItemV2-public primaryText?: ResourceStr--><!--Device-ContentItemV2-public primaryText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryText

```TypeScript
public secondaryText?: ResourceStr
```

Subtitle content of the middle element.

This attribute is not set or set to **undefined** by default, meaning the subtitle is not displayed.

**Text processing rule:** Text is displayed with unlimited line wrap when it overflows.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ContentItemV2-public secondaryText?: ResourceStr--><!--Device-ContentItemV2-public secondaryText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
public symbolStyle?: SymbolGlyphModifier
```

Symbol icon resource of the left element, which takes precedence over **icon**. If both **icon** and **symbolStyle** are set, only the symbol icon is displayed.

This attribute is not set or set to **undefined** by default, meaning the symbol icon is not displayed.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ContentItemV2-public symbolStyle?: SymbolGlyphModifier--><!--Device-ContentItemV2-public symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
