# SwipeRefresherV2

```TypeScript
export declare struct SwipeRefresherV2
```

The **SwipeRefresherV2** component is used to implement the pull-to-refresh feature. It supports custom loading prompt text and loading state control, and is suitable for scenarios where pull-to-refresh interaction needs to be implemented on a page.

This component is implemented based on [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). It provides developers with a standardized pull-to-refresh UI and simplifies the implementation of refresh logic. Compared with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), state management V2 delivers enhanced capabilities for deep observation and management of data objects, and is no longer limited to the component level. Developers can more flexibly control the data and state of content loading, achieving more efficient UI refresh.

> **NOTE:** 
> 
> - This component can only be used in the stage model.
> 
> - If [universal attributes](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) and [universal events](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) are set for **SwipeRefresherV2**, the compilation toolchain will generate an additional node \_\_Common\_\_ and mount the universal attributes or universal events on \_\_Common\_\_, rather than directly applying them to **SwipeRefresherV2** itself. This may cause the set universal attributes or universal events to not take effect or behave unexpectedly. Therefore, it is not recommended to set universal attributes and universal events on **SwipeRefresherV2**.

@struct { SwipeRefresherV2 }

**Since:** 26.0.0

**Decorator:** @ComponentV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SwipeRefresherV2 } from '@kit.ArkUI';
```

## content

```TypeScript
content?: ResourceStr
```

Text displayed when content is loading.

Default value: an empty string.

**Note:** If the text is wider than the column, it is truncated.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isLoading

```TypeScript
isLoading: boolean
```

Whether the content is currently being loaded.

**true**: The content is being loaded.

**false**: The content is not being loaded.

**Type:** boolean

**Since:** 26.0.0

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
