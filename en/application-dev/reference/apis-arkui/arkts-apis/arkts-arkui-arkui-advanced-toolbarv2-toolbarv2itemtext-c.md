# ToolBarV2ItemText

```TypeScript
export declare class ToolBarV2ItemText
```

Defines the text of a toolbar item.

**Since:** 18

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class ToolBarV2ItemText--><!--Device-unnamed-export declare class ToolBarV2ItemText-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolbarV2Item, AdvancedToolbarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolbarV2ItemGroupStyle, ToolbarV2ItemGroupStyleOptions, ToolbarV2ItemPlacement, ToolbarV2OverflowMenuStyle, ToolbarV2PaddingOptions, ToolbarV2StyleConfigs, ToolbarV2StyleOptions, ToolbarV2TitleConfigs, ToolbarV2TitleOptions, ToolbarV2TitleStyle, ToolbarV2TitleStyleOptions } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options: ToolBarV2ItemTextOptions)
```

A constructor used to create a **ToolBarV2ItemText** instance.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2ItemText-constructor(options: ToolBarV2ItemTextOptions)--><!--Device-ToolBarV2ItemText-constructor(options: ToolBarV2ItemTextOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ToolBarV2ItemTextOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemtextoptions-i.md) | Yes | text info. |

## activatedColor

```TypeScript
activatedColor?: ColorMetrics
```

Font color of the toolbar item in the activated state.

</div>Default value: **$r('sys.color.font_emphasize')**.

Decorator: @Trace

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2ItemText-activatedColor?: ColorMetrics--><!--Device-ToolBarV2ItemText-activatedColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ColorMetrics
```

Font color of the toolbar item.

Default value: **$r('sys.color.font_primary')**.

Decorator: @Trace

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2ItemText-color?: ColorMetrics--><!--Device-ToolBarV2ItemText-color?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: ResourceStr
```

Text of the toolbar item.

Decorator: @Trace

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2ItemText-text: ResourceStr--><!--Device-ToolBarV2ItemText-text: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
