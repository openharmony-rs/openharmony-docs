# ToolbarV2StyleConfigs

```TypeScript
export declare class ToolbarV2StyleConfigs
```

Defines the style configuration for the toolbar.

**Since:** 26.1.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class ToolbarV2StyleConfigs--><!--Device-unnamed-export declare class ToolbarV2StyleConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolbarV2Item, AdvancedToolbarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolbarV2ItemGroupStyle, ToolbarV2ItemGroupStyleOptions, ToolbarV2ItemPlacement, ToolbarV2OverflowMenuStyle, ToolbarV2PaddingOptions, ToolbarV2StyleConfigs, ToolbarV2StyleOptions, ToolbarV2TitleConfigs, ToolbarV2TitleOptions, ToolbarV2TitleStyle, ToolbarV2TitleStyleOptions } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ToolbarV2StyleOptions)
```

Constructs a ToolbarV2StyleConfigs instance.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleConfigs-constructor(options?: ToolbarV2StyleOptions)--><!--Device-ToolbarV2StyleConfigs-constructor(options?: ToolbarV2StyleOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ToolbarV2StyleOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2styleoptions-i.md) | No | Constructor options. |

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur style of the toolbar. Default value: undefined.

**Type:** [BlurStyle](../arkts-components/arkts-arkui-common-comp-blurstyle-e.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleConfigs-backgroundBlurStyle?: BlurStyle--><!--Device-ToolbarV2StyleConfigs-backgroundBlurStyle?: BlurStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ColorMetrics
```

Background color of the toolbar. Default value: $r('sys.color.comp_background_primary').

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleConfigs-backgroundColor?: ColorMetrics--><!--Device-ToolbarV2StyleConfigs-backgroundColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundVisibility

```TypeScript
backgroundVisibility?: BarBackgroundVisibility
```

Whether the toolbar background is visible. Default value: BarBackgroundVisibility.VISIBLE.

**Type:** [BarBackgroundVisibility](arkts-arkui-arkui-advanced-toolbarv2-barbackgroundvisibility-e.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleConfigs-backgroundVisibility?: BarBackgroundVisibility--><!--Device-ToolbarV2StyleConfigs-backgroundVisibility?: BarBackgroundVisibility-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ColorMetrics
```

Border color of the toolbar. Default value: undefined.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleConfigs-borderColor?: ColorMetrics--><!--Device-ToolbarV2StyleConfigs-borderColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: LengthMetrics
```

Border radius of the toolbar. Default value: undefined.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleConfigs-borderRadius?: LengthMetrics--><!--Device-ToolbarV2StyleConfigs-borderRadius?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: LengthMetrics
```

Border width of the toolbar. Default value: undefined.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleConfigs-borderWidth?: LengthMetrics--><!--Device-ToolbarV2StyleConfigs-borderWidth?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: LengthMetrics
```

Font size of the toolbar item text. Default value: $r('sys.float.ohos_id_text_size_caption').

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleConfigs-fontSize?: LengthMetrics--><!--Device-ToolbarV2StyleConfigs-fontSize?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## groupSpace

```TypeScript
groupSpace?: LengthMetrics
```

Spacing between item groups. Default value: 12vp, value range [8vp, 20vp], clamped to the boundary when out of range.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleConfigs-groupSpace?: LengthMetrics--><!--Device-ToolbarV2StyleConfigs-groupSpace?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSize

```TypeScript
itemSize?: Size
```

Item size of the toolbar items. Default value: mainAxis 56vp x crossAxis 48vp. When horizontal: 56vp(width) x 48vp(height). When vertical: 48vp(width) x 56vp(height).

**Type:** Size

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleConfigs-itemSize?: Size--><!--Device-ToolbarV2StyleConfigs-itemSize?: Size-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## padding

```TypeScript
padding?: ToolbarV2PaddingOptions
```

Toolbar padding. Each edge can be set independently. Default value: undefined.

**Type:** [ToolbarV2PaddingOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2paddingoptions-i.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2StyleConfigs-padding?: ToolbarV2PaddingOptions--><!--Device-ToolbarV2StyleConfigs-padding?: ToolbarV2PaddingOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
