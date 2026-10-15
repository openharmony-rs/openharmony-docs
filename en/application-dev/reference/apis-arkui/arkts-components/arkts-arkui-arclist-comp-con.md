# Constants

## ArcListItem

```TypeScript
export declare const ArcListItem: ArcListItemInterface
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

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-export declare const ArcListItem: ArcListItemInterface--><!--Device-unnamed-export declare const ArcListItem: ArcListItemInterface-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

### Child Components

This component can contain a single child component.

## ArcListItemInstance

```TypeScript
export declare const ArcListItemInstance: ArcListItemAttribute
```

Defines ArcListItem Component instance.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-export declare const ArcListItemInstance: ArcListItemAttribute--><!--Device-unnamed-export declare const ArcListItemInstance: ArcListItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
