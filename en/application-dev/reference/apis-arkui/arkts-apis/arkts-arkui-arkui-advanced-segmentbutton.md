# @ohos.arkui.advanced.SegmentButton

## Modules to Import

```TypeScript
import { SegmentButton, SegmentButtonOptions, SegmentButtonItemOptionsArray, TabSegmentButtonOptions, TabSegmentButtonConstructionOptions, CapsuleSegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonTextItem, SegmentButtonIconItem, SegmentButtonIconTextItem, DimensionNoPercentage, CommonSegmentButtonOptions, ItemRestriction, SegmentButtonItemTuple, SegmentButtonItemArray, SegmentButtonItemOptionsConstructorOptions, SegmentButtonItemOptions, BorderRadiusMode } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [SegmentButtonItemOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptions-c.md) | Button options in a segmented button. |
| [SegmentButtonItemOptionsArray](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsarray-c.md) | Represents an array for storing button information. |
| [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) |  |

### Structs

| Name | Description |
| --- | --- |
| [SegmentButton](arkts-arkui-arkui-advanced-segmentbutton-segmentbutton-s.md) | **SegmentButton** is a versatile component that organizes related options into visually grouped buttons. It supports three variants: tab-style, capsule-style single-select, and capsule-style multi-select. |

### Interfaces

| Name | Description |
| --- | --- |
| [CapsuleSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonconstructionoptions-i.md) | Represents configuration options for creating a **SegmentButton** component consisting of capsule-style segmented buttons. |
| [CapsuleSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonoptions-i.md) | Provides configuration options for capsule-style segmented buttons. Inherits from [CapsuleSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonconstructionoptions-i.md). |
| [CommonSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-commonsegmentbuttonoptions-i.md) | Defines the customizable attributes of a segment button component. |
| [SegmentButtonIconItem](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttoniconitem-i.md) | Icon button information. |
| [SegmentButtonIconTextItem](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonicontextitem-i.md) | Icon and text button information. |
| [SegmentButtonItemOptionsConstructorOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsconstructoroptions-i.md) | Construct parameters for SegmentButtonItemOptions. |
| [SegmentButtonTextItem](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttontextitem-i.md) | Text button information. |
| [TabSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonconstructionoptions-i.md) | Creates a SegmentButtonOptions object of the tab type. |
| [TabSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonoptions-i.md) | Provides configuration options for tab-style segmented buttons. Inherits from [TabSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonconstructionoptions-i.md). |

### Enums

| Name | Description |
| --- | --- |
| [BorderRadiusMode](arkts-arkui-arkui-advanced-segmentbutton-borderradiusmode-e.md) | Enumerates the border radius modes for the **SegmentButton** component, which are used to control the border radius calculation method. |

### Types

| Name | Description |
| --- | --- |
| [DimensionNoPercentage](arkts-arkui-dimensionnopercentage-t.md) | The percentage length union type is not supported. |
| [ItemRestriction](arkts-arkui-itemrestriction-t.md) | Tuple type that stores button information. |
| [SegmentButtonItemArray](arkts-arkui-segmentbuttonitemarray-t.md) | Represents the array union type used to store button information. |
| [SegmentButtonItemTuple](arkts-arkui-segmentbuttonitemtuple-t.md) | Represents the tuple union type used to store button information. |

## Examples

```TypeScript
### Example 1: Setting the Type of the SegmentButton component

This example demonstrates how to create two different types of SegmentButton components by configuring SegmentButtonOptions with tab and capsule types.


```

```TypeScript
### Example 2: Setting the Style of the SegmentButton component

Customize the text and background style of the segment button by configuring CommonSegmentButtonOptions.


```

```TypeScript
### Example 3: Performing Array Operations on the SegmentButton Component

This example shows how to perform operations such as adding and removing segment buttons using array functions like pop, shift, and unshift.


```

```TypeScript
### Example 4: Implementing a Mirrored Layout

This example shows how to implement a mirrored layout for a SegmentButton component by configuring direction.


```

```TypeScript
### Example 5: Setting Accessibility

This example showcases how to implement accessibility features for the SegmentButton component by configuring attributes such as accessibilityLevel and selectedIconAccessibilityText.
```

```TypeScript
### Example 6: Setting Custom Border Radius

This example demonstrates how to set a custom border radius for the SegmentButton component.


```

```TypeScript
### Example 7: Enabling Property Animation for SegmentButton

This example demonstrates how to enable property animation for SegmentButton. That is, after enableStateAnimation is set to true, modifying the selectedIndexes value triggers a button switching animation. In addition, two SegmentButton components with the same selectedIndexes value present different switching animations depending on whether property animation is enabled.

Since API version 24, [SegmentButton](#segmentbutton-1) has added the enableStateAnimation attribute.


```

```TypeScript
### Example 8: Setting the Background Material

The following example uses the backgroundSystemMaterial attribute to set a transparent background material for the segment button, enable automatic color inversion and interactive deformation effects, and customize the color of the feedback light effect.

Starting from API version 26.0.0, the backgroundSystemMaterial attribute has been added to [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) and [CommonSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-commonsegmentbuttonoptions-i.md).


```

```TypeScript
### Example 9: Listening for Changes to Properties in SegmentButtonOptions

[SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) uses the @Observed decorator, and the SegmentButton component receives this object through @ObjectLink. For first-level basic type properties of SegmentButtonOptions (such as fontColor and backgroundColor), the linkage mechanism of @Observed and @ObjectLink can already observe property changes and trigger UI refresh without additional processing. However, for internal properties of object-type properties in SegmentButtonOptions (such as width and height of imageSize, or properties of buttonPadding), which are deeper nested properties, @State can only observe first-level assignment changes and cannot detect modifications to such deep properties. As a result, the UI does not automatically refresh when internal properties of object-type properties are modified. Using the makeObserved API to wrap object-type properties (such as imageSize) can add deep observation capability to the internal properties of the object, so that when internal properties (such as width and height) are modified, the framework can detect the changes and trigger UI refresh. For details about the makeObserved API, see [makeObserved API: Changing Unobservable Data to Observable Data](../../../ui/state-management/arkts-new-makeObserved.md).

The following example compares two scenarios: tapping the "Change fontColor" button changes the fontColor property of iconTextCapsuleOptions (a first-level basic type property, already supported for observation through @Observed and @ObjectLink), and the UI automatically refreshes. Tapping the "Change icon size" button changes the width and height properties of iconTextCapsuleOptions.imageSize (internal properties of the imageSize object, which require UIUtils.makeObserved to wrap imageSize for observation), and the UI also automatically refreshes.
```
