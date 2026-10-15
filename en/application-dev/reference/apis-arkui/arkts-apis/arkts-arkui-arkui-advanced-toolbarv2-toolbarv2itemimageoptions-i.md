# ToolBarV2ItemImageOptions

```TypeScript
export interface ToolBarV2ItemImageOptions
```

Defines the options for initializing a **ToolBarV2ItemImage** object.

**Since:** 18

<!--Device-unnamed-export interface ToolBarV2ItemImageOptions--><!--Device-unnamed-export interface ToolBarV2ItemImageOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction } from '@kit.ArkUI';
```

## activatedColor

```TypeScript
activatedColor?: ColorMetrics
```

Color of the icon when the toolbar item is activated.

Default value: **$r('sys.color.icon_emphasize')**.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2ItemImageOptions-activatedColor?: ColorMetrics--><!--Device-ToolBarV2ItemImageOptions-activatedColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ColorMetrics
```

Color of the icon.

Default value: **$r('sys.color.icon_primary')**.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2ItemImageOptions-color?: ColorMetrics--><!--Device-ToolBarV2ItemImageOptions-color?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: ResourceStr
```

Icon of the toolbar item.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2ItemImageOptions-src: ResourceStr--><!--Device-ToolBarV2ItemImageOptions-src: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
