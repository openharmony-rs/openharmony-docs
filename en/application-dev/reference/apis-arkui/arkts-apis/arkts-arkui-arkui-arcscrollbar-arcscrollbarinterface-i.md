# ArcScrollBarInterface

The **ArcScrollBar** component is designed to be used together with scrollable components such as ArcList, List, Grid, Scroll, and WaterFlow.

> **NOTE:** 
> 
> - This component is supported since API version 18. Updates will be marked with a superscript to indicate their earliest API version.
> 
> - When the width and height of the **ArcScrollBar** component are not set, the **maxSize** value specified in its parent component [LayoutConstraint](arkts-arkui-framenode-layoutconstraint-i.md) is used as the width and height. If the parent component of the **ArcScrollBar** component contains scrollable components, such as ArcList, List,Grid, Scroll, or WaterFlow, you are advised to set the width and height of the
> **ArcScrollBar** component. Otherwise, the width and height of the component may be infinite.
> 
> - This component can be used on phones, PCs, 2-in-1 devices, tablets, TVs, and wearables. In API version 22 and earlier versions, a compilation warning will be reported when this component is used on phones, PCs, 2-in-1 devices , tablets, and TVs, but the component can still run properly.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcScrollBar, ArcScrollBarAttribute } from '@kit.ArkUI';
```

## [[Call]]

```TypeScript
(options: ArcScrollBarOptions): ArcScrollBarAttribute
```

A constructor used to create an **ArcScrollBar** instance.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ArcScrollBarOptions](arkts-arkui-arkui-arcscrollbar-arcscrollbaroptions-i.md) | Yes | Parameters of the **ArcScrollBar** component. |

**Return value:**

| Type | Description |
| --- | --- |
| [ArcScrollBarAttribute](arkts-arkui-arkui-arcscrollbar-arcscrollbarattribute-c.md) |  |
