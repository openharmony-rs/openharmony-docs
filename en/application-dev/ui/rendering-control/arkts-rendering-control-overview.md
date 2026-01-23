# Rendering Control Overview
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liubihao-->
<!--Designer: @lixingchi1-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->


ArkUI leverages two primary approaches for building UIs: the [build()](../state-management/arkts-create-custom-components.md#build) function of [custom components](../state-management/arkts-create-custom-components.md) and declarative UI description statements in the [@Builder](../state-management/arkts-builder.md) decorator. In declarative description statements, you can use rendering control statements along with built-in components to accelerate UI construction. These rendering control statements include conditional rendering statements that control component visibility and loop statements that quickly generate components based on array data.

## Basic Concepts

| Term    | Description         |
| ---------- | ------------- |
| Conditional rendering| Determines whether to render a specified UI component based on the given conditions.|
| Rendering of repeated content| Renders a series of similar UI components based on the given data source.|
| Conditional rendering statement| [if-else](./arkts-rendering-control-ifelse.md)|
| Loop statement| [ForEach](./arkts-rendering-control-foreach.md), [LazyForEach](./arkts-rendering-control-lazyforeach.md), and [Repeat](./arkts-new-rendering-control-repeat.md)|
| Scrollable container component| [List](../../reference/apis-arkui/arkui-ts/ts-container-list.md), [ListItemGroup](../../reference/apis-arkui/arkui-ts/ts-container-listitemgroup.md), [Grid](../../reference/apis-arkui/arkui-ts/ts-container-grid.md), [Swiper](../../reference/apis-arkui/arkui-ts/ts-container-swiper.md), and [WaterFlow](../../reference/apis-arkui/arkui-ts/ts-container-waterflow.md)|
| Preload area| The area adjacent to the visible area of the container component in lazy loading mode. The child components in this area are created and laid out in advance when the system is idle. The size of this area is determined by the **cachedCount** attribute of the container component.<br>Take the **List** component as an example. After the [cachedCount](../../reference/apis-arkui/arkui-ts/ts-container-list.md#cachedcount) attribute is set, a specified number of [ListItem](../../reference/apis-arkui/arkui-ts/ts-container-listitem.md) components are preloaded and laid out in the upper and lower areas outside the visible area. The default value of **cachedCount** is equal to the number of nodes in the visible area.|

## Full Loading and Lazy Loading

There are two modes to repeatedly render array data: full loading and lazy loading (used with the scrollable container components).

![full-lazy-load-overview](./figures/full-lazy-load-overview.png)

When full loading mode is used, all child component nodes are mounted to the UI tree at a time in the composition phase, and all child components are drawn in the subsequent rendering phase. For a long list, loading all nodes will cause page freezing and high memory usage. Especially when the list data is frequently refreshed, the page usage experience is greatly affected. The initial loading takes a long time, but the performance is good when user scrolls the page. This mode is suitable for scenarios with a small amount of data.

In contrast, only the child component nodes in the list visible area and preload area are loaded in lazy loading mode. The scrollable container component obtains the index range of the components to be constructed, creates the required nodes, and calculates the layout. When the list is scrolled or data is updated, the index range is refreshed again. The performance of the initial loading is improved. However, the performance deteriorates when nodes are created during scrolling.

You should select a proper rendering mode based on the actual service. If the length of the data list is fixed and is less than a certain value (depending on the number of child components displayed in the container component), you can use the full loading mode. In other scenarios, lazy loading is recommended for rendering list data.

The ArkUI framework provides the [ForEach](./arkts-rendering-control-foreach.md) component for full loading and [LazyForEach](./arkts-rendering-control-lazyforeach.md) component for lazy loading. In addition, the [Repeat](./arkts-new-rendering-control-repeat.md) component can be used in both rendering modes and supports component reuse by default.

|  Component | Lazy Loading Supported| Component Reuse Supported| Recommended Usage Scenarios|
| ------ | ------ | ------ | ------ |
| ForEach | × | × | Short list with a small number of data records.|
| LazyForEach | √ | × | Long list or grid where a large amount of data needs to be scrolled through.|
| Repeat | √ | √ | Long list or grid where a large amount of data needs to be scrolled through. **Repeat**'s reuse capability helps optimize rendering performance.|

## Best Practices

- [Optimizing Performance Using LazyForEach](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-lazyforeach-optimization)
- [Optimizing Frame Loss for Long List Loading](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-best-practices-long-list)
