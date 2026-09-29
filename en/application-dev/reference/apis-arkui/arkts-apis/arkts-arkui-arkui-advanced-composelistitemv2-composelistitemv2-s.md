# ComposeListItemV2

```TypeScript
export declare struct ComposeListItemV2
```

The **ComposeListItemV2** component is used to display a series of list items with the same width, suitable for presenting continuous, multi-row combinations of similar data (such as images and text).

This component is implemented based on [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), state management V2 delivers enhanced capabilities for deep observation and management of data objects, and is no longer limited to the component level. With state management V2, you can more flexibly control the data and state of list items through this component, achieving more efficient UI refresh.

> **NOTE:** 
> 
> - If [universal attributes](../arkts-components/arkts-arkui-common-comp.md) and [universal events](../arkts-components/arkts-arkui-common-comp.md) are set for **ComposeListItemV2**, the compilation toolchain will generate an additional node \_\_Common\_\_ and mount the universal attributes or universal events on \_\_Common\_\_, rather than directly applying them to **ComposeListItemV2** itself. This may cause the set universal attributes or universal events to not take effect or behave unexpectedly. Therefore, it is not recommended to set universal attributes and universal events on **ComposeListItemV2**.

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
