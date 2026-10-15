# SymbolRenderingStrategy

```TypeScript
declare enum SymbolRenderingStrategy
```

Enumerates the rendering modes.

**Since:** 11

<!--Device-unnamed-declare enum SymbolRenderingStrategy--><!--Device-unnamed-declare enum SymbolRenderingStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MULTIPLE_COLOR

```TypeScript
MULTIPLE_COLOR = 1
```

Multicolor mode.

Up to three colors can be set. When only one color is set, the first-layer color of the symbol icon is modified, and the other colors remain the default colors.

The color setting order matches the icon layer order. When the number of colors is greater than the number of icon layers, the extra colors do not take effect.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-SymbolRenderingStrategy-MULTIPLE_COLOR = 1--><!--Device-SymbolRenderingStrategy-MULTIPLE_COLOR = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MULTIPLE_OPACITY

```TypeScript
MULTIPLE_OPACITY = 2
```

Layered mode.

The default is black, and one or more colors can be set. When multiple colors are set, only the first color takes effect.

The opacity is related to the layers. For a common symbol icon, the default opacity of the first layer is 100%, that of the second layer is 50%, and that of the third layer is 20%. When the set color contains opacity, the set opacity is superimposed with the default opacity of each layer.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-SymbolRenderingStrategy-MULTIPLE_OPACITY = 2--><!--Device-SymbolRenderingStrategy-MULTIPLE_OPACITY = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SINGLE

```TypeScript
SINGLE = 0
```

Monochrome mode (default value).

One or more colors can be set, and the default is black.

When multiple colors are set, only the first color takes effect.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-SymbolRenderingStrategy-SINGLE = 0--><!--Device-SymbolRenderingStrategy-SINGLE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
