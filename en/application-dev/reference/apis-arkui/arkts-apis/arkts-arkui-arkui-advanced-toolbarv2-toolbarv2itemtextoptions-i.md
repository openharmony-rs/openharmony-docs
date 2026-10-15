# ToolBarV2ItemTextOptions

```TypeScript
export interface ToolBarV2ItemTextOptions
```

Defines the options for initializing a **ToolBarV2ItemText** object.

**Since:** 18

<!--Device-unnamed-export interface ToolBarV2ItemTextOptions--><!--Device-unnamed-export interface ToolBarV2ItemTextOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction } from '@kit.ArkUI';
```

## activatedColor

```TypeScript
activatedColor?: ColorMetrics
```

Font color of the toolbar item in the activated state.

Default value: **$r('sys.color.font_emphasize')**.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2ItemTextOptions-activatedColor?: ColorMetrics--><!--Device-ToolBarV2ItemTextOptions-activatedColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ColorMetrics
```

Font color of the toolbar item.

Default value: **$r('sys.color.font_primary')**.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2ItemTextOptions-color?: ColorMetrics--><!--Device-ToolBarV2ItemTextOptions-color?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: ResourceStr
```

Text of the toolbar item.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2ItemTextOptions-text: ResourceStr--><!--Device-ToolBarV2ItemTextOptions-text: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
