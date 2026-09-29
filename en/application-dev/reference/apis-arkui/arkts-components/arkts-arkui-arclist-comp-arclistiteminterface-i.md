# ArcListItemInterface

```TypeScript
export interface ArcListItemInterface
```

A child component used to display items in an arc list. It must be used in conjunction with [ArcList](arkts-arkui-arclist-comp.md).

> **NOTE:** 
> 
> - The parent component of this component can only be [ArcList](arkts-arkui-arclist-comp.md).
> 
> - When **ArcListItem** is used with [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), its child components are created when **ArcListItem** is created. When it is used with [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) or [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), or directly as a child component of the [ArcList](arkts-arkui-arclist-comp.md) component, its child components are created when **ArcListItem** is laid out.
> 
> - This component can be used on Phone, PC/2in1, Tablet, TV, and Wearable devices. In API version 22 and earlier,using it on Phone, PC/2in1, Tablet, and TV generates a compilation warning, but it can run normally.

**Since:** 18

<!--Device-unnamed-export interface ArcListItemInterface--><!--Device-unnamed-export interface ArcListItemInterface-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';
```

## [[Call]]

```TypeScript
(): ArcListItemAttribute
```

Creates an item for the **ArcList** component.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListItemInterface-(): ArcListItemAttribute--><!--Device-ArcListItemInterface-(): ArcListItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Return value:**

| Type | Description |
| --- | --- |
| [ArcListItemAttribute](arkts-arkui-arclist-comp-arclistitemattribute-c.md) |  |
