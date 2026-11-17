# ToolBarV2ItemImage

```TypeScript
export declare class ToolBarV2ItemImage
```

定义工具栏子项的普通图标。

**Since:** 18

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class ToolBarV2ItemImage--><!--Device-unnamed-export declare class ToolBarV2ItemImage-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolBarV2Item, AdvancedToolBarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolBarV2ItemGroupStyle, ToolBarV2ItemGroupStyleOptions, ToolBarV2ItemPlacement, ToolBarV2OverflowMenuStyle, ToolBarV2PaddingOptions, ToolBarV2StyleConfigs, ToolBarV2StyleOptions, ToolBarV2TitleConfigs, ToolBarV2TitleOptions, ToolBarV2TitleStyle, ToolBarV2TitleStyleOptions, ToolBarV2MaterialStyle } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options: ToolBarV2ItemImageOptions)
```

ToolBarV2ItemImage的构造函数。

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2ItemImage-constructor(options: ToolBarV2ItemImageOptions)--><!--Device-ToolBarV2ItemImage-constructor(options: ToolBarV2ItemImageOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ToolBarV2ItemImageOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemimageoptions-i.md) | Yes | image info. |

## activatedColor

```TypeScript
activatedColor?: ColorMetrics
```

工具栏子项在激活态下图标的颜色。

默认值：$r('sys.color.icon_emphasize')

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2ItemImage-activatedColor?: ColorMetrics--><!--Device-ToolBarV2ItemImage-activatedColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ColorMetrics
```

工具栏子项的图标的颜色。

默认值：$r('sys.color.icon_primary')

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2ItemImage-color?: ColorMetrics--><!--Device-ToolBarV2ItemImage-color?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: ResourceStr
```

工具栏子项的图标。

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2ItemImage-src: ResourceStr--><!--Device-ToolBarV2ItemImage-src: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
