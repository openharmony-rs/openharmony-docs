# ToolbarV2TitleStyle

```TypeScript
export declare class ToolbarV2TitleStyle
```

Title text style configuration.

**Since:** 26.1.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class ToolbarV2TitleStyle--><!--Device-unnamed-export declare class ToolbarV2TitleStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolbarV2Item, AdvancedToolbarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolbarV2ItemGroupStyle, ToolbarV2ItemGroupStyleOptions, ToolbarV2ItemPlacement, ToolbarV2OverflowMenuStyle, ToolbarV2PaddingOptions, ToolbarV2StyleConfigs, ToolbarV2StyleOptions, ToolbarV2TitleConfigs, ToolbarV2TitleOptions, ToolbarV2TitleStyle, ToolbarV2TitleStyleOptions } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ToolbarV2TitleStyleOptions)
```

Constructs a ToolbarV2TitleStyle instance.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2TitleStyle-constructor(options?: ToolbarV2TitleStyleOptions)--><!--Device-ToolbarV2TitleStyle-constructor(options?: ToolbarV2TitleStyleOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ToolbarV2TitleStyleOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2titlestyleoptions-i.md) | No | Constructor options. |

## fontColor

```TypeScript
fontColor?: ColorMetrics
```

Title text color. Default value: $r('sys.color.font_primary').

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2TitleStyle-fontColor?: ColorMetrics--><!--Device-ToolbarV2TitleStyle-fontColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: LengthMetrics
```

Font size of the title text. Default value: 20fp.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2TitleStyle-fontSize?: LengthMetrics--><!--Device-ToolbarV2TitleStyle-fontSize?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: FontWeight
```

Font weight of the title text. Default value: FontWeight.Bold.

**Type:** [FontWeight](arkts-arkui-fontweight-e.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2TitleStyle-fontWeight?: FontWeight--><!--Device-ToolbarV2TitleStyle-fontWeight?: FontWeight-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minLength

```TypeScript
minLength?: LengthMetrics
```

Minimum width of the title. Default value: 48vp.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolbarV2TitleStyle-minLength?: LengthMetrics--><!--Device-ToolbarV2TitleStyle-minLength?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
