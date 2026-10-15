# ArcListItemAttribute

```TypeScript
export declare class ArcListItemAttribute extends CommonMethod<ArcListItemAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

**Inheritance/Implementation:** ArcListItemAttribute extends CommonMethod&lt;ArcListItemAttribute&gt;

**Since:** 18

<!--Device-unnamed-export declare class ArcListItemAttribute extends CommonMethod<ArcListItemAttribute>--><!--Device-unnamed-export declare class ArcListItemAttribute extends CommonMethod<ArcListItemAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';
```

## autoScale

```TypeScript
autoScale(enable: Optional<boolean>): ArcListItemAttribute
```

Sets whether to automatically scale the **ArcListItem**. When enabled, the **ArcListItem** automatically adjusts its display size based on its position in the arc list.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListItemAttribute-autoScale(enable: Optional<boolean>): ArcListItemAttribute--><!--Device-ArcListItemAttribute-autoScale(enable: Optional<boolean>): ArcListItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether ArcListItem supports automatic scaling display. The value true means supported, and false means not supported.<br>Default value: true, automatic scaling display is supported. |

**Return value:**

| Type | Description |
| --- | --- |
| [ArcListItemAttribute](arkts-arkui-arclist-comp-arclistitemattribute-c.md) |  |

## swipeAction

```TypeScript
swipeAction(options: Optional<SwipeActionOptions>): ArcListItemAttribute
```

Sets the swipe action of the **ArcListItem**.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListItemAttribute-swipeAction(options: Optional<SwipeActionOptions>): ArcListItemAttribute--><!--Device-ArcListItemAttribute-swipeAction(options: Optional<SwipeActionOptions>): ArcListItemAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[SwipeActionOptions](arkts-arkui-listitem-comp-swipeactionoptions-i.md)&gt; | Yes | Configuration options for the swipe-out operation of **ArcListItem**. For details, see **SwipeActionOptions**. If this parameter is not set, no swipe-out operation is configured. |

**Return value:**

| Type | Description |
| --- | --- |
| [ArcListItemAttribute](arkts-arkui-arclist-comp-arclistitemattribute-c.md) |  |
