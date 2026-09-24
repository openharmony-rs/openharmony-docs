# ArcListItemInterface

```TypeScript
export interface ArcListItemInterface
```

The **ArcListItem** component is used to display individual child components in an [ArcList](arkts-arkui-arclist-comp.md#ohosarkuiarclist) component and must be used in conjunction with **ArcList**.

> **NOTE:** 

> - This component can be used only as a child of [ArcList](arkts-arkui-arclist-comp.md#ohosarkuiarclist).
> 
> - When this component is used with [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), its child components are created when it is created. When this component is used with [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) or [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), or when the parent component is [ArcList](arkts-arkui-arclist-comp.md#ohosarkuiarclist), its child components are created when it is laid out.
> 
> - This component can be used on phones, PCs, 2-in-1 devices, tablets, TVs, and wearables. In API version 22 and earlier versions, a compilation warning will be reported when this component is used on phones, PCs, 2-in-1 devices , tablets, and TVs, but the component can still run properly.

**Since:** 18

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

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Return value:**

| Type | Description |
| --- | --- |
| [ArcListItemAttribute](arkts-arkui-arclist-comp-arclistitemattribute-c.md) |  |
