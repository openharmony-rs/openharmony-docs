# ToolbarV2StyleOptions

```TypeScript
export interface ToolbarV2StyleOptions
```

Defines the constructor options for ToolbarV2StyleConfigs.

**Since:** 26.1.0

<!--Device-unnamed-export interface ToolbarV2StyleOptions--><!--Device-unnamed-export interface ToolbarV2StyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolbarV2Item, AdvancedToolbarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolbarV2ItemGroupStyle, ToolbarV2ItemGroupStyleOptions, ToolbarV2ItemPlacement, ToolbarV2OverflowMenuStyle, ToolbarV2PaddingOptions, ToolbarV2StyleConfigs, ToolbarV2StyleOptions, ToolbarV2TitleConfigs, ToolbarV2TitleOptions, ToolbarV2TitleStyle, ToolbarV2TitleStyleOptions } from '@kit.ArkUI';
```

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur style of the toolbar.

**Type:** [BlurStyle](../arkts-components/arkts-arkui-common-comp-blurstyle-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleOptions-backgroundBlurStyle?: BlurStyle--><!--Device-ToolbarV2StyleOptions-backgroundBlurStyle?: BlurStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ColorMetrics
```

Background color of the toolbar. Default value: $r('sys.color.comp_background_primary').

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleOptions-backgroundColor?: ColorMetrics--><!--Device-ToolbarV2StyleOptions-backgroundColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundVisibility

```TypeScript
backgroundVisibility?: BarBackgroundVisibility
```

Whether the toolbar background is visible. Default value: BarBackgroundVisibility.VISIBLE.

**Type:** [BarBackgroundVisibility](arkts-arkui-arkui-advanced-toolbarv2-barbackgroundvisibility-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleOptions-backgroundVisibility?: BarBackgroundVisibility--><!--Device-ToolbarV2StyleOptions-backgroundVisibility?: BarBackgroundVisibility-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ColorMetrics
```

Border color of the toolbar. Default value: undefined.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleOptions-borderColor?: ColorMetrics--><!--Device-ToolbarV2StyleOptions-borderColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: LengthMetrics
```

Border radius of the toolbar. Default value: undefined.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleOptions-borderRadius?: LengthMetrics--><!--Device-ToolbarV2StyleOptions-borderRadius?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: LengthMetrics
```

Border width of the toolbar. Default value: undefined.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleOptions-borderWidth?: LengthMetrics--><!--Device-ToolbarV2StyleOptions-borderWidth?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: LengthMetrics
```

Font size of the toolbar item text. Default value: $r('sys.float.ohos_id_text_size_caption').

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleOptions-fontSize?: LengthMetrics--><!--Device-ToolbarV2StyleOptions-fontSize?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## groupSpace

```TypeScript
groupSpace?: LengthMetrics
```

Spacing between item groups. Default value: 12vp, value range [8vp, 20vp], clamped to the boundary when out of range.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleOptions-groupSpace?: LengthMetrics--><!--Device-ToolbarV2StyleOptions-groupSpace?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSize

```TypeScript
itemSize?: Size
```

Item size of the toolbar items. Default value: mainAxis 56vp x crossAxis 48vp. When horizontal: 56vp(width) x 48vp(height). When vertical: 48vp(width) x 56vp(height).

**Type:** Size

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleOptions-itemSize?: Size--><!--Device-ToolbarV2StyleOptions-itemSize?: Size-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## padding

```TypeScript
padding?: ToolbarV2PaddingOptions
```

Toolbar padding. Each edge can be set independently. Default value: undefined.

**Type:** [ToolbarV2PaddingOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2paddingoptions-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleOptions-padding?: ToolbarV2PaddingOptions--><!--Device-ToolbarV2StyleOptions-padding?: ToolbarV2PaddingOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stateEffect

```TypeScript
stateEffect?: boolean
```

Whether to enable the state effect. Default value: true.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleOptions-stateEffect?: boolean--><!--Device-ToolbarV2StyleOptions-stateEffect?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
