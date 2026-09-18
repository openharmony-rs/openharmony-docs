# WaterFlow

The **WaterFlow** component is a water flow container that consists of cells formed by rows and columns and arranges items of different sizes from top to bottom according to the preset rules.

> **NOTE**

> The **WaterFlow** component supports the waterfall layout but does not support the edit mode or dragging of child > elements. > > The component has been bound with gestures to implement functions such as following the finger. If you need to add > custom gestures, refer to Enhanced Gesture Interception.

## Child Components

Only the FlowItem child component and custom components are supported. When a custom component is used in **WaterFlow**, you are advised to use **FlowItem** as the top-level component of the custom component. You are not advised to set attributes and event methods for the custom component.

Child components can be dynamically generated using rendering control types [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md), [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md). **LazyForEach** or **Repeat** is recommended to optimize performance.

> **NOTE:** 
> 
> When the **visibility** attribute of a child component of **WaterFlow** is set to **None**, this child component is
> not displayed in the container, but its **columnsGap**, **rowsGap**, and **margin** settings are still effective.
> 
> If there are a large number of child components, you are advised to adopt methods such as lazy loading, data
> caching, component reuse, fixed dimensions, and layout optimization to improve performance and reduce memory usage.
> For best practices, see
> [Optimizing Frame Loss for Waterfall Loading](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-waterflow-performance-optimization).
> 
> In vertical layout mode, **WaterFlow** calculates the cumulative height of child components in each column and
> places new child components in the column with the smallest cumulative height to maintain a compact overall layout.
> 
> If the heights of multiple columns are the same, the leftmost column is prioritized. In RTL mode, the rightmost
> column is prioritized.
> 
> Starting from API version 21, the maximum width or height for a single child component inside a **WaterFlow**
> container is 16,777,216 px. In API version 20 and earlier versions, the limit was 1,000,000 px. If a child
> component exceeds the applicable size limit, scrolling or display behavior may become abnormal.

## WaterFlow

```TypeScript
WaterFlow(options?: WaterFlowOptions)
```

Creates a **WaterFlow** component.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [WaterFlowOptions](arkts-arkui-waterflowoptions-i.md) | No | Parameters of the **WaterFlow** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [UIWaterFlowEvent](arkts-arkui-uiwaterflowevent-i.md) | Represents the return value of the [getEvent('WaterFlow')](../arkts-apis/arkts-arkui-typenode-getevent-f.md) method in **frameNode**, which can be used to set scroll events for a **WaterFlow** node. |
| [WaterFlowOptions](arkts-arkui-waterflowoptions-i.md) | Provides parameters of the **WaterFlow** component. |

### Types

| Name | Description |
| --- | --- |
| [GetItemMainSizeByIndex](arkts-arkui-getitemmainsizebyindex-t.md) | Obtains the main axis size of a specified water flow item based on its index. |
| [OnWaterFlowScrollIndexCallback](arkts-arkui-onwaterflowscrollindexcallback-t.md) | Represents a callback for item changes in the visible area of the **WaterFlow** component. |

### Enums

| Name | Description |
| --- | --- |
| [WaterFlowLayoutMode](arkts-arkui-waterflowlayoutmode-e.md) | Enumerates the layout modes of the **WaterFlow** component. |

## Examples

```TypeScript
### Example 1: Using a Basic WaterFlow Component

This example demonstrates the basic usage of the WaterFlow component, including data loading, attribute setting, and event callbacks.

WaterFlowDataSource implements the [IDataSource](ts-rendering-control-lazyforeach.md#idatasource) data source interface of [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and is used to provide child components to WaterFlow through LazyForEach.

When a field that affects the width and height of FlowItem in the [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) data changes, you need to notify [DataChangeListener](ts-rendering-control-lazyforeach.md#datachangelistener) after modifying the data, for example, by calling [onDataChange](ts-rendering-control-lazyforeach.md#ondatachange8) or [onDataReloaded](ts-rendering-control-lazyforeach.md#ondatareloaded). If only the data content is modified without triggering a data change notification, LazyForEach may not refresh the corresponding FlowItem.
```

```TypeScript

```

```TypeScript
### Example 2: Implementing Automatic Column Count Calculation

This example showcases how to implement automatic column count calculation using the auto-fill feature.

For details about WaterFlowDataSource and the complete code, see [Example 1: Using a Basic WaterFlow Component](#example-1-using-a-basic-waterflow-component).


```

```TypeScript
### Example 3: Using WaterFlowSections

This example demonstrates the initialization of groups and the different effects of the splice, update, values, and length APIs.

For usage with state management V2, see [WaterFlow and makeObserved](../../../ui/state-management/arkts-v1-v2-migration-inner-object.md#scrollable-component).

For details about WaterFlowDataSource and the complete code, see [Example 1: Using a Basic WaterFlow Component](#example-1-using-a-basic-waterflow-component).


```

```TypeScript
### Example 4: Using the Pinch Gesture to Change the Column Count

This example demonstrates how to use [priorityGesture](ts-gesture-settings.md#prioritygesture) and [PinchGesture](ts-basic-gestures-pinchgesture.md) to implement the feature of using a pinch gesture to change the number of columns in a layout.

For details about WaterFlowDataSource and the complete code, see [Example 1: Using a Basic WaterFlow Component](#example-1-using-a-basic-waterflow-component).


```

```TypeScript
### Example 5: Setting the Edge Fading Effect

This example demonstrates how to enable the edge fading effect for the WaterFlow component using the [fadingEdge](ts-container-scrollable-common.md#fadingedge14) API and set the length of the fading edge using the fadingEdgeLength parameter.

For details about WaterFlowDataSource and the complete code, see [Example 1: Using a Basic WaterFlow Component](#example-1-using-a-basic-waterflow-component).


```

```TypeScript
### Example 6: Setting the Single-Side Edge Effect

This example uses the [edgeEffect](ts-container-scrollable-common.md#edgeeffect11) API to set the single-side edge effect for the WaterFlow component.

For details about WaterFlowDataSource and the complete code, see [Example 1: Using a Basic WaterFlow Component](#example-1-using-a-basic-waterflow-component).


```

```TypeScript
### Example 7: Setting and Changing the Footer Component in the WaterFlow Component

In API version 18 and later versions, this example demonstrates how to set the footer component in the WaterFlow component using the footerContent API of [WaterFlowOptions](arkts-arkui-waterflowoptions-i.md). The footer component is updated using the update function of ComponentContent.

For details about WaterFlowDataSource and the complete code, see [Example 1: Using a Basic WaterFlow Component](#example-1-using-a-basic-waterflow-component).


```

```TypeScript
### Example 8: Implementing Pull-to-Refresh for a WaterFlow Component

This example demonstrates how to implement the pull-to-refresh function for the data source of the WaterFlow component via [Refresh](ts-container-refresh.md).

For details about WaterFlowDataSource and the complete code, see [Example 1: Using a Basic WaterFlow Component](#example-1-using-a-basic-waterflow-component).


```

```TypeScript
### Example 9: Configuring the Number of Columns in the WaterFlow Component Based on Breakpoints

In API version 22 and later versions, this example shows how to configure the number of columns in the WaterFlow component based on breakpoints.

When the WaterFlow width is within the breakpoint range of sm or smaller, two columns are displayed.



When the WaterFlow width is within the breakpoint range of md, three columns are displayed.



When the WaterFlow width is within the breakpoint range of lg or larger, five columns are displayed.


```

```TypeScript
### Example 10: Obtaining the Content Height for the WaterFlow Component

From API version 22, this example uses the WaterFlow component to obtain the content height.

For details about WaterFlowDataSource and the complete code, see [Example 1: Using a Basic WaterFlow Component](#example-1-using-a-basic-waterflow-component).


```

```TypeScript
### Example 11: Setting a Scrolling Event

This example obtains a [UIWaterFlowEvent](arkts-arkui-uiwaterflowevent-i.md) instance via getEvent('WaterFlow') on a FrameNode and sets scroll event callbacks for a WaterFlow component. This approach is intended for scenarios where the page code cannot be directly modified to use declarative callbacks.

The UIWaterFlowEvent API is added since API version 19.
```
