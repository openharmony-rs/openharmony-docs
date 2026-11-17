# ToolBarV2TitleStyle

```TypeScript
export declare class ToolBarV2TitleStyle
```

标题文本样式配置。

**Since:** 26.1.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class ToolBarV2TitleStyle--><!--Device-unnamed-export declare class ToolBarV2TitleStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolBarV2Item, AdvancedToolBarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolBarV2ItemGroupStyle, ToolBarV2ItemGroupStyleOptions, ToolBarV2ItemPlacement, ToolBarV2OverflowMenuStyle, ToolBarV2PaddingOptions, ToolBarV2StyleConfigs, ToolBarV2StyleOptions, ToolBarV2TitleConfigs, ToolBarV2TitleOptions, ToolBarV2TitleStyle, ToolBarV2TitleStyleOptions, ToolBarV2MaterialStyle } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ToolBarV2TitleStyleOptions)
```

构造ToolBarV2TitleStyle实例。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2TitleStyle-constructor(options?: ToolBarV2TitleStyleOptions)--><!--Device-ToolBarV2TitleStyle-constructor(options?: ToolBarV2TitleStyleOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ToolBarV2TitleStyleOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2titlestyleoptions-i.md) | No | 构造函数选项。 |

## fontColor

```TypeScript
fontColor?: ColorMetrics
```

标题文本颜色。默认值：undefined。值为undefined或不设置时，标题文本的默认颜色为$r('sys.color.font_primary')，副标题文本的默认颜色为$r('sys.color.font_secondary')。

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2TitleStyle-fontColor?: ColorMetrics--><!--Device-ToolBarV2TitleStyle-fontColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: LengthMetrics
```

标题文本的字体大小。默认值为：undefined。值为undefined或不设置时，标题文本的默认颜色字体大小为20fp，副标题文本的默认颜色字体大小为14fp。

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2TitleStyle-fontSize?: LengthMetrics--><!--Device-ToolBarV2TitleStyle-fontSize?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: FontWeight
```

标题文本字重。默认值：undefined。值为undefined或不设置时，标题文本的默认颜色字重为FontWeight.Bold，副标题文本的默认颜色字重为FontWeight.Regular。

**Type:** [FontWeight](arkts-arkui-fontweight-e.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2TitleStyle-fontWeight?: FontWeight--><!--Device-ToolBarV2TitleStyle-fontWeight?: FontWeight-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minLength

```TypeScript
minLength?: LengthMetrics
```

标题最小长度。默认值：undefined。值为undefined或不设置时默认为48vp。

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2TitleStyle-minLength?: LengthMetrics--><!--Device-ToolBarV2TitleStyle-minLength?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
