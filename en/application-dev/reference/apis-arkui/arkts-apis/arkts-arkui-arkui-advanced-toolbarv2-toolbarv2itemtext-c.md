# ToolBarV2ItemText

```TypeScript
export declare class ToolBarV2ItemText
```

Declare type ToolBarV2ItemText

**Since:** 18

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class ToolBarV2ItemText--><!--Device-unnamed-export declare class ToolBarV2ItemText-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options: ToolBarV2ItemTextOptions)
```

The constructor used to create a ToolBarV2ItemText object.

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

Text fontColor when the item is activated.

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

Define text fontColor.

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

Define text content.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2ItemText-text: ResourceStr--><!--Device-ToolBarV2ItemText-text: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
