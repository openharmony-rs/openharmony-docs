# ArkListOptions

```TypeScript
declare interface ArkListOptions
```

Provides basic parameters for creating an **ArcList** component.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';
```

## header

```TypeScript
header?: ComponentContent
```

Header component.

**Type:** ComponentContent

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## initialIndex

```TypeScript
initialIndex?: number
```

Item displayed at the beginning of the viewport when the **ArcList** component is loaded for the first time, that is, the first item to be displayed.<br>Default value: **0**<br> **NOTE:** <br>If the set value is a negative number or is greater than the index of the last item, the value is invalid. In this case, the default value will be used.

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## scroller

```TypeScript
scroller?: Scroller
```

Controller of the scrollable component. After being bound to **ArcList**, the controller can control the scrolling of **ArcList**.<br>**NOTE:** <br>The scroller cannot be bound to other scrollable components.

**Type:** [Scroller](arkts-arkui-scroll-comp-scroller-c.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
