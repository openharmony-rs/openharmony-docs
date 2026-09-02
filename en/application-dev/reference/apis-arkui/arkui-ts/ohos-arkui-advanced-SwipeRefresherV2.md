# SwipeRefresherV2

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @song-song-song-->
<!--Designer: @fenglinbailu-->
<!--Tester: @ybhou1993-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=53787af5f94c98e730d62fcc5514158329723f73 translatedAt=2026-08-28T01:33:06.412Z pushedAt=2026-08-28T06:17:24.129Z -->

The **SwipeRefresherV2** component is used to implement the pull-to-refresh feature. It supports custom loading prompt text and loading state control, and is suitable for scenarios where pull-to-refresh interaction needs to be implemented on a page.

This component is implemented based on [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). It provides developers with a standardized pull-to-refresh UI and simplifies the implementation of refresh logic. Compared with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), state management V2 delivers enhanced capabilities for deep observation and management of data objects, and is no longer limited to the component level. Developers can more flexibly control the data and state of content loading, achieving more efficient UI refresh.

> **NOTE**
>
> - This component can only be used in the stage model.
>
> - If [universal attributes](ts-component-general-attributes.md) and [universal events](ts-component-general-events.md) are set for **SwipeRefresherV2**, the compilation toolchain will generate an additional node \_\_Common\_\_ and mount the universal attributes or universal events on \_\_Common\_\_, rather than directly applying them to **SwipeRefresherV2** itself. This may cause the set universal attributes or universal events to not take effect or behave unexpectedly. Therefore, it is not recommended to set universal attributes and universal events on **SwipeRefresherV2**.

**Since:** 26.0.0

## Modules to Import

```ts
import { SwipeRefresherV2 } from '@kit.ArkUI';
```

## Child Components

Not supported

## SwipeRefresherV2

SwipeRefresherV2({content?: ResourceStr, isLoading: boolean})

Implements the pull-to-refresh feature. It is commonly used in scenarios where the latest content needs to be obtained by pulling down, such as refreshing the message list in a social app and loading information in a news app. When the user pulls down the page, the component displays the loading state. Developers need to implement the data acquisition logic themselves and control the switching of the loading state through the **isLoading** parameter.

**Since:** 26.0.0

**Decorator:** @ComponentV2

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Mandatory | Decorator | Description |
| -------- | -------- | -------- | -------- |----------|
| content | [ResourceStr](ts-types.md#resourcestr) | No | @Param | Text displayed when content is loading.<br/>Default value: an empty string.<br/>**Note:** If the text is wider than the column, it is truncated. |
| isLoading | boolean | Yes | @Require<br/>@Param | Whether the content is currently being loaded.<br> **true**: The content is being loaded.<br> **false**: The content is not being loaded. |

## Events

The [universal events](ts-component-general-events.md) are not supported.

## Examples

The **SwipeRefresherV2** component is supported since API version 26.0.0. The following example demonstrates different loading effects when the **content** parameter is set to an empty string or a non-empty string, and **isLoading** is set to **true** or **false**.

```ts
import { SwipeRefresherV2 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  build(): void {
    Column() {
      SwipeRefresherV2({
        content: 'Loading...',
        isLoading: true
      })
      SwipeRefresherV2({
        content: '',
        isLoading: true
      })
      SwipeRefresherV2({
        content: 'Loading...',
        isLoading: false
      })
    }
  }
}
```

<!--Del--> <!--DelEnd-->