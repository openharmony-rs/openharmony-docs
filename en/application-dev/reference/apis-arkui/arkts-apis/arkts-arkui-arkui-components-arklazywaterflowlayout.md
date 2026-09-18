# @ohos.arkui.components.ArkLazyWaterFlowLayout

## Modules to Import

```TypeScript
import { LazyVWaterFlowLayout, LazyVWaterFlowLayoutAttribute, LazyWaterFlowLayoutAttribute } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [LazyVWaterFlowLayoutAttribute](arkts-arkui-arkui-components-arklazywaterflowlayout-lazyvwaterflowlayoutattribute-c.md) | Defines the lazy vertical waterflow layout attribute. |
| [LazyWaterFlowLayoutAttribute](arkts-arkui-arkui-components-arklazywaterflowlayout-lazywaterflowlayoutattribute-c.md) | Defines the lazy waterflow layout attribute. |

### Interfaces

| Name | Description |
| --- | --- |
| [LazyVWaterFlowLayoutInterface](arkts-arkui-arkui-components-arklazywaterflowlayout-lazyvwaterflowlayoutinterface-i.md) | Defines the lazy vertical waterflow layout component. |

### Constants

| Name | Description |
| --- | --- |
| [LazyVWaterFlowLayout](arkts-arkui-arkui-components-arklazywaterflowlayout-con.md#lazyvwaterflowlayout) | Defines LazyVWaterFlowLayout Component. |
| [LazyVWaterFlowLayoutInstance](arkts-arkui-arkui-components-arklazywaterflowlayout-con.md#lazyvwaterflowlayoutinstance) | Defines LazyVWaterFlowLayout Component instance. |

## Examples

```TypeScript
### Example 1: Implementing Lazy-Loading Waterfall Layout

This example shows how to use the [Scroll](ts-container-scroll.md) and LazyVWaterFlowLayout components to implement the lazy-loading waterfall layout.

MyDataSource implements the LazyForEach data source API [IDataSource](ts-rendering-control-lazyforeach.md#idatasource), which is used to provide child components for LazyVWaterFlowLayout through LazyForEach.

Since API version 26.0.0, the LazyVWaterFlowLayout component is supported.
```

```TypeScript

```

```TypeScript
### Example 2: Setting Header or Footer Component and Sticky Styles

This example nests LazyVWaterFlowLayout inside [Scroll](ts-container-scroll.md), and implements sticky styles at the top and bottom of the waterfall layout through header, footer, and sticky. During scrolling, the header sticks to the top of the visible area, and the footer sticks to the bottom of the visible area.

Since API version 26.0.0, the header, footer, and sticky attributes are supported.


```

```TypeScript
### Example 3: Setting Adaptive Column Count

This example uses columnsTemplate to set repeat(auto-fill, track-size) and ItemFillPolicy, implementing adaptive column count for LazyVWaterFlowLayout.

Since API version 26.0.0, the columnsTemplate interface is supported.
```
