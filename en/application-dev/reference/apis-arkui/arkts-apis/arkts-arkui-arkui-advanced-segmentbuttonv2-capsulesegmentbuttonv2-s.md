# CapsuleSegmentButtonV2

Defines the segmented button with capsule style.

**Since:** 18

**Decorator:** @ComponentV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SegmentButtonV2ItemOptions, OnSelectedIndexChange, OnSelectedIndexesChange, SegmentButtonV2Item, SegmentButtonV2Items, TabSegmentButtonV2, CapsuleSegmentButtonV2, MultiCapsuleSegmentButtonV2 } from '@kit.ArkUI';
```

## $selectedIndex

```TypeScript
$selectedIndex?: OnSelectedIndexChange
```

Callback invoked when the selected item changes.

**Since:** 18

**Decorator:** @Event

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
build(): void
```

Sets the build function of the segmented button.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
readonly backgroundSystemMaterial?: uiMaterial.Material
```

Set system-styled materials for the component. Different materials have different effects, which can influence the backgroundColor, border, shadow, and other visual attributes of the component.

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonBackgroundBlurStyle

```TypeScript
readonly buttonBackgroundBlurStyle?: BlurStyle
```

Background blur style of the segmented button.

Default value: **undefined**

This property is read-only.

**Type:** [BlurStyle](../arkts-components/arkts-arkui-blurstyle-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonBackgroundBlurStyleOptions

```TypeScript
readonly buttonBackgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Background blur style options of the segmented button.

Default value: **undefined**

This property is read-only.

**Type:** [BackgroundBlurStyleOptions](../arkts-components/arkts-arkui-backgroundblurstyleoptions-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonBackgroundColor

```TypeScript
readonly buttonBackgroundColor?: ColorMetrics
```

Background color of the segmented button.

Default value: **&#36;r('sys.color.segment_button_v2_tab_button_background')**

If the value is **undefined**, the default value is used.

This property is read-only.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonBackgroundEffect

```TypeScript
readonly buttonBackgroundEffect?: BackgroundEffectOptions
```

Background blur effect options of the segmented button.

Default value: **undefined**

This property is read-only.

**Type:** [BackgroundEffectOptions](../arkts-components/arkts-arkui-backgroundeffectoptions-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonBorderRadius

```TypeScript
readonly buttonBorderRadius?: LengthMetrics
```

Background border radius of the segmented button.

Value range: [0, +∞)

Default value: **&#36;r('sys.float.segment_button_v2_background_corner_radius')**

If the value is out of the range, the default value is used.

This property is read-only.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonMinHeight

```TypeScript
readonly buttonMinHeight?: LengthMetrics
```

Minimum height of the segmented button.

Value range: [0, +∞)

Default value: **&#36;r('sys.float.segment_button_v2_singleline_background_height')** for text-only buttons and icon- only buttons, and **&#36;r('sys.float.segment_button_v2_doubleline_background_height')** for buttons with both an icon and text.

If the value is out of the range, the default value is used.

This property is read-only.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonPadding

```TypeScript
readonly buttonPadding?: LengthMetrics
```

Padding of the segmented button.

Value range: [0, +∞)

Default value: **&#36;r('sys.float.padding_level1')**

If the value is out of the range, the default value is used.

This property is read-only.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableStateAnimation

```TypeScript
readonly enableStateAnimation?: boolean
```

Enable animation when selectedIndexes change.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemBorderRadius

```TypeScript
readonly itemBorderRadius?: LengthMetrics
```

Border radius of segmented button items.

Value range: [0, +∞)

Default value: **&#36;r('sys.float.segment_button_v2_selected_corner_radius')**.

If the value is out of the range, the default value is used.

This property is read-only.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemFontColor

```TypeScript
readonly itemFontColor?: ColorMetrics
```

Font color of the selected segmented button item.

Default value: **&#36;r('sys.color.font_primary')**.

If the value is **undefined**, the default value is used.

**NOTE:** 

When **fontColor** of **textModifier** is set for **items**, **itemSelectedFontColor** has no effect.

This property is read-only.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemFontSize

```TypeScript
readonly itemFontSize?: LengthMetrics
```

Font size of unselected segmented button items.

Value range: [0, +∞)

Default value: **14fp**

**NOTE:** 

Percentage values are not supported. If an invalid value is set, the default value is used.

When **fontSize** of **textModifier** is set for **items**, **itemFontSize** has no effect.

This property is read-only.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemFontWeight

```TypeScript
readonly itemFontWeight?: FontWeight
```

Font weight of unselected segmented button items.

Default value: **FontWeight.Medium**

If the value is out of the range, the default value is used.

**NOTE:** 

When **fontWeight** of **textModifier** is set for **items**, **itemFontWeight** has no effect.

This property is read-only.

**Type:** [FontWeight](arkts-arkui-fontweight-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemIconFillColor

```TypeScript
readonly itemIconFillColor?: ColorMetrics
```

Icon color of unselected segmented button items.

Default value: **&#36;r('sys.color.font_secondary')**

If the value is **undefined**, the default value is used.

**NOTE:** 

When **fillColor** of **iconModifier** is set for **items**, **itemIconFillColor** has no effect.

This property is read-only.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemIconSize

```TypeScript
readonly itemIconSize?: SizeT<LengthMetrics>
```

Image-type icon size of segmented button items.

Value range: [0, +∞)

Default value: **{ width: LengthMetrics.vp(24), height: LengthMetrics.vp(24) }**.

If the value is out of the range, the default value is used.

**NOTE:** 

When **width** and **height** of **iconModifier** are set for **items**, **itemIconSize** has no effect.

This property is read-only.

**Type:** [SizeT](arkts-arkui-graphics-sizet-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt;

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemMaxFontScale

```TypeScript
readonly itemMaxFontScale?: number | Resource
```

Maximum font scale factor of the segmented button item text.

Value range: [1, 2]

Default value: **1**

**NOTE:** 

A value less than 1 is treated as **1**. A value greater than 2 is treated as **2**. Abnormal values are ineffective by default.

This property is read-only.

**Type:** number &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemMinFontScale

```TypeScript
readonly itemMinFontScale?: number | Resource
```

Minimum font scale factor of the segmented button item text.

Value range: [0, 1]

Default value: **0**

**NOTE:** 

A value less than 0 is treated as **0**. A value greater than 1 is treated as **1**. Abnormal values are ineffective by default.

This property is read-only.

**Type:** number &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemMinHeight

```TypeScript
readonly itemMinHeight?: LengthMetrics
```

Minimum height of the segmented button item.

Value range: [0, +∞)

Default value:

**&#36;r('sys.float.segment_button_v2_singleline_selected_height')** for text-only buttons and icon-only buttons, and **&#36;r('sys.float.segment_button_v2_doubleline_selected_height')** for buttons with both an icon and text.

If the value is out of the range, the default value is used.

This property is read-only.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemPadding

```TypeScript
readonly itemPadding?: LocalizedPadding
```

Padding of the segmented button item.

Default value: **{top: LengthMetrics.resource (&#36;r('sys.float.padding_level2')), bottom: LengthMetrics. resource (&#36;r('sys.float.padding_level2')), start: LengthMetrics.resource(&#36;r('sys.float.padding_level4')), end: LengthMetrics.resource(&#36;r('sys.float.padding_level4'))}**

If the value is **undefined**, the default value is used.

This property is read-only.

**Type:** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
readonly items: SegmentButtonV2Items
```

Items of the segmented button.

If the value is **undefined**, the option information is not displayed.

This property is read-only.

**Type:** [SegmentButtonV2Items](arkts-arkui-arkui-advanced-segmentbuttonv2-segmentbuttonv2items-c.md)

**Since:** 18

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedBackgroundColor

```TypeScript
readonly itemSelectedBackgroundColor?: ColorMetrics
```

Background color of the selected segmented button item.

Default value: **&#36;r('sys.color.segment_button_v2_tab_selected_item_background')**

If the value is **undefined**, the default value is used.

This property is read-only.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedFontColor

```TypeScript
readonly itemSelectedFontColor?: ColorMetrics
```

Font color of the selected segmented button item.

Default value: **&#36;r('sys.color.font_primary')**.

If the value is **undefined**, the default value is used.

**NOTE:** 

When **fontColor** of **textModifier** is set for **items**, **itemSelectedFontColor** has no effect.

This property is read-only.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedFontSize

```TypeScript
readonly itemSelectedFontSize?: LengthMetrics
```

Font size of the selected segmented button item.

Value range: [0, +∞)

Default value: **14fp**

**NOTE:** 

Percentage values are not supported. If an invalid value is set, the default value is used.

When **fontSize** of **textModifier** is set for **items**, **itemSelectedFontSize** has no effect.

This property is read-only.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedFontWeight

```TypeScript
readonly itemSelectedFontWeight?: FontWeight
```

Font weight of the selected segmented button item.

Default value: **FontWeight.Medium**

If the value is out of the range, the default value is used.

**NOTE:** 

When **fontWeight** of **textModifier** is set for **items**, **itemSelectedFontWeight** has no effect.

This property is read-only.

**Type:** [FontWeight](arkts-arkui-fontweight-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedIconFillColor

```TypeScript
readonly itemSelectedIconFillColor?: ColorMetrics
```

Icon color of the selected segmented button item.

Default value: **&#36;r('sys.color.font_primary')**

If the value is **undefined**, the default value is used.

**NOTE:** 

When **fillColor** of **iconModifier** is set for **items**, **itemSelectedIconFillColor** has no effect.

This property is read-only.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedSymbolFontColor

```TypeScript
readonly itemSelectedSymbolFontColor?: ColorMetrics
```

HM Symbol icon color of the selected segmented button item.

Default value: **&#36;r('sys.color.font_primary')**

If the value is **undefined**, the default value is used.

**NOTE:** 

When **fontColor** of **symbolModifier** is set for **items**, **itemSelectedSymbolFontColor** has no effect.

This property is read-only.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemShadow

```TypeScript
readonly itemShadow?: ShadowOptions | ShadowStyle
```

Shadow of the segmented button item.

Default value: **ShadowStyle.OUTER_DEFAULT_XS**

If the value is out of the range, the default value is used.

This property is read-only.

**Type:** [ShadowOptions](../arkts-components/arkts-arkui-shadowoptions-i.md) &#124; [ShadowStyle](../arkts-components/arkts-arkui-shadowstyle-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSpace

```TypeScript
readonly itemSpace?: LengthMetrics
```

Space between segmented button items.

Value range: [0, +∞)

Default value: **LengthMetrics.vp(0)**

**NOTE:** 

Percentage values are not supported. If an invalid value is set, the default value is used.

This property is read-only.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSymbolFontColor

```TypeScript
readonly itemSymbolFontColor?: ColorMetrics
```

HM Symbol icon color of unselected segmented button items.

Default value: **&#36;r('sys.color.font_secondary')**

If the value is **undefined**, the default value is used.

**NOTE:** 

When **fontColor** of **symbolModifier** is set for **items**, **itemSymbolFontColor** has no effect.

This property is read-only.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSymbolFontSize

```TypeScript
readonly itemSymbolFontSize?: LengthMetrics
```

HM Symbol icon size of segmented button items.

Value range: [0, +∞)

Default value: **20fp**

**NOTE:** 

Percentage values are not supported. If an invalid value is set, the default value is used.

When **fontSize** of **symbolModifier** is set for **items**, **itemSymbolFontSize** has no effect.

This property is read-only.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## languageDirection

```TypeScript
readonly languageDirection?: Direction
```

Language direction of the segmented button.

Default value: **Direction.Auto**

If the value is out of the range, the default value is used.

This property is read-only.

**Type:** [Direction](arkts-arkui-direction-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onItemClicked

```TypeScript
onItemClicked?: Callback<number>
```

Callback invoked when a segmented button item is clicked.

**Type:** Callback&lt;number&gt;

**Since:** 18

**Decorator:** @Event

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedIndex

```TypeScript
readonly selectedIndex: number
```

Index of the selected segmented button item. The index is zero-based and increments by 1.

If the value is undefined, no item is selected. If the value is a non-positive value, the default value **0** is used.

This property is read-only.

**Type:** number

**Since:** 18

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
