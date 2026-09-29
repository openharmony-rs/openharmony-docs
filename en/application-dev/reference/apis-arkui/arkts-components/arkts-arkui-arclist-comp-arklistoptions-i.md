# ArkListOptions

```TypeScript
declare interface ArkListOptions
```

Provides basic parameters for creating an **ArcList** component.

**Since:** 18

<!--Device-unnamed-declare interface ArkListOptions--><!--Device-unnamed-declare interface ArkListOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';
```

## header

```TypeScript
header?: ComponentContent
```

Header component of **ArcList**, used to display a title or custom content at the top of the list. If not set, no header component is displayed.

**Type:** ComponentContent

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArkListOptions-header?: ComponentContent--><!--Device-ArkListOptions-header?: ComponentContent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## initialIndex

```TypeScript
initialIndex?: number
```

Index value of the item displayed at the start position of the viewport when **ArcList** is initially loaded.

Default value: **0**

**Note:** If the value is set to a negative number or exceeds the index value of the last item in the current **ArcList**, it is considered invalid, and the default value is used.

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArkListOptions-initialIndex?: number--><!--Device-ArkListOptions-initialIndex?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## scroller

```TypeScript
scroller?: Scroller
```

Controller of the scrollable component. After being bound to **ArcList**, it can be used to control the scrolling of **ArcList**. If not set, no scroll controller is bound.

**Note:** It is not allowed to bind the same scroll control object with other scrollable components, such as [List](arkts-arkui-list-comp.md), [Grid](arkts-arkui-grid-comp.md), [Scroll](arkts-arkui-scroll-comp.md), and [WaterFlow](arkts-arkui-waterflow-comp.md).

**Type:** [Scroller](arkts-arkui-scroll-comp-scroller-c.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArkListOptions-scroller?: Scroller--><!--Device-ArkListOptions-scroller?: Scroller-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
