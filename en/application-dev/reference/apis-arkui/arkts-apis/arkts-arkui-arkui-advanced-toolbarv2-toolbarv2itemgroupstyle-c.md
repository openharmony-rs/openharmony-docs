# ToolBarV2ItemGroupStyle

```TypeScript
export declare class ToolBarV2ItemGroupStyle
```

定义工具栏项组的样式配置。

**Since:** 26.1.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class ToolBarV2ItemGroupStyle--><!--Device-unnamed-export declare class ToolBarV2ItemGroupStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolBarV2Item, AdvancedToolBarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolBarV2ItemGroupStyle, ToolBarV2ItemGroupStyleOptions, ToolBarV2ItemPlacement, ToolBarV2OverflowMenuStyle, ToolBarV2PaddingOptions, ToolBarV2StyleConfigs, ToolBarV2StyleOptions, ToolBarV2TitleConfigs, ToolBarV2TitleOptions, ToolBarV2TitleStyle, ToolBarV2TitleStyleOptions, ToolBarV2MaterialStyle } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ToolBarV2ItemGroupStyleOptions)
```

构造ToolBarV2ItemGroupStyle实例。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2ItemGroupStyle-constructor(options?: ToolBarV2ItemGroupStyleOptions)--><!--Device-ToolBarV2ItemGroupStyle-constructor(options?: ToolBarV2ItemGroupStyleOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ToolBarV2ItemGroupStyleOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemgroupstyleoptions-i.md) | No | 构造函数选项。 |

## backgroundColor

```TypeScript
backgroundColor?: ColorMetrics
```

组容器的背景颜色。默认值：undefined。值为undefined或不设置时，值为$r('sys.color.comp_background_primary').

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2ItemGroupStyle-backgroundColor?: ColorMetrics--><!--Device-ToolBarV2ItemGroupStyle-backgroundColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ColorMetrics
```

组容器的圆角颜色。默认值：undefined。值为undefined或不设置时，默认无颜色。

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2ItemGroupStyle-borderColor?: ColorMetrics--><!--Device-ToolBarV2ItemGroupStyle-borderColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: LengthMetrics
```

组容器的边界边框圆角半径。默认值：undefined。值为undefined或不设置时，默认值为工具栏交叉轴长度的一半。

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2ItemGroupStyle-borderRadius?: LengthMetrics--><!--Device-ToolBarV2ItemGroupStyle-borderRadius?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: LengthMetrics
```

组容器的边框宽度。默认值：undefined。值为undefined或不设置时，默认无宽度。

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2ItemGroupStyle-borderWidth?: LengthMetrics--><!--Device-ToolBarV2ItemGroupStyle-borderWidth?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## padding

```TypeScript
padding?: ToolBarV2PaddingOptions
```

group容器的Padding。默认值：undefined。值为undefined或不设置时，默认值为12vp。

**Type:** [ToolBarV2PaddingOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2paddingoptions-i.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2ItemGroupStyle-padding?: ToolBarV2PaddingOptions--><!--Device-ToolBarV2ItemGroupStyle-padding?: ToolBarV2PaddingOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placement

```TypeScript
placement?: ToolBarV2ItemPlacement
```

组在工具栏中的放置位置。组放置优先于组中单个项目的放置。默认值：ToolBarV2ItemPlacement.MAIN。

**Type:** [ToolBarV2ItemPlacement](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemplacement-e.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2ItemGroupStyle-placement?: ToolBarV2ItemPlacement--><!--Device-ToolBarV2ItemGroupStyle-placement?: ToolBarV2ItemPlacement-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: LengthMetrics
```

组内项目之间的间距。默认值：0vp。

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2ItemGroupStyle-space?: LengthMetrics--><!--Device-ToolBarV2ItemGroupStyle-space?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stateEffect

```TypeScript
stateEffect?: boolean
```

是否显示组内项目的按压状态效果。默认值：true。

**Type:** boolean

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2ItemGroupStyle-stateEffect?: boolean--><!--Device-ToolBarV2ItemGroupStyle-stateEffect?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
