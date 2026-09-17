# SymbolRenderingStrategy

The symbol rendering strategy.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SINGLE

```TypeScript
SINGLE = 0
```

Single-color mode (default value).

The default color is black.

You can set one or multiple colors, but only the first color will be applied.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MULTIPLE_COLOR

```TypeScript
MULTIPLE_COLOR = 1
```

Multi-color mode.

A maximum of three colors can be set. If only one color is set, it updates the color of the first layer, leaving other colors at their default values.

The sequence of color settings matches the layering order of the symbol; any colors beyond the number of symbol layers will not take effect.

Only color values are accepted. Opacity settings do not take effect.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MULTIPLE_OPACITY

```TypeScript
MULTIPLE_OPACITY = 2
```

Layered mode.

The default color is black. You can set one or multiple colors, but only the first color will be applied.

Opacity is predefined for the layers: 100% for the first layer, 50% for the second layer, and 20% for the third layer.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
