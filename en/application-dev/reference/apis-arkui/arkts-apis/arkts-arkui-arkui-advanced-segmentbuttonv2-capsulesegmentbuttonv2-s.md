# CapsuleSegmentButtonV2

```TypeScript
export declare struct CapsuleSegmentButtonV2
```

The segmented button component is used to create tab-type, single-selection, or multi-selection capsule segmented buttons. It supports multiple option types such as text, icons, and symbols, as well as graphic-text hybrid configurations, and allows customization of fonts, colors, corner radii, and other styles. The tab segmented button is suitable for tab switching scenarios, the single-selection capsule segmented button is suitable for single- selection switching scenarios, and the multi-selection capsule segmented button is suitable for multi-selection filtering scenarios.

> **NOTE:** 
> 
> Since API version 26.0.0, when **backgroundSystemMaterial** is set to a system material with automatic color
> inversion, **itemFontColor**, **itemSelectedFontColor**, **itemIconFillColor**,
> **itemSelectedIconFillColor**, **itemSymbolFontColor**, and **itemSelectedSymbolFontColor** use special
> system resources that support color inversion, and the colors automatically adapt to the inverted color of the
> material background.

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

Callback invoked when the selected item of the segmented button changes.

Default value: **undefined**, meaning the callback is not triggered when not set.

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

System material of the background of the segmented button component. Different system materials have different attribute effects. After a material is passed in, the animation effect of **SegmentButtonV2** changes.

When a system material is used, the segmented button supports the capability of the background of the selected item following the finger drag. The index of the selected item remains unchanged during the drag and is updated when the drag ends.

Default value: no material effect.

This member is read-only and cannot be changed.

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonBackgroundBlurStyle

```TypeScript
readonly buttonBackgroundBlurStyle?: BlurStyle
```

Blur material of the segmented button background.

Default value: **undefined**

This member is read-only and cannot be changed.

**Type:** [BlurStyle](../arkts-components/arkts-arkui-common-comp-blurstyle-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonBackgroundBlurStyleOptions

```TypeScript
readonly buttonBackgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Blur material parameters of the segmented button background.

Default value: **undefined**

This member is read-only and cannot be changed.

**Type:** [BackgroundBlurStyleOptions](../arkts-components/arkts-arkui-common-comp-backgroundblurstyleoptions-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonBackgroundColor

```TypeScript
readonly buttonBackgroundColor?: ColorMetrics
```

Background color of the segmented button.

Default value: `$r('sys.color.segment_button_v2_tab_button_background')`

When the value is **undefined**, the default value is used.

This member is read-only and cannot be changed.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonBackgroundEffect

```TypeScript
readonly buttonBackgroundEffect?: BackgroundEffectOptions
```

Background effect parameters of the segmented button.

Default value: **undefined**

This member is read-only and cannot be changed.

**Type:** [BackgroundEffectOptions](../arkts-components/arkts-arkui-common-comp-backgroundeffectoptions-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonBorderRadius

```TypeScript
readonly buttonBorderRadius?: LengthMetrics
```

Corner radius of the segmented button background.

Value range: [0, +∞)

Default value: `$r('sys.float.segment_button_v2_background_corner_radius')`

If the value is out of range, the default value is used.

This member is read-only and cannot be changed.

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

Default value: when there are only text-only or icon-only options: `$r('sys.float.segment_button_v2_singleline_background_height')`; when there are mixed icon and text items: `$r('sys.float.segment_button_v2_doubleline_background_height')`

If the value is out of range, the default value is used.

This member is read-only and cannot be changed.

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

Default value: `$r('sys.float.padding_level1')`

If the value is out of range, the default value is used.

This member is read-only and cannot be changed.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableStateAnimation

```TypeScript
readonly enableStateAnimation?: boolean
```

Whether to enable the attribute animation of the segmented button when the **selectedIndex** value is modified through a variable.

The value **true** means to enable the attribute animation of the segmented button; when this attribute is not configured or the value is **false**, the attribute animation of the segmented button is not enabled, and the default transition animation effect of the component is used.

Default value: **false**

This member is read-only and cannot be changed.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemBorderRadius

```TypeScript
readonly itemBorderRadius?: LengthMetrics
```

Corner radius of the segmented button item.

Value range: [0, +∞)

Default value: `$r('sys.float.segment_button_v2_selected_corner_radius')`

If the value is out of range, the default value is used.

This member is read-only and cannot be changed.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemFontColor

```TypeScript
readonly itemFontColor?: ColorMetrics
```

Font color of the unselected option in the segmented button.

Default value: `$r('sys.color.font_secondary')`

When the value is **undefined**, the default value is used.

**Note:** 

When **items** sets the **textModifier**\/**fontColor** attribute, **itemFontColor** does not take effect.

When **backgroundSystemMaterial** is set to a system material with automatic color inversion, this attribute uses a special system resource that supports color inversion, and the color automatically adapts to the inverted color of the material background.

This member is read-only and cannot be changed.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemFontSize

```TypeScript
readonly itemFontSize?: LengthMetrics
```

Font size of the unselected option in the segmented button.

Value range: [0, +∞)

Default value: `14fp`

**Note:** 

Percentage types are not supported. Abnormal values are handled as the default value.

When **items** sets the **textModifier**\/**fontSize** attribute, **itemFontSize** does not take effect.

This member is read-only and cannot be changed.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemFontWeight

```TypeScript
readonly itemFontWeight?: FontWeight
```

Font weight of the unselected option in the segmented button.

Default value: **FontWeight.Medium**

If the value is out of range, the default value is used.

**Note:** 

When **items** sets the **textModifier**\/**fontWeight** attribute, **itemFontWeight** does not take effect.

This member is read-only and cannot be changed.

**Type:** [FontWeight](arkts-arkui-fontweight-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemIconFillColor

```TypeScript
readonly itemIconFillColor?: ColorMetrics
```

Icon color of the unselected option in the segmented button.

Default value: `$r('sys.color.font_secondary')`

When the value is **undefined**, the default value is used.

**Note:** 

When **items** sets the **iconModifier**\/**fillColor** attribute, **itemIconFillColor** does not take effect.

When **backgroundSystemMaterial** is set to a system material with automatic color inversion, this attribute uses a special system resource that supports color inversion, and the color automatically adapts to the inverted color of the material background.

This member is read-only and cannot be changed.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemIconSize

```TypeScript
readonly itemIconSize?: SizeT<LengthMetrics>
```

Size of the image icon in the segmented button item.

Value range: [0, +∞)

Default value: `{ width: LengthMetrics.vp(24), height: LengthMetrics.vp(24) }`

If the value is out of range, the default value is used.

**Note:** 

When **items** sets the **iconModifier**\/**width** or **height** attribute, **itemIconSize** does not take effect.

This member is read-only and cannot be changed.

**Type:** [SizeT](arkts-arkui-graphics-sizet-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt;

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemMaxFontScale

```TypeScript
readonly itemMaxFontScale?: number | Resource
```

Maximum font scale multiplier for the text size of the segmented button item.

Value range: [1, 2]

Default value: **1**

**NOTE:** 

If the set value is less than 1, the value **1** is used. If the set value is greater than 2, the value **2** is used. Abnormal values do not take effect by default.

This member is read-only and cannot be changed.

**Type:** number &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemMinFontScale

```TypeScript
readonly itemMinFontScale?: number | Resource
```

Minimum font scale multiplier for the text size of the segmented button item.

Value range: [0, 1]

Default value: **0**

**NOTE:** 

If the set minimum font scale value is less than 0, the value **0** is used. If the set minimum font scale value is greater than 1, the value **1** is used. Abnormal values do not take effect by default.

This member is read-only and cannot be changed.

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

When there are only text-only or icon-only options: `$r('sys.float.segment_button_v2_singleline_selected_height')`; when there are mixed icon and text items: `$r('sys.float.segment_button_v2_doubleline_selected_height')`

If the value is out of range, the default value is used.

This member is read-only and cannot be changed.

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

Default value: `{ top: LengthMetrics.resource($r('sys.float.padding_level2')), bottom: LengthMetrics.resource($r('sys.float.padding_level2')), start: LengthMetrics.resource($r('sys.float.padding_level4')), end: LengthMetrics.resource($r('sys.float.padding_level4')) }`

When the value is **undefined**, the default value is used.

This member is read-only and cannot be changed.

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

When the value is **undefined**, no item information is displayed.

This member is read-only and cannot be changed.

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

Background color of the selected option in the segmented button.

Default value: `$r('sys.color.comp_background_emphasize')`

When the value is **undefined**, the default value is used.

This member is read-only and cannot be changed.

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

**Note:** 

When **items** sets the **textModifier**\/**fontColor** attribute, **itemSelectedFontColor** does not take effect.

When **backgroundSystemMaterial** is set to a system material with automatic color inversion, this attribute uses a special system resource that supports color inversion, and the color automatically adapts to the inverted color of the material background.

This member is read-only and cannot be changed.

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

**Note:** 

Percentage types are not supported. Abnormal values are handled as the default value.

When **items** sets the **textModifier**\/**fontSize** attribute, **itemSelectedFontSize** does not take effect.

This member is read-only and cannot be changed.

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

If the value is out of range, the default value is used.

**Note:** 

When **items** sets the **textModifier**\/**fontWeight** attribute, **itemSelectedFontWeight** does not take effect.

This member is read-only and cannot be changed.

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

**Note:** 

When **items** sets the **iconModifier**\/**fillColor** attribute, **itemSelectedIconFillColor** does not take effect.

When **backgroundSystemMaterial** is set to a system material with automatic color inversion, this attribute uses a special system resource that supports color inversion, and the color automatically adapts to the inverted color of the material background.

This member is read-only and cannot be changed.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSelectedSymbolFontColor

```TypeScript
readonly itemSelectedSymbolFontColor?: ColorMetrics
```

HM Symbol-type icon color of the selected option in the segmented button.

Default value: `$r('sys.color.font_on_primary')`

When the value is **undefined**, the default value is used.

**Note:** 

When **items** sets the **symbolModifier**\/**fontColor** attribute, **itemSelectedSymbolFontColor** does not take effect.

When **backgroundSystemMaterial** is set to a system material with automatic color inversion, this attribute uses a special system resource that supports color inversion, and the color automatically adapts to the inverted color of the material background.

This member is read-only and cannot be changed.

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

If the value is out of range, the default value is used.

This member is read-only and cannot be changed.

**Type:** [ShadowOptions](../arkts-components/arkts-arkui-common-comp-shadowoptions-i.md) &#124; [ShadowStyle](../arkts-components/arkts-arkui-common-comp-shadowstyle-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSpace

```TypeScript
readonly itemSpace?: LengthMetrics
```

Spacing between segmented button items.

Value range: [0, +∞)

Default value: `LengthMetrics.vp(0)`

**Note:** 

Percentage types are not supported. Abnormal values are handled as the default value.

This member is read-only and cannot be changed.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSymbolFontColor

```TypeScript
readonly itemSymbolFontColor?: ColorMetrics
```

HM Symbol-type icon color of the unselected option in the segmented button.

Default value: `$r('sys.color.font_secondary')`

When the value is **undefined**, the default value is used.

**Note:** 

When **items** sets the **symbolModifier**\/**fontColor** attribute, **itemSymbolFontColor** does not take effect.

When **backgroundSystemMaterial** is set to a system material with automatic color inversion, this attribute uses a special system resource that supports color inversion, and the color automatically adapts to the inverted color of the material background.

This member is read-only and cannot be changed.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSymbolFontSize

```TypeScript
readonly itemSymbolFontSize?: LengthMetrics
```

Size of the HM Symbol-type icon in the segmented button item.

Value range: [0, +∞)

Default value: `20fp`

**Note:** 

Percentage types are not supported. Abnormal values are handled as the default value.

When **items** sets the **symbolModifier**\/**fontSize** attribute, **itemSymbolFontSize** does not take effect.

This member is read-only and cannot be changed.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## languageDirection

```TypeScript
readonly languageDirection?: Direction
```

Layout direction of the segmented button.

Default value: **Direction.Auto**

If the value is out of range, the default value is used.

This member is read-only and cannot be changed.

**Type:** [Direction](arkts-arkui-direction-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onItemClicked

```TypeScript
onItemClicked?: Callback<number>
```

Callback invoked when a segmented button item is clicked. The callback parameter is of the number type, indicating the index of the clicked option. The first item is numbered 0, and subsequent items are numbered sequentially.

Default value: **undefined**, meaning the callback is not triggered when not set.

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

Index of the selected option in the segmented button. The first item is numbered 0, and subsequent items are numbered sequentially.

Value range: [0, items length - 1]

When the value is **undefined**, no option is selected. When a valid value (including **0**) is passed, the option at the corresponding index is selected. When the value is greater than items length - 1, the item at index items length - 1 is selected. When the value is less than 0, the item at index 0 is selected.

This member is read-only and cannot be changed.

**Type:** number

**Since:** 18

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
