# ComposeListItemV2

```TypeScript
export declare struct ComposeListItemV2
```

Defines the left element, middle element, and right display content of the list item.

**Since:** 26.0.0

**Decorator:** @ComponentV2

<!--Device-unnamed-export declare struct ComposeListItemV2--><!--Device-unnamed-export declare struct ComposeListItemV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ComposeListItemV2, ContentItemV2, ContentItemV2Options, IconTypeV2, OperateButtonV2, OperateButtonV2Options, OperateCheckV2, OperateCheckV2Options, OperateIconV2, OperateIconV2Options, OperateItemV2, OperateItemV2Options } from '@kit.ArkUI';
```

## contentItemV2

```TypeScript
contentItemV2?: ContentItemV2
```

Left and middle elements of the list item.

If not set or set to undefined, the left and middle elements are not displayed.

**Type:** [ContentItemV2](arkts-arkui-arkui-advanced-composelistitemv2-contentitemv2-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ComposeListItemV2-contentItemV2?: ContentItemV2--><!--Device-ComposeListItemV2-contentItemV2?: ContentItemV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## operateItemV2

```TypeScript
operateItemV2?: OperateItemV2
```

Right element of the list item.

If not set or set to **undefined**, the right element is not displayed.

**Type:** [OperateItemV2](arkts-arkui-arkui-advanced-composelistitemv2-operateitemv2-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ComposeListItemV2-operateItemV2?: OperateItemV2--><!--Device-ComposeListItemV2-operateItemV2?: OperateItemV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
