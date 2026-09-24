# SegmentButton

```TypeScript
declare struct SegmentButton
```

The segment button component includes tab-style segment buttons and capsule-style segment buttons. Tab-style segment buttons are suitable for switching between pages or content areas. Capsule-style segment buttons are suitable for single-select or multi-select scenarios, including capsule-style single-select segment buttons and capsule-style multi-select segment buttons. This component supports custom appearance attributes such as text color, font size, font weight, background color, image size, padding, and background blur material. It supports three button styles: text-only, icon-only, and icon + text. It also provides capabilities such as accessibility reading, layout direction mirroring, custom rounded corners, and property animation, making it suitable for scenarios where you need to quickly build a segmented selection interface that complies with design specifications.

> **NOTE:** 
> 
> - The segment button does not support [universal attributes](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md). The segment button uses the maximum available width in the current area as the component width, and evenly distributes the width among the buttons based on the number of buttons. The segment button height automatically adapts to the button content (text and images), with a minimum height of 28 vp.
> 
> - Attributes decorated by **@Prop** are optional parameters. They must be passed during construction only when used together with the **@Require** decorator.

**Since:** 11

**Decorator:** @Component

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SegmentButton, SegmentButtonOptions, SegmentButtonItemOptionsArray, TabSegmentButtonOptions, TabSegmentButtonConstructionOptions, CapsuleSegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonTextItem, SegmentButtonIconItem, SegmentButtonIconTextItem, DimensionNoPercentage, CommonSegmentButtonOptions, ItemRestriction, SegmentButtonItemTuple, SegmentButtonItemArray, SegmentButtonItemOptionsConstructorOptions, SegmentButtonItemOptions, BorderRadiusMode } from '@kit.ArkUI';
```

## enableStateAnimation

```TypeScript
enableStateAnimation: boolean
```

Whether to enable the attribute animation of the segment button when the **selectedIndexes** value is modified through a variable.

The value **true** means to enable the attribute animation of the segment button, and **false** means the opposite.

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 24

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxFontScale

```TypeScript
maxFontScale: number | Resource
```

Maximum font scale factor for the segment button option text, used to limit the upper bound of font scaling. Pass in this parameter when you need to control the font scale factor to fit a specific UI layout or avoid excessively large text.

Value range: [1, 2]

If the set value is less than 1, the value **1** is used. If the set value is greater than 2, the value **2** is used.

Default value: **1**

**Type:** number &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 14

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onItemClicked

```TypeScript
onItemClicked?: Callback<number>
```

Callback invoked when a segment button option is clicked. It receives the index of the clicked option as a parameter. If this parameter is not passed in, no callback is triggered upon clicking.

**Type:** Callback&lt;number&gt;

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: SegmentButtonOptions
```

Configuration options of the segment button, used to set the button type (tab type or capsule type), appearance style (color, font, size, etc.), button content, selected state, and other attributes.

**Type:** [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md)

**Since:** 11

**Decorator:** @ObjectLink

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedIndexes

```TypeScript
selectedIndexes: number[]
```

Index of the selected item in the segment button. The index of the first item is 0, and subsequent items are numbered sequentially.

**NOTE:** 

`selectedIndexes` uses the [@Link decorator: two-way synchronization between parent and child](../../../ui/state-management/arkts-link.md). Only valid button indexes are supported (the first button index is 0, and subsequent indexes increase sequentially, with the maximum index being the number of buttons minus 1). If an invalid index is passed in, it does not take effect. If no item is selected, an empty array `[]` can be passed in.

**Type:** number[]

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
