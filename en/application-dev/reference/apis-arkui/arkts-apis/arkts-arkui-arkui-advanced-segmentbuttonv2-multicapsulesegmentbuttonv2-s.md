# MultiCapsuleSegmentButtonV2

```TypeScript
export declare struct MultiCapsuleSegmentButtonV2
```

The segmented button component is used to create tab-type, single-selection, or multi-selection capsule segmented buttons. It supports multiple option types such as text, icons, and symbols, as well as graphic-text hybrid configurations, and allows customization of fonts, colors, corner radii, and other styles. The tab segmented button is suitable for tab switching scenarios, the single-selection capsule segmented button is suitable for single- selection switching scenarios, and the multi-selection capsule segmented button is suitable for multi-selection filtering scenarios.

**Since:** 18

**Decorator:** @ComponentV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SegmentButtonV2ItemOptions, OnSelectedIndexChange, OnSelectedIndexesChange, SegmentButtonV2Item, SegmentButtonV2Items, TabSegmentButtonV2, CapsuleSegmentButtonV2, MultiCapsuleSegmentButtonV2 } from '@kit.ArkUI';
```

## $selectedIndexes

```TypeScript
$selectedIndexes: OnSelectedIndexesChange
```

Callback triggered when the selected item of the segmented button changes.

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

## itemBackgroundBlurStyle

```TypeScript
readonly itemBackgroundBlurStyle?: BlurStyle
```

Background blur style of segmented button items.

Default value: **undefined**

This property is read-only.

**Type:** [BlurStyle](../arkts-components/arkts-arkui-common-comp-blurstyle-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemBackgroundBlurStyleOptions

```TypeScript
readonly itemBackgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Background blur style options of segmented button items.

Default value: **undefined**

This property is read-only.

**Type:** [BackgroundBlurStyleOptions](../arkts-components/arkts-arkui-common-comp-backgroundblurstyleoptions-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemBackgroundColor

```TypeScript
readonly itemBackgroundColor?: ColorMetrics
```

Background color of unselected segmented button items.

Default value: **$r('sys.color.segment_button_v2_multi_capsule_button_background')**

If the value is **undefined**, the default value is used.

This property is read-only.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemBackgroundEffect

```TypeScript
readonly itemBackgroundEffect?: BackgroundEffectOptions
```

Background effect of segmented button items.

Default value: **undefined**

This property is read-only.

**Type:** [BackgroundEffectOptions](../arkts-components/arkts-arkui-common-comp-backgroundeffectoptions-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemBorderRadius

```TypeScript
readonly itemBorderRadius?: LengthMetrics
```

Border radius of segmented button items.

Value range: [0, +∞)

Default value: **$r('sys.float.segment_button_v2_multi_corner_radius')**

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

Font color of unselected options in the segmented button.

Default value: `$r('sys.color.font_secondary')`

When the value is **undefined**, the default value is used.

NOTE

When **items** sets the **textModifier**\/**fontColor** attribute, **itemFontColor** does not take effect.

This member is read-only and cannot be modified.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemFontSize

```TypeScript
readonly itemFontSize?: LengthMetrics
```

Font size of unselected options in the segmented button.

Value range: [0, +∞)

Default value: `14fp`

NOTE

Percentage type is not supported. Abnormal values are processed as the default value.

When **items** sets the **textModifier**\/**fontSize** attribute, **itemFontSize** does not take effect.

This member is read-only and cannot be modified.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemFontWeight

```TypeScript
readonly itemFontWeight?: FontWeight
```

Font weight of unselected options in the segmented button.

Default value: **FontWeight.Medium**

Values outside the value range are processed as the default value.

NOTE

When **items** sets the **textModifier**\/**fontWeight** attribute, **itemFontWeight** does not take effect.

This member is read-only and cannot be modified.

**Type:** [FontWeight](arkts-arkui-fontweight-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemIconFillColor

```TypeScript
readonly itemIconFillColor?: ColorMetrics
```

Icon color of unselected options in the segmented button.

Default value: `$r('sys.color.font_secondary')`

When the value is **undefined**, the default value is used.

NOTE

When **items** sets the **iconModifier**\/**fillColor** attribute, **itemIconFillColor** does not take effect.

This member is read-only and cannot be modified.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemIconSize

```TypeScript
readonly itemIconSize?: SizeT<LengthMetrics>
```

Size of image icons in segmented button items.

Value range: [0, +∞)

Default value: `{ width: LengthMetrics.vp(24), height: LengthMetrics.vp(24) }`

Values outside the value range are processed as the default value.

NOTE

When **items** sets the **iconModifier**\/**width** or height attribute, **itemIconSize** does not take effect.

This member is read-only and cannot be modified.

**Type:** [SizeT](arkts-arkui-graphics-sizet-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt;

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemMaxFontScale

```TypeScript
readonly itemMaxFontScale?: number | Resource
```

Maximum font scale factor for the text size of segmented button items.

Value range: [1, 2]

Default value: **1**

NOTE

When the set value is less than 1, the value **1** is used. When the set value is greater than 2, the value **2** is used. Abnormal values do not take effect by default.

This member is read-only and cannot be modified.

**Type:** number &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemMinFontScale

```TypeScript
readonly itemMinFontScale?: number | Resource
```

Minimum font scale factor for the text size of segmented button items.

Value range: [0, 1]

Default value: **0**

NOTE

When the set minimum font scale value is less than 0, the value **0** is used. When the set minimum font scale value is greater than 1, the value **1** is used. Abnormal values do not take effect by default.

This member is read-only and cannot be modified.

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

**$r('sys.float.segment_button_v2_singleline_selected_height')** for text-only buttons and icon-only buttons, and **$r('sys.float.segment_button_v2_doubleline_selected_height')** for text+icon buttons.

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

Default value: **{top: LengthMetrics.resource ($r('sys.float.padding_level2')), bottom: LengthMetrics.resource ($r('sys.float.padding_level2')), start: LengthMetrics.resource($r('sys.float.padding_level4')), end: LengthMetrics.resource($r('sys.float.padding_level4'))}**

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

When the value is **undefined**, no option information is displayed.

This member is read-only and cannot be modified.

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

Default value: **$r('sys.color.comp_background_emphasize')**

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

Font color of the selected option in the segmented button.

Default value: `$r('sys.color.font_on_primary')`

When the value is **undefined**, the default value is used.

NOTE

When **items** sets the **textModifier**\/**fontColor** attribute, **itemSelectedFontColor** does not take effect.

This member is read-only and cannot be modified.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedFontSize

```TypeScript
readonly itemSelectedFontSize?: LengthMetrics
```

Font size of the selected option in the segmented button.

Value range: [0, +∞)

Default value: `14fp`

NOTE

Percentage type is not supported. Abnormal values are processed as the default value.

When **items** sets the **textModifier**\/**fontSize** attribute, **itemSelectedFontSize** does not take effect.

This member is read-only and cannot be modified.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedFontWeight

```TypeScript
readonly itemSelectedFontWeight?: FontWeight
```

Font weight of the selected option in the segmented button.

Default value: **FontWeight.Medium**

Values outside the value range are processed as the default value.

NOTE

When **items** sets the **textModifier**\/**fontWeight** attribute, **itemSelectedFontWeight** does not take effect.

This member is read-only and cannot be modified.

**Type:** [FontWeight](arkts-arkui-fontweight-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedIconFillColor

```TypeScript
readonly itemSelectedIconFillColor?: ColorMetrics
```

Icon color of the selected option in the segmented button.

Default value: `$r('sys.color.font_on_primary')`

When the value is **undefined**, the default value is used.

NOTE

When **items** sets the **iconModifier**\/**fillColor** attribute, **itemSelectedIconFillColor** does not take effect.

This member is read-only and cannot be modified.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedSymbolFontColor

```TypeScript
readonly itemSelectedSymbolFontColor?: ColorMetrics
```

Color of HM Symbol-type icons in the selected option of the segmented button.

Default value: `$r('sys.color.font_on_primary')`

When the value is **undefined**, the default value is used.

NOTE

When **items** sets the **symbolModifier**\/**fontColor** attribute, **itemSelectedSymbolFontColor** does not take effect.

This member is read-only and cannot be modified.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

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

Default value: **LengthMetrics.vp(1)**

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

Color of HM Symbol-type icons in unselected options of the segmented button.

Default value: `$r('sys.color.font_secondary')`

When the value is **undefined**, the default value is used.

NOTE

When **items** sets the **symbolModifier**\/**fontColor** attribute, **itemSymbolFontColor** does not take effect.

This member is read-only and cannot be modified.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSymbolFontSize

```TypeScript
readonly itemSymbolFontSize?: LengthMetrics
```

Size of HM Symbol-type icons in segmented button items.

Value range: [0, +∞)

Default value: `20fp`

NOTE

Percentage type is not supported. Abnormal values are processed as the default value.

When **items** sets the **symbolModifier**\/**fontSize** attribute, **itemSymbolFontSize** does not take effect.

This member is read-only and cannot be modified.

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

Callback triggered when a segmented button item is clicked. The callback parameter is of the number type, indicating the index of the clicked option. The first item is numbered 0, and subsequent items are numbered sequentially.

Default value: **undefined**. When not set, the callback is not triggered.

**Type:** Callback&lt;number&gt;

**Since:** 18

**Decorator:** @Event

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedIndexes

```TypeScript
readonly selectedIndexes: number[]
```

Indexes for the selected items of the segmented button. The first item is numbered 0, and subsequent items are numbered sequentially.

When the value is **undefined**, no option is selected.

NOTE

Only valid button numbers are supported (the first button is numbered 0, and subsequent buttons are numbered sequentially. Value range: [0, items length - 1]). If no item is selected, an empty array `[]` can be passed. When an invalid number (less than 0 or greater than items length - 1) is passed, the corresponding option is not selected.

This member is read-only and cannot be modified.

**Type:** number[]

**Since:** 18

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
