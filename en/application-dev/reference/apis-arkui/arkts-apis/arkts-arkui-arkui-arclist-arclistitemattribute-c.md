# ArcListItemAttribute

In addition to the universal attributes, the following attributes are supported.

**Inheritance/Implementation:** ArcListItemAttribute extends CommonMethod<ArcListItemAttribute>

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';
```

## autoScale

```TypeScript
autoScale(enable: Optional<boolean>): ArcListItemAttribute
```

Sets whether to enable auto-scaling for the **ArcListItem** component.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable auto-scaling.<br>**true**: Enable auto-scaling.<br> **false**: Disable auto-scaling.<br>Default value: **true**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ArcListItemAttribute](arkts-arkui-arkui-arclist-arclistitemattribute-c.md) |  |

## swipeAction

```TypeScript
swipeAction(options: Optional<SwipeActionOptions>): ArcListItemAttribute
```

Sets the swipe action item displayed when the **ArcListItem** component is swiped out from the screen edge.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[SwipeActionOptions](../arkts-components/arkts-arkui-swipeactionoptions-i.md)&gt; | Yes | Swipe action item displayed when the **ArcListItem** component is swiped out from the screen edge. |

**Return value:**

| Type | Description |
| --- | --- |
| [ArcListItemAttribute](arkts-arkui-arkui-arclist-arclistitemattribute-c.md) |  |
