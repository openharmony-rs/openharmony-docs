# @ohos.arkui.advanced.SegmentButtonV2(api/@ohos.arkui.advanced.SegmentedButton.d.ts)

## Modules to Import

```TypeScript
import { SegmentButtonV2ItemOptions, OnSelectedIndexChange, OnSelectedIndexesChange, SegmentButtonV2Item, SegmentButtonV2Items, TabSegmentButtonV2, CapsuleSegmentButtonV2, MultiCapsuleSegmentButtonV2 } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [SegmentButtonV2Item](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2item-c.md) | Defines segmented button item. |
| [SegmentButtonV2Items](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2items-c.md) | Represents items of the **SegmentButtonV2** component. |

### Structs

| Name | Description |
| --- | --- |
| [CapsuleSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-capsulesegmentbuttonv2-s.md) | Defines the segmented button with capsule style. |
| [MultiCapsuleSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-multicapsulesegmentbuttonv2-s.md) | Defines the segmented button with multi capsule style. |
| [TabSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-tabsegmentbuttonv2-s.md) | Defines segmented button with tab style. |

### Interfaces

| Name | Description |
| --- | --- |
| [SegmentButtonV2ItemOptions](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2itemoptions-i.md) | Defines segmented button item options. |

### Types

| Name | Description |
| --- | --- |
| [OnSelectedIndexChange](arkts-arkui-onselectedindexchange-t.md) | Defines a callback invoked when the selected segmented button item changes. |
| [OnSelectedIndexesChange](arkts-arkui-onselectedindexeschange-t.md) | Defines a callback invoked when the selected segmented button items change. |

## Examples

```TypeScript
### Example 1: Using the TabSegmentButtonV2

This example describes how to use the TabSegmentButtonV2 component.


```

```TypeScript
### Example 2: Using the CapsuleSegmentButtonV2

This example describes how to use the CapsuleSegmentButtonV2 component.


```

```TypeScript
### Example 3: Using the MultiCapsuleSegmentButtonV2

This example describes how to use the MultiCapsuleSegmentButtonV2 component.


```

```TypeScript
### Example 4: Implementing Basic Usage of the Segmented Button Modifier

This example describes the basic usage of the Modifier for the tab segmented button, single-selection capsule segmented button, and multi-selection capsule segmented button.


```

```TypeScript
### Example 5: Enabling Property Animation for SegmentButtonV2

This example shows that after enableStateAnimation is enabled for SegmentButtonV2, the button switching also has an animation effect when the value of selectedIndex is modified through a state variable.

Since API version 24, the enableStateAnimation attribute is added to [TabSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-tabsegmentbuttonv2-s.md) and [CapsuleSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-capsulesegmentbuttonv2-s.md).
```

```TypeScript
### Example 6: Setting the Background Material

The following example uses the backgroundSystemMaterial attribute to set a transparent background material for the segment button, enable automatic color inversion and interactive deformation effects, and customize the color of the feedback light effect.

Since API version 26.0.0, the backgroundSystemMaterial attribute is added to [TabSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-tabsegmentbuttonv2-s.md) and [CapsuleSegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2-capsulesegmentbuttonv2-s.md).
```

```TypeScript
### Example 7: Listening to Changes in Inner Properties of Object-Type Properties

[SegmentButtonV2Item](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2item-c.md) uses the @ObservedV2 decorator, and the SegmentButtonV2 component receives each attribute parameter through @Param. For basic type properties decorated by @Trace, @Param can already observe property changes and trigger UI refresh. However, for internal properties of object type properties (such as itemIconSize and itemPadding) — for example, width and height of itemIconSize, or top, bottom, start, and end of itemPadding — these object types themselves are not decorated by @ObservedV2, so their internal property changes cannot be detected by @Param. Therefore, the UI does not automatically refresh when internal properties are modified. Using the makeObserved API to wrap object type properties (such as itemIconSize) can add deep observation capability to the internal properties of the object, so that when internal properties (such as width and height) are modified, the framework can detect the changes and trigger UI refresh. For details about the makeObserved API, see [makeObserved API: Changing Unobservable Data to Observable Data](../../../ui/state-management/arkts-new-makeObserved.md).

The following example uses UIUtils.makeObserved to wrap itemIconSize, and modifies the width and height properties of itemIconSize through a Button, to verify that changes to internal properties of object type properties can trigger UI refresh of SegmentButtonV2.
```
