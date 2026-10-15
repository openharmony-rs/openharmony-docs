# ToolBarV2ItemImage

```TypeScript
export declare class ToolBarV2ItemImage
```

Defines the icon content of a toolbar item.

**Since:** 18

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class ToolBarV2ItemImage--><!--Device-unnamed-export declare class ToolBarV2ItemImage-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options: ToolBarV2ItemImageOptions)
```

A constructor used to create a **ToolBarV2ItemImage** instance.

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

Color of the icon when the toolbar item is activated.

Default value: **$r('sys.color.icon_emphasize')**.

Decorator: @Trace

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

Color of the icon.

Default value: **$r('sys.color.icon_primary')**.

Decorator: @Trace

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

Icon of the toolbar item.

Decorator: @Trace

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2ItemImage-src: ResourceStr--><!--Device-ToolBarV2ItemImage-src: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
